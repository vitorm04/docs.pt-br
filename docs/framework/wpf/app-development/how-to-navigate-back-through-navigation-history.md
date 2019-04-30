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
ms.openlocfilehash: c489a1593b3d1f22fe1ad6e648d3f8a3f7a6cd44
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947778"
---
# <a name="how-to-navigate-back-through-navigation-history"></a>Como: Navegar para trás por meio do histórico de navegação
Este exemplo ilustra como navegar até as entradas antigas no histórico de navegação.  
  
## <a name="example"></a>Exemplo  
 Código que está sendo executado do conteúdo que está hospedado em um <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame> usando <xref:System.Windows.Navigation.NavigationService>, ou [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)] pode navegar para trás no histórico de navegação, uma entrada por vez.  
  
 Navegação de volta uma entrada requer primeiro verificar se há entradas no histórico de navegação, inspecionando o **CanGoBack** propriedade, antes de navegar de volta uma entrada, chamando o **GoBack** método. Isso é ilustrado no exemplo a seguir:  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 **CanGoBack** e **GoBack** são implementadas pelo <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, e <xref:System.Windows.Navigation.NavigationService>.  
  
> [!NOTE]
>  Se você chamar **GoBack**, e não existem entradas no histórico de navegação, uma <xref:System.InvalidOperationException> é gerado.
