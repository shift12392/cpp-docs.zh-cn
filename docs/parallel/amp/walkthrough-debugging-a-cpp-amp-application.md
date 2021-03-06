---
title: 演练： 调试 c + + AMP 应用程序 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- debugging, C++ Accelerated Massive Parallelism
- C++ AMP, debugging
- C++ Accelerated Massive Parallelism, debugging
- debugging, C++ AMP
ms.assetid: 40e92ecc-f6ba-411c-960c-b3047b854fb5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1bf80276b5434804651bcc4507397e9479f6e494
ms.sourcegitcommit: da7b7533d1a4dc141cc0f09149e4e4196f2fe329
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2018
---
# <a name="walkthrough-debugging-a-c-amp-application"></a>演练：调试 C++ AMP 应用程序
本主题演示如何调试使用 C++ Accelerated Massive Parallelism (C++ AMP) 应用程序以便利用图形处理单元 (GPU)。 它使用总结大整数数组的并行缩减程序。 本演练阐释了以下任务：  
  
-   启动 GPU 调试器。  
  
-   在“GPU 线程”窗口中检查 GPU 线程。  
  
-   使用“并行堆栈”窗口同时查看多个 GPU 线程调用堆栈。  
  
-   使用“并行监视”窗口同时检查单个表达式在多个线程中的值。  
  
-   标记、冻结、解冻和组合 GPU 线程。  
  
-   将 Tile 的所有线程执行到代码中的特定位置。  
  
## <a name="prerequisites"></a>系统必备  
 在开始本演练之前：  
  
-   读取[c + + AMP 概述](../../parallel/amp/cpp-amp-overview.md)。  
  
-   确保文本编辑器中显示行号。 有关详细信息，请参阅[如何： 在编辑器中显示行号](/visualstudio/ide/reference/how-to-display-line-numbers-in-the-editor)。  
  
-   确保运行 [!INCLUDE[win8](../../build/reference/includes/win8_md.md)] 或 [!INCLUDE[winserver8](../../build/reference/includes/winserver8_md.md)] 以支持在软件模拟器中进行调试。  
  
 [!INCLUDE[note_settings_general](../../mfc/includes/note_settings_general_md.md)]  
  
### <a name="to-create-the-sample-project"></a>创建示例项目  
  
1.  启动 Visual Studio。  
  
2.  在菜单栏上，依次选择“文件” 、“新建” 、“项目” 。  
  
3.  下**已安装**在模板窗格中，选择**Visual c + +**。  
  
4.  选择**Win32 控制台应用程序**，类型`AMPMapReduce`中**名称**框中，，然后选择**确定**按钮。  
  
5.  选择“下一步”按钮。  
  
6.  清除**预编译标头**复选框，然后依次**完成**按钮。  
  
7.  在**解决方案资源管理器**，从项目中删除 stdafx.h、 targetver.h 和 stdafx.cpp。  
  
