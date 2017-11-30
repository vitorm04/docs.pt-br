---
title: "Como preservar a taxa de proporção de uma imagem usada como um plano de fundo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- aspect ratios of background images [WPF], preserving
- brushes [WPF], preserving aspect ratios of background images
- background images [WPF], preserving aspect ratios
ms.assetid: 28c39478-13d7-4011-80a3-8b9cc3e54478
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a34377403a55ba42d9d3f2946ef26ea48982f5d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-preserve-the-aspect-ratio-of-an-image-used-as-a-background"></a><span data-ttu-id="2b6c3-102">Como preservar a taxa de proporção de uma imagem usada como um plano de fundo</span><span class="sxs-lookup"><span data-stu-id="2b6c3-102">How to: Preserve the Aspect Ratio of an Image Used as a Background</span></span>
<span data-ttu-id="2b6c3-103">Este exemplo mostra como usar o <xref:System.Windows.Media.TileBrush.Stretch%2A> propriedade de um <xref:System.Windows.Media.ImageBrush> para preservar a taxa de proporção da imagem.</span><span class="sxs-lookup"><span data-stu-id="2b6c3-103">This example shows how to use the <xref:System.Windows.Media.TileBrush.Stretch%2A> property of an <xref:System.Windows.Media.ImageBrush> in order to preserve the aspect ratio of the image.</span></span>  
  
 <span data-ttu-id="2b6c3-104">Por padrão, quando você usa um <xref:System.Windows.Media.ImageBrush> para pintar uma área, seu conteúdo é alongado para preencher completamente a área de saída.</span><span class="sxs-lookup"><span data-stu-id="2b6c3-104">By default, when you use an <xref:System.Windows.Media.ImageBrush> to paint an area, its content stretches to completely fill the output area.</span></span> <span data-ttu-id="2b6c3-105">Quando a área de saída e a imagem têm proporções diferentes, a imagem é distorcida pelo ajuste.</span><span class="sxs-lookup"><span data-stu-id="2b6c3-105">When the output area and the image have different aspect ratios, the image is distorted by this stretching.</span></span>  
  
 <span data-ttu-id="2b6c3-106">Para fazer um <xref:System.Windows.Media.ImageBrush> preservar a proporção de sua imagem, defina o <xref:System.Windows.Media.TileBrush.Stretch%2A> propriedade <xref:System.Windows.Media.Stretch.Uniform> ou <xref:System.Windows.Media.Stretch.UniformToFill>.</span><span class="sxs-lookup"><span data-stu-id="2b6c3-106">To make an <xref:System.Windows.Media.ImageBrush> preserve the aspect ratio of its image, set the <xref:System.Windows.Media.TileBrush.Stretch%2A> property to <xref:System.Windows.Media.Stretch.Uniform> or <xref:System.Windows.Media.Stretch.UniformToFill>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b6c3-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b6c3-107">Example</span></span>  
 <span data-ttu-id="2b6c3-108">O exemplo a seguir usa duas <xref:System.Windows.Media.ImageBrush> objetos para pintar dois retângulos.</span><span class="sxs-lookup"><span data-stu-id="2b6c3-108">The following example uses two <xref:System.Windows.Media.ImageBrush> objects to paint two rectangles.</span></span> <span data-ttu-id="2b6c3-109">Cada retângulo tem 300 por 150 pixels, e cada um contém uma imagem de 300 por 300 pixels.</span><span class="sxs-lookup"><span data-stu-id="2b6c3-109">Each rectangle is 300 by 150 pixels and each contains a 300 by 300 pixel image.</span></span> <span data-ttu-id="2b6c3-110">O <xref:System.Windows.Media.TileBrush.Stretch%2A> do primeiro pincel é definida como <xref:System.Windows.Media.Stretch.Uniform>e o <xref:System.Windows.Media.TileBrush.Stretch%2A> do segundo pincel é definida como <xref:System.Windows.Media.Stretch.UniformToFill>.</span><span class="sxs-lookup"><span data-stu-id="2b6c3-110">The <xref:System.Windows.Media.TileBrush.Stretch%2A> property of the first brush is set to <xref:System.Windows.Media.Stretch.Uniform>, and the <xref:System.Windows.Media.TileBrush.Stretch%2A> property of the second brush is set to <xref:System.Windows.Media.Stretch.UniformToFill>.</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushStretchModesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/StretchModes.cs#imagebrushstretchmodesexamplewholepage)]  
  
 <span data-ttu-id="2b6c3-111">A ilustração a seguir mostra a saída do primeiro pincel, que tem um <xref:System.Windows.Media.TileBrush.Stretch%2A> de <xref:System.Windows.Media.Stretch.Uniform>.</span><span class="sxs-lookup"><span data-stu-id="2b6c3-111">The following illustration shows the output of the first brush, which has a <xref:System.Windows.Media.TileBrush.Stretch%2A> setting of <xref:System.Windows.Media.Stretch.Uniform>.</span></span>  
  
 <span data-ttu-id="2b6c3-112">![ImageBrush com alongamento uniforme](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformstretch.jpg "graphicsmm_ImageBrushUniformStretch")</span><span class="sxs-lookup"><span data-stu-id="2b6c3-112">![ImageBrush with Uniform stretching](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformstretch.jpg "graphicsmm_ImageBrushUniformStretch")</span></span>  
  
 <span data-ttu-id="2b6c3-113">A ilustração a seguir mostra a saída do segundo pincel, que tem um <xref:System.Windows.Media.TileBrush.Stretch%2A> de <xref:System.Windows.Media.Stretch.UniformToFill>.</span><span class="sxs-lookup"><span data-stu-id="2b6c3-113">The next illustration shows the output of the second brush, which has a <xref:System.Windows.Media.TileBrush.Stretch%2A> setting of <xref:System.Windows.Media.Stretch.UniformToFill>.</span></span>  
  
 <span data-ttu-id="2b6c3-114">![ImageBrush com alongamento UniformToFill](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformtofillstretch.jpg "graphicsmm_ImageBrushUniformToFillStretch")</span><span class="sxs-lookup"><span data-stu-id="2b6c3-114">![ImageBrush with UniformToFill stretching](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformtofillstretch.jpg "graphicsmm_ImageBrushUniformToFillStretch")</span></span>  
  
 <span data-ttu-id="2b6c3-115">Observe que o <xref:System.Windows.Media.TileBrush.Stretch%2A> propriedade se comporta de forma idêntica para os outros <xref:System.Windows.Media.TileBrush> objetos, ou seja, para <xref:System.Windows.Media.DrawingBrush> e <xref:System.Windows.Media.VisualBrush>.</span><span class="sxs-lookup"><span data-stu-id="2b6c3-115">Note that the <xref:System.Windows.Media.TileBrush.Stretch%2A> property behaves identically for the other <xref:System.Windows.Media.TileBrush> objects, that is, for <xref:System.Windows.Media.DrawingBrush> and <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="2b6c3-116">Para obter mais informações sobre <xref:System.Windows.Media.ImageBrush> e outros <xref:System.Windows.Media.TileBrush> objetos, consulte [pintura com imagens, desenhos e visuais](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).</span><span class="sxs-lookup"><span data-stu-id="2b6c3-116">For more information about <xref:System.Windows.Media.ImageBrush> and the other <xref:System.Windows.Media.TileBrush> objects, see [Painting with Images, Drawings, and Visuals](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).</span></span>  
  
 <span data-ttu-id="2b6c3-117">Observe também que, embora o <xref:System.Windows.Media.TileBrush.Stretch%2A> propriedade aparece para especificar como o <xref:System.Windows.Media.TileBrush> conteúdo ajusta-se para sua área de saída, ela na verdade especifica como o <xref:System.Windows.Media.TileBrush> conteúdo expande para preencher seu tile base.</span><span class="sxs-lookup"><span data-stu-id="2b6c3-117">Note also that, although the <xref:System.Windows.Media.TileBrush.Stretch%2A> property appears to specify how the <xref:System.Windows.Media.TileBrush> content stretches to fit its output area, it actually specifies how the <xref:System.Windows.Media.TileBrush> content stretches to fill its base tile.</span></span> <span data-ttu-id="2b6c3-118">Para obter mais informações, consulte <xref:System.Windows.Media.TileBrush>.</span><span class="sxs-lookup"><span data-stu-id="2b6c3-118">For more information, see <xref:System.Windows.Media.TileBrush>.</span></span>  
  
 <span data-ttu-id="2b6c3-119">Este exemplo de código é parte de um exemplo maior fornecido para a <xref:System.Windows.Media.ImageBrush> classe.</span><span class="sxs-lookup"><span data-stu-id="2b6c3-119">This code example is part of a larger example that is provided for the <xref:System.Windows.Media.ImageBrush> class.</span></span> <span data-ttu-id="2b6c3-120">Para o exemplo completo, consulte [ImageBrush exemplo](http://go.microsoft.com/fwlink/?LinkID=160005).</span><span class="sxs-lookup"><span data-stu-id="2b6c3-120">For the complete sample, see [ImageBrush Sample](http://go.microsoft.com/fwlink/?LinkID=160005).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b6c3-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2b6c3-121">See Also</span></span>  
 <xref:System.Windows.Media.TileBrush>  
 [<span data-ttu-id="2b6c3-122">Pintando com imagens, desenhos e visuais</span><span class="sxs-lookup"><span data-stu-id="2b6c3-122">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
