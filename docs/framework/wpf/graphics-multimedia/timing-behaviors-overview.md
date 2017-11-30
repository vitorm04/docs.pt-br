---
title: "Visão geral dos comportamentos de tempo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- timing behaviors [WPF]
- behaviors [WPF], timing
ms.assetid: 5b714d46-bd46-48b8-b467-b4be89ba3091
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ac6671033a439051b062ddae70649a63bacd4979
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="timing-behaviors-overview"></a>Visão geral dos comportamentos de tempo
Este tópico descreve os comportamentos de temporização de animações e outros <xref:System.Windows.Media.Animation.Timeline> objetos.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Pré-requisitos  
 Para entender este tópico, você deve estar familiarizado com recursos básicos de animação. Para obter mais informações, consulte o [visão geral de animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
<a name="timelinetypes"></a>   
## <a name="timeline-types"></a>Tipos de linha do tempo  
 Um <xref:System.Windows.Media.Animation.Timeline> representa um segmento de tempo. Ela fornece propriedades que permitem que você especifique o comprimento desse segmento, quando ele deve ser iniciado, quantas vezes ele se repetirá, quão rápido o tempo progride nesse segmento e muito mais.  
  
 As classes que herdam da classe linha do tempo fornecem funcionalidades adicionais, como animação e reprodução de mídia. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fornece o seguinte <xref:System.Windows.Media.Animation.Timeline> tipos.  
  
|Tipo de linha do tempo|Descrição|  
|-------------------|-----------------|  
|<xref:System.Windows.Media.Animation.AnimationTimeline>|Classe abstrata base para <xref:System.Windows.Media.Animation.Timeline> objetos que geram valores de saída para animação de propriedades.|  
|<xref:System.Windows.Media.MediaTimeline>|Gera a saída de um arquivo de mídia.|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|Um tipo de <xref:System.Windows.Media.Animation.TimelineGroup> criança grupos e controles <xref:System.Windows.Media.Animation.Timeline> objetos.|  
|<xref:System.Windows.Media.Animation.Storyboard>|Um tipo de <xref:System.Windows.Media.Animation.ParallelTimeline> que fornece informações de direcionamento para os objetos de Timeline que ele contém.|  
|<xref:System.Windows.Media.Animation.Timeline>|Classe base abstrata que define comportamentos de tempo.|  
|<xref:System.Windows.Media.Animation.TimelineGroup>|Classe abstrata para <xref:System.Windows.Media.Animation.Timeline> objetos que podem conter outros <xref:System.Windows.Media.Animation.Timeline> objetos.|  
  
<a name="propertiesthatcontroltimelinelength"></a>   
## <a name="properties-that-control-the-length-of-a-timeline"></a>Propriedades que controlam o comprimento de uma linha do tempo  
 Um <xref:System.Windows.Media.Animation.Timeline> representa um segmento de tempo e o comprimento de uma linha do tempo podem ser descrito de maneiras diferentes. A tabela a seguir define diversos termos para descrever o comprimento de uma linha do tempo.  
  
|Termo|Descrição|Propriedades||||  
|----------|-----------------|----------------|-|-|-|  
|Duração simples|O tempo que uma linha do tempo leva para realizar uma única iteração.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>||||  
|Uma repetição|O período de tempo que leva para uma linha de tempo tocar uma vez e, se o <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> propriedade for verdadeira, tocar ao contrário uma vez.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>||||  
|Período ativo|O período de tempo que leva para uma linha do tempo concluir todas as repetições especificadas por sua <xref:System.Windows.Media.Animation.RepeatBehavior> propriedade.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>, <xref:System.Windows.Media.Animation.RepeatBehavior>||||  
  
<a name="duration"></a>   
### <a name="the-duration-property"></a>A propriedade Duration  
 Conforme mencionado anteriormente, uma linha do tempo representa um segmento de tempo. O comprimento do segmento é determinado pela linha do tempo <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. Quando uma linha de tempo alcança o final de sua duração, sua execução é interrompida. Se a linha do tempo tiver linhas do tempo filho, a execução delas também será interrompida. No caso de uma animação, a <xref:System.Windows.Media.Animation.Timeline.Duration%2A> Especifica quanto tempo a animação leva para fazer a transição do seu valor inicial ao seu valor final. Duração da linha de tempo é geralmente chamada de seu *duração simples*, para distinguir entre a duração de uma única iteração e o comprimento total de tempo que a animação é reproduzida incluindo repetições. Você pode especificar uma duração usando um valor de tempo finito ou os valores especiais <xref:System.Windows.Duration.Automatic%2A> ou <xref:System.Windows.Duration.Forever%2A>. Duração de uma animação deve resolver para um <xref:System.Windows.Duration.TimeSpan%2A> de valor, portanto ele pode fazer a transição entre valores.  
  
 A exemplo a seguir mostra um <xref:System.Windows.Media.Animation.DoubleAnimation> com um <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de cinco segundos.  
  
 [!code-xaml[animation_ovws_snippet#AnimationWith5SecondDurationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#animationwith5seconddurationinline)]  
  
 Cronogramas de contêiner, como <xref:System.Windows.Media.Animation.Storyboard> e <xref:System.Windows.Media.Animation.ParallelTimeline>, ter uma duração padrão de <xref:System.Windows.Duration.Automatic%2A>, o que significa que elas automaticamente terminam quando seu último filho termina de executar. A exemplo a seguir mostra um <xref:System.Windows.Media.Animation.Storyboard> cujo <xref:System.Windows.Media.Animation.Timeline.Duration%2A> resolvida como cinco segundos, o período de tempo que leva a todos os seus filhos <xref:System.Windows.Media.Animation.DoubleAnimation> objetos para concluir.  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelineexampleinline)]  
  
 Definindo o <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de um cronograma de contêiner para um <xref:System.Windows.Duration.TimeSpan%2A> valor, você pode forçar a reproduzir maiores ou menores que seu filho <xref:System.Windows.Media.Animation.Timeline> teria objetos. Se você definir o <xref:System.Windows.Media.Animation.Timeline.Duration%2A> para um valor menor que o comprimento do filho do cronograma contêiner <xref:System.Windows.Media.Animation.Timeline> objetos, o filho <xref:System.Windows.Media.Animation.Timeline> objetos parar a execução quando a linha do tempo do contêiner. O exemplo a seguir define o <xref:System.Windows.Media.Animation.Timeline.Duration%2A> do <xref:System.Windows.Media.Animation.Storyboard> dos exemplos anteriores para três segundos. Como resultado, a primeira <xref:System.Windows.Media.Animation.DoubleAnimation> para de progredir após três segundos, quando ela tiver animado a largura do retângulo alvo até 60.  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineWithShorterDurationExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelinewithshorterdurationexampleinline)]  
  
