---
title: 'Como: converter uma imagem BMP em uma imagem PNG'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BMP images [Windows Forms], converting to PNG
- image formats [Windows Forms], converting between
ms.assetid: 9d4a692d-73ac-4ce3-9e05-9ec321e8fbd6
ms.openlocfilehash: 3072c07781a8e8e57b64b48e5b4c304c2a0a0efb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217010"
---
# <a name="how-to-convert-a-bmp-image-to-a-png-image"></a><span data-ttu-id="8ab23-102">Como: converter uma imagem BMP em uma imagem PNG</span><span class="sxs-lookup"><span data-stu-id="8ab23-102">How to: Convert a BMP image to a PNG image</span></span>
<span data-ttu-id="8ab23-103">Muitas vezes, convém converter do formato de arquivo de uma imagem para outra.</span><span class="sxs-lookup"><span data-stu-id="8ab23-103">Oftentimes, you will want to convert from one image file format to another.</span></span> <span data-ttu-id="8ab23-104">Você pode fazer essa conversão facilmente por meio da chamada a <xref:System.Drawing.Image.Save%2A> método da <xref:System.Drawing.Image> classe e especificando o <xref:System.Drawing.Imaging.ImageFormat> para o formato de arquivo de imagem desejada.</span><span class="sxs-lookup"><span data-stu-id="8ab23-104">You can do this conversion easily by calling the <xref:System.Drawing.Image.Save%2A> method of the <xref:System.Drawing.Image> class and specifying the <xref:System.Drawing.Imaging.ImageFormat> for the desired image file format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ab23-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8ab23-105">Example</span></span>  
 <span data-ttu-id="8ab23-106">O exemplo a seguir carrega uma imagem BMP de um tipo e salva a imagem no formato PNG.</span><span class="sxs-lookup"><span data-stu-id="8ab23-106">The following example loads a BMP image from a type, and saves the image in the PNG format.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#4](~/samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#4)]
 [!code-vb[UsingImageEncodersDecoders#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8ab23-107">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="8ab23-107">Compiling the Code</span></span>  
 <span data-ttu-id="8ab23-108">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="8ab23-108">This example requires:</span></span>  
  
-   <span data-ttu-id="8ab23-109">Um aplicativo Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="8ab23-109">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="8ab23-110">Uma referência para o `System.Drawing.Imaging` namespace.</span><span class="sxs-lookup"><span data-stu-id="8ab23-110">A reference to the `System.Drawing.Imaging` namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ab23-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ab23-111">See also</span></span>

- [<span data-ttu-id="8ab23-112">Como: listar os codificadores instalados</span><span class="sxs-lookup"><span data-stu-id="8ab23-112">How to: List Installed Encoders</span></span>](how-to-list-installed-encoders.md)
- [<span data-ttu-id="8ab23-113">Usando codecs de imagem no GDI+ gerenciado</span><span class="sxs-lookup"><span data-stu-id="8ab23-113">Using Image Encoders and Decoders in Managed GDI+</span></span>](using-image-encoders-and-decoders-in-managed-gdi.md)
- [<span data-ttu-id="8ab23-114">Tipos de bitmaps</span><span class="sxs-lookup"><span data-stu-id="8ab23-114">Types of Bitmaps</span></span>](types-of-bitmaps.md)
