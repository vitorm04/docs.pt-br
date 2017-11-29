---
title: "Como acelerar ou desacelerar uma animação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- decelerating animation [WPF]
- accelerating animation [WPF]
- animation [WPF], accelerating
- animation [WPF], decelerating
ms.assetid: 4f383b2c-f94d-4a4e-9a06-f56f5dae95f9
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f4820f312ca8d404123710321a9f45bff1545f10
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-accelerate-or-decelerate-an-animation"></a><span data-ttu-id="f1f56-102">Como acelerar ou desacelerar uma animação</span><span class="sxs-lookup"><span data-stu-id="f1f56-102">How to: Accelerate or Decelerate an Animation</span></span>
<span data-ttu-id="f1f56-103">Este exemplo demonstra como fazer uma animação acelerar e desacelerar ao longo do tempo.</span><span class="sxs-lookup"><span data-stu-id="f1f56-103">This example demonstrates how to make an animation accelerate and decelerate over time.</span></span> <span data-ttu-id="f1f56-104">No exemplo a seguir, vários retângulos são animados por animações com diferentes <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> e <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A> configurações.</span><span class="sxs-lookup"><span data-stu-id="f1f56-104">In the following example, several rectangles are animated by animations with different <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> and <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A> settings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1f56-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f1f56-105">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AccelDecelExample.xaml#1)]  
  
 <span data-ttu-id="f1f56-106">O código foi omitido neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="f1f56-106">Code has been omitted from this example.</span></span> <span data-ttu-id="f1f56-107">Para o código completo, consulte o [exemplo de comportamento de tempo de animação](http://go.microsoft.com/fwlink/?LinkID=159970).</span><span class="sxs-lookup"><span data-stu-id="f1f56-107">For the complete code, see the [Animation Timing Behavior Sample](http://go.microsoft.com/fwlink/?LinkID=159970).</span></span>
