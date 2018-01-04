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
# <a name="how-to-create-a-composite-shape"></a><span data-ttu-id="9a5c9-102">Como criar uma forma composta</span><span class="sxs-lookup"><span data-stu-id="9a5c9-102">How to: Create a Composite Shape</span></span>
<span data-ttu-id="9a5c9-103">Este exemplo mostra como criar formas compostas utilizando <xref:System.Windows.Media.Geometry> objetos e exibi-los usando um <xref:System.Windows.Shapes.Path> elemento.</span><span class="sxs-lookup"><span data-stu-id="9a5c9-103">This example shows how to create composite shapes using <xref:System.Windows.Media.Geometry> objects and display them using a <xref:System.Windows.Shapes.Path> element.</span></span> <span data-ttu-id="9a5c9-104">No exemplo a seguir, uma <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.EllipseGeometry>e um <xref:System.Windows.Media.RectangleGeometry> são usados com um <xref:System.Windows.Media.GeometryGroup> para criar uma forma de composição.</span><span class="sxs-lookup"><span data-stu-id="9a5c9-104">In the following example, a <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.EllipseGeometry>, and a <xref:System.Windows.Media.RectangleGeometry> are used with a <xref:System.Windows.Media.GeometryGroup> to create a composite shape.</span></span> <span data-ttu-id="9a5c9-105">As geometrias são então desenhadas utilizando um <xref:System.Windows.Shapes.Path> elemento.</span><span class="sxs-lookup"><span data-stu-id="9a5c9-105">The geometries are then drawn using a <xref:System.Windows.Shapes.Path> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a5c9-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9a5c9-106">Example</span></span>  
 [!code-xaml[GeometrySample#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#19)]  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/CompositeShapeExample.cs#compositeshapecodeexampleinline1)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/compositeshapeexample.vb#compositeshapecodeexampleinline1)]  
  
 <span data-ttu-id="9a5c9-107">A ilustração a seguir mostra a forma criada no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="9a5c9-107">The following illustration shows the shape created in the previous example.</span></span>  
  
 <span data-ttu-id="9a5c9-108">![Uma geometria composta criada com um GeometryGroup](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")</span><span class="sxs-lookup"><span data-stu-id="9a5c9-108">![A composite geometry created using a GeometryGroup](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")</span></span>  
<span data-ttu-id="9a5c9-109">Geometria composta</span><span class="sxs-lookup"><span data-stu-id="9a5c9-109">Composite Geometry</span></span>  
  
 <span data-ttu-id="9a5c9-110">Formas mais complexas, como polígonos e formas com segmentos curvos, podem ser criadas utilizando um <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="9a5c9-110">More complex shapes, such as polygons and shapes with curved segments, may be created using a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="9a5c9-111">Para obter um exemplo mostrando como criar uma forma usando uma <xref:System.Windows.Media.PathGeometry>, consulte [criar uma forma usando um PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md).</span><span class="sxs-lookup"><span data-stu-id="9a5c9-111">For an example showing how to create a shape using a <xref:System.Windows.Media.PathGeometry>, see [Create a Shape by Using a PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md).</span></span>  <span data-ttu-id="9a5c9-112">Embora este exemplo renderize uma forma na tela utilizando um <xref:System.Windows.Shapes.Path> elemento <xref:System.Windows.Media.Geometry> objetos também podem ser usados para descrever o conteúdo de um <xref:System.Windows.Media.GeometryDrawing> ou <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="9a5c9-112">Although this example renders a shape to the screen using a <xref:System.Windows.Shapes.Path> element, <xref:System.Windows.Media.Geometry> objects may also be used to describe the contents of a <xref:System.Windows.Media.GeometryDrawing> or a <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="9a5c9-113">Eles também podem ser usados para recortes e testes de clique.</span><span class="sxs-lookup"><span data-stu-id="9a5c9-113">They may also be used for clipping and hit-testing.</span></span>  
  
 <span data-ttu-id="9a5c9-114">Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, confira o [Exemplo de geometrias](http://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="9a5c9-114">This example is part of larger sample; for the complete sample, see the [Geometries Sample](http://go.microsoft.com/fwlink/?LinkID=159989).</span></span>
