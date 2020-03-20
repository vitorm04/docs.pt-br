---
title: Como transformar um pincel
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], rotating contents
- brushes [WPF], Transform property
- rotating contents of brushes [WPF]
ms.assetid: ebada2f9-f01f-4863-9ea2-c2e4e51610f1
ms.openlocfilehash: b4484e2fc1ae3e969b02b1d8f3ae4ab2a035558e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187333"
---
# <a name="how-to-transform-a-brush"></a><span data-ttu-id="c68fa-102">Como transformar um pincel</span><span class="sxs-lookup"><span data-stu-id="c68fa-102">How to: Transform a Brush</span></span>
<span data-ttu-id="c68fa-103">Este exemplo mostra <xref:System.Windows.Media.Brush> como transformar objetos usando <xref:System.Windows.Media.Brush.RelativeTransform%2A> <xref:System.Windows.Media.Brush.Transform%2A>suas duas propriedades de transformação: e .</span><span class="sxs-lookup"><span data-stu-id="c68fa-103">This example shows how to transform <xref:System.Windows.Media.Brush> objects by using their two transformation properties: <xref:System.Windows.Media.Brush.RelativeTransform%2A> and <xref:System.Windows.Media.Brush.Transform%2A>.</span></span>  
  
 <span data-ttu-id="c68fa-104">Os exemplos a <xref:System.Windows.Media.RotateTransform> seguir usam um <xref:System.Windows.Media.ImageBrush> para girar o conteúdo de um em 45 graus.</span><span class="sxs-lookup"><span data-stu-id="c68fa-104">The following examples use a <xref:System.Windows.Media.RotateTransform> to rotate the content of an <xref:System.Windows.Media.ImageBrush> by 45 degrees.</span></span>  
  
 <span data-ttu-id="c68fa-105">A ilustração <xref:System.Windows.Media.ImageBrush> a <xref:System.Windows.Media.RotateTransform>seguir mostra <xref:System.Windows.Media.RotateTransform> o sem um , com o aplicado ao <xref:System.Windows.Media.Brush.RelativeTransform%2A> imóvel, e com o <xref:System.Windows.Media.RotateTransform> aplicado ao <xref:System.Windows.Media.Brush.Transform%2A> imóvel.</span><span class="sxs-lookup"><span data-stu-id="c68fa-105">The following illustration shows the <xref:System.Windows.Media.ImageBrush> without a <xref:System.Windows.Media.RotateTransform>, with the <xref:System.Windows.Media.RotateTransform> applied to the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property, and with the <xref:System.Windows.Media.RotateTransform> applied to the <xref:System.Windows.Media.Brush.Transform%2A> property.</span></span>  
  
 <span data-ttu-id="c68fa-106">![Configurações de Brush RelativeTransform e Transform](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")</span><span class="sxs-lookup"><span data-stu-id="c68fa-106">![Brush RelativeTransform and Transform settings](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")</span></span>  
  
## <a name="example"></a><span data-ttu-id="c68fa-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c68fa-107">Example</span></span>  
 <span data-ttu-id="c68fa-108">O primeiro exemplo <xref:System.Windows.Media.RotateTransform> se <xref:System.Windows.Media.Brush.RelativeTransform%2A> aplica a <xref:System.Windows.Media.ImageBrush>a a propriedade de um .</span><span class="sxs-lookup"><span data-stu-id="c68fa-108">The first example applies a <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property of an <xref:System.Windows.Media.ImageBrush>.</span></span> <span data-ttu-id="c68fa-109">As <xref:System.Windows.Media.RotateTransform.CenterX%2A> <xref:System.Windows.Media.RotateTransform.CenterY%2A> propriedades de <xref:System.Windows.Media.RotateTransform> um objeto são definidas como 0,5, que é a coordenada relativa do ponto central deste conteúdo.</span><span class="sxs-lookup"><span data-stu-id="c68fa-109">The <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of a <xref:System.Windows.Media.RotateTransform> object are both set to 0.5, which is the relative coordinate of the center point of this content.</span></span> <span data-ttu-id="c68fa-110">Como resultado, <xref:System.Windows.Media.ImageBrush> o conteúdo gira sobre seu centro.</span><span class="sxs-lookup"><span data-stu-id="c68fa-110">As a result, the <xref:System.Windows.Media.ImageBrush> content rotates about its center.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 <span data-ttu-id="c68fa-111">O segundo exemplo também <xref:System.Windows.Media.RotateTransform> se <xref:System.Windows.Media.ImageBrush>aplica a a a; no entanto, <xref:System.Windows.Media.Brush.Transform%2A> este exemplo <xref:System.Windows.Media.Brush.RelativeTransform%2A> usa a propriedade em vez da propriedade.</span><span class="sxs-lookup"><span data-stu-id="c68fa-111">The second example also applies a <xref:System.Windows.Media.RotateTransform> to an <xref:System.Windows.Media.ImageBrush>; however, this example uses the <xref:System.Windows.Media.Brush.Transform%2A> property instead of the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property.</span></span>  
  
 <span data-ttu-id="c68fa-112">Para girar o pincel sobre seu <xref:System.Windows.Media.RotateTransform.CenterX%2A> centro, o exemplo define as propriedades do <xref:System.Windows.Media.RotateTransform.CenterY%2A> <xref:System.Windows.Media.RotateTransform> objeto para coordenadas absolutas.</span><span class="sxs-lookup"><span data-stu-id="c68fa-112">To rotate the brush about its center, the example sets the <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of the <xref:System.Windows.Media.RotateTransform> object to absolute coordinates.</span></span> <span data-ttu-id="c68fa-113">Como o pincel pinta um retângulo de 175 x 90 pixels, o ponto central do retângulo é (87,5, 45).</span><span class="sxs-lookup"><span data-stu-id="c68fa-113">Because the brush paints a rectangle that is 175 by 90 pixels, the center point of the rectangle is (87.5, 45).</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 <span data-ttu-id="c68fa-114">Para obter uma <xref:System.Windows.Media.Brush.RelativeTransform%2A> descrição <xref:System.Windows.Media.Brush.Transform%2A> de como as propriedades funcionam, consulte a visão geral da [transformação do pincel](brush-transformation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c68fa-114">For a description of how the <xref:System.Windows.Media.Brush.RelativeTransform%2A> and <xref:System.Windows.Media.Brush.Transform%2A> properties work, see the [Brush Transformation Overview](brush-transformation-overview.md).</span></span>  
  
 <span data-ttu-id="c68fa-115">Para obter o exemplo completo, consulte [Exemplo de pincéis](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span><span class="sxs-lookup"><span data-stu-id="c68fa-115">For the complete sample, see [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span></span> <span data-ttu-id="c68fa-116">Para obter mais informações sobre pincéis, consulte [Visão geral da pintura com cores sólidas e gradientes](painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c68fa-116">For more information about brushes, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c68fa-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="c68fa-117">See also</span></span>

- [<span data-ttu-id="c68fa-118">Visão geral da transformação de pincel</span><span class="sxs-lookup"><span data-stu-id="c68fa-118">Brush Transformation Overview</span></span>](brush-transformation-overview.md)
- [<span data-ttu-id="c68fa-119">Visão geral da pintura com cores sólidas e gradientes</span><span class="sxs-lookup"><span data-stu-id="c68fa-119">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="c68fa-120">Visão geral de transformações</span><span class="sxs-lookup"><span data-stu-id="c68fa-120">Transforms Overview</span></span>](transforms-overview.md)
