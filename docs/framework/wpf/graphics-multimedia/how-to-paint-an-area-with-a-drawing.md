---
title: Como pintar uma área com um desenho
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with drawings
- painting [WPF], with drawings
- drawings [WPF], painting with
ms.assetid: c10dc4b1-09b1-41e8-ad14-456b5fb377df
ms.openlocfilehash: 222aa3fbb72ebaf15be3ed7f9804936e7e1187e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-paint-an-area-with-a-drawing"></a>Como pintar uma área com um desenho
Este exemplo mostra como pintar uma área com um desenho. Para pintar uma área com um desenho, use um <xref:System.Windows.Media.DrawingBrush> e um ou mais <xref:System.Windows.Media.Drawing> objetos.   O exemplo a seguir usa um <xref:System.Windows.Media.DrawingBrush> para pintar um objeto com um desenho de duas elipses.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[drawingbrush_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_snip/CS/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 [!code-csharp[drawingbrush_procedural_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_procedural_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-vb[drawingbrush_procedural_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/drawingbrush_procedural_snip/VisualBasic/DrawingBrushExample.vb#drawingbrushexamplewholepage)]  
  
 A ilustração a seguir mostra a saída do exemplo.  
  
 ![Saída de um DrawingBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrush-simple.png "graphicsmm_drawingbrush_simple")  
  
 (O centro da forma é banco por razões descritas em [controlar o preenchimento de uma forma de composição](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-the-fill-of-a-composite-shape.md).)  
  
 Definindo um <xref:System.Windows.Media.DrawingBrush> do objeto <xref:System.Windows.Media.TileBrush.Viewport%2A> e <xref:System.Windows.Media.TileBrush.TileMode%2A> propriedades, você pode criar um padrão de repetição. O exemplo a seguir pinta um objeto com um padrão criado de um desenho de duas elipses.  
  
 [!code-xaml[drawingbrush_snip#TiledDrawingBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_snip/CS/TiledDrawingBrushExample.xaml#tileddrawingbrushexamplewholepage)]  
  
 [!code-csharp[drawingbrush_procedural_snip#TiledDrawingBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_procedural_snip/CSharp/TiledDrawingBrushExample.cs#tileddrawingbrushexamplewholepage)]
 [!code-vb[drawingbrush_procedural_snip#TiledDrawingBrushExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/drawingbrush_procedural_snip/VisualBasic/TiledDrawingBrushExample.vb#tileddrawingbrushexamplewholepage)]  
  
 A ilustração a seguir mostra o lado a lado <xref:System.Windows.Media.DrawingBrush> saída.  
  
 ![Saída lado a lado de um DrawingBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrush-tiled.png "graphicsmm_drawingbrush_tiled")  
  
 Para obter mais informações sobre pincéis de desenho, consulte [pintura com imagens, desenhos e visuais](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md). Para obter mais informações sobre <xref:System.Windows.Media.Drawing> objetos, consulte o [visão geral de objetos de desenho](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).
