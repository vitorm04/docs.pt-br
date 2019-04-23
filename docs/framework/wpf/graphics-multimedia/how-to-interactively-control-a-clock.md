---
title: 'Como: Controlar interativamente um relógio'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controlling clocks interactively [WPF]
- clocks [WPF], controlling interactively
ms.assetid: d0b520e0-2f18-4cef-977f-2909e709548a
ms.openlocfilehash: 05989b6a03e03fb5723a70c9c36d5e32f9117049
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186583"
---
# <a name="how-to-interactively-control-a-clock"></a><span data-ttu-id="4727c-102">Como: Controlar interativamente um relógio</span><span class="sxs-lookup"><span data-stu-id="4727c-102">How to: Interactively Control a Clock</span></span>
<span data-ttu-id="4727c-103">Um <xref:System.Windows.Media.Animation.Clock> do objeto <xref:System.Windows.Media.Animation.ClockController> propriedade permite que você interativamente Iniciar, pausar, retomar, buscar, Avançar o relógio para seu período de preenchimento e parar o relógio.</span><span class="sxs-lookup"><span data-stu-id="4727c-103">A <xref:System.Windows.Media.Animation.Clock> object's <xref:System.Windows.Media.Animation.ClockController> property enables you to interactively start, pause, resume, seek, advance the clock to its fill period, and stop the clock.</span></span> <span data-ttu-id="4727c-104">Somente o relógio raiz de uma árvore de tempo pode ser controlado interativamente.</span><span class="sxs-lookup"><span data-stu-id="4727c-104">Only the root clock of a timing tree can be interactively controlled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4727c-105">Há outras maneiras de controlar interativamente animações que não exigem que você trabalhe diretamente com relógios: você também pode usar Storyboards.</span><span class="sxs-lookup"><span data-stu-id="4727c-105">There are other ways to interactively control animations that don't require you to work directly with clocks: you can also use Storyboards.</span></span> <span data-ttu-id="4727c-106">Storyboards são suportados em código e marcação.</span><span class="sxs-lookup"><span data-stu-id="4727c-106">Storyboards are supported in both markup and code.</span></span> <span data-ttu-id="4727c-107">Por exemplo, consulte [animar uma propriedade usando um Storyboard](how-to-animate-a-property-by-using-a-storyboard.md) ou o [visão geral da animação](animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="4727c-107">For an example, see [Animate a Property by Using a Storyboard](how-to-animate-a-property-by-using-a-storyboard.md) or the [Animation Overview](animation-overview.md).</span></span>  
  
 <span data-ttu-id="4727c-108">No exemplo a seguir, vários botões são usados para controlar interativamente um relógio de animação.</span><span class="sxs-lookup"><span data-stu-id="4727c-108">In the following example, several buttons are used to interactively control an animation clock.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4727c-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4727c-109">Example</span></span>  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerExample.cs#graphicsmmclockcontrollerexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerexample.vb#graphicsmmclockcontrollerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="4727c-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4727c-110">See also</span></span>

- [<span data-ttu-id="4727c-111">Animar uma propriedade usando um storyboard</span><span class="sxs-lookup"><span data-stu-id="4727c-111">Animate a Property by Using a Storyboard</span></span>](how-to-animate-a-property-by-using-a-storyboard.md)
- [<span data-ttu-id="4727c-112">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="4727c-112">Animation Overview</span></span>](animation-overview.md)
