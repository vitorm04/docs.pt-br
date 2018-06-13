---
title: Como definir um retângulo usando um RectangleGeometry
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rectangles
- rectangles [WPF], creating with RectangleGeometry class
ms.assetid: e40b8a8e-54b8-416b-a9f2-be6dca9fdf0b
ms.openlocfilehash: 5d2ec6aec1eea8528ea6b43f72f4820b8bc19a37
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560417"
---
# <a name="how-to-define-a-rectangle-using-a-rectanglegeometry"></a>Como definir um retângulo usando um RectangleGeometry
Este exemplo descreve como usar o <xref:System.Windows.Media.RectangleGeometry> classe para descrever um retângulo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como criar e processar um <xref:System.Windows.Media.RectangleGeometry>.  A posição relativa e as dimensões do retângulo são definidas por um <xref:System.Windows.Rect> estrutura. A posição relativa é `50,50` e a altura e a largura são ambos `25` criando um quadrado. O interior do retângulo é pintado com um <xref:System.Windows.Media.Brushes.LemonChiffon%2A> pincel e seu contorno é pintado com um <xref:System.Windows.Media.Brushes.Black%2A> traço com uma espessura de `1`.  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 ![Uma geometria de retângulos](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rectangle.gif "graphicsmm_rectangle")  
RectangleGeometry  
  
 Embora esse exemplo tenha usado um <xref:System.Windows.Shapes.Path> elemento para renderizar o <xref:System.Windows.Media.RectangleGeometry>, há muitas outras maneiras de usar <xref:System.Windows.Media.RectangleGeometry> objetos. Por exemplo, um <xref:System.Windows.Media.RectangleGeometry> pode ser usado para especificar o <xref:System.Windows.UIElement.Clip%2A> de um <xref:System.Windows.UIElement> ou <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> de um <xref:System.Windows.Media.GeometryDrawing>.  
  
 Outras classes de geometria simples incluem <xref:System.Windows.Media.LineGeometry> e <xref:System.Windows.Media.EllipseGeometry>. Esses geometrias, bem como aquelas mais complexas, também podem ser criadas usando um <xref:System.Windows.Media.PathGeometry> ou <xref:System.Windows.Media.StreamGeometry>.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de geometria](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [Criar uma forma composta](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)  
 [Criar uma forma usando um PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)
