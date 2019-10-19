---
title: Como obter e definir a janela principal do aplicativo
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
ms.openlocfilehash: 5894761c4b6258cbf90d369a722ffc5abca51885
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582552"
---
# <a name="how-to-get-and-set-the-main-application-window"></a>Como obter e definir a janela principal do aplicativo
Este exemplo mostra como obter e definir a janela principal do aplicativo.  
  
## <a name="example"></a>Exemplo  
 A primeira <xref:System.Windows.Window> instanciada em um aplicativo de Windows Presentation Foundation (WPF) é automaticamente definida pelo <xref:System.Windows.Application> como a janela principal do aplicativo. A primeira <xref:System.Windows.Window> a ser instanciada provavelmente será a janela especificada como o URI (Uniform Resource Identifier) de inicialização (consulte <xref:System.Windows.Application.StartupUri%2A>).  
  
 A primeira <xref:System.Windows.Window> também pode ser instanciada usando código. Um exemplo é abrir uma janela durante a inicialização do aplicativo, como o seguinte:  
  
 [!code-csharp[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/App.xaml.cs#firstwindowusingcodecodebehind)]
 [!code-vb[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/application.xaml.vb#firstwindowusingcodecodebehind)]  
  
 Às vezes, a primeira <xref:System.Windows.Window> instanciada não é, na verdade, a janela principal do aplicativo, por exemplo, uma tela inicial. Nesse caso, você pode especificar a janela principal do aplicativo usando marcação semelhante ao seguinte:  
  
 [!code-xaml[ApplicationMainWindowSnippets#SetApplicationMainWindowXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/ApplicationMainWindowSnippets/XAML/App.xaml#setapplicationmainwindowxaml)]  
  
 Se a janela principal for especificada automaticamente ou manualmente, você poderá obter a janela principal de <xref:System.Windows.Application.MainWindow%2A> usando o código a seguir, como o seguinte:  
  
 [!code-csharp[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationMainWindowSnippets/CSharp/App.xaml.cs#getapplicationmainwindowcode)]
 [!code-vb[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationMainWindowSnippets/visualbasic/application.xaml.vb#getapplicationmainwindowcode)]
