---
title: Como animar um duplo usando quadros-chave
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Doubles [WPF], animating with key frames
- animation [WPF], Doubles with key frames
- key frames [WPF], animating Doubles with
ms.assetid: 3a1a7dba-7694-4907-8a2f-3408baebfa82
ms.openlocfilehash: 9eab794cc8411230226cddc97beaa13c1bdd9405
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344925"
---
# <a name="how-to-animate-a-double-by-using-key-frames"></a><span data-ttu-id="e1689-102">Como animar um duplo usando quadros-chave</span><span class="sxs-lookup"><span data-stu-id="e1689-102">How to: Animate a Double by Using Key Frames</span></span>
<span data-ttu-id="e1689-103">Este exemplo mostra como animar o valor de <xref:System.Double> uma propriedade que leva a usando quadros-chave.</span><span class="sxs-lookup"><span data-stu-id="e1689-103">This example shows how to animate the value of a property that takes a <xref:System.Double> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1689-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e1689-104">Example</span></span>  
 <span data-ttu-id="e1689-105">O exemplo a seguir move um retângulo por uma tela.</span><span class="sxs-lookup"><span data-stu-id="e1689-105">The following example moves a rectangle across a screen.</span></span> <span data-ttu-id="e1689-106">O exemplo <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> usa a classe <xref:System.Windows.Media.TranslateTransform.X%2A> para <xref:System.Windows.Media.TranslateTransform> animar a <xref:System.Windows.Shapes.Rectangle>propriedade de um aplicado a um .</span><span class="sxs-lookup"><span data-stu-id="e1689-106">The example uses the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.TranslateTransform.X%2A> property of a <xref:System.Windows.Media.TranslateTransform> applied to a <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="e1689-107">Essa animação, que se repete indefinidamente, usa três quadros chave da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="e1689-107">This animation, which repeats indefinitely, uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="e1689-108">Durante os primeiros três segundos, <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> usa uma instância da classe para mover o retângulo ao longo de um caminho a uma taxa constante de sua posição inicial para a posição de 500.</span><span class="sxs-lookup"><span data-stu-id="e1689-108">During the first three seconds, uses an instance of the <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> class to move the rectangle along a path at a steady rate from its starting position to the 500 position.</span></span> <span data-ttu-id="e1689-109">Quadros de <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> chaves lineares como criar uma transição linear suave entre os valores.</span><span class="sxs-lookup"><span data-stu-id="e1689-109">Linear key frames like <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> create a smooth linear transition between values.</span></span>  
  
2. <span data-ttu-id="e1689-110">No final do quarto segundo, usa <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> uma instância da classe para de repente mover o retângulo para a próxima posição.</span><span class="sxs-lookup"><span data-stu-id="e1689-110">At the end of the fourth second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> class to suddenly move the rectangle to the next position.</span></span> <span data-ttu-id="e1689-111">Quadros-chave discretos <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> como criar saltos repentinos entre os valores.</span><span class="sxs-lookup"><span data-stu-id="e1689-111">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> create sudden jumps between values.</span></span> <span data-ttu-id="e1689-112">Neste exemplo, o retângulo está na posição inicial e, de repente, aparece na posição 500.</span><span class="sxs-lookup"><span data-stu-id="e1689-112">In this example, the rectangle is at the starting position and then suddenly appears at the 500 position.</span></span>  
  
3. <span data-ttu-id="e1689-113">Nos dois segundos finais, usa <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> uma instância da classe para mover o retângulo de volta para sua posição inicial.</span><span class="sxs-lookup"><span data-stu-id="e1689-113">In the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> class to move the rectangle back to its starting position.</span></span> <span data-ttu-id="e1689-114">Quadros-chave spline como <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> criar uma transição variável <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A> entre valores de acordo com o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="e1689-114">Spline key frames like <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> create a variable transition between values according to the value of the <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="e1689-115">Neste exemplo, o retângulo começa a se mover lentamente e acelera exponencialmente em direção ao final do segmento de tempo.</span><span class="sxs-lookup"><span data-stu-id="e1689-115">In this example, the rectangle begins by moving slowly and then speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/AltDoubleAnimationUsingKeyFramesExample.cs#altdoubleanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/altdoubleanimationusingkeyframesexample.vb#altdoubleanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/AltDoubleAnimationUsingKeyFramesExample.xaml#altdoubleanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="e1689-116">Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span><span class="sxs-lookup"><span data-stu-id="e1689-116">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
 <span data-ttu-id="e1689-117">Para obter consistência com outros exemplos de animação, <xref:System.Windows.Media.Animation.Storyboard> as versões de código deste exemplo usam um objeto para aplicar o <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.</span><span class="sxs-lookup"><span data-stu-id="e1689-117">For consistency with other animation examples, the code versions of this example use a <xref:System.Windows.Media.Animation.Storyboard> object to apply the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.</span></span> <span data-ttu-id="e1689-118">Alternativamente, ao aplicar uma única animação em código, <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> é mais <xref:System.Windows.Media.Animation.Storyboard>simples usar o método em vez de usar um .</span><span class="sxs-lookup"><span data-stu-id="e1689-118">Alternatively, when applying a single animation in code, it is simpler to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method instead of using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="e1689-119">Por exemplo, consulte [Animar uma propriedade sem usar um storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="e1689-119">For an example, see [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1689-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="e1689-120">See also</span></span>

- <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>
- <xref:System.Windows.Shapes.Rectangle>
- <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>
- <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>
- [<span data-ttu-id="e1689-121">Visão geral das animações de quadro-chave</span><span class="sxs-lookup"><span data-stu-id="e1689-121">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="e1689-122">Tópicos explicativos sobre quadros-chave</span><span class="sxs-lookup"><span data-stu-id="e1689-122">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
