---
title: "Como navegar para frente ou para trás por meio do histórico de navegação"
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
- history [WPF], navigating forward
- navigation [WPF], through navigation history (forward)
ms.assetid: 5939d574-5f53-469e-85f5-1f2b13607caa
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7ad909af071d4006346d64ad8e4bd7b57c4eefad
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-navigate-forward-or-back-through-navigation-history"></a><span data-ttu-id="c93ed-102">Como navegar para frente ou para trás por meio do histórico de navegação</span><span class="sxs-lookup"><span data-stu-id="c93ed-102">How to: Navigate Forward or Back Through Navigation History</span></span>
<span data-ttu-id="c93ed-103">Este exemplo ilustra como navegar para frente ou para trás nas entradas no histórico de navegação.</span><span class="sxs-lookup"><span data-stu-id="c93ed-103">This example illustrates how to navigate forward or back to entries in navigation history.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c93ed-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c93ed-104">Example</span></span>  
 <span data-ttu-id="c93ed-105">Código executado do conteúdo dos seguintes hosts pode navegar para frente ou para trás no histórico de navegação, uma entrada de cada vez.</span><span class="sxs-lookup"><span data-stu-id="c93ed-105">Code that runs from content in the following hosts can navigate forward or back through navigation history, one entry at a time.</span></span>  
  
-   <span data-ttu-id="c93ed-106"><xref:System.Windows.Navigation.NavigationWindow>usando o<xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="c93ed-106"><xref:System.Windows.Navigation.NavigationWindow> using <xref:System.Windows.Navigation.NavigationService></span></span>  
  
-   <span data-ttu-id="c93ed-107"><xref:System.Windows.Controls.Frame>usando o<xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="c93ed-107"><xref:System.Windows.Controls.Frame> using <xref:System.Windows.Navigation.NavigationService></span></span>  
  
-   [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]  
  
 <span data-ttu-id="c93ed-108">Para poder navegar para frente em uma entrada, primeiro verifique se existem entradas no histórico de navegação progressiva inspecionando a propriedade **CanGoForward**.</span><span class="sxs-lookup"><span data-stu-id="c93ed-108">Before you can navigate forward one entry, you must first check that there are entries in forward navigation history by inspecting the **CanGoForward** property.</span></span> <span data-ttu-id="c93ed-109">Para navegar para frente em uma entrada, chame o método **GoForward**.</span><span class="sxs-lookup"><span data-stu-id="c93ed-109">To navigate forward one entry, you call the **GoForward** method.</span></span> <span data-ttu-id="c93ed-110">Isso é ilustrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="c93ed-110">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateForwardCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigateforwardcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateForwardCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigateforwardcode)]  
  
 <span data-ttu-id="c93ed-111">Para poder navegar para trás em uma entrada, primeiro verifique se há entradas no histórico de navegação de retorno inspecionando a propriedade **CanGoBack**.</span><span class="sxs-lookup"><span data-stu-id="c93ed-111">Before you can navigate back one entry, you must first check that there are entries in back navigation history by inspecting the **CanGoBack** property.</span></span> <span data-ttu-id="c93ed-112">Para navegar para trás em uma entrada, chame o método **GoBack**.</span><span class="sxs-lookup"><span data-stu-id="c93ed-112">To navigate back one entry, you call the **GoBack** method.</span></span> <span data-ttu-id="c93ed-113">Isso é ilustrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="c93ed-113">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 <span data-ttu-id="c93ed-114">**CanGoForward**, **GoForward**, **CanGoBack**, e **GoBack** são implementados por <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, e <xref:System.Windows.Navigation.NavigationService>.</span><span class="sxs-lookup"><span data-stu-id="c93ed-114">**CanGoForward**, **GoForward**, **CanGoBack**, and **GoBack** are implemented by <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, and <xref:System.Windows.Navigation.NavigationService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c93ed-115">Se você chamar **GoForward**, e não existem entradas no histórico de navegação de avanço, ou se você chamar **GoBack**, e não existem entradas no histórico de navegação, um <xref:System.InvalidOperationException> é gerada.</span><span class="sxs-lookup"><span data-stu-id="c93ed-115">If you call **GoForward**, and there are no entries in forward navigation history, or if you call **GoBack**, and there are no entries in back navigation history, an <xref:System.InvalidOperationException> is thrown.</span></span>
