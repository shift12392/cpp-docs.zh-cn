---
title: "编译器错误 C2228 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2228
dev_langs:
- C++
helpviewer_keywords:
- C2228
ms.assetid: 901cadb1-ce90-4ae0-a360-547a9ba2ca18
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 39bbed326de5fc0a367e9b7693d3975b766e9bfc
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c2228"></a>编译器错误 C2228
“.identifier”的左边必须有类/结构/联合  
  
 句点 （.） 左侧的操作数不是类、 结构或联合。  
  
 下面的示例生成 C2228：  
  
```  
// C2228.cpp  
int i;  
struct S {  
public:  
    int member;  
} s, *ps = &s;  
  
int main() {  
   i.member = 0;   // C2228 i is not a class type  
   ps.member = 0;  // C2228 ps is a pointer to a structure  
  
   s.member = 0;   // s is a structure type  
   ps->member = 0; // ps points to a structure S  
}  
```  
  
 如果在使用托管扩展时用了不正确的语法，也会看到此错误。 而在其他 Visual Studio 语言中，可以使用点运算符访问托管类的成员，指向 C++ 中对象的指针意味着你需要使用 -> 运算符来访问该成员:  
  
 错误︰`String * myString = checkedListBox1->CheckedItems->Item[0].ToString();`  
  
 权限︰`String * myString = checkedListBox1->CheckedItems->Item[0]->ToString();`