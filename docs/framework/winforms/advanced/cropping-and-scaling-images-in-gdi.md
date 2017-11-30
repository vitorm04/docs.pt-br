---
title: Cortando e dimensionando imagens no GDI+
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI+, scaling images
- GDI+, cropping images
- images [Windows Forms], cropping
- compressing data [Windows Forms], images
- images [Windows Forms], expansion
- images [Windows Forms], scaling
- rectangles [Windows Forms], source
- rectangles [Windows Forms], destination
- images [Windows Forms], compression
ms.assetid: ad5daf26-005f-45bc-a2af-e0e97777a21a
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 63e1e55e57d586cbbca87361b95c18f0f53b8c75
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="cropping-and-scaling-images-in-gdi"></a><span data-ttu-id="2fe45-102">Cortando e dimensionando imagens no GDI+</span><span class="sxs-lookup"><span data-stu-id="2fe45-102">Cropping and Scaling Images in GDI+</span></span>
<span data-ttu-id="2fe45-103">Você pode usar o <xref:System.Drawing.Graphics.DrawImage%2A> método o <xref:System.Drawing.Graphics> classe para desenhar e posicionar o vetor de imagens e imagens de varredura.</span><span class="sxs-lookup"><span data-stu-id="2fe45-103">You can use the <xref:System.Drawing.Graphics.DrawImage%2A> method of the <xref:System.Drawing.Graphics> class to draw and position vector images and raster images.</span></span> <span data-ttu-id="2fe45-104"><xref:System.Drawing.Graphics.DrawImage%2A>é um método sobrecarregado, portanto, há várias maneiras que você pode fornecer argumentos.</span><span class="sxs-lookup"><span data-stu-id="2fe45-104"><xref:System.Drawing.Graphics.DrawImage%2A> is an overloaded method, so there are several ways you can supply it with arguments.</span></span>  
  
## <a name="drawimage-variations"></a><span data-ttu-id="2fe45-105">Variações de DrawImage</span><span class="sxs-lookup"><span data-stu-id="2fe45-105">DrawImage Variations</span></span>  
 <span data-ttu-id="2fe45-106">Uma variação do <xref:System.Drawing.Graphics.DrawImage%2A> método recebe um <xref:System.Drawing.Bitmap> e um <xref:System.Drawing.Rectangle>.</span><span class="sxs-lookup"><span data-stu-id="2fe45-106">One variation of the <xref:System.Drawing.Graphics.DrawImage%2A> method receives a <xref:System.Drawing.Bitmap> and a <xref:System.Drawing.Rectangle>.</span></span> <span data-ttu-id="2fe45-107">O retângulo especifica o destino da operação de desenho ou seja, especifica o retângulo no qual a imagem será desenhada.</span><span class="sxs-lookup"><span data-stu-id="2fe45-107">The rectangle specifies the destination for the drawing operation; that is, it specifies the rectangle in which to draw the image.</span></span> <span data-ttu-id="2fe45-108">Se o tamanho do retângulo de destino for diferente do tamanho da imagem original, a escala dela será ajustada para caber no retângulo de destino.</span><span class="sxs-lookup"><span data-stu-id="2fe45-108">If the size of the destination rectangle is different from the size of the original image, the image is scaled to fit the destination rectangle.</span></span> <span data-ttu-id="2fe45-109">O exemplo de código a seguir mostra como desenhar a mesma imagem três vezes: uma vez sem escala, uma vez expandida e outra compactada:</span><span class="sxs-lookup"><span data-stu-id="2fe45-109">The following code example shows how to draw the same image three times: once with no scaling, once with an expansion, and once with a compression:</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#31)]  
  
 <span data-ttu-id="2fe45-110">A ilustração a seguir mostra as três imagens.</span><span class="sxs-lookup"><span data-stu-id="2fe45-110">The following illustration shows the three pictures.</span></span>  
  
 <span data-ttu-id="2fe45-111">![Colocação em escala](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art06.gif "AboutGdip03_Art06")</span><span class="sxs-lookup"><span data-stu-id="2fe45-111">![Scaling](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art06.gif "AboutGdip03_Art06")</span></span>  
  
 <span data-ttu-id="2fe45-112">Algumas variações do <xref:System.Drawing.Graphics.DrawImage%2A> método tem um parâmetro do retângulo de origem, bem como um parâmetro do retângulo de destino.</span><span class="sxs-lookup"><span data-stu-id="2fe45-112">Some variations of the <xref:System.Drawing.Graphics.DrawImage%2A> method have a source-rectangle parameter as well as a destination-rectangle parameter.</span></span> <span data-ttu-id="2fe45-113">O parâmetro do retângulo de origem especifica a parte da imagem original a ser desenhada.</span><span class="sxs-lookup"><span data-stu-id="2fe45-113">The source-rectangle parameter specifies the portion of the original image to draw.</span></span> <span data-ttu-id="2fe45-114">O retângulo de destino especifica o retângulo no qual desenhar a parte da imagem.</span><span class="sxs-lookup"><span data-stu-id="2fe45-114">The destination rectangle specifies the rectangle in which to draw that portion of the image.</span></span> <span data-ttu-id="2fe45-115">Se o tamanho do retângulo de destino for diferente do tamanho do retângulo de origem, a escala dela será ajustada para caber no retângulo de destino.</span><span class="sxs-lookup"><span data-stu-id="2fe45-115">If the size of the destination rectangle is different from the size of the source rectangle, the picture is scaled to fit the destination rectangle.</span></span>  
  
 <span data-ttu-id="2fe45-116">O exemplo de código a seguir mostra como construir um <xref:System.Drawing.Bitmap> do arquivo Runner.jpg.</span><span class="sxs-lookup"><span data-stu-id="2fe45-116">The following code example shows how to construct a <xref:System.Drawing.Bitmap> from the file Runner.jpg.</span></span> <span data-ttu-id="2fe45-117">Toda a imagem é desenhada sem nenhuma escala em (0, 0).</span><span class="sxs-lookup"><span data-stu-id="2fe45-117">The entire image is drawn with no scaling at (0, 0).</span></span> <span data-ttu-id="2fe45-118">Em seguida, uma pequena parte da imagem é desenhada duas vezes: uma expandida e outra compactada.</span><span class="sxs-lookup"><span data-stu-id="2fe45-118">Then a small portion of the image is drawn twice: once with a compression and once with an expansion.</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#32)]  
  
 <span data-ttu-id="2fe45-119">A ilustração a seguir mostra a imagem sem escala e as partes da imagem compactada e expandida.</span><span class="sxs-lookup"><span data-stu-id="2fe45-119">The following illustration shows the unscaled image, and the compressed and expanded image portions.</span></span>  
  
 <span data-ttu-id="2fe45-120">![Recorte e colocação em escala](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art07.gif "AboutGdip03_Art07")</span><span class="sxs-lookup"><span data-stu-id="2fe45-120">![Cropping and Scaling](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art07.gif "AboutGdip03_Art07")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fe45-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2fe45-121">See Also</span></span>  
 [<span data-ttu-id="2fe45-122">Imagens, bitmaps e metarquivos</span><span class="sxs-lookup"><span data-stu-id="2fe45-122">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="2fe45-123">Trabalhando com Imagens, Bitmaps, Ícones e Metarquivos</span><span class="sxs-lookup"><span data-stu-id="2fe45-123">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
