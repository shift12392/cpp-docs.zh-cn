---
title: 类型转换 (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- conversions, type
- type conversion
- converting types
- integral promotions
- type casts, when performed
ms.assetid: d130ee7c-03c3-48f4-af7b-1fdba0d3b086
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e06da627d18fa643cb64fda870c986264c573641
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="type-conversions-c"></a>类型转换 (C)
类型转换取决于指定的运算符以及操作数或运算符的类型。 下列情况下将执行类型转换：  
  
-   当将一个类型的值赋给其他类型的变量或运算符在执行运算前转换了其一个或多个操作数的类型时  
  
-   当一个类型的值显式强制转换为其他类型时  
  
-   当值作为参数传递给函数时，或当类型从函数返回时  
  
 字符、短整数或整数位域（无论带符号还是无符号）或枚举类型的对象均可在可使用整数的表达式中使用。 如果一个 `int` 可表示原始类型的所有值，则该值将转换为 `int`；否则，该值将转换为 `unsigned int`。 此过程称为“整型提升”。 整型提升将保留值。 即，保证提升后的值与提升前一样。 有关详细信息，请参阅[常用算术转换](../c-language/usual-arithmetic-conversions.md)。  
  
## <a name="see-also"></a>请参阅  
 [表达式和赋值](../c-language/expressions-and-assignments.md)