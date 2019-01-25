---
title: 'Como: Animar cor usando quadros-chave'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [WPF], animating with key frames
- animation [WPF], colors with key frames
- key frames [WPF], animating colors with
ms.assetid: ab04ffa6-4de9-4d5b-a3b4-4e35d5b2ef35
ms.openlocfilehash: 8d7dbe70f25b4712d1384a751a02053fb7f287ee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645087"
---
# <a name="how-to-animate-color-by-using-key-frames"></a><span data-ttu-id="fae26-102">Como: Animar cor usando quadros-chave</span><span class="sxs-lookup"><span data-stu-id="fae26-102">How to: Animate Color by Using Key Frames</span></span>
<span data-ttu-id="fae26-103">Este exemplo mostra como animar a <xref:System.Windows.Media.SolidColorBrush.Color%2A> de um <xref:System.Windows.Media.SolidColorBrush> usando quadros-chave.</span><span class="sxs-lookup"><span data-stu-id="fae26-103">This example shows how to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> of a <xref:System.Windows.Media.SolidColorBrush> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fae26-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fae26-104">Example</span></span>  
 <span data-ttu-id="fae26-105">O exemplo a seguir usa o <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames> classe para animar a <xref:System.Windows.Media.SolidColorBrush.Color%2A> propriedade de um <xref:System.Windows.Media.SolidColorBrush>.</span><span class="sxs-lookup"><span data-stu-id="fae26-105">The following example uses the <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> property of a <xref:System.Windows.Media.SolidColorBrush>.</span></span> <span data-ttu-id="fae26-106">Essa animação usa três quadros-chave da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="fae26-106">This animation uses three key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="fae26-107">Durante os primeiros dois segundos, usa uma instância da <xref:System.Windows.Media.Animation.LinearColorKeyFrame> classe para mudar gradualmente a cor de verde para vermelho.</span><span class="sxs-lookup"><span data-stu-id="fae26-107">During the first two seconds, uses an instance of the <xref:System.Windows.Media.Animation.LinearColorKeyFrame> class to gradually change the color from green to red.</span></span> <span data-ttu-id="fae26-108">Quadros-chave lineares como <xref:System.Windows.Media.Animation.LinearColorKeyFrame> criam uma transição linear suave entre valores.</span><span class="sxs-lookup"><span data-stu-id="fae26-108">Linear key frames like <xref:System.Windows.Media.Animation.LinearColorKeyFrame> create a smooth linear transition between values.</span></span>  
  
2.  <span data-ttu-id="fae26-109">Durante o final do próximo meio segundo, usa uma instância da <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> classe para alterar rapidamente a cor de vermelho para amarelo.</span><span class="sxs-lookup"><span data-stu-id="fae26-109">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> class to quickly change the color from red to yellow.</span></span> <span data-ttu-id="fae26-110">Quadros chave discretos como <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> criam alterações repentinas entre valores, ou seja, a alteração de cor nesta parte da animação ocorre rapidamente e não é sutil.</span><span class="sxs-lookup"><span data-stu-id="fae26-110">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> create sudden changes between values, that is, the color change in this part of the animation occurs quickly and is not subtle.</span></span>  
  
3.  <span data-ttu-id="fae26-111">Durante os dois segundos finais, usa uma instância da <xref:System.Windows.Media.Animation.SplineColorKeyFrame> classe para alterar a cor novamente – desta vez de amarelo para verde.</span><span class="sxs-lookup"><span data-stu-id="fae26-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineColorKeyFrame> class to change the color again—this time from yellow back to green.</span></span> <span data-ttu-id="fae26-112">Como quadros-chave spline <xref:System.Windows.Media.Animation.SplineColorKeyFrame> criam uma transição variável entre valores de acordo com os valores da <xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="fae26-112">Spline key frames like <xref:System.Windows.Media.Animation.SplineColorKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="fae26-113">Neste exemplo, a alteração na cor começa lentamente e acelera exponencialmente na direção do final do segmento de tempo.</span><span class="sxs-lookup"><span data-stu-id="fae26-113">In this example, the change in color begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/ColorAnimationUsingKeyFramesExample.cs#coloranimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/coloranimationusingkeyframesexample.vb#coloranimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ColorAnimationUsingKeyFramesExample.xaml#coloranimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="fae26-114">Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="fae26-114">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fae26-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fae26-115">See also</span></span>
- <xref:System.Windows.Media.SolidColorBrush.Color%2A>
- <xref:System.Windows.Media.SolidColorBrush>
- <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>
- [<span data-ttu-id="fae26-116">Visão geral das animações de quadro-chave</span><span class="sxs-lookup"><span data-stu-id="fae26-116">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)
- [<span data-ttu-id="fae26-117">Tópicos explicativos sobre quadros-chave</span><span class="sxs-lookup"><span data-stu-id="fae26-117">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
