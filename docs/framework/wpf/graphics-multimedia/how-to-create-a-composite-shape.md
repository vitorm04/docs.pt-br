---
title: Como criar uma forma composta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- shapes [WPF], composite
- composite shapes [WPF]
- graphics [WPF], composite shapes
ms.assetid: 8e5c7ef4-d7ed-4c43-afc9-ca01325c300b
ms.openlocfilehash: c56053f2b07d6055deac5097a68fd7b80ad704ba
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452091"
---
# <a name="how-to-create-a-composite-shape"></a>Como criar uma forma composta
Este exemplo mostra como criar formas compostas usando objetos <xref:System.Windows.Media.Geometry> e exibi-los usando um elemento <xref:System.Windows.Shapes.Path>. No exemplo a seguir, um <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.EllipseGeometry>e um <xref:System.Windows.Media.RectangleGeometry> são usados com um <xref:System.Windows.Media.GeometryGroup> para criar uma forma composta. Em seguida, as geometrias são desenhadas usando um elemento <xref:System.Windows.Shapes.Path>.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[GeometrySample#19](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#19)]  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/CompositeShapeExample.cs#compositeshapecodeexampleinline1)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/compositeshapeexample.vb#compositeshapecodeexampleinline1)]  
  
 A ilustração a seguir mostra a forma criada no exemplo anterior.  
  
 ![Uma geometria composta criada com um GeometryGroup](./media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")  
Geometria composta  
  
 Formas mais complexas, como polígonos e formas com segmentos curvos, podem ser criadas usando um <xref:System.Windows.Media.PathGeometry>. Para obter um exemplo que mostra como criar uma forma usando uma <xref:System.Windows.Media.PathGeometry>, consulte [criar uma forma usando um PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).  Embora este exemplo processe uma forma para a tela usando um elemento <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Media.Geometry> objetos também podem ser usados para descrever o conteúdo de um <xref:System.Windows.Media.GeometryDrawing> ou um <xref:System.Windows.Media.DrawingContext>. Eles também podem ser usados para recortes e testes de clique.  
  
 Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, confira o [Exemplo de geometrias](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).
