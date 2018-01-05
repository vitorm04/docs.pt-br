---
title: Como animar uma propriedade usando um AnimationClock
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], properties [WPF], with AnimationClocks
- AnimationClocks [WPF]
ms.assetid: e6542021-714c-4675-9567-04f1c7380834
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 145ff1be88f1af6692a8cf374e871479ed38d7bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-a-property-by-using-an-animationclock"></a><span data-ttu-id="8d330-102">Como animar uma propriedade usando um AnimationClock</span><span class="sxs-lookup"><span data-stu-id="8d330-102">How to: Animate a Property by Using an AnimationClock</span></span>
<span data-ttu-id="8d330-103">Este exemplo mostra como usar <xref:System.Windows.Media.Animation.Clock> objetos para animar uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="8d330-103">This example shows how to use <xref:System.Windows.Media.Animation.Clock> objects to animate a property.</span></span>  
  
 <span data-ttu-id="8d330-104">Existem três maneiras de animar uma propriedade de dependência:</span><span class="sxs-lookup"><span data-stu-id="8d330-104">There are three ways to animate a dependency property:</span></span>  
  
-   <span data-ttu-id="8d330-105">Criar um <xref:System.Windows.Media.Animation.AnimationTimeline> e associá-la com essa propriedade usando um <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="8d330-105">Create an <xref:System.Windows.Media.Animation.AnimationTimeline> and associate it with that property by using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
-   <span data-ttu-id="8d330-106">Usar o objeto <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> método para aplicar uma única <xref:System.Windows.Media.Animation.AnimationTimeline> para uma propriedade de destino.</span><span class="sxs-lookup"><span data-stu-id="8d330-106">Use the object's <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method to apply a single <xref:System.Windows.Media.Animation.AnimationTimeline> to a target property.</span></span>  
  
-   <span data-ttu-id="8d330-107">Criar um <xref:System.Windows.Media.Animation.AnimationClock> de um <xref:System.Windows.Media.Animation.AnimationTimeline> e aplicá-la a uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="8d330-107">Create an <xref:System.Windows.Media.Animation.AnimationClock> from an <xref:System.Windows.Media.Animation.AnimationTimeline> and apply it to a property.</span></span>  
  
 <span data-ttu-id="8d330-108"><xref:System.Windows.Media.Animation.Storyboard>objetos e o <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> método permitem que você animar propriedades sem criar e distribuir relógios diretamente (para obter exemplos, consulte [animar uma propriedade usando um Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md) e [animar uma propriedade sem Usando um Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)); relógios são criados e distribuídos para você automaticamente.</span><span class="sxs-lookup"><span data-stu-id="8d330-108"><xref:System.Windows.Media.Animation.Storyboard> objects and the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method enable you to animate properties without directly creating and distributing clocks (for examples, see [Animate a Property by Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md) and [Animate a Property Without Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)); clocks are created and distributed for you automatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d330-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8d330-109">Example</span></span>  
 <span data-ttu-id="8d330-110">O exemplo a seguir mostra como criar um <xref:System.Windows.Media.Animation.AnimationClock> e aplicá-la a duas propriedades semelhantes.</span><span class="sxs-lookup"><span data-stu-id="8d330-110">The following example shows how to create an <xref:System.Windows.Media.Animation.AnimationClock> and apply it to two similar properties.</span></span>  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 <span data-ttu-id="8d330-111">Para obter um exemplo mostrando como controlar interativamente um <xref:System.Windows.Media.Animation.Clock> depois de iniciada, consulte [controle interativamente um relógio](../../../../docs/framework/wpf/graphics-multimedia/how-to-interactively-control-a-clock.md).</span><span class="sxs-lookup"><span data-stu-id="8d330-111">For an example showing how to interactively control a <xref:System.Windows.Media.Animation.Clock> after it starts, see [Interactively Control a Clock](../../../../docs/framework/wpf/graphics-multimedia/how-to-interactively-control-a-clock.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d330-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d330-112">See Also</span></span>  
 [<span data-ttu-id="8d330-113">Animar uma propriedade usando um storyboard</span><span class="sxs-lookup"><span data-stu-id="8d330-113">Animate a Property by Using a Storyboard</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)  
 [<span data-ttu-id="8d330-114">Animar uma propriedade sem usar um storyboard</span><span class="sxs-lookup"><span data-stu-id="8d330-114">Animate a Property Without Using a Storyboard</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)  
 [<span data-ttu-id="8d330-115">Visão geral das técnicas de animação da propriedade</span><span class="sxs-lookup"><span data-stu-id="8d330-115">Property Animation Techniques Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)
