---
title: 'Como: Modificar o limite ao final de uma linha ou um segmento'
ms.date: 03/30/2017
helpviewer_keywords:
- Shape elements [WPF], ends
- Shape elements [WPF], caps
- graphics [WPF], Shape caps
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
ms.openlocfilehash: ba61b30b4ff575bb504f792f8990bbfc64a6c33e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371470"
---
# <a name="how-to-modify-the-cap-at-the-end-of-a-line-or-segment"></a>Como: Modificar o limite ao final de uma linha ou um segmento
Este exemplo mostra como modificar a forma no início ou final de uma abertura <xref:System.Windows.Shapes.Shape> elemento. Para alterar o limite no início de uma abertura <xref:System.Windows.Shapes.Shape>, use seu <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A> propriedade. Para alterar o limite ao final de uma abertura <xref:System.Windows.Shapes.Shape>, use seu <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> propriedade. Para exibir as terminações de linha disponíveis, consulte o <xref:System.Windows.Media.PenLineCap> enumeração.  
  
> [!NOTE]
>  Essa propriedade afeta apenas uma forma aberta, como um <xref:System.Windows.Shapes.Line>, um <xref:System.Windows.Shapes.Polyline>, ou um aberto <xref:System.Windows.Shapes.Path> elemento.  
  
 O exemplo a seguir desenha quatro <xref:System.Windows.Shapes.Polyline> elementos e usa um conjunto de formas diferentes nas extremidades de cada um.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[drawingwithshapeelements#ShapeLineCaps1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, consulte o [Exemplo de elementos de forma](https://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Media.PenLineCap>
