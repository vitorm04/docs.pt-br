---
title: Como obter e definir a janela principal do aplicativo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
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
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0d6bca158172fd3fc31526287c6d4a9928a8ea0c
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-get-and-set-the-main-application-window"></a>Como obter e definir a janela principal do aplicativo
Este exemplo mostra como obter e definir a janela principal do aplicativo.  
  
## <a name="example"></a>Exemplo  
 A primeira <xref:System.Windows.Window> instanciado em um [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] aplicativo é definido automaticamente pelo <xref:System.Windows.Application> como a janela principal do aplicativo. A primeira <xref:System.Windows.Window> para ser instanciado será provavelmente ser a janela que é especificada como a inicialização [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] (consulte <xref:System.Windows.Application.StartupUri%2A>).  
  
 A primeira <xref:System.Windows.Window> também pode ser instanciado usando o código. Um exemplo é abrir uma janela durante a inicialização do aplicativo, como o seguinte:  
  
 [!code-csharp[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/App.xaml.cs#firstwindowusingcodecodebehind)]
 [!code-vb[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/application.xaml.vb#firstwindowusingcodecodebehind)]  
  
 Às vezes, a primeira instanciado <xref:System.Windows.Window> é na verdade não a janela principal do aplicativo, por exemplo, uma tela inicial. Nesse caso, você pode especificar a janela principal do aplicativo usando marcação semelhante ao seguinte:  
  
 [!code-xaml[ApplicationMainWindowSnippets#SetApplicationMainWindowXAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/ApplicationMainWindowSnippets/XAML/App.xaml#setapplicationmainwindowxaml)]  
  
 Se a janela principal é especificada automaticamente ou manualmente, você pode obter a janela principal do <xref:System.Windows.Application.MainWindow%2A> usando o seguinte código, como o seguinte:  
  
 [!code-csharp[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationMainWindowSnippets/CSharp/App.xaml.cs#getapplicationmainwindowcode)]
 [!code-vb[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationMainWindowSnippets/visualbasic/application.xaml.vb#getapplicationmainwindowcode)]
