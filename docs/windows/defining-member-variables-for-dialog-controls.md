---
title: 为对话框控件定义成员变量 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- member variables, defining for controls
- variables, dialog box control member variables
- controls [C++], member variables
- Dialog editor, defining member variables for controls
ms.assetid: 84347c63-c33c-4b04-91f5-6d008c45ba58
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8ba8fc95290ecb90557203be2b6ab4cce18b91e3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="defining-member-variables-for-dialog-controls"></a>定义对话框控件的成员变量
要定义除按钮外的任何对话框控件的成员变量，可以使用以下方法。  
  
> [!NOTE]
>  本文仅适用于 MFC 项目中的对话框控件。 ATL 项目应使用**新的 Windows 消息和事件处理程序**对话框。  
  
### <a name="to-define-a-member-variable-for-a-non-button-dialog-box-control"></a>定义（非按钮）对话框控件的成员变量  
  
1.  在[对话框编辑器](../windows/dialog-editor.md)，选择一个控件。  
  
2.  时按**CTRL**密钥中，双击对话框控件。  
  
     [添加成员变量向导](../ide/add-member-variable-wizard.md)显示。  
  
3.  键入中的相应信息**添加成员变量**向导。 有关详细信息，请参阅[对话框数据交换](../mfc/dialog-data-exchange.md)。  
  
4.  单击**确定**以返回到对话框编辑器。  
  
    > [!TIP]
    >  若要从任何对话框控件跳转到其现有的处理程序，请双击该控件。  
  

  
 你还可以使用**成员变量**选项卡中**MFC 类向导**添加为指定类的新成员变量并查看已定义的那些。  
  
 要求  
  
 MFC  
  
## <a name="see-also"></a>请参阅  
 [将消息映射到函数](../mfc/reference/mapping-messages-to-functions.md)   
 [用代码向导添加功能](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [MFC 类向导](../mfc/reference/mfc-class-wizard.md)   
 [添加类](../ide/adding-a-class-visual-cpp.md)   
 [添加成员函数](../ide/adding-a-member-function-visual-cpp.md)   
 [添加成员变量](../ide/adding-a-member-variable-visual-cpp.md)   
 [重写虚函数](../ide/overriding-a-virtual-function-visual-cpp.md)   
 [MFC 消息处理程序](../mfc/reference/adding-an-mfc-message-handler.md)

