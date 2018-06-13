---
title: Como definir uma duração para uma animação
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], duration
- Timelines [WPF], description
- duration of animations [WPF]
ms.assetid: 155034ef-7d00-4416-a73c-b1713992d2eb
ms.openlocfilehash: df9e12e1bd3a365c3013d0f75df663bd46186ee2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561369"
---
# <a name="how-to-set-a-duration-for-an-animation"></a>Como definir uma duração para uma animação
Um <xref:System.Windows.Media.Animation.Timeline> representa um segmento de tempo e o comprimento do segmento são determinados pela linha do tempo <xref:System.Windows.Duration>. Quando um <xref:System.Windows.Media.Animation.Timeline> atinge o final de sua duração, sua execução é interrompida. Se o <xref:System.Windows.Media.Animation.Timeline> possui linhas filho, são interrompidas também. No caso de uma animação, a <xref:System.Windows.Duration> Especifica quanto tempo a animação leva para fazer a transição do seu valor inicial ao seu valor final.  
  
 Você pode especificar um <xref:System.Windows.Duration> com um tempo específico, finito ou os valores especiais <xref:System.Windows.Duration.Automatic%2A> ou <xref:System.Windows.Duration.Forever%2A>. A duração de uma animação sempre deve ser um valor temporal, porque uma animação deve sempre ter uma duração finita definida, caso contrário, a animação não saberia como fazer a transição entre seus valores de destino. Cronogramas contêiner (<xref:System.Windows.Media.Animation.TimelineGroup> objetos), como <xref:System.Windows.Media.Animation.Storyboard> e <xref:System.Windows.Media.Animation.ParallelTimeline>, ter uma duração padrão de <xref:System.Windows.Duration.Automatic%2A>, o que significa que elas automaticamente terminam quando seu último filho termina de executar.  
  
 No seguinte exemplo, a largura, altura e preenchimento de cor de um <xref:System.Windows.Shapes.Rectangle> é animado. As durações são definidas na animação e linhas de tempo do contêiner resultando em efeitos de animação, incluindo o controle da velocidade percebida de uma animação e a substituição da duração das linhas de tempo filho pela linha de tempo do contêiner.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[timingbehaviors_snip#DurationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/DurationExample.xaml#durationexamplewholepage)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Duration>  
 [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
