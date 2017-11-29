---
title: Como desenhar um bitmap existente na tela
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
- bitmaps [Windows Forms], displaying in Windows Forms
- bitmaps [Windows Forms], loading in Windows Forms applications
- images [Windows Forms], displaying on Windows Forms
ms.assetid: 5bc558d7-b326-4050-a834-b8600da0de95
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f435c397832e8f64b2bf911a59aae7578ffd3bdf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-an-existing-bitmap-to-the-screen"></a><span data-ttu-id="8fc90-102">Como desenhar um bitmap existente na tela</span><span class="sxs-lookup"><span data-stu-id="8fc90-102">How to: Draw an Existing Bitmap to the Screen</span></span>
<span data-ttu-id="8fc90-103">Você pode desenhar facilmente uma imagem existente na tela.</span><span class="sxs-lookup"><span data-stu-id="8fc90-103">You can easily draw an existing image on the screen.</span></span> <span data-ttu-id="8fc90-104">Primeiro você precisa criar um <xref:System.Drawing.Bitmap> objeto usando o construtor de bitmap que usa um nome de arquivo <xref:System.Drawing.Bitmap.%23ctor%28System.String%29>.</span><span class="sxs-lookup"><span data-stu-id="8fc90-104">First you need to create a <xref:System.Drawing.Bitmap> object by using the bitmap constructor that takes a file name, <xref:System.Drawing.Bitmap.%23ctor%28System.String%29>.</span></span> <span data-ttu-id="8fc90-105">Este construtor aceita imagens com diferentes formatos de arquivo, incluindo BMP, GIF, JPEG, PNG e TIFF.</span><span class="sxs-lookup"><span data-stu-id="8fc90-105">This constructor accepts images with several different file formats, including BMP, GIF, JPEG, PNG, and TIFF.</span></span> <span data-ttu-id="8fc90-106">Depois que você criou o <xref:System.Drawing.Bitmap> de objeto, passe que <xref:System.Drawing.Bitmap> o objeto para o <xref:System.Drawing.Graphics.DrawImage%2A> método de um <xref:System.Drawing.Graphics> objeto.</span><span class="sxs-lookup"><span data-stu-id="8fc90-106">After you have created the <xref:System.Drawing.Bitmap> object, pass that <xref:System.Drawing.Bitmap> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8fc90-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8fc90-107">Example</span></span>  
 <span data-ttu-id="8fc90-108">Este exemplo cria um <xref:System.Drawing.Bitmap> objeto a partir de um arquivo JPEG e, em seguida, usa o bitmap com seu canto superior esquerdo no (60, 10).</span><span class="sxs-lookup"><span data-stu-id="8fc90-108">This example creates a <xref:System.Drawing.Bitmap> object from a JPEG file and then draws the bitmap with its upper-left corner at (60, 10).</span></span>  
  
 <span data-ttu-id="8fc90-109">A ilustração a seguir mostra o bitmap desenhado no local especificado.</span><span class="sxs-lookup"><span data-stu-id="8fc90-109">The following illustration shows the bitmap drawn at the specified location.</span></span>  
  
 <span data-ttu-id="8fc90-110">![Posição da imagem](../../../../docs/framework/winforms/advanced/media/csimageposition1.png "csimageposition1")</span><span class="sxs-lookup"><span data-stu-id="8fc90-110">![Image Position](../../../../docs/framework/winforms/advanced/media/csimageposition1.png "csimageposition1")</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.WorkingWithImages#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8fc90-111">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="8fc90-111">Compiling the Code</span></span>  
 <span data-ttu-id="8fc90-112">O exemplo anterior é projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="8fc90-112">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fc90-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8fc90-113">See Also</span></span>  
 [<span data-ttu-id="8fc90-114">Elementos Gráficos e Desenho nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8fc90-114">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="8fc90-115">Trabalhando com Imagens, Bitmaps, Ícones e Metarquivos</span><span class="sxs-lookup"><span data-stu-id="8fc90-115">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
