---
title: 'Como: Modificar o limite ao final de uma linha ou um segmento'
ms.date: 03/30/2017
helpviewer_keywords:
- Shape elements [WPF], ends
- Shape elements [WPF], caps
- graphics [WPF], Shape caps
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
ms.openlocfilehash: 53487417636dae8d855fe70b7b9255351a2dfb1e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916126"
---
# <a name="how-to-modify-the-cap-at-the-end-of-a-line-or-segment"></a>Como: Modificar o limite ao final de uma linha ou um segmento
Este exemplo mostra como modificar a forma no início ou no final de um elemento aberto <xref:System.Windows.Shapes.Shape> . Para alterar o limite no início de uma abertura <xref:System.Windows.Shapes.Shape>, use sua <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A> propriedade. Para alterar o limite no final de uma abertura <xref:System.Windows.Shapes.Shape>, use sua <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> propriedade. Para exibir as limites de linha disponíveis, consulte <xref:System.Windows.Media.PenLineCap> a enumeração.  
  
> [!NOTE]
> Essa propriedade afeta apenas uma forma aberta, como um <xref:System.Windows.Shapes.Line>, um <xref:System.Windows.Shapes.Polyline>ou um elemento aberto <xref:System.Windows.Shapes.Path> .  
  
 O exemplo a seguir desenha <xref:System.Windows.Shapes.Polyline> quatro elementos e usa um conjunto diferente de formas nas extremidades de cada um.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[drawingwithshapeelements#ShapeLineCaps1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, consulte o [Exemplo de elementos de forma](https://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Media.PenLineCap>
