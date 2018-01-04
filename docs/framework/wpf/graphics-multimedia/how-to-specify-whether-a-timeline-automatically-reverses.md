---
title: "Como especificar se uma linha do tempo é revertida automaticamente"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AutoReverse property of timelines [WPF]
- Timelines [WPF], AutoReverse property
ms.assetid: 1648dd90-1bee-409a-ac69-ac729867f557
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da1330a8513f43e7543f97838ef8e9be788af396
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-whether-a-timeline-automatically-reverses"></a>Como especificar se uma linha do tempo é revertida automaticamente
Uma linha do tempo <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> propriedade determina se ele executa em ordem inversa após ele concluir uma interação direta. O exemplo a seguir mostra várias animações com duração e valores de destino idênticos, mas com diferentes <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> configurações. Para demonstrar como o <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> propriedade se comporta com diferentes <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> configurações, algumas animações são definidas para repetir. A última animação mostra como o <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> propriedade funciona em cronogramas aninhados.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[timingbehaviors_snip#AutoReverseAndRepeatBehaviorExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AutoReverseExample.xaml#autoreverseandrepeatbehaviorexamplewholepage)]
