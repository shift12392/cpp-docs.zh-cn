---
title: _FREEENTRY、_USEDENTRY | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- USEDENTRY
- _USEDENTRY
- _FREEENTRY
- FREEENTRY
dev_langs:
- C++
helpviewer_keywords:
- _USEDENTRY constant
- _FREEENTRY constant
- FREEENTRY constant
- USEDENTRY constant
ms.assetid: 26f658e6-6846-4a4e-9984-262cfe392770
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d75dbc61ae2c9b0c30217a782519ba4e826d2b98
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="freeentry-usedentry"></a>_FREEENTRY、_USEDENTRY
## <a name="syntax"></a>语法  
  
```  
#include <malloc.h>  
```  
  
## <a name="remarks"></a>备注  
 这些常量表示由 `_heapwalk` 例程分配给 _HEAPINFO 结构的 _useflag 元素的值。 它们指示堆条目的状态。  
  
## <a name="see-also"></a>请参阅  
 [_heapwalk](../c-runtime-library/reference/heapwalk.md)   
 [全局常量](../c-runtime-library/global-constants.md)