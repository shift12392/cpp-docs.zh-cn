---
title: 编译器警告 （等级 4） C4238 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4238
dev_langs:
- C++
helpviewer_keywords:
- C4238
ms.assetid: 5d4051d3-7b0f-43ea-8c8d-d194bfdceb71
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 06dbec01da8d1b47cb7b93c90a22ae5266e9b4c8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4238"></a>编译器警告（等级 4）C4238
使用的非标准扩展： 类右值用作左值  
  
 与以前版本的 Visual c + +，Microsoft 扩展的兼容性 (**/Ze**) 允许你使用的类类型，如在上下文中的为右值的隐式或显式采用其地址。 在某些情况下，如以下示例中，这可能是危险。  
  
## <a name="example"></a>示例  
  
```  
// C4238.cpp  
// compile with: /W4 /c  
struct C {  
   C() {}  
};  
  
C * pC = &C();   // C4238  
```  
  
 这种用法会导致在 ANSI 兼容性错误 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。