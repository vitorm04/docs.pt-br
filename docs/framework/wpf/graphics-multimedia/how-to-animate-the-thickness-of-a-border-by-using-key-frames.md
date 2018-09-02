---
title: Como animar a espessura de uma borda usando quadros-chave
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], border thickness with key frames
- key frames [WPF], animating border thickness with
- border thickness [WPF], animating with key frames
ms.assetid: 3a9cb463-0a63-407d-aae7-3fbb1a559947
ms.openlocfilehash: a601fd6779a4d912166366652435aff9ae37613f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43421404"
---
# <a name="how-to-animate-the-thickness-of-a-border-by-using-key-frames"></a><span data-ttu-id="887a9-102">Como animar a espessura de uma borda usando quadros-chave</span><span class="sxs-lookup"><span data-stu-id="887a9-102">How to: Animate the Thickness of a Border by Using Key Frames</span></span>
<span data-ttu-id="887a9-103">Este exemplo mostra como animar a <xref:System.Windows.Controls.Control.BorderThickness%2A> propriedade de um <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="887a9-103">This example shows how to animate the <xref:System.Windows.Controls.Control.BorderThickness%2A> property of a <xref:System.Windows.Controls.Border>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="887a9-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="887a9-104">Example</span></span>  
 <span data-ttu-id="887a9-105">O exemplo a seguir usa o <xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames> classe para animar a <xref:System.Windows.Controls.Control.BorderThickness%2A> propriedade de um <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="887a9-105">The following example uses the <xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Controls.Control.BorderThickness%2A> property of a <xref:System.Windows.Controls.Border>.</span></span> <span data-ttu-id="887a9-106">Essa animação usa três quadros-chave da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="887a9-106">This animation uses three key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="887a9-107">Durante o primeiro meio segundo, usa uma instância da <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> classe para aumentar gradualmente a espessura da borda.</span><span class="sxs-lookup"><span data-stu-id="887a9-107">During the first half second, uses an instance of the <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> class to gradually increase the thickness of the border.</span></span> <span data-ttu-id="887a9-108">O exemplo usa <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> para criar um aumento linear suave entre valores.</span><span class="sxs-lookup"><span data-stu-id="887a9-108">The example uses <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> to create a smooth linear increase between values.</span></span>  
  
2.  <span data-ttu-id="887a9-109">No final do próximo meio segundo, usa uma instância da <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> classe para aumentar repentinamente a espessura da borda.</span><span class="sxs-lookup"><span data-stu-id="887a9-109">At the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> class to suddenly increase the thickness of the border.</span></span> <span data-ttu-id="887a9-110">Quadros chave discretos como aqueles derivam <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> criam saltos repentinos entre valores, ou seja, o movimento da animação é brusco.</span><span class="sxs-lookup"><span data-stu-id="887a9-110">Discrete key frames like those derived from <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
3.  <span data-ttu-id="887a9-111">Durante os dois segundos finais, usa uma instância da <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> classe para diminuir a espessura da borda.</span><span class="sxs-lookup"><span data-stu-id="887a9-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> class to decrease the thickness of the border.</span></span> <span data-ttu-id="887a9-112">Quadros-chave spline, como aqueles derivam <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> criam uma transição variável entre valores de acordo com os valores da <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="887a9-112">Spline key frames like those derived from <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="887a9-113">Neste quadro-chave, a animação começa lentamente e acelera exponencialmente na direção do final do segmento de tempo.</span><span class="sxs-lookup"><span data-stu-id="887a9-113">In this key frame, the animation starts off slow and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-xaml[keyframes_snip#ThicknessAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ThicknessAnimationUsingKeyFramesExample.xaml#thicknessanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="887a9-114">Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="887a9-114">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="887a9-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="887a9-115">See Also</span></span>  
 <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>  
 <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>  
 <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>  
 [<span data-ttu-id="887a9-116">Visão geral das animações de quadro-chave</span><span class="sxs-lookup"><span data-stu-id="887a9-116">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="887a9-117">Tópicos explicativos sobre quadros-chave</span><span class="sxs-lookup"><span data-stu-id="887a9-117">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)  
 [<span data-ttu-id="887a9-118">Animar um valor de BorderThickness</span><span class="sxs-lookup"><span data-stu-id="887a9-118">Animate a BorderThickness Value</span></span>](../../../../docs/framework/wpf/controls/how-to-animate-a-borderthickness-value.md)
