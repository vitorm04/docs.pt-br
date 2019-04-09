---
title: 'Como: listar os decodificadores instalados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image codecs [Windows Forms], listing
- image decoders [Windows Forms], listing
ms.assetid: 11417191-8c95-40ca-8024-779e61706fb6
ms.openlocfilehash: c92b8010def2f77f859ee0bd9cdb1ed51dd15f27
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079403"
---
# <a name="how-to-list-installed-decoders"></a><span data-ttu-id="c56e1-102">Como: listar os decodificadores instalados</span><span class="sxs-lookup"><span data-stu-id="c56e1-102">How to: List Installed Decoders</span></span>
<span data-ttu-id="c56e1-103">Você talvez queira listar os decodificadores de imagem disponíveis em um computador, para determinar se o seu aplicativo pode ler um formato de arquivo de imagem em particular.</span><span class="sxs-lookup"><span data-stu-id="c56e1-103">You may want to list the image decoders available on a computer, to determine whether your application can read a particular image file format.</span></span> <span data-ttu-id="c56e1-104">O <xref:System.Drawing.Imaging.ImageCodecInfo> classe fornece o <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> métodos estáticos para que você possa determinar qual imagem decodificadores estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="c56e1-104">The <xref:System.Drawing.Imaging.ImageCodecInfo> class provides the <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> static methods so that you can determine which image decoders are available.</span></span> <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> <span data-ttu-id="c56e1-105">Retorna uma matriz de <xref:System.Drawing.Imaging.ImageCodecInfo> objetos.</span><span class="sxs-lookup"><span data-stu-id="c56e1-105">returns an array of <xref:System.Drawing.Imaging.ImageCodecInfo> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c56e1-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c56e1-106">Example</span></span>  
 <span data-ttu-id="c56e1-107">O exemplo de código a seguir gera a lista de decodificadores instalados e seus valores de propriedade.</span><span class="sxs-lookup"><span data-stu-id="c56e1-107">The following code example outputs the list of installed decoders and their property values.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#2](~/samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#2)]
 [!code-vb[UsingImageEncodersDecoders#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c56e1-108">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="c56e1-108">Compiling the Code</span></span>  
 <span data-ttu-id="c56e1-109">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="c56e1-109">This example requires:</span></span>  
  
-   <span data-ttu-id="c56e1-110">Um aplicativo Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c56e1-110">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="c56e1-111">Um <xref:System.Windows.Forms.PaintEventArgs>, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="c56e1-111">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c56e1-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c56e1-112">See also</span></span>

- [<span data-ttu-id="c56e1-113">Como: listar os codificadores instalados</span><span class="sxs-lookup"><span data-stu-id="c56e1-113">How to: List Installed Encoders</span></span>](how-to-list-installed-encoders.md)
- [<span data-ttu-id="c56e1-114">Usando codecs de imagem no GDI+ gerenciado</span><span class="sxs-lookup"><span data-stu-id="c56e1-114">Using Image Encoders and Decoders in Managed GDI+</span></span>](using-image-encoders-and-decoders-in-managed-gdi.md)
