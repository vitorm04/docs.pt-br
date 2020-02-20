---
title: Como criar uma curva de Bézier cúbica
ms.date: 03/30/2017
helpviewer_keywords:
- curves [WPF], cubic Bezier
- Bezier curves [WPF], cubic
- graphics [WPF], cubic Bezier curves
- cubic Bezier curves [WPF]
ms.assetid: 450a3a77-7c57-48b0-a008-0f6051add980
ms.openlocfilehash: c12bd84fcebb3acebb80bef5f4479ad535fd6691
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452104"
---
# <a name="how-to-create-a-cubic-bezier-curve"></a>Como criar uma curva de Bézier cúbica
Este exemplo mostra como criar uma curva de Bézier cúbica. Para criar uma curva de Bézier cúbica, use as classes <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>e <xref:System.Windows.Media.BezierSegment>.  Para exibir a geometria resultante, use um elemento <xref:System.Windows.Shapes.Path> ou use-o com uma <xref:System.Windows.Media.GeometryDrawing> ou uma <xref:System.Windows.Media.DrawingContext>. Nos exemplos a seguir, uma curva de Bézier cúbica é desenhada de (10, 100) para (300, 100). A curva tem pontos de controle de (100, 0) e (200, 200).  
  
## <a name="example"></a>Exemplo  
 XAML  
  
 No [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], você pode usar a sintaxe de marcação abreviada para descrever um caminho.  
  
 [!code-xaml[GeometrySample#53](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#53)]  
  
 XAML  
  
 Em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você também pode desenhar uma curva de Bézier cúbica usando marcas de objeto. O seguinte é equivalente ao exemplo de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] anterior.  
  
 [!code-xaml[GeometrySample#33](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#33)]  
  
 Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, confira o [Exemplo de geometrias](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).  
  
## <a name="see-also"></a>Confira também

- [Criar um arco elíptico](how-to-create-an-elliptical-arc.md)
- [Criar um LineSegment em uma PathGeometry](how-to-create-a-linesegment-in-a-pathgeometry.md)
- [Criar uma curva de Bézier cúbica](how-to-create-a-cubic-bezier-curve.md)
- [Criar uma curva de Bézier quadrática](how-to-create-a-quadratic-bezier-curve.md)
