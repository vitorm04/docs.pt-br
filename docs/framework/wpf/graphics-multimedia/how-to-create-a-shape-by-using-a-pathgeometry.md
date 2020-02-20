---
title: Como criar uma forma usando um PathGeometry
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], creating with PathGeometry class
- graphics [WPF], shapes
ms.assetid: 49a4a8b7-e738-45be-8dac-b54a6d8f5b21
ms.openlocfilehash: bdf3c937bfff1780a72e8743bc86a3c3dad2558d
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452039"
---
# <a name="how-to-create-a-shape-by-using-a-pathgeometry"></a>Como criar uma forma usando um PathGeometry
Este exemplo mostra como criar uma forma usando a classe <xref:System.Windows.Media.PathGeometry>. <xref:System.Windows.Media.PathGeometry> objetos são compostos de um ou mais objetos de <xref:System.Windows.Media.PathFigure>; cada <xref:System.Windows.Media.PathFigure> representa uma "figura" ou forma diferente. Cada <xref:System.Windows.Media.PathFigure> é composta de um ou mais objetos <xref:System.Windows.Media.PathSegment>, cada um representando uma parte conectada da figura ou forma. Os tipos de segmento incluem <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.ArcSegment>e <xref:System.Windows.Media.BezierSegment>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa um <xref:System.Windows.Media.PathGeometry> para criar um triângulo. O <xref:System.Windows.Media.PathGeometry> é exibido usando um elemento <xref:System.Windows.Shapes.Path>.  
  
 [!code-xaml[GeometrySample#49](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#49)]  
  
 A ilustração a seguir mostra a forma criada no exemplo anterior.  
  
 ![Uma PathGeometry](./media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")  
Um triângulo criado com um PathGeometry  
  
 O exemplo anterior mostrou como criar uma forma relativamente simples: um triângulo. Um <xref:System.Windows.Media.PathGeometry> também pode ser usado para criar formas mais complexas, incluindo arcos e curvas. Para obter exemplos, veja [Criar um arco elíptico](how-to-create-an-elliptical-arc.md), [Criar uma curva de Bézier cúbica](how-to-create-a-cubic-bezier-curve.md) e [Criar uma curva de Bézier quadrática](how-to-create-a-quadratic-bezier-curve.md).  
  
 Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, confira o [Exemplo de geometrias](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.GeometryDrawing>
- [Visão geral de geometria](geometry-overview.md)
- [Exemplo de geometrias](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry)
