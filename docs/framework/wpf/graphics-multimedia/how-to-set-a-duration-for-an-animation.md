---
title: "Como definir uma duração para uma animação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], duration
- Timelines [WPF], description
- duration of animations [WPF]
ms.assetid: 155034ef-7d00-4416-a73c-b1713992d2eb
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e8d15a1b8432b3dae5bee73396bdec9fc9d50f0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
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
