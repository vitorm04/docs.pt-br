---
title: Como enumerar fontes de sistema
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], enumerating system fonts
- fonts [WPF], enumerating
- system fonts [WPF], enumerating
- enumerating [WPF], system fonts
ms.assetid: 36e37791-55b9-4f01-a496-5cc10335e6a6
ms.openlocfilehash: 7fc996a2d3ba7042fce70afc20be5d64042c2b63
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543749"
---
# <a name="how-to-enumerate-system-fonts"></a>Como enumerar fontes de sistema
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como enumerar as fontes na coleção de fontes de sistema. O nome de família de fonte de cada <xref:System.Windows.Media.FontFamily> em <xref:System.Windows.Media.Fonts.SystemFontFamilies%2A> é adicionado como um item de caixa de combinação.  
  
 [!code-csharp[TextOverview#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextOverview/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextOverview#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextOverview/visualbasic/window1.xaml.vb#100)]  
  
 Se múltiplas versões da mesma família de fonte residir no mesmo diretório, o [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] enumeração de fonte retorna a versão mais recente da fonte. Se as informações de versão não fornecer a resolução, a fonte com carimbo de hora mais recente será retornada. Se as informações de carimbo de hora forem equivalentes, no arquivo de fonte que é o primeiro na ordem alfabética é retornado.
