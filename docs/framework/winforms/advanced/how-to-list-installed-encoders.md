---
title: 'Como: listar os codificadores instalados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image codecs [Windows Forms], listing
- image encoders [Windows Forms], listing
ms.assetid: 49e8e4e9-7a67-42d9-86bf-08821cdc282e
ms.openlocfilehash: ce297cb6d183bc63c8b276e30100aa4e864cd90d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078805"
---
# <a name="how-to-list-installed-encoders"></a><span data-ttu-id="1cd4d-102">Como: listar os codificadores instalados</span><span class="sxs-lookup"><span data-stu-id="1cd4d-102">How to: List Installed Encoders</span></span>
<span data-ttu-id="1cd4d-103">Você talvez queira listar os codificadores de imagem disponíveis em um computador, para determinar se o seu aplicativo pode salvar em um formato de arquivo de imagem em particular.</span><span class="sxs-lookup"><span data-stu-id="1cd4d-103">You may want to list the image encoders available on a computer, to determine whether your application can save to a particular image file format.</span></span> <span data-ttu-id="1cd4d-104">O <xref:System.Drawing.Imaging.ImageCodecInfo> classe fornece o <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> métodos estáticos para que você possa determinar qual imagem codificadores estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="1cd4d-104">The <xref:System.Drawing.Imaging.ImageCodecInfo> class provides the <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> static methods so that you can determine which image encoders are available.</span></span> <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> <span data-ttu-id="1cd4d-105">Retorna uma matriz de <xref:System.Drawing.Imaging.ImageCodecInfo> objetos.</span><span class="sxs-lookup"><span data-stu-id="1cd4d-105">returns an array of <xref:System.Drawing.Imaging.ImageCodecInfo> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1cd4d-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1cd4d-106">Example</span></span>  
 <span data-ttu-id="1cd4d-107">O exemplo de código a seguir gera a lista de codificadores instalados e seus valores de propriedade.</span><span class="sxs-lookup"><span data-stu-id="1cd4d-107">The following code example outputs the list of installed encoders and their property values.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#1](~/samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#1)]
 [!code-vb[UsingImageEncodersDecoders#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1cd4d-108">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="1cd4d-108">Compiling the Code</span></span>  
 <span data-ttu-id="1cd4d-109">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="1cd4d-109">This example requires:</span></span>  
  
-   <span data-ttu-id="1cd4d-110">Um aplicativo Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1cd4d-110">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="1cd4d-111">Um <xref:System.Windows.Forms.PaintEventArgs>, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="1cd4d-111">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cd4d-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1cd4d-112">See also</span></span>

- [<span data-ttu-id="1cd4d-113">Como: listar os decodificadores instalados</span><span class="sxs-lookup"><span data-stu-id="1cd4d-113">How to: List Installed Decoders</span></span>](how-to-list-installed-decoders.md)
- [<span data-ttu-id="1cd4d-114">Usando codecs de imagem no GDI+ gerenciado</span><span class="sxs-lookup"><span data-stu-id="1cd4d-114">Using Image Encoders and Decoders in Managed GDI+</span></span>](using-image-encoders-and-decoders-in-managed-gdi.md)
