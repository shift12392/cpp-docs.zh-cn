---
title: "硬件异常 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "错误 [C++], 硬件"
  - "错误 [C++], 低级别"
  - "异常, 硬件"
  - "硬件异常"
  - "低级别错误"
ms.assetid: 06ac6f01-a8cf-4426-bb12-1688315ae1cd
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 硬件异常
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

操作系统识别的大多数标准异常是硬件上定义的异常。  Windows 可识别少数低级别的软件异常，但这些异常通常最好通过操作系统进行处理。  
  
 Windows 将不同处理器的硬件错误映射到本节中的异常代码。  在某些情况下，处理器可能只生成这些异常中的一部分。  Windows 对异常的相关信息进行预处理并发布相应的异常代码。  
  
 Windows 识别的硬件异常在下表中进行了汇总：  
  
|异常代码|异常的原因|  
|----------|-----------|  
|**STATUS\_ACCESS\_VIOLATION**|读取或写入不可访问的内存位置。|  
|**STATUS\_BREAKPOINT**|遇到硬件定义的断点；仅由调试器使用。|  
|**STATUS\_DATATYPE\_MISALIGNMENT**|在没有正确对齐的地址上读取或写入数据；例如，16 位实体必须在 2 字节边界对齐。（不适用于 Intel 80 *x* 86 处理器。）|  
|**STATUS\_FLOAT\_DIVIDE\_BY\_ZERO**|将浮点类型除以 0.0。|  
|**STATUS\_FLOAT\_OVERFLOW**|超过浮点类型的最大正指数。|  
|**STATUS\_FLOAT\_UNDERFLOW**|超过浮点类型的最小负指数的大小。|  
|**STATUS\_FLOATING\_RESEVERED\_OPERAND**|使用保留的浮点格式（无效的使用格式）。|  
|**STATUS\_ILLEGAL\_INSTRUCTION**|尝试执行处理器未定义的指令代码。|  
|**STATUS\_PRIVILEGED\_INSTRUCTION**|执行当前计算机模式下不允许的指令。|  
|**STATUS\_INTEGER\_DIVIDE\_BY\_ZERO**|将整数类型除以 0。|  
|**STATUS\_INTEGER\_OVERFLOW**|尝试超出整数的范围的操作。|  
|**STATUS\_SINGLE\_STEP**|以单步模式执行一条指令；仅由调试器使用。|  
  
 上表中列出的很多异常应由调试器、操作系统或其他低级别代码处理。  您的代码不应处理这些错误（整数和浮点错误除外）。  因此，您通常应使用异常处理筛选器来忽略异常（计算结果为 0）。  否则，您可能阻止低级别机制进行适当的响应。  但是，您可以通过[编写终止处理程序](../cpp/writing-a-termination-handler.md)，采取适当的预防措施来消除这些低级别错误的潜在影响。  
  
## 请参阅  
 [编写异常处理程序](../cpp/writing-an-exception-handler.md)   
 [结构化异常处理](../cpp/structured-exception-handling-c-cpp.md)