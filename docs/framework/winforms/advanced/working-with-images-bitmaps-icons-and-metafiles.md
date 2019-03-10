---
title: Trabalhando com imagens, bitmaps, ícones e metarquivos
ms.date: 03/30/2017
helpviewer_keywords:
- metafiles [Windows Forms], working with
- examples [Windows Forms], bitmaps
- examples [Windows Forms], images
- bitmaps [Windows Forms], working with
- images [Windows Forms], working with
- examples [Windows Forms], metafiles
ms.assetid: a626d701-bd99-4fd8-b92f-7b8f794e042b
ms.openlocfilehash: 61d534f8299c920f656abe4280cc3ea5e609c0b2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710453"
---
# <a name="working-with-images-bitmaps-icons-and-metafiles"></a><span data-ttu-id="124d8-102">Trabalhando com imagens, bitmaps, ícones e metarquivos</span><span class="sxs-lookup"><span data-stu-id="124d8-102">Working with Images, Bitmaps, Icons, and Metafiles</span></span>
<span data-ttu-id="124d8-103">O [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] fornece a classe `Bitmap` para trabalhar com imagens de varredura e a classe `Metafile` para trabalhar com imagens vetoriais.</span><span class="sxs-lookup"><span data-stu-id="124d8-103">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] provides the `Bitmap` class for working with raster images and the `Metafile` class for working with vector images.</span></span> <span data-ttu-id="124d8-104">as classes `Bitmap` e `Metafile` são herdadas da classe `Image`.</span><span class="sxs-lookup"><span data-stu-id="124d8-104">The `Bitmap` and the `Metafile` classes both inherit from the `Image` class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="124d8-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="124d8-105">In This Section</span></span>  
 [<span data-ttu-id="124d8-106">Como: Desenhar um Bitmap existente na tela</span><span class="sxs-lookup"><span data-stu-id="124d8-106">How to: Draw an Existing Bitmap to the Screen</span></span>](how-to-draw-an-existing-bitmap-to-the-screen.md)  
 <span data-ttu-id="124d8-107">Descreve como carregar e desenhar bitmaps.</span><span class="sxs-lookup"><span data-stu-id="124d8-107">Describes how to load and draw bitmaps.</span></span>  
  
 [<span data-ttu-id="124d8-108">Como: Carregar e exibir metarquivos</span><span class="sxs-lookup"><span data-stu-id="124d8-108">How to: Load and Display Metafiles</span></span>](how-to-load-and-display-metafiles.md)  
 <span data-ttu-id="124d8-109">Mostra como carregar e desenhar metarquivos.</span><span class="sxs-lookup"><span data-stu-id="124d8-109">Shows how to load and draw metafiles.</span></span>  
  
 [<span data-ttu-id="124d8-110">Cortar e Dimensionar Imagens no GDI+</span><span class="sxs-lookup"><span data-stu-id="124d8-110">Cropping and Scaling Images in GDI+</span></span>](cropping-and-scaling-images-in-gdi.md)  
 <span data-ttu-id="124d8-111">Explica como cortar e dimensionar imagens vetoriais e de varredura.</span><span class="sxs-lookup"><span data-stu-id="124d8-111">Explains how to crop and scale vector and raster images.</span></span>  
  
 [<span data-ttu-id="124d8-112">Como: Girar, refletir e distorcer imagens</span><span class="sxs-lookup"><span data-stu-id="124d8-112">How to: Rotate, Reflect, and Skew Images</span></span>](how-to-rotate-reflect-and-skew-images.md)  
 <span data-ttu-id="124d8-113">Descreve como desenhar imagens giradas, refletidas e distorcidas.</span><span class="sxs-lookup"><span data-stu-id="124d8-113">Describes how to draw rotated, reflected and skewed images.</span></span>  
  
 [<span data-ttu-id="124d8-114">Como: Usar o modo de interpolação para controlar a qualidade da imagem durante o dimensionamento</span><span class="sxs-lookup"><span data-stu-id="124d8-114">How to: Use Interpolation Mode to Control Image Quality During Scaling</span></span>](how-to-use-interpolation-mode-to-control-image-quality-during-scaling.md)  
 <span data-ttu-id="124d8-115">Mostra como usar o <xref:System.Drawing.Drawing2D.InterpolationMode> enumeração para alterar a qualidade da imagem.</span><span class="sxs-lookup"><span data-stu-id="124d8-115">Shows how to use the <xref:System.Drawing.Drawing2D.InterpolationMode> enumeration to change image quality.</span></span>  
  
 [<span data-ttu-id="124d8-116">Como: Criar imagens em miniatura</span><span class="sxs-lookup"><span data-stu-id="124d8-116">How to: Create Thumbnail Images</span></span>](how-to-create-thumbnail-images.md)  
 <span data-ttu-id="124d8-117">Descreve como criar imagens em miniatura.</span><span class="sxs-lookup"><span data-stu-id="124d8-117">Describes how to create thumbnail images.</span></span>  
  
 [<span data-ttu-id="124d8-118">Como: Melhorar o desempenho, evitando o dimensionamento automático</span><span class="sxs-lookup"><span data-stu-id="124d8-118">How to: Improve Performance by Avoiding Automatic Scaling</span></span>](how-to-improve-performance-by-avoiding-automatic-scaling.md)  
 <span data-ttu-id="124d8-119">Explica como desenhar uma imagem sem o dimensionamento automático.</span><span class="sxs-lookup"><span data-stu-id="124d8-119">Explains how to draw an image without automatic scaling.</span></span>  
  
 [<span data-ttu-id="124d8-120">Como: Ler metadados de imagem</span><span class="sxs-lookup"><span data-stu-id="124d8-120">How to: Read Image Metadata</span></span>](how-to-read-image-metadata.md)  
 <span data-ttu-id="124d8-121">Descreve como ler metadados de uma imagem.</span><span class="sxs-lookup"><span data-stu-id="124d8-121">Describes how to read metadata from an image.</span></span>  
  
 [<span data-ttu-id="124d8-122">Como: Criar um Bitmap em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="124d8-122">How to: Create a Bitmap at Run Time</span></span>](how-to-create-a-bitmap-at-run-time.md)  
 <span data-ttu-id="124d8-123">Mostra como desenhar um bitmap em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="124d8-123">Shows how to draw a bitmap at runtime.</span></span>  
  
 [<span data-ttu-id="124d8-124">Como: Extrair o ícone associado a um arquivo nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="124d8-124">How to: Extract the Icon Associated with a File in Windows Forms</span></span>](how-to-extract-the-icon-associated-with-a-file-in-windows-forms.md)  
 <span data-ttu-id="124d8-125">Descreve como extrair um ícone que seja um recurso inserido de um arquivo.</span><span class="sxs-lookup"><span data-stu-id="124d8-125">Describes how to extract an icon that is an embedded resource of a file.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="124d8-126">Referência</span><span class="sxs-lookup"><span data-stu-id="124d8-126">Reference</span></span>  
 <xref:System.Drawing.Image>  
 <span data-ttu-id="124d8-127">Descreve essa classe e tem links para todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="124d8-127">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Imaging.Metafile>  
 <span data-ttu-id="124d8-128">Descreve essa classe e tem links para todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="124d8-128">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Bitmap>  
 <span data-ttu-id="124d8-129">Descreve essa classe e tem links para todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="124d8-129">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="124d8-130">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="124d8-130">Related Sections</span></span>  
 [<span data-ttu-id="124d8-131">Imagens, bitmaps e metarquivos</span><span class="sxs-lookup"><span data-stu-id="124d8-131">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)  
 <span data-ttu-id="124d8-132">Contém links para tópicos que discutem diferentes tipos de bitmaps e como manipulá-los em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="124d8-132">Contains links to topics that discuss different types of bitmaps and manipulating them in your applications.</span></span>
