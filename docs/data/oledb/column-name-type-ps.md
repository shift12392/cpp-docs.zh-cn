---
title: COLUMN_NAME_TYPE_PS |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- COLUMN_NAME_TYPE_PS
dev_langs:
- C++
helpviewer_keywords:
- COLUMN_NAME_TYPE_PS macro
ms.assetid: 99df7e33-47fc-48ec-ad03-5fd03a190aa9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 967a43d16de1914ad03b24bd83edf5233f5950b5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="columnnametypeps"></a>COLUMN_NAME_TYPE_PS
在行集中的特定列表示行集上的绑定。 类似于[COLUMN_NAME](../../data/oledb/column-name.md)，只不过此宏还采用数据类型、 精度和小数位数。  
  
## <a name="syntax"></a>语法  
  
```cpp
COLUMN_NAME_TYPE_PS(pszName, wType, nPrecision, nScale, data)  
  
```  
  
#### <a name="parameters"></a>参数  
 `pszName`  
 [in]指向的列名称的指针。 名称必须是 Unicode 字符串。 你可以完成此操作通过将放在 L 的所有引用，例如： `L"MyColumn"`。  
  
 `wType`  
 [in]数据类型。  
  
 `nPrecision`  
 [in]获取数据时要使用的最大精度和`wType`是`DBTYPE_NUMERIC`。 否则，将忽略此参数。  
  
 `nScale`  
 [in]要获取数据时使用的比例和`wType`是`DBTYPE_NUMERIC`或**DBTYPE_DECIMAL**。  
  
 `data`  
 [in] 用户记录中的对应数据成员。  
  
## <a name="remarks"></a>备注  
 请参阅[COLUMN_NAME](../../data/oledb/column-name.md)有关在何处信息**COLUMN_NAME_\*** 使用宏，则。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [宏和全局函数 OLE DB 使用者模板](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [COLUMN_NAME](../../data/oledb/column-name.md)   
 [COLUMN_NAME_EX](../../data/oledb/column-name-ex.md)   
 [COLUMN_NAME_LENGTH](../../data/oledb/column-name-length.md)   
 [COLUMN_NAME_LENGTH_STATUS](../../data/oledb/column-name-length-status.md)   
 [COLUMN_NAME_STATUS](../../data/oledb/column-name-status.md)   
 [COLUMN_NAME_PS](../../data/oledb/column-name-ps.md)   
 [COLUMN_NAME_PS_LENGTH](../../data/oledb/column-name-ps-length.md)   
 [COLUMN_NAME_PS_STATUS](../../data/oledb/column-name-ps-status.md)   
 [COLUMN_NAME_PS_LENGTH_STATUS](../../data/oledb/column-name-ps-length-status.md)   
 [COLUMN_NAME_TYPE](../../data/oledb/column-name-type.md)   
 [COLUMN_NAME_TYPE_SIZE](../../data/oledb/column-name-type-size.md)   
 [COLUMN_NAME_TYPE_STATUS](../../data/oledb/column-name-type-status.md)