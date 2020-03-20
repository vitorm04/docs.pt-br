---
title: Como especificar o FillBehavior para uma linha do tempo que tenha atingido fim do período ativo
ms.date: 03/30/2017
helpviewer_keywords:
- FillBehavior property for inactive timelines [WPF]
- Timelines [WPF], FillBehavior property
ms.assetid: db805f59-d513-4dac-af15-47005dae3199
ms.openlocfilehash: 1f54f2c1bb49bb7a0301f112a109194ab1a8658e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141167"
---
# <a name="how-to-specify-the-fillbehavior-for-a-timeline-that-has-reached-the-end-of-its-active-period"></a><span data-ttu-id="d64ce-102">Como especificar o FillBehavior para uma linha do tempo que tenha atingido fim do período ativo</span><span class="sxs-lookup"><span data-stu-id="d64ce-102">How to: Specify the FillBehavior for a Timeline that has Reached the End of Its Active Period</span></span>
<span data-ttu-id="d64ce-103">Este exemplo mostra como <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> especificar <xref:System.Windows.Media.Animation.Timeline> o para o inativo de uma propriedade animada.</span><span class="sxs-lookup"><span data-stu-id="d64ce-103">This example shows how to specify the <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> for the inactive <xref:System.Windows.Media.Animation.Timeline> of an animated property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d64ce-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d64ce-104">Example</span></span>  
 <span data-ttu-id="d64ce-105">A <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> propriedade <xref:System.Windows.Media.Animation.Timeline> de um determina o que acontece com o valor de uma propriedade <xref:System.Windows.Media.Animation.Timeline> animada quando ela <xref:System.Windows.Media.Animation.Timeline> não está sendo animada, ou seja, quando o pai está dentro de seu período ativo ou de reter.</span><span class="sxs-lookup"><span data-stu-id="d64ce-105">The <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> determines what happens to the value of an animated property when it is not being animated, that is, when the <xref:System.Windows.Media.Animation.Timeline> is inactive but its parent <xref:System.Windows.Media.Animation.Timeline> is inside its active or hold period.</span></span> <span data-ttu-id="d64ce-106">Por exemplo, uma propriedade animada permanece no valor final depois que a animação terminar ou ela volta para o valor que tinha antes de a animação ter começado?</span><span class="sxs-lookup"><span data-stu-id="d64ce-106">For example, does an animated property remain at its end value after the animation ends or does it revert back to the value it had before the animation started?</span></span>  
  
 <span data-ttu-id="d64ce-107">O exemplo a <xref:System.Windows.Media.Animation.DoubleAnimation> seguir usa <xref:System.Windows.FrameworkElement.Width%2A> um para animar os dois retângulos.</span><span class="sxs-lookup"><span data-stu-id="d64ce-107">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the <xref:System.Windows.FrameworkElement.Width%2A> of two rectangles.</span></span> <span data-ttu-id="d64ce-108">Cada retângulo usa <xref:System.Windows.Media.Animation.Timeline> um objeto diferente.</span><span class="sxs-lookup"><span data-stu-id="d64ce-108">Each rectangle uses a different <xref:System.Windows.Media.Animation.Timeline> object.</span></span>  
  
 <span data-ttu-id="d64ce-109">Um <xref:System.Windows.Media.Animation.Timeline> tem <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> um que <xref:System.Windows.Media.Animation.FillBehavior.Stop>é definido para, o que faz com que a largura <xref:System.Windows.Media.Animation.Timeline> do retângulo reverta para o seu valor não animado quando as extremidades.</span><span class="sxs-lookup"><span data-stu-id="d64ce-109">One <xref:System.Windows.Media.Animation.Timeline> has a <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> that is set to <xref:System.Windows.Media.Animation.FillBehavior.Stop>, which causes the width of the rectangle to revert back to its non-animated value when the <xref:System.Windows.Media.Animation.Timeline> ends.</span></span> <span data-ttu-id="d64ce-110">O <xref:System.Windows.Media.Animation.Timeline> outro <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> tem <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>um de , que faz com <xref:System.Windows.Media.Animation.Timeline> que a largura permaneça em seu valor final quando o fim.</span><span class="sxs-lookup"><span data-stu-id="d64ce-110">The other <xref:System.Windows.Media.Animation.Timeline> has a <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> of <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, which causes the width to remain at its end value when the <xref:System.Windows.Media.Animation.Timeline> ends.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#FillBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/FillBehaviorExample.xaml#fillbehaviorwholepage)]  
  
 <span data-ttu-id="d64ce-111">Para obter o exemplo completo, consulte [Galeria de exemplo de animação](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span><span class="sxs-lookup"><span data-stu-id="d64ce-111">For the complete sample, see [Animation Example Gallery](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d64ce-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="d64ce-112">See also</span></span>

- <xref:System.Windows.Media.Animation.DoubleAnimation>
- <xref:System.Windows.FrameworkElement.Width%2A>
- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>
- <xref:System.Windows.Media.Animation.FillBehavior.Stop>
- <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>
- [<span data-ttu-id="d64ce-113">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="d64ce-113">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="d64ce-114">Tópicos explicativos de animação e tempo</span><span class="sxs-lookup"><span data-stu-id="d64ce-114">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
