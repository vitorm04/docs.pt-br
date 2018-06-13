---
title: Como arredondar os cantos de um RectangleGeometry
ms.date: 03/30/2017
helpviewer_keywords:
- corners [WPF], rounding
- RectangleGeometry class [WPF], rounding corners
- graphics [WPF], rounding corners of RectangleGeometry objects [WPF]
- rounding corners of RectangleGeometry objects [WPF]
ms.assetid: 926644bc-1357-4c0b-ac81-694bd090ae87
ms.openlocfilehash: e4f1d37e2c0f26967affff14ed6475fc8c0cb28c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561635"
---
# <a name="how-to-round-the-corners-of-a-rectanglegeometry"></a><span data-ttu-id="d6342-102">Como arredondar os cantos de um RectangleGeometry</span><span class="sxs-lookup"><span data-stu-id="d6342-102">How to: Round the Corners of a RectangleGeometry</span></span>
<span data-ttu-id="d6342-103">Para arredondar os cantos de uma <xref:System.Windows.Media.RectangleGeometry>, defina seu <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> e <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> propriedades para um valor maior que zero.</span><span class="sxs-lookup"><span data-stu-id="d6342-103">To round the corners of a <xref:System.Windows.Media.RectangleGeometry>, set its <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> and <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> properties to a value greater than zero.</span></span> <span data-ttu-id="d6342-104">Quanto maior os valores, mais arredondados serão os cantos do retângulo.</span><span class="sxs-lookup"><span data-stu-id="d6342-104">The larger the values, the rounder the rectangle's corners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6342-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d6342-105">Example</span></span>  
 <span data-ttu-id="d6342-106">O exemplo a seguir mostra vários <xref:System.Windows.Media.RectangleGeometry> objetos com diferentes <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> e <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> configurações.</span><span class="sxs-lookup"><span data-stu-id="d6342-106">The following example shows several <xref:System.Windows.Media.RectangleGeometry> objects with different <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> and <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> settings.</span></span> <span data-ttu-id="d6342-107">O <xref:System.Windows.Media.RectangleGeometry> objetos são exibidos usando <xref:System.Windows.Shapes.Path> elementos.</span><span class="sxs-lookup"><span data-stu-id="d6342-107">The <xref:System.Windows.Media.RectangleGeometry> objects are displayed using <xref:System.Windows.Shapes.Path> elements.</span></span>  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRoundedRectangleGeometryExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/RectangleGeometryRoundedCornerExample.xaml#graphicsmmroundedrectanglegeometryexamplewholepage)]  
  
 <span data-ttu-id="d6342-108">![Retângulos com diferente RadiusX&#47;configurações RadiusY](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rounded.png "graphicsmm_rounded")</span><span class="sxs-lookup"><span data-stu-id="d6342-108">![Rectangles with different RadiusX&#47;RadiusY settings](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rounded.png "graphicsmm_rounded")</span></span>  
<span data-ttu-id="d6342-109">Retângulos com cantos arredondados</span><span class="sxs-lookup"><span data-stu-id="d6342-109">Rectangles with Rounded Corners</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6342-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d6342-110">See Also</span></span>  
 [<span data-ttu-id="d6342-111">Visão geral de geometria</span><span class="sxs-lookup"><span data-stu-id="d6342-111">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [<span data-ttu-id="d6342-112">Criar uma forma composta</span><span class="sxs-lookup"><span data-stu-id="d6342-112">Create a Composite Shape</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)  
 [<span data-ttu-id="d6342-113">Criar uma forma usando um PathGeometry</span><span class="sxs-lookup"><span data-stu-id="d6342-113">Create a Shape by Using a PathGeometry</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)
