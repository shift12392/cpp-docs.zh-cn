---
title: CSimpleDialog 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSimpleDialog
- ATLWIN/ATL::CSimpleDialog
- ATLWIN/ATL::CSimpleDialog::DoModal
dev_langs:
- C++
helpviewer_keywords:
- CSimpleDialog class
- CSimpleDialog class, modal dialog boxes in ATL
- dialog boxes, modal
- modal dialog boxes, ATL
ms.assetid: 2ae65cc9-4f32-4168-aecd-200b4a480fdf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f3a8f6cb2ead8798b86d65a1fa875a42a68cdd77
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="csimpledialog-class"></a>CSimpleDialog 类
此类实现基本的模式对话框。  
  
## <a name="syntax"></a>语法  
  
```
template <WORD t_wDlgTemplateID, BOOL t_bCenter = TRUE>  
class CSimpleDialog : public CDialogImplBase
```  
  
#### <a name="parameters"></a>参数  
 *t_wDlgTemplateID*  
  
 对话框模板资源的资源 ID。  
  
 *t_bCenter*  
 **TRUE**对话框对象是否为中心的所有者窗口; 否则为**FALSE**。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CSimpleDialog::DoModal](#domodal)|创建模式对话框。|  
  
## <a name="remarks"></a>备注  
 实现模式对话框的基本功能。 `CSimpleDialog` 提供 Windows 公共控件仅支持。 若要创建和显示模式对话框，请创建此类，在对话框中提供现有的资源模板的名称的实例。 当用户单击与预定义的值 （如 IDOK 或 IDCANCEL） 的任何控件，将关闭对话框对象。  
  
 `CSimpleDialog` 可以创建仅有模式对话框。 `CSimpleDialog` 提供对话框过程，使用默认消息映射来将消息定向到相应的处理程序。  
  
 请参阅[实现对话框](../../atl/implementing-a-dialog-box.md)有关详细信息。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CDialogImplBase`  
  
 `CSimpleDialog`  
  
## <a name="requirements"></a>要求  
 **标头：** atlwin.h  
  
##  <a name="domodal"></a>  CSimpleDialog::DoModal  
 调用模式对话框并返回完成的对话框结果。  
  
```
INT_PTR DoModal(HWND hWndParent = ::GetActiveWindow());
```  
  
### <a name="parameters"></a>参数  
 `hWndParent`  
 对话框中的父句柄。 如果没有提供任何值，则会将父设置为当前的活动窗口。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回值是控件的关闭对话框中的资源 ID。  
  
 如果函数失败，返回值为-1。 若要获得扩展的错误信息，请调用 `GetLastError`。  
  
### <a name="remarks"></a>备注  
 对话框中处于活动状态时，此方法可处理所有与用户交互。 正是这使得对话框模式;也就是说，用户不能交互与其他窗口中，是关闭该对话框之前。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../../atl/atl-class-overview.md)
