---
title: Como definir o tamanho de lado para um TileBrush
ms.date: 03/30/2017
helpviewer_keywords:
- TileBrush [WPF], size of tile properties
- Viewport property of TileBrush [WPF]
ms.assetid: 04f41090-1b46-4e36-832f-d27d28708b8c
ms.openlocfilehash: af7bab59a292549b29dad9b6a7417f22b1b84e48
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186831"
---
# <a name="how-to-set-the-tile-size-for-a-tilebrush"></a><span data-ttu-id="8d945-102">Como definir o tamanho de lado para um TileBrush</span><span class="sxs-lookup"><span data-stu-id="8d945-102">How to: Set the Tile Size for a TileBrush</span></span>

<span data-ttu-id="8d945-103">Este exemplo mostra como definir o <xref:System.Windows.Media.TileBrush>tamanho do azulejo para um .</span><span class="sxs-lookup"><span data-stu-id="8d945-103">This example shows how to set the tile size for a <xref:System.Windows.Media.TileBrush>.</span></span> <span data-ttu-id="8d945-104">Por padrão, <xref:System.Windows.Media.TileBrush> um produz um único ladrilho que preenche completamente a área que você está pintando.</span><span class="sxs-lookup"><span data-stu-id="8d945-104">By default, a <xref:System.Windows.Media.TileBrush> produces a single tile that completely fills the area that you are painting.</span></span> <span data-ttu-id="8d945-105">Você pode substituir esse comportamento <xref:System.Windows.Media.TileBrush.Viewport%2A> <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> definindo as propriedades e as propriedades.</span><span class="sxs-lookup"><span data-stu-id="8d945-105">You can override this behavior by setting the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> properties.</span></span>

<span data-ttu-id="8d945-106">A <xref:System.Windows.Media.TileBrush.Viewport%2A> propriedade especifica o tamanho <xref:System.Windows.Media.TileBrush>do azulejo para um .</span><span class="sxs-lookup"><span data-stu-id="8d945-106">The <xref:System.Windows.Media.TileBrush.Viewport%2A> property specifies the tile size for a <xref:System.Windows.Media.TileBrush>.</span></span> <span data-ttu-id="8d945-107">Por padrão, o <xref:System.Windows.Media.TileBrush.Viewport%2A> valor do imóvel é relativo ao tamanho da área que está sendo pintada.</span><span class="sxs-lookup"><span data-stu-id="8d945-107">By default, the value of the <xref:System.Windows.Media.TileBrush.Viewport%2A> property is relative to the size of the area being painted.</span></span> <span data-ttu-id="8d945-108">Para fazer <xref:System.Windows.Media.TileBrush.Viewport%2A> com que a propriedade <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> especifique um tamanho absoluto de telhas, defina a propriedade como <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span><span class="sxs-lookup"><span data-stu-id="8d945-108">To make the <xref:System.Windows.Media.TileBrush.Viewport%2A> property specify an absolute tile size, set the <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> property to <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span></span>

## <a name="example"></a><span data-ttu-id="8d945-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8d945-109">Example</span></span>

<span data-ttu-id="8d945-110">O exemplo a <xref:System.Windows.Media.ImageBrush>seguir usa <xref:System.Windows.Media.TileBrush>um tipo de , para pintar um retângulo com telhas.</span><span class="sxs-lookup"><span data-stu-id="8d945-110">The following example uses an <xref:System.Windows.Media.ImageBrush>, a type of <xref:System.Windows.Media.TileBrush>, to paint a rectangle with tiles.</span></span> <span data-ttu-id="8d945-111">O exemplo define cada ladrilho para 50% por 50% da área de saída (o retângulo).</span><span class="sxs-lookup"><span data-stu-id="8d945-111">The example sets each tile to 50 percent by 50 percent of the output area (the rectangle).</span></span> <span data-ttu-id="8d945-112">Como resultado, o retângulo é pintado com quatro projeções da imagem.</span><span class="sxs-lookup"><span data-stu-id="8d945-112">As a result, the rectangle is painted with four projections of the image.</span></span>

<span data-ttu-id="8d945-113">A ilustração a seguir mostra a saída que o exemplo produz:</span><span class="sxs-lookup"><span data-stu-id="8d945-113">The following illustration shows the output that the example produces:</span></span>

