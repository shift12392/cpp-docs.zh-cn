---
title: 资源编译器错误 RW1022 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RW1022
dev_langs:
- C++
helpviewer_keywords:
- RW1022
ms.assetid: 6747c8a9-9c9b-4422-b414-0645d22092d0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f57bb435d17cf1d539d558b5dead9c299f83494a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="resource-compiler-fatal-error-rw1022"></a>资源编译器错误 RW1022
**写入文件时出现 I/O 错误**  
  
 资源编译器无法写入文件。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复  
  
1.  磁盘空间不足。 可用空间必须等于正在创建的可执行文件的大小的至少两倍。  
  
2.  卷为只读。  
  
3.  坏扇区。  
  
4.  共享冲突。