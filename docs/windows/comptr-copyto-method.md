---
title: 'Comptr:: Copyto 方法 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::CopyTo
dev_langs:
- C++
helpviewer_keywords:
- CopyTo method
ms.assetid: 8801bc49-6db4-4393-a55f-a701ae3b8718
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 680c1278ca2b17c7ea35e72946fb5d5030c5e7c0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="comptrcopyto-method"></a>ComPtr::CopyTo 方法
副本与指定的指针到此 ComPtr 关联的当前或指定的接口。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT CopyTo(  
   _Deref_out_ InterfaceType** ptr  
);  
  
HRESULT CopyTo(  
   REFIID riid,  
   _Deref_out_ void** ptr  
) const;  

template<typename U>  
HRESULT CopyTo(  
   _Deref_out_ U** ptr  
) const;  
```  
  
#### <a name="parameters"></a>参数  
 `U`  
 类型名称。  
  
 `ptr`  
 此操作完成后，指向所请求的接口的指针。  
  
 `riid`  
 接口 ID。  
  
## <a name="return-value"></a>返回值  
 如果成功，则则为 S_OK否则为指示隐式 QueryInterface 操作失败的原因的 HRESULT。  
  
## <a name="remarks"></a>备注  
 第一个函数返回与此 ComPtr 关联的接口的指针的副本。 此函数始终返回，则为 S_OK。  
  
 第二个函数执行上与指定的接口此 ComPtr 关联的接口的 QueryInterface 操作`riid`参数。  
  
 第三个函数将执行与此 ComPtr 的基础接口关联的接口 QueryInterface 操作`U`参数。  
  
## <a name="requirements"></a>要求  
 **标头：** client.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [ComPtr 类](../windows/comptr-class.md)