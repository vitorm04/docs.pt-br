---
title: Como arredondar os cantos de um RectangleGeometry
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- corners [WPF], rounding
- RectangleGeometry class [WPF], rounding corners
- graphics [WPF], rounding corners of RectangleGeometry objects [WPF]
- rounding corners of RectangleGeometry objects [WPF]
ms.assetid: 926644bc-1357-4c0b-ac81-694bd090ae87
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 92a51b3c610d3755583f8a39314f45d3980ee1bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-round-the-corners-of-a-rectanglegeometry"></a><span data-ttu-id="5b3c0-102">Como arredondar os cantos de um RectangleGeometry</span><span class="sxs-lookup"><span data-stu-id="5b3c0-102">How to: Round the Corners of a RectangleGeometry</span></span>
<span data-ttu-id="5b3c0-103">Para arredondar os cantos de uma <xref:System.Windows.Media.RectangleGeometry>, defina seu <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> e <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> propriedades para um valor maior que zero.</span><span class="sxs-lookup"><span data-stu-id="5b3c0-103">To round the corners of a <xref:System.Windows.Media.RectangleGeometry>, set its <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> and <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> properties to a value greater than zero.</span></span> <span data-ttu-id="5b3c0-104">Quanto maior os valores, mais arredondados serão os cantos do retângulo.</span><span class="sxs-lookup"><span data-stu-id="5b3c0-104">The larger the values, the rounder the rectangle's corners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b3c0-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5b3c0-105">Example</span></span>  
 <span data-ttu-id="5b3c0-106">O exemplo a seguir mostra vários <xref:System.Windows.Media.RectangleGeometry> objetos com diferentes <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> e <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> configurações.</span><span class="sxs-lookup"><span data-stu-id="5b3c0-106">The following example shows several <xref:System.Windows.Media.RectangleGeometry> objects with different <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> and <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> settings.</span></span> <span data-ttu-id="5b3c0-107">O <xref:System.Windows.Media.RectangleGeometry> objetos são exibidos usando <xref:System.Windows.Shapes.Path> elementos.</span><span class="sxs-lookup"><span data-stu-id="5b3c0-107">The <xref:System.Windows.Media.RectangleGeometry> objects are displayed using <xref:System.Windows.Shapes.Path> elements.</span></span>  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRoundedRectangleGeometryExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/RectangleGeometryRoundedCornerExample.xaml#graphicsmmroundedrectanglegeometryexamplewholepage)]  
  
 <span data-ttu-id="5b3c0-108">![Retângulos com diferentes RadiusX &#47; Configurações radiusY](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rounded.png "graphicsmm_rounded")</span><span class="sxs-lookup"><span data-stu-id="5b3c0-108">![Rectangles with different RadiusX&#47;RadiusY settings](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rounded.png "graphicsmm_rounded")</span></span>  
<span data-ttu-id="5b3c0-109">Retângulos com cantos arredondados</span><span class="sxs-lookup"><span data-stu-id="5b3c0-109">Rectangles with Rounded Corners</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b3c0-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5b3c0-110">See Also</span></span>  
 [<span data-ttu-id="5b3c0-111">Visão geral de geometria</span><span class="sxs-lookup"><span data-stu-id="5b3c0-111">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [<span data-ttu-id="5b3c0-112">Criar uma forma composta</span><span class="sxs-lookup"><span data-stu-id="5b3c0-112">Create a Composite Shape</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)  
 [<span data-ttu-id="5b3c0-113">Criar uma forma usando um PathGeometry</span><span class="sxs-lookup"><span data-stu-id="5b3c0-113">Create a Shape by Using a PathGeometry</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)
