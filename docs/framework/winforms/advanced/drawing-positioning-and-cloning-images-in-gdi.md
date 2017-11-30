---
title: Desenhando, posicionando e clonando imagens no GDI+
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
- raster images [Windows Forms]
- images [Windows Forms], positioning
- drawing [Windows Forms], images
- drawing [Windows Forms], raster images
- images [Windows Forms], cloning
- images [Windows Forms], drawing
- GDI+, drawing images
- GDI+, cloning images
- GDI+, positioning images
ms.assetid: 09f0c07a-19c0-43b4-90a2-862a10545ce8
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a3ba716a36280d2ac08dae907abbdbe05e563dfc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="drawing-positioning-and-cloning-images-in-gdi"></a><span data-ttu-id="e0408-102">Desenhando, posicionando e clonando imagens no GDI+</span><span class="sxs-lookup"><span data-stu-id="e0408-102">Drawing, Positioning, and Cloning Images in GDI+</span></span>
<span data-ttu-id="e0408-103">Você pode usar o <xref:System.Drawing.Bitmap> classe para carregar e exibir as imagens de varredura e você pode usar o <xref:System.Drawing.Imaging.Metafile> classe para carregar e exibir imagens de vetor.</span><span class="sxs-lookup"><span data-stu-id="e0408-103">You can use the <xref:System.Drawing.Bitmap> class to load and display raster images, and you can use the <xref:System.Drawing.Imaging.Metafile> class to load and display vector images.</span></span> <span data-ttu-id="e0408-104">O <xref:System.Drawing.Bitmap> e <xref:System.Drawing.Imaging.Metafile> classes herdam o <xref:System.Drawing.Image> classe.</span><span class="sxs-lookup"><span data-stu-id="e0408-104">The <xref:System.Drawing.Bitmap> and <xref:System.Drawing.Imaging.Metafile> classes inherit from the <xref:System.Drawing.Image> class.</span></span> <span data-ttu-id="e0408-105">Para exibir uma imagem de vetor, você precisa de uma ocorrência da <xref:System.Drawing.Graphics> classe e um <xref:System.Drawing.Imaging.Metafile>.</span><span class="sxs-lookup"><span data-stu-id="e0408-105">To display a vector image, you need an instance of the <xref:System.Drawing.Graphics> class and a <xref:System.Drawing.Imaging.Metafile>.</span></span> <span data-ttu-id="e0408-106">Para exibir uma imagem de varredura, você precisa de uma ocorrência da <xref:System.Drawing.Graphics> classe e um <xref:System.Drawing.Bitmap>.</span><span class="sxs-lookup"><span data-stu-id="e0408-106">To display a raster image, you need an instance of the <xref:System.Drawing.Graphics> class and a <xref:System.Drawing.Bitmap>.</span></span> <span data-ttu-id="e0408-107">A instância do <xref:System.Drawing.Graphics> classe fornece a <xref:System.Drawing.Graphics.DrawImage%2A> método, que recebe o <xref:System.Drawing.Imaging.Metafile> ou <xref:System.Drawing.Bitmap> como um argumento.</span><span class="sxs-lookup"><span data-stu-id="e0408-107">The instance of the <xref:System.Drawing.Graphics> class provides the <xref:System.Drawing.Graphics.DrawImage%2A> method, which receives the <xref:System.Drawing.Imaging.Metafile> or <xref:System.Drawing.Bitmap> as an argument.</span></span>  
  
