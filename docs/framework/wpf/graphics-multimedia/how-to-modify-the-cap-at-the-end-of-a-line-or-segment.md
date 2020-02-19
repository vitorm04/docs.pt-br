---
title: Como modificar o limite ao final de uma linha ou um segmento
ms.date: 03/30/2017
helpviewer_keywords:
- Shape elements [WPF], ends
- Shape elements [WPF], caps
- graphics [WPF], Shape caps
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
ms.openlocfilehash: 5f755d7b4d1682755ea461121f91c0666d450ad1
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452773"
---
# <a name="how-to-modify-the-cap-at-the-end-of-a-line-or-segment"></a>Como modificar o limite ao final de uma linha ou um segmento
Este exemplo mostra como modificar a forma no início ou no final de um elemento de <xref:System.Windows.Shapes.Shape> aberto. Para alterar o limite no início de um <xref:System.Windows.Shapes.Shape>aberto, use sua propriedade <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A>. Para alterar o limite no final de um <xref:System.Windows.Shapes.Shape>aberto, use sua propriedade <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A>. Para exibir as limites de linha disponíveis, consulte a enumeração <xref:System.Windows.Media.PenLineCap>.  
  
> [!NOTE]
> Essa propriedade afeta apenas uma forma aberta, como um <xref:System.Windows.Shapes.Line>, um <xref:System.Windows.Shapes.Polyline>ou um elemento <xref:System.Windows.Shapes.Path> aberto.  
  
 O exemplo a seguir desenha quatro elementos <xref:System.Windows.Shapes.Polyline> e usa um conjunto diferente de formas nas extremidades de cada um.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[drawingwithshapeelements#ShapeLineCaps1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, consulte o [Exemplo de elementos de forma](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Media.PenLineCap>
