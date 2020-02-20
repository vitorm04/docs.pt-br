---
title: Como criar uma curva de Bézier cúbica
ms.date: 03/30/2017
helpviewer_keywords:
- curves [WPF], cubic Bezier
- Bezier curves [WPF], cubic
- graphics [WPF], cubic Bezier curves
- cubic Bezier curves [WPF]
ms.assetid: 450a3a77-7c57-48b0-a008-0f6051add980
ms.openlocfilehash: c12bd84fcebb3acebb80bef5f4479ad535fd6691
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452104"
---
# <a name="how-to-create-a-cubic-bezier-curve"></a><span data-ttu-id="568e2-102">Como criar uma curva de Bézier cúbica</span><span class="sxs-lookup"><span data-stu-id="568e2-102">How to: Create a Cubic Bezier Curve</span></span>
<span data-ttu-id="568e2-103">Este exemplo mostra como criar uma curva de Bézier cúbica.</span><span class="sxs-lookup"><span data-stu-id="568e2-103">This example shows how to create a cubic Bezier curve.</span></span> <span data-ttu-id="568e2-104">Para criar uma curva de Bézier cúbica, use as classes <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>e <xref:System.Windows.Media.BezierSegment>.</span><span class="sxs-lookup"><span data-stu-id="568e2-104">To create a cubic Bezier curve, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.BezierSegment> classes.</span></span>  <span data-ttu-id="568e2-105">Para exibir a geometria resultante, use um elemento <xref:System.Windows.Shapes.Path> ou use-o com uma <xref:System.Windows.Media.GeometryDrawing> ou uma <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="568e2-105">To display the resulting geometry, use a <xref:System.Windows.Shapes.Path> element, or use it with a <xref:System.Windows.Media.GeometryDrawing> or a <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="568e2-106">Nos exemplos a seguir, uma curva de Bézier cúbica é desenhada de (10, 100) para (300, 100).</span><span class="sxs-lookup"><span data-stu-id="568e2-106">In the following examples, a cubic Bezier curve is drawn from (10, 100) to (300, 100).</span></span> <span data-ttu-id="568e2-107">A curva tem pontos de controle de (100, 0) e (200, 200).</span><span class="sxs-lookup"><span data-stu-id="568e2-107">The curve has control points of (100, 0) and (200, 200).</span></span>  
  
## <a name="example"></a><span data-ttu-id="568e2-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="568e2-108">Example</span></span>  
 <span data-ttu-id="568e2-109">XAML</span><span class="sxs-lookup"><span data-stu-id="568e2-109">[xaml]</span></span>  
  
 <span data-ttu-id="568e2-110">No [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], você pode usar a sintaxe de marcação abreviada para descrever um caminho.</span><span class="sxs-lookup"><span data-stu-id="568e2-110">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you may use abbreviated markup syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#53](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#53)]  
  
 <span data-ttu-id="568e2-111">XAML</span><span class="sxs-lookup"><span data-stu-id="568e2-111">[xaml]</span></span>  
  
 <span data-ttu-id="568e2-112">Em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você também pode desenhar uma curva de Bézier cúbica usando marcas de objeto.</span><span class="sxs-lookup"><span data-stu-id="568e2-112">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can also draw a cubic Bezier curve using object tags.</span></span> <span data-ttu-id="568e2-113">O seguinte é equivalente ao exemplo de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] anterior.</span><span class="sxs-lookup"><span data-stu-id="568e2-113">The following is equivalent to the previous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example.</span></span>  
  
 [!code-xaml[GeometrySample#33](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#33)]  
  
 <span data-ttu-id="568e2-114">Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, confira o [Exemplo de geometrias](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span><span class="sxs-lookup"><span data-stu-id="568e2-114">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="568e2-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="568e2-115">See also</span></span>

- [<span data-ttu-id="568e2-116">Criar um arco elíptico</span><span class="sxs-lookup"><span data-stu-id="568e2-116">Create an Elliptical Arc</span></span>](how-to-create-an-elliptical-arc.md)
- [<span data-ttu-id="568e2-117">Criar um LineSegment em uma PathGeometry</span><span class="sxs-lookup"><span data-stu-id="568e2-117">Create a LineSegment in a PathGeometry</span></span>](how-to-create-a-linesegment-in-a-pathgeometry.md)
- [<span data-ttu-id="568e2-118">Criar uma curva de Bézier cúbica</span><span class="sxs-lookup"><span data-stu-id="568e2-118">Create a Cubic Bezier Curve</span></span>](how-to-create-a-cubic-bezier-curve.md)
- [<span data-ttu-id="568e2-119">Criar uma curva de Bézier quadrática</span><span class="sxs-lookup"><span data-stu-id="568e2-119">Create a Quadratic Bezier Curve</span></span>](how-to-create-a-quadratic-bezier-curve.md)
