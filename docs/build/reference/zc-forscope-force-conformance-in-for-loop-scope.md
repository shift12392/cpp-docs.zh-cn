---
title: '/Zc: forscope （强制在 for 循环范围一致性） |Microsoft 文档'
ms.custom: ''
ms.date: 03/06/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.ForceConformanceInForLoopScope
- VC.Project.VCCLWCECompilerTool.ForceConformanceInForLoopScope
- /zc:forScope
dev_langs:
- C++
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: 3031f02d-3b14-4ad0-869e-22b0110c3aed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b21c844cd29c7fb45e58f44fdf8eaae427b74235
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="zcforscope-force-conformance-in-for-loop-scope"></a>/Zc:forScope（强制 for 循环范围中的一致性）

用于针对具有 Microsoft 扩展 ( [/Ze](../../cpp/for-statement-cpp.md) ) 的[for](../../build/reference/za-ze-disable-language-extensions.md)循环实现标准 C++ 行为。

## <a name="syntax"></a>语法

> **/Zc:forScope**[**-**]

## <a name="remarks"></a>备注

标准行为是使 **for** 循环的初始值设定项在 **for** 循环之后超出范围。 在 **/Zc:forScope-** 和 [/Ze](../../build/reference/za-ze-disable-language-extensions.md)下， **for** 循环的初始值设定项保持在范围内，直到局部范围结束。

**/Zc: forscope**选项默认处于启用。 **/Zc: forscope**时不会影响[/ 宽松-](permissive-standards-conformance.md)指定选项。

**/Zc:forScope-** 选项已弃用，并将从未来版本中删除。 使用 **/Zc:forScope-** 将生成弃用警告 D9035。

以下代码在 **/Ze** （而不是 **/Za**）下进行编译：

```cpp
// zc_forScope.cpp
// compile by using: cl /Zc:forScope- /Za zc_forScope.cpp
// C2065, D9035 expected  
int main() {
    // Compile by using cl /Zc:forScope- zc_forScope.cpp
    // to compile this non-standard code as-is.
    // Uncomment the following line to resolve C2065 for /Za.
    // int i;
    for (int i = 0; i < 1; i++)
        ;
    i = 20;   // i has already gone out of scope under /Za
}
```

使用 **/Zc:forScope-** 时，如果变量由于在上一范围内所作的声明而处在范围内，则将生成警告 C4288（默认关闭）。 为了说明这点，请删除示例代码中用于声明 `//` 的 `int i`字符。

可通过使用 **conform** 杂注修改 [/Zc:forScope](../../preprocessor/conform.md) 的运行时行为。

如果在包含现有 .pch 文件的项目中使用 **/Zc:forScope-** ，则将生成警告、忽略 **/Zc:forScope-** ，并使用现有 .pch 文件继续进行编译。 如果你希望生成新的.pch 文件，使用[/Yc （创建预编译标头文件）](../../build/reference/yc-create-precompiled-header-file.md)。

有关 Visual C++ 中一致性问题的详细信息，请参阅 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **C/c + +** > **语言**属性页。

1. 修改 **“强制 For 循环范围中的一致性”** 属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForceConformanceInForLoopScope%2A>。

## <a name="see-also"></a>请参阅

[/Zc（一致性）](../../build/reference/zc-conformance.md)<br/>
[/Za、/Ze（禁用语言扩展）](../../build/reference/za-ze-disable-language-extensions.md)<br/>
