---
title: Usando codecs de imagem no GDI+ gerenciado
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- image encoders [Windows Forms], using
- image decoders [Windows Forms], using
ms.assetid: 0e838ea1-4e7e-4334-b882-ab25df607b8b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 084e8ff21e308cc20b633719dd31809b96b3c79a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="using-image-encoders-and-decoders-in-managed-gdi"></a><span data-ttu-id="19c29-102">Usando codecs de imagem no GDI+ gerenciado</span><span class="sxs-lookup"><span data-stu-id="19c29-102">Using Image Encoders and Decoders in Managed GDI+</span></span>
<span data-ttu-id="19c29-103">O <xref:System.Drawing> namespace fornece o <xref:System.Drawing.Image> e <xref:System.Drawing.Bitmap> classes para armazenar e manipular imagens.</span><span class="sxs-lookup"><span data-stu-id="19c29-103">The <xref:System.Drawing> namespace provides the <xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> classes for storing and manipulating images.</span></span> <span data-ttu-id="19c29-104">Ao usar codificadores de imagem no [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], você pode gravar imagens da memória no disco.</span><span class="sxs-lookup"><span data-stu-id="19c29-104">By using image encoders in [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you can write images from memory to disk.</span></span> <span data-ttu-id="19c29-105">Ao usar codificadores de imagem no [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], você pode carregar imagens do disco na memória.</span><span class="sxs-lookup"><span data-stu-id="19c29-105">By using image decoders in [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you can load images from disk into memory.</span></span> <span data-ttu-id="19c29-106">Um codificador converte os dados em um <xref:System.Drawing.Image> ou <xref:System.Drawing.Bitmap> objeto em um formato de arquivo de disco designado.</span><span class="sxs-lookup"><span data-stu-id="19c29-106">An encoder translates the data in an <xref:System.Drawing.Image> or <xref:System.Drawing.Bitmap> object into a designated disk file format.</span></span> <span data-ttu-id="19c29-107">Um decodificador converte os dados em um arquivo de disco para o formato exigido pelo <xref:System.Drawing.Image> e <xref:System.Drawing.Bitmap> objetos.</span><span class="sxs-lookup"><span data-stu-id="19c29-107">A decoder translates the data in a disk file to the format required by the <xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 <span data-ttu-id="19c29-108">O [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] tem codecs internos que oferecem suporte aos seguintes tipos de arquivo:</span><span class="sxs-lookup"><span data-stu-id="19c29-108">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] has built-in encoders and decoders that support the following file types:</span></span>  
  
-   <span data-ttu-id="19c29-109">BMP</span><span class="sxs-lookup"><span data-stu-id="19c29-109">BMP</span></span>  
  
-   <span data-ttu-id="19c29-110">GIF</span><span class="sxs-lookup"><span data-stu-id="19c29-110">GIF</span></span>  
  
-   <span data-ttu-id="19c29-111">JPEG</span><span class="sxs-lookup"><span data-stu-id="19c29-111">JPEG</span></span>  
  
-   <span data-ttu-id="19c29-112">PNG</span><span class="sxs-lookup"><span data-stu-id="19c29-112">PNG</span></span>  
  
-   <span data-ttu-id="19c29-113">TIFF</span><span class="sxs-lookup"><span data-stu-id="19c29-113">TIFF</span></span>  
  
 <span data-ttu-id="19c29-114">O [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] também tem decodificadores internos que oferecem suporte aos seguintes tipos de arquivo:</span><span class="sxs-lookup"><span data-stu-id="19c29-114">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] also has built-in decoders that support the following file types:</span></span>  
  
-   <span data-ttu-id="19c29-115">WMF</span><span class="sxs-lookup"><span data-stu-id="19c29-115">WMF</span></span>  
  
-   <span data-ttu-id="19c29-116">EMF</span><span class="sxs-lookup"><span data-stu-id="19c29-116">EMF</span></span>  
  
