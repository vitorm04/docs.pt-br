---
title: Visão geral dos comportamentos de tempo
ms.date: 03/30/2017
helpviewer_keywords:
- timing behaviors [WPF]
- behaviors [WPF], timing
ms.assetid: 5b714d46-bd46-48b8-b467-b4be89ba3091
ms.openlocfilehash: 3bb42ddd991d3ae1221cc794afdd4aafc74a6046
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145391"
---
# <a name="timing-behaviors-overview"></a>Visão geral dos comportamentos de tempo
Este tópico descreve os comportamentos de tempo <xref:System.Windows.Media.Animation.Timeline> de animações e outros objetos.  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Pré-requisitos  
 Para entender este tópico, você deve estar familiarizado com recursos básicos de animação. Para obter mais informações, consulte a [visão geral da animação](animation-overview.md).  
  
<a name="timelinetypes"></a>
## <a name="timeline-types"></a>Tipos de linha do tempo  
 Um <xref:System.Windows.Media.Animation.Timeline> representa um segmento de tempo. Ela fornece propriedades que permitem que você especifique o comprimento desse segmento, quando ele deve ser iniciado, quantas vezes ele se repetirá, quão rápido o tempo progride nesse segmento e muito mais.  
  
 As classes que herdam da classe linha do tempo fornecem funcionalidades adicionais, como animação e reprodução de mídia. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fornece os <xref:System.Windows.Media.Animation.Timeline> seguintes tipos.  
  
|Tipo de linha do tempo|Descrição|  
|-------------------|-----------------|  
|<xref:System.Windows.Media.Animation.AnimationTimeline>|Classe base <xref:System.Windows.Media.Animation.Timeline> abstrata para objetos que geram valores de saída para propriedades animadoras.|  
|<xref:System.Windows.Media.MediaTimeline>|Gera a saída de um arquivo de mídia.|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|Um tipo <xref:System.Windows.Media.Animation.TimelineGroup> disso agrupa e <xref:System.Windows.Media.Animation.Timeline> controla objetos infantis.|  
|<xref:System.Windows.Media.Animation.Storyboard>|Um tipo <xref:System.Windows.Media.Animation.ParallelTimeline> que fornece informações de segmentação para os objetos Timeline que ele contém.|  
|<xref:System.Windows.Media.Animation.Timeline>|Classe base abstrata que define comportamentos de tempo.|  
|<xref:System.Windows.Media.Animation.TimelineGroup>|Classe abstrata <xref:System.Windows.Media.Animation.Timeline> para objetos <xref:System.Windows.Media.Animation.Timeline> que podem conter outros objetos.|  
  
<a name="propertiesthatcontroltimelinelength"></a>
## <a name="properties-that-control-the-length-of-a-timeline"></a>Propriedades que controlam o comprimento de uma linha do tempo  
 A <xref:System.Windows.Media.Animation.Timeline> representa um segmento de tempo, e o comprimento de uma linha do tempo pode ser descrito de diferentes maneiras. A tabela a seguir define diversos termos para descrever o comprimento de uma linha do tempo.  
  
|Termo|Descrição|Propriedades||||  
|----------|-----------------|----------------|-|-|-|  
|Duração simples|O tempo que uma linha do tempo leva para realizar uma única iteração.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>||||  
|Uma repetição|O tempo que leva para uma linha do tempo <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> para jogar para a frente uma vez e, se a propriedade for verdadeira, jogue para trás uma vez.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>||||  
|Período ativo|O tempo que leva para uma linha do tempo para <xref:System.Windows.Media.Animation.RepeatBehavior> completar todas as repetições especificadas por sua propriedade.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>, <xref:System.Windows.Media.Animation.RepeatBehavior>||||  
  
