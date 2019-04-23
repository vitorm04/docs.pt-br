---
title: 'Como: Organizar lado a lado uma forma com uma imagem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- texture brushes [Windows Forms], tiling images with
- images [Windows Forms], filling shapes with
- shapes [Windows Forms], tiling with images
- bitmaps [Windows Forms], filling shapes with
ms.assetid: 6d407891-6e5c-4495-a546-3da5604e9fb8
ms.openlocfilehash: ad7b8737a63028e533cadfa6db56b063eb943f22
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59221532"
---
# <a name="how-to-tile-a-shape-with-an-image"></a><span data-ttu-id="ca678-102">Como: Organizar lado a lado uma forma com uma imagem</span><span class="sxs-lookup"><span data-stu-id="ca678-102">How to: Tile a Shape with an Image</span></span>
<span data-ttu-id="ca678-103">Da mesma forma que blocos podem ser colocados lado a lado para recobrir um piso, imagens retangulares podem ser colocadas umas ao lado das outras para preencher (organizar lado a lado) uma forma.</span><span class="sxs-lookup"><span data-stu-id="ca678-103">Just as tiles can be placed next to each other to cover a floor, rectangular images can be placed next to each other to fill (tile) a shape.</span></span> <span data-ttu-id="ca678-104">Para organizar o interior de uma forma lado a lado, use um pincel de textura.</span><span class="sxs-lookup"><span data-stu-id="ca678-104">To tile the interior of a shape, use a texture brush.</span></span> <span data-ttu-id="ca678-105">Quando você constrói uma <xref:System.Drawing.TextureBrush> do objeto, um dos argumentos passados para o construtor é um <xref:System.Drawing.Image> objeto.</span><span class="sxs-lookup"><span data-stu-id="ca678-105">When you construct a <xref:System.Drawing.TextureBrush> object, one of the arguments you pass to the constructor is an <xref:System.Drawing.Image> object.</span></span> <span data-ttu-id="ca678-106">Quando você usa o pincel de textura para pintar o interior de uma forma, ela será preenchida com repetidas cópias dessa imagem.</span><span class="sxs-lookup"><span data-stu-id="ca678-106">When you use the texture brush to paint the interior of a shape, the shape is filled with repeated copies of this image.</span></span>  
  
 <span data-ttu-id="ca678-107">A propriedade de modo de encapsulamento do <xref:System.Drawing.TextureBrush> objeto determina como a imagem é orientada conforme ele é repetida em uma grade retangular.</span><span class="sxs-lookup"><span data-stu-id="ca678-107">The wrap mode property of the <xref:System.Drawing.TextureBrush> object determines how the image is oriented as it is repeated in a rectangular grid.</span></span> <span data-ttu-id="ca678-108">Você pode fazer todos os blocos na grade terem a mesma orientação ou fazer com que a imagem fique invertida de uma posição de grade para a próxima.</span><span class="sxs-lookup"><span data-stu-id="ca678-108">You can make all the tiles in the grid have the same orientation, or you can make the image flip from one grid position to the next.</span></span> <span data-ttu-id="ca678-109">A inversão pode ser horizontal, vertical ou ambas.</span><span class="sxs-lookup"><span data-stu-id="ca678-109">The flipping can be horizontal, vertical, or both.</span></span> <span data-ttu-id="ca678-110">Os exemplos a seguir demonstram organização lado a lado com tipos diferentes de inversão.</span><span class="sxs-lookup"><span data-stu-id="ca678-110">The following examples demonstrate tiling with different types of flipping.</span></span>  
  
### <a name="to-tile-an-image"></a><span data-ttu-id="ca678-111">Organizar uma imagem lado a lado</span><span class="sxs-lookup"><span data-stu-id="ca678-111">To tile an image</span></span>  
  
-   <span data-ttu-id="ca678-112">Este exemplo usa a imagem de 75 × 75 a seguir para organização lado a lado em um retângulo de 200 × 200.</span><span class="sxs-lookup"><span data-stu-id="ca678-112">This example uses the following 75×75 image to tile a 200×200 rectangle.</span></span>  
  
 <span data-ttu-id="ca678-113">![Bloco 1](./media/tile1.gif "tile1")</span><span class="sxs-lookup"><span data-stu-id="ca678-113">![Tile 1](./media/tile1.gif "tile1")</span></span>  
  
-   <span data-ttu-id="ca678-114">A ilustração a seguir mostra como o retângulo é organizado lado a lado com a imagem.</span><span class="sxs-lookup"><span data-stu-id="ca678-114">The following illustration shows how the rectangle is tiled with the image.</span></span> <span data-ttu-id="ca678-115">Observe que todos os blocos têm a mesma orientação; não há nenhum inversão.</span><span class="sxs-lookup"><span data-stu-id="ca678-115">Note that all tiles have the same orientation; there is no flipping.</span></span>  
  
 <span data-ttu-id="ca678-116">![Bloco 2](./media/tile2.gif "tile2")</span><span class="sxs-lookup"><span data-stu-id="ca678-116">![Tile 2](./media/tile2.gif "tile2")</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingABrush#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#31)]  
  
