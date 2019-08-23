---
title: 'Como: Desenhar uma polilinha usando o elemento Polyline'
ms.date: 03/30/2017
helpviewer_keywords:
- connected lines [WPF]
- polylines [WPF], drawing
- graphics [WPF], polylines
- lines [WPF], connected (see polylines)
- drawing [WPF], polylines
ms.assetid: 65db8935-d047-4295-87c4-b427ff3ad293
ms.openlocfilehash: fb5220082989a9d0a22c4998bb79c0a196067e7e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934955"
---
# <a name="how-to-draw-a-polyline-by-using-the-polyline-element"></a>Como: Desenhar uma polilinha usando o elemento Polyline
Este exemplo mostra como desenhar uma polilinha, que é uma série de linhas conectadas, usando o <xref:System.Windows.Shapes.Polyline> elemento.  
  
 Para desenhar uma polilinha, crie um <xref:System.Windows.Shapes.Polyline> elemento e use sua <xref:System.Windows.Shapes.Polyline.Points%2A> propriedade para especificar os vértices de forma. Por fim, use <xref:System.Windows.Shapes.Shape.Stroke%2A> as <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> Propriedades e para descrever o contorno de polilinha porque uma linha sem um traço é invisível.  
  
> [!NOTE]
> Como o <xref:System.Windows.Shapes.Polyline> elemento não é uma forma fechada, a <xref:System.Windows.Shapes.Shape.Fill%2A> propriedade não tem efeito, mesmo que você feche deliberadamente o contorno da forma. Para criar uma forma fechada com um <xref:System.Windows.Shapes.Shape.Fill%2A>, use um <xref:System.Windows.Shapes.Polygon> elemento.  
  
 O exemplo a seguir desenha <xref:System.Windows.Shapes.Polyline> dois elementos dentro <xref:System.Windows.Controls.Canvas>de um.  
  
## <a name="example"></a>Exemplo  
 Em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], sintaxe válida para os pontos é uma lista delimitada por espaço de pares de coordenadas x e y, separados por vírgulas.  
  
 [!code-xaml[drawingwithshapeelements#PolylineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 Embora este exemplo use um <xref:System.Windows.Controls.Canvas> para conter as polilinhas, você pode usar elementos Polyline (e todos os outros elementos Shape) com qualquer <xref:System.Windows.Controls.Panel> um <xref:System.Windows.Controls.Control> ou que ofereça suporte a conteúdo que não seja de texto.  
  
 Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, consulte o [Exemplo de elementos de forma](https://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Shapes.Polygon>
- <xref:System.Windows.Shapes.Shape>
- [Exemplo de elementos de forma](https://go.microsoft.com/fwlink/?LinkID=160037)
- [Visão geral de formas e desenho básico no WPF](shapes-and-basic-drawing-in-wpf-overview.md)
