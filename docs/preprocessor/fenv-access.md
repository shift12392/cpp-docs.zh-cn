---
title: fenv_access |Microsoft 文档
ms.custom: ''
ms.date: 03/12/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.fenv_access
- fenv_access_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, fenv_access
- fenv_access pragma
ms.assetid: 2ccea292-0ae4-42ce-9c67-cc189299857b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f74f20b1dcb20c1449d21e91181f8bfb17075b7e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="fenvaccess"></a>fenv_access

禁用 (**上**) 或启用 (**关闭*) 可更改浮点环境优化，标记测试和模式更改。

## <a name="syntax"></a>语法

> **#pragma fenv_access (** {**上** | **关闭**} **)**  

## <a name="remarks"></a>备注

默认情况下， **fenv_access**是**关闭**。 如果编译器可以假设你的代码不会访问或操作浮点的环境中，则它可以执行许多浮点代码优化。 设置**fenv_access**到**上**以告知编译器你的代码访问的浮点环境来测试状态标志，例外情况之外，或设置控件模式的标志。 编译器将禁用这些优化，以便你的代码可以访问的浮点环境一致。 

浮点行为的详细信息，请参阅[/fp （指定浮点行为）](../build/reference/fp-specify-floating-point-behavior.md)。

类型的一些优化功能，都可能会**fenv_access**是：

- 全局公共子表达式消除

- 代码运动

- 常量折叠

其他浮点杂注包括：

- [float_control](../preprocessor/float-control.md)

- [fp_contract](../preprocessor/fp-contract.md)

## <a name="examples"></a>示例

此示例将设置**fenv_access**到**上**设置 24 位精度的浮点控制寄存器：

```cpp
// pragma_directive_fenv_access_x86.cpp
// compile with: /O2
// processor: x86
#include <stdio.h>
#include <float.h>
#include <errno.h>
#pragma fenv_access (on)

int main() {
   double z, b = 0.1, t = 0.1;
   unsigned int currentControl;
   errno_t err;

   err = _controlfp_s(&currentControl, _PC_24, _MCW_PC);
   if (err != 0) {
      printf_s("The function _controlfp_s failed!\n");
      return -1;
   }
   z = b * t;
   printf_s ("out=%.15e\n",z);
}
```

```Output
out=9.999999776482582e-003
```

如果注释掉`#pragma fenv_access (on)`从上面的示例中，请注意，输出不同由于编译器执行编译时计算，这个过程未使用的控件模式。

```cpp
// pragma_directive_fenv_access_2.cpp
// compile with: /O2
#include <stdio.h>
#include <float.h>

int main() {
   double z, b = 0.1, t = 0.1;
   unsigned int currentControl;
   errno_t err;

   err = _controlfp_s(&currentControl, _PC_24, _MCW_PC);
   if (err != 0) {
      printf_s("The function _controlfp_s failed!\n");
      return -1;
   }
   z = b * t;
   printf_s ("out=%.15e\n",z);
}
```

```Output
out=1.000000000000000e-002
```

## <a name="see-also"></a>请参阅

[Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
