---
title: 'Como: Animar uma propriedade usando um AnimationClock'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], properties [WPF], with AnimationClocks
- AnimationClocks [WPF]
ms.assetid: e6542021-714c-4675-9567-04f1c7380834
ms.openlocfilehash: 4fa9efc593461d26eabaee5e2f62c1a17da1b543
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59201358"
---
# <a name="how-to-animate-a-property-by-using-an-animationclock"></a><span data-ttu-id="7e0ac-102">Como: Animar uma propriedade usando um AnimationClock</span><span class="sxs-lookup"><span data-stu-id="7e0ac-102">How to: Animate a Property by Using an AnimationClock</span></span>
<span data-ttu-id="7e0ac-103">Este exemplo mostra como usar <xref:System.Windows.Media.Animation.Clock> objetos para animar uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="7e0ac-103">This example shows how to use <xref:System.Windows.Media.Animation.Clock> objects to animate a property.</span></span>  
  
 <span data-ttu-id="7e0ac-104">Existem três maneiras de animar uma propriedade de dependência:</span><span class="sxs-lookup"><span data-stu-id="7e0ac-104">There are three ways to animate a dependency property:</span></span>  
  
-   <span data-ttu-id="7e0ac-105">Criar uma <xref:System.Windows.Media.Animation.AnimationTimeline> e associá-lo com essa propriedade usando um <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="7e0ac-105">Create an <xref:System.Windows.Media.Animation.AnimationTimeline> and associate it with that property by using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
-   <span data-ttu-id="7e0ac-106">Usar o objeto <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> método para aplicar uma única <xref:System.Windows.Media.Animation.AnimationTimeline> para uma propriedade de destino.</span><span class="sxs-lookup"><span data-stu-id="7e0ac-106">Use the object's <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method to apply a single <xref:System.Windows.Media.Animation.AnimationTimeline> to a target property.</span></span>  
  
-   <span data-ttu-id="7e0ac-107">Criar uma <xref:System.Windows.Media.Animation.AnimationClock> de um <xref:System.Windows.Media.Animation.AnimationTimeline> e aplicá-la a uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="7e0ac-107">Create an <xref:System.Windows.Media.Animation.AnimationClock> from an <xref:System.Windows.Media.Animation.AnimationTimeline> and apply it to a property.</span></span>  
  
 <span data-ttu-id="7e0ac-108"><xref:System.Windows.Media.Animation.Storyboard> objetos e o <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> método permitem animar propriedades sem criar e distribuir relógios diretamente (para obter exemplos, consulte [animar uma propriedade usando um Storyboard](how-to-animate-a-property-by-using-a-storyboard.md) e [animar uma propriedade sem Usar um Storyboard](how-to-animate-a-property-without-using-a-storyboard.md)); relógios são criados e distribuídos para você automaticamente.</span><span class="sxs-lookup"><span data-stu-id="7e0ac-108"><xref:System.Windows.Media.Animation.Storyboard> objects and the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method enable you to animate properties without directly creating and distributing clocks (for examples, see [Animate a Property by Using a Storyboard](how-to-animate-a-property-by-using-a-storyboard.md) and [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md)); clocks are created and distributed for you automatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e0ac-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7e0ac-109">Example</span></span>  
 <span data-ttu-id="7e0ac-110">O exemplo a seguir mostra como criar um <xref:System.Windows.Media.Animation.AnimationClock> e aplicá-lo a duas propriedades semelhantes.</span><span class="sxs-lookup"><span data-stu-id="7e0ac-110">The following example shows how to create an <xref:System.Windows.Media.Animation.AnimationClock> and apply it to two similar properties.</span></span>  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 <span data-ttu-id="7e0ac-111">Para obter um exemplo que mostra como controlar interativamente um <xref:System.Windows.Media.Animation.Clock> depois de ter começado, consulte [controlar interativamente um relógio](how-to-interactively-control-a-clock.md).</span><span class="sxs-lookup"><span data-stu-id="7e0ac-111">For an example showing how to interactively control a <xref:System.Windows.Media.Animation.Clock> after it starts, see [Interactively Control a Clock](how-to-interactively-control-a-clock.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e0ac-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e0ac-112">See also</span></span>

- [<span data-ttu-id="7e0ac-113">Animar uma propriedade usando um storyboard</span><span class="sxs-lookup"><span data-stu-id="7e0ac-113">Animate a Property by Using a Storyboard</span></span>](how-to-animate-a-property-by-using-a-storyboard.md)
- [<span data-ttu-id="7e0ac-114">Animar uma propriedade sem usar um storyboard</span><span class="sxs-lookup"><span data-stu-id="7e0ac-114">Animate a Property Without Using a Storyboard</span></span>](how-to-animate-a-property-without-using-a-storyboard.md)
- [<span data-ttu-id="7e0ac-115">Visão geral das técnicas de animação da propriedade</span><span class="sxs-lookup"><span data-stu-id="7e0ac-115">Property Animation Techniques Overview</span></span>](property-animation-techniques-overview.md)
