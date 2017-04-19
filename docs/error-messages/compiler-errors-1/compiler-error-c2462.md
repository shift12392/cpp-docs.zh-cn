---
title: "编译器错误 C2462 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2462"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2462"
ms.assetid: a8601bf8-f5ce-41de-9117-e2632bd4996b
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C2462
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 不能在“new\-expression”中定义类型  
  
 不能在 `new` 运算符的操作数字段中定义类型。  请将类型定义放在单独的语句中。  
  
 下面的示例生成 C2462：  
  
```  
// C2462.cpp  
int main() {  
   new struct S { int i; };   // C2462  
}  
```