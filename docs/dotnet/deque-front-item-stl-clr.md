---
title: "deque::front_item (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::deque::front_item"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "front_item 成员 [STL/CLR]"
ms.assetid: 6243e52d-47fb-45d8-ade8-70debd97887d
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# deque::front_item (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

访问第一个元素。  
  
## 语法  
  
```  
property value_type front_item;  
```  
  
## 备注  
 属性访问第一个元素，该元素必须为非空元素。  如果您知道存在时，使用它读取或写入第一个元素。  
  
## 示例  
  
```  
// cliext_deque_front_item.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first item   
    System::Console::WriteLine("front_item = {0}", c1.front_item);   
  
// alter first item and reinspect   
    c1.front_item = L'x';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
**front\_item \= a**  
 **x b c**   
## 要求  
 **标头:** \<cliext\/deque\>  
  
 **Namespace:** cliext  
  
## 请参阅  
 [deque](../dotnet/deque-stl-clr.md)   
 [deque::back](../dotnet/deque-back-stl-clr.md)   
 [deque::back\_item](../dotnet/deque-back-item-stl-clr.md)   
 [deque::front](../dotnet/deque-front-stl-clr.md)