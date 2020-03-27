---
title: Como animar a espessura de uma borda usando quadros-chave
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], border thickness with key frames
- key frames [WPF], animating border thickness with
- border thickness [WPF], animating with key frames
ms.assetid: 3a9cb463-0a63-407d-aae7-3fbb1a559947
ms.openlocfilehash: 884b62e88c347449ae39caa9c028d09db39b9f4b
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344699"
---
# <a name="how-to-animate-the-thickness-of-a-border-by-using-key-frames"></a><span data-ttu-id="17d7b-102">Como animar a espessura de uma borda usando quadros-chave</span><span class="sxs-lookup"><span data-stu-id="17d7b-102">How to: Animate the Thickness of a Border by Using Key Frames</span></span>
<span data-ttu-id="17d7b-103">Este exemplo mostra como <xref:System.Windows.Controls.Control.BorderThickness%2A> animar a <xref:System.Windows.Controls.Border>propriedade de um .</span><span class="sxs-lookup"><span data-stu-id="17d7b-103">This example shows how to animate the <xref:System.Windows.Controls.Control.BorderThickness%2A> property of a <xref:System.Windows.Controls.Border>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17d7b-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="17d7b-104">Example</span></span>  
 <span data-ttu-id="17d7b-105">O exemplo a <xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames> seguir usa <xref:System.Windows.Controls.Control.BorderThickness%2A> a classe <xref:System.Windows.Controls.Border>para animar a propriedade de um .</span><span class="sxs-lookup"><span data-stu-id="17d7b-105">The following example uses the <xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Controls.Control.BorderThickness%2A> property of a <xref:System.Windows.Controls.Border>.</span></span> <span data-ttu-id="17d7b-106">Essa animação usa três quadros-chave da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="17d7b-106">This animation uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="17d7b-107">Durante a primeira metade do segundo, usa uma instância da <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> classe para aumentar gradualmente a espessura da borda.</span><span class="sxs-lookup"><span data-stu-id="17d7b-107">During the first half second, uses an instance of the <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> class to gradually increase the thickness of the border.</span></span> <span data-ttu-id="17d7b-108">O exemplo <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> é usar para criar um aumento linear suave entre os valores.</span><span class="sxs-lookup"><span data-stu-id="17d7b-108">The example uses <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> to create a smooth linear increase between values.</span></span>  
  
2. <span data-ttu-id="17d7b-109">No final da próxima metade do segundo, <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> usa uma instância da classe para aumentar repentinamente a espessura da borda.</span><span class="sxs-lookup"><span data-stu-id="17d7b-109">At the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> class to suddenly increase the thickness of the border.</span></span> <span data-ttu-id="17d7b-110">Quadros-chave discretos como os <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> derivados criam saltos repentinos entre os valores, ou seja, o movimento da animação é jerky.</span><span class="sxs-lookup"><span data-stu-id="17d7b-110">Discrete key frames like those derived from <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
3. <span data-ttu-id="17d7b-111">Durante os dois segundos finais, <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> usa uma instância da classe para diminuir a espessura da borda.</span><span class="sxs-lookup"><span data-stu-id="17d7b-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> class to decrease the thickness of the border.</span></span> <span data-ttu-id="17d7b-112">Quadros-chave spline como <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> os derivados criam uma transição <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A> variável entre valores de acordo com os valores da propriedade.</span><span class="sxs-lookup"><span data-stu-id="17d7b-112">Spline key frames like those derived from <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="17d7b-113">Neste quadro-chave, a animação começa lentamente e acelera exponencialmente na direção do final do segmento de tempo.</span><span class="sxs-lookup"><span data-stu-id="17d7b-113">In this key frame, the animation starts off slow and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-xaml[keyframes_snip#ThicknessAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ThicknessAnimationUsingKeyFramesExample.xaml#thicknessanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="17d7b-114">Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span><span class="sxs-lookup"><span data-stu-id="17d7b-114">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17d7b-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="17d7b-115">See also</span></span>

- <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>
- <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>
- [<span data-ttu-id="17d7b-116">Visão geral das animações de quadro-chave</span><span class="sxs-lookup"><span data-stu-id="17d7b-116">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="17d7b-117">Tópicos explicativos sobre quadros-chave</span><span class="sxs-lookup"><span data-stu-id="17d7b-117">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
- [<span data-ttu-id="17d7b-118">Animar um valor de BorderThickness</span><span class="sxs-lookup"><span data-stu-id="17d7b-118">Animate a BorderThickness Value</span></span>](../controls/how-to-animate-a-borderthickness-value.md)