<a name="repeatinganimations"></a>   
### <a name="the-repeatbehavior-property"></a>A propriedade RepeatBehavior  
 O <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> propriedade de um <xref:System.Windows.Media.Animation.Timeline> controla quantas vezes ela repete sua duração simple. Usando o <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> propriedade, você pode especificar quantas vezes as opções de linha de tempo (uma iteração <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>) ou o comprimento total de tempo deve ser executada (uma repetição <xref:System.Windows.Media.Animation.RepeatBehavior.Duration%2A>). Em ambos os casos, a animação passa por quantas execuções do início ao fim forem necessárias para completar a contagem ou duração solicitada. Por padrão, linhas de tempo tem uma contagem de iteração de `1.0`, que significa que elas tocam uma vez e não repetem.  
  
 O exemplo a seguir usa o <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> propriedade para tornar um <xref:System.Windows.Media.Animation.DoubleAnimation> executada durante o dobro de sua duração simple especificando uma contagem de iteração.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior2xExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior2xexampleinline)]  
  
 O exemplo a seguir usa o <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> propriedade para tornar o <xref:System.Windows.Media.Animation.DoubleAnimation> executado por meio de sua duração simples.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior05xExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior05xexampleinline)]  
  
 Se você definir o <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> propriedade de um <xref:System.Windows.Media.Animation.Timeline> para <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, o <xref:System.Windows.Media.Animation.Timeline> se repete até ser interrompido de forma interativa ou pelo sistema de temporização. O exemplo a seguir usa o <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> propriedade para tornar o <xref:System.Windows.Media.Animation.DoubleAnimation> reproduzir indefinidamente.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehaviorForeverExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehaviorforeverexampleinline)]  
  
 Para obter um exemplo adicional, consulte [repetir uma animação](../../../../docs/framework/wpf/graphics-multimedia/how-to-repeat-an-animation.md).  
  
