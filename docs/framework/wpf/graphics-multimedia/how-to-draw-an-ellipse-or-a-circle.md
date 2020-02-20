---
title: Como desenhar uma elipse ou um círculo
ms.date: 03/30/2017
helpviewer_keywords:
- ellipses [WPF], drawing
- circles [WPF], drawing
- drawing circles [WPF]
- drawing ellipses [WPF]
- graphics [WPF], drawing circles
- graphics [WPF], drawing ellipses
ms.assetid: 99763b8c-bfc8-44be-8231-8a70daf5481a
ms.openlocfilehash: 5f17615da4907cba6e25b68f2f934602c2f8a390
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452916"
---
# <a name="how-to-draw-an-ellipse-or-a-circle"></a>Como desenhar uma elipse ou um círculo
Este exemplo mostra como desenhar reticências e círculos usando o elemento <xref:System.Windows.Shapes.Ellipse>. Para desenhar uma elipse, crie um elemento <xref:System.Windows.Shapes.Ellipse> e especifique seu <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A>. Use sua propriedade <xref:System.Windows.Shapes.Shape.Fill%2A> para especificar o <xref:System.Windows.Media.Brush> usado para pintar o interior da elipse. Use sua propriedade <xref:System.Windows.Shapes.Shape.Stroke%2A> para especificar o <xref:System.Windows.Media.Brush> usado para pintar o contorno da elipse. A propriedade <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> especifica a espessura da estrutura de tópicos da elipse.  
  
 Para desenhar um círculo, torne o <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> do elemento <xref:System.Windows.Shapes.Ellipse> igual um do outro.  
  
 O exemplo a seguir desenha quatro elementos <xref:System.Windows.Shapes.Ellipse> dentro de um <xref:System.Windows.Controls.Canvas>.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[drawingwithshapeelements#EllipseExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 Embora este exemplo use um <xref:System.Windows.Controls.Canvas> para conter as reticências, você pode usar elementos Ellipse (e todos os outros elementos Shape) com qualquer <xref:System.Windows.Controls.Panel> ou <xref:System.Windows.Controls.Control> que ofereça suporte a conteúdo que não seja de texto.  
  
 Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, consulte o [Exemplo de elementos de forma](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Shapes.Ellipse>
- <xref:System.Windows.Shapes.Shape>
- [Exemplo de elementos de forma](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