![Um retângulo com quatro cerejas demonstrando revestimento com um pincel de imagem.](./media/how-to-set-the-tile-size-for-a-tilebrush/rectangle-tile-image-brush.png)

[!code-csharp[UsingImageBrush_snip#RelativeTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#relativetilesizeexample)]

<span data-ttu-id="8d945-115">O próximo exemplo <xref:System.Windows.Media.ImageBrush>cria <xref:System.Windows.Media.TileBrush.Viewport%2A> um `0,0,25,25` , <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> <xref:System.Windows.Media.BrushMappingMode.Absolute>define o seu e o seu para , e usa-o para pintar outro retângulo.</span><span class="sxs-lookup"><span data-stu-id="8d945-115">The next example creates an <xref:System.Windows.Media.ImageBrush>, sets its <xref:System.Windows.Media.TileBrush.Viewport%2A> to `0,0,25,25` and its <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> to <xref:System.Windows.Media.BrushMappingMode.Absolute>, and uses it to paint another rectangle.</span></span> <span data-ttu-id="8d945-116">Como resultado, o pincel produz blocos com uma largura de 25 pixels e uma altura de 25 pixels.</span><span class="sxs-lookup"><span data-stu-id="8d945-116">As a result, the brush produces tiles that have a width of 25  pixels and a height of 25 pixels .</span></span>

<span data-ttu-id="8d945-117">A ilustração a seguir mostra a saída que o exemplo produz:</span><span class="sxs-lookup"><span data-stu-id="8d945-117">The following illustration shows the output that the example produces:</span></span>

![Um retângulo com quarenta e oito cerejas demonstrando um TileBrush ladrilho com um Viewport.](./media/how-to-set-the-tile-size-for-a-tilebrush/25-x-25-viewport-tilebrush.png)

[!code-csharp[UsingImageBrush_snip#AbsoluteTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#absolutetilesizeexample)]

<span data-ttu-id="8d945-119">Os exemplos anteriores fazem parte de um exemplo maior.</span><span class="sxs-lookup"><span data-stu-id="8d945-119">The preceding examples are part of a larger sample.</span></span> <span data-ttu-id="8d945-120">Para obter a amostra completa, consulte [ImageBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush).</span><span class="sxs-lookup"><span data-stu-id="8d945-120">For the complete sample, see [ImageBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush).</span></span>

<span data-ttu-id="8d945-121">Embora este exemplo <xref:System.Windows.Media.ImageBrush> use <xref:System.Windows.Media.TileBrush.Viewport%2A> a <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> classe, as propriedades <xref:System.Windows.Media.TileBrush> e as propriedades <xref:System.Windows.Media.DrawingBrush> se <xref:System.Windows.Media.VisualBrush>comportam de forma idêntica para os outros objetos, ou seja, para e .</span><span class="sxs-lookup"><span data-stu-id="8d945-121">Although this example uses the <xref:System.Windows.Media.ImageBrush> class, the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> properties behave identically for the other <xref:System.Windows.Media.TileBrush> objects, that is, for <xref:System.Windows.Media.DrawingBrush> and <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="8d945-122">Para obter <xref:System.Windows.Media.ImageBrush> mais informações <xref:System.Windows.Media.TileBrush> sobre e os outros objetos, consulte [Pintura com Imagens, Desenhos e Visuais](painting-with-images-drawings-and-visuals.md).</span><span class="sxs-lookup"><span data-stu-id="8d945-122">For more information about <xref:System.Windows.Media.ImageBrush> and the other <xref:System.Windows.Media.TileBrush> objects, see [Painting with Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8d945-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="8d945-123">See also</span></span>

- <xref:System.Windows.Media.TileBrush>
- [<span data-ttu-id="8d945-124">Pintando com imagens, desenhos e visuais</span><span class="sxs-lookup"><span data-stu-id="8d945-124">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="8d945-125">Criar padrões de bloco diferentes com um TileBrush</span><span class="sxs-lookup"><span data-stu-id="8d945-125">Create Different Tile Patterns with a TileBrush</span></span>](how-to-create-different-tile-patterns-with-a-tilebrush.md)
