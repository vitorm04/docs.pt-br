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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61905197"
---
# <a name="how-to-create-a-line-using-a-linegeometry"></a><span data-ttu-id="57ba8-102">Como: Criar uma linha usando um LineGeometry</span><span class="sxs-lookup"><span data-stu-id="57ba8-102">How to: Create a Line Using a LineGeometry</span></span>
<span data-ttu-id="57ba8-103">Este exemplo mostra como usar o <xref:System.Windows.Media.LineGeometry> classe para descrever uma linha.</span><span class="sxs-lookup"><span data-stu-id="57ba8-103">This example shows how to use the <xref:System.Windows.Media.LineGeometry> class to describe a line.</span></span> <span data-ttu-id="57ba8-104">Um <xref:System.Windows.Media.LineGeometry> é definida por seus pontos inicial e final.</span><span class="sxs-lookup"><span data-stu-id="57ba8-104">A <xref:System.Windows.Media.LineGeometry> is defined by its start and end points.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57ba8-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="57ba8-105">Example</span></span>  
 <span data-ttu-id="57ba8-106">O exemplo a seguir mostra como criar e renderizar uma <xref:System.Windows.Media.LineGeometry>.</span><span class="sxs-lookup"><span data-stu-id="57ba8-106">The following example shows how to create and render a <xref:System.Windows.Media.LineGeometry>.</span></span>  <span data-ttu-id="57ba8-107">Um <xref:System.Windows.Shapes.Path> elemento é usado para renderizar a linha.</span><span class="sxs-lookup"><span data-stu-id="57ba8-107">A <xref:System.Windows.Shapes.Path> element is used to render the line.</span></span>  <span data-ttu-id="57ba8-108">Uma vez que uma linha não tem nenhuma área, o <xref:System.Windows.Shapes.Path> do objeto <xref:System.Windows.Shapes.Shape.Fill%2A> não for especificado; em vez disso, o <xref:System.Windows.Shapes.Shape.Stroke%2A> e <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> propriedades são usadas.</span><span class="sxs-lookup"><span data-stu-id="57ba8-108">Since a line has no area, the <xref:System.Windows.Shapes.Path> object's <xref:System.Windows.Shapes.Shape.Fill%2A> is not specified; instead the <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties are used.</span></span>  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 <span data-ttu-id="57ba8-109">![Uma LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")</span><span class="sxs-lookup"><span data-stu-id="57ba8-109">![A LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")</span></span>  
<span data-ttu-id="57ba8-110">Uma LineGeometry desenhada de (10,20) para (100,130)</span><span class="sxs-lookup"><span data-stu-id="57ba8-110">A LineGeometry drawn from (10,20) to (100,130)</span></span>  
  
 <span data-ttu-id="57ba8-111">Outras classes de geometria simples incluem <xref:System.Windows.Media.LineGeometry> e <xref:System.Windows.Media.EllipseGeometry>.</span><span class="sxs-lookup"><span data-stu-id="57ba8-111">Other simple geometry classes include <xref:System.Windows.Media.LineGeometry> and <xref:System.Windows.Media.EllipseGeometry>.</span></span> <span data-ttu-id="57ba8-112">Esses geometrias, bem como aquelas mais complexas, também podem ser criadas usando um <xref:System.Windows.Media.PathGeometry> ou <xref:System.Windows.Media.StreamGeometry>.</span><span class="sxs-lookup"><span data-stu-id="57ba8-112">These geometries, as well as more complex ones, can also be created using a <xref:System.Windows.Media.PathGeometry> or <xref:System.Windows.Media.StreamGeometry>.</span></span> <span data-ttu-id="57ba8-113">Para obter mais informações, consulte o [visão geral de geometria](geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="57ba8-113">For more information, see the [Geometry Overview](geometry-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57ba8-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="57ba8-114">See also</span></span>

- [<span data-ttu-id="57ba8-115">Visão geral de geometria</span><span class="sxs-lookup"><span data-stu-id="57ba8-115">Geometry Overview</span></span>](geometry-overview.md)
- [<span data-ttu-id="57ba8-116">Criar uma forma composta</span><span class="sxs-lookup"><span data-stu-id="57ba8-116">Create a Composite Shape</span></span>](how-to-create-a-composite-shape.md)
- [<span data-ttu-id="57ba8-117">Criar uma forma usando um PathGeometry</span><span class="sxs-lookup"><span data-stu-id="57ba8-117">Create a Shape by Using a PathGeometry</span></span>](how-to-create-a-shape-by-using-a-pathgeometry.md)
