---
title: Como criar uma forma composta
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- shapes [WPF], composite
- composite shapes [WPF]
- graphics [WPF], composite shapes
ms.assetid: 8e5c7ef4-d7ed-4c43-afc9-ca01325c300b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2ecb4ecdc5c83cbb6f2b4faee9cb3654939bd346
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-composite-shape"></a>Como criar uma forma composta
Este exemplo mostra como criar formas compostas utilizando <xref:System.Windows.Media.Geometry> objetos e exibi-los usando um <xref:System.Windows.Shapes.Path> elemento. No exemplo a seguir, uma <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.EllipseGeometry>e um <xref:System.Windows.Media.RectangleGeometry> são usados com um <xref:System.Windows.Media.GeometryGroup> para criar uma forma de composição. As geometrias são então desenhadas utilizando um <xref:System.Windows.Shapes.Path> elemento.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[GeometrySample#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#19)]  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/CompositeShapeExample.cs#compositeshapecodeexampleinline1)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/compositeshapeexample.vb#compositeshapecodeexampleinline1)]  
  
 A ilustração a seguir mostra a forma criada no exemplo anterior.  
  
 ![Uma geometria composta criada com um GeometryGroup](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")  
Geometria composta  
  
 Formas mais complexas, como polígonos e formas com segmentos curvos, podem ser criadas utilizando um <xref:System.Windows.Media.PathGeometry>. Para obter um exemplo mostrando como criar uma forma usando uma <xref:System.Windows.Media.PathGeometry>, consulte [criar uma forma usando um PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md).  Embora este exemplo renderize uma forma na tela utilizando um <xref:System.Windows.Shapes.Path> elemento <xref:System.Windows.Media.Geometry> objetos também podem ser usados para descrever o conteúdo de um <xref:System.Windows.Media.GeometryDrawing> ou <xref:System.Windows.Media.DrawingContext>. Eles também podem ser usados para recortes e testes de clique.  
  
 Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, confira o [Exemplo de geometrias](http://go.microsoft.com/fwlink/?LinkID=159989).