## <a name="file-types-and-cloning"></a><span data-ttu-id="e0408-108">Tipos de arquivo e clonagem</span><span class="sxs-lookup"><span data-stu-id="e0408-108">File Types and Cloning</span></span>  
 <span data-ttu-id="e0408-109">O exemplo de código a seguir mostra como construir um <xref:System.Drawing.Bitmap> do arquivo Climber.jpg e exibe o bitmap.</span><span class="sxs-lookup"><span data-stu-id="e0408-109">The following code example shows how to construct a <xref:System.Drawing.Bitmap> from the file Climber.jpg and displays the bitmap.</span></span> <span data-ttu-id="e0408-110">O ponto de destino para o canto superior esquerdo da imagem, (10, 10), especificado no segundo e terceiro parâmetros.</span><span class="sxs-lookup"><span data-stu-id="e0408-110">The destination point for the upper-left corner of the image, (10, 10), is specified in the second and third parameters.</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#11)]  
  
 <span data-ttu-id="e0408-111">A ilustração a seguir mostra a imagem.</span><span class="sxs-lookup"><span data-stu-id="e0408-111">The following illustration shows the image.</span></span>  
  
 <span data-ttu-id="e0408-112">![Exemplo de imagem](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art04.gif "AboutGdip03_Art04")</span><span class="sxs-lookup"><span data-stu-id="e0408-112">![Image Sample](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art04.gif "AboutGdip03_Art04")</span></span>  
  
 <span data-ttu-id="e0408-113">Você pode construir <xref:System.Drawing.Bitmap> objetos de uma variedade de elementos gráficos de formatos de arquivo: BMP, GIF, JPEG, EXIF, PNG, TIFF e ícone.</span><span class="sxs-lookup"><span data-stu-id="e0408-113">You can construct <xref:System.Drawing.Bitmap> objects from a variety of graphics file formats: BMP, GIF, JPEG, EXIF, PNG, TIFF, and ICON.</span></span>  
  
 <span data-ttu-id="e0408-114">O exemplo de código a seguir mostra como construir <xref:System.Drawing.Bitmap> objetos de uma variedade de tipos de arquivo e, em seguida, exibe os bitmaps.</span><span class="sxs-lookup"><span data-stu-id="e0408-114">The following code example shows how to construct <xref:System.Drawing.Bitmap> objects from a variety of file types and then displays the bitmaps.</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#12)]  
  
 <span data-ttu-id="e0408-115">O <xref:System.Drawing.Bitmap> classe fornece um <xref:System.Drawing.Bitmap.Clone%2A> método que você pode usar para fazer uma cópia de um objeto existente <xref:System.Drawing.Bitmap>.</span><span class="sxs-lookup"><span data-stu-id="e0408-115">The <xref:System.Drawing.Bitmap> class provides a <xref:System.Drawing.Bitmap.Clone%2A> method that you can use to make a copy of an existing <xref:System.Drawing.Bitmap>.</span></span> <span data-ttu-id="e0408-116">O <xref:System.Drawing.Bitmap.Clone%2A> método tem um parâmetro de retângulo de origem que você pode usar para especificar a parte do bitmap original que você deseja copiar.</span><span class="sxs-lookup"><span data-stu-id="e0408-116">The <xref:System.Drawing.Bitmap.Clone%2A> method has a source rectangle parameter that you can use to specify the portion of the original bitmap that you want to copy.</span></span> <span data-ttu-id="e0408-117">O exemplo de código a seguir mostra como criar um <xref:System.Drawing.Bitmap> por meio da clonagem metade superior de um objeto existente <xref:System.Drawing.Bitmap>.</span><span class="sxs-lookup"><span data-stu-id="e0408-117">The following code example shows how to create a <xref:System.Drawing.Bitmap> by cloning the top half of an existing <xref:System.Drawing.Bitmap>.</span></span> <span data-ttu-id="e0408-118">As duas imagens são desenhadas.</span><span class="sxs-lookup"><span data-stu-id="e0408-118">Then both images are drawn.</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#13)]  
  
 <span data-ttu-id="e0408-119">A ilustração a seguir mostra as duas imagens.</span><span class="sxs-lookup"><span data-stu-id="e0408-119">The following illustration shows the two images.</span></span>  
  
 <span data-ttu-id="e0408-120">![Recorte](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art05.gif "AboutGdip03_Art05")</span><span class="sxs-lookup"><span data-stu-id="e0408-120">![Cropping](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art05.gif "AboutGdip03_Art05")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0408-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e0408-121">See Also</span></span>  
 [<span data-ttu-id="e0408-122">Imagens, bitmaps e metarquivos</span><span class="sxs-lookup"><span data-stu-id="e0408-122">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="e0408-123">Como Criar Objetos Gráficos para Desenho</span><span class="sxs-lookup"><span data-stu-id="e0408-123">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [<span data-ttu-id="e0408-124">Trabalhando com Imagens, Bitmaps, Ícones e Metarquivos</span><span class="sxs-lookup"><span data-stu-id="e0408-124">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
