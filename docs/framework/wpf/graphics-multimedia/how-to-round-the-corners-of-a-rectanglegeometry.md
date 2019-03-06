---
title: 'Como: Arredondar os cantos de um RectangleGeometry'
ms.date: 03/30/2017
helpviewer_keywords:
- corners [WPF], rounding
- RectangleGeometry class [WPF], rounding corners
- graphics [WPF], rounding corners of RectangleGeometry objects [WPF]
- rounding corners of RectangleGeometry objects [WPF]
ms.assetid: 926644bc-1357-4c0b-ac81-694bd090ae87
ms.openlocfilehash: f00d7a7cd6117318efb17645bbb9df279c97adff
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378529"
---
# <a name="how-to-round-the-corners-of-a-rectanglegeometry"></a>Como: Arredondar os cantos de um RectangleGeometry
Para arredondar os cantos de um <xref:System.Windows.Media.RectangleGeometry>, defina sua <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> e <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> propriedades para um valor maior que zero. Quanto maior os valores, mais redondos serão os cantos do retângulo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra várias <xref:System.Windows.Media.RectangleGeometry> objetos com diferentes <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> e <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> configurações. O <xref:System.Windows.Media.RectangleGeometry> os objetos são exibidos usando <xref:System.Windows.Shapes.Path> elementos.  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRoundedRectangleGeometryExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/RectangleGeometryRoundedCornerExample.xaml#graphicsmmroundedrectanglegeometryexamplewholepage)]  
  
 ![Retângulos com diferente RadiusX&#47;configurações RadiusY](./media/graphicsmm-rounded.png "graphicsmm_rounded")  
Retângulos com cantos arredondados  
  
## <a name="see-also"></a>Consulte também
- [Visão geral de geometria](geometry-overview.md)
- [Criar uma forma composta](how-to-create-a-composite-shape.md)
- [Criar uma forma usando um PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md)
