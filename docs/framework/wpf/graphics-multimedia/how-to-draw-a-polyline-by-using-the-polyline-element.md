---
title: Como desenhar uma polilinha usando o elemento Polyline
ms.date: 03/30/2017
helpviewer_keywords:
- connected lines [WPF]
- polylines [WPF], drawing
- graphics [WPF], polylines
- lines [WPF], connected (see polylines)
- drawing [WPF], polylines
ms.assetid: 65db8935-d047-4295-87c4-b427ff3ad293
ms.openlocfilehash: 6698141bcaa3b0fd5f5b9cf66bcab1be1f4ea2f0
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452955"
---
# <a name="how-to-draw-a-polyline-by-using-the-polyline-element"></a>Como desenhar uma polilinha usando o elemento Polyline
Este exemplo mostra como desenhar uma polilinha, que é uma série de linhas conectadas, usando o elemento <xref:System.Windows.Shapes.Polyline>.  
  
 Para desenhar uma polilinha, crie um elemento <xref:System.Windows.Shapes.Polyline> e use sua propriedade <xref:System.Windows.Shapes.Polyline.Points%2A> para especificar os vértices de forma. Por fim, use as propriedades <xref:System.Windows.Shapes.Shape.Stroke%2A> e <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> para descrever o contorno de polilinha porque uma linha sem um traço é invisível.  
  
> [!NOTE]
> Como o elemento <xref:System.Windows.Shapes.Polyline> não é uma forma fechada, a propriedade <xref:System.Windows.Shapes.Shape.Fill%2A> não tem efeito, mesmo que você feche deliberadamente o contorno da forma. Para criar uma forma fechada com um <xref:System.Windows.Shapes.Shape.Fill%2A>, use um elemento <xref:System.Windows.Shapes.Polygon>.  
  
 O exemplo a seguir desenha dois elementos <xref:System.Windows.Shapes.Polyline> dentro de um <xref:System.Windows.Controls.Canvas>.  
  
## <a name="example"></a>Exemplo  
 Em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], sintaxe válida para os pontos é uma lista delimitada por espaço de pares de coordenadas x e y, separados por vírgulas.  
  
 [!code-xaml[drawingwithshapeelements#PolylineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 Embora este exemplo use uma <xref:System.Windows.Controls.Canvas> para conter as polilinhas, você pode usar elementos Polyline (e todos os outros elementos Shape) com qualquer <xref:System.Windows.Controls.Panel> ou <xref:System.Windows.Controls.Control> que ofereça suporte a conteúdo que não seja de texto.  
  
 Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, consulte o [Exemplo de elementos de forma](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Shapes.Polygon>
- <xref:System.Windows.Shapes.Shape>
- [Exemplo de elementos de forma](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
- [Visão geral de formas e desenho básico no WPF](shapes-and-basic-drawing-in-wpf-overview.md)
