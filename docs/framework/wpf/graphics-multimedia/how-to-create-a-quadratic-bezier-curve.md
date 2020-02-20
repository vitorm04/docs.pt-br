---
title: Como criar uma curva de Bézier quadrática
ms.date: 03/30/2017
helpviewer_keywords:
- Bezier curves [WPF], creating
- quadratic Bezier curves [WPF], creating
- graphics [WPF], quadratic Bezier curves
ms.assetid: cd8fca4a-504e-4fd8-92ea-2969065a6e02
ms.openlocfilehash: caaf967b7cb5447d86dd031beeb16195413b0393
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452065"
---
# <a name="how-to-create-a-quadratic-bezier-curve"></a><span data-ttu-id="a44fb-102">Como criar uma curva de Bézier quadrática</span><span class="sxs-lookup"><span data-stu-id="a44fb-102">How to: Create a Quadratic Bezier Curve</span></span>
<span data-ttu-id="a44fb-103">Este exemplo mostra como criar uma curva de Bézier quadrática.</span><span class="sxs-lookup"><span data-stu-id="a44fb-103">This example shows how to create a quadratic Bezier curve.</span></span>  <span data-ttu-id="a44fb-104">Para criar uma curva de Bézier quadrática, use as classes <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>e <xref:System.Windows.Media.QuadraticBezierSegment>.</span><span class="sxs-lookup"><span data-stu-id="a44fb-104">To create a quadratic Bezier curve, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.QuadraticBezierSegment> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a44fb-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a44fb-105">Example</span></span>  
 <span data-ttu-id="a44fb-106">Nos exemplos a seguir, uma curva de Bezier quadrática é desenhada de (10.100) para (300.100).</span><span class="sxs-lookup"><span data-stu-id="a44fb-106">In the following examples, a quadratic Bezier curve is drawn from (10,100) to (300,100).</span></span> <span data-ttu-id="a44fb-107">A curva tem um ponto de controle de (200.200).</span><span class="sxs-lookup"><span data-stu-id="a44fb-107">The curve has a control point of (200,200).</span></span>  
  
 <span data-ttu-id="a44fb-108">XAML</span><span class="sxs-lookup"><span data-stu-id="a44fb-108">[xaml]</span></span>  
  
 <span data-ttu-id="a44fb-109">No [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], você pode usar a sintaxe de atributo para descrever um caminho.</span><span class="sxs-lookup"><span data-stu-id="a44fb-109">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you can use attribute syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#54](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#54)]  
  
 <span data-ttu-id="a44fb-110">XAML</span><span class="sxs-lookup"><span data-stu-id="a44fb-110">[xaml]</span></span>  
  
 <span data-ttu-id="a44fb-111">(Observe que essa sintaxe de atributo, na verdade, cria uma <xref:System.Windows.Media.StreamGeometry>, uma versão de peso mais leve de um <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="a44fb-111">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="a44fb-112">Para obter mais informações, consulte a página [sintaxe de marcação de caminho](path-markup-syntax.md) .)</span><span class="sxs-lookup"><span data-stu-id="a44fb-112">For more information, see the [Path Markup Syntax](path-markup-syntax.md) page.)</span></span>  
  
 <span data-ttu-id="a44fb-113">Em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você também pode desenhar uma curva de Bezier quadrática usando a sintaxe do elemento de objeto.</span><span class="sxs-lookup"><span data-stu-id="a44fb-113">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you may also draw a quadratic Bezier curve using object element syntax.</span></span> <span data-ttu-id="a44fb-114">O seguinte é equivalente ao exemplo de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] anterior.</span><span class="sxs-lookup"><span data-stu-id="a44fb-114">The following is equivalent to the previous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example.</span></span>  
  
 [!code-xaml[GeometrySample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 <span data-ttu-id="a44fb-115">Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, confira o [Exemplo de geometrias](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span><span class="sxs-lookup"><span data-stu-id="a44fb-115">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a44fb-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="a44fb-116">See also</span></span>

- [<span data-ttu-id="a44fb-117">Criar um arco elíptico</span><span class="sxs-lookup"><span data-stu-id="a44fb-117">Create an Elliptical Arc</span></span>](how-to-create-an-elliptical-arc.md)
- [<span data-ttu-id="a44fb-118">Criar uma curva de Bézier cúbica</span><span class="sxs-lookup"><span data-stu-id="a44fb-118">Create a Cubic Bezier Curve</span></span>](how-to-create-a-cubic-bezier-curve.md)
