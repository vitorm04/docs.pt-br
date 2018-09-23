---
title: Como criar uma curva de Bézier cúbica
ms.date: 03/30/2017
helpviewer_keywords:
- curves [WPF], cubic Bezier
- Bezier curves [WPF], cubic
- graphics [WPF], cubic Bezier curves
- cubic Bezier curves [WPF]
ms.assetid: 450a3a77-7c57-48b0-a008-0f6051add980
ms.openlocfilehash: 2dd9dfa7f15ce00261c87f316079c25a7aa52532
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2018
ms.locfileid: "46703577"
---
# <a name="how-to-create-a-cubic-bezier-curve"></a>Como criar uma curva de Bézier cúbica
Este exemplo mostra como criar uma curva de Bézier cúbica. Para criar uma curva de Bézier cúbica, use o <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, e <xref:System.Windows.Media.BezierSegment> classes.  Para exibir a geometria resultante, use uma <xref:System.Windows.Shapes.Path> elemento, ou usá-lo com um <xref:System.Windows.Media.GeometryDrawing> ou um <xref:System.Windows.Media.DrawingContext>. Nos exemplos a seguir, uma curva de Bézier cúbica é desenhada de (10, 100) para (300, 100). A curva tem pontos de controle de (100, 0) e (200, 200).  
  
## <a name="example"></a>Exemplo  
 [xaml]  
  
 No [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], você pode usar marcação de sintaxe abreviada para descrever um caminho.  
  
 [!code-xaml[GeometrySample#53](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#53)]  
  
 [xaml]  
  
 No [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você também pode desenhar uma curva de Bézier cúbica usando marcas de objeto. A seguir é equivalente ao anterior [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] exemplo.  
  
 [!code-xaml[GeometrySample#33](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#33)]  
  
 Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, confira o [Exemplo de geometrias](https://go.microsoft.com/fwlink/?LinkID=159989).  
  
## <a name="see-also"></a>Consulte também  
 [Criar um arco elíptico](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md)  
 [Criar um LineSegment em uma PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-linesegment-in-a-pathgeometry.md)  
 [Criar uma curva de Bézier cúbica](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)  
 [Criar uma curva de Bézier quadrática](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md)
