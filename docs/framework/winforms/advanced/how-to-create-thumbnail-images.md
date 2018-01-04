---
title: Como criar imagens em miniatura
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
- thumbnail images [Windows Forms], creating
- images [Windows Forms], creating thumbnails
ms.assetid: e956242a-1e5b-4217-a3cf-5f3fb45d00ba
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b8eeb856fabd895e171c0ad8739ae6a63b5c7065
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-thumbnail-images"></a><span data-ttu-id="5f5fb-102">Como criar imagens em miniatura</span><span class="sxs-lookup"><span data-stu-id="5f5fb-102">How to: Create Thumbnail Images</span></span>
<span data-ttu-id="5f5fb-103">Uma imagem em miniatura é uma versão pequena de uma imagem.</span><span class="sxs-lookup"><span data-stu-id="5f5fb-103">A thumbnail image is a small version of an image.</span></span> <span data-ttu-id="5f5fb-104">Você pode criar uma imagem em miniatura chamando o <xref:System.Drawing.Image.GetThumbnailImage%2A> método de um <xref:System.Drawing.Image> objeto.</span><span class="sxs-lookup"><span data-stu-id="5f5fb-104">You can create a thumbnail image by calling the <xref:System.Drawing.Image.GetThumbnailImage%2A> method of an <xref:System.Drawing.Image> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f5fb-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5f5fb-105">Example</span></span>  
 <span data-ttu-id="5f5fb-106">O exemplo a seguir constrói um <xref:System.Drawing.Image> objeto a partir de um arquivo JPG.</span><span class="sxs-lookup"><span data-stu-id="5f5fb-106">The following example constructs an <xref:System.Drawing.Image> object from a JPG file.</span></span> <span data-ttu-id="5f5fb-107">A imagem original tem uma largura de 640 pixels e uma altura de 479 pixels.</span><span class="sxs-lookup"><span data-stu-id="5f5fb-107">The original image has a width of 640 pixels and a height of 479 pixels.</span></span> <span data-ttu-id="5f5fb-108">O código cria uma imagem em miniatura que tem uma largura de 100 pixels e uma altura de 100 pixels.</span><span class="sxs-lookup"><span data-stu-id="5f5fb-108">The code creates a thumbnail image that has a width of 100 pixels and a height of 100 pixels.</span></span>  
  
 <span data-ttu-id="5f5fb-109">A ilustração a seguir mostra a imagem em miniatura.</span><span class="sxs-lookup"><span data-stu-id="5f5fb-109">The following illustration shows the thumbnail image.</span></span>  
  
 <span data-ttu-id="5f5fb-110">![Thumbnail Image](../../../../docs/framework/winforms/advanced/media/thumbnail1.png "Thumbnail1")</span><span class="sxs-lookup"><span data-stu-id="5f5fb-110">![Thumbnail Image](../../../../docs/framework/winforms/advanced/media/thumbnail1.png "Thumbnail1")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5f5fb-111">Neste exemplo, um método de retorno de chamada é declarado, mas nunca usado.</span><span class="sxs-lookup"><span data-stu-id="5f5fb-111">In this example, a callback method is declared, but never used.</span></span> <span data-ttu-id="5f5fb-112">Isso dá suporte a todas as versões do GDI+.</span><span class="sxs-lookup"><span data-stu-id="5f5fb-112">This supports all versions of GDI+.</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.WorkingWithImages#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5f5fb-113">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="5f5fb-113">Compiling the Code</span></span>  
 <span data-ttu-id="5f5fb-114">O exemplo anterior é projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="5f5fb-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="5f5fb-115">Para executar o exemplo, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="5f5fb-115">To run the example, follow these steps:</span></span>  
  
1.  <span data-ttu-id="5f5fb-116">Criar um novo aplicativo Windows Form.</span><span class="sxs-lookup"><span data-stu-id="5f5fb-116">Create a new Windows Forms application.</span></span>  
  
2.  <span data-ttu-id="5f5fb-117">Adicione o código de exemplo ao formulário.</span><span class="sxs-lookup"><span data-stu-id="5f5fb-117">Add the example code to the form.</span></span>  
  
3.  <span data-ttu-id="5f5fb-118">Criar um manipulador para o formulário <xref:System.Windows.Forms.Control.Paint> evento</span><span class="sxs-lookup"><span data-stu-id="5f5fb-118">Create a handler for the form's <xref:System.Windows.Forms.Control.Paint> event</span></span>  
  
4.  <span data-ttu-id="5f5fb-119">No <xref:System.Windows.Forms.Control.Paint> manipulador, chame o `GetThumbnail` método e passe `e` para <xref:System.Windows.Forms.PaintEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="5f5fb-119">In the <xref:System.Windows.Forms.Control.Paint> handler, call the `GetThumbnail` method and pass `e` for <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
5.  <span data-ttu-id="5f5fb-120">Localize um arquivo de imagem do qual deseja criar uma miniatura.</span><span class="sxs-lookup"><span data-stu-id="5f5fb-120">Find an image file that you want to make a thumbnail of.</span></span>  
  
6.  <span data-ttu-id="5f5fb-121">No método `GetThumbnail`, especifique o caminho e nome do arquivo para sua imagem.</span><span class="sxs-lookup"><span data-stu-id="5f5fb-121">In the `GetThumbnail` method, specify the path and file name to your image.</span></span>  
  
7.  <span data-ttu-id="5f5fb-122">Pressione F5 para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="5f5fb-122">Press F5 to run the example.</span></span>  
  
     <span data-ttu-id="5f5fb-123">Uma imagem em miniatura de 100 por 100 aparece no formulário.</span><span class="sxs-lookup"><span data-stu-id="5f5fb-123">A 100 by 100 thumbnail image appears on the form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f5fb-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5f5fb-124">See Also</span></span>  
 [<span data-ttu-id="5f5fb-125">Imagens, bitmaps e metarquivos</span><span class="sxs-lookup"><span data-stu-id="5f5fb-125">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="5f5fb-126">Trabalhando com Imagens, Bitmaps, Ícones e Metarquivos</span><span class="sxs-lookup"><span data-stu-id="5f5fb-126">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
