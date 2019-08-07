---
title: 'Como: Navegar para trás por meio do histórico de navegação'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- history [WPF], navigating back
- navigation [WPF], through navigation history (back)
ms.assetid: 9343234b-d864-441d-b8a7-d895cba80a87
ms.openlocfilehash: 86590c2794339ac22cbc8ec5e11224736133e870
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/06/2019
ms.locfileid: "68817971"
---
# <a name="how-to-navigate-back-through-navigation-history"></a><span data-ttu-id="254c8-102">Como: Navegar para trás por meio do histórico de navegação</span><span class="sxs-lookup"><span data-stu-id="254c8-102">How to: Navigate Back Through Navigation History</span></span>
<span data-ttu-id="254c8-103">Este exemplo ilustra como navegar para entradas no histórico de navegação de volta.</span><span class="sxs-lookup"><span data-stu-id="254c8-103">This example illustrates how to navigate to entries in back navigation history.</span></span>  
  
## <a name="example"></a><span data-ttu-id="254c8-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="254c8-104">Example</span></span>  
 <span data-ttu-id="254c8-105">O código que está sendo executado do conteúdo que é hospedado <xref:System.Windows.Navigation.NavigationWindow>em <xref:System.Windows.Controls.Frame> um <xref:System.Windows.Navigation.NavigationService>, usando o ou o Internet Explorer pode navegar de volta pelo histórico de navegação, uma entrada de cada vez.</span><span class="sxs-lookup"><span data-stu-id="254c8-105">Code that is running from content that is hosted in a <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame> using <xref:System.Windows.Navigation.NavigationService>, or Internet Explorer can navigate back through navigation history, one entry at a time.</span></span>  
  
 <span data-ttu-id="254c8-106">A navegação de volta de uma entrada requer primeiro verificar se há entradas no histórico de navegação voltar, inspecionando a propriedade **CanGoBack** , antes de navegar de volta em uma entrada, chamando o método **GoBack** .</span><span class="sxs-lookup"><span data-stu-id="254c8-106">Navigating back one entry requires first checking that there are entries in back navigation history, by inspecting the **CanGoBack** property, before navigating back one entry, by calling the **GoBack** method.</span></span> <span data-ttu-id="254c8-107">Isso é ilustrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="254c8-107">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 <span data-ttu-id="254c8-108">**CanGoBack** e **GoBack** são implementados <xref:System.Windows.Navigation.NavigationWindow>pelo <xref:System.Windows.Controls.Frame>, e <xref:System.Windows.Navigation.NavigationService>.</span><span class="sxs-lookup"><span data-stu-id="254c8-108">**CanGoBack** and **GoBack** are implemented by <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, and <xref:System.Windows.Navigation.NavigationService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="254c8-109">Se você chamar o **GoBack**e não houver entradas no histórico de navegação voltar, um <xref:System.InvalidOperationException> será gerado.</span><span class="sxs-lookup"><span data-stu-id="254c8-109">If you call **GoBack**, and there are no entries in back navigation history, an <xref:System.InvalidOperationException> is raised.</span></span>
