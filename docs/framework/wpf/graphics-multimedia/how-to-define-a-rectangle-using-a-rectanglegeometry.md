---
title: "Como definir um retângulo usando um RectangleGeometry"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rectangles
- rectangles [WPF], creating with RectangleGeometry class
ms.assetid: e40b8a8e-54b8-416b-a9f2-be6dca9fdf0b
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3a8254bd60da379d006bc50ab3a935cd83b83d0a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-a-rectangle-using-a-rectanglegeometry"></a><span data-ttu-id="8b691-102">Como definir um retângulo usando um RectangleGeometry</span><span class="sxs-lookup"><span data-stu-id="8b691-102">How to: Define a Rectangle Using a RectangleGeometry</span></span>
<span data-ttu-id="8b691-103">Este exemplo descreve como usar o <xref:System.Windows.Media.RectangleGeometry> classe para descrever um retângulo.</span><span class="sxs-lookup"><span data-stu-id="8b691-103">This example describes how to use the <xref:System.Windows.Media.RectangleGeometry> class to describe a rectangle.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b691-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8b691-104">Example</span></span>  
 <span data-ttu-id="8b691-105">O exemplo a seguir mostra como criar e processar um <xref:System.Windows.Media.RectangleGeometry>.</span><span class="sxs-lookup"><span data-stu-id="8b691-105">The following example shows how to create and render a <xref:System.Windows.Media.RectangleGeometry>.</span></span>  <span data-ttu-id="8b691-106">A posição relativa e as dimensões do retângulo são definidas por um <xref:System.Windows.Rect> estrutura.</span><span class="sxs-lookup"><span data-stu-id="8b691-106">The relative position and the dimensions of the rectangle are defined by a <xref:System.Windows.Rect> structure.</span></span> <span data-ttu-id="8b691-107">A posição relativa é `50,50` e a altura e a largura são ambos `25` criando um quadrado.</span><span class="sxs-lookup"><span data-stu-id="8b691-107">The relative position is `50,50` and the height and the width are both `25` creating a square.</span></span> <span data-ttu-id="8b691-108">O interior do retângulo é pintado com um <xref:System.Windows.Media.Brushes.LemonChiffon%2A> pincel e seu contorno é pintado com um <xref:System.Windows.Media.Brushes.Black%2A> traço com uma espessura de `1`.</span><span class="sxs-lookup"><span data-stu-id="8b691-108">The rectangle's interior is painted with a <xref:System.Windows.Media.Brushes.LemonChiffon%2A> brush and its outline is painted with a <xref:System.Windows.Media.Brushes.Black%2A> stroke with a thickness of `1`.</span></span>  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 <span data-ttu-id="8b691-109">![Uma geometria de retângulos](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rectangle.gif "graphicsmm_rectangle")</span><span class="sxs-lookup"><span data-stu-id="8b691-109">![A RectangleGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rectangle.gif "graphicsmm_rectangle")</span></span>  
<span data-ttu-id="8b691-110">RectangleGeometry</span><span class="sxs-lookup"><span data-stu-id="8b691-110">RectangleGeometry</span></span>  
  
 <span data-ttu-id="8b691-111">Embora esse exemplo tenha usado um <xref:System.Windows.Shapes.Path> elemento para renderizar o <xref:System.Windows.Media.RectangleGeometry>, há muitas outras maneiras de usar <xref:System.Windows.Media.RectangleGeometry> objetos.</span><span class="sxs-lookup"><span data-stu-id="8b691-111">Although this example used a <xref:System.Windows.Shapes.Path> element to render the <xref:System.Windows.Media.RectangleGeometry>, there are many other ways to use <xref:System.Windows.Media.RectangleGeometry> objects.</span></span> <span data-ttu-id="8b691-112">Por exemplo, um <xref:System.Windows.Media.RectangleGeometry> pode ser usado para especificar o <xref:System.Windows.UIElement.Clip%2A> de um <xref:System.Windows.UIElement> ou <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> de um <xref:System.Windows.Media.GeometryDrawing>.</span><span class="sxs-lookup"><span data-stu-id="8b691-112">For example, a <xref:System.Windows.Media.RectangleGeometry> can be used to specify the <xref:System.Windows.UIElement.Clip%2A> of a <xref:System.Windows.UIElement> or the <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> of a <xref:System.Windows.Media.GeometryDrawing>.</span></span>  
  
 <span data-ttu-id="8b691-113">Outras classes de geometria simples incluem <xref:System.Windows.Media.LineGeometry> e <xref:System.Windows.Media.EllipseGeometry>.</span><span class="sxs-lookup"><span data-stu-id="8b691-113">Other simple geometry classes include <xref:System.Windows.Media.LineGeometry> and <xref:System.Windows.Media.EllipseGeometry>.</span></span> <span data-ttu-id="8b691-114">Esses geometrias, bem como aquelas mais complexas, também podem ser criadas usando um <xref:System.Windows.Media.PathGeometry> ou <xref:System.Windows.Media.StreamGeometry>.</span><span class="sxs-lookup"><span data-stu-id="8b691-114">These geometries, as well as more complex ones, can also be created using a <xref:System.Windows.Media.PathGeometry> or <xref:System.Windows.Media.StreamGeometry>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b691-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8b691-115">See Also</span></span>  
 [<span data-ttu-id="8b691-116">Visão geral de geometria</span><span class="sxs-lookup"><span data-stu-id="8b691-116">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [<span data-ttu-id="8b691-117">Criar uma forma composta</span><span class="sxs-lookup"><span data-stu-id="8b691-117">Create a Composite Shape</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)  
 [<span data-ttu-id="8b691-118">Criar uma forma usando um PathGeometry</span><span class="sxs-lookup"><span data-stu-id="8b691-118">Create a Shape by Using a PathGeometry</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)
