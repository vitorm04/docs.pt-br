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
ms.openlocfilehash: 53b32e145390d7052262042c7a793699c163b373
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969349"
---
# <a name="how-to-navigate-back-through-navigation-history"></a>Como: Navegar para trás por meio do histórico de navegação
Este exemplo ilustra como navegar para entradas no histórico de navegação de volta.  
  
## <a name="example"></a>Exemplo  
 O código que está sendo executado do conteúdo que é hospedado <xref:System.Windows.Navigation.NavigationWindow>em <xref:System.Windows.Controls.Frame> um <xref:System.Windows.Navigation.NavigationService>, usando o ou o Internet Explorer pode navegar de volta pelo histórico de navegação, uma entrada de cada vez.  
  
 A navegação de volta de uma entrada requer primeiro verificar se há entradas no histórico de navegação voltar, inspecionando a propriedade **CanGoBack** , antes de navegar de volta em uma entrada, chamando o método **GoBack** . Isso é ilustrado no exemplo a seguir:  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 **CanGoBack** e **GoBack** são implementados <xref:System.Windows.Navigation.NavigationWindow>pelo <xref:System.Windows.Controls.Frame>, e <xref:System.Windows.Navigation.NavigationService>.  
  
> [!NOTE]
> Se você chamar o **GoBack**e não houver entradas no histórico de navegação voltar, um <xref:System.InvalidOperationException> será gerado.
