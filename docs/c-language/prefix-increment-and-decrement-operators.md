---
title: "前缀增量和减量运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "减量运算符"
  - "减量运算符, 语法"
  - "增量运算符, 类型"
ms.assetid: 9a441bb9-d94a-4b6a-9db2-0d0d76bc480d
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 前缀增量和减量运算符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当递增或递减运算符出现在操作数的前面时，一元运算符（`++` 和 **––**）称作“前缀”递增或递减运算符。  与前缀递增和递减相比，后缀递增和递减的优先级更高。  操作数必须具有整型、浮点型或指针类型且必须是可修改的左值表达式（不带 **const** 特性的表达式）。  结果为一个左值。  
  
 当运算符出现在其操作数的前面时，操作数会递增或递减，并且其新值为表达式的结果。  
  
 整型或浮动类型的操作数将按整数值 1 递增或递减。  结果的类型与操作数类型相同。  指针类型的操作数将按其所寻址对象的大小递增或递减。  递增的指针将指向下一个对象；递减的指针将指向上一个对象。  
  
## 示例  
 此示例阐释一元前缀递减运算符：  
  
```  
if( line[--i] != '\n' )  
    return;  
```  
  
 在此示例中，变量 `i` 在用作 `line` 的下标之前是递减的。  
  
## 请参阅  
 [C 一元运算符](../c-language/c-unary-operators.md)