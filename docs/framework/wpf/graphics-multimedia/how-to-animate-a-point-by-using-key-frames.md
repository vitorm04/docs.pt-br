---
title: Como animar um ponto usando quadros-chave
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating Points with
- Points [WPF], animating with key frames
- animation [WPF], Points with key frames
ms.assetid: d2e2ef10-0773-4133-856e-d41c09f60ded
ms.openlocfilehash: edcba36644cf78d6e98f934d9bd8b593af38b328
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344875"
---
# <a name="how-to-animate-a-point-by-using-key-frames"></a><span data-ttu-id="ecb09-102">Como animar um ponto usando quadros-chave</span><span class="sxs-lookup"><span data-stu-id="ecb09-102">How to: Animate a Point by Using Key Frames</span></span>
<span data-ttu-id="ecb09-103">Este exemplo mostra como <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> usar a <xref:System.Windows.Point>classe para animar um .</span><span class="sxs-lookup"><span data-stu-id="ecb09-103">This example shows how to use the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> class to animate a <xref:System.Windows.Point>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ecb09-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ecb09-104">Example</span></span>  
 <span data-ttu-id="ecb09-105">O exemplo a seguir move uma elipse ao longo de um caminho triangular.</span><span class="sxs-lookup"><span data-stu-id="ecb09-105">The following example moves an ellipse along a triangular path.</span></span> <span data-ttu-id="ecb09-106">O exemplo <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> usa a classe <xref:System.Windows.Media.EllipseGeometry.Center%2A> para <xref:System.Windows.Media.EllipseGeometry>animar a propriedade de um .</span><span class="sxs-lookup"><span data-stu-id="ecb09-106">The example uses the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.EllipseGeometry.Center%2A> property of an <xref:System.Windows.Media.EllipseGeometry>.</span></span> <span data-ttu-id="ecb09-107">Essa animação usa três quadros-chave da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="ecb09-107">This animation uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="ecb09-108">Durante a primeira metade do segundo, usa uma instância da <xref:System.Windows.Media.Animation.LinearPointKeyFrame> classe para mover a elipse ao longo de um caminho a uma taxa constante de sua posição inicial.</span><span class="sxs-lookup"><span data-stu-id="ecb09-108">During the first half second, uses an instance of the <xref:System.Windows.Media.Animation.LinearPointKeyFrame> class to move the ellipse along a path at a steady rate from its starting position.</span></span> <span data-ttu-id="ecb09-109">Quadros de <xref:System.Windows.Media.Animation.LinearPointKeyFrame> tecla lineares como criar uma interpolação linear suave entre valores.</span><span class="sxs-lookup"><span data-stu-id="ecb09-109">Linear key frames like <xref:System.Windows.Media.Animation.LinearPointKeyFrame> create a smooth linear interpolation between values.</span></span>  
  
2. <span data-ttu-id="ecb09-110">Durante o final da próxima metade do <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> segundo, usa uma instância da classe para de repente mover a elipse ao longo do caminho para a próxima posição.</span><span class="sxs-lookup"><span data-stu-id="ecb09-110">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> class to suddenly move the ellipse along the path to the next position.</span></span> <span data-ttu-id="ecb09-111">Quadros-chave discretos <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> como criar saltos repentinos entre os valores.</span><span class="sxs-lookup"><span data-stu-id="ecb09-111">Discrete key frames like <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> create sudden jumps between values.</span></span>  
  
3. <span data-ttu-id="ecb09-112">Durante os dois segundos finais, <xref:System.Windows.Media.Animation.SplinePointKeyFrame> usa uma instância da classe para mover a elipse de volta à sua posição inicial.</span><span class="sxs-lookup"><span data-stu-id="ecb09-112">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplinePointKeyFrame> class to move the ellipse back to its starting position.</span></span> <span data-ttu-id="ecb09-113">Quadros-chave spline como <xref:System.Windows.Media.Animation.SplinePointKeyFrame> criar uma transição variável <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> entre valores de acordo com os valores da propriedade.</span><span class="sxs-lookup"><span data-stu-id="ecb09-113">Spline key frames like <xref:System.Windows.Media.Animation.SplinePointKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="ecb09-114">Neste exemplo, a animação começa lentamente e acelera exponencialmente na direção do final do segmento de tempo.</span><span class="sxs-lookup"><span data-stu-id="ecb09-114">In this example, the animation begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/PointAnimationUsingKeyFramesExample.cs#pointanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/pointanimationusingkeyframesexample.vb#pointanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/PointAnimationUsingKeyFramesExample.xaml#pointanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="ecb09-115">Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span><span class="sxs-lookup"><span data-stu-id="ecb09-115">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
 <span data-ttu-id="ecb09-116">Para obter consistência com outros exemplos de animação, <xref:System.Windows.Media.Animation.Storyboard> as versões de código deste exemplo usam um objeto para aplicar o <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>.</span><span class="sxs-lookup"><span data-stu-id="ecb09-116">For consistency with other animation examples, the code versions of this example use a <xref:System.Windows.Media.Animation.Storyboard> object to apply the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>.</span></span> <span data-ttu-id="ecb09-117">No entanto, ao aplicar uma única animação em <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> código, é <xref:System.Windows.Media.Animation.Storyboard>mais simples usar o método em vez de usar um .</span><span class="sxs-lookup"><span data-stu-id="ecb09-117">However, when applying a single animation in code, it's simpler to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method instead of using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="ecb09-118">Por exemplo, consulte [Animar uma propriedade sem usar um storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="ecb09-118">For an example, see [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecb09-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="ecb09-119">See also</span></span>

- <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>
- <xref:System.Windows.Media.EllipseGeometry.Center%2A?displayProperty=nameWithType>
- <xref:System.Windows.Media.EllipseGeometry>
- [<span data-ttu-id="ecb09-120">Visão geral das animações de quadro-chave</span><span class="sxs-lookup"><span data-stu-id="ecb09-120">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="ecb09-121">Tópicos explicativos sobre quadros-chave</span><span class="sxs-lookup"><span data-stu-id="ecb09-121">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
