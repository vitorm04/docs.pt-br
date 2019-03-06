---
title: 'Como: Especificar o FillBehavior para uma linha do tempo que tenha atingido fim do período ativo'
ms.date: 03/30/2017
helpviewer_keywords:
- FillBehavior property for inactive timelines [WPF]
- Timelines [WPF], FillBehavior property
ms.assetid: db805f59-d513-4dac-af15-47005dae3199
ms.openlocfilehash: 1d6a3ec38a6488d997ce5a4734cc095446354070
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57358126"
---
# <a name="how-to-specify-the-fillbehavior-for-a-timeline-that-has-reached-the-end-of-its-active-period"></a><span data-ttu-id="f99b8-102">Como: Especificar o FillBehavior para uma linha do tempo que tenha atingido fim do período ativo</span><span class="sxs-lookup"><span data-stu-id="f99b8-102">How to: Specify the FillBehavior for a Timeline that has Reached the End of Its Active Period</span></span>
<span data-ttu-id="f99b8-103">Este exemplo mostra como especificar o <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> para a inativa <xref:System.Windows.Media.Animation.Timeline> de uma propriedade animada.</span><span class="sxs-lookup"><span data-stu-id="f99b8-103">This example shows how to specify the <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> for the inactive <xref:System.Windows.Media.Animation.Timeline> of an animated property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f99b8-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f99b8-104">Example</span></span>  
 <span data-ttu-id="f99b8-105">O <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> propriedade de um <xref:System.Windows.Media.Animation.Timeline> determina o que acontece com o valor de uma propriedade animada quando ela não está sendo animada, ou seja, quando o <xref:System.Windows.Media.Animation.Timeline> estiver inativo, mas seu pai <xref:System.Windows.Media.Animation.Timeline> está dentro de seu Active Directory ou mantenha o período.</span><span class="sxs-lookup"><span data-stu-id="f99b8-105">The <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> determines what happens to the value of an animated property when it is not being animated, that is, when the <xref:System.Windows.Media.Animation.Timeline> is inactive but its parent <xref:System.Windows.Media.Animation.Timeline> is inside its active or hold period.</span></span> <span data-ttu-id="f99b8-106">Por exemplo, uma propriedade animada permanece no valor final depois que a animação terminar ou ela volta para o valor que tinha antes de a animação ter começado?</span><span class="sxs-lookup"><span data-stu-id="f99b8-106">For example, does an animated property remain at its end value after the animation ends or does it revert back to the value it had before the animation started?</span></span>  
  
 <span data-ttu-id="f99b8-107">O exemplo a seguir usa uma <xref:System.Windows.Media.Animation.DoubleAnimation> animar o <xref:System.Windows.FrameworkElement.Width%2A> de dois retângulos.</span><span class="sxs-lookup"><span data-stu-id="f99b8-107">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the <xref:System.Windows.FrameworkElement.Width%2A> of two rectangles.</span></span> <span data-ttu-id="f99b8-108">Cada retângulo usa outro <xref:System.Windows.Media.Animation.Timeline> objeto.</span><span class="sxs-lookup"><span data-stu-id="f99b8-108">Each rectangle uses a different <xref:System.Windows.Media.Animation.Timeline> object.</span></span>  
  
 <span data-ttu-id="f99b8-109">Uma <xref:System.Windows.Media.Animation.Timeline> tem uma <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> que é definido como <xref:System.Windows.Media.Animation.FillBehavior.Stop>, que faz com que a largura do retângulo a ser revertido para seu não animado valor quando o <xref:System.Windows.Media.Animation.Timeline> termina.</span><span class="sxs-lookup"><span data-stu-id="f99b8-109">One <xref:System.Windows.Media.Animation.Timeline> has a <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> that is set to <xref:System.Windows.Media.Animation.FillBehavior.Stop>, which causes the width of the rectangle to revert back to its non-animated value when the <xref:System.Windows.Media.Animation.Timeline> ends.</span></span> <span data-ttu-id="f99b8-110">A outra <xref:System.Windows.Media.Animation.Timeline> tem uma <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> de <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, que faz com que a largura permaneça em sua extremidade valor quando o <xref:System.Windows.Media.Animation.Timeline> termina.</span><span class="sxs-lookup"><span data-stu-id="f99b8-110">The other <xref:System.Windows.Media.Animation.Timeline> has a <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> of <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, which causes the width to remain at its end value when the <xref:System.Windows.Media.Animation.Timeline> ends.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#FillBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/FillBehaviorExample.xaml#fillbehaviorwholepage)]  
  
 <span data-ttu-id="f99b8-111">Para obter o exemplo completo, consulte [Galeria de exemplo de animação](https://go.microsoft.com/fwlink/?LinkID=159969).</span><span class="sxs-lookup"><span data-stu-id="f99b8-111">For the complete sample, see [Animation Example Gallery](https://go.microsoft.com/fwlink/?LinkID=159969).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f99b8-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f99b8-112">See also</span></span>
- <xref:System.Windows.Media.Animation.DoubleAnimation>
- <xref:System.Windows.FrameworkElement.Width%2A>
- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>
- <xref:System.Windows.Media.Animation.FillBehavior.Stop>
- <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>
- [<span data-ttu-id="f99b8-113">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="f99b8-113">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="f99b8-114">Tópicos explicativos de animação e tempo</span><span class="sxs-lookup"><span data-stu-id="f99b8-114">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
