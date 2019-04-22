---
title: 'Como: Definir o tamanho de bloco um TileBrush'
ms.date: 03/30/2017
helpviewer_keywords:
- TileBrush [WPF], size of tile properties
- Viewport property of TileBrush [WPF]
ms.assetid: 04f41090-1b46-4e36-832f-d27d28708b8c
ms.openlocfilehash: 80b5dfc668464df829db593668bea8a9a4ec09e4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58839664"
---
# <a name="how-to-set-the-tile-size-for-a-tilebrush"></a><span data-ttu-id="ff6e5-102">Como: Definir o tamanho de bloco um TileBrush</span><span class="sxs-lookup"><span data-stu-id="ff6e5-102">How to: Set the Tile Size for a TileBrush</span></span>

<span data-ttu-id="ff6e5-103">Este exemplo mostra como definir o tamanho de bloco para um <xref:System.Windows.Media.TileBrush>.</span><span class="sxs-lookup"><span data-stu-id="ff6e5-103">This example shows how to set the tile size for a <xref:System.Windows.Media.TileBrush>.</span></span> <span data-ttu-id="ff6e5-104">Por padrão, um <xref:System.Windows.Media.TileBrush> produz um único bloco que preenche completamente a área que você está pintando.</span><span class="sxs-lookup"><span data-stu-id="ff6e5-104">By default, a <xref:System.Windows.Media.TileBrush> produces a single tile that completely fills the area that you are painting.</span></span> <span data-ttu-id="ff6e5-105">Você pode substituir esse comportamento, definindo a <xref:System.Windows.Media.TileBrush.Viewport%2A> e <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> propriedades.</span><span class="sxs-lookup"><span data-stu-id="ff6e5-105">You can override this behavior by setting the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> properties.</span></span>

<span data-ttu-id="ff6e5-106">O <xref:System.Windows.Media.TileBrush.Viewport%2A> propriedade especifica o tamanho de bloco para um <xref:System.Windows.Media.TileBrush>.</span><span class="sxs-lookup"><span data-stu-id="ff6e5-106">The <xref:System.Windows.Media.TileBrush.Viewport%2A> property specifies the tile size for a <xref:System.Windows.Media.TileBrush>.</span></span> <span data-ttu-id="ff6e5-107">Por padrão, o valor da <xref:System.Windows.Media.TileBrush.Viewport%2A> propriedade é relativo ao tamanho da área que está sendo pintada.</span><span class="sxs-lookup"><span data-stu-id="ff6e5-107">By default, the value of the <xref:System.Windows.Media.TileBrush.Viewport%2A> property is relative to the size of the area being painted.</span></span> <span data-ttu-id="ff6e5-108">Para tornar o <xref:System.Windows.Media.TileBrush.Viewport%2A> propriedade especificar um tamanho de bloco absoluto, defina a <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> propriedade para <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span><span class="sxs-lookup"><span data-stu-id="ff6e5-108">To make the <xref:System.Windows.Media.TileBrush.Viewport%2A> property specify an absolute tile size, set the <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> property to <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span></span>

## <a name="example"></a><span data-ttu-id="ff6e5-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ff6e5-109">Example</span></span>

<span data-ttu-id="ff6e5-110">O exemplo a seguir usa uma <xref:System.Windows.Media.ImageBrush>, um tipo de <xref:System.Windows.Media.TileBrush>, para desenhar um retângulo com blocos.</span><span class="sxs-lookup"><span data-stu-id="ff6e5-110">The following example uses an <xref:System.Windows.Media.ImageBrush>, a type of <xref:System.Windows.Media.TileBrush>, to paint a rectangle with tiles.</span></span> <span data-ttu-id="ff6e5-111">O exemplo define cada bloco para 50% por 50 por cento da área de saída (o retângulo).</span><span class="sxs-lookup"><span data-stu-id="ff6e5-111">The example sets each tile to 50 percent by 50 percent of the output area (the rectangle).</span></span> <span data-ttu-id="ff6e5-112">Como resultado, o retângulo é pintado com quatro projeções da imagem.</span><span class="sxs-lookup"><span data-stu-id="ff6e5-112">As a result, the rectangle is painted with four projections of the image.</span></span>

<span data-ttu-id="ff6e5-113">A ilustração a seguir mostra a saída que esse exemplo produz:</span><span class="sxs-lookup"><span data-stu-id="ff6e5-113">The following illustration shows the output that the example produces:</span></span>

