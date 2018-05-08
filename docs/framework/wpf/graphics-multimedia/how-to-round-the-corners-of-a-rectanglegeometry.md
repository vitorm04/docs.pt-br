---
title: Como arredondar os cantos de um RectangleGeometry
ms.date: 03/30/2017
helpviewer_keywords:
- corners [WPF], rounding
- RectangleGeometry class [WPF], rounding corners
- graphics [WPF], rounding corners of RectangleGeometry objects [WPF]
- rounding corners of RectangleGeometry objects [WPF]
ms.assetid: 926644bc-1357-4c0b-ac81-694bd090ae87
ms.openlocfilehash: e4f1d37e2c0f26967affff14ed6475fc8c0cb28c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-round-the-corners-of-a-rectanglegeometry"></a>Como arredondar os cantos de um RectangleGeometry
Para arredondar os cantos de uma <xref:System.Windows.Media.RectangleGeometry>, defina seu <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> e <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> propriedades para um valor maior que zero. Quanto maior os valores, mais arredondados serão os cantos do retângulo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra vários <xref:System.Windows.Media.RectangleGeometry> objetos com diferentes <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> e <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> configurações. O <xref:System.Windows.Media.RectangleGeometry> objetos são exibidos usando <xref:System.Windows.Shapes.Path> elementos.  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRoundedRectangleGeometryExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/RectangleGeometryRoundedCornerExample.xaml#graphicsmmroundedrectanglegeometryexamplewholepage)]  
  
 ![Retângulos com diferente RadiusX&#47;configurações RadiusY](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rounded.png "graphicsmm_rounded")  
Retângulos com cantos arredondados  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de geometria](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [Criar uma forma composta](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)  
 [Criar uma forma usando um PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)