<a name="duration"></a>
### <a name="the-duration-property"></a>A propriedade Duration  
 Conforme mencionado anteriormente, uma linha do tempo representa um segmento de tempo. O comprimento desse segmento é determinado <xref:System.Windows.Media.Animation.Timeline.Duration%2A>pela linha do tempo. Quando uma linha de tempo alcança o final de sua duração, sua execução é interrompida. Se a linha do tempo tiver linhas do tempo filho, a execução delas também será interrompida. No caso de uma <xref:System.Windows.Media.Animation.Timeline.Duration%2A> animação, o especifica quanto tempo a animação leva para fazer a transição do seu valor inicial para o seu valor final. A duração de uma linha do tempo é às vezes chamada de *duração simples,* para distinguir entre a duração de uma única iteração e o tempo total que a animação reproduz, incluindo repetições. Você pode especificar uma duração usando um valor <xref:System.Windows.Duration.Automatic%2A> <xref:System.Windows.Duration.Forever%2A>de tempo finito ou os valores especiais ou . A duração de uma animação <xref:System.Windows.Duration.TimeSpan%2A> deve ser resolvida a um valor, para que possa fazer a transição entre os valores.  
  
 O exemplo a <xref:System.Windows.Media.Animation.DoubleAnimation> seguir <xref:System.Windows.Media.Animation.Timeline.Duration%2A> mostra um com um de cinco segundos.  
  
 [!code-xaml[animation_ovws_snippet#AnimationWith5SecondDurationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#animationwith5seconddurationinline)]  
  
 Os cronogramas dos <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.Animation.ParallelTimeline>contêineres, como <xref:System.Windows.Duration.Automatic%2A>e , têm uma duração padrão de , o que significa que eles terminam automaticamente quando seu último filho para de brincar. O exemplo a <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.Animation.Timeline.Duration%2A> seguir mostra um cuja determina para cinco segundos, o tempo que leva todos os seus objetos filho <xref:System.Windows.Media.Animation.DoubleAnimation> para completar.  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelineexampleinline)]  
  
 Ao definir <xref:System.Windows.Media.Animation.Timeline.Duration%2A> a linha do <xref:System.Windows.Duration.TimeSpan%2A> tempo de um contêiner para um valor, você pode forçar a jogar mais ou menos do que seus objetos infantis <xref:System.Windows.Media.Animation.Timeline> reproduziriam. Se você <xref:System.Windows.Media.Animation.Timeline.Duration%2A> definir o valor menor do que o comprimento dos <xref:System.Windows.Media.Animation.Timeline> objetos filho <xref:System.Windows.Media.Animation.Timeline> da linha do tempo do contêiner, os objetos da criança param de jogar quando a linha do tempo do contêiner o faz. O exemplo a <xref:System.Windows.Media.Animation.Timeline.Duration%2A> seguir <xref:System.Windows.Media.Animation.Storyboard> define o dos exemplos anteriores para três segundos. Como resultado, as <xref:System.Windows.Media.Animation.DoubleAnimation> primeiras paradas progridem após três segundos, quando ele tem animado a largura do retângulo alvo para 60.  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineWithShorterDurationExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelinewithshorterdurationexampleinline)]  
  
<a name="repeatinganimations"></a>
### <a name="the-repeatbehavior-property"></a>A propriedade RepeatBehavior  
 A <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> propriedade <xref:System.Windows.Media.Animation.Timeline> de um controla quantas vezes ele repete sua duração simples. Usando <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> a propriedade, você pode especificar quantas vezes <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>a linha do tempo é reproduzda <xref:System.Windows.Media.Animation.RepeatBehavior.Duration%2A>(uma iteração ) ou o tempo total de reprodução (uma repetição ). Em ambos os casos, a animação passa por quantas execuções do início ao fim forem necessárias para completar a contagem ou duração solicitada. Por padrão, os cronogramas têm `1.0`uma contagem de iteração de , o que significa que eles jogam uma vez e não se repetem em tudo.  
  
 O exemplo a <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> seguir usa <xref:System.Windows.Media.Animation.DoubleAnimation> a propriedade para fazer uma jogada pelo dobro de sua duração simples, especificando uma contagem de iteração.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior2xExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior2xexampleinline)]  
  
 O próximo exemplo <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> usa a <xref:System.Windows.Media.Animation.DoubleAnimation> propriedade para fazer a jogada por metade de sua duração simples.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior05xExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior05xexampleinline)]  
  
 Se você <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> definir a <xref:System.Windows.Media.Animation.Timeline> <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>propriedade <xref:System.Windows.Media.Animation.Timeline> de a , as repetições até paradas interativamente ou pelo sistema de tempo. O exemplo a <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> seguir usa <xref:System.Windows.Media.Animation.DoubleAnimation> a propriedade para fazer a jogada indefinidamente.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehaviorForeverExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehaviorforeverexampleinline)]  
  
 Para um exemplo adicional, consulte [Repetir uma animação](how-to-repeat-an-animation.md).  
  
