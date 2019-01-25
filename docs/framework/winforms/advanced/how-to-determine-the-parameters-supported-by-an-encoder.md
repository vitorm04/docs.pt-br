---
title: 'Como: Determinar os parâmetros com suporte em um codificador'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encoder parameters [Windows Forms], determining supported
ms.assetid: f47ae459-e3ce-4d41-a140-2f6c6aea3f44
ms.openlocfilehash: 56b78a0cdfcb9ac8e3a7dbc12527fcc59f0524fd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54723401"
---
# <a name="how-to-determine-the-parameters-supported-by-an-encoder"></a><span data-ttu-id="9d7e4-102">Como: Determinar os parâmetros com suporte em um codificador</span><span class="sxs-lookup"><span data-stu-id="9d7e4-102">How to: Determine the Parameters Supported by an Encoder</span></span>
<span data-ttu-id="9d7e4-103">Você pode ajustar os parâmetros de imagem, como o nível de qualidade e compactação, mas você deve saber quais parâmetros são suportados por um codificador de determinada imagem.</span><span class="sxs-lookup"><span data-stu-id="9d7e4-103">You can adjust image parameters, such as quality and compression level, but you must know which parameters are supported by a given image encoder.</span></span> <span data-ttu-id="9d7e4-104">O <xref:System.Drawing.Image> classe fornece o <xref:System.Drawing.Image.GetEncoderParameterList%2A> método para que você possa determinar quais parâmetros de imagem têm suporte para um codificador específico.</span><span class="sxs-lookup"><span data-stu-id="9d7e4-104">The <xref:System.Drawing.Image> class provides the <xref:System.Drawing.Image.GetEncoderParameterList%2A> method so that you can determine which image parameters are supported for a particular encoder.</span></span> <span data-ttu-id="9d7e4-105">Você pode especificar o codificador com um GUID.</span><span class="sxs-lookup"><span data-stu-id="9d7e4-105">You specify the encoder with a GUID.</span></span> <span data-ttu-id="9d7e4-106">O <xref:System.Drawing.Image.GetEncoderParameterList%2A> método retorna uma matriz de <xref:System.Drawing.Imaging.EncoderParameter> objetos.</span><span class="sxs-lookup"><span data-stu-id="9d7e4-106">The <xref:System.Drawing.Image.GetEncoderParameterList%2A> method returns an array of <xref:System.Drawing.Imaging.EncoderParameter> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d7e4-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9d7e4-107">Example</span></span>  
 <span data-ttu-id="9d7e4-108">O exemplo de código a seguir gera os parâmetros com suporte para o codificador JPEG.</span><span class="sxs-lookup"><span data-stu-id="9d7e4-108">The following example code outputs the supported parameters for the JPEG encoder.</span></span> <span data-ttu-id="9d7e4-109">Use a lista de categorias de parâmetro e GUIDs associados no <xref:System.Drawing.Imaging.Encoder> visão geral da classe para determinar a categoria para cada parâmetro.</span><span class="sxs-lookup"><span data-stu-id="9d7e4-109">Use the list of parameter categories and associated GUIDs in the <xref:System.Drawing.Imaging.Encoder> class overview to determine the category for each parameter.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#3)]
 [!code-vb[UsingImageEncodersDecoders#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9d7e4-110">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="9d7e4-110">Compiling the Code</span></span>  
 <span data-ttu-id="9d7e4-111">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="9d7e4-111">This example requires:</span></span>  
  
-   <span data-ttu-id="9d7e4-112">Um aplicativo Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="9d7e4-112">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="9d7e4-113">Um <xref:System.Windows.Forms.PaintEventArgs>, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="9d7e4-113">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d7e4-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9d7e4-114">See also</span></span>
- [<span data-ttu-id="9d7e4-115">Como: Listar os codificadores instalados</span><span class="sxs-lookup"><span data-stu-id="9d7e4-115">How to: List Installed Encoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)
- [<span data-ttu-id="9d7e4-116">Tipos de Bitmaps</span><span class="sxs-lookup"><span data-stu-id="9d7e4-116">Types of Bitmaps</span></span>](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)
- [<span data-ttu-id="9d7e4-117">Usando Codificadores e Decodificadores de Imagem no GDI+ Gerenciado</span><span class="sxs-lookup"><span data-stu-id="9d7e4-117">Using Image Encoders and Decoders in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
