---
title: 'Como: Arredondar os cantos de um RectangleGeometry'
ms.date: 03/30/2017
helpviewer_keywords:
- corners [WPF], rounding
- RectangleGeometry class [WPF], rounding corners
- graphics [WPF], rounding corners of RectangleGeometry objects [WPF]
- rounding corners of RectangleGeometry objects [WPF]
ms.assetid: 926644bc-1357-4c0b-ac81-694bd090ae87
ms.openlocfilehash: eb2f173bedb903e12b2795264c684524cfa09825
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089127"
---
# <a name="how-to-round-the-corners-of-a-rectanglegeometry"></a><span data-ttu-id="fdb0b-102">Como: Arredondar os cantos de um RectangleGeometry</span><span class="sxs-lookup"><span data-stu-id="fdb0b-102">How to: Round the Corners of a RectangleGeometry</span></span>
<span data-ttu-id="fdb0b-103">Para arredondar os cantos de um <xref:System.Windows.Media.RectangleGeometry>, defina sua <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> e <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> propriedades para um valor maior que zero.</span><span class="sxs-lookup"><span data-stu-id="fdb0b-103">To round the corners of a <xref:System.Windows.Media.RectangleGeometry>, set its <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> and <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> properties to a value greater than zero.</span></span> <span data-ttu-id="fdb0b-104">Quanto maior os valores, mais redondos serão os cantos do retângulo.</span><span class="sxs-lookup"><span data-stu-id="fdb0b-104">The larger the values, the rounder the rectangle's corners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fdb0b-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fdb0b-105">Example</span></span>  
 <span data-ttu-id="fdb0b-106">O exemplo a seguir mostra várias <xref:System.Windows.Media.RectangleGeometry> objetos com diferentes <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> e <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> configurações.</span><span class="sxs-lookup"><span data-stu-id="fdb0b-106">The following example shows several <xref:System.Windows.Media.RectangleGeometry> objects with different <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> and <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> settings.</span></span> <span data-ttu-id="fdb0b-107">O <xref:System.Windows.Media.RectangleGeometry> os objetos são exibidos usando <xref:System.Windows.Shapes.Path> elementos.</span><span class="sxs-lookup"><span data-stu-id="fdb0b-107">The <xref:System.Windows.Media.RectangleGeometry> objects are displayed using <xref:System.Windows.Shapes.Path> elements.</span></span>  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRoundedRectangleGeometryExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/RectangleGeometryRoundedCornerExample.xaml#graphicsmmroundedrectanglegeometryexamplewholepage)]  
  
 <span data-ttu-id="fdb0b-108">![Retângulos com diferente RadiusX&#47;configurações RadiusY](./media/graphicsmm-rounded.png "graphicsmm_rounded")</span><span class="sxs-lookup"><span data-stu-id="fdb0b-108">![Rectangles with different RadiusX&#47;RadiusY settings](./media/graphicsmm-rounded.png "graphicsmm_rounded")</span></span>  
<span data-ttu-id="fdb0b-109">Retângulos com cantos arredondados</span><span class="sxs-lookup"><span data-stu-id="fdb0b-109">Rectangles with Rounded Corners</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdb0b-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fdb0b-110">See also</span></span>

- [<span data-ttu-id="fdb0b-111">Visão geral da geometria</span><span class="sxs-lookup"><span data-stu-id="fdb0b-111">Geometry Overview</span></span>](geometry-overview.md)
- [<span data-ttu-id="fdb0b-112">Criar uma forma composta</span><span class="sxs-lookup"><span data-stu-id="fdb0b-112">Create a Composite Shape</span></span>](how-to-create-a-composite-shape.md)
- [<span data-ttu-id="fdb0b-113">Criar uma forma usando um PathGeometry</span><span class="sxs-lookup"><span data-stu-id="fdb0b-113">Create a Shape by Using a PathGeometry</span></span>](how-to-create-a-shape-by-using-a-pathgeometry.md)
