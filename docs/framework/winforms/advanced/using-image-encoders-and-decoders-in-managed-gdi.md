---
title: Usando codecs de imagem no GDI+ gerenciado
ms.date: 03/30/2017
helpviewer_keywords:
- image encoders [Windows Forms], using
- image decoders [Windows Forms], using
ms.assetid: 0e838ea1-4e7e-4334-b882-ab25df607b8b
ms.openlocfilehash: b2e51587209cb4df41ea1fd18ce5c2088ee07a2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524495"
---
# <a name="using-image-encoders-and-decoders-in-managed-gdi"></a><span data-ttu-id="61185-102">Usando codecs de imagem no GDI+ gerenciado</span><span class="sxs-lookup"><span data-stu-id="61185-102">Using Image Encoders and Decoders in Managed GDI+</span></span>
<span data-ttu-id="61185-103">O <xref:System.Drawing> namespace fornece o <xref:System.Drawing.Image> e <xref:System.Drawing.Bitmap> classes para armazenar e manipular imagens.</span><span class="sxs-lookup"><span data-stu-id="61185-103">The <xref:System.Drawing> namespace provides the <xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> classes for storing and manipulating images.</span></span> <span data-ttu-id="61185-104">Ao usar codificadores de imagem no [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], você pode gravar imagens da memória no disco.</span><span class="sxs-lookup"><span data-stu-id="61185-104">By using image encoders in [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you can write images from memory to disk.</span></span> <span data-ttu-id="61185-105">Ao usar codificadores de imagem no [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], você pode carregar imagens do disco na memória.</span><span class="sxs-lookup"><span data-stu-id="61185-105">By using image decoders in [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you can load images from disk into memory.</span></span> <span data-ttu-id="61185-106">Um codificador converte os dados em um <xref:System.Drawing.Image> ou <xref:System.Drawing.Bitmap> objeto em um formato de arquivo de disco designado.</span><span class="sxs-lookup"><span data-stu-id="61185-106">An encoder translates the data in an <xref:System.Drawing.Image> or <xref:System.Drawing.Bitmap> object into a designated disk file format.</span></span> <span data-ttu-id="61185-107">Um decodificador converte os dados em um arquivo de disco para o formato exigido pelo <xref:System.Drawing.Image> e <xref:System.Drawing.Bitmap> objetos.</span><span class="sxs-lookup"><span data-stu-id="61185-107">A decoder translates the data in a disk file to the format required by the <xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 <span data-ttu-id="61185-108">O [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] tem codecs internos que oferecem suporte aos seguintes tipos de arquivo:</span><span class="sxs-lookup"><span data-stu-id="61185-108">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] has built-in encoders and decoders that support the following file types:</span></span>  
  
-   <span data-ttu-id="61185-109">BMP</span><span class="sxs-lookup"><span data-stu-id="61185-109">BMP</span></span>  
  
-   <span data-ttu-id="61185-110">GIF</span><span class="sxs-lookup"><span data-stu-id="61185-110">GIF</span></span>  
  
-   <span data-ttu-id="61185-111">JPEG</span><span class="sxs-lookup"><span data-stu-id="61185-111">JPEG</span></span>  
  
-   <span data-ttu-id="61185-112">PNG</span><span class="sxs-lookup"><span data-stu-id="61185-112">PNG</span></span>  
  
-   <span data-ttu-id="61185-113">TIFF</span><span class="sxs-lookup"><span data-stu-id="61185-113">TIFF</span></span>  
  
 <span data-ttu-id="61185-114">O [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] também tem decodificadores internos que oferecem suporte aos seguintes tipos de arquivo:</span><span class="sxs-lookup"><span data-stu-id="61185-114">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] also has built-in decoders that support the following file types:</span></span>  
  
-   <span data-ttu-id="61185-115">WMF</span><span class="sxs-lookup"><span data-stu-id="61185-115">WMF</span></span>  
  
-   <span data-ttu-id="61185-116">EMF</span><span class="sxs-lookup"><span data-stu-id="61185-116">EMF</span></span>  
  
