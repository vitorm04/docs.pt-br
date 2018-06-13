---
title: Como criar um arco elíptico
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], elliptical arcs
- elliptical arcs [WPF], creating
- arcs [WPF], elliptical
ms.assetid: 3dcfe502-3485-45de-99fb-d53a1367c484
ms.openlocfilehash: 3b8aab2f2d79b1158adb006049b27a9f15575216
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560884"
---
# <a name="how-to-create-an-elliptical-arc"></a><span data-ttu-id="e173f-102">Como criar um arco elíptico</span><span class="sxs-lookup"><span data-stu-id="e173f-102">How to: Create an Elliptical Arc</span></span>
<span data-ttu-id="e173f-103">Este exemplo mostra como desenhar um arco elíptico. Para criar um arco elíptico, use o <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, e <xref:System.Windows.Media.ArcSegment> classes.</span><span class="sxs-lookup"><span data-stu-id="e173f-103">This example shows how to draw an elliptical arc. To create an elliptical arc, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.ArcSegment> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e173f-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e173f-104">Example</span></span>  
 <span data-ttu-id="e173f-105">Nos exemplos a seguir, um arco elíptico é desenhado de (10,100) a (200,100).</span><span class="sxs-lookup"><span data-stu-id="e173f-105">In the following examples, an elliptical arc is drawn from (10,100) to (200,100).</span></span> <span data-ttu-id="e173f-106">O arco possui um <xref:System.Windows.Media.ArcSegment.Size%2A> de 100 por 50 pixels de independente de dispositivo, um <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> de 45 graus, um <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> de `true`e um <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> de <xref:System.Windows.Media.SweepDirection.Counterclockwise>.</span><span class="sxs-lookup"><span data-stu-id="e173f-106">The arc has a <xref:System.Windows.Media.ArcSegment.Size%2A> of 100 by 50 device-independent pixels, a <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> of 45 degrees, an <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> setting of `true`, and a <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> of <xref:System.Windows.Media.SweepDirection.Counterclockwise>.</span></span>  
  
 <span data-ttu-id="e173f-107">[xaml]</span><span class="sxs-lookup"><span data-stu-id="e173f-107">[xaml]</span></span>  
  
 <span data-ttu-id="e173f-108">Em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], você pode usar a sintaxe para descrever um caminho.</span><span class="sxs-lookup"><span data-stu-id="e173f-108">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you can use attribute syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#56](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#56)]  
  
 <span data-ttu-id="e173f-109">[xaml]</span><span class="sxs-lookup"><span data-stu-id="e173f-109">[xaml]</span></span>  
  
 <span data-ttu-id="e173f-110">(Observe que esta sintaxe de atributo, na verdade, cria um <xref:System.Windows.Media.StreamGeometry>, uma versão leve de um <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="e173f-110">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="e173f-111">Para obter mais informações, consulte o [sintaxe de marcação de caminho](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) página.)</span><span class="sxs-lookup"><span data-stu-id="e173f-111">For more information, see the [Path Markup Syntax](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) page.)</span></span>  
  
 <span data-ttu-id="e173f-112">Em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você também pode desenhar um arco elíptico explicitamente usando marcas de objetos.</span><span class="sxs-lookup"><span data-stu-id="e173f-112">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can also draw an elliptical arc by explicitly using object tags.</span></span> <span data-ttu-id="e173f-113">A seguir é equivalente ao anterior [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] marcação.</span><span class="sxs-lookup"><span data-stu-id="e173f-113">The following is equivalent to the preceding [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[GeometrySample#36](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#36)]  
  
 <span data-ttu-id="e173f-114">Este exemplo é parte de um exemplo maior.</span><span class="sxs-lookup"><span data-stu-id="e173f-114">This example is part of a larger sample.</span></span> <span data-ttu-id="e173f-115">Para o exemplo completo, consulte o [geometrias exemplo](http://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="e173f-115">For the complete sample, see the [Geometries Sample](http://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e173f-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e173f-116">See Also</span></span>  
 [<span data-ttu-id="e173f-117">Criar uma curva de Bézier quadrática</span><span class="sxs-lookup"><span data-stu-id="e173f-117">Create a Quadratic Bezier Curve</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md)  
 [<span data-ttu-id="e173f-118">Criar uma curva de Bézier cúbica</span><span class="sxs-lookup"><span data-stu-id="e173f-118">Create a Cubic Bezier Curve</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)
