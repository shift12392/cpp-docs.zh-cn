---
title: 条件表达式运算符 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- conditional operators
- operators [C++], conditional
- expressions [C++], conditional
ms.assetid: c4f1a5ca-0844-44a7-a384-eca584d4e3dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3f3bead2a40e38698534e433d8e4289eb8da4dc9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="conditional-expression-operator"></a>条件表达式运算符
C 具有一个三元运算符：conditional-expression 运算符 (? :)。  
  
## <a name="syntax"></a>语法  
 *conditional-expression*:  
 *logical-OR-expression*  
  
 logical-OR expression  ?  *expression*  **:**  *conditional-expression*  
  
 logical-OR-expression 必须具有整型类型、浮点型或指针类型。 根据其等效性，其计算结果为 0。 序列点紧跟 logical-OR-expression。 操作数的计算将继续，如下所示：  
  
-   如果 logical-OR-expression 不等于 0，则计算 expression。 由非终止符 expression 给定的表达式的计算结果。 （这意味着，仅当 logical-OR-expression 为 true 时计算 expression。）  
  
-   如果 logical-OR-expression 等于 0，则计算 conditional-expression。 该表达式的结果是 conditional-expression 的值。 （这意味着，仅当 logical-OR-expression 为 false 时计算 conditional-expression。）  
  
 请注意，计算 expression 或 conditional-expression，但不同时计算二者。  
  
 条件运算的结果类型取决于 expression 或 conditional-expression 操作数的类型，如下所示：  
  
-   如果 expression 或 conditional-expression 具有整型类型或浮点型（其类型可不同），则运算符执行常用算术转换。 结果的类型是转换后操作数的类型。  
  
-   如果 expression 和 conditional-expression 都具有相同的结构、联合或指针类型，则结果的类型为相同的结构、联合或指针类型。  
  
-   如果两个操作数都具有类型 `void`，则结果具有类型 `void`。  
  
-   如果其中一个操作数是指向任何类型的对象的指针，且另一个操作数是指向 `void` 的指针，则指向对象的指针将转换为指向 `void` 的指针，而结果是指向 `void` 的指针。  
  
-   如果 expression 或 conditional-expression 是指针，且另一个操作数是具有值 0 的常量表达式，则结果的类型为指针类型。  
  
 在指针的类型比较中，指针指向的类型中的任何类型限定符（const 或 `volatile`）是无意义的，但结果类型从两个条件组件中继承限定符。  
  
## <a name="examples"></a>示例  
 下面的示例演示条件运算符的用法：  
  
```  
j = ( i < 0 ) ? ( -i ) : ( i );  
```  
  
 此示例将 `i` 的绝对值赋给 `j`。 如果 `i` 小于 0，则将 `-i` 赋给 `j`。 如果 `i` 大于或等于 0，则将 `i` 赋给 `j`。  
  
```  
void f1( void );  
void f2( void );  
int x;  
int y;  
    .  
    .  
    .  
( x == y ) ? ( f1() ) : ( f2() );  
```  
  
 在此示例中，声明两个函数（`f1` 和 `f2`）和两个变量（`x` 和 `y`）。 如果两个变量具有相同的值，则稍后在程序中将调用函数 `f1`。 否则，将调用 `f2`。  
  
## <a name="see-also"></a>请参阅  
 [条件运算符：? :](../cpp/conditional-operator-q.md)