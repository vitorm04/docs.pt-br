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
ms.openlocfilehash: be0b6a0bbe927f248be434afd15dde6a66791fe6
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/17/2019
ms.locfileid: "58126117"
---
# <a name="how-to-apply-transforms-to-text"></a><span data-ttu-id="94a77-102">Como: Aplicar transformações ao texto</span><span class="sxs-lookup"><span data-stu-id="94a77-102">How to: Apply Transforms to Text</span></span>
<span data-ttu-id="94a77-103">As transformações podem alterar a exibição do texto no seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="94a77-103">Transforms can alter the display of text in your application.</span></span> <span data-ttu-id="94a77-104">Os exemplos a seguir usam diferentes tipos de transformações de renderização para afetar a exibição do texto em um <xref:System.Windows.Controls.TextBlock> controle.</span><span class="sxs-lookup"><span data-stu-id="94a77-104">The following examples use different types of rendering transforms to affect the display of text in a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94a77-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="94a77-105">Example</span></span>  
 <span data-ttu-id="94a77-106">O exemplo a seguir mostra o texto girado sobre um ponto especificado no plano bidimensional x-y.</span><span class="sxs-lookup"><span data-stu-id="94a77-106">The following example shows text rotated about a specified point in the two-dimensional x-y plane.</span></span>  
  
 ![Texto girado usando um RotateTransform](./media/how-to-apply-transforms-to-text/text-rotated-ninety-degrees.jpg)  
  
 <span data-ttu-id="94a77-108">O seguinte exemplo de código usa um <xref:System.Windows.Media.RotateTransform> para girar o texto.</span><span class="sxs-lookup"><span data-stu-id="94a77-108">The following code example uses a <xref:System.Windows.Media.RotateTransform> to rotate text.</span></span> <span data-ttu-id="94a77-109">Um <xref:System.Windows.Media.RotateTransform.Angle%2A> valor de 90 gira o elemento 90 graus no sentido horário.</span><span class="sxs-lookup"><span data-stu-id="94a77-109">An <xref:System.Windows.Media.RotateTransform.Angle%2A> value of 90 rotates the element 90 degrees clockwise.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 <span data-ttu-id="94a77-110">O exemplo a seguir mostra a segunda linha de texto com escala ajustada em 150% no eixo x e a terceira linha de texto ajustada em 150% no eixo y.</span><span class="sxs-lookup"><span data-stu-id="94a77-110">The following example shows the second line of text scaled by 150% along the x-axis, and the third line of text scaled by 150% along the y-axis.</span></span>  
  
 ![Texto com escala ajustada usando um ScaleTransform](./media/how-to-apply-transforms-to-text/scaled-text-scaletransform.jpg) 
  
 <span data-ttu-id="94a77-112">O seguinte exemplo de código usa um <xref:System.Windows.Media.ScaleTransform> ao texto de escala do seu tamanho original.</span><span class="sxs-lookup"><span data-stu-id="94a77-112">The following code example uses a <xref:System.Windows.Media.ScaleTransform> to scale text from its original size.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
>  <span data-ttu-id="94a77-113">Dimensionar o texto não é igual a aumentar o tamanho da fonte do texto.</span><span class="sxs-lookup"><span data-stu-id="94a77-113">Scaling text is not the same as increasing the font size of text.</span></span> <span data-ttu-id="94a77-114">Tamanhos de fonte são calculados independentemente uns dos outros a fim de fornecer a melhor resolução em tamanhos diferentes.</span><span class="sxs-lookup"><span data-stu-id="94a77-114">Font sizes are calculated independently of each other in order to provide the best resolution at different sizes.</span></span> <span data-ttu-id="94a77-115">O texto com escala ajustada, por outro lado, preserva as proporções do texto em seu tamanho original.</span><span class="sxs-lookup"><span data-stu-id="94a77-115">Scaled text, on the other hand, preserves the proportions of the original-sized text.</span></span>  
  
 <span data-ttu-id="94a77-116">O exemplo a seguir mostra texto distorcido ao longo do eixo x.</span><span class="sxs-lookup"><span data-stu-id="94a77-116">The following example shows text skewed along the x-axis.</span></span>  
  
 ![Texto distorcido usando SkewTransform](./media/how-to-apply-transforms-to-text/skewed-transformed-text.jpg)
   
 <span data-ttu-id="94a77-118">O seguinte exemplo de código usa um <xref:System.Windows.Media.SkewTransform> para distorcer o texto.</span><span class="sxs-lookup"><span data-stu-id="94a77-118">The following code example uses a <xref:System.Windows.Media.SkewTransform> to skew text.</span></span> <span data-ttu-id="94a77-119">Uma distorção, também conhecido como uma inclinação, é uma transformação que alonga o espaço de coordenadas de maneira não uniforme.</span><span class="sxs-lookup"><span data-stu-id="94a77-119">A skew, also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="94a77-120">Neste exemplo, as duas cadeias de caracteres de texto são distorcidas-30° e 30° na coordenada X.</span><span class="sxs-lookup"><span data-stu-id="94a77-120">In this example, the two text strings are skewed -30° and 30° along the x-coordinate.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 <span data-ttu-id="94a77-121">O exemplo a seguir mostra o texto movido, ou deslocado, nos eixos x e y.</span><span class="sxs-lookup"><span data-stu-id="94a77-121">The following example shows text translated, or moved, along the x- and y-axis.</span></span>  
  
 ![Deslocamento de texto usando TranslateTransform](./media/how-to-apply-transforms-to-text/transformed-text-x-y-axis.jpg)
  
 <span data-ttu-id="94a77-123">O seguinte exemplo de código usa um <xref:System.Windows.Media.TranslateTransform> para deslocar o texto.</span><span class="sxs-lookup"><span data-stu-id="94a77-123">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="94a77-124">Neste exemplo, uma cópia ligeiramente deslocada de texto abaixo do texto primário cria um efeito de sombra.</span><span class="sxs-lookup"><span data-stu-id="94a77-124">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
>  <span data-ttu-id="94a77-125">O <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> fornece um conjunto avançado de recursos para criar efeitos de sombra.</span><span class="sxs-lookup"><span data-stu-id="94a77-125">The <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> provides a rich set of features for providing shadow effects.</span></span> <span data-ttu-id="94a77-126">Para obter mais informações, consulte [criar texto com uma sombra](how-to-create-text-with-a-shadow.md).</span><span class="sxs-lookup"><span data-stu-id="94a77-126">For more information, see [Create Text with a Shadow](how-to-create-text-with-a-shadow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94a77-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="94a77-127">See also</span></span>
- [<span data-ttu-id="94a77-128">Aplicar animações ao texto</span><span class="sxs-lookup"><span data-stu-id="94a77-128">Apply Animations to Text</span></span>](how-to-apply-animations-to-text.md)
