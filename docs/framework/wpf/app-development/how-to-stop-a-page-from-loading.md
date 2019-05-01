---
title: 'Como: Parar o carregamento de uma página'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pages [WPF], stopping from loading
- methods [WPF], Stoploading
- events [WPF], NavigationStopped
- NavigationStopped properties [WPF]
- stopping pages from loading [WPF]
- loading [WPF], stopping
ms.assetid: e2b695b0-517e-462c-8ccf-90cc8d6ba864
ms.openlocfilehash: c5694bb2cb6c618cd84bad3dc893ae3855e44892
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62006675"
---
# <a name="how-to-stop-a-page-from-loading"></a><span data-ttu-id="72730-102">Como: Parar o carregamento de uma página</span><span class="sxs-lookup"><span data-stu-id="72730-102">How to: Stop a Page from Loading</span></span>
<span data-ttu-id="72730-103">Este exemplo mostra como chamar o <xref:System.Windows.Navigation.NavigationWindow.StopLoading%2A> método parar a navegação para o conteúdo antes de concluir a que está sendo baixado.</span><span class="sxs-lookup"><span data-stu-id="72730-103">This example shows how to call the <xref:System.Windows.Navigation.NavigationWindow.StopLoading%2A> method to stop navigation to content before it has finished being downloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72730-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72730-104">Example</span></span>  
 <span data-ttu-id="72730-105"><xref:System.Windows.Navigation.NavigationWindow.StopLoading%2A> Interrompe o download do conteúdo solicitado e faz com que o <xref:System.Windows.Navigation.NavigationWindow.NavigationStopped> evento seja acionado.</span><span class="sxs-lookup"><span data-stu-id="72730-105"><xref:System.Windows.Navigation.NavigationWindow.StopLoading%2A> stops the download of the requested content, and causes the <xref:System.Windows.Navigation.NavigationWindow.NavigationStopped> event to be raised.</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateStopLoadingCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigatestoploadingcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateStopLoadingCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigatestoploadingcode)]
