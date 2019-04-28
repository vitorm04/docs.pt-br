---
title: 'Como: Pintar uma área com um desenho'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with drawings
- painting [WPF], with drawings
- drawings [WPF], painting with
ms.assetid: c10dc4b1-09b1-41e8-ad14-456b5fb377df
ms.openlocfilehash: 6b204ae631912181333e2559ebadcdc37e7693b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62010055"
---
# <a name="how-to-paint-an-area-with-a-drawing"></a>Como: Pintar uma área com um desenho
Este exemplo mostra como pintar uma área com um desenho. Para pintar uma área com um desenho, use uma <xref:System.Windows.Media.DrawingBrush> e um ou mais <xref:System.Windows.Media.Drawing> objetos.   O exemplo a seguir usa um <xref:System.Windows.Media.DrawingBrush> para pintar um objeto com um desenho de duas elipses.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[drawingbrush_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_snip/CS/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 [!code-csharp[drawingbrush_procedural_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_procedural_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-vb[drawingbrush_procedural_snip#DrawingBrushExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/drawingbrush_procedural_snip/VisualBasic/DrawingBrushExample.vb#drawingbrushexamplewholepage)]  
  
 A ilustração a seguir mostra a saída do exemplo.  
  
 ![Saída de um DrawingBrush](./media/graphicsmm-drawingbrush-simple.png "graphicsmm_drawingbrush_simple")  
  
 (O centro da forma é branco por razões descritas em [controlar o preenchimento de uma forma composta](how-to-control-the-fill-of-a-composite-shape.md).)  
  
 Definindo uma <xref:System.Windows.Media.DrawingBrush> do objeto <xref:System.Windows.Media.TileBrush.Viewport%2A> e <xref:System.Windows.Media.TileBrush.TileMode%2A> propriedades, você pode criar um padrão de repetição. O exemplo a seguir pinta um objeto com um padrão criado de um desenho de duas elipses.  
  
 [!code-xaml[drawingbrush_snip#TiledDrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_snip/CS/TiledDrawingBrushExample.xaml#tileddrawingbrushexamplewholepage)]  
  
 [!code-csharp[drawingbrush_procedural_snip#TiledDrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_procedural_snip/CSharp/TiledDrawingBrushExample.cs#tileddrawingbrushexamplewholepage)]
 [!code-vb[drawingbrush_procedural_snip#TiledDrawingBrushExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/drawingbrush_procedural_snip/VisualBasic/TiledDrawingBrushExample.vb#tileddrawingbrushexamplewholepage)]  
  
 A ilustração a seguir mostra o lado a lado <xref:System.Windows.Media.DrawingBrush> saída.  
  
 ![Saída lado a lado de um DrawingBrush](./media/graphicsmm-drawingbrush-tiled.png "graphicsmm_drawingbrush_tiled")  
  
 Para obter mais informações sobre pincéis de desenho, consulte [pintando com imagens, desenhos e visuais](painting-with-images-drawings-and-visuals.md). Para obter mais informações sobre <xref:System.Windows.Media.Drawing> objetos, consulte a [visão geral de objetos de desenho](drawing-objects-overview.md).
