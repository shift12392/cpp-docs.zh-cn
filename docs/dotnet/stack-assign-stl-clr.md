---
title: stack::assign (STL/CLR) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::stack::assign
dev_langs:
- C++
helpviewer_keywords:
- assign member [STL/CLR]
ms.assetid: 18cc35ad-23cf-4a5a-adae-d967dc5d6980
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 409e86e0ed11cd1e6cda2984105e3f23a629cd28
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="stackassign-stlclr"></a>stack::assign (STL/CLR)
替换所有元素。  
  
## <a name="syntax"></a>语法  
  
```  
void assign(stack<Value, Container>% right);  
```  
  
#### <a name="parameters"></a>参数  
 右  
 要插入的容器适配器。  
  
## <a name="remarks"></a>备注  
 成员函数将指派`right.get_container()`到基础的容器。 你可以使用它来更改堆栈的全部内容。  
  
## <a name="example"></a>示例  
  
```  
// cliext_stack_assign.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign a repetition of values   
    Mystack c2;   
    c2.assign(c1);   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/堆栈 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [堆栈 (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [stack::operator= (STL/CLR)](../dotnet/stack-operator-assign-stl-clr.md)