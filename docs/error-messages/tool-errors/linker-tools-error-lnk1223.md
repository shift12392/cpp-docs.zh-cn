---
title: 链接器工具错误 LNK1223 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1223
dev_langs:
- C++
helpviewer_keywords:
- LNK1223
ms.assetid: c4728c36-daee-462f-a1c7-8733dcdec88e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e50d29af6ac563fadd3a52e5b1d3d15201289083
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1223"></a>链接器工具错误 LNK1223
无效或已损坏的文件： 文件包含无效的.pdata 基值  
  
 对于使用 pdata 的 RISC 平台，如果编译器发出具有无序条目的 .pdata 部分，则将发生此错误。  
  
 若要解决此问题，请尝试编译而不[/GL （全程序优化）](../../error-messages/tool-errors/linker-tools-error-lnk1223.md)启用。 在某些情况下，空的函数体也可能导致此错误。