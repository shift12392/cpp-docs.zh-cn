---
title: xor | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- Xor
- std::xor
- std.xor
dev_langs:
- C++
helpviewer_keywords:
- xor function
ms.assetid: 0fe9554b-d87b-4487-92ed-366c6dc21df2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc5b3eb831a3d325b054ca3cca51f943631aafbf
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="xor"></a>xor

^ 运算符的替代项。

## <a name="syntax"></a>语法

```C

#define xor ^

```

## <a name="remarks"></a>备注

该宏产生运算符 ^。

## <a name="example"></a>示例

```cpp
// iso646_xor.cpp
// compile with: /EHsc
#include <iostream>
#include <iso646.h>

int main( )
{
   using namespace std;
   int a = 3, b = 2, result;

   result= a ^ b;
   cout << result << endl;

   result= a xor_eq b;
   cout << result << endl;
}
```

```Output
1
1
```

## <a name="requirements"></a>要求

**标头：** \<iso646.h>