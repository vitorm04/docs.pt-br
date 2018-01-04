---
title: Como criar um GeometryDrawing
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shapes [WPF], renderable
- renderable shapes [WPF]
- graphics [WPF], GeometryDrawing class
- classes [WPF], GeometryDrawing
ms.assetid: 11d3c096-91ba-4d41-9bba-aeac0db70f97
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 31417a3eeee2c1e61674c43558c2799705797c35
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-geometrydrawing"></a><span data-ttu-id="2575a-102">Como criar um GeometryDrawing</span><span class="sxs-lookup"><span data-stu-id="2575a-102">How to: Create a GeometryDrawing</span></span>
<span data-ttu-id="2575a-103">Este exemplo mostra como criar e exibir um <xref:System.Windows.Media.GeometryDrawing>.</span><span class="sxs-lookup"><span data-stu-id="2575a-103">This example shows how to create and display a <xref:System.Windows.Media.GeometryDrawing>.</span></span> <span data-ttu-id="2575a-104">Um <xref:System.Windows.Media.GeometryDrawing> permite que você criar uma forma com um preenchimento e um contorno associando um <xref:System.Windows.Media.Pen> e um <xref:System.Windows.Media.Brush> com um <xref:System.Windows.Media.Geometry>.</span><span class="sxs-lookup"><span data-stu-id="2575a-104">A <xref:System.Windows.Media.GeometryDrawing> enables you to create shape with a fill and an outline by associating a <xref:System.Windows.Media.Pen> and a <xref:System.Windows.Media.Brush> with a <xref:System.Windows.Media.Geometry>.</span></span> <span data-ttu-id="2575a-105">O <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> descreve a estrutura da forma, o <xref:System.Windows.Media.GeometryDrawing.Brush%2A> descreve o preenchimento da forma e o <xref:System.Windows.Media.GeometryDrawing.Pen%2A> descreve a estrutura da forma.</span><span class="sxs-lookup"><span data-stu-id="2575a-105">The <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> describes the shape's structure, the <xref:System.Windows.Media.GeometryDrawing.Brush%2A> describes the shape's fill, and the <xref:System.Windows.Media.GeometryDrawing.Pen%2A> describes the shape's outline.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2575a-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2575a-106">Example</span></span>  
 <span data-ttu-id="2575a-107">O exemplo a seguir usa um <xref:System.Windows.Media.GeometryDrawing> para renderizar uma forma.</span><span class="sxs-lookup"><span data-stu-id="2575a-107">The following example uses a <xref:System.Windows.Media.GeometryDrawing> to render a shape.</span></span> <span data-ttu-id="2575a-108">A forma é descrita por um <xref:System.Windows.Media.GeometryGroup> e dois <xref:System.Windows.Media.EllipseGeometry> objetos.</span><span class="sxs-lookup"><span data-stu-id="2575a-108">The shape is described by a <xref:System.Windows.Media.GeometryGroup> and two <xref:System.Windows.Media.EllipseGeometry> objects.</span></span> <span data-ttu-id="2575a-109">O interior da forma é pintado com um <xref:System.Windows.Media.LinearGradientBrush> e seu contorno é desenhado com uma <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>.</span><span class="sxs-lookup"><span data-stu-id="2575a-109">The shape's interior is painted with a <xref:System.Windows.Media.LinearGradientBrush> and its outline is drawn with a <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>.</span></span> <span data-ttu-id="2575a-110">O <xref:System.Windows.Media.GeometryDrawing> é exibido usando um <xref:System.Windows.Media.ImageDrawing> e um <xref:System.Windows.Controls.Image> elemento.</span><span class="sxs-lookup"><span data-stu-id="2575a-110">The <xref:System.Windows.Media.GeometryDrawing> is displayed using an <xref:System.Windows.Media.ImageDrawing> and an <xref:System.Windows.Controls.Image> element.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexamplewholepage)]  
  
 <span data-ttu-id="2575a-111">A ilustração a seguir mostra o resultante <xref:System.Windows.Media.GeometryDrawing>.</span><span class="sxs-lookup"><span data-stu-id="2575a-111">The following illustration shows the resulting <xref:System.Windows.Media.GeometryDrawing>.</span></span>  
  
 <span data-ttu-id="2575a-112">![Um GeometryDrawing de duas elipses](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")</span><span class="sxs-lookup"><span data-stu-id="2575a-112">![A GeometryDrawing of two ellipses](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")</span></span>  
  
 <span data-ttu-id="2575a-113">Para criar desenhos mais complexos, você pode combinar vários objetos de desenho em um único desenho composto usando um <xref:System.Windows.Media.DrawingGroup>.</span><span class="sxs-lookup"><span data-stu-id="2575a-113">To create more complex drawings, you can combine multiple drawing objects into a single composite drawing using a <xref:System.Windows.Media.DrawingGroup>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2575a-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2575a-114">See Also</span></span>  
 <xref:System.Windows.Media.DrawingGroup>  
 [<span data-ttu-id="2575a-115">Visão geral dos objetos de desenho</span><span class="sxs-lookup"><span data-stu-id="2575a-115">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="2575a-116">Visão geral de geometria</span><span class="sxs-lookup"><span data-stu-id="2575a-116">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [<span data-ttu-id="2575a-117">Criar um desenho composto</span><span class="sxs-lookup"><span data-stu-id="2575a-117">Create a Composite Drawing</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-drawing.md)
