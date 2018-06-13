---
title: Como converter uma imagem BMP em uma imagem PNG
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BMP images [Windows Forms], converting to PNG
- image formats [Windows Forms], converting between
ms.assetid: 9d4a692d-73ac-4ce3-9e05-9ec321e8fbd6
ms.openlocfilehash: fd890c4f17b9759d37d7625526366034c664a71a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520780"
---
# <a name="how-to-convert-a-bmp-image-to-a-png-image"></a><span data-ttu-id="55493-102">Como converter uma imagem BMP em uma imagem PNG</span><span class="sxs-lookup"><span data-stu-id="55493-102">How to: Convert a BMP image to a PNG image</span></span>
<span data-ttu-id="55493-103">Muitas vezes, você deve converter do formato de arquivo de uma imagem para outra.</span><span class="sxs-lookup"><span data-stu-id="55493-103">Oftentimes, you will want to convert from one image file format to another.</span></span> <span data-ttu-id="55493-104">Você pode fazer essa conversão facilmente chamando o <xref:System.Drawing.Image.Save%2A> método o <xref:System.Drawing.Image> classe e especificando o <xref:System.Drawing.Imaging.ImageFormat> para o formato de arquivo da imagem desejada.</span><span class="sxs-lookup"><span data-stu-id="55493-104">You can do this conversion easily by calling the <xref:System.Drawing.Image.Save%2A> method of the <xref:System.Drawing.Image> class and specifying the <xref:System.Drawing.Imaging.ImageFormat> for the desired image file format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55493-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="55493-105">Example</span></span>  
 <span data-ttu-id="55493-106">O exemplo a seguir carrega uma imagem BMP de um tipo e salva a imagem no formato PNG.</span><span class="sxs-lookup"><span data-stu-id="55493-106">The following example loads a BMP image from a type, and saves the image in the PNG format.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#4)]
 [!code-vb[UsingImageEncodersDecoders#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="55493-107">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="55493-107">Compiling the Code</span></span>  
 <span data-ttu-id="55493-108">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="55493-108">This example requires:</span></span>  
  
-   <span data-ttu-id="55493-109">Um aplicativo Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="55493-109">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="55493-110">Uma referência para o `System.Drawing.Imaging` namespace.</span><span class="sxs-lookup"><span data-stu-id="55493-110">A reference to the `System.Drawing.Imaging` namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55493-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55493-111">See Also</span></span>  
 [<span data-ttu-id="55493-112">Como Listar os Codificadores Instalados</span><span class="sxs-lookup"><span data-stu-id="55493-112">How to: List Installed Encoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 [<span data-ttu-id="55493-113">Usando Codificadores e Decodificadores de Imagem no GDI+ Gerenciado</span><span class="sxs-lookup"><span data-stu-id="55493-113">Using Image Encoders and Decoders in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)  
 [<span data-ttu-id="55493-114">Tipos de Bitmaps</span><span class="sxs-lookup"><span data-stu-id="55493-114">Types of Bitmaps</span></span>](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)
