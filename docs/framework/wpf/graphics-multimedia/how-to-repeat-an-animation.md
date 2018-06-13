---
title: Como repetir uma animação
ms.date: 03/30/2017
helpviewer_keywords:
- RepeatBehavior property of timelines [WPF]
- repeating animating [WPF]
- Timelines RepeatBehavior property [WPF]
- animation [WPF], repeating
ms.assetid: e6f3b068-eeeb-47fd-8d40-8848c31f1e1e
ms.openlocfilehash: b2281805b62d6d4e639524d9a0959b392006d003
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561203"
---
# <a name="how-to-repeat-an-animation"></a><span data-ttu-id="385c1-102">Como repetir uma animação</span><span class="sxs-lookup"><span data-stu-id="385c1-102">How to: Repeat an Animation</span></span>
<span data-ttu-id="385c1-103">Este exemplo mostra como usar o <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> propriedade de um <xref:System.Windows.Media.Animation.Timeline> para controlar o comportamento de repetição de uma animação.</span><span class="sxs-lookup"><span data-stu-id="385c1-103">This example shows how to use the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> in order to control the repeat behavior of an animation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="385c1-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="385c1-104">Example</span></span>  
 <span data-ttu-id="385c1-105">O <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> propriedade de um <xref:System.Windows.Media.Animation.Timeline> controla quantas vezes uma animação repete sua duração simples.</span><span class="sxs-lookup"><span data-stu-id="385c1-105">The <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> controls how many times an animation repeats its simple duration.</span></span> <span data-ttu-id="385c1-106">Usando <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, você pode especificar que um <xref:System.Windows.Media.Animation.Timeline> se repete para um determinado número de vezes (uma contagem de iteração) ou por um período de tempo especificado.</span><span class="sxs-lookup"><span data-stu-id="385c1-106">By using <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, you can specify that a <xref:System.Windows.Media.Animation.Timeline> repeats for a certain number of times (an iteration count) or for a specified time period.</span></span> <span data-ttu-id="385c1-107">Em ambos os casos, a animação passa por quantas execuções do início ao fim forem necessárias para completar a contagem ou duração solicitada.</span><span class="sxs-lookup"><span data-stu-id="385c1-107">In either case, the animation goes through as many beginning-to-end runs that it needs in order to fill the requested count or duration.</span></span>  
  
 <span data-ttu-id="385c1-108">Por padrão, linhas de tempo têm uma contagem de repetição de 1,0, o que significa que elas são reproduzidas uma vez e não se repetem.</span><span class="sxs-lookup"><span data-stu-id="385c1-108">By default, timelines have a repeat count of 1.0, which means they play one time and do not repeat.</span></span> <span data-ttu-id="385c1-109">No entanto, se você definir o <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> propriedade de um <xref:System.Windows.Media.Animation.Timeline> para <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, a linha de tempo repete indefinidamente.</span><span class="sxs-lookup"><span data-stu-id="385c1-109">However, if you set the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> to <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, the timeline repeats indefinitely.</span></span>  
  
 <span data-ttu-id="385c1-110">O exemplo a seguir mostra como usar o <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> propriedade para controlar o comportamento de repetição de uma animação.</span><span class="sxs-lookup"><span data-stu-id="385c1-110">The following example shows how to use the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property to control the repeat behavior of an animation.</span></span> <span data-ttu-id="385c1-111">O exemplo anima a <xref:System.Windows.FrameworkElement.Width%2A> propriedade de cinco retângulos com cada retângulo usando um tipo diferente de comportamento de repetição.</span><span class="sxs-lookup"><span data-stu-id="385c1-111">The example animates the <xref:System.Windows.FrameworkElement.Width%2A> property of five rectangles with each rectangle using a different type of repeat behavior.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#RepeatBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/RepeatBehaviorExample.xaml#repeatbehaviorwholepage)]  
  
 <span data-ttu-id="385c1-112">Para o exemplo completo, consulte [Exemplo de comportamento do tempo de animação](http://go.microsoft.com/fwlink/?LinkID=159970).</span><span class="sxs-lookup"><span data-stu-id="385c1-112">For the complete sample, see [Animation Timing Behavior Sample](http://go.microsoft.com/fwlink/?LinkID=159970).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="385c1-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="385c1-113">See Also</span></span>  
 [<span data-ttu-id="385c1-114">Acumular valores de animação durante ciclos de repetição</span><span class="sxs-lookup"><span data-stu-id="385c1-114">Accumulate Animation Values During Repeat Cycles</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-accumulate-animation-values-during-repeat-cycles.md)  
 [<span data-ttu-id="385c1-115">Especificar se uma linha do tempo é revertida automaticamente</span><span class="sxs-lookup"><span data-stu-id="385c1-115">Specify Whether a Timeline Automatically Reverses</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-whether-a-timeline-automatically-reverses.md)  
 [<span data-ttu-id="385c1-116">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="385c1-116">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)  
 [<span data-ttu-id="385c1-117">Animação e temporização</span><span class="sxs-lookup"><span data-stu-id="385c1-117">Animation and Timing</span></span>](http://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [<span data-ttu-id="385c1-118">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="385c1-118">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="385c1-119">Amostra de comportamento de tempo da animação</span><span class="sxs-lookup"><span data-stu-id="385c1-119">Animation Timing Behavior Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159970)
