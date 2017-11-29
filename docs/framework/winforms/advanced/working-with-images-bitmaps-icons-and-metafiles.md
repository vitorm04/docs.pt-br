---
title: "Trabalhando com imagens, bitmaps, ícones e metarquivos"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- metafiles [Windows Forms], working with
- examples [Windows Forms], bitmaps
- examples [Windows Forms], images
- bitmaps [Windows Forms], working with
- images [Windows Forms], working with
- examples [Windows Forms], metafiles
ms.assetid: a626d701-bd99-4fd8-b92f-7b8f794e042b
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 53dc25d6a23c5cdbba1c640905eadbdc6b1acb71
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="working-with-images-bitmaps-icons-and-metafiles"></a><span data-ttu-id="13daa-102">Trabalhando com imagens, bitmaps, ícones e metarquivos</span><span class="sxs-lookup"><span data-stu-id="13daa-102">Working with Images, Bitmaps, Icons, and Metafiles</span></span>
<span data-ttu-id="13daa-103">O [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] fornece a classe `Bitmap` para trabalhar com imagens de varredura e a classe `Metafile` para trabalhar com imagens vetoriais.</span><span class="sxs-lookup"><span data-stu-id="13daa-103">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] provides the `Bitmap` class for working with raster images and the `Metafile` class for working with vector images.</span></span> <span data-ttu-id="13daa-104">as classes `Bitmap` e `Metafile` são herdadas da classe `Image`.</span><span class="sxs-lookup"><span data-stu-id="13daa-104">The `Bitmap` and the `Metafile` classes both inherit from the `Image` class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="13daa-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="13daa-105">In This Section</span></span>  
 [<span data-ttu-id="13daa-106">Como Desenhar um Bitmap Existente na Tela</span><span class="sxs-lookup"><span data-stu-id="13daa-106">How to: Draw an Existing Bitmap to the Screen</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-an-existing-bitmap-to-the-screen.md)  
 <span data-ttu-id="13daa-107">Descreve como carregar e desenhar bitmaps.</span><span class="sxs-lookup"><span data-stu-id="13daa-107">Describes how to load and draw bitmaps.</span></span>  
  
 [<span data-ttu-id="13daa-108">Como Carregar e Exibir Metarquivos</span><span class="sxs-lookup"><span data-stu-id="13daa-108">How to: Load and Display Metafiles</span></span>](../../../../docs/framework/winforms/advanced/how-to-load-and-display-metafiles.md)  
 <span data-ttu-id="13daa-109">Mostra como carregar e desenhar metarquivos.</span><span class="sxs-lookup"><span data-stu-id="13daa-109">Shows how to load and draw metafiles.</span></span>  
  
 [<span data-ttu-id="13daa-110">Cortar e Dimensionar Imagens no GDI+</span><span class="sxs-lookup"><span data-stu-id="13daa-110">Cropping and Scaling Images in GDI+</span></span>](../../../../docs/framework/winforms/advanced/cropping-and-scaling-images-in-gdi.md)  
 <span data-ttu-id="13daa-111">Explica como cortar e dimensionar imagens vetoriais e de varredura.</span><span class="sxs-lookup"><span data-stu-id="13daa-111">Explains how to crop and scale vector and raster images.</span></span>  
  
 [<span data-ttu-id="13daa-112">Como Girar, Refletir e Distorcer Imagens</span><span class="sxs-lookup"><span data-stu-id="13daa-112">How to: Rotate, Reflect, and Skew Images</span></span>](../../../../docs/framework/winforms/advanced/how-to-rotate-reflect-and-skew-images.md)  
 <span data-ttu-id="13daa-113">Descreve como desenhar imagens giradas, refletidas e distorcidas.</span><span class="sxs-lookup"><span data-stu-id="13daa-113">Describes how to draw rotated, reflected and skewed images.</span></span>  
  
 [<span data-ttu-id="13daa-114">Como Usar o Modo de Interpolação para Controlar a Qualidade da Imagem Durante o Dimensionamento</span><span class="sxs-lookup"><span data-stu-id="13daa-114">How to: Use Interpolation Mode to Control Image Quality During Scaling</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-interpolation-mode-to-control-image-quality-during-scaling.md)  
 <span data-ttu-id="13daa-115">Mostra como usar o <xref:System.Drawing.Drawing2D.InterpolationMode> enumeração para alterar a qualidade da imagem.</span><span class="sxs-lookup"><span data-stu-id="13daa-115">Shows how to use the <xref:System.Drawing.Drawing2D.InterpolationMode> enumeration to change image quality.</span></span>  
  
 [<span data-ttu-id="13daa-116">Como Criar Imagens em Miniatura</span><span class="sxs-lookup"><span data-stu-id="13daa-116">How to: Create Thumbnail Images</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-thumbnail-images.md)  
 <span data-ttu-id="13daa-117">Descreve como criar imagens em miniatura.</span><span class="sxs-lookup"><span data-stu-id="13daa-117">Describes how to create thumbnail images.</span></span>  
  
 [<span data-ttu-id="13daa-118">Como Melhorar o Desempenho Evitando a Colocação em Escala Automática</span><span class="sxs-lookup"><span data-stu-id="13daa-118">How to: Improve Performance by Avoiding Automatic Scaling</span></span>](../../../../docs/framework/winforms/advanced/how-to-improve-performance-by-avoiding-automatic-scaling.md)  
 <span data-ttu-id="13daa-119">Explica como desenhar uma imagem sem o dimensionamento automático.</span><span class="sxs-lookup"><span data-stu-id="13daa-119">Explains how to draw an image without automatic scaling.</span></span>  
  
 [<span data-ttu-id="13daa-120">Como Ler Metadados de Imagens</span><span class="sxs-lookup"><span data-stu-id="13daa-120">How to: Read Image Metadata</span></span>](../../../../docs/framework/winforms/advanced/how-to-read-image-metadata.md)  
 <span data-ttu-id="13daa-121">Descreve como ler metadados de uma imagem.</span><span class="sxs-lookup"><span data-stu-id="13daa-121">Describes how to read metadata from an image.</span></span>  
  
 [<span data-ttu-id="13daa-122">Como Criar um Bitmap em Tempo de Execução</span><span class="sxs-lookup"><span data-stu-id="13daa-122">How to: Create a Bitmap at Run Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-bitmap-at-run-time.md)  
 <span data-ttu-id="13daa-123">Mostra como desenhar um bitmap em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="13daa-123">Shows how to draw a bitmap at runtime.</span></span>  
  
 [<span data-ttu-id="13daa-124">Como Extrair o Ícone Associado a um Arquivo nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="13daa-124">How to: Extract the Icon Associated with a File in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-extract-the-icon-associated-with-a-file-in-windows-forms.md)  
 <span data-ttu-id="13daa-125">Descreve como extrair um ícone que seja um recurso inserido de um arquivo.</span><span class="sxs-lookup"><span data-stu-id="13daa-125">Describes how to extract an icon that is an embedded resource of a file.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="13daa-126">Referência</span><span class="sxs-lookup"><span data-stu-id="13daa-126">Reference</span></span>  
 <xref:System.Drawing.Image>  
 <span data-ttu-id="13daa-127">Descreve essa classe e tem links para todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="13daa-127">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Imaging.Metafile>  
 <span data-ttu-id="13daa-128">Descreve essa classe e tem links para todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="13daa-128">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Bitmap>  
 <span data-ttu-id="13daa-129">Descreve essa classe e tem links para todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="13daa-129">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="13daa-130">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="13daa-130">Related Sections</span></span>  
 [<span data-ttu-id="13daa-131">Imagens, bitmaps e metarquivos</span><span class="sxs-lookup"><span data-stu-id="13daa-131">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 <span data-ttu-id="13daa-132">Contém links para tópicos que discutem diferentes tipos de bitmaps e como manipulá-los em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="13daa-132">Contains links to topics that discuss different types of bitmaps and manipulating them in your applications.</span></span>
