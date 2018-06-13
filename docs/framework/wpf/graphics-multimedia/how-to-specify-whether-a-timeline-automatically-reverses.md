---
title: Como especificar se uma linha do tempo é revertida automaticamente
ms.date: 03/30/2017
helpviewer_keywords:
- AutoReverse property of timelines [WPF]
- Timelines [WPF], AutoReverse property
ms.assetid: 1648dd90-1bee-409a-ac69-ac729867f557
ms.openlocfilehash: 498aefa16b8a76262c01965b8992ef9a94b7ce28
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560059"
---
# <a name="how-to-specify-whether-a-timeline-automatically-reverses"></a>Como especificar se uma linha do tempo é revertida automaticamente
Uma linha do tempo <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> propriedade determina se ele executa em ordem inversa após ele concluir uma interação direta. O exemplo a seguir mostra várias animações com duração e valores de destino idênticos, mas com diferentes <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> configurações. Para demonstrar como o <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> propriedade se comporta com diferentes <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> configurações, algumas animações são definidas para repetir. A última animação mostra como o <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> propriedade funciona em cronogramas aninhados.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[timingbehaviors_snip#AutoReverseAndRepeatBehaviorExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AutoReverseExample.xaml#autoreverseandrepeatbehaviorexamplewholepage)]
