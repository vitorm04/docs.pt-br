---
title: Como criar uma forma usando um StreamGeometry
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], shapes
- shapes [WPF], creating with StreamGeometry class
ms.assetid: 08f7c8ce-074b-49cd-9aba-cc9592d4ee51
ms.openlocfilehash: 54819f62b262227017e12b2066a0747107b68900
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-shape-using-a-streamgeometry"></a>Como criar uma forma usando um StreamGeometry
<xref:System.Windows.Media.StreamGeometry> é a alternativa leve para <xref:System.Windows.Media.PathGeometry> para criar formas geométricas. Use um <xref:System.Windows.Media.StreamGeometry> quando você precisa descrever uma geometria complexa, mas não quiser que a sobrecarga de associação de dados, animação ou modificação de suporte. Por exemplo, por causa de sua eficiência, a <xref:System.Windows.Media.StreamGeometry> classe é uma boa escolha para descrever decoradores.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa a sintaxe de atributo para criar um triangular <xref:System.Windows.Media.StreamGeometry> em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 Para obter mais informações sobre <xref:System.Windows.Media.StreamGeometry> sintaxe de atributo, consulte o [sintaxe de marcação de caminho](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) página.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa um <xref:System.Windows.Media.StreamGeometry> para definir um triângulo no código. Primeiro, o exemplo cria um <xref:System.Windows.Media.StreamGeometry>, em seguida, obtém um <xref:System.Windows.Media.StreamGeometryContext> e o utiliza para descrever o triângulo.  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryTriangleExample.cs#streamgeometrytriangleexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometrytriangleexample.vb#streamgeometrytriangleexamplewholepage)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria um método que usa um <xref:System.Windows.Media.StreamGeometry> e <xref:System.Windows.Media.StreamGeometryContext> para definir uma forma geométrica com base em parâmetros especificados.  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryExample.cs#streamgeometryexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometryexample.vb#streamgeometryexamplewholepage)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.PathGeometry>  
 <xref:System.Windows.Media.StreamGeometry>  
 <xref:System.Windows.Media.StreamGeometryContext>  
 [Criar uma forma usando um PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)  
 [Visão geral de geometria](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
