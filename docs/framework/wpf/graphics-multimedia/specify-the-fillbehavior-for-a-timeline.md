---
title: Como especificar o FillBehavior para uma linha do tempo que tenha atingido fim do período ativo
ms.date: 03/30/2017
helpviewer_keywords:
- FillBehavior property for inactive timelines [WPF]
- Timelines [WPF], FillBehavior property
ms.assetid: db805f59-d513-4dac-af15-47005dae3199
ms.openlocfilehash: c88deeb679a3e8f2027d6bb2e817edc1ade5926d
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45625042"
---
# <a name="how-to-specify-the-fillbehavior-for-a-timeline-that-has-reached-the-end-of-its-active-period"></a>Como especificar o FillBehavior para uma linha do tempo que tenha atingido fim do período ativo
Este exemplo mostra como especificar o <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> para a inativa <xref:System.Windows.Media.Animation.Timeline> de uma propriedade animada.  
  
## <a name="example"></a>Exemplo  
 O <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> propriedade de um <xref:System.Windows.Media.Animation.Timeline> determina o que acontece com o valor de uma propriedade animada quando ela não está sendo animada, ou seja, quando o <xref:System.Windows.Media.Animation.Timeline> estiver inativo, mas seu pai <xref:System.Windows.Media.Animation.Timeline> está dentro de seu Active Directory ou mantenha o período. Por exemplo, uma propriedade animada permanece no valor final depois que a animação terminar ou ela volta para o valor que tinha antes de a animação ter começado?  
  
 O exemplo a seguir usa uma <xref:System.Windows.Media.Animation.DoubleAnimation> animar o <xref:System.Windows.FrameworkElement.Width%2A> de dois retângulos. Cada retângulo usa outro <xref:System.Windows.Media.Animation.Timeline> objeto.  
  
 Uma <xref:System.Windows.Media.Animation.Timeline> tem uma <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> que é definido como <xref:System.Windows.Media.Animation.FillBehavior.Stop>, que faz com que a largura do retângulo a ser revertido para seu não animado valor quando o <xref:System.Windows.Media.Animation.Timeline> termina. A outra <xref:System.Windows.Media.Animation.Timeline> tem uma <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> de <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, que faz com que a largura permaneça em sua extremidade valor quando o <xref:System.Windows.Media.Animation.Timeline> termina.  
  
 [!code-xaml[timingbehaviors_snip#FillBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/FillBehaviorExample.xaml#fillbehaviorwholepage)]  
  
 Para obter o exemplo completo, consulte [Galeria de exemplo de animação](https://go.microsoft.com/fwlink/?LinkID=159969).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.Animation.DoubleAnimation>  
 <xref:System.Windows.FrameworkElement.Width%2A>  
 <xref:System.Windows.Media.Animation.Timeline>  
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>  
 <xref:System.Windows.Media.Animation.FillBehavior.Stop>  
 <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>  
 [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Animação e tempo](https://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [Tópicos de instruções](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
