---
title: _BitScanReverse、 _BitScanReverse64 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _BitScanReverse64
- _BitScanReverse_cpp
- _BitScanReverse
- _BitScanReverse64_cpp
dev_langs:
- C++
helpviewer_keywords:
- bsr instruction
- _BitScanReverse intrinsic
- BitScanReverse intrinsic
ms.assetid: 2520a207-af8b-4aad-9ae7-831abeadf376
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 35d51f3e7eaf0daeca006ff669398c9a3727a098
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="bitscanreverse-bitscanreverse64"></a>_BitScanReverse、_BitScanReverse64
**Microsoft 专用**  
  
 从设置位 (1) 的最高有效位 (MSB) 到最低有效位 (LSB) 搜索掩码数据。  
  
## <a name="syntax"></a>语法  
  
```  
unsigned char _BitScanReverse(  
   unsigned long * Index,  
   unsigned long Mask  
);  
unsigned char _BitScanReverse64(  
   unsigned long * Index,  
   unsigned __int64 Mask  
);  
```  
  
#### <a name="parameters"></a>参数  
 [out] `Index`  
 已使用找到的第一个设置位 (1) 的位位置加载。  
  
 [in] `Mask`  
 要搜索的 32 位或 64 位值。  
  
## <a name="return-value"></a>返回值  
 如果设定 `Index`，则为非零，如果未发现设置位，则为 0。  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|Header|  
|---------------|------------------|------------|  
|`_BitScanReverse`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h>|  
|`_BitScanReverse64`|ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]||  
  
## <a name="example"></a>示例  
  
```  
// BitScanReverse.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(_BitScanReverse)  
  
int main()  
{  
   unsigned long mask = 0x1000;  
   unsigned long index;  
   unsigned char isNonzero;  
  
   cout << "Enter a positive integer as the mask: " << flush;  
   cin >> mask;  
   isNonzero = _BitScanReverse(&index, mask);  
   if (isNonzero)  
   {  
      cout << "Mask: " << mask << " Index: " << index << endl;  
   }  
   else  
   {  
      cout << "No set bits found.  Mask is zero." << endl;  
   }  
}  
```  
  
## <a name="input"></a>输入  
  
```  
12  
```  
  
## <a name="sample-output"></a>示例输出  
  
```  
Enter a positive integer as the mask:   
Mask: 12 Index: 3  
```  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)