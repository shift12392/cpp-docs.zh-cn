---
title: CPtrList 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPtrList
dev_langs:
- C++
helpviewer_keywords:
- lists, generic
- CPtrList class [MFC]
- generic lists
ms.assetid: 4139a09c-4338-4f42-9eea-51336120b43c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1a143fd99a79212ed0078f06b334ab6ae0964b3f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="cptrlist-class"></a>CPtrList 类
支持 void 指针列表。  
  
## <a name="syntax"></a>语法  
  
```  
class CPtrList : public CObject  
```  
  
## <a name="members"></a>成员  
 成员函数的`CPtrList`类似于类的成员函数[CObList](../../mfc/reference/coblist-class.md)。 由于此相似性，因此你可以使用 `CObList` 参考文档获取成员函数细节。 无论您在何处找到作为函数参数的 `CObject` 或返回值，都将替换指向 `void` 的指针。  
  
 `CObject*& CObList::GetHead() const;`  
  
 例如，转换为  
  
 `void*& CPtrList::GetHead() const;`  
  
## <a name="remarks"></a>备注  
 `CPtrList` 合并 `IMPLEMENT_DYNAMIC` 宏来支持运行时类型访问和转储到 `CDumpContext` 对象。 如果需要单个指针列表元素的转储，则您必须将转储上下文的深度设为 1 或更大的值。  
  
 无法对指针列表进行序列化。  
  
 当删除 `CPtrList` 对象或其元素时，仅删除指针而不是指针引用的实体。  
  
 有关详细信息使用`CPtrList`，请参阅文章[集合](../../mfc/collections.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CPtrList`  
  
## <a name="requirements"></a>要求  
 **标头：** afxcoll.h  
  
## <a name="see-also"></a>请参阅  
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CObList 类](../../mfc/reference/coblist-class.md)
