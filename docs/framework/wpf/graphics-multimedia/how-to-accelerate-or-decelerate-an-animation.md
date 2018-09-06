---
title: Como acelerar ou desacelerar uma animação
ms.date: 03/30/2017
helpviewer_keywords:
- decelerating animation [WPF]
- accelerating animation [WPF]
- animation [WPF], accelerating
- animation [WPF], decelerating
ms.assetid: 4f383b2c-f94d-4a4e-9a06-f56f5dae95f9
ms.openlocfilehash: b1649f27fc8ff850516eef2086dbce732915406b
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43803734"
---
# <a name="how-to-accelerate-or-decelerate-an-animation"></a><span data-ttu-id="4754a-102">Como acelerar ou desacelerar uma animação</span><span class="sxs-lookup"><span data-stu-id="4754a-102">How to: Accelerate or Decelerate an Animation</span></span>
<span data-ttu-id="4754a-103">Este exemplo demonstra como fazer uma animação acelerar e desacelerar ao longo do tempo.</span><span class="sxs-lookup"><span data-stu-id="4754a-103">This example demonstrates how to make an animation accelerate and decelerate over time.</span></span> <span data-ttu-id="4754a-104">No exemplo a seguir, vários retângulos são animados por animações com diferentes <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> e <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A> configurações.</span><span class="sxs-lookup"><span data-stu-id="4754a-104">In the following example, several rectangles are animated by animations with different <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> and <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A> settings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4754a-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4754a-105">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AccelDecelExample.xaml#1)]  
  
 <span data-ttu-id="4754a-106">O código foi omitido neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="4754a-106">Code has been omitted from this example.</span></span> <span data-ttu-id="4754a-107">Para o código completo, consulte o [exemplo de comportamento de tempo de animação](https://go.microsoft.com/fwlink/?LinkID=159970).</span><span class="sxs-lookup"><span data-stu-id="4754a-107">For the complete code, see the [Animation Timing Behavior Sample](https://go.microsoft.com/fwlink/?LinkID=159970).</span></span>
