---
title: Como acelerar ou desacelerar uma animação
ms.date: 03/30/2017
helpviewer_keywords:
- decelerating animation [WPF]
- accelerating animation [WPF]
- animation [WPF], accelerating
- animation [WPF], decelerating
ms.assetid: 4f383b2c-f94d-4a4e-9a06-f56f5dae95f9
ms.openlocfilehash: 7ab55ba44b866a992b9021284f170858f0108d15
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243005"
---
# <a name="how-to-accelerate-or-decelerate-an-animation"></a><span data-ttu-id="151d1-102">Como: Acelerar ou desacelerar uma animação</span><span class="sxs-lookup"><span data-stu-id="151d1-102">How to: Accelerate or decelerate an animation</span></span>

<span data-ttu-id="151d1-103">Este exemplo demonstra como fazer uma animação acelerar e desacelerar ao longo do tempo.</span><span class="sxs-lookup"><span data-stu-id="151d1-103">This example demonstrates how to make an animation accelerate and decelerate over time.</span></span> <span data-ttu-id="151d1-104">No exemplo a seguir, vários retângulos <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> são <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A> animados por animações com diferentes configurações.</span><span class="sxs-lookup"><span data-stu-id="151d1-104">In the following example, several rectangles are animated by animations with different <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> and <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A> settings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="151d1-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="151d1-105">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AccelDecelExample.xaml#1)]  
  
 <span data-ttu-id="151d1-106">O código foi omitido neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="151d1-106">Code has been omitted from this example.</span></span> <span data-ttu-id="151d1-107">Para obter o código completo, consulte o [Comportamento de Tempo de Animação (C#)](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp) ou o Comportamento de Tempo de Animação [(Visual Basic)](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic).</span><span class="sxs-lookup"><span data-stu-id="151d1-107">For the complete code, see the [Animation Timing Behavior (C#)](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp) or [Animation Timing Behavior (Visual Basic)](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic).</span></span>
