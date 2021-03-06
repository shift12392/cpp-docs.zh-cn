---
title: BLOB_NAME_LENGTH_STATUS |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- BLOB_NAME_LENGTH_STATUS
dev_langs:
- C++
helpviewer_keywords:
- BLOB_NAME_LENGTH_STATUS macro
ms.assetid: 3cc3ec8d-80a5-4522-848a-123fcaee58cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9c819ecf270f7aee16f05b8e86bbacf01d658d22
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="blobnamelengthstatus"></a>BLOB_NAME_LENGTH_STATUS
与使用`BEGIN_COLUMN_MAP`和`END_COLUMN_MAP`要绑定的二进制大型对象 ([BLOB](https://msdn.microsoft.com/en-us/library/ms711511.aspx))。 类似于[BLOB_NAME](../../data/oledb/blob-name.md)，只不过此宏还可获取的长度和 BLOB 数据列的状态。  
  
## <a name="syntax"></a>语法  
  
```cpp
BLOB_NAME_LENGTH_STATUS(pszName, IID, flags, data, length  
, status )  
```  
  
#### <a name="parameters"></a>参数  
 `pszName`  
 [in]指向的列名称的指针。 名称必须是 Unicode 字符串。 你可以完成此操作通过将放在 L 的所有引用，例如： `L"MyColumn"`。  
  
 *IID*  
 [in]接口的 GUID，如**IDD_ISequentialStream**，可用来检索 BLOB。  
  
 `flags`  
 [in]定义由 OLE 结构化存储模型的存储模式标志 (例如， **STGM_READ**)。  
  
 `data`  
 [in] 用户记录中的对应数据成员。  
  
 *length*  
 [out]BLOB 列 （实际） 长度以字节为单位。  
  
 *status*  
 [out]BLOB 字段的状态。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [宏和全局函数 OLE DB 使用者模板](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)   
 [COLUMN_ENTRY](../../data/oledb/column-entry.md)   
 [BLOB_NAME](../../data/oledb/blob-name.md)   
 [BLOB_NAME_LENGTH](../../data/oledb/blob-name-length.md)   
 [BLOB_NAME_STATUS](../../data/oledb/blob-name-status.md)