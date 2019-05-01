---
title: 'Como: Especificar se uma linha do tempo é revertida automaticamente'
ms.date: 03/30/2017
helpviewer_keywords:
- AutoReverse property of timelines [WPF]
- Timelines [WPF], AutoReverse property
ms.assetid: 1648dd90-1bee-409a-ac69-ac729867f557
ms.openlocfilehash: 0fe2d337d8afa5197475e5b9ee40950226596e8b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62024658"
---
# <a name="how-to-specify-whether-a-timeline-automatically-reverses"></a>Como: Especificar se uma linha do tempo é revertida automaticamente
Uma linha do tempo <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> propriedade determina se ele executa em ordem inversa após ele concluir uma iteração. O exemplo a seguir mostra várias animações com duração e valores de destino idênticos, mas com diferentes <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> configurações. Para demonstrar como o <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> propriedade comporta-se com diferentes <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> configurações, algumas animações são definidas para repetir. A última animação mostra como o <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> propriedade funciona em cronogramas aninhados.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[timingbehaviors_snip#AutoReverseAndRepeatBehaviorExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AutoReverseExample.xaml#autoreverseandrepeatbehaviorexamplewholepage)]
