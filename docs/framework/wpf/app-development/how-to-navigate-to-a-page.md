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
ms.openlocfilehash: c8e808180682bfd97f397d8cadd1e4deafd7eb06
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59141044"
---
# <a name="how-to-navigate-to-a-page"></a><span data-ttu-id="5e8cd-102">Como: Navegar para a página</span><span class="sxs-lookup"><span data-stu-id="5e8cd-102">How to: Navigate to a Page</span></span>
<span data-ttu-id="5e8cd-103">Este exemplo ilustra várias maneiras em que uma página pode ser acessada de um <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="5e8cd-103">This example illustrates several ways in which a page can be navigated to from a <xref:System.Windows.Navigation.NavigationWindow>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e8cd-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5e8cd-104">Example</span></span>  
 <span data-ttu-id="5e8cd-105">É possível que um <xref:System.Windows.Navigation.NavigationWindow> para navegar até uma página usando um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="5e8cd-105">It is possible for a <xref:System.Windows.Navigation.NavigationWindow> to navigate to a page using one of the following:</span></span>  
  
-   <span data-ttu-id="5e8cd-106">A propriedade de <xref:System.Windows.Navigation.NavigationWindow.Source%2A> .</span><span class="sxs-lookup"><span data-stu-id="5e8cd-106">The <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property.</span></span>  
  
-   <span data-ttu-id="5e8cd-107">O método <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A>.</span><span class="sxs-lookup"><span data-stu-id="5e8cd-107">The <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A> method.</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateToPageCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigatetopagecode)]
 [!code-vb[HOWTONavigationSnippets#NavigateToPageCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigatetopagecode)]  
  
> [!NOTE]
>  [!INCLUDE[TLA#tla_uri#initcap#plural](../../../../includes/tlasharptla-urisharpinitcapsharpplural-md.md)] <span data-ttu-id="5e8cd-108">pode ser relativo ou absoluto.</span><span class="sxs-lookup"><span data-stu-id="5e8cd-108">can be either relative or absolute.</span></span> <span data-ttu-id="5e8cd-109">Para obter mais informações, consulte [URIs "pack://" no WPF](pack-uris-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="5e8cd-109">For more information, see [Pack URIs in WPF](pack-uris-in-wpf.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e8cd-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e8cd-110">See also</span></span>

- <xref:System.Windows.Controls.Frame>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.NavigationService>
