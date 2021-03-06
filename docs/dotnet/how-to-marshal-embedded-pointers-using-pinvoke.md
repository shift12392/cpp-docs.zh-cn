---
title: 如何： 封送嵌入式指针使用 PInvoke |Microsoft 文档
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- embedded pointers [C++]
- interop [C++], embedded pointers
- platform invoke [C++], embedded pointers
- marshaling [C++], embedded pointers
- data marshaling [C++], embedded pointers
ms.assetid: f12c1b9a-4f82-45f8-83c8-3fc9321dbb98
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a07c9742c393abe2a6213378ee8963839ab66c90
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-marshal-embedded-pointers-using-pinvoke"></a>如何：使用 PInvoke 封送嵌入式指针
可以使用平台调用 (P/Invoke) 的功能的托管代码中调用在非托管 Dll 中实现的函数。 如果该 DLL 的源代码不可用，P/Invoke 是唯一的选项来进行互操作。 但是，不同于其他.NET 语言，Visual c + + 提供 P/Invoke 的替代方法。 有关详细信息，请参阅[使用 c + + 互操作 (隐式 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)和[How to： 封送嵌入式指针使用 c + + 互操作](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)。  
  
## <a name="example"></a>示例  
 将结构传递给本机代码，则需要创建等效的数据布局到本机结构的托管的结构。 但是，包含指针的结构需要特殊处理。 对于本机结构中每个嵌入的指针，该结构的托管的版本应该包含的实例<xref:System.IntPtr>类型。 此外，内存为必须显式分配这些实例，初始化，并释放使用<xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A>， <xref:System.Runtime.InteropServices.Marshal.StructureToPtr%2A>，和<xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A>方法。  
  
 下面的代码由非托管和的托管的模块组成。 非托管的模块是一个 DLL，它定义接受一个称为包含的指针的 ListString 结构的函数和一个名为 TakesListStruct 函数。 托管的模块是一个命令行应用程序以便导入 TakesListStruct 函数和定义结构调用 MListStruct，它等效于本机 ListStruct，只不过使用表示双 *<xref:System.IntPtr>实例。 在调用 TakesListStruct 之前, 的主函数分配和初始化此字段引用的内存。  
  
```cpp  
// TraditionalDll6.cpp  
// compile with: /EHsc /LD  
#include <stdio.h>  
#include <iostream>  
#define TRADITIONALDLL_EXPORTS  
#ifdef TRADITIONALDLL_EXPORTS  
#define TRADITIONALDLL_API __declspec(dllexport)  
#else  
#define TRADITIONALDLL_API __declspec(dllimport)  
#endif  
  
#pragma pack(push, 8)  
struct ListStruct {  
   int count;  
   double* item;  
};  
#pragma pack(pop)  
  
extern "C" {  
   TRADITIONALDLL_API void TakesListStruct(ListStruct);  
}  
  
void TakesListStruct(ListStruct list) {  
   printf_s("[unmanaged] count = %d\n", list.count);  
   for (int i=0; i<list.count; i++)  
      printf_s("array[%d] = %f\n", i, list.item[i]);  
}  
```  
  
```cpp  
// EmbeddedPointerMarshalling.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
[StructLayout(LayoutKind::Sequential, Pack=8)]  
value struct MListStruct {  
   int count;  
   IntPtr item;  
};  
  
value struct TraditionalDLL {  
    [DllImport("TraditionalDLL6.dll")]  
   static public void TakesListStruct(MListStruct);  
};  
  
int main() {  
   array<double>^ parray = gcnew array<double>(10);  
   Console::WriteLine("[managed] count = {0}", parray->Length);  
  
   Random^ r = gcnew Random();  
   for (int i=0; i<parray->Length; i++) {  
      parray[i] = r->NextDouble() * 100.0;  
      Console::WriteLine("array[{0}] = {1}", i, parray[i]);  
   }  
  
   int size = Marshal::SizeOf(double::typeid);  
   MListStruct list;  
   list.count = parray->Length;  
   list.item = Marshal::AllocCoTaskMem(size * parray->Length);  
  
   for (int i=0; i<parray->Length; i++) {  
      IntPtr t = IntPtr(list.item.ToInt32() + i * size);  
      Marshal::StructureToPtr(parray[i], t, false);  
   }  
  
   TraditionalDLL::TakesListStruct( list );  
   Marshal::FreeCoTaskMem(list.item);  
}  
```  
  
 请注意，对使用传统的托管代码公开的 DLL 没有一部分 #include 指令。 事实上，DLL 在运行时访问仅，因此问题与函数导入具有<xref:System.Runtime.InteropServices.DllImportAttribute>将不会在编译时检测。  
  
## <a name="see-also"></a>请参阅  
 [在 C++ 中使用显式 PInvoke（DllImport 特性）](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)