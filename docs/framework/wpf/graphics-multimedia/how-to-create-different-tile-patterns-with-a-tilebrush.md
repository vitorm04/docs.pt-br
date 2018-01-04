---
title: "Como criar padrões lado a lado diferentes com um TileBrush"
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
- TileBrush [WPF], creating tile patterns
- tile patterns [WPF], creating
- creating [WPF], tile patterns with TileBrush
ms.assetid: 5aa46632-3527-4668-9d8d-0375c8af28aa
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 646ce5142875c95c0b1ca19643790f73f7eb83e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-different-tile-patterns-with-a-tilebrush"></a><span data-ttu-id="8581b-102">Como criar padrões lado a lado diferentes com um TileBrush</span><span class="sxs-lookup"><span data-stu-id="8581b-102">How to: Create Different Tile Patterns with a TileBrush</span></span>
<span data-ttu-id="8581b-103">Este exemplo mostra como usar o <xref:System.Windows.Media.TileBrush.TileMode%2A> propriedade de um <xref:System.Windows.Media.TileBrush> para criar um padrão.</span><span class="sxs-lookup"><span data-stu-id="8581b-103">This example shows how to use the <xref:System.Windows.Media.TileBrush.TileMode%2A> property of a <xref:System.Windows.Media.TileBrush> to create a pattern.</span></span>  
  
 <span data-ttu-id="8581b-104">O <xref:System.Windows.Media.TileBrush.TileMode%2A> propriedade permite que você especifique como o conteúdo de um <xref:System.Windows.Media.TileBrush> é repetido, ou seja, lado a lado para preencher uma área de saída.</span><span class="sxs-lookup"><span data-stu-id="8581b-104">The <xref:System.Windows.Media.TileBrush.TileMode%2A> property enables you to specify how the content of a <xref:System.Windows.Media.TileBrush> is repeated, that is, tiled to fill an output area.</span></span> <span data-ttu-id="8581b-105">Para criar um padrão, defina o <xref:System.Windows.Media.TileBrush.TileMode%2A> para <xref:System.Windows.Media.TileMode.Tile>, <xref:System.Windows.Media.TileMode.FlipX>, <xref:System.Windows.Media.TileMode.FlipY>, ou <xref:System.Windows.Media.TileMode.FlipXY>.</span><span class="sxs-lookup"><span data-stu-id="8581b-105">To create a pattern, you set the <xref:System.Windows.Media.TileBrush.TileMode%2A> to <xref:System.Windows.Media.TileMode.Tile>, <xref:System.Windows.Media.TileMode.FlipX>, <xref:System.Windows.Media.TileMode.FlipY>, or <xref:System.Windows.Media.TileMode.FlipXY>.</span></span> <span data-ttu-id="8581b-106">Você também deve definir o <xref:System.Windows.Media.TileBrush.Viewport%2A> do <xref:System.Windows.Media.TileBrush> para que seja menor do que a área que você estiver pintando; caso contrário, apenas um único bloco é produzido, independentemente que <xref:System.Windows.Media.TileBrush.TileMode%2A> configuração.</span><span class="sxs-lookup"><span data-stu-id="8581b-106">You must also set the <xref:System.Windows.Media.TileBrush.Viewport%2A> of the <xref:System.Windows.Media.TileBrush> so that it is smaller than the area that you are painting; otherwise, only a single tile is produced, regardless which <xref:System.Windows.Media.TileBrush.TileMode%2A> setting you use.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8581b-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8581b-107">Example</span></span>  
 <span data-ttu-id="8581b-108">O exemplo a seguir cria cinco <xref:System.Windows.Media.DrawingBrush> objetos, cada lhes dá um diferentes <xref:System.Windows.Media.TileBrush.TileMode%2A> configuração e os utiliza para pintar cinco retângulos.</span><span class="sxs-lookup"><span data-stu-id="8581b-108">The following example creates five <xref:System.Windows.Media.DrawingBrush> objects, gives them each a different <xref:System.Windows.Media.TileBrush.TileMode%2A> setting, and uses them to paint five rectangles.</span></span> <span data-ttu-id="8581b-109">Embora este exemplo usa o <xref:System.Windows.Media.DrawingBrush> classe para demonstrar <xref:System.Windows.Media.TileBrush.TileMode%2A> comportamento, o <xref:System.Windows.Media.TileBrush.TileMode%2A> propriedade funciona de forma idêntica para todos o <xref:System.Windows.Media.TileBrush> objetos, ou seja, para <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.VisualBrush>, e <xref:System.Windows.Media.DrawingBrush>.</span><span class="sxs-lookup"><span data-stu-id="8581b-109">Although this example uses the <xref:System.Windows.Media.DrawingBrush> class to demonstrate <xref:System.Windows.Media.TileBrush.TileMode%2A> behavior, the <xref:System.Windows.Media.TileBrush.TileMode%2A> property works identically for all the <xref:System.Windows.Media.TileBrush> objects, that is, for <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.VisualBrush>, and <xref:System.Windows.Media.DrawingBrush>.</span></span>  
  
 <span data-ttu-id="8581b-110">A ilustração a seguir mostra a saída que esse exemplo produz.</span><span class="sxs-lookup"><span data-stu-id="8581b-110">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="8581b-111">![TileBrush lado a lado de saída de exemplo](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrushtilemodeexample.png "graphicsmm_DrawingBrushTileModeExample")</span><span class="sxs-lookup"><span data-stu-id="8581b-111">![TileBrush tiling example output](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrushtilemodeexample.png "graphicsmm_DrawingBrushTileModeExample")</span></span>  
<span data-ttu-id="8581b-112">Padrões de bloco criados com a propriedade TileMode</span><span class="sxs-lookup"><span data-stu-id="8581b-112">Tile patterns created with the TileMode property</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/TileModeExample.cs#graphicsmmdrawingbrushtilemodeexample)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/tilemodeexample.vb#graphicsmmdrawingbrushtilemodeexample)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/TileModeExample.xaml#graphicsmmdrawingbrushtilemodeexample)]  
  
## <a name="see-also"></a><span data-ttu-id="8581b-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8581b-113">See Also</span></span>  
 [<span data-ttu-id="8581b-114">Definir o tamanho de bloco um TileBrush</span><span class="sxs-lookup"><span data-stu-id="8581b-114">Set the Tile Size for a TileBrush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-the-tile-size-for-a-tilebrush.md)  
 [<span data-ttu-id="8581b-115">Pintando com imagens, desenhos e visuais</span><span class="sxs-lookup"><span data-stu-id="8581b-115">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
