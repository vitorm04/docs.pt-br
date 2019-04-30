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
ms.openlocfilehash: 4c20ebfab45a24cf34b1476fb94dae6913fb4d99
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947752"
---
# <a name="how-to-navigate-forward-or-back-through-navigation-history"></a><span data-ttu-id="62e99-102">Como: Navegar para frente ou para trás por meio do histórico de navegação</span><span class="sxs-lookup"><span data-stu-id="62e99-102">How to: Navigate Forward or Back Through Navigation History</span></span>
<span data-ttu-id="62e99-103">Este exemplo ilustra como navegar para frente ou para trás nas entradas no histórico de navegação.</span><span class="sxs-lookup"><span data-stu-id="62e99-103">This example illustrates how to navigate forward or back to entries in navigation history.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62e99-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="62e99-104">Example</span></span>  
 <span data-ttu-id="62e99-105">Código executado do conteúdo dos seguintes hosts pode navegar para frente ou para trás no histórico de navegação, uma entrada de cada vez.</span><span class="sxs-lookup"><span data-stu-id="62e99-105">Code that runs from content in the following hosts can navigate forward or back through navigation history, one entry at a time.</span></span>  
  
- <span data-ttu-id="62e99-106"><xref:System.Windows.Navigation.NavigationWindow> Usando o <xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="62e99-106"><xref:System.Windows.Navigation.NavigationWindow> using <xref:System.Windows.Navigation.NavigationService></span></span>  
  
- <span data-ttu-id="62e99-107"><xref:System.Windows.Controls.Frame> Usando o <xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="62e99-107"><xref:System.Windows.Controls.Frame> using <xref:System.Windows.Navigation.NavigationService></span></span>  
  
- [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]  
  
 <span data-ttu-id="62e99-108">Para poder navegar para frente em uma entrada, primeiro verifique se existem entradas no histórico de navegação progressiva inspecionando a propriedade **CanGoForward**.</span><span class="sxs-lookup"><span data-stu-id="62e99-108">Before you can navigate forward one entry, you must first check that there are entries in forward navigation history by inspecting the **CanGoForward** property.</span></span> <span data-ttu-id="62e99-109">Para navegar para frente em uma entrada, chame o método **GoForward**.</span><span class="sxs-lookup"><span data-stu-id="62e99-109">To navigate forward one entry, you call the **GoForward** method.</span></span> <span data-ttu-id="62e99-110">Isso é ilustrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="62e99-110">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigateforwardcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigateforwardcode)]  
  
 <span data-ttu-id="62e99-111">Para poder navegar para trás em uma entrada, primeiro verifique se há entradas no histórico de navegação de retorno inspecionando a propriedade **CanGoBack**.</span><span class="sxs-lookup"><span data-stu-id="62e99-111">Before you can navigate back one entry, you must first check that there are entries in back navigation history by inspecting the **CanGoBack** property.</span></span> <span data-ttu-id="62e99-112">Para navegar para trás em uma entrada, chame o método **GoBack**.</span><span class="sxs-lookup"><span data-stu-id="62e99-112">To navigate back one entry, you call the **GoBack** method.</span></span> <span data-ttu-id="62e99-113">Isso é ilustrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="62e99-113">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 <span data-ttu-id="62e99-114">**CanGoForward**, **GoForward**, **CanGoBack**, e **GoBack** são implementadas pelo <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, e <xref:System.Windows.Navigation.NavigationService>.</span><span class="sxs-lookup"><span data-stu-id="62e99-114">**CanGoForward**, **GoForward**, **CanGoBack**, and **GoBack** are implemented by <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, and <xref:System.Windows.Navigation.NavigationService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="62e99-115">Se você chamar **GoForward**, e não existem entradas no histórico de Navegação progressiva ou se você chamar **GoBack**, e não existem entradas no histórico de navegação, uma <xref:System.InvalidOperationException> é gerada.</span><span class="sxs-lookup"><span data-stu-id="62e99-115">If you call **GoForward**, and there are no entries in forward navigation history, or if you call **GoBack**, and there are no entries in back navigation history, an <xref:System.InvalidOperationException> is thrown.</span></span>