<a name="autoreverseproperty"></a>
### <a name="the-autoreverse-property"></a>A propriedade AutoReverse  
 A <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> propriedade especifica <xref:System.Windows.Media.Animation.Timeline> se um será retolado no final de cada iteração para a frente. O exemplo a <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> seguir define <xref:System.Windows.Media.Animation.DoubleAnimation> `true`a propriedade de a; como resultado, ele anima de zero a 100, e depois de 100 a zero. Ela será executada por um total de 10 segundos.  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverseexampleinline)]  
  
 Quando você <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A> usa um <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> valor <xref:System.Windows.Media.Animation.Timeline> para <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> especificar <xref:System.Windows.Media.Animation.Timeline> a `true`propriedade de a e a propriedade disso é, uma única repetição consiste em uma iteração para a frente seguida de uma iteração para trás.  O exemplo a <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> seguir <xref:System.Windows.Media.Animation.DoubleAnimation> define o do <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A> exemplo anterior para um de dois. Como resultado, <xref:System.Windows.Media.Animation.DoubleAnimation> as jogadas por 20 segundos: para frente por cinco segundos, para trás por cinco segundos, para frente por 5 segundos novamente, e depois para trás por cinco segundos.  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseRepeatExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverserepeatexampleinline)]  
  
 Se a linha <xref:System.Windows.Media.Animation.Timeline> do tempo de um contêiner tiver objetos-filho, eles revertem quando a linha do tempo do contêiner o fizer. Para exemplos adicionais, consulte [Especificar se uma linha do tempo inverte automaticamente](how-to-specify-whether-a-timeline-automatically-reverses.md).  
  
