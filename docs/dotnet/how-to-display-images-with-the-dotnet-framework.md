---
title: 如何： 显示使用.NET Framework 的映像 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- GDI+ [C++], displaying images
- graphics [C++], displaying images
ms.assetid: c0eddfa1-4bd6-4af5-a533-1fa84b360325
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4a7f3ed2d8fe90501b5ef3d0ae5028890fe5290e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-display-images-with-the-net-framework"></a>如何：使用 .NET Framework 显示图像
下面的代码示例修改 OnPaint 事件处理程序来检索指向<xref:System.Drawing.Graphics>主窗体的对象。 <xref:System.Windows.Forms.Form.OnPaint%2A>函数适用于 Windows 窗体应用程序，最有可能创建了使用 Visual Studio 应用程序向导。  
  
 映像由<xref:System.Drawing.Image>类。 从.jpg 文件使用加载图像数据<xref:System.Drawing.Image.FromFile%2A?displayProperty=fullName>方法。 在窗体中绘制图像之前，窗体调整大小以容纳新映像。 使用执行绘制图像<xref:System.Drawing.Graphics.DrawImage%2A?displayProperty=fullName>方法。  
  
 <xref:System.Drawing.Graphics>和<xref:System.Drawing.Image>类都在<xref:System.Drawing?displayProperty=fullName>命名空间。  
  
## <a name="example"></a>示例  
  
```  
#using <system.drawing.dll>  
  
using namespace System;  
using namespace System::Drawing;  
  
protected:  
virtual Void Form1::OnPaint(PaintEventArgs^ pe) override  
{  
    Graphics^ g = pe->Graphics;  
    Image^ image = Image::FromFile("SampleImage.jpg");  
    Form::ClientSize = image->Size;  
    g->DrawImage( image, 0, 0, image->Size.Width, image->Size.Height );  
}  
```  
  
## <a name="see-also"></a>请参阅  
 <xref:System.Drawing?displayProperty=fullName>   
 [使用 C++/CLI (Visual C++) 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)