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
ms.openlocfilehash: d6273c08881e802595e831cafe120a5bec841c4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-animate-a-boolean-by-using-key-frames"></a><span data-ttu-id="97c83-102">Como animar um valor booliano usando quadros-chave</span><span class="sxs-lookup"><span data-stu-id="97c83-102">How to: Animate a Boolean by Using Key Frames</span></span>
<span data-ttu-id="97c83-103">Este exemplo mostra como o valor da propriedade booliana de animar uma <xref:System.Windows.Controls.Button> controle usando quadros chave.</span><span class="sxs-lookup"><span data-stu-id="97c83-103">This example shows how to animate the Boolean property value of a <xref:System.Windows.Controls.Button> control by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97c83-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="97c83-104">Example</span></span>  
 <span data-ttu-id="97c83-105">O exemplo a seguir usa o <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames> classe para animar a <xref:System.Windows.UIElement.IsEnabled%2A> propriedade de um <xref:System.Windows.Controls.Button> controle.</span><span class="sxs-lookup"><span data-stu-id="97c83-105">The following example uses the <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames> class to animate the <xref:System.Windows.UIElement.IsEnabled%2A> property of a <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="97c83-106">Todos os quadros chave nesse exemplo usam uma instância do <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> classe.</span><span class="sxs-lookup"><span data-stu-id="97c83-106">All the key frames in this example use an instance of the <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> class.</span></span> <span data-ttu-id="97c83-107">Quadros chave discretos como <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> criar saltos repentinos entre valores, ou seja, a movimentação da animação é uma.</span><span class="sxs-lookup"><span data-stu-id="97c83-107">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
 [!code-csharp[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/BooleanAnimationUsingKeyFramesExample.cs#booleananimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/booleananimationusingkeyframesexample.vb#booleananimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/BooleanAnimationUsingKeyFramesExample.xaml#booleananimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="97c83-108">Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](http://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="97c83-108">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97c83-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="97c83-109">See Also</span></span>  
 <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames>  
 <xref:System.Windows.UIElement.IsEnabled%2A>  
 <xref:System.Windows.Controls.Button>  
 [<span data-ttu-id="97c83-110">Visão geral das animações de quadro-chave</span><span class="sxs-lookup"><span data-stu-id="97c83-110">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="97c83-111">Tópicos explicativos sobre quadros-chave</span><span class="sxs-lookup"><span data-stu-id="97c83-111">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
