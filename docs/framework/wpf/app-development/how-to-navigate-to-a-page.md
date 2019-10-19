---
title: Como navegar para uma página
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pages [WPF], navigating to
- navigation [WPF], to page
ms.assetid: 2a556fc0-748b-417f-a58a-0d05a7afb66f
ms.openlocfilehash: 25a0dbbc609c7b6f8f2878d2068e61e492a59c7e
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582535"
---
# <a name="how-to-navigate-to-a-page"></a><span data-ttu-id="73d3d-102">Como navegar para uma página</span><span class="sxs-lookup"><span data-stu-id="73d3d-102">How to: Navigate to a Page</span></span>
<span data-ttu-id="73d3d-103">Este exemplo ilustra várias maneiras em que uma página pode ser navegada de um <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="73d3d-103">This example illustrates several ways in which a page can be navigated to from a <xref:System.Windows.Navigation.NavigationWindow>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73d3d-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="73d3d-104">Example</span></span>  
 <span data-ttu-id="73d3d-105">É possível que um <xref:System.Windows.Navigation.NavigationWindow> navegue para uma página usando uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="73d3d-105">It is possible for a <xref:System.Windows.Navigation.NavigationWindow> to navigate to a page using one of the following:</span></span>  
  
- <span data-ttu-id="73d3d-106">A propriedade de <xref:System.Windows.Navigation.NavigationWindow.Source%2A> .</span><span class="sxs-lookup"><span data-stu-id="73d3d-106">The <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property.</span></span>  
  
- <span data-ttu-id="73d3d-107">O método <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A>.</span><span class="sxs-lookup"><span data-stu-id="73d3d-107">The <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A> method.</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateToPageCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigatetopagecode)]
 [!code-vb[HOWTONavigationSnippets#NavigateToPageCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigatetopagecode)]  
  
> [!NOTE]
> <span data-ttu-id="73d3d-108">Os URIs (identificadores de recursos uniformes) podem ser relativos ou absolutos.</span><span class="sxs-lookup"><span data-stu-id="73d3d-108">Uniform resource identifiers (URIs) can be either relative or absolute.</span></span> <span data-ttu-id="73d3d-109">Para obter mais informações, consulte [URIs "pack://" no WPF](pack-uris-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="73d3d-109">For more information, see [Pack URIs in WPF](pack-uris-in-wpf.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73d3d-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73d3d-110">See also</span></span>

- <xref:System.Windows.Controls.Frame>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.NavigationService>
