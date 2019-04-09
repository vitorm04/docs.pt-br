---
title: 'Como: Criar uma curva de Bezier quadrática'
ms.date: 03/30/2017
helpviewer_keywords:
- Bezier curves [WPF], creating
- quadratic Bezier curves [WPF], creating
- graphics [WPF], quadratic Bezier curves
ms.assetid: cd8fca4a-504e-4fd8-92ea-2969065a6e02
ms.openlocfilehash: a0b2145b4a5bba11186419fe680f2eca41949d6a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134855"
---
# <a name="how-to-create-a-quadratic-bezier-curve"></a><span data-ttu-id="8132d-102">Como: Criar uma curva de Bezier quadrática</span><span class="sxs-lookup"><span data-stu-id="8132d-102">How to: Create a Quadratic Bezier Curve</span></span>
<span data-ttu-id="8132d-103">Este exemplo mostra como criar uma curva de Bezier quadrática.</span><span class="sxs-lookup"><span data-stu-id="8132d-103">This example shows how to create a quadratic Bezier curve.</span></span>  <span data-ttu-id="8132d-104">Para criar uma curva de Bezier quadrática, use o <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, e <xref:System.Windows.Media.QuadraticBezierSegment> classes.</span><span class="sxs-lookup"><span data-stu-id="8132d-104">To create a quadratic Bezier curve, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.QuadraticBezierSegment> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8132d-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8132d-105">Example</span></span>  
 <span data-ttu-id="8132d-106">Nos exemplos a seguir, uma curva de Bezier quadrática é desenhada de (10,100) (300,100).</span><span class="sxs-lookup"><span data-stu-id="8132d-106">In the following examples, a quadratic Bezier curve is drawn from (10,100) to (300,100).</span></span> <span data-ttu-id="8132d-107">A curva tem um ponto de controle de (200, 200).</span><span class="sxs-lookup"><span data-stu-id="8132d-107">The curve has a control point of (200,200).</span></span>  
  
 <span data-ttu-id="8132d-108">[xaml]</span><span class="sxs-lookup"><span data-stu-id="8132d-108">[xaml]</span></span>  
  
 <span data-ttu-id="8132d-109">No [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], você pode usar a sintaxe de atributo para descrever um caminho.</span><span class="sxs-lookup"><span data-stu-id="8132d-109">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you can use attribute syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#54](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#54)]  
  
 <span data-ttu-id="8132d-110">[xaml]</span><span class="sxs-lookup"><span data-stu-id="8132d-110">[xaml]</span></span>  
  
 <span data-ttu-id="8132d-111">(Observe que essa sintaxe de atributo na verdade cria um <xref:System.Windows.Media.StreamGeometry>, uma versão leve de um <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="8132d-111">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="8132d-112">Para obter mais informações, consulte o [sintaxe de marcação de caminho](path-markup-syntax.md) página.)</span><span class="sxs-lookup"><span data-stu-id="8132d-112">For more information, see the [Path Markup Syntax](path-markup-syntax.md) page.)</span></span>  
  
 <span data-ttu-id="8132d-113">No [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você também pode desenhar uma curva de Bezier quadrática usando sintaxe de elemento de objeto.</span><span class="sxs-lookup"><span data-stu-id="8132d-113">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you may also draw a quadratic Bezier curve using object element syntax.</span></span> <span data-ttu-id="8132d-114">A seguir é equivalente ao anterior [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] exemplo.</span><span class="sxs-lookup"><span data-stu-id="8132d-114">The following is equivalent to the previous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example.</span></span>  
  
 [!code-xaml[GeometrySample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 <span data-ttu-id="8132d-115">Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, confira o [Exemplo de geometrias](https://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="8132d-115">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8132d-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8132d-116">See also</span></span>

- [<span data-ttu-id="8132d-117">Criar um arco elíptico</span><span class="sxs-lookup"><span data-stu-id="8132d-117">Create an Elliptical Arc</span></span>](how-to-create-an-elliptical-arc.md)
- [<span data-ttu-id="8132d-118">Criar uma curva de Bézier cúbica</span><span class="sxs-lookup"><span data-stu-id="8132d-118">Create a Cubic Bezier Curve</span></span>](how-to-create-a-cubic-bezier-curve.md)
