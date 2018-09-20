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
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46492101"
---
# <a name="how-to-navigate-back-through-navigation-history"></a>Como: navegar para trás no histórico de navegação
Este exemplo ilustra como navegar até as entradas antigas no histórico de navegação.  
  
## <a name="example"></a>Exemplo  
 Código que está sendo executado do conteúdo que está hospedado em um <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame> usando <xref:System.Windows.Navigation.NavigationService>, ou [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)] pode navegar para trás no histórico de navegação, uma entrada por vez.  
  
 Navegação de volta uma entrada requer primeiro verificar se há entradas no histórico de navegação, inspecionando o **CanGoBack** propriedade, antes de navegar de volta uma entrada, chamando o **GoBack** método. Isso é ilustrado no exemplo a seguir:  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 **CanGoBack** e **GoBack** são implementadas pelo <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, e <xref:System.Windows.Navigation.NavigationService>.  
  
> [!NOTE]
>  Se você chamar **GoBack**, e não existem entradas no histórico de navegação, uma <xref:System.InvalidOperationException> é gerado.
