---
title: Edit 控件中丰富的剪贴板操作 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- pasting Clipboard data
- CRichEditCtrl class [MFC], paste operation
- cut operation in CRichEditCtrl class [MFC]
- CRichEditCtrl class [MFC], Clipboard operations
- copy operations in rich edit controls
- Clipboard, operations in CRichEditCtrl
- rich edit controls [MFC], Clipboard operations
ms.assetid: 15ce66bc-2636-4a35-a2ae-d52285dc1af6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e831a76a491d1025ae45117d40362a85523742da
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="clipboard-operations-in-rich-edit-controls"></a>Rich Edit 控件中的剪贴板操作
你的应用程序可以将剪贴板内容粘贴到 rich edit 控件 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) 使用最佳可用的剪贴板格式或特定剪贴板格式。 您还可以确定格式文本编辑控件是否能粘贴剪贴板格式。  
  
 你可以复制或剪切当前所选内容的内容通过使用[复制](../mfc/reference/cricheditctrl-class.md#copy)或[剪切](../mfc/reference/cricheditctrl-class.md#cut)成员函数。 同样，你可以将粘贴剪贴板的内容到 rich edit 控件通过使用[粘贴](../mfc/reference/cricheditctrl-class.md#paste)成员函数。 该控件将粘贴它识别的第一种可用格式，该格式可能是最具描述性的格式。  
  
 若要粘贴特定剪贴板格式，可以使用[PasteSpecial](../mfc/reference/cricheditctrl-class.md#pastespecial)成员函数。 此函数对使用“选择性粘贴”命令（使用户能够选择剪贴板格式）的应用程序特别有用。 你可以使用[CanPaste](../mfc/reference/cricheditctrl-class.md#canpaste)成员函数来确定控件是否可识别给定的格式。  
  
 您还可使用 `CanPaste` 确定格式文本编辑控件是否可识别任何可用剪贴板格式。 此函数在 `OnInitMenuPopup` 处理程序中很有用。 应用程序可能启用或灰显“粘贴”命令，这取决于控件能否粘贴任何可用格式。  
  
 文本格式编辑控件将注册两种剪贴板格式：RTF 格式和称为“RichEdit 文本和对象”的格式。 应用程序可以通过使用注册这些格式[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)函数，指定**CF_RTF**和**CF_RETEXTOBJ**值。  
  
## <a name="see-also"></a>请参阅  
 [使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [控件](../mfc/controls-mfc.md)

