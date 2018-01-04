---
title: "Como pintar uma área com um desenho"
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
- brushes [WPF], painting with drawings
- painting [WPF], with drawings
- drawings [WPF], painting with
ms.assetid: c10dc4b1-09b1-41e8-ad14-456b5fb377df
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fbb7c4aff56fae9b4cc0346f8086bc490269ec8b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-paint-an-area-with-a-drawing"></a><span data-ttu-id="22416-102">Como pintar uma área com um desenho</span><span class="sxs-lookup"><span data-stu-id="22416-102">How to: Paint an Area with a Drawing</span></span>
<span data-ttu-id="22416-103">Este exemplo mostra como pintar uma área com um desenho.</span><span class="sxs-lookup"><span data-stu-id="22416-103">This example shows how to paint an area with a drawing.</span></span> <span data-ttu-id="22416-104">Para pintar uma área com um desenho, use um <xref:System.Windows.Media.DrawingBrush> e um ou mais <xref:System.Windows.Media.Drawing> objetos.</span><span class="sxs-lookup"><span data-stu-id="22416-104">To paint an area with a drawing, you use a <xref:System.Windows.Media.DrawingBrush> and one or more <xref:System.Windows.Media.Drawing> objects.</span></span>   <span data-ttu-id="22416-105">O exemplo a seguir usa um <xref:System.Windows.Media.DrawingBrush> para pintar um objeto com um desenho de duas elipses.</span><span class="sxs-lookup"><span data-stu-id="22416-105">The following example uses a <xref:System.Windows.Media.DrawingBrush> to paint an object with a drawing of two ellipses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22416-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="22416-106">Example</span></span>  
 [!code-xaml[drawingbrush_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_snip/CS/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 [!code-csharp[drawingbrush_procedural_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_procedural_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-vb[drawingbrush_procedural_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/drawingbrush_procedural_snip/VisualBasic/DrawingBrushExample.vb#drawingbrushexamplewholepage)]  
  
 <span data-ttu-id="22416-107">A ilustração a seguir mostra a saída do exemplo.</span><span class="sxs-lookup"><span data-stu-id="22416-107">The following illustration shows the example's output.</span></span>  
  
 <span data-ttu-id="22416-108">![Saída de um DrawingBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrush-simple.png "graphicsmm_drawingbrush_simple")</span><span class="sxs-lookup"><span data-stu-id="22416-108">![Output from a DrawingBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrush-simple.png "graphicsmm_drawingbrush_simple")</span></span>  
  
 <span data-ttu-id="22416-109">(O centro da forma é banco por razões descritas em [controlar o preenchimento de uma forma de composição](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-the-fill-of-a-composite-shape.md).)</span><span class="sxs-lookup"><span data-stu-id="22416-109">(The center of the shape is white for reasons described in     [Control the Fill of a Composite Shape](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-the-fill-of-a-composite-shape.md).)</span></span>  
  
 <span data-ttu-id="22416-110">Definindo um <xref:System.Windows.Media.DrawingBrush> do objeto <xref:System.Windows.Media.TileBrush.Viewport%2A> e <xref:System.Windows.Media.TileBrush.TileMode%2A> propriedades, você pode criar um padrão de repetição.</span><span class="sxs-lookup"><span data-stu-id="22416-110">By setting a <xref:System.Windows.Media.DrawingBrush> object's <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.TileMode%2A> properties, you can create a repeating pattern.</span></span> <span data-ttu-id="22416-111">O exemplo a seguir pinta um objeto com um padrão criado de um desenho de duas elipses.</span><span class="sxs-lookup"><span data-stu-id="22416-111">The following example paints an object with a pattern created from a drawing of two ellipses.</span></span>  
  
 [!code-xaml[drawingbrush_snip#TiledDrawingBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_snip/CS/TiledDrawingBrushExample.xaml#tileddrawingbrushexamplewholepage)]  
  
 [!code-csharp[drawingbrush_procedural_snip#TiledDrawingBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_procedural_snip/CSharp/TiledDrawingBrushExample.cs#tileddrawingbrushexamplewholepage)]
 [!code-vb[drawingbrush_procedural_snip#TiledDrawingBrushExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/drawingbrush_procedural_snip/VisualBasic/TiledDrawingBrushExample.vb#tileddrawingbrushexamplewholepage)]  
  
 <span data-ttu-id="22416-112">A ilustração a seguir mostra o lado a lado <xref:System.Windows.Media.DrawingBrush> saída.</span><span class="sxs-lookup"><span data-stu-id="22416-112">The following illustration shows the tiled <xref:System.Windows.Media.DrawingBrush> output.</span></span>  
  
 <span data-ttu-id="22416-113">![Saída lado a lado de um DrawingBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrush-tiled.png "graphicsmm_drawingbrush_tiled")</span><span class="sxs-lookup"><span data-stu-id="22416-113">![Tiled output from a DrawingBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrush-tiled.png "graphicsmm_drawingbrush_tiled")</span></span>  
  
 <span data-ttu-id="22416-114">Para obter mais informações sobre pincéis de desenho, consulte [pintura com imagens, desenhos e visuais](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).</span><span class="sxs-lookup"><span data-stu-id="22416-114">For more information about drawing brushes, see [Painting with Images, Drawings, and Visuals](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).</span></span> <span data-ttu-id="22416-115">Para obter mais informações sobre <xref:System.Windows.Media.Drawing> objetos, consulte o [visão geral de objetos de desenho](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="22416-115">For more information about <xref:System.Windows.Media.Drawing> objects, see the [Drawing Objects Overview](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).</span></span>