8.  打开 AMPMapReduce.cpp 并用下面的代码替换其中的内容。  
  
 ```cpp  
    // AMPMapReduce.cpp defines the entry point for the program.  
    // The program performs a parallel-sum reduction that computes the sum of an array of integers.   
  
    #include <stdio.h>  
    #include <tchar.h>  
    #include <amp.h>  
  
    const int BLOCK_DIM = 32;  
  
    using namespace concurrency;  
  
    void sum_kernel_tiled(tiled_index<BLOCK_DIM> t_idx, array<int, 1> &A, int stride_size) restrict(amp)  
    {  
        tile_static int localA[BLOCK_DIM];  
  
        index<1> globalIdx = t_idx.global * stride_size;  
        index<1> localIdx = t_idx.local;  
  
        localA[localIdx[0]] =  A[globalIdx];  
  
        t_idx.barrier.wait();  
  
        // Aggregate all elements in one tile into the first element.  
        for (int i = BLOCK_DIM / 2; i > 0; i /= 2)   
        {  
            if (localIdx[0] < i)   
            {  
  
                localA[localIdx[0]] += localA[localIdx[0] + i];  
            }  
  
            t_idx.barrier.wait();  
        }  
  
        if (localIdx[0] == 0)  
        {  
            A[globalIdx] = localA[0];  
        }  
    }  
  
    int size_after_padding(int n)  
    {  
        // The extent might have to be slightly bigger than num_stride to   
        // be evenly divisible by BLOCK_DIM. You can do this by padding with zeros.  
        // The calculation to do this is BLOCK_DIM * ceil(n / BLOCK_DIM)  
        return ((n - 1) / BLOCK_DIM + 1) * BLOCK_DIM;  
    }  
  
    int reduction_sum_gpu_kernel(array<int, 1> input)   
    {  
        int len = input.extent[0];  
  
        //Tree-based reduction control that uses the CPU.  
        for (int stride_size = 1; stride_size < len; stride_size *= BLOCK_DIM)   
        {  
            // Number of useful values in the array, given the current  
            // stride size.  
            int num_strides = len / stride_size;    
  
            extent<1> e(size_after_padding(num_strides));  
  
            // The sum kernel that uses the GPU.  
            parallel_for_each(extent<1>(e).tile<BLOCK_DIM>(), [&input, stride_size] (tiled_index<BLOCK_DIM> idx) restrict(amp)  
            {  
                sum_kernel_tiled(idx, input, stride_size);  
            });  
        }  
  
        array_view<int, 1> output = input.section(extent<1>(1));  
        return output[0];  
    }  
  
    int cpu_sum(const std::vector<int> &arr) {  
        int sum = 0;  
        for (size_t i = 0; i < arr.size(); i++) {  
            sum += arr[i];  
        }  
        return sum;  
    }  
  
    std::vector<int> rand_vector(unsigned int size) {  
        srand(2011);  
  
        std::vector<int> vec(size);  
        for (size_t i = 0; i < size; i++) {  
            vec[i] = rand();  
        }  
        return vec;  
    }  
  
    array<int, 1> vector_to_array(const std::vector<int> &vec) {  
        array<int, 1> arr(vec.size());  
        copy(vec.begin(), vec.end(), arr);  
        return arr;  
    }  
  
    int _tmain(int argc, _TCHAR* argv[])  
    {  
        std::vector<int> vec = rand_vector(10000);  
        array<int, 1> arr = vector_to_array(vec);  
  
        int expected = cpu_sum(vec);  
        int actual = reduction_sum_gpu_kernel(arr);  
  
        bool passed = (expected == actual);  
        if (!passed) {  
            printf("Actual (GPU): %d, Expected (CPU): %d", actual, expected);  
        }  
        printf("sum: %s\n", passed  "Passed!" : "Failed!");   
  
        getchar();  
  
        return 0;  
    }  
  
 ```  
  
9. 在菜单栏上，依次选择“文件”、“全部保存”。  
  
10. 在**解决方案资源管理器**，打开快捷菜单**AMPMapReduce**，然后选择**属性**。  
  
11. 在**属性页**对话框中，在**配置属性**，选择**C/c + +**，**预编译标头**。  
  
12. 有关**预编译标头**属性中，选择**不使用预编译头**，然后选择**确定**按钮。  
  
13. 在菜单栏上，依次选择 **“生成”**、 **“生成解决方案”**。  
  
## <a name="debugging-the-cpu-code"></a>调试 CPU 代码  
 在此过程中，您将使用本地 Windows 调试器，以确保此应用程序中的 CPU 代码是正确的。 在此应用程序中，特别值得关注的 CPU 代码段是 `for` 函数中的 `reduction_sum_gpu_kernel` 循环。 它控制运行在 GPU 上的基于树的并行缩减。  
  
### <a name="to-debug-the-cpu-code"></a>调试 CPU 代码  
  
1.  在**解决方案资源管理器**，打开快捷菜单**AMPMapReduce**，然后选择**属性**。  
  
2.  在**属性页**对话框中，在**配置属性**，选择**调试**。 验证**本地 Windows 调试器**中选择**要启动的调试器**列表。  
  
3.  返回代码编辑器。  
  
4.  在下图所示的代码行上设置断点（大约第 67 和 70 行）。  
  
     ![CPU 断点](../../parallel/amp/media/campcpubreakpoints.png "campcpubreakpoints")  
CPU 断点  
  
5.  在菜单栏上，依次选择“调试”、“开始调试”。  
  
6.  在**局部变量**窗口中，观察的值`stride_size`直到抵达第 70 行断点。  
  
