---
title: 编译器错误 C2032 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2032
dev_langs:
- C++
helpviewer_keywords:
- C2032
ms.assetid: 625d7c83-70b6-42c2-a558-81fbc0026324
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1db268222f3b9f7ca6f9ce297680866185e6661d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2032"></a>编译器错误 C2032
identifier： 函数不能为结构/联合 structorunion 的成员  
  
 结构或联合具有成员函数时，这允许 c + + 中但不是在 c。若要解决此错误，请编译为 c + + 程序，或删除成员函数。  
  
 下面的示例生成 C2032:  
  
```  
// C2032.c  
struct z {  
   int i;  
   void func();   // C2032  
};  
```  
  
 可能的解决方法：  
  
```  
// C2032b.c  
// compile with: /c  
struct z {  
   int i;  
};  
```