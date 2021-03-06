---
title: 调节钮成员函数 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- spin button control, methods
- CSpinButtonCtrl class [MFC], methods
ms.assetid: a08a26fd-b803-4cbe-a509-395fa357d057
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 524863b816c62903cb610b57a6e3275bcdf6a3d6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="spin-button-member-functions"></a>调节钮成员函数
有几个成员函数可用于数值调节钮控件 ([CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md))。 使用这些函数可更改数值调节钮的以下特性。  
  
-   **加速**可以调整时同时用户按住箭头按钮位置更改的速率。 若要使用加速，请使用[SetAccel](../mfc/reference/cspinbuttonctrl-class.md#setaccel)和[GetAccel](../mfc/reference/cspinbuttonctrl-class.md#getaccel)成员函数。  
  
-   **基**可以更改用于显示合作者窗口的标题中的位置的基 （10 或 16）。 若要使用基，请使用[GetBase](../mfc/reference/cspinbuttonctrl-class.md#getbase)和[SetBase](../mfc/reference/cspinbuttonctrl-class.md#setbase)成员函数。  
  
-   **Buddy Window**可以动态设置合作者窗口。 若要查询或更改哪些控件合作者窗口，使用[GetBuddy](../mfc/reference/cspinbuttonctrl-class.md#getbuddy)和[SetBuddy](../mfc/reference/cspinbuttonctrl-class.md#setbuddy)成员函数。  
  
-   **位置**您可以查询和更改的位置。 若要直接使用位置，请使用[GetPos](../mfc/reference/cspinbuttonctrl-class.md#getpos)和[SetPos](../mfc/reference/cspinbuttonctrl-class.md#setpos)成员函数。 由于合作者控件的标题可能已更改（例如，在合作者是编辑控件的情况下），因此 `GetPos` 将检索当前标题并相应地调整位置。  
  
-   **范围**可以更改数值调节钮的最大和最小位置。 默认情况下，最大值设置为 0，最小值设置为 100。 由于默认最大值小于默认最小值，因此箭头按钮的操作是反直觉的。 通常，你会将设置范围使用[SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange)成员函数。 若要查询范围使用[GetRange](../mfc/reference/cspinbuttonctrl-class.md#getrange)。  
  
## <a name="see-also"></a>请参阅  
 [使用 CSpinButtonCtrl](../mfc/using-cspinbuttonctrl.md)   
 [控件](../mfc/controls-mfc.md)

