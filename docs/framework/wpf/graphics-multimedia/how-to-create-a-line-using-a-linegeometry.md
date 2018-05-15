---
title: Como criar uma linha usando um LineGeometry
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], lines
ms.assetid: 41231b22-1f74-4c26-a8e7-a55b29f8f6bd
ms.openlocfilehash: 8db33fc5c611dcbcae50c71ada1c6b6f9fd9bd29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-line-using-a-linegeometry"></a><span data-ttu-id="c2c13-102">Como criar uma linha usando um LineGeometry</span><span class="sxs-lookup"><span data-stu-id="c2c13-102">How to: Create a Line Using a LineGeometry</span></span>
<span data-ttu-id="c2c13-103">Este exemplo mostra como usar o <xref:System.Windows.Media.LineGeometry> classe para descrever uma linha.</span><span class="sxs-lookup"><span data-stu-id="c2c13-103">This example shows how to use the <xref:System.Windows.Media.LineGeometry> class to describe a line.</span></span> <span data-ttu-id="c2c13-104">Um <xref:System.Windows.Media.LineGeometry> é definida por seus pontos de início e término.</span><span class="sxs-lookup"><span data-stu-id="c2c13-104">A <xref:System.Windows.Media.LineGeometry> is defined by its start and end points.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2c13-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c2c13-105">Example</span></span>  
 <span data-ttu-id="c2c13-106">O exemplo a seguir mostra como criar e processar um <xref:System.Windows.Media.LineGeometry>.</span><span class="sxs-lookup"><span data-stu-id="c2c13-106">The following example shows how to create and render a <xref:System.Windows.Media.LineGeometry>.</span></span>  <span data-ttu-id="c2c13-107">Um <xref:System.Windows.Shapes.Path> elemento é usado para processar a linha.</span><span class="sxs-lookup"><span data-stu-id="c2c13-107">A <xref:System.Windows.Shapes.Path> element is used to render the line.</span></span>  <span data-ttu-id="c2c13-108">Como uma linha não tem nenhuma área, o <xref:System.Windows.Shapes.Path> do objeto <xref:System.Windows.Shapes.Shape.Fill%2A> não for especificado; em vez disso, o <xref:System.Windows.Shapes.Shape.Stroke%2A> e <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> propriedades são usadas.</span><span class="sxs-lookup"><span data-stu-id="c2c13-108">Since a line has no area, the <xref:System.Windows.Shapes.Path> object's <xref:System.Windows.Shapes.Shape.Fill%2A> is not specified; instead the <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties are used.</span></span>  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 <span data-ttu-id="c2c13-109">![Um LineGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-line.gif "graphicsmm_line")</span><span class="sxs-lookup"><span data-stu-id="c2c13-109">![A LineGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-line.gif "graphicsmm_line")</span></span>  
<span data-ttu-id="c2c13-110">Uma LineGeometry desenhada de (10,20) para (100,130)</span><span class="sxs-lookup"><span data-stu-id="c2c13-110">A LineGeometry drawn from (10,20) to (100,130)</span></span>  
  
 <span data-ttu-id="c2c13-111">Outras classes de geometria simples incluem <xref:System.Windows.Media.LineGeometry> e <xref:System.Windows.Media.EllipseGeometry>.</span><span class="sxs-lookup"><span data-stu-id="c2c13-111">Other simple geometry classes include <xref:System.Windows.Media.LineGeometry> and <xref:System.Windows.Media.EllipseGeometry>.</span></span> <span data-ttu-id="c2c13-112">Esses geometrias, bem como aquelas mais complexas, também podem ser criadas usando um <xref:System.Windows.Media.PathGeometry> ou <xref:System.Windows.Media.StreamGeometry>.</span><span class="sxs-lookup"><span data-stu-id="c2c13-112">These geometries, as well as more complex ones, can also be created using a <xref:System.Windows.Media.PathGeometry> or <xref:System.Windows.Media.StreamGeometry>.</span></span> <span data-ttu-id="c2c13-113">Para obter mais informações, consulte o [visão geral de geometria](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c2c13-113">For more information, see the [Geometry Overview](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2c13-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c2c13-114">See Also</span></span>  
 [<span data-ttu-id="c2c13-115">Visão geral de geometria</span><span class="sxs-lookup"><span data-stu-id="c2c13-115">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [<span data-ttu-id="c2c13-116">Criar uma forma composta</span><span class="sxs-lookup"><span data-stu-id="c2c13-116">Create a Composite Shape</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)  
 [<span data-ttu-id="c2c13-117">Criar uma forma usando um PathGeometry</span><span class="sxs-lookup"><span data-stu-id="c2c13-117">Create a Shape by Using a PathGeometry</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)
