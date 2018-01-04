---
title: "Como criar padrões lado a lado diferentes com um TileBrush"
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
- TileBrush [WPF], creating tile patterns
- tile patterns [WPF], creating
- creating [WPF], tile patterns with TileBrush
ms.assetid: 5aa46632-3527-4668-9d8d-0375c8af28aa
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 646ce5142875c95c0b1ca19643790f73f7eb83e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-different-tile-patterns-with-a-tilebrush"></a>Como criar padrões lado a lado diferentes com um TileBrush
Este exemplo mostra como usar o <xref:System.Windows.Media.TileBrush.TileMode%2A> propriedade de um <xref:System.Windows.Media.TileBrush> para criar um padrão.  
  
 O <xref:System.Windows.Media.TileBrush.TileMode%2A> propriedade permite que você especifique como o conteúdo de um <xref:System.Windows.Media.TileBrush> é repetido, ou seja, lado a lado para preencher uma área de saída. Para criar um padrão, defina o <xref:System.Windows.Media.TileBrush.TileMode%2A> para <xref:System.Windows.Media.TileMode.Tile>, <xref:System.Windows.Media.TileMode.FlipX>, <xref:System.Windows.Media.TileMode.FlipY>, ou <xref:System.Windows.Media.TileMode.FlipXY>. Você também deve definir o <xref:System.Windows.Media.TileBrush.Viewport%2A> do <xref:System.Windows.Media.TileBrush> para que seja menor do que a área que você estiver pintando; caso contrário, apenas um único bloco é produzido, independentemente que <xref:System.Windows.Media.TileBrush.TileMode%2A> configuração.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria cinco <xref:System.Windows.Media.DrawingBrush> objetos, cada lhes dá um diferentes <xref:System.Windows.Media.TileBrush.TileMode%2A> configuração e os utiliza para pintar cinco retângulos. Embora este exemplo usa o <xref:System.Windows.Media.DrawingBrush> classe para demonstrar <xref:System.Windows.Media.TileBrush.TileMode%2A> comportamento, o <xref:System.Windows.Media.TileBrush.TileMode%2A> propriedade funciona de forma idêntica para todos o <xref:System.Windows.Media.TileBrush> objetos, ou seja, para <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.VisualBrush>, e <xref:System.Windows.Media.DrawingBrush>.  
  
 A ilustração a seguir mostra a saída que esse exemplo produz.  
  
 ![TileBrush lado a lado de saída de exemplo](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrushtilemodeexample.png "graphicsmm_DrawingBrushTileModeExample")  
Padrões de bloco criados com a propriedade TileMode  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/TileModeExample.cs#graphicsmmdrawingbrushtilemodeexample)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/tilemodeexample.vb#graphicsmmdrawingbrushtilemodeexample)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/TileModeExample.xaml#graphicsmmdrawingbrushtilemodeexample)]  
  
## <a name="see-also"></a>Consulte também  
 [Definir o tamanho de bloco um TileBrush](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-the-tile-size-for-a-tilebrush.md)  
 [Pintando com imagens, desenhos e visuais](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
