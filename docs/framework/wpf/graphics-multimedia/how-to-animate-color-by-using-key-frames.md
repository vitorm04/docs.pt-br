---
title: Como animar cor usando quadros-chave
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [WPF], animating with key frames
- animation [WPF], colors with key frames
- key frames [WPF], animating colors with
ms.assetid: ab04ffa6-4de9-4d5b-a3b4-4e35d5b2ef35
ms.openlocfilehash: 8a444706f7541b52722ab8257a88e76c3e1b0938
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344745"
---
# <a name="how-to-animate-color-by-using-key-frames"></a><span data-ttu-id="23465-102">Como animar cor usando quadros-chave</span><span class="sxs-lookup"><span data-stu-id="23465-102">How to: Animate Color by Using Key Frames</span></span>
<span data-ttu-id="23465-103">Este exemplo mostra como <xref:System.Windows.Media.SolidColorBrush.Color%2A> animar <xref:System.Windows.Media.SolidColorBrush> a de a usando quadros-chave.</span><span class="sxs-lookup"><span data-stu-id="23465-103">This example shows how to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> of a <xref:System.Windows.Media.SolidColorBrush> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23465-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="23465-104">Example</span></span>  
 <span data-ttu-id="23465-105">O exemplo a <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames> seguir usa <xref:System.Windows.Media.SolidColorBrush.Color%2A> a classe <xref:System.Windows.Media.SolidColorBrush>para animar a propriedade de um .</span><span class="sxs-lookup"><span data-stu-id="23465-105">The following example uses the <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> property of a <xref:System.Windows.Media.SolidColorBrush>.</span></span> <span data-ttu-id="23465-106">Essa animação usa três quadros-chave da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="23465-106">This animation uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="23465-107">Durante os dois primeiros segundos, <xref:System.Windows.Media.Animation.LinearColorKeyFrame> usa uma instância da classe para mudar gradualmente a cor de verde para vermelho.</span><span class="sxs-lookup"><span data-stu-id="23465-107">During the first two seconds, uses an instance of the <xref:System.Windows.Media.Animation.LinearColorKeyFrame> class to gradually change the color from green to red.</span></span> <span data-ttu-id="23465-108">Quadros de <xref:System.Windows.Media.Animation.LinearColorKeyFrame> chaves lineares como criar uma transição linear suave entre os valores.</span><span class="sxs-lookup"><span data-stu-id="23465-108">Linear key frames like <xref:System.Windows.Media.Animation.LinearColorKeyFrame> create a smooth linear transition between values.</span></span>  
  
2. <span data-ttu-id="23465-109">Durante o final do segundo seguinte, usa <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> uma instância da classe para mudar rapidamente a cor de vermelho para amarelo.</span><span class="sxs-lookup"><span data-stu-id="23465-109">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> class to quickly change the color from red to yellow.</span></span> <span data-ttu-id="23465-110">Quadros-chave discretos <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> como criar mudanças bruscas entre valores, ou seja, a mudança de cor nesta parte da animação ocorre rapidamente e não é sutil.</span><span class="sxs-lookup"><span data-stu-id="23465-110">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> create sudden changes between values, that is, the color change in this part of the animation occurs quickly and is not subtle.</span></span>  
  
3. <span data-ttu-id="23465-111">Durante os dois segundos finais, <xref:System.Windows.Media.Animation.SplineColorKeyFrame> usa uma instância da classe para mudar a cor novamente — desta vez de amarelo de volta para verde.</span><span class="sxs-lookup"><span data-stu-id="23465-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineColorKeyFrame> class to change the color again—this time from yellow back to green.</span></span> <span data-ttu-id="23465-112">Quadros-chave spline como <xref:System.Windows.Media.Animation.SplineColorKeyFrame> criar uma transição variável <xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A> entre valores de acordo com os valores da propriedade.</span><span class="sxs-lookup"><span data-stu-id="23465-112">Spline key frames like <xref:System.Windows.Media.Animation.SplineColorKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="23465-113">Neste exemplo, a alteração na cor começa lentamente e acelera exponencialmente na direção do final do segmento de tempo.</span><span class="sxs-lookup"><span data-stu-id="23465-113">In this example, the change in color begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/ColorAnimationUsingKeyFramesExample.cs#coloranimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/coloranimationusingkeyframesexample.vb#coloranimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ColorAnimationUsingKeyFramesExample.xaml#coloranimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="23465-114">Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span><span class="sxs-lookup"><span data-stu-id="23465-114">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23465-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="23465-115">See also</span></span>

- <xref:System.Windows.Media.SolidColorBrush.Color%2A>
- <xref:System.Windows.Media.SolidColorBrush>
- <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>
- [<span data-ttu-id="23465-116">Visão geral das animações de quadro-chave</span><span class="sxs-lookup"><span data-stu-id="23465-116">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="23465-117">Tópicos explicativos sobre quadros-chave</span><span class="sxs-lookup"><span data-stu-id="23465-117">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
