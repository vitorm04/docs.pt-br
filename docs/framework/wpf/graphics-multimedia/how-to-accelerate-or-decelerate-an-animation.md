---
title: 'Como: Acelerar ou desacelerar uma animação'
ms.date: 03/30/2017
helpviewer_keywords:
- decelerating animation [WPF]
- accelerating animation [WPF]
- animation [WPF], accelerating
- animation [WPF], decelerating
ms.assetid: 4f383b2c-f94d-4a4e-9a06-f56f5dae95f9
ms.openlocfilehash: 28c7940b9a60f3bd485ba2aea77e6bc1ae5fec54
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55065837"
---
# <a name="how-to-accelerate-or-decelerate-an-animation"></a>Como: Acelerar ou desacelerar uma animação
Este exemplo demonstra como fazer uma animação acelerar e desacelerar ao longo do tempo. No exemplo a seguir, vários retângulos são animados por animações com diferentes <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> e <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A> configurações.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[timingbehaviors_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AccelDecelExample.xaml#1)]  
  
 O código foi omitido neste exemplo. Para o código completo, consulte o [comportamento de tempo de animação (C#)](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp) ou [comportamento de tempo de animação (Visual Basic)](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic).
