---
title: Como criar um arco elíptico
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], elliptical arcs
- elliptical arcs [WPF], creating
- arcs [WPF], elliptical
ms.assetid: 3dcfe502-3485-45de-99fb-d53a1367c484
ms.openlocfilehash: d0fffbb25f3c5aaceb2cd80af4f1093e44111200
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453059"
---
# <a name="how-to-create-an-elliptical-arc"></a><span data-ttu-id="71dbb-102">Como criar um arco elíptico</span><span class="sxs-lookup"><span data-stu-id="71dbb-102">How to: Create an Elliptical Arc</span></span>
<span data-ttu-id="71dbb-103">Este exemplo mostra como desenhar um arco elíptico. Para criar um arco elíptico, use as classes <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>e <xref:System.Windows.Media.ArcSegment>.</span><span class="sxs-lookup"><span data-stu-id="71dbb-103">This example shows how to draw an elliptical arc. To create an elliptical arc, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.ArcSegment> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71dbb-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71dbb-104">Example</span></span>  
 <span data-ttu-id="71dbb-105">Nos exemplos a seguir, um arco elíptico é desenhado de (10.100) a (200.100).</span><span class="sxs-lookup"><span data-stu-id="71dbb-105">In the following examples, an elliptical arc is drawn from (10,100) to (200,100).</span></span> <span data-ttu-id="71dbb-106">O arco tem um <xref:System.Windows.Media.ArcSegment.Size%2A> de 100 por 50 pixels independentes de dispositivo, uma <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> de 45 graus, uma configuração de <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> de `true`e uma <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> de <xref:System.Windows.Media.SweepDirection.Counterclockwise>.</span><span class="sxs-lookup"><span data-stu-id="71dbb-106">The arc has a <xref:System.Windows.Media.ArcSegment.Size%2A> of 100 by 50 device-independent pixels, a <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> of 45 degrees, an <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> setting of `true`, and a <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> of <xref:System.Windows.Media.SweepDirection.Counterclockwise>.</span></span>  
  
 <span data-ttu-id="71dbb-107">XAML</span><span class="sxs-lookup"><span data-stu-id="71dbb-107">[xaml]</span></span>  
  
 <span data-ttu-id="71dbb-108">No [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], você pode usar a sintaxe de atributo para descrever um caminho.</span><span class="sxs-lookup"><span data-stu-id="71dbb-108">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you can use attribute syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#56](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#56)]  
  
 <span data-ttu-id="71dbb-109">XAML</span><span class="sxs-lookup"><span data-stu-id="71dbb-109">[xaml]</span></span>  
  
 <span data-ttu-id="71dbb-110">(Observe que essa sintaxe de atributo, na verdade, cria uma <xref:System.Windows.Media.StreamGeometry>, uma versão de peso mais leve de um <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="71dbb-110">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="71dbb-111">Para obter mais informações, consulte a página [sintaxe de marcação de caminho](path-markup-syntax.md) .)</span><span class="sxs-lookup"><span data-stu-id="71dbb-111">For more information, see the [Path Markup Syntax](path-markup-syntax.md) page.)</span></span>  
  
 <span data-ttu-id="71dbb-112">Em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você também pode desenhar um arco elíptico explicitamente usando marcas de objeto.</span><span class="sxs-lookup"><span data-stu-id="71dbb-112">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can also draw an elliptical arc by explicitly using object tags.</span></span> <span data-ttu-id="71dbb-113">O seguinte é equivalente à marcação de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] anterior.</span><span class="sxs-lookup"><span data-stu-id="71dbb-113">The following is equivalent to the preceding [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[GeometrySample#36](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#36)]  
  
 <span data-ttu-id="71dbb-114">Este exemplo é parte de um exemplo maior.</span><span class="sxs-lookup"><span data-stu-id="71dbb-114">This example is part of a larger sample.</span></span> <span data-ttu-id="71dbb-115">Para obter o exemplo completo, consulte o [exemplo de geometrias](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span><span class="sxs-lookup"><span data-stu-id="71dbb-115">For the complete sample, see the [Geometries Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71dbb-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="71dbb-116">See also</span></span>

- [<span data-ttu-id="71dbb-117">Criar uma curva de Bézier quadrática</span><span class="sxs-lookup"><span data-stu-id="71dbb-117">Create a Quadratic Bezier Curve</span></span>](how-to-create-a-quadratic-bezier-curve.md)
- [<span data-ttu-id="71dbb-118">Criar uma curva de Bézier cúbica</span><span class="sxs-lookup"><span data-stu-id="71dbb-118">Create a Cubic Bezier Curve</span></span>](how-to-create-a-cubic-bezier-curve.md)
