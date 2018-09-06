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
ms.openlocfilehash: d065d3cead1ed9746a9615ce2bb6d3ec4cbd614d
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43855424"
---
# <a name="how-to-draw-a-polyline-by-using-the-polyline-element"></a>Como desenhar uma polilinha usando o elemento Polyline
Este exemplo mostra como desenhar uma polilinha, que é uma série de linhas conectadas, usando o <xref:System.Windows.Shapes.Polyline> elemento.  
  
 Para desenhar uma polilinha, crie uma <xref:System.Windows.Shapes.Polyline> elemento e use seu <xref:System.Windows.Shapes.Polyline.Points%2A> propriedade para especificar os vértices da forma. Por fim, use o <xref:System.Windows.Shapes.Shape.Stroke%2A> e <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> propriedades para descrever a polyline descrevem porque uma linha sem traço é invisível.  
  
> [!NOTE]
>  Porque o <xref:System.Windows.Shapes.Polyline> elemento não é uma forma fechada, o <xref:System.Windows.Shapes.Shape.Fill%2A> propriedade não tem efeito, mesmo se você fecha deliberadamente o contorno da forma. Para criar uma forma fechada com um <xref:System.Windows.Shapes.Shape.Fill%2A>, use um <xref:System.Windows.Shapes.Polygon> elemento.  
  
 O exemplo a seguir desenha dois <xref:System.Windows.Shapes.Polyline> elementos dentro de um <xref:System.Windows.Controls.Canvas>.  
  
## <a name="example"></a>Exemplo  
 Em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], sintaxe válida para os pontos é uma lista delimitada por espaço de pares de coordenadas x e y, separados por vírgulas.  
  
 [!code-xaml[drawingwithshapeelements#PolylineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 Embora este exemplo usa uma <xref:System.Windows.Controls.Canvas> para conter as polilinhas, você pode usar elementos polyline (e todos os outros elementos de forma) com qualquer <xref:System.Windows.Controls.Panel> ou <xref:System.Windows.Controls.Control> que dá suporte a conteúdo não textual.  
  
 Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, consulte o [Exemplo de elementos de forma](https://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Shapes.Polyline>  
 <xref:System.Windows.Shapes.Polygon>  
 <xref:System.Windows.Shapes.Shape>  
 [Exemplo de elementos de forma](https://go.microsoft.com/fwlink/?LinkID=160037)  
 [Visão geral de formas e desenho básico no WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