<a name="autoreverseproperty"></a>   
### <a name="the-autoreverse-property"></a>A propriedade AutoReverse  
 O <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> propriedade especifica se um <xref:System.Windows.Media.Animation.Timeline> funcionará com versões anteriores do final de cada iteração direta. O exemplo a seguir define como o <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> propriedade de um <xref:System.Windows.Media.Animation.DoubleAnimation> para `true`; como resultado, ele anima de zero a 100 e, em seguida, de 100 a zero. Ela será executada por um total de 10 segundos.  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverseexampleinline)]  
  
 Quando você usa um <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A> valor para especificar o <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> de um <xref:System.Windows.Media.Animation.Timeline> e <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> propriedade que <xref:System.Windows.Media.Animation.Timeline> é `true`, uma única repetição consiste em uma interação direta seguida por uma iteração com versões anteriores.  O exemplo a seguir define o <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> do <xref:System.Windows.Media.Animation.DoubleAnimation> do exemplo anterior para um <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A> de dois. Como resultado, o <xref:System.Windows.Media.Animation.DoubleAnimation> será executada por 20 segundos: para frente por cinco segundos, para trás por cinco segundos, para frente por 5 segundos novamente e para trás por cinco segundos.  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseRepeatExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverserepeatexampleinline)]  
  
 Se uma linha do tempo do contêiner filho <xref:System.Windows.Media.Animation.Timeline> objetos, eles são revertidos quando a linha do tempo do contêiner. Para obter exemplos adicionais, consulte [especificar se uma linha do tempo automaticamente reverte](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-whether-a-timeline-automatically-reverses.md).  
  
