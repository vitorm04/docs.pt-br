---
title: Como animar um valor booliano usando quadros-chave
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Booleans [WPF], animating with key frames
- animation [WPF], Booleans with key frames
- key frames [WPF], animating Booleans with
ms.assetid: 4b0fac96-6231-4fcf-9775-4dd673ddc785
ms.openlocfilehash: 35704996dcf21fe463169dc13572941bcd8fbad1
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344930"
---
# <a name="how-to-animate-a-boolean-by-using-key-frames"></a><span data-ttu-id="1471b-102">Como animar um valor booliano usando quadros-chave</span><span class="sxs-lookup"><span data-stu-id="1471b-102">How to: Animate a Boolean by Using Key Frames</span></span>
<span data-ttu-id="1471b-103">Este exemplo mostra como animar o valor <xref:System.Windows.Controls.Button> de propriedade booleana de um controle usando quadros-chave.</span><span class="sxs-lookup"><span data-stu-id="1471b-103">This example shows how to animate the Boolean property value of a <xref:System.Windows.Controls.Button> control by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1471b-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1471b-104">Example</span></span>  
 <span data-ttu-id="1471b-105">O exemplo a <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames> seguir usa <xref:System.Windows.UIElement.IsEnabled%2A> a classe <xref:System.Windows.Controls.Button> para animar a propriedade de um controle.</span><span class="sxs-lookup"><span data-stu-id="1471b-105">The following example uses the <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames> class to animate the <xref:System.Windows.UIElement.IsEnabled%2A> property of a <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="1471b-106">Todos os quadros-chave neste exemplo <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> usam uma instância da classe.</span><span class="sxs-lookup"><span data-stu-id="1471b-106">All the key frames in this example use an instance of the <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> class.</span></span> <span data-ttu-id="1471b-107">Quadros-chave discretos <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> como criar saltos repentinos entre os valores, ou seja, o movimento da animação é jerky.</span><span class="sxs-lookup"><span data-stu-id="1471b-107">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
 [!code-csharp[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/BooleanAnimationUsingKeyFramesExample.cs#booleananimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/booleananimationusingkeyframesexample.vb#booleananimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/BooleanAnimationUsingKeyFramesExample.xaml#booleananimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="1471b-108">Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span><span class="sxs-lookup"><span data-stu-id="1471b-108">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1471b-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="1471b-109">See also</span></span>

- <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames>
- <xref:System.Windows.UIElement.IsEnabled%2A>
- <xref:System.Windows.Controls.Button>
- [<span data-ttu-id="1471b-110">Visão geral das animações de quadro-chave</span><span class="sxs-lookup"><span data-stu-id="1471b-110">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="1471b-111">Tópicos explicativos sobre quadros-chave</span><span class="sxs-lookup"><span data-stu-id="1471b-111">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
