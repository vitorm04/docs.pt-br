---
title: 'Como: Criar padrões de bloco diferentes com um TileBrush'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TileBrush [WPF], creating tile patterns
- tile patterns [WPF], creating
- creating [WPF], tile patterns with TileBrush
ms.assetid: 5aa46632-3527-4668-9d8d-0375c8af28aa
ms.openlocfilehash: c1051b234961eee9ae740af2abac3d64c523656c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61905120"
---
# <a name="how-to-create-different-tile-patterns-with-a-tilebrush"></a>Como: Criar padrões de bloco diferentes com um TileBrush
Este exemplo mostra como usar o <xref:System.Windows.Media.TileBrush.TileMode%2A> propriedade de um <xref:System.Windows.Media.TileBrush> para criar um padrão.  
  
 O <xref:System.Windows.Media.TileBrush.TileMode%2A> propriedade permite que você especifique como o conteúdo de um <xref:System.Windows.Media.TileBrush> é repetido, ou seja, lado a lado para preencher uma área de saída. Para criar um padrão, defina as <xref:System.Windows.Media.TileBrush.TileMode%2A> à <xref:System.Windows.Media.TileMode.Tile>, <xref:System.Windows.Media.TileMode.FlipX>, <xref:System.Windows.Media.TileMode.FlipY>, ou <xref:System.Windows.Media.TileMode.FlipXY>. Você também deve definir a <xref:System.Windows.Media.TileBrush.Viewport%2A> do <xref:System.Windows.Media.TileBrush> para que seja menor do que a área que você está pintando; caso contrário, apenas um único bloco será produzido, independentemente que <xref:System.Windows.Media.TileBrush.TileMode%2A> configuração que você usar.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria cinco <xref:System.Windows.Media.DrawingBrush> objetos, dá a eles cada um diferentes <xref:System.Windows.Media.TileBrush.TileMode%2A> definindo e os utiliza para pintar cinco retângulos. Embora este exemplo usa o <xref:System.Windows.Media.DrawingBrush> para demonstrar <xref:System.Windows.Media.TileBrush.TileMode%2A> comportamento, o <xref:System.Windows.Media.TileBrush.TileMode%2A> propriedade funciona de forma idêntica para todos os as <xref:System.Windows.Media.TileBrush> objetos, ou seja, para <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.VisualBrush>, e <xref:System.Windows.Media.DrawingBrush>.  
  
 A ilustração a seguir mostra a saída que esse exemplo produz.  
  
 ![TileBrush lado a lado de saída de exemplo](./media/graphicsmm-drawingbrushtilemodeexample.png "graphicsmm_DrawingBrushTileModeExample")  
Padrões de bloco criados com a propriedade TileMode  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/TileModeExample.cs#graphicsmmdrawingbrushtilemodeexample)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/tilemodeexample.vb#graphicsmmdrawingbrushtilemodeexample)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/TileModeExample.xaml#graphicsmmdrawingbrushtilemodeexample)]  
  
## <a name="see-also"></a>Consulte também

- [Definir o tamanho de bloco um TileBrush](how-to-set-the-tile-size-for-a-tilebrush.md)
- [Pintando com imagens, desenhos e visuais](painting-with-images-drawings-and-visuals.md)
