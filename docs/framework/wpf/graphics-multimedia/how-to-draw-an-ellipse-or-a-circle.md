---
title: 'Como: Desenhar uma elipse ou um círculo'
ms.date: 03/30/2017
helpviewer_keywords:
- ellipses [WPF], drawing
- circles [WPF], drawing
- drawing circles [WPF]
- drawing ellipses [WPF]
- graphics [WPF], drawing circles
- graphics [WPF], drawing ellipses
ms.assetid: 99763b8c-bfc8-44be-8231-8a70daf5481a
ms.openlocfilehash: 3a3d25643daaf48f7a0230e199dbba8710184a43
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365341"
---
# <a name="how-to-draw-an-ellipse-or-a-circle"></a>Como: Desenhar uma elipse ou um círculo
Este exemplo mostra como desenhar elipses e círculos usando o <xref:System.Windows.Shapes.Ellipse> elemento. Para desenhar uma elipse, crie uma <xref:System.Windows.Shapes.Ellipse> elemento e especifique seus <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A>. Use sua <xref:System.Windows.Shapes.Shape.Fill%2A> propriedade para especificar o <xref:System.Windows.Media.Brush> que é usado para pintar o interior da elipse. Use sua <xref:System.Windows.Shapes.Shape.Stroke%2A> propriedade para especificar o <xref:System.Windows.Media.Brush> que é usado para pintar o contorno da elipse. O <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> propriedade especifica a espessura do contorno elipse.  
  
 Para desenhar um círculo, faça o <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> da <xref:System.Windows.Shapes.Ellipse> elemento igual entre si.  
  
 O exemplo a seguir desenha quatro <xref:System.Windows.Shapes.Ellipse> elementos dentro de um <xref:System.Windows.Controls.Canvas>.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[drawingwithshapeelements#EllipseExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 Embora este exemplo usa uma <xref:System.Windows.Controls.Canvas> para conter as elipses, você pode usar elementos de elipse (e todos os outros elementos de forma) com qualquer <xref:System.Windows.Controls.Panel> ou <xref:System.Windows.Controls.Control> que dá suporte a conteúdo não textual.  
  
 Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, consulte o [Exemplo de elementos de forma](https://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Shapes.Ellipse>
- <xref:System.Windows.Shapes.Shape>
- [Exemplo de elementos de forma](https://go.microsoft.com/fwlink/?LinkID=160037)
