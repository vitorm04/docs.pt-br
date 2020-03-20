---
title: Como especificar o FillBehavior para uma linha do tempo que tenha atingido fim do período ativo
ms.date: 03/30/2017
helpviewer_keywords:
- FillBehavior property for inactive timelines [WPF]
- Timelines [WPF], FillBehavior property
ms.assetid: db805f59-d513-4dac-af15-47005dae3199
ms.openlocfilehash: 1f54f2c1bb49bb7a0301f112a109194ab1a8658e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141167"
---
# <a name="how-to-specify-the-fillbehavior-for-a-timeline-that-has-reached-the-end-of-its-active-period"></a>Como especificar o FillBehavior para uma linha do tempo que tenha atingido fim do período ativo
Este exemplo mostra como <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> especificar <xref:System.Windows.Media.Animation.Timeline> o para o inativo de uma propriedade animada.  
  
## <a name="example"></a>Exemplo  
 A <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> propriedade <xref:System.Windows.Media.Animation.Timeline> de um determina o que acontece com o valor de uma propriedade <xref:System.Windows.Media.Animation.Timeline> animada quando ela <xref:System.Windows.Media.Animation.Timeline> não está sendo animada, ou seja, quando o pai está dentro de seu período ativo ou de reter. Por exemplo, uma propriedade animada permanece no valor final depois que a animação terminar ou ela volta para o valor que tinha antes de a animação ter começado?  
  
 O exemplo a <xref:System.Windows.Media.Animation.DoubleAnimation> seguir usa <xref:System.Windows.FrameworkElement.Width%2A> um para animar os dois retângulos. Cada retângulo usa <xref:System.Windows.Media.Animation.Timeline> um objeto diferente.  
  
 Um <xref:System.Windows.Media.Animation.Timeline> tem <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> um que <xref:System.Windows.Media.Animation.FillBehavior.Stop>é definido para, o que faz com que a largura <xref:System.Windows.Media.Animation.Timeline> do retângulo reverta para o seu valor não animado quando as extremidades. O <xref:System.Windows.Media.Animation.Timeline> outro <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> tem <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>um de , que faz com <xref:System.Windows.Media.Animation.Timeline> que a largura permaneça em seu valor final quando o fim.  
  
 [!code-xaml[timingbehaviors_snip#FillBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/FillBehaviorExample.xaml#fillbehaviorwholepage)]  
  
 Para obter o exemplo completo, consulte [Galeria de exemplo de animação](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.Animation.DoubleAnimation>
- <xref:System.Windows.FrameworkElement.Width%2A>
- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>
- <xref:System.Windows.Media.Animation.FillBehavior.Stop>
- <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>
- [Visão geral da animação](animation-overview.md)
- [Tópicos explicativos de animação e tempo](animation-and-timing-how-to-topics.md)
