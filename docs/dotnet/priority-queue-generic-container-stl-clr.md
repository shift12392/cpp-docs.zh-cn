---
title: priority_queue::generic_container (STL/CLR) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::priority_queue::generic_container
dev_langs:
- C++
helpviewer_keywords:
- generic_container member [STL/CLR]
ms.assetid: b938c433-7ef1-4077-93c2-2aee8ddf4d67
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1e1f13b8775a7ce53e634a53b0a5abe72396a869
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="priorityqueuegenericcontainer-stlclr"></a>priority_queue::generic_container (STL/CLR)
容器的泛型接口的类型。  
  
## <a name="syntax"></a>语法  
  
```  
typedef Microsoft::VisualC::StlClr::IPriorityQueue<Value>  
    generic_container;  
```  
  
## <a name="remarks"></a>备注  
 该类型描述此模板容器适配器类的泛型接口。  
  
## <a name="example"></a>示例  
  
```  
// cliext_priority_queue_generic_container.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Mypriority_queue::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1->get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    gc1->push(L'd');   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify original and display generic   
    c1.push(L'e');   
    for each (wchar_t elem in gc1->get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c a b  
c a b  
d c b a  
e d b a c  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/队列 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)