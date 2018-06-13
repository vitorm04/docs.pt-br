---
title: Como listar os codificadores instalados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image codecs [Windows Forms], listing
- image encoders [Windows Forms], listing
ms.assetid: 49e8e4e9-7a67-42d9-86bf-08821cdc282e
ms.openlocfilehash: 1882ce9a140fb325c29411173ba7bde717bd3f98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524749"
---
# <a name="how-to-list-installed-encoders"></a><span data-ttu-id="0d1c2-102">Como listar os codificadores instalados</span><span class="sxs-lookup"><span data-stu-id="0d1c2-102">How to: List Installed Encoders</span></span>
<span data-ttu-id="0d1c2-103">Pode ser que você deseja listar os codificadores de imagem disponíveis em um computador, para determinar se o seu aplicativo pode salvar em um formato de arquivo de imagem específico.</span><span class="sxs-lookup"><span data-stu-id="0d1c2-103">You may want to list the image encoders available on a computer, to determine whether your application can save to a particular image file format.</span></span> <span data-ttu-id="0d1c2-104">O <xref:System.Drawing.Imaging.ImageCodecInfo> classe fornece a <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> métodos estáticos para que você possa determinar qual imagem codificadores estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="0d1c2-104">The <xref:System.Drawing.Imaging.ImageCodecInfo> class provides the <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> static methods so that you can determine which image encoders are available.</span></span> <span data-ttu-id="0d1c2-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> Retorna uma matriz de <xref:System.Drawing.Imaging.ImageCodecInfo> objetos.</span><span class="sxs-lookup"><span data-stu-id="0d1c2-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> returns an array of <xref:System.Drawing.Imaging.ImageCodecInfo> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d1c2-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0d1c2-106">Example</span></span>  
 <span data-ttu-id="0d1c2-107">O exemplo de código a seguir gera a lista de codificadores instalados e seus valores de propriedade.</span><span class="sxs-lookup"><span data-stu-id="0d1c2-107">The following code example outputs the list of installed encoders and their property values.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#1)]
 [!code-vb[UsingImageEncodersDecoders#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0d1c2-108">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="0d1c2-108">Compiling the Code</span></span>  
 <span data-ttu-id="0d1c2-109">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="0d1c2-109">This example requires:</span></span>  
  
-   <span data-ttu-id="0d1c2-110">Um aplicativo Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="0d1c2-110">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="0d1c2-111">Um <xref:System.Windows.Forms.PaintEventArgs>, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="0d1c2-111">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d1c2-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0d1c2-112">See Also</span></span>  
 [<span data-ttu-id="0d1c2-113">Como Listar os Decodificadores Instalados</span><span class="sxs-lookup"><span data-stu-id="0d1c2-113">How to: List Installed Decoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-decoders.md)  
 [<span data-ttu-id="0d1c2-114">Usando Codificadores e Decodificadores de Imagem no GDI+ Gerenciado</span><span class="sxs-lookup"><span data-stu-id="0d1c2-114">Using Image Encoders and Decoders in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