### <a name="to-flip-an-image-horizontally-while-tiling"></a><span data-ttu-id="ca678-117">Inverter uma imagem horizontalmente com organização lado a lado</span><span class="sxs-lookup"><span data-stu-id="ca678-117">To flip an image horizontally while tiling</span></span>  
  
-   <span data-ttu-id="ca678-118">Este exemplo usa a mesma imagem de 75 × 75 para preencher um retângulo 200 × 200.</span><span class="sxs-lookup"><span data-stu-id="ca678-118">This example uses the same 75×75 image to fill a 200×200 rectangle.</span></span> <span data-ttu-id="ca678-119">O modo de encapsulamento é definido para inverter a imagem horizontalmente.</span><span class="sxs-lookup"><span data-stu-id="ca678-119">The wrap mode is set to flip the image horizontally.</span></span> <span data-ttu-id="ca678-120">A ilustração a seguir mostra como o retângulo é organizado lado a lado com a imagem.</span><span class="sxs-lookup"><span data-stu-id="ca678-120">The following illustration shows how the rectangle is tiled with the image.</span></span> <span data-ttu-id="ca678-121">Observe que, ao mudar de um bloco para o próximo em uma determinada linha, a imagem é invertida horizontalmente.</span><span class="sxs-lookup"><span data-stu-id="ca678-121">Note that as you move from one tile to the next in a given row, the image is flipped horizontally.</span></span>  
  
 <span data-ttu-id="ca678-122">![Bloco 3](./media/tile3.gif "tile3")</span><span class="sxs-lookup"><span data-stu-id="ca678-122">![Tile 3](./media/tile3.gif "tile3")</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.UsingABrush#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#32)]  
  
### <a name="to-flip-an-image-vertically-while-tiling"></a><span data-ttu-id="ca678-123">Inverter uma imagem verticalmente com organização lado a lado</span><span class="sxs-lookup"><span data-stu-id="ca678-123">To flip an image vertically while tiling</span></span>  
  
-   <span data-ttu-id="ca678-124">Este exemplo usa a mesma imagem de 75 × 75 para preencher um retângulo 200 × 200.</span><span class="sxs-lookup"><span data-stu-id="ca678-124">This example uses the same 75×75 image to fill a 200×200 rectangle.</span></span> <span data-ttu-id="ca678-125">O modo de encapsulamento é definido para inverter a imagem verticalmente.</span><span class="sxs-lookup"><span data-stu-id="ca678-125">The wrap mode is set to flip the image vertically.</span></span>  
  
     [!code-csharp[System.Drawing.UsingABrush#33](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#33)]
     [!code-vb[System.Drawing.UsingABrush#33](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#33)]  
  
### <a name="to-flip-an-image-horizontally-and-vertically-while-tiling"></a><span data-ttu-id="ca678-126">Inverter uma imagem horizontalmente e verticalmente com organização lado a lado</span><span class="sxs-lookup"><span data-stu-id="ca678-126">To flip an image horizontally and vertically while tiling</span></span>  
  
-   <span data-ttu-id="ca678-127">Este exemplo usa a mesma imagem de 75 × 75 para organizar lado a lado um retângulo de 200 × 200.</span><span class="sxs-lookup"><span data-stu-id="ca678-127">This example uses the same 75×75 image to tile a 200×200 rectangle.</span></span> <span data-ttu-id="ca678-128">O modo de encapsulamento é definido para inverter a imagem tanto horizontalmente quanto verticalmente.</span><span class="sxs-lookup"><span data-stu-id="ca678-128">The wrap mode is set to flip the image both horizontally and vertically.</span></span> <span data-ttu-id="ca678-129">A ilustração a seguir mostra como o retângulo é organizado lado a lado pela imagem.</span><span class="sxs-lookup"><span data-stu-id="ca678-129">The following illustration shows how the rectangle is tiled by the image.</span></span> <span data-ttu-id="ca678-130">Observe que, ao mudar de um bloco para o próximo em uma determinada linha, a imagem é invertida horizontalmente e, ao mudar de um bloco para o próximo em uma determinada coluna, a imagem é invertida verticalmente.</span><span class="sxs-lookup"><span data-stu-id="ca678-130">Note that as you move from one tile to the next in a given row, the image is flipped horizontally, and as you move from one tile to the next in a given column, the image is flipped vertically.</span></span>  
  
 <span data-ttu-id="ca678-131">![Bloco 5](./media/tile5.gif "tile5")</span><span class="sxs-lookup"><span data-stu-id="ca678-131">![Tile 5](./media/tile5.gif "tile5")</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#34](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.UsingABrush#34](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#34)]  
  
## <a name="see-also"></a><span data-ttu-id="ca678-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ca678-132">See also</span></span>

- [<span data-ttu-id="ca678-133">Usando um pincel para preencher formas</span><span class="sxs-lookup"><span data-stu-id="ca678-133">Using a Brush to Fill Shapes</span></span>](using-a-brush-to-fill-shapes.md)
