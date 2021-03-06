---
title: IID_PPV_ARGS_Helper 函数 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/IID_PPV_ARGS_Helper
dev_langs:
- C++
helpviewer_keywords:
- IID_PPV_ARGS_Helper function
ms.assetid: afee9b23-8df1-4575-903f-e9ba748418f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0cef979ae284a303b120df7d14ae71f311498423
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="iidppvargshelper-function"></a>IID_PPV_ARGS_Helper 函数
验证指定的参数的类型派生自`IUnknown`接口。  
  
> [!IMPORTANT]
>  此模板专用化支持 WRL 基础结构，不宜在代码中直接使用。 使用[IID_PPV_ARGS](http://msdn.microsoft.com/library/windows/desktop/ee330727.aspx)相反。  
  
## <a name="syntax"></a>语法  
  
```  
template<typename T>  
void** IID_PPV_ARGS_Helper(  
   _Inout_ Microsoft::WRL::Details::ComPtrRef<T> pp  
);  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 自变量的类型`pp`。  
  
 `pp`  
 双向间接指针。  
  
## <a name="return-value"></a>返回值  
 自变量`pp`强制转换为指针-到-a-指向的指针`void`。  
  
## <a name="remarks"></a>备注  
 如果将生成编译时错误的模板参数`T`不派生自`IUnknown`。  
  
## <a name="requirements"></a>要求  
 **标头：** client.h  
  
## <a name="see-also"></a>请参阅  
 [参考 （Windows 运行时库）](http://msdn.microsoft.com/en-us/00000000-0000-0000-0000-000000000000)