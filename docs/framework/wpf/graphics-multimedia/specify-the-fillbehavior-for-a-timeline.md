---
title: Como especificar o FillBehavior para uma linha do tempo que tenha atingido fim do período ativo
ms.date: 03/30/2017
helpviewer_keywords:
- FillBehavior property for inactive timelines [WPF]
- Timelines [WPF], FillBehavior property
ms.assetid: db805f59-d513-4dac-af15-47005dae3199
ms.openlocfilehash: 947be09140dc2d1d5e130ccb74472d8dce3408cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-specify-the-fillbehavior-for-a-timeline-that-has-reached-the-end-of-its-active-period"></a>Como especificar o FillBehavior para uma linha do tempo que tenha atingido fim do período ativo
Este exemplo mostra como especificar o <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> para o inativo <xref:System.Windows.Media.Animation.Timeline> de uma propriedade animada.  
  
## <a name="example"></a>Exemplo  
 O <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> propriedade de um <xref:System.Windows.Media.Animation.Timeline> determina o que acontece com o valor de uma propriedade animada quando ela não está sendo animada, isto é, quando o <xref:System.Windows.Media.Animation.Timeline> está inativo mas seu pai <xref:System.Windows.Media.Animation.Timeline> está dentro de seu ativo ou manter período. Por exemplo, uma propriedade animada permanece no valor final depois que a animação terminar ou ela volta para o valor que tinha antes de a animação ter começado?  
  
 O exemplo a seguir usa uma <xref:System.Windows.Media.Animation.DoubleAnimation> para animar a <xref:System.Windows.FrameworkElement.Width%2A> de dois retângulos. Cada retângulo usa outro <xref:System.Windows.Media.Animation.Timeline> objeto.  
  
 Um <xref:System.Windows.Media.Animation.Timeline> tem um <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> está definido como <xref:System.Windows.Media.Animation.FillBehavior.Stop>, que faz com que a largura do retângulo volte ao seu sem animação quando a <xref:System.Windows.Media.Animation.Timeline> termina. O outro <xref:System.Windows.Media.Animation.Timeline> tem um <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> de <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, que faz com que a largura se mantenha seu final quando a <xref:System.Windows.Media.Animation.Timeline> termina.  
  
 [!code-xaml[timingbehaviors_snip#FillBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/FillBehaviorExample.xaml#fillbehaviorwholepage)]  
  
 Para obter o exemplo completo, consulte [Galeria de exemplo de animação](http://go.microsoft.com/fwlink/?LinkID=159969).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.Animation.DoubleAnimation>  
 <xref:System.Windows.FrameworkElement.Width%2A>  
 <xref:System.Windows.Media.Animation.Timeline>  
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>  
 <xref:System.Windows.Media.Animation.FillBehavior.Stop>  
 <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>  
 [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Animação e temporização](http://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [Tópicos de instruções](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
