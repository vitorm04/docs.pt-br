---
title: Visão geral dos comportamentos de tempo
ms.date: 03/30/2017
helpviewer_keywords:
- timing behaviors [WPF]
- behaviors [WPF], timing
ms.assetid: 5b714d46-bd46-48b8-b467-b4be89ba3091
ms.openlocfilehash: a85f980a0cefaa282e9e92d533a2306a9009e3e7
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559944"
---
# <a name="timing-behaviors-overview"></a>Visão geral dos comportamentos de tempo
Este tópico descreve os comportamentos de temporização de animações e outros objetos de <xref:System.Windows.Media.Animation.Timeline>.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}  
 Para entender este tópico, você deve estar familiarizado com recursos básicos de animação. Para obter mais informações, consulte a [visão geral da animação](animation-overview.md).  
  
<a name="timelinetypes"></a>   
## <a name="timeline-types"></a>Tipos de linha do tempo  
 Um <xref:System.Windows.Media.Animation.Timeline> representa um segmento de tempo. Ela fornece propriedades que permitem que você especifique o comprimento desse segmento, quando ele deve ser iniciado, quantas vezes ele se repetirá, quão rápido o tempo progride nesse segmento e muito mais.  
  
 As classes que herdam da classe linha do tempo fornecem funcionalidades adicionais, como animação e reprodução de mídia. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece os tipos de <xref:System.Windows.Media.Animation.Timeline> a seguir.  
  
|Tipo de linha do tempo|Descrição|  
|-------------------|-----------------|  
|<xref:System.Windows.Media.Animation.AnimationTimeline>|Classe base abstrata para objetos <xref:System.Windows.Media.Animation.Timeline> que geram valores de saída para propriedades de animação.|  
|<xref:System.Windows.Media.MediaTimeline>|Gera a saída de um arquivo de mídia.|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|Um tipo de <xref:System.Windows.Media.Animation.TimelineGroup> que agrupa e controla objetos <xref:System.Windows.Media.Animation.Timeline> filhos.|  
|<xref:System.Windows.Media.Animation.Storyboard>|Um tipo de <xref:System.Windows.Media.Animation.ParallelTimeline> que fornece informações de destino para os objetos de linha do tempo que ele contém.|  
|<xref:System.Windows.Media.Animation.Timeline>|Classe base abstrata que define comportamentos de tempo.|  
|<xref:System.Windows.Media.Animation.TimelineGroup>|Classe abstrata para objetos de <xref:System.Windows.Media.Animation.Timeline> que podem conter outros objetos <xref:System.Windows.Media.Animation.Timeline>.|  
  
<a name="propertiesthatcontroltimelinelength"></a>   
## <a name="properties-that-control-the-length-of-a-timeline"></a>Propriedades que controlam o comprimento de uma linha do tempo  
 Um <xref:System.Windows.Media.Animation.Timeline> representa um segmento de tempo e o comprimento de uma linha do tempo pode ser descrito de maneiras diferentes. A tabela a seguir define diversos termos para descrever o comprimento de uma linha do tempo.  
  
|Termo|Descrição|{1&gt;Propriedades&lt;1}||||  
|----------|-----------------|----------------|-|-|-|  
|Duração simples|O tempo que uma linha do tempo leva para realizar uma única iteração.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>||||  
|Uma repetição|O período de tempo que leva para que uma linha do tempo seja executada uma vez e, se a propriedade <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> for true, reproduza uma vez.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>||||  
|Período ativo|O período de tempo que leva para uma linha do tempo concluir todas as repetições especificadas por sua propriedade <xref:System.Windows.Media.Animation.RepeatBehavior>.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>, <xref:System.Windows.Media.Animation.RepeatBehavior>||||  
  
