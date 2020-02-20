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
# <a name="how-to-create-a-composite-shape"></a><span data-ttu-id="1969f-102">Como criar uma forma composta</span><span class="sxs-lookup"><span data-stu-id="1969f-102">How to: Create a Composite Shape</span></span>
<span data-ttu-id="1969f-103">Este exemplo mostra como criar formas compostas usando objetos <xref:System.Windows.Media.Geometry> e exibi-los usando um elemento <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="1969f-103">This example shows how to create composite shapes using <xref:System.Windows.Media.Geometry> objects and display them using a <xref:System.Windows.Shapes.Path> element.</span></span> <span data-ttu-id="1969f-104">No exemplo a seguir, um <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.EllipseGeometry>e um <xref:System.Windows.Media.RectangleGeometry> são usados com um <xref:System.Windows.Media.GeometryGroup> para criar uma forma composta.</span><span class="sxs-lookup"><span data-stu-id="1969f-104">In the following example, a <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.EllipseGeometry>, and a <xref:System.Windows.Media.RectangleGeometry> are used with a <xref:System.Windows.Media.GeometryGroup> to create a composite shape.</span></span> <span data-ttu-id="1969f-105">Em seguida, as geometrias são desenhadas usando um elemento <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="1969f-105">The geometries are then drawn using a <xref:System.Windows.Shapes.Path> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1969f-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1969f-106">Example</span></span>  
 [!code-xaml[GeometrySample#19](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#19)]  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/CompositeShapeExample.cs#compositeshapecodeexampleinline1)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/compositeshapeexample.vb#compositeshapecodeexampleinline1)]  
  
 <span data-ttu-id="1969f-107">A ilustração a seguir mostra a forma criada no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="1969f-107">The following illustration shows the shape created in the previous example.</span></span>  
  
 <span data-ttu-id="1969f-108">![Uma geometria composta criada com um GeometryGroup](./media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")</span><span class="sxs-lookup"><span data-stu-id="1969f-108">![A composite geometry created using a GeometryGroup](./media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")</span></span>  
<span data-ttu-id="1969f-109">Geometria composta</span><span class="sxs-lookup"><span data-stu-id="1969f-109">Composite Geometry</span></span>  
  
 <span data-ttu-id="1969f-110">Formas mais complexas, como polígonos e formas com segmentos curvos, podem ser criadas usando um <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="1969f-110">More complex shapes, such as polygons and shapes with curved segments, may be created using a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="1969f-111">Para obter um exemplo que mostra como criar uma forma usando uma <xref:System.Windows.Media.PathGeometry>, consulte [criar uma forma usando um PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).</span><span class="sxs-lookup"><span data-stu-id="1969f-111">For an example showing how to create a shape using a <xref:System.Windows.Media.PathGeometry>, see [Create a Shape by Using a PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).</span></span>  <span data-ttu-id="1969f-112">Embora este exemplo processe uma forma para a tela usando um elemento <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Media.Geometry> objetos também podem ser usados para descrever o conteúdo de um <xref:System.Windows.Media.GeometryDrawing> ou um <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="1969f-112">Although this example renders a shape to the screen using a <xref:System.Windows.Shapes.Path> element, <xref:System.Windows.Media.Geometry> objects may also be used to describe the contents of a <xref:System.Windows.Media.GeometryDrawing> or a <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="1969f-113">Eles também podem ser usados para recortes e testes de clique.</span><span class="sxs-lookup"><span data-stu-id="1969f-113">They may also be used for clipping and hit-testing.</span></span>  
  
 <span data-ttu-id="1969f-114">Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, confira o [Exemplo de geometrias](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span><span class="sxs-lookup"><span data-stu-id="1969f-114">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span></span>
