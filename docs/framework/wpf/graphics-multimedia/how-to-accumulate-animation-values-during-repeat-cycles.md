---
title: 'Como: Acumular valores de animação durante ciclos de repetição'
ms.date: 03/30/2017
helpviewer_keywords:
- accumulating animation values across repeating cycles [WPF]
- animation [WPF], accumulating values across repeating cycles
ms.assetid: 548df369-c7cc-4dab-b569-08b95ced2e7e
ms.openlocfilehash: 4b739883322751e2df86e13bfd07249abdb10a08
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61762170"
---
# <a name="how-to-accumulate-animation-values-during-repeat-cycles"></a><span data-ttu-id="43b4e-102">Como: Acumular valores de animação durante ciclos de repetição</span><span class="sxs-lookup"><span data-stu-id="43b4e-102">How to: Accumulate Animation Values During Repeat Cycles</span></span>
<span data-ttu-id="43b4e-103">Este exemplo mostra como usar o <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> propriedade para acumular valores de animação entre ciclos de repetição.</span><span class="sxs-lookup"><span data-stu-id="43b4e-103">This example shows how to use the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to accumulate animation values across repeating cycles.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43b4e-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="43b4e-104">Example</span></span>  
 <span data-ttu-id="43b4e-105">Use o <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> propriedade para acumular valores de base de uma animação entre ciclos de repetição.</span><span class="sxs-lookup"><span data-stu-id="43b4e-105">Use the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to accumulate base values of an animation across repeating cycles.</span></span> <span data-ttu-id="43b4e-106">Por exemplo, se você definir uma animação para repetir 9 vezes (<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> = "9x") e você definir a propriedade para animar entre 10 e 15 (From = 10 To = 15), a propriedade anima de 10 a 15 durante o primeiro ciclo, de 15 a 20 durante o segundo ciclo , de 20 a 25 durante o terceiro ciclo e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="43b4e-106">For example, if you set an animation to repeat 9 times (<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> = "9x") and you set the property to animate between 10 and 15 (From = 10 To = 15), the property animates from 10 to 15 during the first cycle, from 15 to 20 during the second cycle, from 20 to 25 during the third cycle, and so on.</span></span> <span data-ttu-id="43b4e-107">Portanto, cada ciclo de animação usa o valor final de animação do ciclo de animação anterior como seu valor de base.</span><span class="sxs-lookup"><span data-stu-id="43b4e-107">Hence, each animation cycle uses the ending animation value from the previous animation cycle as its base value.</span></span>  
  
 <span data-ttu-id="43b4e-108">Você pode usar a propriedade `IsCumulative` com animações mais básicas e a maioria das animações de quadro-chave.</span><span class="sxs-lookup"><span data-stu-id="43b4e-108">You can use the `IsCumulative` property with most basic animations and most key frame animations.</span></span> <span data-ttu-id="43b4e-109">Para obter mais informações, consulte [Visão geral da animação](animation-overview.md) e [Visão geral de animações de quadro-chave](key-frame-animations-overview.md).</span><span class="sxs-lookup"><span data-stu-id="43b4e-109">For more information, see [Animation Overview](animation-overview.md) and [Key-Frame Animations Overview](key-frame-animations-overview.md).</span></span>  
  
 <span data-ttu-id="43b4e-110">O exemplo a seguir mostra esse comportamento, animando a largura de quatro retângulos.</span><span class="sxs-lookup"><span data-stu-id="43b4e-110">The following example shows this behavior by animating the width of four rectangles.</span></span> <span data-ttu-id="43b4e-111">O Exemplo:</span><span class="sxs-lookup"><span data-stu-id="43b4e-111">The example:</span></span>  
  
- <span data-ttu-id="43b4e-112">Anima o primeiro retângulo com <xref:System.Windows.Media.Animation.DoubleAnimation> e define o <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="43b4e-112">Animates the first rectangle with <xref:System.Windows.Media.Animation.DoubleAnimation> and sets the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to `true`.</span></span>  
  
- <span data-ttu-id="43b4e-113">Anima o segundo retângulo com <xref:System.Windows.Media.Animation.DoubleAnimation> e define o <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> propriedade para o valor padrão de `false`.</span><span class="sxs-lookup"><span data-stu-id="43b4e-113">Animates the second rectangle with <xref:System.Windows.Media.Animation.DoubleAnimation> and sets the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to the default value of `false`.</span></span>  
  
- <span data-ttu-id="43b4e-114">Anima o terceiro retângulo com <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> e define o <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="43b4e-114">Animates the third rectangle with <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> and sets the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> property to `true`.</span></span>  
  
- <span data-ttu-id="43b4e-115">Anima o último retângulo com <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> e define o <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> propriedade `false`.</span><span class="sxs-lookup"><span data-stu-id="43b4e-115">Animates the last rectangle with <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> and sets the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> property to `false`.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#IsCumulativeWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsCumulativeExample.xaml#iscumulativewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="43b4e-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43b4e-116">See also</span></span>

- [<span data-ttu-id="43b4e-117">Adicionar um valor de saída da animação a um valor inicial de animação</span><span class="sxs-lookup"><span data-stu-id="43b4e-117">Add an Animation Output Value to an Animation Starting Value</span></span>](how-to-add-an-animation-output-value-to-an-animation-starting-value.md)
- [<span data-ttu-id="43b4e-118">Repetir uma animação</span><span class="sxs-lookup"><span data-stu-id="43b4e-118">Repeat an Animation</span></span>](how-to-repeat-an-animation.md)
- [<span data-ttu-id="43b4e-119">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="43b4e-119">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="43b4e-120">Visão geral das animações de quadro-chave</span><span class="sxs-lookup"><span data-stu-id="43b4e-120">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="43b4e-121">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="43b4e-121">How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
