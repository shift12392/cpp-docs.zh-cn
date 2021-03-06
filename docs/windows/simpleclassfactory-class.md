---
title: SimpleClassFactory 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleClassFactory
dev_langs:
- C++
helpviewer_keywords:
- SimpleClassFactory class
ms.assetid: 6edda1b2-4e44-4e14-9364-72f519249962
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: debb78ba4be2731b8cffce1133518b0b4a04f63d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="simpleclassfactory-class"></a>SimpleClassFactory 类
提供创建基类的基本机制。  
  
## <a name="syntax"></a>语法  
  
```  
template<typename Base>  
class SimpleClassFactory : public ClassFactory<>;  
```  
  
#### <a name="parameters"></a>参数  
 `Base`  
 基类。  
  
## <a name="remarks"></a>备注  
 基类必须提供一个默认构造函数。  
  
 下面的代码示例演示如何使用与 SimpleClassFactory [ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md)宏。  
  
 `ActivatableClassWithFactoryEx(MyClass, SimpleClassFactory, MyServerName);`  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[SimpleClassFactory::CreateInstance 方法](../windows/simpleclassfactory-createinstance-method.md)|创建指定的接口的实例。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `I0`  
  
 `ChainInterfaces`  
  
 `I0`  
  
 `RuntimeClassBase`  
  
 `ImplementsHelper`  
  
 `DontUseNewUseMake`  
  
 `RuntimeClassFlags`  
  
 `RuntimeClassBaseT`  
  
 `RuntimeClass`  
  
 `ClassFactory`  
  
 `SimpleClassFactory`  
  
## <a name="requirements"></a>要求  
 **标头：** module.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)