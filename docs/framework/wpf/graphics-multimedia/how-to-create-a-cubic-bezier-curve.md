---
title: Como criar uma curva de Bézier cúbica
ms.date: 03/30/2017
helpviewer_keywords:
- curves [WPF], cubic Bezier
- Bezier curves [WPF], cubic
- graphics [WPF], cubic Bezier curves
- cubic Bezier curves [WPF]
ms.assetid: 450a3a77-7c57-48b0-a008-0f6051add980
ms.openlocfilehash: 6332129179e1934e5a37c7a1a40ef5f46ab669a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-cubic-bezier-curve"></a><span data-ttu-id="5ca5e-102">Como criar uma curva de Bézier cúbica</span><span class="sxs-lookup"><span data-stu-id="5ca5e-102">How to: Create a Cubic Bezier Curve</span></span>
<span data-ttu-id="5ca5e-103">Este exemplo mostra como criar uma curva cúbica de Bezier.</span><span class="sxs-lookup"><span data-stu-id="5ca5e-103">This example shows how to create a cubic Bezier curve.</span></span> <span data-ttu-id="5ca5e-104">Para criar uma curva cúbica de Bezier, use o <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, e <xref:System.Windows.Media.BezierSegment> classes.</span><span class="sxs-lookup"><span data-stu-id="5ca5e-104">To create a cubic Bezier curve, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.BezierSegment> classes.</span></span>  <span data-ttu-id="5ca5e-105">Para exibir o resultado geométrico, use um <xref:System.Windows.Shapes.Path> elemento, ou usá-la com um <xref:System.Windows.Media.GeometryDrawing> ou <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="5ca5e-105">To display the resulting geometry, use a <xref:System.Windows.Shapes.Path> element, or use it with a <xref:System.Windows.Media.GeometryDrawing> or a <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="5ca5e-106">Nos exemplos a seguir, uma curva cúbica de Bezier é desenhada de (10, 100) para (300, 100).</span><span class="sxs-lookup"><span data-stu-id="5ca5e-106">In the following examples, a cubic Bezier curve is drawn from (10, 100) to (300, 100).</span></span> <span data-ttu-id="5ca5e-107">A curva tem pontos de controle de (100, 0) e (200, 200).</span><span class="sxs-lookup"><span data-stu-id="5ca5e-107">The curve has control points of (100, 0) and (200, 200).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ca5e-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ca5e-108">Example</span></span>  
 <span data-ttu-id="5ca5e-109">[xaml]</span><span class="sxs-lookup"><span data-stu-id="5ca5e-109">[xaml]</span></span>  
  
 <span data-ttu-id="5ca5e-110">Em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], você pode usar a marcação de sintaxe abreviada para descrever um caminho.</span><span class="sxs-lookup"><span data-stu-id="5ca5e-110">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you may use abbreviated markup syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#53](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#53)]  
  
 <span data-ttu-id="5ca5e-111">[xaml]</span><span class="sxs-lookup"><span data-stu-id="5ca5e-111">[xaml]</span></span>  
  
 <span data-ttu-id="5ca5e-112">Em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você também pode desenhar uma curva cúbica de Bezier com marcas de objetos.</span><span class="sxs-lookup"><span data-stu-id="5ca5e-112">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can also draw a cubic Bezier curve using object tags.</span></span> <span data-ttu-id="5ca5e-113">A seguir é equivalente ao anterior [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] exemplo.</span><span class="sxs-lookup"><span data-stu-id="5ca5e-113">The following is equivalent to the previous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example.</span></span>  
  
 [!code-xaml[GeometrySample#33](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#33)]  
  
 <span data-ttu-id="5ca5e-114">Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, confira o [Exemplo de geometrias](http://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="5ca5e-114">This example is part of larger sample; for the complete sample, see the [Geometries Sample](http://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ca5e-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5ca5e-115">See Also</span></span>  
 [<span data-ttu-id="5ca5e-116">Criar um arco elíptico</span><span class="sxs-lookup"><span data-stu-id="5ca5e-116">Create an Elliptical Arc</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md)  
 [<span data-ttu-id="5ca5e-117">Criar um LineSegment em uma PathGeometry</span><span class="sxs-lookup"><span data-stu-id="5ca5e-117">Create a LineSegment in a PathGeometry</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-linesegment-in-a-pathgeometry.md)  
 [<span data-ttu-id="5ca5e-118">Criar uma curva de Bézier cúbica</span><span class="sxs-lookup"><span data-stu-id="5ca5e-118">Create a Cubic Bezier Curve</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)  
 [<span data-ttu-id="5ca5e-119">Criar uma curva de Bézier quadrática</span><span class="sxs-lookup"><span data-stu-id="5ca5e-119">Create a Quadratic Bezier Curve</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md)
