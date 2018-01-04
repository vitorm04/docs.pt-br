---
title: "Como adicionar um valor de saída da animação a um valor inicial de animação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: animation [WPF]
ms.assetid: b89a82be-b03d-481e-a8d3-cc513d09ca00
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1a6a5923655c5857b813df778b36b6c7fd208b0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-an-animation-output-value-to-an-animation-starting-value"></a><span data-ttu-id="bbb41-102">Como adicionar um valor de saída da animação a um valor inicial de animação</span><span class="sxs-lookup"><span data-stu-id="bbb41-102">How to: Add an Animation Output Value to an Animation Starting Value</span></span>
<span data-ttu-id="bbb41-103">Este exemplo mostra como adicionar um valor de saída de animação a um valor inicial de animação.</span><span class="sxs-lookup"><span data-stu-id="bbb41-103">This example shows how to add an animation output value to an animation starting value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbb41-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bbb41-104">Example</span></span>  
 <span data-ttu-id="bbb41-105">O <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> propriedade especifica se o valor de saída de uma animação seja adicionado ao valor inicial (valor base) de uma propriedade animada.</span><span class="sxs-lookup"><span data-stu-id="bbb41-105">The <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> property specifies whether you want the output value of an animation added to the starting value (base value) of an animated property.</span></span> <span data-ttu-id="bbb41-106">Você pode usar a propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> com animações mais básicas e a maioria das animações de quadro-chave.</span><span class="sxs-lookup"><span data-stu-id="bbb41-106">You can use the <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> property with most basic animations and most key frame animations.</span></span> <span data-ttu-id="bbb41-107">Para obter mais informações, consulte [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) e [Visão geral de animações de quadro-chave](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bbb41-107">For more information, see [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) and [Key-Frame Animations Overview](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).</span></span>  
  
 <span data-ttu-id="bbb41-108">O exemplo a seguir mostra o efeito de usar o <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=nameWithType> propriedade com <xref:System.Windows.Media.Animation.DoubleAnimation> e usando o <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=nameWithType> propriedade com <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.</span><span class="sxs-lookup"><span data-stu-id="bbb41-108">The following example shows the effect of using the <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=nameWithType> property with <xref:System.Windows.Media.Animation.DoubleAnimation> and using the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=nameWithType> property with <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#IsAdditiveWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsAdditiveExample.xaml#isadditivewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="bbb41-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bbb41-109">See Also</span></span>  
 [<span data-ttu-id="bbb41-110">Acumular valores de animação durante ciclos de repetição</span><span class="sxs-lookup"><span data-stu-id="bbb41-110">Accumulate Animation Values During Repeat Cycles</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-accumulate-animation-values-during-repeat-cycles.md)  
 [<span data-ttu-id="bbb41-111">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="bbb41-111">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="bbb41-112">Visão geral das animações de quadro-chave</span><span class="sxs-lookup"><span data-stu-id="bbb41-112">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="bbb41-113">Animação e temporização</span><span class="sxs-lookup"><span data-stu-id="bbb41-113">Animation and Timing</span></span>](http://msdn.microsoft.com/en-us/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [<span data-ttu-id="bbb41-114">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="bbb41-114">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
