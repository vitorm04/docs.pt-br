---
title: Como desenhar uma imagem usando ImageDrawing
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], images
- graphics [WPF], drawing images
- images [WPF], drawing
ms.assetid: df28ab41-25fb-4ab3-b51d-7f695b24f55e
ms.openlocfilehash: 2c7771f841fb3b600d4790eb4d484b0a09c45dd5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559873"
---
# <a name="how-to-draw-an-image-using-imagedrawing"></a><span data-ttu-id="44cd9-102">Como desenhar uma imagem usando ImageDrawing</span><span class="sxs-lookup"><span data-stu-id="44cd9-102">How to: Draw an Image Using ImageDrawing</span></span>
<span data-ttu-id="44cd9-103">Este exemplo mostra como usar um <xref:System.Windows.Media.ImageDrawing> para desenhar uma imagem.</span><span class="sxs-lookup"><span data-stu-id="44cd9-103">This example shows how to use an <xref:System.Windows.Media.ImageDrawing> to draw an image.</span></span> <span data-ttu-id="44cd9-104">Um <xref:System.Windows.Media.ImageDrawing> permite que você exiba um <xref:System.Windows.Media.ImageSource> com um <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.DrawingImage>, ou <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="44cd9-104">An <xref:System.Windows.Media.ImageDrawing> enables you display an <xref:System.Windows.Media.ImageSource> with a <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.DrawingImage>, or <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="44cd9-105">Para desenhar uma imagem, você cria um <xref:System.Windows.Media.ImageDrawing> e defina seu <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> e <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> propriedades.</span><span class="sxs-lookup"><span data-stu-id="44cd9-105">To draw an image, you create an <xref:System.Windows.Media.ImageDrawing> and set its <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> and <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> properties.</span></span> <span data-ttu-id="44cd9-106">O <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> propriedade especifica a imagem a ser desenhada e o <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> propriedade especifica a posição e o tamanho de cada imagem.</span><span class="sxs-lookup"><span data-stu-id="44cd9-106">The <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> property specifies the image to draw, and the <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> property specifies the position and size of each image.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44cd9-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="44cd9-107">Example</span></span>  
 <span data-ttu-id="44cd9-108">O exemplo a seguir cria um desenho composto usando quatro <xref:System.Windows.Media.ImageDrawing> objetos.</span><span class="sxs-lookup"><span data-stu-id="44cd9-108">The following example creates a composite drawing using four <xref:System.Windows.Media.ImageDrawing> objects.</span></span> <span data-ttu-id="44cd9-109">Este exemplo produz a imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="44cd9-109">This example produces the following image:</span></span>  
  
 <span data-ttu-id="44cd9-110">![Vários objetos DrawingImage](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagedrawingexample.jpg "graphicsmm_ImageDrawingExample")</span><span class="sxs-lookup"><span data-stu-id="44cd9-110">![Several DrawingImage objects](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagedrawingexample.jpg "graphicsmm_ImageDrawingExample")</span></span>  
<span data-ttu-id="44cd9-111">Quatro objetos ImageDrawing</span><span class="sxs-lookup"><span data-stu-id="44cd9-111">Four ImageDrawing objects</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawingExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawingexample)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawingExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawingexample)]  
  
 <span data-ttu-id="44cd9-112">Para obter um exemplo que mostra uma maneira simples para exibir uma imagem sem usar <xref:System.Windows.Media.ImageDrawing>, consulte [usar o elemento de imagem](../../../../docs/framework/wpf/controls/how-to-use-the-image-element.md).</span><span class="sxs-lookup"><span data-stu-id="44cd9-112">For an example showing a simple way to display an image without using <xref:System.Windows.Media.ImageDrawing>, see [Use the Image Element](../../../../docs/framework/wpf/controls/how-to-use-the-image-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44cd9-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="44cd9-113">See Also</span></span>  
 <xref:System.Windows.Freezable.Freeze%2A>  
 <xref:System.Windows.Controls.Image>  
 [<span data-ttu-id="44cd9-114">Visão geral dos objetos de desenho</span><span class="sxs-lookup"><span data-stu-id="44cd9-114">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="44cd9-115">Visão geral de objetos congeláveis</span><span class="sxs-lookup"><span data-stu-id="44cd9-115">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [<span data-ttu-id="44cd9-116">Atributo PresentationOptions:Freeze</span><span class="sxs-lookup"><span data-stu-id="44cd9-116">PresentationOptions:Freeze Attribute</span></span>](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)
