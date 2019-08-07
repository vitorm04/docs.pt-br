---
title: 'Como: Navegar para frente ou para trás por meio do histórico de navegação'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- history [WPF], navigating forward
- navigation [WPF], through navigation history (forward)
ms.assetid: 5939d574-5f53-469e-85f5-1f2b13607caa
ms.openlocfilehash: 85d3562246170901d83d6314caec5747d52fb9a0
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/06/2019
ms.locfileid: "68817956"
---
# <a name="how-to-navigate-forward-or-back-through-navigation-history"></a><span data-ttu-id="d0ff4-102">Como: Navegar para frente ou para trás por meio do histórico de navegação</span><span class="sxs-lookup"><span data-stu-id="d0ff4-102">How to: Navigate Forward or Back Through Navigation History</span></span>
<span data-ttu-id="d0ff4-103">Este exemplo ilustra como navegar para frente ou para trás nas entradas no histórico de navegação.</span><span class="sxs-lookup"><span data-stu-id="d0ff4-103">This example illustrates how to navigate forward or back to entries in navigation history.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0ff4-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d0ff4-104">Example</span></span>  
 <span data-ttu-id="d0ff4-105">Código executado do conteúdo dos seguintes hosts pode navegar para frente ou para trás no histórico de navegação, uma entrada de cada vez.</span><span class="sxs-lookup"><span data-stu-id="d0ff4-105">Code that runs from content in the following hosts can navigate forward or back through navigation history, one entry at a time.</span></span>  
  
- <span data-ttu-id="d0ff4-106"><xref:System.Windows.Navigation.NavigationWindow>usando<xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="d0ff4-106"><xref:System.Windows.Navigation.NavigationWindow> using <xref:System.Windows.Navigation.NavigationService></span></span>  
  
- <span data-ttu-id="d0ff4-107"><xref:System.Windows.Controls.Frame>usando<xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="d0ff4-107"><xref:System.Windows.Controls.Frame> using <xref:System.Windows.Navigation.NavigationService></span></span>  
  
- <span data-ttu-id="d0ff4-108">Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="d0ff4-108">Internet Explorer</span></span>  
  
 <span data-ttu-id="d0ff4-109">Para poder navegar para frente em uma entrada, primeiro verifique se existem entradas no histórico de navegação progressiva inspecionando a propriedade **CanGoForward**.</span><span class="sxs-lookup"><span data-stu-id="d0ff4-109">Before you can navigate forward one entry, you must first check that there are entries in forward navigation history by inspecting the **CanGoForward** property.</span></span> <span data-ttu-id="d0ff4-110">Para navegar para frente em uma entrada, chame o método **GoForward**.</span><span class="sxs-lookup"><span data-stu-id="d0ff4-110">To navigate forward one entry, you call the **GoForward** method.</span></span> <span data-ttu-id="d0ff4-111">Isso é ilustrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="d0ff4-111">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigateforwardcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigateforwardcode)]  
  
 <span data-ttu-id="d0ff4-112">Para poder navegar para trás em uma entrada, primeiro verifique se há entradas no histórico de navegação de retorno inspecionando a propriedade **CanGoBack**.</span><span class="sxs-lookup"><span data-stu-id="d0ff4-112">Before you can navigate back one entry, you must first check that there are entries in back navigation history by inspecting the **CanGoBack** property.</span></span> <span data-ttu-id="d0ff4-113">Para navegar para trás em uma entrada, chame o método **GoBack**.</span><span class="sxs-lookup"><span data-stu-id="d0ff4-113">To navigate back one entry, you call the **GoBack** method.</span></span> <span data-ttu-id="d0ff4-114">Isso é ilustrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="d0ff4-114">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 <span data-ttu-id="d0ff4-115">**CanGoForward**, **GoForward**, CanGoBack e **GoBack** são implementados pelo <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>e. <xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="d0ff4-115">**CanGoForward**, **GoForward**, **CanGoBack**, and **GoBack** are implemented by <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, and <xref:System.Windows.Navigation.NavigationService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d0ff4-116">Se você chamar **GoForward**e não houver entradas no histórico de navegação progressiva, ou se você chamar **GoBack**, e não houver entradas no histórico de navegação de volta, um <xref:System.InvalidOperationException> será lançado.</span><span class="sxs-lookup"><span data-stu-id="d0ff4-116">If you call **GoForward**, and there are no entries in forward navigation history, or if you call **GoBack**, and there are no entries in back navigation history, an <xref:System.InvalidOperationException> is thrown.</span></span>
