---
title: Como animar alterações de tamanho usando quadros-chave
ms.date: 03/30/2017
helpviewer_keywords:
- key frames [WPF], animating size changes with
- animation [WPF], size changes with key frames
- size changes [WPF], animating with key frames
ms.assetid: 86bd2950-d4c9-4ec4-aa8d-7dc3ccadded4
ms.openlocfilehash: 42cecfc9df4304be4033ea39edc0517016de4a92
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344643"
---
# <a name="how-to-animate-size-changes-by-using-key-frames"></a><span data-ttu-id="e073b-102">Como animar alterações de tamanho usando quadros-chave</span><span class="sxs-lookup"><span data-stu-id="e073b-102">How to: Animate Size Changes by Using Key Frames</span></span>
<span data-ttu-id="e073b-103">Esse exemplo demonstra como animar alterações de tamanho usando quadros-chave.</span><span class="sxs-lookup"><span data-stu-id="e073b-103">This example shows how to animate size changes by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e073b-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e073b-104">Example</span></span>  
 <span data-ttu-id="e073b-105">O exemplo a <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> seguir usa <xref:System.Windows.Media.ArcSegment.Size%2A> a classe <xref:System.Windows.Media.ArcSegment>para animar a propriedade de um .</span><span class="sxs-lookup"><span data-stu-id="e073b-105">The following example uses the <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.ArcSegment.Size%2A> property of an <xref:System.Windows.Media.ArcSegment>.</span></span> <span data-ttu-id="e073b-106">Essa animação usa três quadros-chave da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="e073b-106">This animation uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="e073b-107">Durante a primeira metade da animação, usa <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> uma instância da classe para aumentar gradualmente o tamanho do arco. Quadros de <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> chaves lineares como criar uma transição linear suave entre os valores.</span><span class="sxs-lookup"><span data-stu-id="e073b-107">During the first half second of the animation, uses an instance of the <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> class to gradually increase the size of the arc. Linear key frames like <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> create a smooth linear transition between values.</span></span>  
  
2. <span data-ttu-id="e073b-108">No final da próxima metade do segundo, <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> usa uma instância da classe para aumentar repentinamente o tamanho do arco. Quadros-chave discretos <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> como criar saltos repentinos entre os valores, ou seja, as mudanças de tamanho ocorrem de repente e não são sutis.</span><span class="sxs-lookup"><span data-stu-id="e073b-108">At the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> class to suddenly increase the size of the arc. Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> create sudden jumps between values, that is, the size changes occur suddenly and are not subtle.</span></span>  
  
3. <span data-ttu-id="e073b-109">Nos dois segundos finais, usa <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> uma instância da classe para aumentar o tamanho do arco. Quadros-chave spline como <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> criar uma transição variável <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> entre valores de acordo com os valores da propriedade.</span><span class="sxs-lookup"><span data-stu-id="e073b-109">Over the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> class to increase the size of the arc. Spline key frames like <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="e073b-110">Neste exemplo, o tamanho do arco aumenta lentamente no início e aumenta exponencialmente até o final do segmento de tempo.</span><span class="sxs-lookup"><span data-stu-id="e073b-110">In this example, the size of the arc increases slowly at first and then increases exponentially toward the end of the time segment.</span></span>  
  
 [!code-xaml[keyframes_snip#SizeAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/SizeAnimationUsingKeyFramesExample.xaml#sizeanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="e073b-111">Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span><span class="sxs-lookup"><span data-stu-id="e073b-111">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e073b-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="e073b-112">See also</span></span>

- <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>
- <xref:System.Windows.Media.ArcSegment.Size%2A>
- <xref:System.Windows.Media.ArcSegment>
- <xref:System.Windows.Media.Animation.LinearSizeKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>
- <xref:System.Windows.Media.Animation.SplineSizeKeyFrame>
- [<span data-ttu-id="e073b-113">Visão geral das animações de quadro-chave</span><span class="sxs-lookup"><span data-stu-id="e073b-113">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="e073b-114">Tópicos explicativos sobre quadros-chave</span><span class="sxs-lookup"><span data-stu-id="e073b-114">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
