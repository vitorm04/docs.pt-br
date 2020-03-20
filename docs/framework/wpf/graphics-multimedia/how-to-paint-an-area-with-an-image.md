---
title: Como pintar uma área com uma imagem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [WPF], painting with
- painting [WPF], with images
- brushes [WPF], painting with images
ms.assetid: 3432c533-1fc7-492d-94ee-0b13d60125ae
ms.openlocfilehash: 92969778c04c6ac634a2964c402d6c3439b96b49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186052"
---
# <a name="how-to-paint-an-area-with-an-image"></a><span data-ttu-id="24b5a-102">Como pintar uma área com uma imagem</span><span class="sxs-lookup"><span data-stu-id="24b5a-102">How to: Paint an Area with an Image</span></span>
<span data-ttu-id="24b5a-103">Este exemplo mostra como <xref:System.Windows.Media.ImageBrush> usar a classe para pintar uma área com uma imagem.</span><span class="sxs-lookup"><span data-stu-id="24b5a-103">This example shows how to use the <xref:System.Windows.Media.ImageBrush> class to paint an area with an image.</span></span> <span data-ttu-id="24b5a-104">Um <xref:System.Windows.Media.ImageBrush> exibe uma única imagem, que <xref:System.Windows.Media.ImageBrush.ImageSource%2A> é especificada por sua propriedade.</span><span class="sxs-lookup"><span data-stu-id="24b5a-104">An <xref:System.Windows.Media.ImageBrush> displays a single image, which is specified by its <xref:System.Windows.Media.ImageBrush.ImageSource%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24b5a-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="24b5a-105">Example</span></span>  
 <span data-ttu-id="24b5a-106">O exemplo a <xref:System.Windows.Controls.Control.Background%2A> seguir pinta o <xref:System.Windows.Media.ImageBrush>de um botão usando um .</span><span class="sxs-lookup"><span data-stu-id="24b5a-106">The following example paints the <xref:System.Windows.Controls.Control.Background%2A> of a button by using an <xref:System.Windows.Media.ImageBrush>.</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/PaintingWithImagesExample.cs#imagebrushexamplewholepage)]  
  
 <span data-ttu-id="24b5a-107">Por padrão, <xref:System.Windows.Media.ImageBrush> um alonga sua imagem para preencher completamente a área que você está pintando.</span><span class="sxs-lookup"><span data-stu-id="24b5a-107">By default, an <xref:System.Windows.Media.ImageBrush> stretches its image to completely fill the area that you are painting.</span></span> <span data-ttu-id="24b5a-108">No exemplo anterior, a imagem é esticada para preencher o botão, possivelmente distorcendo a imagem.</span><span class="sxs-lookup"><span data-stu-id="24b5a-108">In the preceding example, the image is stretched to fill the button, possibly distorting the image.</span></span> <span data-ttu-id="24b5a-109">Você pode controlar esse <xref:System.Windows.Media.TileBrush.Stretch%2A> comportamento <xref:System.Windows.Media.TileBrush> definindo <xref:System.Windows.Media.Stretch.UniformToFill>a propriedade de ou <xref:System.Windows.Media.Stretch.Uniform> , o que faz com que o pincel preserve a proporção da imagem.</span><span class="sxs-lookup"><span data-stu-id="24b5a-109">You can control this behavior by setting the <xref:System.Windows.Media.TileBrush.Stretch%2A> property of <xref:System.Windows.Media.TileBrush> to <xref:System.Windows.Media.Stretch.Uniform> or <xref:System.Windows.Media.Stretch.UniformToFill>, which causes the brush to preserve the aspect ratio of the image.</span></span>  
  
 <span data-ttu-id="24b5a-110">Se você <xref:System.Windows.Media.TileBrush.Viewport%2A> definir <xref:System.Windows.Media.TileBrush.TileMode%2A> as <xref:System.Windows.Media.ImageBrush>propriedades de um , você pode criar um padrão de repetição.</span><span class="sxs-lookup"><span data-stu-id="24b5a-110">If you set the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.TileMode%2A> properties of an <xref:System.Windows.Media.ImageBrush>, you can create a repeating pattern.</span></span> <span data-ttu-id="24b5a-111">O exemplo a seguir pinta um botão usando um padrão que é criado por meio de uma imagem.</span><span class="sxs-lookup"><span data-stu-id="24b5a-111">The following example paints a button by using a pattern that is created from an image.</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#TiledImageBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TiledImageBrushExample.cs#tiledimagebrushexamplewholepage)]
 [!code-vb[UsingImageBrush_snip#TiledImageBrushExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UsingImageBrush_snip/VisualBasic/TiledImageBrushExample.vb#tiledimagebrushexamplewholepage)]  
  
 <span data-ttu-id="24b5a-112">Para obter mais <xref:System.Windows.Media.ImageBrush> informações sobre a classe, consulte [Pintura com Imagens, Desenhos e Visuais](painting-with-images-drawings-and-visuals.md).</span><span class="sxs-lookup"><span data-stu-id="24b5a-112">For more information about the <xref:System.Windows.Media.ImageBrush> class, see [Painting with Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).</span></span>  
  
 <span data-ttu-id="24b5a-113">Este exemplo de código é parte de um <xref:System.Windows.Media.ImageBrush> exemplo maior que é fornecido para a classe.</span><span class="sxs-lookup"><span data-stu-id="24b5a-113">This code example is part of a larger example that is provided for the <xref:System.Windows.Media.ImageBrush> class.</span></span> <span data-ttu-id="24b5a-114">Para obter a amostra completa, consulte [ImageBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush).</span><span class="sxs-lookup"><span data-stu-id="24b5a-114">For the complete sample, see [ImageBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24b5a-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="24b5a-115">See also</span></span>

- [<span data-ttu-id="24b5a-116">Pintando com imagens, desenhos e visuais</span><span class="sxs-lookup"><span data-stu-id="24b5a-116">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