<a name="timelinebegin"></a>
## <a name="the-begintime-property"></a>A propriedade BeginTime  
 A <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> propriedade permite que você especifique quando uma linha do tempo é iniciada.  A hora de início de uma linha do tempo é relativa à sua linha do tempo pai. Uma hora de início de zero segundos significa que a linha do tempo se inicia assim que o pai iniciar. Qualquer outro valor cria um deslocamento entre o momento em que a linha do tempo pai inicia a execução e o momento em que a linha do tempo filho é executada. Por exemplo, uma hora de início de dois segundos significa que a linha do tempo começa sua execução quando sua linha do tempo pai atinge um tempo de dois segundos. Por padrão, todas as linhas do tempo têm uma hora de início de zero segundos. Você também pode definir a hora `null`de início de uma linha do tempo, o que impede que a linha do tempo comece. In [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], você especifica nulo usando a [extensão x:Null Markup](../../../desktop-wpf/xaml-services/xnull-markup-extension.md).  
  
 Observe que a hora de início não é aplicada <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> cada vez que uma linha do tempo se repete por causa de sua configuração. Se você fosse criar uma <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> animação com um <xref:System.Windows.Media.Animation.RepeatBehavior> <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>de 10 segundos e um de , haveria um atraso de 10 segundos antes da animação ser reproduzida pela primeira vez, mas não para cada repetição sucessiva. No entanto, se a linha do tempo da animação pai fosse reiniciada ou repetida, o atraso de 10 segundos ocorreria.  
  
 A <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> propriedade é útil para cronogramas surpreendentes. O exemplo a <xref:System.Windows.Media.Animation.Storyboard> seguir cria <xref:System.Windows.Media.Animation.DoubleAnimation> um que tem dois objetos-filho. A primeira animação <xref:System.Windows.Media.Animation.Timeline.Duration%2A> tem um de cinco <xref:System.Windows.Media.Animation.Timeline.Duration%2A> segundos, e a segunda tem 3 segundos. O exemplo <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> define o <xref:System.Windows.Media.Animation.DoubleAnimation> do segundo a 5 segundos, de <xref:System.Windows.Media.Animation.DoubleAnimation> modo que ele começa a jogar após as primeiras extremidades.  
  
 [!code-xaml[animation_ovws_snippet#TBBeginTimeExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbbegintimeexampleinline)]  
  
<a name="fillbehaviorproperty"></a>
## <a name="the-fillbehavior-property"></a>A propriedade FillBehavior  
 Quando <xref:System.Windows.Media.Animation.Timeline> um atinge o fim de sua <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> duração ativa total, a propriedade especifica se ela pára ou mantém seu último valor. Uma animação <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> com <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd> um de "segura" seu valor de saída: a propriedade que está sendo animada retém o último valor da animação. Um valor <xref:System.Windows.Media.Animation.FillBehavior.Stop> de causas que a animação para de afetar sua propriedade de destino depois que ela termina.  
  
 O exemplo a <xref:System.Windows.Media.Animation.Storyboard> seguir cria <xref:System.Windows.Media.Animation.DoubleAnimation> um que tem dois objetos-filho. Ambos <xref:System.Windows.Media.Animation.DoubleAnimation> os objetos <xref:System.Windows.Shapes.Rectangle> animam de <xref:System.Windows.FrameworkElement.Width%2A> 0 a 100. Os <xref:System.Windows.Shapes.Rectangle> elementos têm <xref:System.Windows.FrameworkElement.Width%2A> valores não animados de 500 [pixels independentes do dispositivo].  
  
- A <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> propriedade do <xref:System.Windows.Media.Animation.DoubleAnimation> primeiro <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>é definida como , o valor padrão. Como resultado, a largura do retângulo permanece em <xref:System.Windows.Media.Animation.DoubleAnimation> 100 após o término.  
  
- A <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> propriedade do <xref:System.Windows.Media.Animation.DoubleAnimation> segundo <xref:System.Windows.Media.Animation.FillBehavior.Stop>está definida para . Como resultado, <xref:System.Windows.FrameworkElement.Width%2A> o do <xref:System.Windows.Shapes.Rectangle> segundo reverte para <xref:System.Windows.Media.Animation.DoubleAnimation> 500 após o término.  
  
 [!code-xaml[animation_ovws_snippet#TBFillBehaviorExample](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbfillbehaviorexample)]  
  
<a name="speedproperties"></a>
## <a name="properties-that-control-the-speed-of-a-timeline"></a>Propriedades que controlam a velocidade de uma linha do tempo  
 A <xref:System.Windows.Media.Animation.Timeline> classe fornece três propriedades para especificar sua velocidade:  
  
- <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A>– Especifica essa taxa, em relação ao seu pai, em que o tempo progride para um <xref:System.Windows.Media.Animation.Timeline>. Valores maiores que um <xref:System.Windows.Media.Animation.Timeline> aumentam <xref:System.Windows.Media.Animation.Timeline> a velocidade dos objetos e de seus filhos; valores entre zero e um retardá-lo. Um valor de <xref:System.Windows.Media.Animation.Timeline> um indica que progride na mesma taxa que seu pai. A <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> configuração de uma linha do <xref:System.Windows.Media.Animation.Timeline> tempo de contêiner afeta todos os objetos infantis também.  
  
- <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A>– Especifica a porcentagem <xref:System.Windows.Media.Animation.Timeline.Duration%2A> do cronograma gasto acelerando. Por exemplo, [consulte Como: Acelerar ou Desacelerar uma Animação](how-to-accelerate-or-decelerate-an-animation.md).
  
- <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A>- Especifica a porcentagem <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de uma linha do tempo gasta desacelerando. Por exemplo, [consulte Como: Acelerar ou Desacelerar uma Animação](how-to-accelerate-or-decelerate-an-animation.md).  
  
## <a name="see-also"></a>Confira também

- [Visão geral da animação](animation-overview.md)
- [Visão geral da animação e do sistema de tempo](animation-and-timing-system-overview.md)
- [Visão geral dos eventos de tempo](timing-events-overview.md)
- [Tópicos de como fazer](animation-and-timing-how-to-topics.md)
- [Amostra de comportamento de tempo da animação](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming)
