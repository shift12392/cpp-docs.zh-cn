---
title: 对 (STL/CLR) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::pair
dev_langs:
- C++
helpviewer_keywords:
- pair class [STL/CLR]
ms.assetid: 3326b4d9-a52a-49e5-8103-9aa5e8b352de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2d05dceaa763f8d0e33ccc86e783f66447c48b76
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="pair-stlclr"></a>pair (STL/CLR)
此模板类描述一个包装成对的值的对象。  
  
## <a name="syntax"></a>语法  
  
```  
template<typename Value1,  
    typename Value2>  
    ref class pair;  
```  
  
#### <a name="parameters"></a>参数  
 Value1  
 第一个已包装的值的类型。  
  
 Value2  
 第二个已包装的值的类型。  
  
## <a name="members"></a>成员  
  
|类型定义|描述|  
|---------------------|-----------------|  
|[pair::first_type (STL/CLR)](../dotnet/pair-first-type-stl-clr.md)|第一个包装值类型。|  
|[pair::second_type (STL/CLR)](../dotnet/pair-second-type-stl-clr.md)|已包装的第二个值的类型。|  
  
|成员对象|描述|  
|-------------------|-----------------|  
|[pair::first (STL/CLR)](../dotnet/pair-first-stl-clr.md)|第一个存储的值。|  
|[pair::second (STL/CLR)](../dotnet/pair-second-stl-clr.md)|第二个存储的值。|  
  
|成员函数|描述|  
|---------------------|-----------------|  
|[pair::pair (STL/CLR)](../dotnet/pair-pair-stl-clr.md)|构造 pair 对象。|  
|[pair::swap (STL/CLR)](../dotnet/pair-swap-stl-clr.md)|交换两个对的内容。|  
  
|运算符|描述|  
|--------------|-----------------|  
|[pair::operator= (STL/CLR)](../dotnet/pair-operator-assign-stl-clr.md)|替换存储的值对。|  
  
## <a name="remarks"></a>备注  
 此对象存储值的对。 你使用此模板类将两个值合并到单个对象。 请注意， `cliext::pair` （此处所述） 存储仅托管类型; 若要存储的成对的非托管类型，请使用`std::pair`中声明`<utility>`。  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/实用工具 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [make_pair (STL/CLR)](../dotnet/make-pair-stl-clr.md)