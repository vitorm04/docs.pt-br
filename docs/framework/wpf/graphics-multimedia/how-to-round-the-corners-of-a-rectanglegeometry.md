---
title: 'Como: Arredondar os cantos de um RectangleGeometry'
ms.date: 03/30/2017
helpviewer_keywords:
- corners [WPF], rounding
- RectangleGeometry class [WPF], rounding corners
- graphics [WPF], rounding corners of RectangleGeometry objects [WPF]
- rounding corners of RectangleGeometry objects [WPF]
ms.assetid: 926644bc-1357-4c0b-ac81-694bd090ae87
ms.openlocfilehash: 1a3ea08e4f54af117474cee23e6ac1041a1ed72b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54648369"
---
# <a name="how-to-round-the-corners-of-a-rectanglegeometry"></a><span data-ttu-id="6f1d6-102">Como: Arredondar os cantos de um RectangleGeometry</span><span class="sxs-lookup"><span data-stu-id="6f1d6-102">How to: Round the Corners of a RectangleGeometry</span></span>
<span data-ttu-id="6f1d6-103">Para arredondar os cantos de um <xref:System.Windows.Media.RectangleGeometry>, defina sua <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> e <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> propriedades para um valor maior que zero.</span><span class="sxs-lookup"><span data-stu-id="6f1d6-103">To round the corners of a <xref:System.Windows.Media.RectangleGeometry>, set its <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> and <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> properties to a value greater than zero.</span></span> <span data-ttu-id="6f1d6-104">Quanto maior os valores, mais redondos serão os cantos do retângulo.</span><span class="sxs-lookup"><span data-stu-id="6f1d6-104">The larger the values, the rounder the rectangle's corners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f1d6-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6f1d6-105">Example</span></span>  
 <span data-ttu-id="6f1d6-106">O exemplo a seguir mostra várias <xref:System.Windows.Media.RectangleGeometry> objetos com diferentes <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> e <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> configurações.</span><span class="sxs-lookup"><span data-stu-id="6f1d6-106">The following example shows several <xref:System.Windows.Media.RectangleGeometry> objects with different <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> and <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> settings.</span></span> <span data-ttu-id="6f1d6-107">O <xref:System.Windows.Media.RectangleGeometry> os objetos são exibidos usando <xref:System.Windows.Shapes.Path> elementos.</span><span class="sxs-lookup"><span data-stu-id="6f1d6-107">The <xref:System.Windows.Media.RectangleGeometry> objects are displayed using <xref:System.Windows.Shapes.Path> elements.</span></span>  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRoundedRectangleGeometryExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/RectangleGeometryRoundedCornerExample.xaml#graphicsmmroundedrectanglegeometryexamplewholepage)]  
  
 <span data-ttu-id="6f1d6-108">![Retângulos com diferente RadiusX&#47;configurações RadiusY](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rounded.png "graphicsmm_rounded")</span><span class="sxs-lookup"><span data-stu-id="6f1d6-108">![Rectangles with different RadiusX&#47;RadiusY settings](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rounded.png "graphicsmm_rounded")</span></span>  
<span data-ttu-id="6f1d6-109">Retângulos com cantos arredondados</span><span class="sxs-lookup"><span data-stu-id="6f1d6-109">Rectangles with Rounded Corners</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f1d6-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6f1d6-110">See also</span></span>
- [<span data-ttu-id="6f1d6-111">Visão geral de geometria</span><span class="sxs-lookup"><span data-stu-id="6f1d6-111">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
- [<span data-ttu-id="6f1d6-112">Criar uma forma composta</span><span class="sxs-lookup"><span data-stu-id="6f1d6-112">Create a Composite Shape</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)
- [<span data-ttu-id="6f1d6-113">Criar uma forma usando um PathGeometry</span><span class="sxs-lookup"><span data-stu-id="6f1d6-113">Create a Shape by Using a PathGeometry</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)
