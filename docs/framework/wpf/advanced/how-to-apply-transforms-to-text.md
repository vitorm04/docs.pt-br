---
title: 'Como: Aplicar transformações ao texto'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], rotated text
- typography [WPF], scaled text
- skewed text [WPF]
- typography [WPF], translated text
- typography [WPF], shadowed text
- rotated text [WPF]
- translated text [WPF]
- shadowed text [WPF]
- transforms in text [WPF]
- typography [WPF], transforms
- scaled text [WPF]
- typography [WPF], skewed text
ms.assetid: 0d61678a-4185-4f2a-85c6-c1d020f96fa0
ms.openlocfilehash: 7737a2e01ddfe2a639426bbced643d8f78961207
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54740535"
---
# <a name="how-to-apply-transforms-to-text"></a><span data-ttu-id="2e6f9-102">Como: Aplicar transformações ao texto</span><span class="sxs-lookup"><span data-stu-id="2e6f9-102">How to: Apply Transforms to Text</span></span>
<span data-ttu-id="2e6f9-103">As transformações podem alterar a exibição do texto no seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2e6f9-103">Transforms can alter the display of text in your application.</span></span> <span data-ttu-id="2e6f9-104">Os exemplos a seguir usam diferentes tipos de transformações de renderização para afetar a exibição do texto em um <xref:System.Windows.Controls.TextBlock> controle.</span><span class="sxs-lookup"><span data-stu-id="2e6f9-104">The following examples use different types of rendering transforms to affect the display of text in a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e6f9-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2e6f9-105">Example</span></span>  
 <span data-ttu-id="2e6f9-106">O exemplo a seguir mostra o texto girado sobre um ponto especificado no plano bidimensional x-y.</span><span class="sxs-lookup"><span data-stu-id="2e6f9-106">The following example shows text rotated about a specified point in the two-dimensional x-y plane.</span></span>  
  
 <span data-ttu-id="2e6f9-107">![Texto girado usando um RotateTransform](../../../../docs/framework/wpf/advanced/media/transformedtext01.jpg "TransformedText01")</span><span class="sxs-lookup"><span data-stu-id="2e6f9-107">![Text rotated using a RotateTransform](../../../../docs/framework/wpf/advanced/media/transformedtext01.jpg "TransformedText01")</span></span>  
<span data-ttu-id="2e6f9-108">Exemplo de texto girado em 90 graus</span><span class="sxs-lookup"><span data-stu-id="2e6f9-108">Example of text rotated 90 degrees</span></span>  
  
 <span data-ttu-id="2e6f9-109">O seguinte exemplo de código usa um <xref:System.Windows.Media.RotateTransform> para girar o texto.</span><span class="sxs-lookup"><span data-stu-id="2e6f9-109">The following code example uses a <xref:System.Windows.Media.RotateTransform> to rotate text.</span></span> <span data-ttu-id="2e6f9-110">Um <xref:System.Windows.Media.RotateTransform.Angle%2A> valor de 90 gira o elemento 90 graus no sentido horário.</span><span class="sxs-lookup"><span data-stu-id="2e6f9-110">An <xref:System.Windows.Media.RotateTransform.Angle%2A> value of 90 rotates the element 90 degrees clockwise.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 <span data-ttu-id="2e6f9-111">O exemplo a seguir mostra a segunda linha de texto com escala ajustada em 150% no eixo x e a terceira linha de texto ajustada em 150% no eixo y.</span><span class="sxs-lookup"><span data-stu-id="2e6f9-111">The following example shows the second line of text scaled by 150% along the x-axis, and the third line of text scaled by 150% along the y-axis.</span></span>  
  
 <span data-ttu-id="2e6f9-112">![Texto com escala ajustada usando um ScaleTransform](../../../../docs/framework/wpf/advanced/media/transformedtext02.jpg "TransformedText02")</span><span class="sxs-lookup"><span data-stu-id="2e6f9-112">![Text scaled using a ScaleTransform](../../../../docs/framework/wpf/advanced/media/transformedtext02.jpg "TransformedText02")</span></span>  
<span data-ttu-id="2e6f9-113">Exemplo de texto escalado</span><span class="sxs-lookup"><span data-stu-id="2e6f9-113">Example of scaled text</span></span>  
  
 <span data-ttu-id="2e6f9-114">O seguinte exemplo de código usa um <xref:System.Windows.Media.ScaleTransform> ao texto de escala do seu tamanho original.</span><span class="sxs-lookup"><span data-stu-id="2e6f9-114">The following code example uses a <xref:System.Windows.Media.ScaleTransform> to scale text from its original size.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