7.  在菜单栏上，依次选择“调试”、“停止调试”。  
  
## <a name="debugging-the-gpu-code"></a>调试 GPU 代码  
 本部分说明如何调试 GPU 代码，即 `sum_kernel_tiled` 函数包含的代码。 GPU 代码为每个“块”并行计算整数和。  
  
### <a name="to-debug-the-gpu-code"></a>调试 GPU 代码  
  
1.  在**解决方案资源管理器**，打开快捷菜单**AMPMapReduce**，然后选择**属性**。  
  
2.  在**属性页**对话框中，在**配置属性**，选择**调试**。  
  
3.  在**要启动的调试器**列表中，选择**本地 Windows 调试器**。  
  
4.  在**调试器类型**列表中，验证**自动**选择。

    **自动**是默认值。 在 Windows 10 之前**仅限 GPU**是必需的值，而不是**自动**。
  
5.  选择“确定”  按钮。  
  
6.  如下图所示，在第 30 行处设置一个断点。  
  
     ![GPU 断点](../../parallel/amp/media/campgpubreakpoints.png "campgpubreakpoints")  
GPU 断点  
  
7.  在菜单栏上，依次选择“调试”、“开始调试”。 由于第 67 和 70 行代码在 CPU 上执行，因此 GPU 调试期间将不执行这些行中的 CPU 代码断点。  
  
### <a name="to-use-the-gpu-threads-window"></a>使用“GPU 线程”窗口  
  
1.  若要打开 GPU 线程窗口中的，在菜单栏上，选择**调试**， **Windows**， **GPU 线程**。  
  
     在出现的“GPU 线程”窗口中，可以检查 GPU 线程的状态。  
  
2.  将“GPU 线程”窗口停靠在 Visual Studio 底部。 选择**展开线程切换**按钮以显示 tile 和线程文本框。 如下图所示，“GPU 线程”窗口显示活动和受阻的 GPU 线程的总数。  
  
     ![包含 4 个活动线程的 GPU 线程窗口](../../parallel/amp/media/campc.png "campc")  
