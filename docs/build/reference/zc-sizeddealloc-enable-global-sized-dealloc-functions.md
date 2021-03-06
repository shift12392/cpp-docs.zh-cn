---
title: /Zc:sizedDealloc （启用全局调整大小的释放函数） |Microsoft 文档
ms.custom: ''
ms.date: 03/06/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- sizedDealloc
- /Zc:sizedDealloc
dev_langs:
- C++
helpviewer_keywords:
- -Zc compiler options (C++)
- sizedDealloc
- Enable Global Sized Deallocation Functions
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 3a73ace0-4d36-420a-b699-0ca6fc0dd134
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0a912b87240ad37e29cade077b7a93aa1e7886a6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="zcsizeddealloc-enable-global-sized-deallocation-functions"></a>/Zc:sizedDealloc （启用全局调整大小的释放函数）

**/Zc:sizedDealloc**编译器选项告知编译器优先调用全局`operator delete`或`operator delete[]`函数具有第二个参数的类型的`size_t`时可用的对象的大小。 这些函数可能使用`size_t`参数来优化性能的释放函数。

## <a name="syntax"></a>语法

> **/Zc:sizedDealloc**[**-**]

## <a name="remarks"></a>备注

C + + 11 标准中，你可以定义静态成员函数`operator delete`和`operator delete[]`它们采用第二个，`size_t`参数。 通常这些与结合使用时[运算符 new](../../cpp/new-operator-cpp.md)函数来实现更高效的分配器和释放的对象。 但是，C + + 11 未定义一组等效的释放函数在全局范围内。 在 C + + 11，全局释放函数具有第二个参数的类型的`size_t`被视为位置删除函数。 它们必须由大小自变量传递显式调用。

C + + 14 标准更改编译器的行为。 在定义全局`operator delete`和`operator delete[]`它们采用类型的第二个参数`size_t`，编译器首选时不会调用成员作用域版本和对象的大小可调用这些函数。 编译器将隐式传递大小自变量。 当编译器无法确定正在解除分配的对象的大小，时会调用的单个自变量版本。 否则，选择要调用的释放函数的版本的一般规则仍适用。 对全局函数的调用可以显式指定通过预先计算范围解析运算符 (`::`) 到解除分配的函数调用。

默认情况下，启动 Visual Studio 2015 中的 Visual c + + 实现此 C + + 14 标准行为。 可以通过设置显式指定此 **/Zc:sizedDealloc**编译器选项。 这表示可能影响重大更改。 使用 **/zc: sizeddealloc-** 选项以保留旧行为，例如，当你的代码定义了使用类型的第二个参数的放置 delete 运算符`size_t`。 具有第二个参数的类型的全局释放函数的默认 Visual Studio 库实现`size_t`调用的单个参数版本。 如果你的代码提供了唯一单-参数全局 delete 运算符和运算符 delete []，全局调整了大小的释放函数的默认库实现调用全局函数。

**/Zc:sizedDealloc**编译器选项默认处于启用。 [/ 宽松-](permissive-standards-conformance.md)选项不影响 **/Zc:sizedDealloc**。

有关 Visual C++ 中一致性问题的详细信息，请参阅 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 从**配置**下拉列表菜单中，选择**所有配置**。

1. 选择**配置属性** > **C/c + +** > **命令行**属性页。

1. 修改**其他选项**属性以包含 **/Zc:sizedDealloc**或 **/zc: sizeddealloc-** ，然后选择**确定**。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)<br/>
[/Zc（一致性）](../../build/reference/zc-conformance.md)<br/>
