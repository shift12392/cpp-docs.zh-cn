---
title: 'Ierrorrecordsimpl:: Adderrorrecord |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IErrorRecordsImpl.AddErrorRecord
- AddErrorRecord
- IErrorRecordsImpl::AddErrorRecord
dev_langs:
- C++
helpviewer_keywords:
- AddErrorRecord method
ms.assetid: b5f8e9ae-509d-454f-b511-4bda7e972607
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bc60982a99b6c052d10ffe300efbfbcdde49d0fa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="ierrorrecordsimpladderrorrecord"></a>IErrorRecordsImpl::AddErrorRecord
将记录添加到 OLE DB 错误对象。  
  
## <a name="syntax"></a>语法  
  
```cpp
      STDMETHOD(AddErrorRecord )(ERRORINFO *pErrorInfo,  
   DWORD dwLookupID,  
   DISPPARAMS *pdispparams,  
   IUnknown *punkCustomError,  
   DWORD dwDynamicErrorID);  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[IErrorRecords::AddErrorRecord](https://msdn.microsoft.com/en-us/library/ms725362.aspx)中*OLE DB 程序员参考*。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [IErrorRecordsImpl 类](../../data/oledb/ierrorrecordsimpl-class.md)