---
title: 'Irowsetupdateimpl:: Getoriginaldata |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IRowsetUpdateImpl.GetOriginalData
- IRowsetUpdateImpl.GetOriginalData
- GetOriginalData
- ATL::IRowsetUpdateImpl::GetOriginalData
- IRowsetUpdateImpl::GetOriginalData
dev_langs:
- C++
helpviewer_keywords:
- GetOriginalData method
ms.assetid: 7477b3b7-6b1b-49a7-8167-b34323f0fdcc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3684b9e1b7e6998d47b37d0d1a03fc08182c6a28
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="irowsetupdateimplgetoriginaldata"></a>IRowsetUpdateImpl::GetOriginalData
获取最近传输到或从忽略挂起的更改的数据源中获取的数据。  
  
## <a name="syntax"></a>语法  
  
```cpp
      STDMETHOD (GetOriginalData )(HROW hRow,  
   HACCESSOR hAccessor,  
   void* pData);  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[IRowsetUpdate::GetOriginalData](https://msdn.microsoft.com/en-us/library/ms709947.aspx)中*OLE DB 程序员参考*。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [IRowsetUpdateImpl 类](../../data/oledb/irowsetupdateimpl-class.md)