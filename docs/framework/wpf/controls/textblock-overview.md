---
title: Visão geral de TextBlock
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], TextBlock
- TextBlock control [WPF]
ms.assetid: 24720bca-341a-4b03-8a6b-7a678023b10a
ms.openlocfilehash: a3ea656a902f8a112a700667b6e08cae7463f68d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374460"
---
# <a name="textblock-overview"></a>Visão geral de TextBlock
O <xref:System.Windows.Controls.TextBlock> controle oferece suporte a texto flexível para [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativos. O elemento se destina principalmente basic [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] cenários que não exigem mais de um parágrafo de texto. Ele dá suporte a um número de propriedades que permitem que um controle preciso da apresentação, como <xref:System.Windows.Controls.TextBlock.FontFamily%2A>, <xref:System.Windows.Controls.TextBlock.FontSize%2A>, <xref:System.Windows.Controls.TextBlock.FontWeight%2A>, <xref:System.Windows.Controls.TextBlock.TextEffects%2A>, e <xref:System.Windows.Controls.TextBlock.TextWrapping%2A>. Conteúdo de texto pode ser adicionado usando o <xref:System.Windows.Controls.TextBlock.Text%2A> propriedade. Quando usado em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], conteúdo entre a abertura e a marca de fechamento é implicitamente adicionado como o texto do elemento.  
  
 Um <xref:System.Windows.Controls.TextBlock> elemento pode ser instanciado muito simplesmente usando [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[TextBlockSnip_XAML#2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBlockSnip_XAML/CS/default.xaml#2)]  
  
 Da mesma forma, o uso do <xref:System.Windows.Controls.TextBlock> elemento no código é relativamente simple.  
  
 [!code-csharp[TextBlockSnip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBlockSnip/CSharp/TextBlockSnips.cs#1)]
 [!code-vb[TextBlockSnip#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBlockSnip/VisualBasic/TextBlockSnips.vb#1)]  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Controls.Label>
