---
title: "Como criar uma curva de Bézier quadrática"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Bezier curves [WPF], creating
- quadratic Bezier curves [WPF], creating
- graphics [WPF], quadratic Bezier curves
ms.assetid: cd8fca4a-504e-4fd8-92ea-2969065a6e02
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8320889f931e4482091b15bd9295c77a36d6d1e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-quadratic-bezier-curve"></a><span data-ttu-id="48f23-102">Como criar uma curva de Bézier quadrática</span><span class="sxs-lookup"><span data-stu-id="48f23-102">How to: Create a Quadratic Bezier Curve</span></span>
<span data-ttu-id="48f23-103">Este exemplo mostra como criar uma curva de Bézier quadrática.</span><span class="sxs-lookup"><span data-stu-id="48f23-103">This example shows how to create a quadratic Bezier curve.</span></span>  <span data-ttu-id="48f23-104">Para criar uma curva de Bézier quadrática, use o <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, e <xref:System.Windows.Media.QuadraticBezierSegment> classes.</span><span class="sxs-lookup"><span data-stu-id="48f23-104">To create a quadratic Bezier curve, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.QuadraticBezierSegment> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48f23-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="48f23-105">Example</span></span>  
 <span data-ttu-id="48f23-106">Nos exemplos a seguir, uma curva de Bézier quadrática é desenhada de (10,100) para (300,100).</span><span class="sxs-lookup"><span data-stu-id="48f23-106">In the following examples, a quadratic Bezier curve is drawn from (10,100) to (300,100).</span></span> <span data-ttu-id="48f23-107">A curva tem um ponto de controle de (200, 200).</span><span class="sxs-lookup"><span data-stu-id="48f23-107">The curve has a control point of (200,200).</span></span>  
  
 <span data-ttu-id="48f23-108">[xaml]</span><span class="sxs-lookup"><span data-stu-id="48f23-108">[xaml]</span></span>  
  
 <span data-ttu-id="48f23-109">Em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], você pode usar a sintaxe para descrever um caminho.</span><span class="sxs-lookup"><span data-stu-id="48f23-109">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you can use attribute syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#54](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#54)]  
  
 <span data-ttu-id="48f23-110">[xaml]</span><span class="sxs-lookup"><span data-stu-id="48f23-110">[xaml]</span></span>  
  
 <span data-ttu-id="48f23-111">(Observe que esta sintaxe de atributo, na verdade, cria um <xref:System.Windows.Media.StreamGeometry>, uma versão leve de um <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="48f23-111">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="48f23-112">Para obter mais informações, consulte o [sintaxe de marcação de caminho](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) página.)</span><span class="sxs-lookup"><span data-stu-id="48f23-112">For more information, see the [Path Markup Syntax](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) page.)</span></span>  
  
 <span data-ttu-id="48f23-113">Em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você também pode desenhar uma curva de Bézier quadrática usando sintaxe de elemento de objeto.</span><span class="sxs-lookup"><span data-stu-id="48f23-113">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you may also draw a quadratic Bezier curve using object element syntax.</span></span> <span data-ttu-id="48f23-114">A seguir é equivalente ao anterior [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] exemplo.</span><span class="sxs-lookup"><span data-stu-id="48f23-114">The following is equivalent to the previous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example.</span></span>  
  
 [!code-xaml[GeometrySample#34](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 <span data-ttu-id="48f23-115">Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, confira o [Exemplo de geometrias](http://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="48f23-115">This example is part of larger sample; for the complete sample, see the [Geometries Sample](http://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48f23-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="48f23-116">See Also</span></span>  
 [<span data-ttu-id="48f23-117">Criar um arco elíptico</span><span class="sxs-lookup"><span data-stu-id="48f23-117">Create an Elliptical Arc</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md)  
 [<span data-ttu-id="48f23-118">Criar uma curva de Bézier cúbica</span><span class="sxs-lookup"><span data-stu-id="48f23-118">Create a Cubic Bezier Curve</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)
