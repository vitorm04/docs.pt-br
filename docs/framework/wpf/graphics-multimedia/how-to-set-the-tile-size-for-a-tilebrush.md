---
title: Como definir o tamanho de lado para um TileBrush
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TileBrush [WPF], size of tilepropertys
- Viewport property of TileBrush [WPF]
ms.assetid: 04f41090-1b46-4e36-832f-d27d28708b8c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 484419c05c3d607212ea6d565777cf49cbfdbc19
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-tile-size-for-a-tilebrush"></a><span data-ttu-id="8ed9b-102">Como definir o tamanho de lado para um TileBrush</span><span class="sxs-lookup"><span data-stu-id="8ed9b-102">How to: Set the Tile Size for a TileBrush</span></span>
<span data-ttu-id="8ed9b-103">Este exemplo mostra como definir o tamanho de bloco para um <xref:System.Windows.Media.TileBrush>.</span><span class="sxs-lookup"><span data-stu-id="8ed9b-103">This example shows how to set the tile size for a <xref:System.Windows.Media.TileBrush>.</span></span> <span data-ttu-id="8ed9b-104">Por padrão, um <xref:System.Windows.Media.TileBrush> produz um único bloco que preenche completamente a área que você estiver pintando.</span><span class="sxs-lookup"><span data-stu-id="8ed9b-104">By default, a <xref:System.Windows.Media.TileBrush> produces a single tile that completely fills the area that you are painting.</span></span> <span data-ttu-id="8ed9b-105">Você pode substituir esse comportamento, definindo a <xref:System.Windows.Media.TileBrush.Viewport%2A> e <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> propriedades.</span><span class="sxs-lookup"><span data-stu-id="8ed9b-105">You can override this behavior by setting the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> properties.</span></span>  
  
 <span data-ttu-id="8ed9b-106">O <xref:System.Windows.Media.TileBrush.Viewport%2A> propriedade especifica o tamanho de bloco para um <xref:System.Windows.Media.TileBrush>.</span><span class="sxs-lookup"><span data-stu-id="8ed9b-106">The <xref:System.Windows.Media.TileBrush.Viewport%2A> property specifies the tile size for a <xref:System.Windows.Media.TileBrush>.</span></span> <span data-ttu-id="8ed9b-107">Por padrão, o valor de <xref:System.Windows.Media.TileBrush.Viewport%2A> propriedade é relativo ao tamanho da área que está sendo pintada.</span><span class="sxs-lookup"><span data-stu-id="8ed9b-107">By default, the value of the <xref:System.Windows.Media.TileBrush.Viewport%2A> property is relative to the size of the area being painted.</span></span> <span data-ttu-id="8ed9b-108">Para fazer o <xref:System.Windows.Media.TileBrush.Viewport%2A> propriedade especificar um tamanho de bloco absoluto, definir o <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> propriedade <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span><span class="sxs-lookup"><span data-stu-id="8ed9b-108">To make the <xref:System.Windows.Media.TileBrush.Viewport%2A> property specify an absolute tile size, set the <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> property to <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ed9b-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8ed9b-109">Example</span></span>  
 <span data-ttu-id="8ed9b-110">O exemplo a seguir usa uma <xref:System.Windows.Media.ImageBrush>, um tipo de <xref:System.Windows.Media.TileBrush>, para desenhar um retângulo com blocos.</span><span class="sxs-lookup"><span data-stu-id="8ed9b-110">The following example uses an <xref:System.Windows.Media.ImageBrush>, a type of <xref:System.Windows.Media.TileBrush>, to paint a rectangle with tiles.</span></span> <span data-ttu-id="8ed9b-111">O exemplo define cada bloco para 50% por 50% da área de saída (o retângulo).</span><span class="sxs-lookup"><span data-stu-id="8ed9b-111">The example sets each tile to  50 percent by 50 percent of the output area (the rectangle).</span></span> <span data-ttu-id="8ed9b-112">Como resultado, o retângulo é pintado com quatro projeções da imagem.</span><span class="sxs-lookup"><span data-stu-id="8ed9b-112">As a result, the rectangle is painted with four projections of the image.</span></span>  
  
 <span data-ttu-id="8ed9b-113">A ilustração a seguir mostra a saída que esse exemplo produz.</span><span class="sxs-lookup"><span data-stu-id="8ed9b-113">The following illustration shows the output that the example produces.</span></span>
  
 <span data-ttu-id="8ed9b-114">![Exemplo de agrupamento lado a lado com um pincel de imagem](../../../../docs/framework/wpf/graphics-multimedia/media/0.png "0")</span><span class="sxs-lookup"><span data-stu-id="8ed9b-114">![Example of tiling with an image brush](../../../../docs/framework/wpf/graphics-multimedia/media/0.png "0")</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#RelativeTileSizeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#relativetilesizeexample)]  
  
 <span data-ttu-id="8ed9b-115">O exemplo a seguir cria um <xref:System.Windows.Media.ImageBrush>, define seu <xref:System.Windows.Media.TileBrush.Viewport%2A> para `0,0,25,25` e sua <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> para <xref:System.Windows.Media.BrushMappingMode.Absolute>e o utiliza para pintar outro retângulo.</span><span class="sxs-lookup"><span data-stu-id="8ed9b-115">The next example creates an <xref:System.Windows.Media.ImageBrush>, sets its <xref:System.Windows.Media.TileBrush.Viewport%2A> to `0,0,25,25` and its <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> to <xref:System.Windows.Media.BrushMappingMode.Absolute>, and uses it to paint another rectangle.</span></span> <span data-ttu-id="8ed9b-116">Como resultado, o pincel produz blocos com uma largura de 25 pixels e uma altura de 25 pixels.</span><span class="sxs-lookup"><span data-stu-id="8ed9b-116">As a result, the brush produces tiles that have a width of 25  pixels and a height of 25 pixels .</span></span>  
  
 <span data-ttu-id="8ed9b-117">A ilustração a seguir mostra a saída que esse exemplo produz.</span><span class="sxs-lookup"><span data-stu-id="8ed9b-117">The following illustration shows the output that the example produces.</span></span>  
  
 <span data-ttu-id="8ed9b-118">![Um TileBrush organizado lado a lado com um Viewport de 0,0,0,25,0,25](../../../../docs/framework/wpf/graphics-multimedia/media/25x25viewport.png "25x25viewport")</span><span class="sxs-lookup"><span data-stu-id="8ed9b-118">![A tiled TileBrush with a Viewport of 0,0,0.25,0.25](../../../../docs/framework/wpf/graphics-multimedia/media/25x25viewport.png "25x25viewport")</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#AbsoluteTileSizeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#absolutetilesizeexample)]  
  
 <span data-ttu-id="8ed9b-119">Os exemplos anteriores fazem parte de um exemplo maior.</span><span class="sxs-lookup"><span data-stu-id="8ed9b-119">The preceding examples are part of a larger sample.</span></span> <span data-ttu-id="8ed9b-120">Para o exemplo completo, consulte [ImageBrush exemplo](http://go.microsoft.com/fwlink/?LinkID=160005).</span><span class="sxs-lookup"><span data-stu-id="8ed9b-120">For the complete sample, see [ImageBrush Sample](http://go.microsoft.com/fwlink/?LinkID=160005).</span></span>  
  
 <span data-ttu-id="8ed9b-121">Embora este exemplo usa o <xref:System.Windows.Media.ImageBrush> classe, o <xref:System.Windows.Media.TileBrush.Viewport%2A> e <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> propriedades se comportam de forma idêntica para os outros <xref:System.Windows.Media.TileBrush> objetos, ou seja, para <xref:System.Windows.Media.DrawingBrush> e <xref:System.Windows.Media.VisualBrush>.</span><span class="sxs-lookup"><span data-stu-id="8ed9b-121">Although this example uses the <xref:System.Windows.Media.ImageBrush> class, the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> properties behave identically for the other <xref:System.Windows.Media.TileBrush> objects, that is, for <xref:System.Windows.Media.DrawingBrush> and <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="8ed9b-122">Para obter mais informações sobre <xref:System.Windows.Media.ImageBrush> e outros <xref:System.Windows.Media.TileBrush> objetos, consulte [pintura com imagens, desenhos e visuais](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).</span><span class="sxs-lookup"><span data-stu-id="8ed9b-122">For more information about <xref:System.Windows.Media.ImageBrush> and the other <xref:System.Windows.Media.TileBrush> objects, see [Painting with Images, Drawings, and Visuals](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ed9b-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ed9b-123">See Also</span></span>  
 <xref:System.Windows.Media.TileBrush>  
 [<span data-ttu-id="8ed9b-124">Pintando com imagens, desenhos e visuais</span><span class="sxs-lookup"><span data-stu-id="8ed9b-124">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [<span data-ttu-id="8ed9b-125">Criar padrões de bloco diferentes com um TileBrush</span><span class="sxs-lookup"><span data-stu-id="8ed9b-125">Create Different Tile Patterns with a TileBrush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-different-tile-patterns-with-a-tilebrush.md)
