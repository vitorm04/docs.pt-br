---
title: Como desenhar um retângulo
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], rectangles
- graphics [WPF], rectangles
- rectangles [WPF], drawing
ms.assetid: beeb57ef-fab5-4446-a38a-1588f97b4c2f
ms.openlocfilehash: 95191e9d90bc2ac32902399125d9a51192e897bf
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452929"
---
# <a name="how-to-draw-a-rectangle"></a>Como desenhar um retângulo
Este exemplo mostra como desenhar um retângulo usando o elemento <xref:System.Windows.Shapes.Rectangle>.  
  
 Para desenhar um retângulo, crie um elemento <xref:System.Windows.Shapes.Rectangle> e especifique seu <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A>. Para pintar o interior do retângulo, defina seu <xref:System.Windows.Shapes.Shape.Fill%2A>. Para dar um esboço ao retângulo, use suas propriedades <xref:System.Windows.Shapes.Shape.Stroke%2A> e <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>.  
  
 Para dar os cantos arredondados do retângulo, especifique as propriedades opcionais <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> e <xref:System.Windows.Shapes.Rectangle.RadiusY%2A>. As propriedades <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> e <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> definem o raios do eixo x e do eixo y da elipse que é usada para arredondar os cantos do retângulo.  
  
 No exemplo a seguir, dois elementos de <xref:System.Windows.Shapes.Rectangle> são desenhados em um <xref:System.Windows.Controls.Canvas>. O primeiro retângulo tem um <xref:System.Windows.Media.Brushes.Blue%2A> interior. O segundo retângulo tem um <xref:System.Windows.Media.Brushes.Blue%2A> interior, uma estrutura de tópicos <xref:System.Windows.Media.Brushes.Black%2A> e cantos arredondados.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[drawingwithshapeelements#Rectangle1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/rectangleexample.xaml#rectangle1)]  
  
 Embora este exemplo use um <xref:System.Windows.Controls.Canvas> para conter os retângulos, você pode usar elementos Rectangle (e todos os outros elementos Shape) com qualquer <xref:System.Windows.Controls.Panel> ou <xref:System.Windows.Controls.Control> que ofereça suporte a conteúdo que não seja de texto. Na verdade, os retângulos são particularmente úteis para fornecer planos de fundo para partes de <xref:System.Windows.Controls.Grid> painéis. Para ver um exemplo, consulte a [Visão geral da tabela](../advanced/table-overview.md).  
  
 Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, consulte o [Exemplo de elementos de forma](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Shapes.Rectangle>
- [Exemplo de elementos de forma](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
- [Visão geral de formas e desenho básico no WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Visão Geral da Tabela](../advanced/table-overview.md)