<a name="duration"></a>   
### <a name="the-duration-property"></a>A propriedade Duration  
 Conforme mencionado anteriormente, uma linha do tempo representa um segmento de tempo. O comprimento desse segmento é determinado pelo <xref:System.Windows.Media.Animation.Timeline.Duration%2A>da linha do tempo. Quando uma linha de tempo alcança o final de sua duração, sua execução é interrompida. Se a linha do tempo tiver linhas do tempo filho, a execução delas também será interrompida. No caso de uma animação, o <xref:System.Windows.Media.Animation.Timeline.Duration%2A> especifica quanto tempo a animação leva para fazer a transição do seu valor inicial para o valor final. A duração de uma linha do tempo é, às vezes, chamada de sua *duração simples*, para distinguir entre a duração de uma única iteração e o período total de tempo que a animação toca, incluindo repetições. Você pode especificar uma duração usando um valor de tempo finito ou os valores especiais <xref:System.Windows.Duration.Automatic%2A> ou <xref:System.Windows.Duration.Forever%2A>. A duração de uma animação deve ser resolvida para um valor <xref:System.Windows.Duration.TimeSpan%2A>, para que possa fazer a transição entre valores.  
  
 O exemplo a seguir mostra um <xref:System.Windows.Media.Animation.DoubleAnimation> com um <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de cinco segundos.  
  
 [!code-xaml[animation_ovws_snippet#AnimationWith5SecondDurationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#animationwith5seconddurationinline)]  
  
 As linhas do tempo do contêiner, como <xref:System.Windows.Media.Animation.Storyboard> e <xref:System.Windows.Media.Animation.ParallelTimeline>, têm uma duração padrão de <xref:System.Windows.Duration.Automatic%2A>, o que significa que elas terminam automaticamente quando o último filho pára de ser tocado. O exemplo a seguir mostra um <xref:System.Windows.Media.Animation.Storyboard> cujo <xref:System.Windows.Media.Animation.Timeline.Duration%2A> é resolvido para cinco segundos, o período de tempo que leva para a conclusão de todos os seus objetos filho <xref:System.Windows.Media.Animation.DoubleAnimation>.  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelineexampleinline)]  
  
 Ao definir a <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de uma linha do tempo de contêiner para um valor de <xref:System.Windows.Duration.TimeSpan%2A>, você pode forçar a reprodução mais longa ou menor do que a de seus objetos <xref:System.Windows.Media.Animation.Timeline> filhos. Se você definir o <xref:System.Windows.Media.Animation.Timeline.Duration%2A> como um valor que seja menor do que o comprimento dos objetos de <xref:System.Windows.Media.Animation.Timeline> filho da linha do tempo do contêiner, os objetos <xref:System.Windows.Media.Animation.Timeline> filhos deixarão de ser reproduzidos quando a linha do tempo do contêiner. O exemplo a seguir define a <xref:System.Windows.Media.Animation.Timeline.Duration%2A> do <xref:System.Windows.Media.Animation.Storyboard> dos exemplos anteriores para três segundos. Como resultado, o primeiro <xref:System.Windows.Media.Animation.DoubleAnimation> parar de progredir após três segundos, quando ele tiver animado a largura do retângulo de destino para 60.  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineWithShorterDurationExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelinewithshorterdurationexampleinline)]  
  
<a name="repeatinganimations"></a>   
### <a name="the-repeatbehavior-property"></a>A propriedade RepeatBehavior  
 A propriedade <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> de um <xref:System.Windows.Media.Animation.Timeline> controla quantas vezes ele repete sua duração simples. Usando a propriedade <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, você pode especificar quantas vezes a linha do tempo é reproduzida (uma iteração <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>) ou o período total de tempo que deve ser reproduzido (um <xref:System.Windows.Media.Animation.RepeatBehavior.Duration%2A>repetido). Em ambos os casos, a animação passa por quantas execuções do início ao fim forem necessárias para completar a contagem ou duração solicitada. Por padrão, os cronogramas têm uma contagem de iteração de `1.0`, o que significa que eles são executados uma vez e não se repetem.  
  
 O exemplo a seguir usa a propriedade <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> para fazer com que uma <xref:System.Windows.Media.Animation.DoubleAnimation> reproduza duas vezes sua duração simples, especificando uma contagem de iteração.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior2xExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior2xexampleinline)]  
  
 O exemplo a seguir usa a propriedade <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> para fazer com que a <xref:System.Windows.Media.Animation.DoubleAnimation> Jogue pela metade da sua duração simples.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior05xExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior05xexampleinline)]  
  
 Se você definir a propriedade <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> de uma <xref:System.Windows.Media.Animation.Timeline> como <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, a <xref:System.Windows.Media.Animation.Timeline> será repetida até ser interrompida interativamente ou pelo sistema de tempo. O exemplo a seguir usa a propriedade <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> para fazer a <xref:System.Windows.Media.Animation.DoubleAnimation> reproduzir indefinidamente.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehaviorForeverExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehaviorforeverexampleinline)]  
  
 Para obter um exemplo adicional, consulte [repetir uma animação](how-to-repeat-an-animation.md).  
  
