---
title: Como posicionar um ToolTip
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
- ToolTip control [WPF], positioning
- positioning ToolTip controls [WPF]
ms.assetid: cddf3757-9e5f-4ce3-a6eb-44489cf3804a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0e8345b74cf9269bca21e1e5698de974109c2aee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-position-a-tooltip"></a>Como posicionar um ToolTip
Este exemplo mostra como especificar a posição de uma dica de ferramenta na tela.  
  
## <a name="example"></a>Exemplo  
 Você pode posicionar um tooltip usando um conjunto de cinco propriedades que são definidas em ambas as <xref:System.Windows.Controls.ToolTip> e <xref:System.Windows.Controls.ToolTipService> classes. A tabela a seguir mostra esses dois conjuntos de cinco propriedades e fornece links para a documentação de referência de acordo com a classe.  
  
### <a name="corresponding-tooltip-properties-according-to-class"></a>Propriedades de dica de ferramentas correspondentes de acordo com a classe  
  
|<xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType>Propriedades de classe|<xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType>Propriedades de classe|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.ToolTip.Placement%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.Placement%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementTarget%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementTarget%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementRectangle%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementRectangle%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.HorizontalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.HorizontalOffset%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.VerticalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.VerticalOffset%2A?displayProperty=nameWithType>|  
  
 Se você definir o conteúdo de uma dica de ferramenta usando um <xref:System.Windows.Controls.ToolTip> do objeto, você pode usar as propriedades de qualquer classe; no entanto, o <xref:System.Windows.Controls.ToolTipService> propriedades têm precedência. Use o <xref:System.Windows.Controls.ToolTipService> propriedades de dicas de ferramenta que não são definidas como <xref:System.Windows.Controls.ToolTip> objetos.  
  
 As ilustrações a seguir mostram como posicionar uma dica de ferramenta usando essas propriedades. Embora, o [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] exemplos estas ilustrações mostram como definir as propriedades que são definidas pelo <xref:System.Windows.Controls.ToolTip> classe, as propriedades correspondentes do <xref:System.Windows.Controls.ToolTipService> classe seguem as mesmas regras de layout. Para obter mais informações sobre os possíveis valores para a propriedade de Posicionamento, consulte [Comportamento de posicionamento de pop-up](../../../../docs/framework/wpf/controls/popup-placement-behavior.md).  
  
 ![Posicionamento de dica de ferramenta](../../../../docs/framework/wpf/controls/media/tooltipplacement.png "ToolTipPlacement")  
Posicionamento de ToolTip usando a propriedade de Posicionamento  
  
 ![Colocando uma dica de ferramenta usando um retângulo de posicionamento](../../../../docs/framework/wpf/controls/media/tooltipplacementrectangle.png "ToolTipPlacementRectangle")  
Posicionamento de ToolTip usando as propriedades Placement e PlacementRectangle  
  
 ![Diagrama de posicionamento de dica de ferramenta](../../../../docs/framework/wpf/controls/media/tooltipplacementprhv.png "ToolTipPlacementPRHV")  
Posicionamento de ToolTip usando as propriedades Placement, PlacementRectangle e Offset  
  
 O exemplo a seguir mostra como usar o <xref:System.Windows.Controls.ToolTip> propriedades para especificar a posição de um tooltip cujo conteúdo é um <xref:System.Windows.Controls.ToolTip> objeto.  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
 [!code-csharp[ToolTipService#ToolTipCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#tooltipcode)]
 [!code-vb[ToolTipService#ToolTipCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#tooltipcode)]  
  
 O exemplo a seguir mostra como usar o <xref:System.Windows.Controls.ToolTipService> propriedades para especificar a posição de um tooltip cujo conteúdo não é um <xref:System.Windows.Controls.ToolTip> objeto.  
  
 [!code-xaml[ToolTipService#NoToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
 [!code-csharp[ToolTipService#NoToolTipCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#notooltipcode)]
 [!code-vb[ToolTipService#NoToolTipCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#notooltipcode)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipService>  
 [Tópicos explicativos](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)  
 [Visão geral de ToolTip](../../../../docs/framework/wpf/controls/tooltip-overview.md)  
 [Usar o ContextMenuService e o ToolTipService](http://msdn.microsoft.com/en-us/809b0e9c-d612-4cda-b8af-1a698c68f4d1)
