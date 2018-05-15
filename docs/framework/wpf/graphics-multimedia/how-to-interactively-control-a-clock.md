---
title: Como controlar interativamente um relógio
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controlling clocks interactively [WPF]
- clocks [WPF], controlling interactively
ms.assetid: d0b520e0-2f18-4cef-977f-2909e709548a
ms.openlocfilehash: 63e72c48afd9b72a6b334ccdc234d08cef7288f0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-interactively-control-a-clock"></a><span data-ttu-id="adab7-102">Como controlar interativamente um relógio</span><span class="sxs-lookup"><span data-stu-id="adab7-102">How to: Interactively Control a Clock</span></span>
<span data-ttu-id="adab7-103">Um <xref:System.Windows.Media.Animation.Clock> do objeto <xref:System.Windows.Media.Animation.ClockController> propriedade permite que você interativamente Iniciar, pausar, retomar, busca, Avançar o relógio para completar seu período e parar o relógio.</span><span class="sxs-lookup"><span data-stu-id="adab7-103">A <xref:System.Windows.Media.Animation.Clock> object's <xref:System.Windows.Media.Animation.ClockController> property enables you to interactively start, pause, resume, seek, advance the clock to its fill period, and stop the clock.</span></span> <span data-ttu-id="adab7-104">Somente o relógio raiz de uma árvore de tempo pode ser controlado interativamente.</span><span class="sxs-lookup"><span data-stu-id="adab7-104">Only the root clock of a timing tree can be interactively controlled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="adab7-105">Existem outras maneiras de controlar animações que não exigem que você trabalhe diretamente com relógios: você também pode usar Storyboards.</span><span class="sxs-lookup"><span data-stu-id="adab7-105">There are other ways to interactively control animations that don't require you to work directly with clocks: you can also use Storyboards.</span></span> <span data-ttu-id="adab7-106">Storyboards são suportados na marcação e código.</span><span class="sxs-lookup"><span data-stu-id="adab7-106">Storyboards are supported in both markup and code.</span></span> <span data-ttu-id="adab7-107">Para obter um exemplo, consulte [animar uma propriedade usando um Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md) ou [visão geral de animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="adab7-107">For an example, see [Animate a Property by Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md) or the [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span>  
  
 <span data-ttu-id="adab7-108">No exemplo a seguir, vários botões são usados para controlar interativamente um relógio de animação.</span><span class="sxs-lookup"><span data-stu-id="adab7-108">In the following example, several buttons are used to interactively control an animation clock.</span></span>  
  
## <a name="example"></a><span data-ttu-id="adab7-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="adab7-109">Example</span></span>  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerExample.cs#graphicsmmclockcontrollerexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerexample.vb#graphicsmmclockcontrollerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="adab7-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="adab7-110">See Also</span></span>  
 [<span data-ttu-id="adab7-111">Animar uma propriedade usando um storyboard</span><span class="sxs-lookup"><span data-stu-id="adab7-111">Animate a Property by Using a Storyboard</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)  
 [<span data-ttu-id="adab7-112">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="adab7-112">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
