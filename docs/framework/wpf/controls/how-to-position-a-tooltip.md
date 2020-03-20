---
title: Como posicionar um ToolTip
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolTip control [WPF], positioning
- positioning ToolTip controls [WPF]
ms.assetid: cddf3757-9e5f-4ce3-a6eb-44489cf3804a
ms.openlocfilehash: 0f52703e4fe127daa40f220280f084b2026580cc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186945"
---
# <a name="how-to-position-a-tooltip"></a>Como posicionar um ToolTip
Este exemplo mostra como especificar a posição de uma dica de ferramenta na tela.  
  
## <a name="example"></a>Exemplo  
 Você pode posicionar uma dica de ferramenta usando um conjunto <xref:System.Windows.Controls.ToolTip> <xref:System.Windows.Controls.ToolTipService> de cinco propriedades definidas tanto nas classes quanto nas classes. A tabela a seguir mostra esses dois conjuntos de cinco propriedades e fornece links para a documentação de referência de acordo com a classe.  
  
### <a name="corresponding-tooltip-properties-according-to-class"></a>Propriedades de dica de ferramentas correspondentes de acordo com a classe  
  
|<xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType>propriedades de classe|<xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType>propriedades de classe|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.ToolTip.Placement%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.Placement%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementTarget%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementTarget%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementRectangle%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementRectangle%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.HorizontalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.HorizontalOffset%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.VerticalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.VerticalOffset%2A?displayProperty=nameWithType>|  
  
 Se você definir o conteúdo de <xref:System.Windows.Controls.ToolTip> uma dica de ferramenta usando um objeto, você poderá usar as propriedades de qualquer classe; no entanto, as <xref:System.Windows.Controls.ToolTipService> propriedades têm precedência. Use <xref:System.Windows.Controls.ToolTipService> as propriedades para dicas de <xref:System.Windows.Controls.ToolTip> ferramentas que não são definidas como objetos.  
  
 As ilustrações a seguir mostram como posicionar uma dica de ferramenta usando essas propriedades. Embora, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] os exemplos nestas ilustrações mostrem como definir <xref:System.Windows.Controls.ToolTip> as propriedades definidas <xref:System.Windows.Controls.ToolTipService> pela classe, as propriedades correspondentes da classe seguem as mesmas regras de layout. Para obter mais informações sobre os possíveis valores para a propriedade de Posicionamento, consulte [Comportamento de posicionamento de pop-up](popup-placement-behavior.md).  

 A imagem a seguir mostra a colocação da dica de ferramenta usando a propriedade Colocação:  
  
 ![Diagrama mostrando a colocação ToolTip usando a propriedade Colocação.](./media/how-to-position-a-tooltip/tooltip-placement-property.png)

 A imagem a seguir mostra a colocação da dica de ferramenta usando as propriedades Placement e PlacementRectangle:

 ![Diagrama mostrando a colocação toolTip usando uma propriedade PlacementRectangle.](./media/how-to-position-a-tooltip/tooltip-placement-rectangle-property.png)  

 A imagem a seguir mostra a colocação da dica de ferramenta usando as propriedades Colocação, PlacementRectangle e Offset:
  
 ![Diagrama mostrando a colocação toolTip usando a propriedade Offset.](./media/how-to-position-a-tooltip/tooltip-placement-offset-property.png)

 O exemplo a seguir <xref:System.Windows.Controls.ToolTip> mostra como usar as propriedades para especificar a posição de uma dica de ferramenta cujo conteúdo é um <xref:System.Windows.Controls.ToolTip> objeto.  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
 [!code-csharp[ToolTipService#ToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#tooltipcode)]
 [!code-vb[ToolTipService#ToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#tooltipcode)]  
  
 O exemplo a seguir <xref:System.Windows.Controls.ToolTipService> mostra como usar as propriedades para especificar <xref:System.Windows.Controls.ToolTip> a posição de uma dica de ferramenta cujo conteúdo não é um objeto.  
  
 [!code-xaml[ToolTipService#NoToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
 [!code-csharp[ToolTipService#NoToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#notooltipcode)]
 [!code-vb[ToolTipService#NoToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#notooltipcode)]  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [Tópicos de como fazer](tooltip-how-to-topics.md)
- [Visão geral de ToolTip](tooltip-overview.md)
