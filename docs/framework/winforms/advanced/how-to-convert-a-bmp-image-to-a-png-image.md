---
title: 'Como: Converter uma imagem BMP em uma imagem PNG'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BMP images [Windows Forms], converting to PNG
- image formats [Windows Forms], converting between
ms.assetid: 9d4a692d-73ac-4ce3-9e05-9ec321e8fbd6
ms.openlocfilehash: e11e2874853fb924b2da09f9fdc986873941f141
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676439"
---
# <a name="how-to-convert-a-bmp-image-to-a-png-image"></a><span data-ttu-id="aae4d-102">Como: Converter uma imagem BMP em uma imagem PNG</span><span class="sxs-lookup"><span data-stu-id="aae4d-102">How to: Convert a BMP image to a PNG image</span></span>
<span data-ttu-id="aae4d-103">Muitas vezes, convém converter do formato de arquivo de uma imagem para outra.</span><span class="sxs-lookup"><span data-stu-id="aae4d-103">Oftentimes, you will want to convert from one image file format to another.</span></span> <span data-ttu-id="aae4d-104">Você pode fazer essa conversão facilmente por meio da chamada a <xref:System.Drawing.Image.Save%2A> método da <xref:System.Drawing.Image> classe e especificando o <xref:System.Drawing.Imaging.ImageFormat> para o formato de arquivo de imagem desejada.</span><span class="sxs-lookup"><span data-stu-id="aae4d-104">You can do this conversion easily by calling the <xref:System.Drawing.Image.Save%2A> method of the <xref:System.Drawing.Image> class and specifying the <xref:System.Drawing.Imaging.ImageFormat> for the desired image file format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aae4d-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aae4d-105">Example</span></span>  
 <span data-ttu-id="aae4d-106">O exemplo a seguir carrega uma imagem BMP de um tipo e salva a imagem no formato PNG.</span><span class="sxs-lookup"><span data-stu-id="aae4d-106">The following example loads a BMP image from a type, and saves the image in the PNG format.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#4)]
 [!code-vb[UsingImageEncodersDecoders#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="aae4d-107">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="aae4d-107">Compiling the Code</span></span>  
 <span data-ttu-id="aae4d-108">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="aae4d-108">This example requires:</span></span>  
  
-   <span data-ttu-id="aae4d-109">Um aplicativo Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="aae4d-109">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="aae4d-110">Uma referência para o `System.Drawing.Imaging` namespace.</span><span class="sxs-lookup"><span data-stu-id="aae4d-110">A reference to the `System.Drawing.Imaging` namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aae4d-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aae4d-111">See also</span></span>
- [<span data-ttu-id="aae4d-112">Como: Listar os codificadores instalados</span><span class="sxs-lookup"><span data-stu-id="aae4d-112">How to: List Installed Encoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)
- [<span data-ttu-id="aae4d-113">Usando Codificadores e Decodificadores de Imagem no GDI+ Gerenciado</span><span class="sxs-lookup"><span data-stu-id="aae4d-113">Using Image Encoders and Decoders in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
- [<span data-ttu-id="aae4d-114">Tipos de Bitmaps</span><span class="sxs-lookup"><span data-stu-id="aae4d-114">Types of Bitmaps</span></span>](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)
