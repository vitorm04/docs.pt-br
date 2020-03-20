---
title: Como repetir uma animação
ms.date: 03/30/2017
helpviewer_keywords:
- RepeatBehavior property of timelines [WPF]
- repeating animating [WPF]
- Timelines RepeatBehavior property [WPF]
- animation [WPF], repeating
ms.assetid: e6f3b068-eeeb-47fd-8d40-8848c31f1e1e
ms.openlocfilehash: 1512c49a658c80f3ab6af652839c3562af3dd205
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141533"
---
# <a name="how-to-repeat-an-animation"></a><span data-ttu-id="7b923-102">Como repetir uma animação</span><span class="sxs-lookup"><span data-stu-id="7b923-102">How to: Repeat an Animation</span></span>
<span data-ttu-id="7b923-103">Este exemplo mostra como <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> usar <xref:System.Windows.Media.Animation.Timeline> a propriedade de um para controlar o comportamento repetido de uma animação.</span><span class="sxs-lookup"><span data-stu-id="7b923-103">This example shows how to use the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> in order to control the repeat behavior of an animation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b923-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7b923-104">Example</span></span>  
 <span data-ttu-id="7b923-105">A <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> propriedade <xref:System.Windows.Media.Animation.Timeline> de um controla quantas vezes uma animação repete sua duração simples.</span><span class="sxs-lookup"><span data-stu-id="7b923-105">The <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> controls how many times an animation repeats its simple duration.</span></span> <span data-ttu-id="7b923-106">Ao <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>usar, você pode <xref:System.Windows.Media.Animation.Timeline> especificar que uma repetição por um determinado número de vezes (uma contagem de iteração) ou por um período de tempo especificado.</span><span class="sxs-lookup"><span data-stu-id="7b923-106">By using <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, you can specify that a <xref:System.Windows.Media.Animation.Timeline> repeats for a certain number of times (an iteration count) or for a specified time period.</span></span> <span data-ttu-id="7b923-107">Em ambos os casos, a animação passa por quantas execuções do início ao fim forem necessárias para completar a contagem ou duração solicitada.</span><span class="sxs-lookup"><span data-stu-id="7b923-107">In either case, the animation goes through as many beginning-to-end runs that it needs in order to fill the requested count or duration.</span></span>  
  
 <span data-ttu-id="7b923-108">Por padrão, linhas de tempo têm uma contagem de repetição de 1,0, o que significa que elas são reproduzidas uma vez e não se repetem.</span><span class="sxs-lookup"><span data-stu-id="7b923-108">By default, timelines have a repeat count of 1.0, which means they play one time and do not repeat.</span></span> <span data-ttu-id="7b923-109">No entanto, <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> se você <xref:System.Windows.Media.Animation.Timeline> <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>definir a propriedade de a , a linha do tempo se repete indefinidamente.</span><span class="sxs-lookup"><span data-stu-id="7b923-109">However, if you set the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> to <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, the timeline repeats indefinitely.</span></span>  
  
 <span data-ttu-id="7b923-110">O exemplo a seguir <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> mostra como usar a propriedade para controlar o comportamento repetido de uma animação.</span><span class="sxs-lookup"><span data-stu-id="7b923-110">The following example shows how to use the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property to control the repeat behavior of an animation.</span></span> <span data-ttu-id="7b923-111">O exemplo anima <xref:System.Windows.FrameworkElement.Width%2A> a propriedade de cinco retângulos com cada retângulo usando um tipo diferente de comportamento repetitivo.</span><span class="sxs-lookup"><span data-stu-id="7b923-111">The example animates the <xref:System.Windows.FrameworkElement.Width%2A> property of five rectangles with each rectangle using a different type of repeat behavior.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#RepeatBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/RepeatBehaviorExample.xaml#repeatbehaviorwholepage)]  
  
 <span data-ttu-id="7b923-112">Para o exemplo completo, consulte [Exemplo de comportamento do tempo de animação](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming).</span><span class="sxs-lookup"><span data-stu-id="7b923-112">For the complete sample, see [Animation Timing Behavior Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b923-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="7b923-113">See also</span></span>

- [<span data-ttu-id="7b923-114">Acumular valores de animação durante ciclos de repetição</span><span class="sxs-lookup"><span data-stu-id="7b923-114">Accumulate Animation Values During Repeat Cycles</span></span>](how-to-accumulate-animation-values-during-repeat-cycles.md)
- [<span data-ttu-id="7b923-115">Especificar se uma linha do tempo é revertida automaticamente</span><span class="sxs-lookup"><span data-stu-id="7b923-115">Specify Whether a Timeline Automatically Reverses</span></span>](how-to-specify-whether-a-timeline-automatically-reverses.md)
- [<span data-ttu-id="7b923-116">Tópicos explicativos de animação e tempo</span><span class="sxs-lookup"><span data-stu-id="7b923-116">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
- [<span data-ttu-id="7b923-117">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="7b923-117">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="7b923-118">Amostra de comportamento de tempo da animação</span><span class="sxs-lookup"><span data-stu-id="7b923-118">Animation Timing Behavior Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming)
