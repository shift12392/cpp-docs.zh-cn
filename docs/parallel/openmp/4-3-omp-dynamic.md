---
title: 4.3 OMP_DYNAMIC |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a15edefb-1f85-4f06-a427-beb3cfc4434f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f376fe639d9bca58b6e2bd55fd081b88921a7342
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="43-ompdynamic"></a>4.3 OMP_DYNAMIC
**OMP_DYNAMIC**环境变量启用或禁用动态调整可用的并行区域执行的线程数，除非显式启用或禁用通过调用动态调整**omp_set_dynamic**库例程。 其值必须为**TRUE**或**FALSE**。  
  
 如果设置为**TRUE**，可能由运行时环境，以最大程度利用系统资源调整用于执行并行区域的线程数。  如果设置为**FALSE**，禁用动态调整。 默认条件是实现定义的。  
  
 示例:  
  
```  
setenv OMP_DYNAMIC TRUE  
```  
  
## <a name="cross-references"></a>交叉引用：  
  
-   并行区域的详细信息，请参阅[2.3 节](../../parallel/openmp/2-3-parallel-construct.md)第 8 页上。  
  
-   **omp_set_dynamic**函数中，请参阅[部分 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)页 39 上。