---
title: 'Como: Navegar para a página'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pages [WPF], navigating to
- navigation [WPF], to page
ms.assetid: 2a556fc0-748b-417f-a58a-0d05a7afb66f
ms.openlocfilehash: 38814268c9bb271ad3d88d549fb6ec4c6cbfed40
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966035"
---
# <a name="how-to-navigate-to-a-page"></a><span data-ttu-id="fabf5-102">Como: Navegar para a página</span><span class="sxs-lookup"><span data-stu-id="fabf5-102">How to: Navigate to a Page</span></span>
<span data-ttu-id="fabf5-103">Este exemplo ilustra várias maneiras em que uma página pode ser navegada de um <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="fabf5-103">This example illustrates several ways in which a page can be navigated to from a <xref:System.Windows.Navigation.NavigationWindow>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fabf5-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fabf5-104">Example</span></span>  
 <span data-ttu-id="fabf5-105">É possível <xref:System.Windows.Navigation.NavigationWindow> navegar para uma página usando uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="fabf5-105">It is possible for a <xref:System.Windows.Navigation.NavigationWindow> to navigate to a page using one of the following:</span></span>  
  
- <span data-ttu-id="fabf5-106">A propriedade de <xref:System.Windows.Navigation.NavigationWindow.Source%2A> .</span><span class="sxs-lookup"><span data-stu-id="fabf5-106">The <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property.</span></span>  
  
- <span data-ttu-id="fabf5-107">O método <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A>.</span><span class="sxs-lookup"><span data-stu-id="fabf5-107">The <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A> method.</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateToPageCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigatetopagecode)]
 [!code-vb[HOWTONavigationSnippets#NavigateToPageCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigatetopagecode)]  
  
> [!NOTE]
> [!INCLUDE[TLA#tla_uri#initcap#plural](../../../../includes/tlasharptla-urisharpinitcapsharpplural-md.md)]<span data-ttu-id="fabf5-108">pode ser relativo ou absoluto.</span><span class="sxs-lookup"><span data-stu-id="fabf5-108">can be either relative or absolute.</span></span> <span data-ttu-id="fabf5-109">Para obter mais informações, consulte [URIs "pack://" no WPF](pack-uris-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="fabf5-109">For more information, see [Pack URIs in WPF](pack-uris-in-wpf.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fabf5-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fabf5-110">See also</span></span>

- <xref:System.Windows.Controls.Frame>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.NavigationService>