“GPU 线程”窗口  
  
     系统为此计算分配了 313 个 Tile。 每个 Tile 包含 32 个线程。 由于本地 GPU 调试在软件模拟器中进行，因此有四个活动的 GPU 线程。 四个线程同时执行指令，然后一起移动到下一条指令。  
  
     在 GPU 线程窗口中，有四个 GPU 线程活动和 28 个 GPU 线程受阻[tile_barrier:: wait](reference/tile-barrier-class.md#wait)大约第 21 行处定义的语句 (`t_idx.barrier.wait();`)。 所有这 32 个GPU 线程都属于第一个 Tile `tile[0]`。 当前线程所在的行由箭头指示。 若要切换到其他线程，请使用下列方法之一：  

  
    -   在线程可以在 GPU 线程窗口中切换到行中，打开快捷菜单，然后选择**切换到线程**。 如果该行代表多个线程，将按线程坐标切换到第一个线程。  
  
    -   在对应的文本框中输入线程的平铺和线程值，然后选择**切换线程**按钮。  
  
     调用堆栈窗口显示当前 GPU 线程的调用堆栈。  
  
### <a name="to-use-the-parallel-stacks-window"></a>使用“并行堆栈”窗口  
  
1.  若要打开并行堆栈窗口中的，在菜单栏上，选择**调试**， **Windows**，**并行堆栈**。  
  
     可以使用“并行堆栈”窗口同时检查多个 GPU 线程的堆栈帧。  
  
2.  将“并行堆栈”窗口停靠在 Visual Studio 底部。  
  
3.  请确保**线程**在左上角中的列表中选择。 在下图中，“并行堆栈”窗口显示了您在“GPU 线程”窗口看到的 GPU 线程的调用堆栈集中视图。  
  
     ![包含 4 个活动线程的并行堆栈窗口](../../parallel/amp/media/campd.png "campd")  
“并行堆栈”窗口  
  
     32 个线程从 `_kernel_stub` 执行到 `parallel_for_each` 函数调用中的 lambda 语句，随后执行到 `sum_kernel_tiled` 函数，再从这里进行并行缩减。 28 个线程超出 32 个线程前进到[tile_barrier:: wait](reference/tile-barrier-class.md#wait)语句和保持在行 22，阻止状态，而其他 4 个线程中保持活动状态`sum_kernel_tiled`在第 30 行的函数。  

  
     通过“并行堆栈”窗口中丰富的数据提示，可以检查“GPU 线程”窗口中可用 GPU 线程的属性。 若要执行此操作，请将鼠标指针停留在的堆栈帧**sum_kernel_tiled**。 下图显示了数据提示。  
  
     ![并行堆栈窗口的数据提示](../../parallel/amp/media/campe.png "campe")  
GPU 线程数据提示  
  
     有关并行堆栈窗口的详细信息，请参阅[使用并行堆栈窗口](/visualstudio/debugger/using-the-parallel-stacks-window)。  
  
### <a name="to-use-the-parallel-watch-window"></a>使用“并行监视”窗口  
  
1.  若要打开并行监视窗口中的，在菜单栏上，选择**调试**， **Windows**，**并行监视**，**并行监视 1**。  
  
     可以使用“并行监视”窗口来检查某表达式在多个线程中的值。  
  
2.  将“并行监视 1”窗口停靠在 Visual Studio 底部。 “并行监视”窗口的表中有 32 行。 每个行对应于同时出现在“GPU 线程”窗口和“并行堆栈”窗口的 GPU 线程。 现在，可以输入所需的表达式，以检查其在所有这 32 个 GPU 线程中的值。  
  
3.  选择**添加监视**列标题，输入`localIdx`，然后选择 Enter 键。  
  
4.  选择**添加监视**再次列标题，键入`globalIdx`，然后选择 Enter 键。  
  
5.  选择**添加监视**再次列标题，键入`localA[localIdx[0]]`，然后选择 Enter 键。  
  
     您可以通过选择相应的列标题来按指定表达式排序。  
  
     选择**localA [localIdx [0]]** 列标题对列排序。 下图显示通过排序的结果**localA [localIdx [0]]**。  
  
     ![结果按顺序排列的并行监视窗口](../../parallel/amp/media/campf.png "campf")  
 排序结果  
  
     你可以通过选择 Excel 按钮，然后选择将并行监视窗口中的内容导出到 Excel**在 Excel 中打开**。 如果开发计算机上安装有 Excel，这将打开包含该内容的 Excel 工作表。  
  
6.  “并行监视”窗口的右上角有一个筛选器控件，可以使用布尔表达式来筛选内容。 Enter`localA[localIdx[0]] > 20000`中筛选器控件文本框中，然后选择 Enter 键。  
  
     该窗口现在只包含 `localA[localIdx[0]]` 值大于 20000 的线程。 内容仍按 `localA[localIdx[0]]` 列排序，这是之前执行的排序操作。  
  
## <a name="flagging-gpu-threads"></a>标记 GPU 线程  
 通过在“GPU 线程”窗口、“并行监视”窗口或“并行堆栈”窗口的数据提示中进行标记，可以标记特定的 GPU 线程。 如果“GPU 线程”窗口中的某一行包含多个线程，则通过标记该行，可标记该行中包含的所有线程。  
  
### <a name="to-flag-gpu-threads"></a>标记 GPU 线程  
  
1.  选择 **[线程]** 并行监视 1 窗口按平铺索引和线程索引进行排序中的列标题。  
  
2.  在菜单栏上，选择**调试**，**继续**，这将导致产生的四个线程的处于活动状态前进到下一个屏障 （在 ampmapreduce.cpp 的第 32 行处定义）。  
  
3.  在当前处于活动状态的四个线程所在行的左侧，选择标志符号。  
  
     下图显示了“GPU 线程”窗口中经过标记的四个活动线程。  
  
     ![使用标记的线程的 GPU 线程窗口](../../parallel/amp/media/campg.png "campg")  
GPU 线程窗口中的活动线程  
  
     “并行监视”窗口和“并行堆栈”窗口的数据提示都会指示已标记的线程。  
  
4.  如果要关注所标记的四个线程，可在“GPU 线程”、“并行监视”和“并行堆栈”窗口中选择仅显示标记的线程。  
  
     选择仅显示标记的线程上的按钮任何的 windows 或在**调试位置**工具栏。 下图上显示的仅显示标记的线程按钮**调试位置**工具栏。  
  
     ![调试仅显示已标记项图标的位置工具栏](../../parallel/amp/media/camph.png "camph")  
“仅显示已标记项”按钮  
  
     现在，“GPU 线程”、“并行监视”和“并行堆栈”窗口将仅显示标记的线程。  
  
## <a name="freezing-and-thawing-gpu-threads"></a>冻结和解冻 GPU 线程  
 您可以从“GPU 线程”窗口或“并行监视”窗口冻结（挂起）和解冻（恢复）GPU 线程。 你可以冻结或解冻 CPU 线程相同的方式;有关信息，请参阅[如何： 使用线程窗口](/visualstudio/debugger/how-to-use-the-threads-window)。  
  
### <a name="to-freeze-and-thaw-gpu-threads"></a>冻结和解冻 GPU 线程  
  
1.  选择**仅显示标记的线程**按钮以显示所有线程。  
  
2.  在菜单栏上，选择**调试**，**继续**。  
  
3.  打开活动行的快捷菜单，然后选择**冻结**。  
  
     下图中的“GPU 线程”窗口显示，所有四个线程均已冻结。  
  
     ![显示已冻结的线程的 GPU 线程窗口](../../parallel/amp/media/campk.png "campk")  
GPU 线程窗口中的已冻结线程  
  
     同样，“并行监视”窗口也显示所有四个线程均已冻结。  
  
4.  在菜单栏上，选择**调试**，**继续**以允许以第 22 行处的屏障并抵达第 30 行处的断点的接下来四个 GPU 线程。 “GPU 线程”窗口显示，之前冻结的四个线程仍被冻结并处于活动状态。  
  
5.  在菜单栏上，选择**调试**，**继续**。  
  
6.  从“并行监视”窗口中，还可以单独解冻一个或同时解冻多个 GPU 线程。  
  
### <a name="to-group-gpu-threads"></a>对 GPU 线程分组  
  
1.  其中一个中的线程的快捷菜单上**GPU 线程**窗口中，选择**Group By**，**地址**。  
  
     “GPU 线程”窗口中的线程随即按地址分组。 该地址对应于每组线程所在的反汇编指令。 24 个线程位于第 22 行其中[tile_barrier:: wait 方法](reference/tile-barrier-class.md#wait)执行。 12 个线程位于第 32 行屏障的指令处。 其中 4 个线程经过标记。 8 个线程位于第 30 行的断点处。 其中 4 个线程已冻结。 下图显示了“GPU 线程”窗口中经过分组的线程。  

  
     ![与线程的 GPU 线程窗口按地址分组](../../parallel/amp/media/campl.png "campl")  
“GPU 线程”窗口中经过分组的线程  
  
2.  你还可以执行**Group By**操作通过打开并行监视窗口中，数据网格的快捷菜单选择**Group By**，然后选择对应于你希望如何菜单项若要进行分组的线程。  
  
## <a name="running-all-threads-to-a-specific-location-in-code"></a>将所有线程运行到代码中的特定位置  
 将给定 tile 中的所有线程都运行到通过使用包含光标的行**都运行当前平铺到光标处**。  
  
### <a name="to-run-all-threads-to-the-location-marked-by-the-cursor"></a>将所有线程运行到光标指示的位置  
  
1.  在已冻结线程的快捷菜单，选择**解冻**。  
  
2.  在代码编辑器中，将光标置于第 30 行内。  
  
3.  在代码编辑器的快捷菜单中，选择**当前 Tile 运行到光标处**。  
  
     之前在第 21 行处受阻的 24 个线程将继续运行到第 32 行。 这一点在**GPU 线程**窗口。  
  
## <a name="see-also"></a>请参阅  
 [C++ AMP 概述](../../parallel/amp/cpp-amp-overview.md)   
 [调试 GPU 代码](/visualstudio/debugger/debugging-gpu-code)   
 [如何： 使用 GPU 线程窗口](/visualstudio/debugger/how-to-use-the-gpu-threads-window)   
 [如何： 使用并行监视窗口](/visualstudio/debugger/how-to-use-the-parallel-watch-window)   
 [分析 c + + AMP 代码使用并发可视化工具](http://go.microsoft.com/fwlink/p/?linkid=253987&clcid=0x409)

