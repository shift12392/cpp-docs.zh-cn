---
title: 更改签名 |Microsoft 文档
ms.custom: ''
ms.date: 11/16/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: 8daaa060-7305-4035-99d2-8b460b4f4454
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4f913f0b3065b136f626ef15cc2a77dce8d0254f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="change-signature"></a>更改签名
**新增功能：**可让你修改函数的参数。

**何时：**你想要重新排序、 添加、 删除或修改当前正在使用中的不同位置的函数的参数。  

**原因：**但你无法手动更改这些参数你自己，然后查找对该函数的所有调用，并更改它们一个由一，可能导致错误。  此重构工具可自动执行此任务。

方法：

1. 将文本或鼠标光标置于要修改的方法或其用法之一的名称：

   ![突出显示的代码](images/changesignature_highlight.png)

1. 接下来，执行以下操作之一：
   * **键盘**
     * 按**Ctrl + R**，然后**Ctrl + O**。  （请注意，键盘快捷方式可能因所选的配置文件而有所不同。）
     * 按“Ctrl+.” 向触发器**快速操作和重构**菜单，然后选择**更改签名**从上下文菜单。
   * **鼠标**
     * 选择“编辑 > 重构 > 重新排列参数”。
     * 右键单击代码中，选择**快速操作和重构**菜单，然后选择**更改签名**从上下文菜单。

1. 在弹出的“更改签名”对话框中，可以使用右侧的按钮更改方法签名：

   ![“更改签名”对话框](images/changesignature_dialog.png)

   | Button | 描述
   | ------ | ---
   | 上移/下移    | 在列表中向上和向下移动所选的参数
   | **添加**        | 将新参数添加到列表
   | **移除**     | 从列表删除所选的参数
   | **修改**     | 通过更改其类型，来修改所选的参数名称和可选的它是否以及其插入的值将为
   | **还原**     | 还原其原始状态的所选的参数
   | **还原所有** | 还原到其原始状态的所有参数

   > [!TIP]
   > 使用**如果确认所有引用更改时，跳过预览引用**复选框以使所做的更改立即没有首先弹出的预览窗口。

   当添加或修改参数，你将看到**添加参数**或**编辑参数**窗口。

   ![添加/修改参数](images/changesignature_addmodify.png)

   在这里，你可以执行以下操作：

   | 条目 | 描述
   | ----- | ---
   | **Type**               | 参数的类型 (int、 double、 float 等。)
   | **名称**               | 参数的名称
   | **可选参数** | 使 （可选） 指定的参数
   | **插入的值**     | 插入到任何调用函数未指定参数的值 (仅对有效**添加**)
   | **默认值**      | 如果调用方不指定一个使用该函数的值 (仅对有效**可选参数**)

1. 使用**搜索作用域**下拉框来选择如果所做的更改将应用于整个解决方案或项目。

1. 完成后，按“确定”按钮进行更改。  请确保相应地进行您请求的更改。  使用在窗口的上半复选框启用或禁用任何项重命名。

   ![更改签名预览](images/changesignature_preview.png)

1. 当一切看上去正常时，则单击**应用**按钮，该函数将更改在你的源代码。

   ![“更改签名”的结果](images/changesignature_result.png)