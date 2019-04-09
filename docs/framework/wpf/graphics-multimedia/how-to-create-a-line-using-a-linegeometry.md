---
title: 'Como: Criar uma linha usando um LineGeometry'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], lines
ms.assetid: 41231b22-1f74-4c26-a8e7-a55b29f8f6bd
ms.openlocfilehash: f8c334a54f78aec7af91064a447fd18f23dcfbdc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59123052"
---
# <a name="how-to-create-a-line-using-a-linegeometry"></a>Como: Criar uma linha usando um LineGeometry
Este exemplo mostra como usar o <xref:System.Windows.Media.LineGeometry> classe para descrever uma linha. Um <xref:System.Windows.Media.LineGeometry> é definida por seus pontos inicial e final.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como criar e renderizar uma <xref:System.Windows.Media.LineGeometry>.  Um <xref:System.Windows.Shapes.Path> elemento é usado para renderizar a linha.  Uma vez que uma linha não tem nenhuma área, o <xref:System.Windows.Shapes.Path> do objeto <xref:System.Windows.Shapes.Shape.Fill%2A> não for especificado; em vez disso, o <xref:System.Windows.Shapes.Shape.Stroke%2A> e <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> propriedades são usadas.  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 ![Uma LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")  
Uma LineGeometry desenhada de (10,20) para (100,130)  
  
 Outras classes de geometria simples incluem <xref:System.Windows.Media.LineGeometry> e <xref:System.Windows.Media.EllipseGeometry>. Esses geometrias, bem como aquelas mais complexas, também podem ser criadas usando um <xref:System.Windows.Media.PathGeometry> ou <xref:System.Windows.Media.StreamGeometry>. Para obter mais informações, consulte o [visão geral de geometria](geometry-overview.md).  
  
## <a name="see-also"></a>Consulte também

- [Visão geral da geometria](geometry-overview.md)
- [Criar uma forma composta](how-to-create-a-composite-shape.md)
- [Criar uma forma usando um PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md)