<a name="autoreverseproperty"></a>   
### <a name="the-autoreverse-property"></a>A propriedade AutoReverse  
 A propriedade <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> especifica se uma <xref:System.Windows.Media.Animation.Timeline> será reproduzida no final de cada iteração posterior. O exemplo a seguir define como a propriedade <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> de uma <xref:System.Windows.Media.Animation.DoubleAnimation> como `true`; Como resultado, ele anima de zero a 100 e, em seguida, de 100 a zero. Ela será executada por um total de 10 segundos.  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverseexampleinline)]  
  
 Quando você usa um valor de <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A> para especificar a <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> de um <xref:System.Windows.Media.Animation.Timeline> e a propriedade <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> dessa <xref:System.Windows.Media.Animation.Timeline> é `true`da, uma única repetição consiste em uma iteração posterior seguida de uma iteração para trás.  O exemplo a seguir define a <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> do <xref:System.Windows.Media.Animation.DoubleAnimation> do exemplo anterior para um <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A> de dois. Como resultado, a <xref:System.Windows.Media.Animation.DoubleAnimation> é reproduzida por 20 segundos: encaminhar por cinco segundos, para trás por cinco segundos, encaminhar por 5 segundos novamente e, em seguida, para trás por cinco segundos.  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseRepeatExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverserepeatexampleinline)]  
  
 Se uma linha do tempo de contêiner tiver objetos de <xref:System.Windows.Media.Animation.Timeline> filhos, eles serão invertidos quando a linha do tempo do contêiner fizer. Para obter exemplos adicionais, consulte [especificar se uma linha do tempo é revertida automaticamente](how-to-specify-whether-a-timeline-automatically-reverses.md).  
  
