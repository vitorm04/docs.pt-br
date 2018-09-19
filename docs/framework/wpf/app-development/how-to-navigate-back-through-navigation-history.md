---
title: 'Como: navegar para trás no histórico de navegação'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- history [WPF], navigating back
- navigation [WPF], through navigation history (back)
ms.assetid: 9343234b-d864-441d-b8a7-d895cba80a87
ms.openlocfilehash: 7266c9486524e962a859c34c9be5ab8f6d7bf7d5
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46322227"
---
# <a name="how-to-navigate-back-through-navigation-history"></a><span data-ttu-id="669a7-102">Como: navegar para trás no histórico de navegação</span><span class="sxs-lookup"><span data-stu-id="669a7-102">How to: Navigate Back Through Navigation History</span></span>
<span data-ttu-id="669a7-103">Este exemplo ilustra como navegar até as entradas antigas no histórico de navegação.</span><span class="sxs-lookup"><span data-stu-id="669a7-103">This example illustrates how to navigate to entries in back navigation history.</span></span>  
  
## <a name="example"></a><span data-ttu-id="669a7-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669a7-104">Example</span></span>  
 <span data-ttu-id="669a7-105">Código que está sendo executado do conteúdo que está hospedado em um <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame> usando <xref:System.Windows.Navigation.NavigationService>, ou [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)] pode navegar para trás no histórico de navegação, uma entrada por vez.</span><span class="sxs-lookup"><span data-stu-id="669a7-105">Code that is running from content that is hosted in a <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame> using <xref:System.Windows.Navigation.NavigationService>, or [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)] can navigate back through navigation history, one entry at a time.</span></span>  
  
 <span data-ttu-id="669a7-106">Navegação de volta uma entrada requer primeiro verificar se há entradas no histórico de navegação, inspecionando o **CanGoBack** propriedade, antes de navegar de volta uma entrada, chamando o **GoBack** método.</span><span class="sxs-lookup"><span data-stu-id="669a7-106">Navigating back one entry requires first checking that there are entries in back navigation history, by inspecting the **CanGoBack** property, before navigating back one entry, by calling the **GoBack** method.</span></span> <span data-ttu-id="669a7-107">Isso é ilustrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="669a7-107">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 <span data-ttu-id="669a7-108">**CanGoBack** e **GoBack** são implementadas pelo <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, e <xref:System.Windows.Navigation.NavigationService>.</span><span class="sxs-lookup"><span data-stu-id="669a7-108">**CanGoBack** and **GoBack** are implemented by <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, and <xref:System.Windows.Navigation.NavigationService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="669a7-109">Se você chamar **GoBack**, e não existem entradas no histórico de navegação, uma <xref:System.InvalidOperationException> é gerado.</span><span class="sxs-lookup"><span data-stu-id="669a7-109">If you call **GoBack**, and there are no entries in back navigation history, an <xref:System.InvalidOperationException> is raised.</span></span>
