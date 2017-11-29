---
title: Imagens, bitmaps e metarquivos
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- metafiles [Windows Forms], about metafiles
- bitmaps [Windows Forms], about bitmaps
- images [Windows Forms], about images
- Windows Forms, images
ms.assetid: 7152b45b-a55c-49bc-8c78-ae002a844f71
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3f48027e413f9573158cfa2c3748fc93408b3f83
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="images-bitmaps-and-metafiles"></a><span data-ttu-id="1bca7-102">Imagens, bitmaps e metarquivos</span><span class="sxs-lookup"><span data-stu-id="1bca7-102">Images, Bitmaps, and Metafiles</span></span>
<span data-ttu-id="1bca7-103">A classe base `Image` é abstrata e fornece métodos para trabalhar com imagens de varredura (bitmaps) e imagens vetoriais (metarquivos).</span><span class="sxs-lookup"><span data-stu-id="1bca7-103">The `Image` class is an abstract base class that provides methods for working with raster images (bitmaps) and vector images (metafiles).</span></span> <span data-ttu-id="1bca7-104">O `Bitmap` classe e o <xref:System.Drawing.Imaging.Metafile> classe ambos herdam o `Image` classe.</span><span class="sxs-lookup"><span data-stu-id="1bca7-104">The `Bitmap` class and the <xref:System.Drawing.Imaging.Metafile> class both inherit from the `Image` class.</span></span> <span data-ttu-id="1bca7-105">A classe `Bitmap` expande os recursos da classe `Image` fornecendo métodos adicionais para carregar, salvar e manipular imagens de varredura.</span><span class="sxs-lookup"><span data-stu-id="1bca7-105">The `Bitmap` class expands on the capabilities of the `Image` class by providing additional methods for loading, saving, and manipulating raster images.</span></span> <span data-ttu-id="1bca7-106">O <xref:System.Drawing.Imaging.Metafile> classe expande os recursos da `Image` classe fornecendo métodos adicionais para registrar e examinar imagens de vetor.</span><span class="sxs-lookup"><span data-stu-id="1bca7-106">The <xref:System.Drawing.Imaging.Metafile> class expands on the capabilities of the `Image` class by providing additional methods for recording and examining vector images.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1bca7-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="1bca7-107">In This Section</span></span>  
 [<span data-ttu-id="1bca7-108">Tipos de Bitmaps</span><span class="sxs-lookup"><span data-stu-id="1bca7-108">Types of Bitmaps</span></span>](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)  
 <span data-ttu-id="1bca7-109">Discute os diversos formatos de imagem.</span><span class="sxs-lookup"><span data-stu-id="1bca7-109">Discusses the various image formats.</span></span>  
  
 [<span data-ttu-id="1bca7-110">Metarquivos no GDI+</span><span class="sxs-lookup"><span data-stu-id="1bca7-110">Metafiles in GDI+</span></span>](../../../../docs/framework/winforms/advanced/metafiles-in-gdi.md)  
 <span data-ttu-id="1bca7-111">Discute o suporte a [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] para metarquivos.</span><span class="sxs-lookup"><span data-stu-id="1bca7-111">Discusses [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] support for metafiles.</span></span>  
  
 [<span data-ttu-id="1bca7-112">Desenhando, Posicionando e Clonando Imagens no GDI+</span><span class="sxs-lookup"><span data-stu-id="1bca7-112">Drawing, Positioning, and Cloning Images in GDI+</span></span>](../../../../docs/framework/winforms/advanced/drawing-positioning-and-cloning-images-in-gdi.md)  
 <span data-ttu-id="1bca7-113">Discute os métodos para desenhar imagens de varredura e vetoriais com código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="1bca7-113">Discusses methods for drawing vector and raster images with managed code.</span></span>  
  
 [<span data-ttu-id="1bca7-114">Cortar e Dimensionar Imagens no GDI+</span><span class="sxs-lookup"><span data-stu-id="1bca7-114">Cropping and Scaling Images in GDI+</span></span>](../../../../docs/framework/winforms/advanced/cropping-and-scaling-images-in-gdi.md)  
 <span data-ttu-id="1bca7-115">Discute os métodos para recortar e dimensionar imagens de varredura e vetoriais com código gerenciado</span><span class="sxs-lookup"><span data-stu-id="1bca7-115">Discusses methods for cropping and scaling vector and raster images with managed code</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1bca7-116">Referência</span><span class="sxs-lookup"><span data-stu-id="1bca7-116">Reference</span></span>  
 <xref:System.Drawing.Image>  
 <span data-ttu-id="1bca7-117">Descreve essa classe e tem links para todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="1bca7-117">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Bitmap>  
 <span data-ttu-id="1bca7-118">Descreve essa classe e tem links para todos os seus membros</span><span class="sxs-lookup"><span data-stu-id="1bca7-118">Describes this class and has links to all of its members</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1bca7-119">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="1bca7-119">Related Sections</span></span>  
 [<span data-ttu-id="1bca7-120">Trabalhando com Imagens, Bitmaps, Ícones e Metarquivos</span><span class="sxs-lookup"><span data-stu-id="1bca7-120">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)  
 <span data-ttu-id="1bca7-121">Contém links para tópicos que demonstram como usar imagens no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1bca7-121">Contains links to topics that demonstrate how to use images in your application.</span></span>