-   <span data-ttu-id="61185-117">ICON</span><span class="sxs-lookup"><span data-stu-id="61185-117">ICON</span></span>  
  
 <span data-ttu-id="61185-118">Os tópicos a seguir abordam os codificadores e decodificadores mais detalhadamente:</span><span class="sxs-lookup"><span data-stu-id="61185-118">The following topics discuss encoders and decoders in more detail:</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="61185-119">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="61185-119">In This Section</span></span>  
 [<span data-ttu-id="61185-120">Como Listar os Codificadores Instalados</span><span class="sxs-lookup"><span data-stu-id="61185-120">How to: List Installed Encoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 <span data-ttu-id="61185-121">Descreve como listar os codificadores disponíveis em um computador.</span><span class="sxs-lookup"><span data-stu-id="61185-121">Describes how to list the encoders available on a computer.</span></span>  
  
 [<span data-ttu-id="61185-122">Como Listar os Decodificadores Instalados</span><span class="sxs-lookup"><span data-stu-id="61185-122">How to: List Installed Decoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-decoders.md)  
 <span data-ttu-id="61185-123">Descreve como listar os decodificadores disponíveis em um computador.</span><span class="sxs-lookup"><span data-stu-id="61185-123">Describes how to list the decoders available on a computer.</span></span>  
  
 [<span data-ttu-id="61185-124">Como Determinar os Parâmetros com Suporte em um Codificador</span><span class="sxs-lookup"><span data-stu-id="61185-124">How to: Determine the Parameters Supported by an Encoder</span></span>](../../../../docs/framework/winforms/advanced/how-to-determine-the-parameters-supported-by-an-encoder.md)  
 <span data-ttu-id="61185-125">Descreve como listar o <xref:System.Drawing.Imaging.EncoderParameters> compatíveis com um codificador.</span><span class="sxs-lookup"><span data-stu-id="61185-125">Describes how to list the <xref:System.Drawing.Imaging.EncoderParameters> supported by an encoder.</span></span>  
  
 [<span data-ttu-id="61185-126">Como Converter uma Imagem BMP em uma Imagem PNG</span><span class="sxs-lookup"><span data-stu-id="61185-126">How to: Convert a BMP image to a PNG image</span></span>](../../../../docs/framework/winforms/advanced/how-to-convert-a-bmp-image-to-a-png-image.md)  
 <span data-ttu-id="61185-127">Descreve como salvar uma imagem em um formato de imagem diferente.</span><span class="sxs-lookup"><span data-stu-id="61185-127">Describes how to save a image in a different image format.</span></span>  
  
 [<span data-ttu-id="61185-128">Como Definir o Nível de Compactação de JPEG</span><span class="sxs-lookup"><span data-stu-id="61185-128">How to: Set JPEG Compression Level</span></span>](../../../../docs/framework/winforms/advanced/how-to-set-jpeg-compression-level.md)  
 <span data-ttu-id="61185-129">Descreve como alterar o nível de qualidade de uma imagem.</span><span class="sxs-lookup"><span data-stu-id="61185-129">Describes how to change the quality level of an image.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="61185-130">Referência</span><span class="sxs-lookup"><span data-stu-id="61185-130">Reference</span></span>  
 <xref:System.Drawing.Image>  
  
 <xref:System.Drawing.Bitmap>  
  
 <xref:System.Drawing.Imaging.ImageCodecInfo>  
  
 <xref:System.Drawing.Imaging.EncoderParameter>  
  
 <xref:System.Drawing.Imaging.Encoder>  
  
## <a name="related-sections"></a><span data-ttu-id="61185-131">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="61185-131">Related Sections</span></span>  
 [<span data-ttu-id="61185-132">Sobre o Código Gerenciado no GDI+</span><span class="sxs-lookup"><span data-stu-id="61185-132">About GDI+ Managed Code</span></span>](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
  
 [<span data-ttu-id="61185-133">Imagens, bitmaps e metarquivos</span><span class="sxs-lookup"><span data-stu-id="61185-133">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
