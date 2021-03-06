---
title: 2.4.3 single 构造 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 15c180cd-e462-4b41-bf8c-cb8b1afb1a9b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: db3f9ca834fb3f35c95732698fd02e16f31b4225
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="243-single-construct"></a>2.4.3 single 构造
**单个**指令标识一个构造，用于指定关联的结构化的块只能由团队 （不一定的主线程） 中的一个线程执行。 语法**单个**指令是，如下所示：  
  
```  
#pragma omp single [clause[[,] clause] ...] new-linestructured-block  
```  
  
 子句是以下项之一：  
  
 **private(** *variable-list* **)**  
  
 **firstprivate(** *variable-list* **)**  
  
 **copyprivate (** *变量列表* **)**  
  
 **nowait**  
  
 没有隐式屏障后的**单个**构造，除非**nowait**指定子句。  
  
 限制到**单个**指令如下所示：  
  
-   只有一个**nowait**子句可以出现在**单个**指令。  
  
-   **Copyprivate**必须不能使用带有子句**nowait**子句。  
  
## <a name="cross-references"></a>交叉引用：  
  
-   **私有**， **firstprivate**，和**copyprivate**子句，请参阅[部分 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md)第 25 页上。