<a name="timelinebegin"></a>   
## <a name="the-begintime-property"></a>A propriedade BeginTime  
 A propriedade <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> permite que você especifique quando uma linha do tempo é iniciada.  A hora de início de uma linha do tempo é relativa à sua linha do tempo pai. Uma hora de início de zero segundos significa que a linha do tempo se inicia assim que o pai iniciar. Qualquer outro valor cria um deslocamento entre o momento em que a linha do tempo pai inicia a execução e o momento em que a linha do tempo filho é executada. Por exemplo, uma hora de início de dois segundos significa que a linha do tempo começa sua execução quando sua linha do tempo pai atinge um tempo de dois segundos. Por padrão, todas as linhas do tempo têm uma hora de início de zero segundos. Você também pode definir a hora de início de uma linha do tempo para `null`, o que impede que a linha do tempo seja iniciada. Em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], você especifica NULL usando a [extensão de marcação x:NULL](../../../desktop-wpf/xaml-services/xnull-markup-extension.md).  
  
 Observe que a hora de início não é aplicada a cada vez que uma linha do tempo se repete devido à sua configuração de <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>. Se você criasse uma animação com um <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> de 10 segundos e uma <xref:System.Windows.Media.Animation.RepeatBehavior> de <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, haveria um atraso de 10 segundo antes da animação ser executada pela primeira vez, mas não para cada repetição sucessiva. No entanto, se a linha do tempo da animação pai fosse reiniciada ou repetida, o atraso de 10 segundos ocorreria.  
  
 A propriedade <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> é útil para linhas do tempo escalonadas. O exemplo a seguir cria um <xref:System.Windows.Media.Animation.Storyboard> que tem dois objetos de <xref:System.Windows.Media.Animation.DoubleAnimation> filho. A primeira animação tem um <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de cinco segundos e a segunda tem um <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de 3 segundos. O exemplo define o <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> do segundo <xref:System.Windows.Media.Animation.DoubleAnimation> como 5 segundos, para que ele comece a ser reproduzido após o primeiro <xref:System.Windows.Media.Animation.DoubleAnimation> terminar.  
  
 [!code-xaml[animation_ovws_snippet#TBBeginTimeExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbbegintimeexampleinline)]  
  
<a name="fillbehaviorproperty"></a>   
## <a name="the-fillbehavior-property"></a>A propriedade FillBehavior  
 Quando um <xref:System.Windows.Media.Animation.Timeline> atinge o final de sua duração ativa total, a propriedade <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> especifica se ele interrompe ou mantém seu último valor. Uma animação com uma <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> de <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd> "retém" seu valor de saída: a propriedade que está sendo animada retém o último valor da animação. Um valor de <xref:System.Windows.Media.Animation.FillBehavior.Stop> faz com que a animação pare de afetar sua propriedade de destino depois de terminar.  
  
 O exemplo a seguir cria um <xref:System.Windows.Media.Animation.Storyboard> que tem dois objetos de <xref:System.Windows.Media.Animation.DoubleAnimation> filho. Ambos os objetos <xref:System.Windows.Media.Animation.DoubleAnimation> animam a <xref:System.Windows.FrameworkElement.Width%2A> de um <xref:System.Windows.Shapes.Rectangle> de 0 a 100. Os elementos de <xref:System.Windows.Shapes.Rectangle> têm valores de <xref:System.Windows.FrameworkElement.Width%2A> não animados de 500 [pixels independentes de dispositivo].  
  
- A propriedade <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> da primeira <xref:System.Windows.Media.Animation.DoubleAnimation> é definida como <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, o valor padrão. Como resultado, a largura do retângulo permanece em 100 depois que o <xref:System.Windows.Media.Animation.DoubleAnimation> termina.  
  
- A propriedade <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> da segunda <xref:System.Windows.Media.Animation.DoubleAnimation> é definida como <xref:System.Windows.Media.Animation.FillBehavior.Stop>. Como resultado, o <xref:System.Windows.FrameworkElement.Width%2A> da segunda <xref:System.Windows.Shapes.Rectangle> reverte para 500 depois que o <xref:System.Windows.Media.Animation.DoubleAnimation> termina.  
  
 [!code-xaml[animation_ovws_snippet#TBFillBehaviorExample](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbfillbehaviorexample)]  
  
<a name="speedproperties"></a>   
## <a name="properties-that-control-the-speed-of-a-timeline"></a>Propriedades que controlam a velocidade de uma linha do tempo  
 A classe <xref:System.Windows.Media.Animation.Timeline> fornece três propriedades para especificar sua velocidade:  
  
- <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> – especifica essa taxa, em relação ao seu pai, em que o tempo progride para uma <xref:System.Windows.Media.Animation.Timeline>. Valores maiores que um aumentam a velocidade do <xref:System.Windows.Media.Animation.Timeline> e seus objetos <xref:System.Windows.Media.Animation.Timeline> filho; os valores entre zero e um tornam-os mais lentos. Um valor de um indica que <xref:System.Windows.Media.Animation.Timeline> progride na mesma taxa que seu pai. A configuração de <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> de uma linha do tempo de contêiner afeta todos os seus objetos de <xref:System.Windows.Media.Animation.Timeline> filhos também.  
  
- <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> – especifica a porcentagem da <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de uma linha do tempo gasta acelerando. Para obter um exemplo, consulte [como: acelerar ou desacelerar uma animação](how-to-accelerate-or-decelerate-an-animation.md). 
  
- <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A>-especifica a porcentagem do <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de uma linha do tempo gasto decelerating. Para obter um exemplo, consulte [como: acelerar ou desacelerar uma animação](how-to-accelerate-or-decelerate-an-animation.md).  
  
## <a name="see-also"></a>Veja também

- [Visão geral da animação](animation-overview.md)
- [Visão geral da animação e do sistema de tempo](animation-and-timing-system-overview.md)
- [Visão geral de eventos de tempo](timing-events-overview.md)
- [Tópicos de instruções](animation-and-timing-how-to-topics.md)
- [Amostra de comportamento de tempo da animação](https://go.microsoft.com/fwlink/?LinkID=159970)
