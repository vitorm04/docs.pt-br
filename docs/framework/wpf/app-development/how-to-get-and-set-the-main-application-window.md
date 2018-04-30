---
title: Como obter e definir a janela principal do aplicativo
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- windows objects [WPF], setting
- setting windows objects [WPF]
- windows objects [WPF], getting
- getting windows objects [WPF]
ms.assetid: ec902bc4-4a59-46f5-8ec1-963b46789356
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9bdc96c509f88650edd93ba4a7f595e2b161db39
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-get-and-set-the-main-application-window"></a><span data-ttu-id="c6eed-102">Como obter e definir a janela principal do aplicativo</span><span class="sxs-lookup"><span data-stu-id="c6eed-102">How to: Get and Set the Main Application Window</span></span>
<span data-ttu-id="c6eed-103">Este exemplo mostra como obter e definir a janela principal do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c6eed-103">This example shows how to get and set the main application window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6eed-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c6eed-104">Example</span></span>  
 <span data-ttu-id="c6eed-105">A primeira <xref:System.Windows.Window> instanciado em um WPF Windows Presentation Foundation () aplicativo é definido automaticamente pelo <xref:System.Windows.Application> como a janela principal do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c6eed-105">The first <xref:System.Windows.Window> that is instantiated within a Windows Presentation Foundation (WPF) application is automatically set by <xref:System.Windows.Application> as the main application window.</span></span> <span data-ttu-id="c6eed-106">A primeira <xref:System.Windows.Window> para ser instanciado será provavelmente ser a janela que é especificada como a inicialização [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] (consulte <xref:System.Windows.Application.StartupUri%2A>).</span><span class="sxs-lookup"><span data-stu-id="c6eed-106">The first <xref:System.Windows.Window> to be instantiated will most likely be the window that is specified as the startup [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] (see <xref:System.Windows.Application.StartupUri%2A>).</span></span>  
  
 <span data-ttu-id="c6eed-107">A primeira <xref:System.Windows.Window> também pode ser instanciado usando o código.</span><span class="sxs-lookup"><span data-stu-id="c6eed-107">The first <xref:System.Windows.Window> could also be instantiated using code.</span></span> <span data-ttu-id="c6eed-108">Um exemplo é abrir uma janela durante a inicialização do aplicativo, como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c6eed-108">One example is opening a window during application startup, like the following:</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/App.xaml.cs#firstwindowusingcodecodebehind)]
 [!code-vb[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/application.xaml.vb#firstwindowusingcodecodebehind)]  
  
 <span data-ttu-id="c6eed-109">Às vezes, a primeira instanciado <xref:System.Windows.Window> é na verdade não a janela principal do aplicativo, por exemplo, uma tela inicial.</span><span class="sxs-lookup"><span data-stu-id="c6eed-109">Sometimes, the first instantiated <xref:System.Windows.Window> is not actually the main application window e.g. a splash screen.</span></span> <span data-ttu-id="c6eed-110">Nesse caso, você pode especificar a janela principal do aplicativo usando marcação semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="c6eed-110">In this case, you can specify the main application window using markup, like the following:</span></span>  
  
 [!code-xaml[ApplicationMainWindowSnippets#SetApplicationMainWindowXAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/ApplicationMainWindowSnippets/XAML/App.xaml#setapplicationmainwindowxaml)]  
  
 <span data-ttu-id="c6eed-111">Se a janela principal é especificada automaticamente ou manualmente, você pode obter a janela principal do <xref:System.Windows.Application.MainWindow%2A> usando o seguinte código, como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c6eed-111">Whether the main window is specified automatically or manually, you can get the main window from <xref:System.Windows.Application.MainWindow%2A> using the following code, like the following:</span></span>  
  
 [!code-csharp[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationMainWindowSnippets/CSharp/App.xaml.cs#getapplicationmainwindowcode)]
 [!code-vb[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationMainWindowSnippets/visualbasic/application.xaml.vb#getapplicationmainwindowcode)]
