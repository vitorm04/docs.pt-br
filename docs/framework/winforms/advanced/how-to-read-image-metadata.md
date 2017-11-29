---
title: Como ler metadados de imagens
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
- metadata [Windows Forms], property item
- metadata [Windows Forms], reading image
ms.assetid: 72ec0b31-0be7-444a-9575-1dbcb864e0be
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9df2866251e08b8989f8550d045b587c9de8d2cb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-image-metadata"></a><span data-ttu-id="4eb91-102">Como ler metadados de imagens</span><span class="sxs-lookup"><span data-stu-id="4eb91-102">How to: Read Image Metadata</span></span>
<span data-ttu-id="4eb91-103">Alguns arquivos de imagem contêm metadados que você pode ler para determinar os recursos da imagem.</span><span class="sxs-lookup"><span data-stu-id="4eb91-103">Some image files contain metadata that you can read to determine features of the image.</span></span> <span data-ttu-id="4eb91-104">Por exemplo, uma fotografia digital pode conter metadados que você pode ler para determinar a marca e modelo da câmera usada para capturar a imagem.</span><span class="sxs-lookup"><span data-stu-id="4eb91-104">For example, a digital photograph might contain metadata that you can read to determine the make and model of the camera used to capture the image.</span></span> <span data-ttu-id="4eb91-105">Com o [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], você pode ler os metadados existentes e escrever novos metadados para os arquivos de imagem.</span><span class="sxs-lookup"><span data-stu-id="4eb91-105">With [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you can read existing metadata, and you can also write new metadata to image files.</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="4eb91-106">armazena um item individual de metadados em um <xref:System.Drawing.Imaging.PropertyItem> objeto.</span><span class="sxs-lookup"><span data-stu-id="4eb91-106"> stores an individual piece of metadata in a <xref:System.Drawing.Imaging.PropertyItem> object.</span></span> <span data-ttu-id="4eb91-107">Você pode ler o <xref:System.Drawing.Image.PropertyItems%2A> propriedade de um <xref:System.Drawing.Image> objeto para recuperar todos os metadados de um arquivo.</span><span class="sxs-lookup"><span data-stu-id="4eb91-107">You can read the <xref:System.Drawing.Image.PropertyItems%2A> property of an <xref:System.Drawing.Image> object to retrieve all the metadata from a file.</span></span> <span data-ttu-id="4eb91-108">O <xref:System.Drawing.Image.PropertyItems%2A> propriedade retorna uma matriz de <xref:System.Drawing.Imaging.PropertyItem> objetos.</span><span class="sxs-lookup"><span data-stu-id="4eb91-108">The <xref:System.Drawing.Image.PropertyItems%2A> property returns an array of <xref:System.Drawing.Imaging.PropertyItem> objects.</span></span>  
  
 <span data-ttu-id="4eb91-109">Um <xref:System.Drawing.Imaging.PropertyItem> objeto tem as seguintes quatro propriedades: `Id`, `Value`, `Len`, e `Type`.</span><span class="sxs-lookup"><span data-stu-id="4eb91-109">A <xref:System.Drawing.Imaging.PropertyItem> object has the following four properties: `Id`, `Value`, `Len`, and `Type`.</span></span>  
  
## <a name="id"></a><span data-ttu-id="4eb91-110">Id</span><span class="sxs-lookup"><span data-stu-id="4eb91-110">Id</span></span>  
 <span data-ttu-id="4eb91-111">Uma marca que identifica o item de metadados.</span><span class="sxs-lookup"><span data-stu-id="4eb91-111">A tag that identifies the metadata item.</span></span> <span data-ttu-id="4eb91-112">Alguns valores que podem ser atribuídos a <xref:System.Drawing.Imaging.PropertyItem.Id%2A> são mostrados na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="4eb91-112">Some values that can be assigned to <xref:System.Drawing.Imaging.PropertyItem.Id%2A> are shown in the following table.</span></span>  
  
|<span data-ttu-id="4eb91-113">Valor hexadecimal</span><span class="sxs-lookup"><span data-stu-id="4eb91-113">Hexadecimal value</span></span>|<span data-ttu-id="4eb91-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="4eb91-114">Description</span></span>|  
|-----------------------|-----------------|  
|<span data-ttu-id="4eb91-115">0x0320</span><span class="sxs-lookup"><span data-stu-id="4eb91-115">0x0320</span></span><br /><br /> <span data-ttu-id="4eb91-116">0x010F</span><span class="sxs-lookup"><span data-stu-id="4eb91-116">0x010F</span></span><br /><br /> <span data-ttu-id="4eb91-117">0x0110</span><span class="sxs-lookup"><span data-stu-id="4eb91-117">0x0110</span></span><br /><br /> <span data-ttu-id="4eb91-118">0x9003</span><span class="sxs-lookup"><span data-stu-id="4eb91-118">0x9003</span></span><br /><br /> <span data-ttu-id="4eb91-119">0x829A</span><span class="sxs-lookup"><span data-stu-id="4eb91-119">0x829A</span></span><br /><br /> <span data-ttu-id="4eb91-120">0x5090</span><span class="sxs-lookup"><span data-stu-id="4eb91-120">0x5090</span></span><br /><br /> <span data-ttu-id="4eb91-121">0x5091</span><span class="sxs-lookup"><span data-stu-id="4eb91-121">0x5091</span></span>|<span data-ttu-id="4eb91-122">Título da imagem</span><span class="sxs-lookup"><span data-stu-id="4eb91-122">Image title</span></span><br /><br /> <span data-ttu-id="4eb91-123">Fabricante do equipamento</span><span class="sxs-lookup"><span data-stu-id="4eb91-123">Equipment manufacturer</span></span><br /><br /> <span data-ttu-id="4eb91-124">Modelo do equipamento</span><span class="sxs-lookup"><span data-stu-id="4eb91-124">Equipment model</span></span><br /><br /> <span data-ttu-id="4eb91-125">ExifDTOriginal</span><span class="sxs-lookup"><span data-stu-id="4eb91-125">ExifDTOriginal</span></span><br /><br /> <span data-ttu-id="4eb91-126">Tempo de exposição de Exif</span><span class="sxs-lookup"><span data-stu-id="4eb91-126">Exif exposure time</span></span><br /><br /> <span data-ttu-id="4eb91-127">Tabela de luminância</span><span class="sxs-lookup"><span data-stu-id="4eb91-127">Luminance table</span></span><br /><br /> <span data-ttu-id="4eb91-128">Tabela de crominância</span><span class="sxs-lookup"><span data-stu-id="4eb91-128">Chrominance table</span></span>|  
  
## <a name="value"></a><span data-ttu-id="4eb91-129">Valor</span><span class="sxs-lookup"><span data-stu-id="4eb91-129">Value</span></span>  
 <span data-ttu-id="4eb91-130">Uma matriz de valores.</span><span class="sxs-lookup"><span data-stu-id="4eb91-130">An array of values.</span></span> <span data-ttu-id="4eb91-131">O formato dos valores é determinado pelo <xref:System.Drawing.Imaging.PropertyItem.Type%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="4eb91-131">The format of the values is determined by the <xref:System.Drawing.Imaging.PropertyItem.Type%2A> property.</span></span>  
  
## <a name="len"></a><span data-ttu-id="4eb91-132">Len</span><span class="sxs-lookup"><span data-stu-id="4eb91-132">Len</span></span>  
 <span data-ttu-id="4eb91-133">O comprimento (em bytes) da matriz de valores apontada pelo <xref:System.Drawing.Imaging.PropertyItem.Value%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="4eb91-133">The length (in bytes) of the array of values pointed to by the <xref:System.Drawing.Imaging.PropertyItem.Value%2A> property.</span></span>  
  
## <a name="type"></a><span data-ttu-id="4eb91-134">Tipo</span><span class="sxs-lookup"><span data-stu-id="4eb91-134">Type</span></span>  
 <span data-ttu-id="4eb91-135">O tipo de dados dos valores na matriz aponta para a propriedade `Value`.</span><span class="sxs-lookup"><span data-stu-id="4eb91-135">The data type of the values in the array pointed to by the `Value` property.</span></span> <span data-ttu-id="4eb91-136">Os formatos indicados pelos valores de propriedade `Type` são mostrados na tabela a seguir</span><span class="sxs-lookup"><span data-stu-id="4eb91-136">The formats indicated by the `Type` property values are shown in the following table</span></span>  
  
|<span data-ttu-id="4eb91-137">Valor numérico</span><span class="sxs-lookup"><span data-stu-id="4eb91-137">Numeric value</span></span>|<span data-ttu-id="4eb91-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="4eb91-138">Description</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="4eb91-139">1</span><span class="sxs-lookup"><span data-stu-id="4eb91-139">1</span></span>|<span data-ttu-id="4eb91-140">Um `Byte`</span><span class="sxs-lookup"><span data-stu-id="4eb91-140">A `Byte`</span></span>|  
|<span data-ttu-id="4eb91-141">2</span><span class="sxs-lookup"><span data-stu-id="4eb91-141">2</span></span>|<span data-ttu-id="4eb91-142">Uma matriz de objetos `Byte` codificados como ASCII</span><span class="sxs-lookup"><span data-stu-id="4eb91-142">An array of `Byte` objects encoded as ASCII</span></span>|  
|<span data-ttu-id="4eb91-143">3</span><span class="sxs-lookup"><span data-stu-id="4eb91-143">3</span></span>|<span data-ttu-id="4eb91-144">Um inteiro de 16 bits</span><span class="sxs-lookup"><span data-stu-id="4eb91-144">A 16-bit integer</span></span>|  
|<span data-ttu-id="4eb91-145">4</span><span class="sxs-lookup"><span data-stu-id="4eb91-145">4</span></span>|<span data-ttu-id="4eb91-146">Um inteiro de 32 bits</span><span class="sxs-lookup"><span data-stu-id="4eb91-146">A 32-bit integer</span></span>|  
|<span data-ttu-id="4eb91-147">5</span><span class="sxs-lookup"><span data-stu-id="4eb91-147">5</span></span>|<span data-ttu-id="4eb91-148">Uma matriz de dois objetos `Byte` que representam um número racional</span><span class="sxs-lookup"><span data-stu-id="4eb91-148">An array of two `Byte` objects that represent a rational number</span></span>|  
|<span data-ttu-id="4eb91-149">6</span><span class="sxs-lookup"><span data-stu-id="4eb91-149">6</span></span>|<span data-ttu-id="4eb91-150">Não usado</span><span class="sxs-lookup"><span data-stu-id="4eb91-150">Not used</span></span>|  
|<span data-ttu-id="4eb91-151">7</span><span class="sxs-lookup"><span data-stu-id="4eb91-151">7</span></span>|<span data-ttu-id="4eb91-152">Indefinido</span><span class="sxs-lookup"><span data-stu-id="4eb91-152">Undefined</span></span>|  
|<span data-ttu-id="4eb91-153">8</span><span class="sxs-lookup"><span data-stu-id="4eb91-153">8</span></span>|<span data-ttu-id="4eb91-154">Não usado</span><span class="sxs-lookup"><span data-stu-id="4eb91-154">Not used</span></span>|  
|<span data-ttu-id="4eb91-155">9</span><span class="sxs-lookup"><span data-stu-id="4eb91-155">9</span></span>|`SLong`|  
|<span data-ttu-id="4eb91-156">10</span><span class="sxs-lookup"><span data-stu-id="4eb91-156">10</span></span>|`SRational`|  
  
## <a name="example"></a><span data-ttu-id="4eb91-157">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4eb91-157">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="4eb91-158">Descrição</span><span class="sxs-lookup"><span data-stu-id="4eb91-158">Description</span></span>  
 <span data-ttu-id="4eb91-159">O exemplo de código a seguir lê e exibe as sete partes dos metadados no arquivo `FakePhoto.jpg`.</span><span class="sxs-lookup"><span data-stu-id="4eb91-159">The following code example reads and displays the seven pieces of metadata in the file `FakePhoto.jpg`.</span></span> <span data-ttu-id="4eb91-160">O segundo item de propriedade (índice 1) na lista tem <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (fabricante de equipamento) e <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (matriz de bytes codificados em ASCII).</span><span class="sxs-lookup"><span data-stu-id="4eb91-160">The second (index 1) property item in the list has <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (equipment manufacturer) and <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (ASCII-encoded byte array).</span></span> <span data-ttu-id="4eb91-161">O exemplo de código exibe o valor desse item de propriedade.</span><span class="sxs-lookup"><span data-stu-id="4eb91-161">The code example displays the value of that property item.</span></span>  
  
 <span data-ttu-id="4eb91-162">O código produz uma saída semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="4eb91-162">The code produces output similar to the following:</span></span>  
  
 `Property Item 0`  
  
 `id: 0x320`  
  
 `type: 2`  
  
 `length: 16 bytes`  
  
 `Property Item 1`  
  
 `id: 0x10f`  
  
 `type: 2`  
  
 `length: 17 bytes`  
  
 `Property Item 2`  
  
 `id: 0x110`  
  
 `type: 2`  
  
 `length: 7 bytes`  
  
 `Property Item 3`  
  
 `id: 0x9003`  
  
 `type: 2`  
  
 `length: 20 bytes`  
  
 `Property Item 4`  
  
 `id: 0x829a`  
  
 `type: 5`  
  
 `length: 8 bytes`  
  
 `Property Item 5`  
  
 `id: 0x5090`  
  
 `type: 3`  
  
 `length: 128 bytes`  
  
 `Property Item 6`  
  
 `id: 0x5091`  
  
 `type: 3`  
  
 `length: 128 bytes`  
  
 `The equipment make is Northwind Camera.`  
  
### <a name="code"></a><span data-ttu-id="4eb91-163">Código</span><span class="sxs-lookup"><span data-stu-id="4eb91-163">Code</span></span>  
 [!code-csharp[System.Drawing.WorkingWithImages#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.WorkingWithImages#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4eb91-164">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="4eb91-164">Compiling the Code</span></span>  
 <span data-ttu-id="4eb91-165">O exemplo anterior é projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="4eb91-165">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="4eb91-166">Controlar o formulário <xref:System.Windows.Forms.Control.Paint> eventos e cole esse código no manipulador de eventos de pintura.</span><span class="sxs-lookup"><span data-stu-id="4eb91-166">Handle the form's <xref:System.Windows.Forms.Control.Paint> event and paste this code into the paint event handler.</span></span> <span data-ttu-id="4eb91-167">Você deve substituir `FakePhoto.jpg` por um nome e caminho de imagem válidos no seu sistema e importar o namespace `System.Drawing.Imaging`.</span><span class="sxs-lookup"><span data-stu-id="4eb91-167">You must replace `FakePhoto.jpg` with an image name and path valid on your system and import the `System.Drawing.Imaging` namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4eb91-168">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4eb91-168">See Also</span></span>  
 [<span data-ttu-id="4eb91-169">Imagens, bitmaps e metarquivos</span><span class="sxs-lookup"><span data-stu-id="4eb91-169">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="4eb91-170">Trabalhando com Imagens, Bitmaps, Ícones e Metarquivos</span><span class="sxs-lookup"><span data-stu-id="4eb91-170">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
