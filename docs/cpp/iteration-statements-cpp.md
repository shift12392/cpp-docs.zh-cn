---
title: 迭代语句 （C++） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- iteration statements
- loop structures, iteration statements
ms.assetid: bf6d75f7-ead2-426a-9c47-33847f59b8c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1973223d6aab44d4c5d8652111d3e6b8251676fb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="iteration-statements-c"></a>迭代语句 (C++)
根据一些循环终止条件，迭代语句会导致语句（或复合语句）被执行零次或多次。 当这些语句是复合语句时，它们的顺序执行，除非任一[中断](../cpp/break-statement-cpp.md)语句或[继续](../cpp/continue-statement-cpp.md)遇到语句。  
  
 C++ 提供四个迭代语句-[时](../cpp/while-statement-cpp.md)，[执行](../cpp/do-while-statement-cpp.md)，[为](../cpp/for-statement-cpp.md)，和[基于范围的 for](../cpp/range-based-for-statement-cpp.md)。 其中每个循环直到其终止表达式的计算结果为零 (false)，或使用强制执行循环终止**中断**语句。 下表汇总了这些语句及其操作；后面各节详细讨论了它们。  
  
### <a name="iteration-statements"></a>迭代语句  
  
|语句|计算位置|初始化|递增|  
|---------------|------------------|--------------------|---------------|  
|`while`|循环的顶部|否|否|  
|**do**|循环的底部|否|否|  
|**for**|循环的顶部|是|是|  
|**基于范围的 for**|循环的顶部|是|是|  
  
 迭代语句的语句部分不能为声明。 但是，它可以是包含声明的复合语句。  
  
## <a name="see-also"></a>请参阅  
 [ 语句概述](../cpp/overview-of-cpp-statements.md)