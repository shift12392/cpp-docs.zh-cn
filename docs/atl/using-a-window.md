---
title: 使用窗口 (ATL) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ATL, windows
- CWindow class, about CWindow class
- windows [C++], ATL
ms.assetid: b3b9cc8e-4287-486b-b080-38852bc2943a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f946f99fd198db281418e2a471489b2236972435
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="using-a-window"></a>使用窗口
类[CWindow](../atl/reference/cwindow-class.md)允许你使用一个窗口。 将连接到的窗口后`CWindow`对象，然后，你可以调用`CWindow`操作窗口的方法。 `CWindow` 此外包含`HWND`运算符以转换`CWindow`对象传递给`HWND`。 因此可以传递`CWindow`向需要一个窗口的句柄的任何函数对象。 您可以轻松地混用`CWindow`的方法调用和 Win32 函数调用，而不创建任何临时对象。  
  
 因为`CWindow`有只有两个数据成员 （窗口句柄和的默认尺寸），它不会施加于你的代码的开销。 此外，许多`CWindow`方法只包装对应 Win32 API 函数。 通过使用`CWindow`、`HWND`成员将自动传递给 Win32 函数。  
  
 除了使用`CWindow`直接，你可以从它派生以将数据或代码添加到你的类。 ATL 本身派生三个类从`CWindow`: [CWindowImpl](../atl/implementing-a-window.md)， [CDialogImpl](../atl/implementing-a-dialog-box.md)，和[CContainedWindowT](../atl/using-contained-windows.md)。  
  
## <a name="see-also"></a>请参阅  
 [窗口类](../atl/atl-window-classes.md)