<a name="timelinebegin"></a>   
## <a name="the-begintime-property"></a>A propriedade BeginTime  
 O <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> propriedade permite que você especifique o início de uma linha do tempo.  A hora de início de uma linha do tempo é relativa à sua linha do tempo pai. Uma hora de início de zero segundos significa que a linha do tempo se inicia assim que o pai iniciar. Qualquer outro valor cria um deslocamento entre o momento em que a linha do tempo pai inicia a execução e o momento em que a linha do tempo filho é executada. Por exemplo, uma hora de início de dois segundos significa que a linha do tempo começa sua execução quando sua linha do tempo pai atinge um tempo de dois segundos. Por padrão, todas as linhas do tempo têm uma hora de início de zero segundos. Você também pode definir um cronograma começar tempo para `null`, que impede que a linha do tempo seja iniciado. Em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], você especifica null usando o [extensão de marcação X:Null](../../../../docs/framework/xaml-services/x-null-markup-extension.md).  
  
 Observe que a hora de início não é aplicado sempre que uma linha do tempo se repete porque seu <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> configuração. Se você criar uma animação com um <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> de 10 segundos e um <xref:System.Windows.Media.Animation.RepeatBehavior> de <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, deve haver um atraso de 10 segundos antes da animação ser executada pela primeira vez, mas não para cada repetição sucessiva. No entanto, se a linha do tempo da animação pai fosse reiniciada ou repetida, o atraso de 10 segundos ocorreria.  
  
 O <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> propriedade é útil para encadear linhas de tempo. O exemplo a seguir cria um <xref:System.Windows.Media.Animation.Storyboard> que tem dois filhos <xref:System.Windows.Media.Animation.DoubleAnimation> objetos. A primeira animação tem um <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de cinco segundos, e o segundo tem uma <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de 3 segundos. O exemplo define o <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> da segunda <xref:System.Windows.Media.Animation.DoubleAnimation> para 5 segundos, assim que ele comece a ser executada após a primeira <xref:System.Windows.Media.Animation.DoubleAnimation> termina.  
  
 [!code-xaml[animation_ovws_snippet#TBBeginTimeExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbbegintimeexampleinline)]  
  
<a name="fillbehaviorproperty"></a>   
## <a name="the-fillbehavior-property"></a>A propriedade FillBehavior  
 Quando um <xref:System.Windows.Media.Animation.Timeline> atinge o final de sua duração total ativa, o <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> propriedade especifica se ela para ou se mantém seu último valor. Uma animação com um <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> de <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd> "segura" o valor de saída: a propriedade sendo animada retém o último valor da animação. Um valor de <xref:System.Windows.Media.Animation.FillBehavior.Stop> faz com que a animação pare de afetar sua propriedade de destino após seu término.  
  
 O exemplo a seguir cria um <xref:System.Windows.Media.Animation.Storyboard> que tem dois filhos <xref:System.Windows.Media.Animation.DoubleAnimation> objetos. Ambos <xref:System.Windows.Media.Animation.DoubleAnimation> animam objetos o <xref:System.Windows.FrameworkElement.Width%2A> de um <xref:System.Windows.Shapes.Rectangle> de 0 a 100. O <xref:System.Windows.Shapes.Rectangle> elementos têm não animado <xref:System.Windows.FrameworkElement.Width%2A> valores de 500 [pixels independentes de dispositivo].  
  
-   O <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> propriedade do primeiro <xref:System.Windows.Media.Animation.DoubleAnimation> é definido como <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, o valor padrão. Como resultado, a largura do retângulo permanece em 100 após a <xref:System.Windows.Media.Animation.DoubleAnimation> termina.  
  
-   O <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> propriedade da segunda <xref:System.Windows.Media.Animation.DoubleAnimation> é definido como <xref:System.Windows.Media.Animation.FillBehavior.Stop>. Como resultado, o <xref:System.Windows.FrameworkElement.Width%2A> da segunda <xref:System.Windows.Shapes.Rectangle> volta para 500 após a <xref:System.Windows.Media.Animation.DoubleAnimation> termina.  
  
 [!code-xaml[animation_ovws_snippet#TBFillBehaviorExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbfillbehaviorexample)]  
  
<a name="speedproperties"></a>   
## <a name="properties-that-control-the-speed-of-a-timeline"></a>Propriedades que controlam a velocidade de uma linha do tempo  
 O <xref:System.Windows.Media.Animation.Timeline> classe fornece três propriedades para especificar sua velocidade:  
  
-   <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A>– Especifica a taxa, em relação ao seu pai, na qual progride o tempo para um <xref:System.Windows.Media.Animation.Timeline>. Valores maiores do que um aumentam a velocidade do <xref:System.Windows.Media.Animation.Timeline> e seu filho <xref:System.Windows.Media.Animation.Timeline> objetos, valores entre zero e um diminuem. Um valor de 1 indica que <xref:System.Windows.Media.Animation.Timeline> é feita com a mesma taxa como seu pai. O <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> configuração de tempo contêiner afeta todos os seus filhos <xref:System.Windows.Media.Animation.Timeline> objetos.  
  
-   <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A>– Especifica a porcentagem da <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de uma linha de tempo gasta acelerando. Para obter um exemplo, consulte [como: acelerar ou desacelerar uma animação](../../../../docs/framework/wpf/graphics-multimedia/how-to-accelerate-or-decelerate-an-animation.md). 
  
-   <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A>-Especifica a porcentagem da <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de uma linha do tempo gasto desacelerando. Para obter um exemplo, consulte [como: acelerar ou desacelerar uma animação](../../../../docs/framework/wpf/graphics-multimedia/how-to-accelerate-or-decelerate-an-animation.md).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Visão geral da animação e do sistema de tempo](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)  
 [Visão geral de eventos de tempo](../../../../docs/framework/wpf/graphics-multimedia/timing-events-overview.md)  
 [Tópicos explicativos](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)  
 [Amostra de comportamento de tempo da animação](http://go.microsoft.com/fwlink/?LinkID=159970)
