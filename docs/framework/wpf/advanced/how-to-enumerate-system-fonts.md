---
title: 'Como: Enumerar fontes de sistema'
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
ms.openlocfilehash: c7e81b5d1b70ba911a0b505219f7977e019038cf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62001592"
---
# <a name="how-to-enumerate-system-fonts"></a>Como: Enumerar fontes de sistema
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como enumerar as fontes na coleção de fontes do sistema. O nome de família de fonte de cada <xref:System.Windows.Media.FontFamily> dentro de <xref:System.Windows.Media.Fonts.SystemFontFamilies%2A> é adicionado como um item de caixa de combinação.  
  
 [!code-csharp[TextOverview#100](~/samples/snippets/csharp/VS_Snippets_Wpf/TextOverview/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextOverview#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextOverview/visualbasic/window1.xaml.vb#100)]  
  
 Se várias versões da mesma família de fonte residir no mesmo diretório, o [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] enumeração de fonte retorna a versão mais recente da fonte. Se as informações de versão não fornece a resolução, a fonte com carimbo de hora mais recente será retornada. Se as informações de carimbo de hora são equivalentes, o arquivo de fonte que é o primeiro em ordem alfabética será retornado.
