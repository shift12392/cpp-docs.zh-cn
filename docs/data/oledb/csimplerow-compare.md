---
title: 'Csimplerow:: Compare |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CSimpleRow.Compare
- CSimpleRow::Compare
dev_langs:
- C++
helpviewer_keywords:
- Compare method
ms.assetid: 0bb65f09-c7bc-449b-aa4e-c828cac13510
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 75d79e753f1f4af630c26ef07fbb7241576535ce
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="csimplerowcompare"></a>CSimpleRow::Compare
比较两个行，以查看它们是否引用相同的行实例。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT Compare(CSimpleRow* pRow);  
```  
  
#### <a name="parameters"></a>参数  
 `pRow`  
 指向的指针`CSimpleRow`对象。  
  
## <a name="return-value"></a>返回值  
 `HRESULT`值，通常`S_OK`，，该值指示两个行相同的行实例，或**S_FALSE**，，用于指示两个行都不同。 请参阅[IRowsetIdentity::IsSameRow](https://msdn.microsoft.com/en-us/library/ms719629.aspx)中*OLE DB 程序员参考*有关其他可能的返回值。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [CSimpleRow 类](../../data/oledb/csimplerow-class.md)   
 [Csimplerow:: Releaserow](../../data/oledb/csimplerow-releaserow.md)   
 [IRowsetImpl::RefRows](../../data/oledb/irowsetimpl-refrows.md)