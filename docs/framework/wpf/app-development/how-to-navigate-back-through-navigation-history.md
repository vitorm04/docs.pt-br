---
title: "Como: navegar para trás no histórico de navegação"
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
- history [WPF], navigating back
- navigation [WPF], through navigation history (back)
ms.assetid: 9343234b-d864-441d-b8a7-d895cba80a87
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9c715bda86fe6a4a010d80000db89619fc8bf8b7
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-navigate-back-through-navigation-history"></a>Como: navegar para trás no histórico de navegação
Este exemplo ilustra como navegar até as entradas antigas no histórico de navegação.  
  
## <a name="example"></a>Exemplo  
 Código que está em execução do conteúdo que está hospedado em um <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame> usar <xref:System.Windows.Navigation.NavigationService>, ou [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)] pode navegar para trás no histórico de navegação, uma entrada de cada vez.  
  
 Entrada de uma navegação requer primeiro verificar se há entradas no histórico de navegação, inspecionando o **CanGoBack** propriedade antes uma entrada, chamando o **GoBack** método. Isso é ilustrado no exemplo a seguir:  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 **CanGoBack** e **GoBack** são implementados por <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, e <xref:System.Windows.Navigation.NavigationService>.  
  
> [!NOTE]
>  Se você chamar **GoBack**, e não existem entradas no histórico de navegação, um <xref:System.InvalidOperationException> é gerado.
