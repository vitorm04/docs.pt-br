---
title: 'Como: Animar alterações de tamanho usando quadros principais'
ms.date: 03/30/2017
helpviewer_keywords:
- key frames [WPF], animating size changes with
- animation [WPF], size changes with key frames
- size changes [WPF], animating with key frames
ms.assetid: 86bd2950-d4c9-4ec4-aa8d-7dc3ccadded4
ms.openlocfilehash: a7adb16297f50e191628344d7e25d41f38a97861
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180226"
---
# <a name="how-to-animate-size-changes-by-using-key-frames"></a><span data-ttu-id="9ec21-102">Como: Animar alterações de tamanho usando quadros principais</span><span class="sxs-lookup"><span data-stu-id="9ec21-102">How to: Animate Size Changes by Using Key Frames</span></span>
<span data-ttu-id="9ec21-103">Esse exemplo demonstra como animar alterações de tamanho usando quadros-chave.</span><span class="sxs-lookup"><span data-stu-id="9ec21-103">This example shows how to animate size changes by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ec21-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9ec21-104">Example</span></span>  
 <span data-ttu-id="9ec21-105">O exemplo a seguir usa o <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> classe para animar a <xref:System.Windows.Media.ArcSegment.Size%2A> propriedade de um <xref:System.Windows.Media.ArcSegment>.</span><span class="sxs-lookup"><span data-stu-id="9ec21-105">The following example uses the <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.ArcSegment.Size%2A> property of an <xref:System.Windows.Media.ArcSegment>.</span></span> <span data-ttu-id="9ec21-106">Essa animação usa três quadros-chave da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="9ec21-106">This animation uses three key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="9ec21-107">Durante o primeiro meio segundo da animação, usa uma instância da <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> classe para aumentar gradualmente o tamanho do arco. Quadros-chave lineares como <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> criam uma transição linear suave entre valores.</span><span class="sxs-lookup"><span data-stu-id="9ec21-107">During the first half second of the animation, uses an instance of the <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> class to gradually increase the size of the arc. Linear key frames like <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> create a smooth linear transition between values.</span></span>  
  
2.  <span data-ttu-id="9ec21-108">No final do próximo meio segundo, usa uma instância da <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> classe, de repente, aumentar o tamanho do arco. Quadros chave discretos como <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> criam saltos repentinos entre valores, ou seja, as alterações de tamanho ocorrem repentinamente e não são sutis.</span><span class="sxs-lookup"><span data-stu-id="9ec21-108">At the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> class to suddenly increase the size of the arc. Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> create sudden jumps between values, that is, the size changes occur suddenly and are not subtle.</span></span>  
  
3.  <span data-ttu-id="9ec21-109">Sobre os dois segundos finais, usa uma instância da <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> classe para aumentar o tamanho do arco. Como quadros-chave spline <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> criam uma transição variável entre valores de acordo com os valores da <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="9ec21-109">Over the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> class to increase the size of the arc. Spline key frames like <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="9ec21-110">Neste exemplo, o tamanho do arco aumenta lentamente no início e aumenta exponencialmente até o final do segmento de tempo.</span><span class="sxs-lookup"><span data-stu-id="9ec21-110">In this example, the size of the arc increases slowly at first and then increases exponentially toward the end of the time segment.</span></span>  
  
 [!code-xaml[keyframes_snip#SizeAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/SizeAnimationUsingKeyFramesExample.xaml#sizeanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="9ec21-111">Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="9ec21-111">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ec21-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9ec21-112">See also</span></span>

- <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>
- <xref:System.Windows.Media.ArcSegment.Size%2A>
- <xref:System.Windows.Media.ArcSegment>
- <xref:System.Windows.Media.Animation.LinearSizeKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>
- <xref:System.Windows.Media.Animation.SplineSizeKeyFrame>
- [<span data-ttu-id="9ec21-113">Visão geral das animações de quadro-chave</span><span class="sxs-lookup"><span data-stu-id="9ec21-113">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="9ec21-114">Tópicos explicativos sobre quadros-chave</span><span class="sxs-lookup"><span data-stu-id="9ec21-114">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
