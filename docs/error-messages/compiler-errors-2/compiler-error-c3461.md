---
title: 编译器错误 C3461 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3461
dev_langs:
- C++
helpviewer_keywords:
- C3461
ms.assetid: bd66833a-545d-445a-bdfe-dee771a450a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a0b9349ed9450c6d74a9311d5b9265f57cc37b81
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3461"></a>编译器错误 C3461
“type”：仅可转发托管类型  
  
 类型转发只会在 CLR 类型上发生。  请参阅[类和结构](../../windows/classes-and-structs-cpp-component-extensions.md)有关详细信息。  
  
 有关详细信息，请参阅[类型转发 (C + + /cli CLI)](../../windows/type-forwarding-cpp-cli.md)。  
  
## <a name="example"></a>示例  
 下面的示例创建一个组件。  
  
```  
// C3461.cpp  
// compile with: /clr /LD  
public ref class R {};  
```  
  
## <a name="example"></a>示例  
 下面的示例生成 C3461。  
  
```  
// C3461b.cpp  
// compile with: /clr /c  
#using "C3461.dll"  
class N {};  
[assembly:TypeForwardedTo(N::typeid)];   // C3461  
[assembly:TypeForwardedTo(R::typeid)];   // OK  
```