>  <span data-ttu-id="2e6f9-115">Dimensionar o texto não é igual a aumentar o tamanho da fonte do texto.</span><span class="sxs-lookup"><span data-stu-id="2e6f9-115">Scaling text is not the same as increasing the font size of text.</span></span> <span data-ttu-id="2e6f9-116">Tamanhos de fonte são calculados independentemente uns dos outros a fim de fornecer a melhor resolução em tamanhos diferentes.</span><span class="sxs-lookup"><span data-stu-id="2e6f9-116">Font sizes are calculated independently of each other in order to provide the best resolution at different sizes.</span></span> <span data-ttu-id="2e6f9-117">O texto com escala ajustada, por outro lado, preserva as proporções do texto em seu tamanho original.</span><span class="sxs-lookup"><span data-stu-id="2e6f9-117">Scaled text, on the other hand, preserves the proportions of the original-sized text.</span></span>  
  
 <span data-ttu-id="2e6f9-118">O exemplo a seguir mostra texto distorcido ao longo do eixo x.</span><span class="sxs-lookup"><span data-stu-id="2e6f9-118">The following example shows text skewed along the x-axis.</span></span>  
  
 <span data-ttu-id="2e6f9-119">![Texto distorcido usando SkewTransform](../../../../docs/framework/wpf/advanced/media/transformedtext03.jpg "TransformedText03")</span><span class="sxs-lookup"><span data-stu-id="2e6f9-119">![Text skewed using a SkewTransform](../../../../docs/framework/wpf/advanced/media/transformedtext03.jpg "TransformedText03")</span></span>  
<span data-ttu-id="2e6f9-120">Exemplo de texto distorcido</span><span class="sxs-lookup"><span data-stu-id="2e6f9-120">Example of skewed text</span></span>  
  
 <span data-ttu-id="2e6f9-121">O seguinte exemplo de código usa um <xref:System.Windows.Media.SkewTransform> para distorcer o texto.</span><span class="sxs-lookup"><span data-stu-id="2e6f9-121">The following code example uses a <xref:System.Windows.Media.SkewTransform> to skew text.</span></span> <span data-ttu-id="2e6f9-122">Uma distorção, também conhecido como uma inclinação, é uma transformação que alonga o espaço de coordenadas de maneira não uniforme.</span><span class="sxs-lookup"><span data-stu-id="2e6f9-122">A skew, also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="2e6f9-123">Neste exemplo, as duas cadeias de caracteres de texto são distorcidas-30° e 30° na coordenada X.</span><span class="sxs-lookup"><span data-stu-id="2e6f9-123">In this example, the two text strings are skewed -30° and 30° along the x-coordinate.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 <span data-ttu-id="2e6f9-124">O exemplo a seguir mostra o texto movido, ou deslocado, nos eixos x e y.</span><span class="sxs-lookup"><span data-stu-id="2e6f9-124">The following example shows text translated, or moved, along the x- and y-axis.</span></span>  
  
 <span data-ttu-id="2e6f9-125">![Deslocamento de texto usando TranslateTransform](../../../../docs/framework/wpf/advanced/media/transformedtext04.jpg "TransformedText04")</span><span class="sxs-lookup"><span data-stu-id="2e6f9-125">![Text offset using a TranslateTransform](../../../../docs/framework/wpf/advanced/media/transformedtext04.jpg "TransformedText04")</span></span>  
<span data-ttu-id="2e6f9-126">Exemplo de texto traduzido</span><span class="sxs-lookup"><span data-stu-id="2e6f9-126">Example of translated text</span></span>  
  
 <span data-ttu-id="2e6f9-127">O seguinte exemplo de código usa um <xref:System.Windows.Media.TranslateTransform> para deslocar o texto.</span><span class="sxs-lookup"><span data-stu-id="2e6f9-127">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="2e6f9-128">Neste exemplo, uma cópia ligeiramente deslocada de texto abaixo do texto primário cria um efeito de sombra.</span><span class="sxs-lookup"><span data-stu-id="2e6f9-128">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
>  <span data-ttu-id="2e6f9-129">O <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> fornece um conjunto avançado de recursos para criar efeitos de sombra.</span><span class="sxs-lookup"><span data-stu-id="2e6f9-129">The <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> provides a rich set of features for providing shadow effects.</span></span> <span data-ttu-id="2e6f9-130">Para obter mais informações, consulte [criar texto com uma sombra](../../../../docs/framework/wpf/advanced/how-to-create-text-with-a-shadow.md).</span><span class="sxs-lookup"><span data-stu-id="2e6f9-130">For more information, see [Create Text with a Shadow](../../../../docs/framework/wpf/advanced/how-to-create-text-with-a-shadow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e6f9-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2e6f9-131">See also</span></span>
- [<span data-ttu-id="2e6f9-132">Aplicar animações ao texto</span><span class="sxs-lookup"><span data-stu-id="2e6f9-132">Apply Animations to Text</span></span>](../../../../docs/framework/wpf/advanced/how-to-apply-animations-to-text.md)
