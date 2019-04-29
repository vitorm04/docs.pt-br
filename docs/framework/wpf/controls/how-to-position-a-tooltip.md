---
title: 'Como: Posicionar um ToolTip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolTip control [WPF], positioning
- positioning ToolTip controls [WPF]
ms.assetid: cddf3757-9e5f-4ce3-a6eb-44489cf3804a
ms.openlocfilehash: 811818fe6e7c0d8ce9e2aa058b42bf592ada4b92
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770887"
---
# <a name="how-to-position-a-tooltip"></a>Como: Posicionar um ToolTip
Este exemplo mostra como especificar a posição de uma dica de ferramenta na tela.  
  
## <a name="example"></a>Exemplo  
 Você pode posicionar um tooltip usando um conjunto de cinco propriedades que são definidas em ambas as <xref:System.Windows.Controls.ToolTip> e <xref:System.Windows.Controls.ToolTipService> classes. A tabela a seguir mostra esses dois conjuntos de cinco propriedades e fornece links para a documentação de referência de acordo com a classe.  
  
### <a name="corresponding-tooltip-properties-according-to-class"></a>Propriedades de dica de ferramentas correspondentes de acordo com a classe  
  
|<xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType> Propriedades de classe|<xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType> Propriedades de classe|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.ToolTip.Placement%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.Placement%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementTarget%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementTarget%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementRectangle%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementRectangle%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.HorizontalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.HorizontalOffset%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.VerticalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.VerticalOffset%2A?displayProperty=nameWithType>|  
  
 Se você definir o conteúdo de uma dica de ferramenta usando um <xref:System.Windows.Controls.ToolTip> objeto, você pode usar as propriedades de qualquer classe; no entanto, o <xref:System.Windows.Controls.ToolTipService> propriedades têm precedência. Use o <xref:System.Windows.Controls.ToolTipService> propriedades de dicas de ferramenta que não são definidas como <xref:System.Windows.Controls.ToolTip> objetos.  
  
 As ilustrações a seguir mostram como posicionar uma dica de ferramenta usando essas propriedades. Embora, a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] exemplos nessas ilustrações mostram como definir as propriedades que são definidas pela <xref:System.Windows.Controls.ToolTip> classe, as propriedades correspondentes do <xref:System.Windows.Controls.ToolTipService> classe seguem as mesmas regras de layout. Para obter mais informações sobre os possíveis valores para a propriedade de Posicionamento, consulte [Comportamento de posicionamento de pop-up](popup-placement-behavior.md).  
 
 A imagem a seguir mostra o posicionamento de tooltip usando a propriedade de posicionamento:  
  
 ![Diagrama mostrando o posicionamento de ToolTip usando a propriedade de posicionamento.](./media/how-to-position-a-tooltip/tooltip-placement-property.png)
 
 A imagem a seguir mostra o posicionamento de tooltip usando as propriedades Placement e PlacementRectangle:   

 ![Diagrama mostrando o posicionamento de ToolTip usando uma propriedade PlacementRectangle.](./media/how-to-position-a-tooltip/tooltip-placement-rectangle-property.png)  
 
 A imagem a seguir mostra o posicionamento de tooltip usando as propriedades Placement, PlacementRectangle e Offset:   
  
 ![Diagrama mostrando o posicionamento de ToolTip usando a propriedade de deslocamento.](./media/how-to-position-a-tooltip/tooltip-placement-offset-property.png)

 O exemplo a seguir mostra como usar o <xref:System.Windows.Controls.ToolTip> propriedades para especificar a posição de uma dica de ferramenta cujo conteúdo é um <xref:System.Windows.Controls.ToolTip> objeto.  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
 [!code-csharp[ToolTipService#ToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#tooltipcode)]
 [!code-vb[ToolTipService#ToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#tooltipcode)]  
  
 O exemplo a seguir mostra como usar o <xref:System.Windows.Controls.ToolTipService> propriedades para especificar a posição de uma dica de ferramenta cujo conteúdo não é um <xref:System.Windows.Controls.ToolTip> objeto.  
  
 [!code-xaml[ToolTipService#NoToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
 [!code-csharp[ToolTipService#NoToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#notooltipcode)]
 [!code-vb[ToolTipService#NoToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#notooltipcode)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [Tópicos de instruções](tooltip-how-to-topics.md)
- [Visão geral de ToolTip](tooltip-overview.md)
