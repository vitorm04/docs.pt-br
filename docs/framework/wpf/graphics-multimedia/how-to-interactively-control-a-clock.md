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
ms.openlocfilehash: 2d18f395974750a6b85458f636a27f6101e7978f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951343"
---
# <a name="how-to-interactively-control-a-clock"></a><span data-ttu-id="ddd5f-102">Como: Controlar interativamente um relógio</span><span class="sxs-lookup"><span data-stu-id="ddd5f-102">How to: Interactively Control a Clock</span></span>
<span data-ttu-id="ddd5f-103">A <xref:System.Windows.Media.Animation.Clock> propriedade de <xref:System.Windows.Media.Animation.ClockController> um objeto permite que você inicie, pause, retome, busque, avance o relógio para seu período de preenchimento interativamente e pare o relógio.</span><span class="sxs-lookup"><span data-stu-id="ddd5f-103">A <xref:System.Windows.Media.Animation.Clock> object's <xref:System.Windows.Media.Animation.ClockController> property enables you to interactively start, pause, resume, seek, advance the clock to its fill period, and stop the clock.</span></span> <span data-ttu-id="ddd5f-104">Somente o relógio raiz de uma árvore de tempo pode ser controlado interativamente.</span><span class="sxs-lookup"><span data-stu-id="ddd5f-104">Only the root clock of a timing tree can be interactively controlled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ddd5f-105">Há outras maneiras de controlar interativamente animações que não exigem que você trabalhe diretamente com relógios: você também pode usar storyboards.</span><span class="sxs-lookup"><span data-stu-id="ddd5f-105">There are other ways to interactively control animations that don't require you to work directly with clocks: you can also use Storyboards.</span></span> <span data-ttu-id="ddd5f-106">Os storyboards têm suporte tanto na marcação quanto no código.</span><span class="sxs-lookup"><span data-stu-id="ddd5f-106">Storyboards are supported in both markup and code.</span></span> <span data-ttu-id="ddd5f-107">Para obter um exemplo, consulte [animar uma propriedade usando um storyboard](how-to-animate-a-property-by-using-a-storyboard.md) ou a [visão geral da animação](animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ddd5f-107">For an example, see [Animate a Property by Using a Storyboard](how-to-animate-a-property-by-using-a-storyboard.md) or the [Animation Overview](animation-overview.md).</span></span>  
  
 <span data-ttu-id="ddd5f-108">No exemplo a seguir, vários botões são usados para controlar interativamente um relógio de animação.</span><span class="sxs-lookup"><span data-stu-id="ddd5f-108">In the following example, several buttons are used to interactively control an animation clock.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddd5f-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ddd5f-109">Example</span></span>  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerExample.cs#graphicsmmclockcontrollerexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerexample.vb#graphicsmmclockcontrollerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="ddd5f-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ddd5f-110">See also</span></span>

- [<span data-ttu-id="ddd5f-111">Animar uma propriedade usando um storyboard</span><span class="sxs-lookup"><span data-stu-id="ddd5f-111">Animate a Property by Using a Storyboard</span></span>](how-to-animate-a-property-by-using-a-storyboard.md)
- [<span data-ttu-id="ddd5f-112">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="ddd5f-112">Animation Overview</span></span>](animation-overview.md)
