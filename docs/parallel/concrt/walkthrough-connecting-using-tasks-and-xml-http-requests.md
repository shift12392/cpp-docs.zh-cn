---
title: 演练： 使用任务和 XML HTTP 请求进行连接 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- connecting to web services, UWP apps [C++]
- IXMLHTTPRequest2 and tasks, example
- IXHR2 and tasks, example
ms.assetid: e8e12d46-604c-42a7-abfd-b1d1bb2ed6b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 411d52201aad69a94267615cd0a2acbe6376f64d
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="walkthrough-connecting-using-tasks-and-xml-http-requests"></a>演练：使用任务和 XML HTTP 请求进行连接
此示例演示如何使用[IXMLHTTPRequest2](http://msdn.microsoft.com/en-us/bbc11c4a-aecf-4d6d-8275-3e852e309908)和[IXMLHTTPRequest2Callback](http://msdn.microsoft.com/en-us/aa4b3f4c-6e28-458b-be25-6cce8865fc71)接口与任务以将 HTTP GET 和 POST 请求发送到 web 服务在通用 Windows 平台 (UWP) 应用程序。 通过将 `IXMLHTTPRequest2` 与任务组合在一起，您可以编写通过其他任务编写的代码。 例如，可以使用下载任务作为任务链的一部分。 工作取消时，下载任务也会响应。  
  
> [!TIP]
>  C + + REST SDK 还可用于执行 HTTP 请求，从 UWP 应用使用 c + + 应用程序或桌面 c + + 应用程序。 有关详细信息，请参阅[c + + REST SDK (Codename"Casablanca")](https://github.com/Microsoft/cpprestsdk)。  
  
 有关任务的详细信息，请参阅[任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)。 有关如何在 UWP 应用中使用任务的详细信息，请参阅[c + + 中的异步编程](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps)和[创建异步操作在 c + + 中适用于 UWP 应用](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)。  
  
 本文档首先演示如何创建 `HttpRequest` 及其支持类。 然后，它演示如何使用此类从使用 c + + 和 XAML 的 UWP 应用。  
  
 有关的更完整示例，使用`HttpReader`类描述在此文档中，请参阅[开发必应地图行程优化器，以 JavaScript 和 c + + Windows 应用商店应用](http://msdn.microsoft.com/library/974cf025-de1a-4299-b7dd-c6c7bf0e5d30)。 有关其他示例，使用`IXMLHTTPRequest2`但不使用任务，请参阅[快速入门： 使用 XML HTTP 请求 (IXMLHTTPRequest2) 进行连接](http://msdn.microsoft.com/en-us/cc7aed53-b2c5-4d83-b85d-cff2f5ba7b35)。  
  
> [!TIP]
>  `IXMLHTTPRequest2` 和`IXMLHTTPRequest2Callback`是我们建议在 UWP 应用中使用的接口。 还可以调整此示例，以用于桌面应用程序。  
  
## <a name="prerequisites"></a>系统必备  
  
## <a name="defining-the-httprequest-httprequestbufferscallback-and-httprequeststringcallback-classes"></a>定义 HttpRequest、HttpRequestBuffersCallback 和 HttpRequestStringCallback 类  
 当您使用 `IXMLHTTPRequest2` 接口通过 HTTP 创建 Web 请求时，可以实现 `IXMLHTTPRequest2Callback` 接口来接收服务器响应并对其他事件做出响应。 此示例定义了 `HttpRequest` 类来创建 Web 请求，并定义了 `HttpRequestBuffersCallback` 和 `HttpRequestStringCallback` 类来处理响应。 `HttpRequestBuffersCallback` 和 `HttpRequestStringCallback` 类支持 `HttpRequest` 类；在应用程序代码中您只能使用 `HttpRequest` 类。  
  
 `GetAsync` 类的 `PostAsync` 和 `HttpRequest` 方法可以使您分别启动 HTTP GET 和 POST 操作。 这些方法使用 `HttpRequestStringCallback` 类以便将服务器响应作为字符串读取。 `SendAsync` 和 `ReadAsync` 方法使您能够对区块中的大型内容进行流式处理。 这些方法均返回[concurrency:: task](../../parallel/concrt/reference/task-class.md)以表示操作。 `GetAsync` 和 `PostAsync` 方法将产生 `task<std::wstring>` 值，值中的 `wstring` 部分表示服务器的响应。 `SendAsync` 和 `ReadAsync` 方法将产生 `task<void>` 值；当发送和读取操作完成后这些任务将会完成。  
  
 因为`IXMLHTTPRequest2`接口是异步操作，此示例使用[concurrency:: task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md)创建回调对象完成或取消下载操作后完成的任务。 `HttpRequest` 类从此任务创建基于任务的延续以设置最终结果。 `HttpRequest` 类使用基于任务的延续来确保，即使在前面的任务产生错误或取消的情况下，延续任务也会运行。 有关基于任务的延续的详细信息，请参阅[任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)  
  
 若要支持取消，`HttpRequest`、`HttpRequestBuffersCallback` 和 `HttpRequestStringCallback` 类将使用取消标记。 `HttpRequestBuffersCallback`和`HttpRequestStringCallback`类使用[concurrency::cancellation_token::register_callback](reference/cancellation-token-class.md#register_callback)方法，以使任务完成事件能够响应取消。 此取消回调将中止下载。 有关取消的详细信息，请参阅[取消](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation)。  
  
#### <a name="to-define-the-httprequest-class"></a>定义 HttpRequest 类  
  
1.  使用 Visual c + +**空白应用 (XAML)** 模板来创建一个空白 XAML 应用程序项目。 此示例将项目命名为 `UsingIXMLHTTPRequest2`。  
  
2.  在项目中添加一个名为 HttpRequest.h 的标头文件和一个名为 HttpRequest.cpp 的源文件。  
  
3.  在 pch.h 中，添加此代码：  
  
     [!code-cpp[concrt-using-ixhr2#1](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_1.h)]  
  
4.  在 HttpRequest.h 中，添加此代码：  
  
     [!code-cpp[concrt-using-ixhr2#2](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_2.h)]  
  
5.  在 HttpRequest.cpp 中，添加此代码：  
  
     [!code-cpp[concrt-using-ixhr2#3](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_3.cpp)]  
  
## <a name="using-the-httprequest-class-in-a-uwp-app"></a>在 UWP 应用中使用 HttpRequest 类  
 本部分演示如何使用`HttpRequest`在 UWP 应用中的类。 应用程序会提供一个输入框，该输入框定义了一个 URL 资源、用于执行 GET 和 POST 操作的按钮命令和用于取消当前操作的按钮命令。  
  
#### <a name="to-use-the-httprequest-class"></a>使用 HttpRequest 类  
  
1.  在 MainPage.xaml 中，定义[StackPanel](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.stackpanel.aspx)元素，如下所示。  
  
     [!code-xml[concrt-using-ixhr2#A1](../../parallel/concrt/codesnippet/xaml/walkthrough-connecting-using-tasks-and-xml-http-requests_4.xaml)]  
  
2.  在 MainPage.xaml.h 中，添加此 `#include` 指令：  
  
     [!code-cpp[concrt-using-ixhr2#A2](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_5.h)]  
  
3.  在 MainPage.xaml.h 中，将这些 `private` 成员变量添加到 `MainPage` 类中：  
  
     [!code-cpp[concrt-using-ixhr2#A3](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_6.h)]  
  
4.  在 MainPage.xaml.h 中，声明 `private` 方法 `ProcessHttpRequest`：  
  
     [!code-cpp[concrt-using-ixhr2#A4](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_7.h)]  
  
5.  在 MainPage.xaml.cpp 中，添加这些 `using` 语句：  
  
     [!code-cpp[concrt-using-ixhr2#A5](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_8.cpp)]  
  
6.  在 MainPage.xaml.cpp 中，实现 `GetButton_Click` 类的 `PostButton_Click`、`CancelButton_Click` 和 `MainPage` 方法。  
  
     [!code-cpp[concrt-using-ixhr2#A6](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_9.cpp)]  
  
    > [!TIP]


    >  如果你的应用程序不需要取消支持，将传递[concurrency:: cancellation_token:: none](reference/cancellation-token-class.md#none)到`HttpRequest::GetAsync`和`HttpRequest::PostAsync`方法。  


  
7.  在 MainPage.xaml.cpp 中，实现 `MainPage::ProcessHttpRequest` 方法。  
  
     [!code-cpp[concrt-using-ixhr2#A7](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_10.cpp)]  
  
8.  在项目属性中，在**链接器**，**输入**，指定`shcore.lib`和`msxml6.lib`。  
  
 这是正在运行的应用程序：  
  
 ![正在运行的 Windows 运行时应用](../../parallel/concrt/media/concrt_usingixhr2.png "concrt_usingixhr2")  
  
## <a name="next-steps"></a>后续步骤  
 [并发运行时演练](../../parallel/concrt/concurrency-runtime-walkthroughs.md)  
  
## <a name="see-also"></a>请参阅  
 [任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [PPL 中的取消](cancellation-in-the-ppl.md)   
 [C + + 中的异步编程](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps)   
 [在为 UWP 应用的 c + + 中创建异步操作](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)   
 [快速入门： 使用 XML HTTP 请求 (IXMLHTTPRequest2) 进行连接](http://msdn.microsoft.com/en-us/cc7aed53-b2c5-4d83-b85d-cff2f5ba7b35)   
 [task 类 （并发运行时）](../../parallel/concrt/reference/task-class.md)   
 [task_completion_event 类](../../parallel/concrt/reference/task-completion-event-class.md)
