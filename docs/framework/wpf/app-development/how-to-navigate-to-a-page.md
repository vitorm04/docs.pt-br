---
title: 'Como: Navegar para a página'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pages [WPF], navigating to
- navigation [WPF], to page
ms.assetid: 2a556fc0-748b-417f-a58a-0d05a7afb66f
ms.openlocfilehash: 38814268c9bb271ad3d88d549fb6ec4c6cbfed40
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966035"
---
# <a name="how-to-navigate-to-a-page"></a>Como: Navegar para a página
Este exemplo ilustra várias maneiras em que uma página pode ser navegada de um <xref:System.Windows.Navigation.NavigationWindow>.  
  
## <a name="example"></a>Exemplo  
 É possível <xref:System.Windows.Navigation.NavigationWindow> navegar para uma página usando uma das seguintes opções:  
  
- A propriedade de <xref:System.Windows.Navigation.NavigationWindow.Source%2A> .  
  
- O método <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A>.  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateToPageCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigatetopagecode)]
 [!code-vb[HOWTONavigationSnippets#NavigateToPageCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigatetopagecode)]  
  
> [!NOTE]
> [!INCLUDE[TLA#tla_uri#initcap#plural](../../../../includes/tlasharptla-urisharpinitcapsharpplural-md.md)]pode ser relativo ou absoluto. Para obter mais informações, consulte [URIs "pack://" no WPF](pack-uris-in-wpf.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.Frame>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.NavigationService>
