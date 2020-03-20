---
title: Como repetir uma animação
ms.date: 03/30/2017
helpviewer_keywords:
- RepeatBehavior property of timelines [WPF]
- repeating animating [WPF]
- Timelines RepeatBehavior property [WPF]
- animation [WPF], repeating
ms.assetid: e6f3b068-eeeb-47fd-8d40-8848c31f1e1e
ms.openlocfilehash: 1512c49a658c80f3ab6af652839c3562af3dd205
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141533"
---
# <a name="how-to-repeat-an-animation"></a>Como repetir uma animação
Este exemplo mostra como <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> usar <xref:System.Windows.Media.Animation.Timeline> a propriedade de um para controlar o comportamento repetido de uma animação.  
  
## <a name="example"></a>Exemplo  
 A <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> propriedade <xref:System.Windows.Media.Animation.Timeline> de um controla quantas vezes uma animação repete sua duração simples. Ao <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>usar, você pode <xref:System.Windows.Media.Animation.Timeline> especificar que uma repetição por um determinado número de vezes (uma contagem de iteração) ou por um período de tempo especificado. Em ambos os casos, a animação passa por quantas execuções do início ao fim forem necessárias para completar a contagem ou duração solicitada.  
  
 Por padrão, linhas de tempo têm uma contagem de repetição de 1,0, o que significa que elas são reproduzidas uma vez e não se repetem. No entanto, <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> se você <xref:System.Windows.Media.Animation.Timeline> <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>definir a propriedade de a , a linha do tempo se repete indefinidamente.  
  
 O exemplo a seguir <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> mostra como usar a propriedade para controlar o comportamento repetido de uma animação. O exemplo anima <xref:System.Windows.FrameworkElement.Width%2A> a propriedade de cinco retângulos com cada retângulo usando um tipo diferente de comportamento repetitivo.  
  
 [!code-xaml[timingbehaviors_snip#RepeatBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/RepeatBehaviorExample.xaml#repeatbehaviorwholepage)]  
  
 Para o exemplo completo, consulte [Exemplo de comportamento do tempo de animação](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming).  
  
## <a name="see-also"></a>Confira também

- [Acumular valores de animação durante ciclos de repetição](how-to-accumulate-animation-values-during-repeat-cycles.md)
- [Especificar se uma linha do tempo é revertida automaticamente](how-to-specify-whether-a-timeline-automatically-reverses.md)
- [Tópicos explicativos de animação e tempo](animation-and-timing-how-to-topics.md)
- [Visão geral da animação](animation-overview.md)
- [Amostra de comportamento de tempo da animação](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming)
