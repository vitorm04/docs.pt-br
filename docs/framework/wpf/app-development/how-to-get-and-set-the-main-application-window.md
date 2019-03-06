---
title: 'Como: Obter e definir a janela principal do aplicativo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- windows objects [WPF], setting
- setting windows objects [WPF]
- windows objects [WPF], getting
- getting windows objects [WPF]
ms.assetid: ec902bc4-4a59-46f5-8ec1-963b46789356
ms.openlocfilehash: ea8333aa82f1159afb438215940ee1e7c2605e96
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373550"
---
# <a name="how-to-get-and-set-the-main-application-window"></a><span data-ttu-id="65172-102">Como: Obter e definir a janela principal do aplicativo</span><span class="sxs-lookup"><span data-stu-id="65172-102">How to: Get and Set the Main Application Window</span></span>
<span data-ttu-id="65172-103">Este exemplo mostra como obter e definir a janela principal do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="65172-103">This example shows how to get and set the main application window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65172-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="65172-104">Example</span></span>  
 <span data-ttu-id="65172-105">A primeira <xref:System.Windows.Window> que é instanciado em um Windows Presentation Foundation (WPF) aplicativo é definido automaticamente pelo <xref:System.Windows.Application> como a janela principal do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="65172-105">The first <xref:System.Windows.Window> that is instantiated within a Windows Presentation Foundation (WPF) application is automatically set by <xref:System.Windows.Application> as the main application window.</span></span> <span data-ttu-id="65172-106">A primeira <xref:System.Windows.Window> ser instanciado provavelmente mais ser a janela que é especificada como o tipo de inicialização [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] (consulte <xref:System.Windows.Application.StartupUri%2A>).</span><span class="sxs-lookup"><span data-stu-id="65172-106">The first <xref:System.Windows.Window> to be instantiated will most likely be the window that is specified as the startup [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] (see <xref:System.Windows.Application.StartupUri%2A>).</span></span>  
  
 <span data-ttu-id="65172-107">A primeira <xref:System.Windows.Window> também pode ser instanciada usando código.</span><span class="sxs-lookup"><span data-stu-id="65172-107">The first <xref:System.Windows.Window> could also be instantiated using code.</span></span> <span data-ttu-id="65172-108">Um exemplo é abrir uma janela durante a inicialização do aplicativo, como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="65172-108">One example is opening a window during application startup, like the following:</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/App.xaml.cs#firstwindowusingcodecodebehind)]
 [!code-vb[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/application.xaml.vb#firstwindowusingcodecodebehind)]  
  
 <span data-ttu-id="65172-109">Às vezes, a primeira é instanciado <xref:System.Windows.Window> é, na verdade, não a janela principal do aplicativo, por exemplo, uma tela inicial.</span><span class="sxs-lookup"><span data-stu-id="65172-109">Sometimes, the first instantiated <xref:System.Windows.Window> is not actually the main application window e.g. a splash screen.</span></span> <span data-ttu-id="65172-110">Nesse caso, você pode especificar a janela principal do aplicativo usando marcação semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="65172-110">In this case, you can specify the main application window using markup, like the following:</span></span>  
  
 [!code-xaml[ApplicationMainWindowSnippets#SetApplicationMainWindowXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/ApplicationMainWindowSnippets/XAML/App.xaml#setapplicationmainwindowxaml)]  
  
 <span data-ttu-id="65172-111">Se a janela principal for especificada automática ou manualmente, você pode obter a janela principal do <xref:System.Windows.Application.MainWindow%2A> usando o seguinte código, semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="65172-111">Whether the main window is specified automatically or manually, you can get the main window from <xref:System.Windows.Application.MainWindow%2A> using the following code, like the following:</span></span>  
  
 [!code-csharp[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationMainWindowSnippets/CSharp/App.xaml.cs#getapplicationmainwindowcode)]
 [!code-vb[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationMainWindowSnippets/visualbasic/application.xaml.vb#getapplicationmainwindowcode)]