-   <span data-ttu-id="19c29-117">ICON</span><span class="sxs-lookup"><span data-stu-id="19c29-117">ICON</span></span>  
  
 <span data-ttu-id="19c29-118">Os tópicos a seguir abordam os codificadores e decodificadores mais detalhadamente:</span><span class="sxs-lookup"><span data-stu-id="19c29-118">The following topics discuss encoders and decoders in more detail:</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="19c29-119">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="19c29-119">In This Section</span></span>  
 [<span data-ttu-id="19c29-120">Como Listar os Codificadores Instalados</span><span class="sxs-lookup"><span data-stu-id="19c29-120">How to: List Installed Encoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 <span data-ttu-id="19c29-121">Descreve como listar os codificadores disponíveis em um computador.</span><span class="sxs-lookup"><span data-stu-id="19c29-121">Describes how to list the encoders available on a computer.</span></span>  
  
 [<span data-ttu-id="19c29-122">Como Listar os Decodificadores Instalados</span><span class="sxs-lookup"><span data-stu-id="19c29-122">How to: List Installed Decoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-decoders.md)  
 <span data-ttu-id="19c29-123">Descreve como listar os decodificadores disponíveis em um computador.</span><span class="sxs-lookup"><span data-stu-id="19c29-123">Describes how to list the decoders available on a computer.</span></span>  
  
 [<span data-ttu-id="19c29-124">Como Determinar os Parâmetros com Suporte em um Codificador</span><span class="sxs-lookup"><span data-stu-id="19c29-124">How to: Determine the Parameters Supported by an Encoder</span></span>](../../../../docs/framework/winforms/advanced/how-to-determine-the-parameters-supported-by-an-encoder.md)  
 <span data-ttu-id="19c29-125">Descreve como listar o <xref:System.Drawing.Imaging.EncoderParameters> compatíveis com um codificador.</span><span class="sxs-lookup"><span data-stu-id="19c29-125">Describes how to list the <xref:System.Drawing.Imaging.EncoderParameters> supported by an encoder.</span></span>  
  
 [<span data-ttu-id="19c29-126">Como Converter uma Imagem BMP em uma Imagem PNG</span><span class="sxs-lookup"><span data-stu-id="19c29-126">How to: Convert a BMP image to a PNG image</span></span>](../../../../docs/framework/winforms/advanced/how-to-convert-a-bmp-image-to-a-png-image.md)  
 <span data-ttu-id="19c29-127">Descreve como salvar uma imagem em um formato de imagem diferente.</span><span class="sxs-lookup"><span data-stu-id="19c29-127">Describes how to save a image in a different image format.</span></span>  
  
 [<span data-ttu-id="19c29-128">Como Definir o Nível de Compactação de JPEG</span><span class="sxs-lookup"><span data-stu-id="19c29-128">How to: Set JPEG Compression Level</span></span>](../../../../docs/framework/winforms/advanced/how-to-set-jpeg-compression-level.md)  
 <span data-ttu-id="19c29-129">Descreve como alterar o nível de qualidade de uma imagem.</span><span class="sxs-lookup"><span data-stu-id="19c29-129">Describes how to change the quality level of an image.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="19c29-130">Referência</span><span class="sxs-lookup"><span data-stu-id="19c29-130">Reference</span></span>  
 <xref:System.Drawing.Image>  
  
 <xref:System.Drawing.Bitmap>  
  
 <xref:System.Drawing.Imaging.ImageCodecInfo>  
  
 <xref:System.Drawing.Imaging.EncoderParameter>  
  
 <xref:System.Drawing.Imaging.Encoder>  
  
## <a name="related-sections"></a><span data-ttu-id="19c29-131">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="19c29-131">Related Sections</span></span>  
 [<span data-ttu-id="19c29-132">Sobre o Código Gerenciado no GDI+</span><span class="sxs-lookup"><span data-stu-id="19c29-132">About GDI+ Managed Code</span></span>](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
  
 [<span data-ttu-id="19c29-133">Imagens, bitmaps e metarquivos</span><span class="sxs-lookup"><span data-stu-id="19c29-133">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
