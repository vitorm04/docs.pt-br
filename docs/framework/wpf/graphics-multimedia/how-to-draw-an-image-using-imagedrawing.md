---
title: 'Como: Desenhar uma imagem usando ImageDrawing'
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], images
- graphics [WPF], drawing images
- images [WPF], drawing
ms.assetid: df28ab41-25fb-4ab3-b51d-7f695b24f55e
ms.openlocfilehash: f9459185bf81160b45222e7d6821e0f945ada381
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947584"
---
# <a name="how-to-draw-an-image-using-imagedrawing"></a><span data-ttu-id="592f8-102">Como: Desenhar uma imagem usando ImageDrawing</span><span class="sxs-lookup"><span data-stu-id="592f8-102">How to: Draw an Image Using ImageDrawing</span></span>
<span data-ttu-id="592f8-103">Este exemplo mostra como usar um <xref:System.Windows.Media.ImageDrawing> para desenhar uma imagem.</span><span class="sxs-lookup"><span data-stu-id="592f8-103">This example shows how to use an <xref:System.Windows.Media.ImageDrawing> to draw an image.</span></span> <span data-ttu-id="592f8-104">Uma <xref:System.Windows.Media.ImageDrawing> permite que você exiba uma <xref:System.Windows.Media.ImageSource> com um <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.DrawingImage>, ou <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="592f8-104">An <xref:System.Windows.Media.ImageDrawing> enables you display an <xref:System.Windows.Media.ImageSource> with a <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.DrawingImage>, or <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="592f8-105">Para desenhar uma imagem, você cria um <xref:System.Windows.Media.ImageDrawing> e defina sua <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> e <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> propriedades.</span><span class="sxs-lookup"><span data-stu-id="592f8-105">To draw an image, you create an <xref:System.Windows.Media.ImageDrawing> and set its <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> and <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> properties.</span></span> <span data-ttu-id="592f8-106">O <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> propriedade especifica a imagem a ser desenhada e o <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> propriedade especifica a posição e tamanho de cada imagem.</span><span class="sxs-lookup"><span data-stu-id="592f8-106">The <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> property specifies the image to draw, and the <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> property specifies the position and size of each image.</span></span>  
  
## <a name="example"></a><span data-ttu-id="592f8-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="592f8-107">Example</span></span>  
 <span data-ttu-id="592f8-108">O exemplo a seguir cria um desenho composto usando quatro <xref:System.Windows.Media.ImageDrawing> objetos.</span><span class="sxs-lookup"><span data-stu-id="592f8-108">The following example creates a composite drawing using four <xref:System.Windows.Media.ImageDrawing> objects.</span></span> <span data-ttu-id="592f8-109">Este exemplo produz a imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="592f8-109">This example produces the following image:</span></span>  
  
 <span data-ttu-id="592f8-110">![Vários objetos DrawingImage](./media/graphicsmm-imagedrawingexample.jpg "graphicsmm_ImageDrawingExample")</span><span class="sxs-lookup"><span data-stu-id="592f8-110">![Several DrawingImage objects](./media/graphicsmm-imagedrawingexample.jpg "graphicsmm_ImageDrawingExample")</span></span>  
<span data-ttu-id="592f8-111">Quatro objetos ImageDrawing</span><span class="sxs-lookup"><span data-stu-id="592f8-111">Four ImageDrawing objects</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawingExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawingexample)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawingExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawingexample)]  
  
 <span data-ttu-id="592f8-112">Para obter um exemplo que mostra uma maneira simples para exibir uma imagem sem usar <xref:System.Windows.Media.ImageDrawing>, consulte [usar o elemento Image](../controls/how-to-use-the-image-element.md).</span><span class="sxs-lookup"><span data-stu-id="592f8-112">For an example showing a simple way to display an image without using <xref:System.Windows.Media.ImageDrawing>, see [Use the Image Element](../controls/how-to-use-the-image-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="592f8-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="592f8-113">See also</span></span>

- <xref:System.Windows.Freezable.Freeze%2A>
- <xref:System.Windows.Controls.Image>
- [<span data-ttu-id="592f8-114">Visão geral dos objetos de desenho</span><span class="sxs-lookup"><span data-stu-id="592f8-114">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="592f8-115">Visão geral de objetos congeláveis</span><span class="sxs-lookup"><span data-stu-id="592f8-115">Freezable Objects Overview</span></span>](../advanced/freezable-objects-overview.md)
- [<span data-ttu-id="592f8-116">Atributo PresentationOptions:Freeze</span><span class="sxs-lookup"><span data-stu-id="592f8-116">PresentationOptions:Freeze Attribute</span></span>](../advanced/presentationoptions-freeze-attribute.md)
