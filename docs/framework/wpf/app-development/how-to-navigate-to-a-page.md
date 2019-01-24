---
title: 'Como: Navegue até uma página'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pages [WPF], navigating to
- navigation [WPF], to page
ms.assetid: 2a556fc0-748b-417f-a58a-0d05a7afb66f
ms.openlocfilehash: 7b76a12cbe6e1622e5624f5416abf24a4ca292a4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54536900"
---
# <a name="how-to-navigate-to-a-page"></a>Como: Navegue até uma página
Este exemplo ilustra várias maneiras em que uma página pode ser acessada de um <xref:System.Windows.Navigation.NavigationWindow>.  
  
## <a name="example"></a>Exemplo  
 É possível que um <xref:System.Windows.Navigation.NavigationWindow> para navegar até uma página usando um dos seguintes:  
  
-   A propriedade de <xref:System.Windows.Navigation.NavigationWindow.Source%2A> .  
  
-   O método <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A>.  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateToPageCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigatetopagecode)]
 [!code-vb[HOWTONavigationSnippets#NavigateToPageCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigatetopagecode)]  
  
> [!NOTE]
>  [!INCLUDE[TLA#tla_uri#initcap#plural](../../../../includes/tlasharptla-urisharpinitcapsharpplural-md.md)] pode ser relativo ou absoluto. Para obter mais informações, consulte [URIs "pack://" no WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md).  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Controls.Frame>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.NavigationService>