![Um retângulo com quatro números errados demonstrando lado a lado com um pincel de imagem.](./media/how-to-set-the-tile-size-for-a-tilebrush/rectangle-tile-image-brush.png)

[!code-csharp[UsingImageBrush_snip#RelativeTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#relativetilesizeexample)]

<span data-ttu-id="ff6e5-115">O exemplo a seguir cria uma <xref:System.Windows.Media.ImageBrush>, define sua <xref:System.Windows.Media.TileBrush.Viewport%2A> para `0,0,25,25` e sua <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> para <xref:System.Windows.Media.BrushMappingMode.Absolute>e o utiliza para pintar outro retângulo.</span><span class="sxs-lookup"><span data-stu-id="ff6e5-115">The next example creates an <xref:System.Windows.Media.ImageBrush>, sets its <xref:System.Windows.Media.TileBrush.Viewport%2A> to `0,0,25,25` and its <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> to <xref:System.Windows.Media.BrushMappingMode.Absolute>, and uses it to paint another rectangle.</span></span> <span data-ttu-id="ff6e5-116">Como resultado, o pincel produz blocos com uma largura de 25 pixels e uma altura de 25 pixels.</span><span class="sxs-lookup"><span data-stu-id="ff6e5-116">As a result, the brush produces tiles that have a width of 25  pixels and a height of 25 pixels .</span></span>

<span data-ttu-id="ff6e5-117">A ilustração a seguir mostra a saída que esse exemplo produz:</span><span class="sxs-lookup"><span data-stu-id="ff6e5-117">The following illustration shows the output that the example produces:</span></span>

![Um retângulo com números errados de oito quarenta e demonstrar um TileBrush lado a lado com um visor.](./media/how-to-set-the-tile-size-for-a-tilebrush/25-x-25-viewport-tilebrush.png)

[!code-csharp[UsingImageBrush_snip#AbsoluteTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#absolutetilesizeexample)]

<span data-ttu-id="ff6e5-119">Os exemplos anteriores fazem parte de um exemplo maior.</span><span class="sxs-lookup"><span data-stu-id="ff6e5-119">The preceding examples are part of a larger sample.</span></span> <span data-ttu-id="ff6e5-120">Para o exemplo completo, consulte [exemplo de ImageBrush](https://go.microsoft.com/fwlink/?LinkID=160005).</span><span class="sxs-lookup"><span data-stu-id="ff6e5-120">For the complete sample, see [ImageBrush Sample](https://go.microsoft.com/fwlink/?LinkID=160005).</span></span>

<span data-ttu-id="ff6e5-121">Embora este exemplo usa o <xref:System.Windows.Media.ImageBrush> classe, o <xref:System.Windows.Media.TileBrush.Viewport%2A> e <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> propriedades se comportam de forma idêntica para os outros <xref:System.Windows.Media.TileBrush> objetos, ou seja, para <xref:System.Windows.Media.DrawingBrush> e <xref:System.Windows.Media.VisualBrush>.</span><span class="sxs-lookup"><span data-stu-id="ff6e5-121">Although this example uses the <xref:System.Windows.Media.ImageBrush> class, the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> properties behave identically for the other <xref:System.Windows.Media.TileBrush> objects, that is, for <xref:System.Windows.Media.DrawingBrush> and <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="ff6e5-122">Para obter mais informações sobre <xref:System.Windows.Media.ImageBrush> e o outro <xref:System.Windows.Media.TileBrush> objetos, consulte [pintando com imagens, desenhos e visuais](painting-with-images-drawings-and-visuals.md).</span><span class="sxs-lookup"><span data-stu-id="ff6e5-122">For more information about <xref:System.Windows.Media.ImageBrush> and the other <xref:System.Windows.Media.TileBrush> objects, see [Painting with Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ff6e5-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ff6e5-123">See also</span></span>

- <xref:System.Windows.Media.TileBrush>
- [<span data-ttu-id="ff6e5-124">Pintando com imagens, desenhos e visuais</span><span class="sxs-lookup"><span data-stu-id="ff6e5-124">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="ff6e5-125">Criar padrões de bloco diferentes com um TileBrush</span><span class="sxs-lookup"><span data-stu-id="ff6e5-125">Create Different Tile Patterns with a TileBrush</span></span>](how-to-create-different-tile-patterns-with-a-tilebrush.md)
