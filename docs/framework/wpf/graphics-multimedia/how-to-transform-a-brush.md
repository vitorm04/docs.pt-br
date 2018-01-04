---
title: Como transformar um pincel
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], rotating contents
- brushes [WPF], Transform property
- rotating contents of brushes [WPF]
ms.assetid: ebada2f9-f01f-4863-9ea2-c2e4e51610f1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2ee517eb76877bb4e02c021061055b328597c517
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-transform-a-brush"></a><span data-ttu-id="a25c8-102">Como transformar um pincel</span><span class="sxs-lookup"><span data-stu-id="a25c8-102">How to: Transform a Brush</span></span>
<span data-ttu-id="a25c8-103">Este exemplo mostra como transformar <xref:System.Windows.Media.Brush> objetos por meio de suas propriedades de dois transformação: <xref:System.Windows.Media.Brush.RelativeTransform%2A> e <xref:System.Windows.Media.Brush.Transform%2A>.</span><span class="sxs-lookup"><span data-stu-id="a25c8-103">This example shows how to transform <xref:System.Windows.Media.Brush> objects by using their two transformation properties: <xref:System.Windows.Media.Brush.RelativeTransform%2A> and <xref:System.Windows.Media.Brush.Transform%2A>.</span></span>  
  
 <span data-ttu-id="a25c8-104">Os exemplos seguintes usam um <xref:System.Windows.Media.RotateTransform> para girar o conteúdo de um <xref:System.Windows.Media.ImageBrush> 45 graus.</span><span class="sxs-lookup"><span data-stu-id="a25c8-104">The following examples use a <xref:System.Windows.Media.RotateTransform> to rotate the content of an <xref:System.Windows.Media.ImageBrush> by 45 degrees.</span></span>  
  
 <span data-ttu-id="a25c8-105">A ilustração a seguir mostra o <xref:System.Windows.Media.ImageBrush> sem um <xref:System.Windows.Media.RotateTransform>, com o <xref:System.Windows.Media.RotateTransform> aplicada ao <xref:System.Windows.Media.Brush.RelativeTransform%2A> propriedade e com o <xref:System.Windows.Media.RotateTransform> aplicada ao <xref:System.Windows.Media.Brush.Transform%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="a25c8-105">The following illustration shows the <xref:System.Windows.Media.ImageBrush> without a <xref:System.Windows.Media.RotateTransform>, with the <xref:System.Windows.Media.RotateTransform> applied to the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property, and with the <xref:System.Windows.Media.RotateTransform> applied to the <xref:System.Windows.Media.Brush.Transform%2A> property.</span></span>  
  
 <span data-ttu-id="a25c8-106">![Brush RelativeTransform and Transform settings](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")</span><span class="sxs-lookup"><span data-stu-id="a25c8-106">![Brush RelativeTransform and Transform settings](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")</span></span>  
  
## <a name="example"></a><span data-ttu-id="a25c8-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a25c8-107">Example</span></span>  
 <span data-ttu-id="a25c8-108">O primeiro exemplo aplica-se um <xref:System.Windows.Media.RotateTransform> para o <xref:System.Windows.Media.Brush.RelativeTransform%2A> propriedade de um <xref:System.Windows.Media.ImageBrush>.</span><span class="sxs-lookup"><span data-stu-id="a25c8-108">The first example applies a <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property of an <xref:System.Windows.Media.ImageBrush>.</span></span> <span data-ttu-id="a25c8-109">O <xref:System.Windows.Media.RotateTransform.CenterX%2A> e <xref:System.Windows.Media.RotateTransform.CenterY%2A> propriedades de um <xref:System.Windows.Media.RotateTransform> do objeto são definidas como 0,5, que é a coordenada relativa do ponto central deste conteúdo.</span><span class="sxs-lookup"><span data-stu-id="a25c8-109">The <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of a <xref:System.Windows.Media.RotateTransform> object are both set to 0.5, which is the relative coordinate of the center point of this content.</span></span> <span data-ttu-id="a25c8-110">Como resultado, o <xref:System.Windows.Media.ImageBrush> conteúdo gira sobre seu centro.</span><span class="sxs-lookup"><span data-stu-id="a25c8-110">As a result, the <xref:System.Windows.Media.ImageBrush> content rotates about its center.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 <span data-ttu-id="a25c8-111">O segundo exemplo também se aplica uma <xref:System.Windows.Media.RotateTransform> para um <xref:System.Windows.Media.ImageBrush>; no entanto, este exemplo usa o <xref:System.Windows.Media.Brush.Transform%2A> propriedade em vez do <xref:System.Windows.Media.Brush.RelativeTransform%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="a25c8-111">The second example also applies a <xref:System.Windows.Media.RotateTransform> to an <xref:System.Windows.Media.ImageBrush>; however, this example uses the <xref:System.Windows.Media.Brush.Transform%2A> property instead of the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property.</span></span>  
  
 <span data-ttu-id="a25c8-112">Para girar o pincel sobre seu centro, o exemplo define o <xref:System.Windows.Media.RotateTransform.CenterX%2A> e <xref:System.Windows.Media.RotateTransform.CenterY%2A> propriedades do <xref:System.Windows.Media.RotateTransform> objeto em coordenadas absolutas.</span><span class="sxs-lookup"><span data-stu-id="a25c8-112">To rotate the brush about its center, the example sets the <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of the <xref:System.Windows.Media.RotateTransform> object to absolute coordinates.</span></span> <span data-ttu-id="a25c8-113">Como o pincel pinta um retângulo de 175 x 90 pixels, o ponto central do retângulo é (87,5, 45).</span><span class="sxs-lookup"><span data-stu-id="a25c8-113">Because the brush paints a rectangle that is 175 by 90 pixels, the center point of the rectangle is (87.5, 45).</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 <span data-ttu-id="a25c8-114">Para obter uma descrição de como o <xref:System.Windows.Media.Brush.RelativeTransform%2A> e <xref:System.Windows.Media.Brush.Transform%2A> propriedades, consulte o [visão geral de transformação de pincel](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a25c8-114">For a description of how the <xref:System.Windows.Media.Brush.RelativeTransform%2A> and <xref:System.Windows.Media.Brush.Transform%2A> properties work, see the [Brush Transformation Overview](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md).</span></span>  
  
 <span data-ttu-id="a25c8-115">Para obter o exemplo completo, consulte [Exemplo de pincéis](http://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="a25c8-115">For the complete sample, see [Brushes Sample](http://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="a25c8-116">Para obter mais informações sobre pincéis, consulte [Visão geral da pintura com cores sólidas e gradientes](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a25c8-116">For more information about brushes, see [Painting with Solid Colors and Gradients Overview](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a25c8-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a25c8-117">See Also</span></span>  
 [<span data-ttu-id="a25c8-118">Visão geral da transformação de pincel</span><span class="sxs-lookup"><span data-stu-id="a25c8-118">Brush Transformation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md)  
 [<span data-ttu-id="a25c8-119">Visão geral da pintura com cores sólidas e gradientes</span><span class="sxs-lookup"><span data-stu-id="a25c8-119">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [<span data-ttu-id="a25c8-120">Visão geral de transformações</span><span class="sxs-lookup"><span data-stu-id="a25c8-120">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
