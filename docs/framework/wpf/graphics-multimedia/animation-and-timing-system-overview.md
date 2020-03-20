---
title: Visão geral da animação e do sistema de tempo
ms.date: 03/30/2017
helpviewer_keywords:
- timing system [WPF]
- animation [WPF]
ms.assetid: 172cd5a8-a333-4c81-9456-fafccc19f382
ms.openlocfilehash: d0ac2a8160a1e6f9bcdb333593ec207954b391aa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187718"
---
# <a name="animation-and-timing-system-overview"></a>Visão geral da animação e do sistema de tempo
Este tópico descreve como o sistema <xref:System.Windows.Media.Animation.Timeline>de <xref:System.Windows.Media.Animation.Clock> tempo usa a animação, e classes para animar propriedades.  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Pré-requisitos  
 Para entender esse tópico, você deve ser capaz de usar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animações para animar propriedades, conforme descrito na [Visão geral da animação](animation-overview.md). Ele também ajuda a se familiarizar com as propriedades de dependência; para obter mais informações, consulte o [visão geral das propriedades de dependência](../advanced/dependency-properties-overview.md).  
  
<a name="timelinesandclocks"></a>
## <a name="timelines-and-clocks"></a>Linhas de tempo e relógios  
 A [visão geral da animação](animation-overview.md) descreveu como um <xref:System.Windows.Media.Animation.Timeline> representa um segmento <xref:System.Windows.Media.Animation.Timeline> de tempo, e uma animação é um tipo de que produz valores de saída. Por si <xref:System.Windows.Media.Animation.Timeline>só, a não faz nada além de apenas descrever um segmento de tempo. É o <xref:System.Windows.Media.Animation.Clock> objeto da linha do tempo que faz o trabalho real. Da mesma forma, a animação não anima as propriedades: uma classe de animação descreve <xref:System.Windows.Media.Animation.Clock> como os valores de saída devem ser calculados, mas é o que foi criado para a animação que impulsiona a saída de animação e aplica-a às propriedades.  
  
 A <xref:System.Windows.Media.Animation.Clock> é um tipo especial de objeto que mantém <xref:System.Windows.Media.Animation.Timeline>o estado de tempo de execução relacionado ao tempo para o . Ele fornece três bits de informação que são <xref:System.Windows.Media.Animation.Clock.CurrentTime%2A>essenciais para o sistema de animação e tempo: , <xref:System.Windows.Media.Animation.Clock.CurrentProgress%2A>e <xref:System.Windows.Media.Animation.Clock.CurrentState%2A>. A <xref:System.Windows.Media.Animation.Clock> determina seu tempo, progresso e estado atuais usando <xref:System.Windows.Media.Animation.Timeline>os <xref:System.Windows.Media.Animation.Timeline.Duration%2A> <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>comportamentos <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>de tempo descritos por seu : , , , e assim por diante.  
  
 Na maioria dos <xref:System.Windows.Media.Animation.Clock> casos, um é criado automaticamente para sua linha do tempo. Quando você anima usando <xref:System.Windows.Media.Animation.Storyboard> um <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> ou o método, relógios são automaticamente criados para suas linhas temporais e animações e aplicados às suas propriedades-alvo. Você também pode <xref:System.Windows.Media.Animation.Clock> criar um <xref:System.Windows.Media.Animation.Timeline.CreateClock%2A> explicitamente usando <xref:System.Windows.Media.Animation.Timeline>o método do seu . O <xref:System.Windows.Media.MediaTimeline.CreateClock%2A?displayProperty=nameWithType> método cria um relógio do <xref:System.Windows.Media.Animation.Timeline> tipo apropriado para o qual é chamado. Se <xref:System.Windows.Media.Animation.Timeline> o contém cronogramas <xref:System.Windows.Media.Animation.Clock> de crianças, ele cria objetos para eles também. Os objetos resultantes <xref:System.Windows.Media.Animation.Clock> são dispostos em <xref:System.Windows.Media.Animation.Timeline> árvores que combinam com a estrutura da árvore de objetos de onde são criados.  
  
 Existem diferentes tipos de relógios para tipos diferentes de linhas de tempo. A tabela a <xref:System.Windows.Media.Animation.Clock> seguir mostra os tipos <xref:System.Windows.Media.Animation.Timeline> que correspondem a alguns dos diferentes tipos.  
  
|Tipo de linha do tempo|Tipo de Relógio|Finalidade do relógio|  
|-------------------|----------------|-------------------|  
|Animação (herda <xref:System.Windows.Media.Animation.AnimationTimeline>de )|<xref:System.Windows.Media.Animation.AnimationClock>|Gera valores de saída para uma propriedade de dependência.|  
|<xref:System.Windows.Media.MediaTimeline>|<xref:System.Windows.Media.MediaClock>|Processa um arquivo de mídia.|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|<xref:System.Windows.Media.Animation.ClockGroup>|Grupos e controles <xref:System.Windows.Media.Animation.Clock> seus objetos infantis|  
|<xref:System.Windows.Media.Animation.Storyboard>|<xref:System.Windows.Media.Animation.ClockGroup>|Grupos e controles <xref:System.Windows.Media.Animation.Clock> seus objetos infantis|  
  
 Você pode <xref:System.Windows.Media.Animation.AnimationClock> aplicar quaisquer objetos que você <xref:System.Windows.Media.Animation.IAnimatable.ApplyAnimationClock%2A> criar para propriedades de dependência compatíveis usando o método.  
  
 Em cenários de desempenho intensivo, como animar um grande <xref:System.Windows.Media.Animation.Clock> número de objetos semelhantes, gerenciar seu próprio uso pode fornecer benefícios de desempenho.  
  
<a name="timemanager"></a>
## <a name="clocks-and-the-time-manager"></a>Relógios e o Gerenciador de tempo  
 Quando você anima [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]objetos, é o gerenciador <xref:System.Windows.Media.MediaPlayer.Clock%2A> de tempo que gerencia os objetos criados para suas linhas temporais. O gerenciador de tempo é <xref:System.Windows.Media.MediaPlayer.Clock%2A> a raiz de uma árvore de objetos e controla o fluxo do tempo naquela árvore.  Um Gerenciador de tempo é automaticamente criado para cada [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo e é invisível para o desenvolvedor do aplicativo. O Gerenciador de tempo "faz tiques" muitas vezes por segundo; o número real de tiques que ocorrem em cada segundo varia dependendo dos recursos disponíveis no sistema. Durante cada um desses carrapatos, o gerenciador <xref:System.Windows.Media.Animation.ClockState.Active> <xref:System.Windows.Media.Animation.Clock> de tempo calcula o estado de todos os objetos na árvore de cronometragem.  
  
 A ilustração a seguir mostra a <xref:System.Windows.Media.Animation.AnimationClock>relação entre o gerenciador de tempo e uma propriedade de dependência animada.  
  
 ![Componentes do sistema de medição de tempo](./media/graphicsmm-clocks-1clock1prop.png "graphicsmm_clocks_1clock1prop")  
Animar uma propriedade  
  
 Quando o gerenciador de tempo marca, <xref:System.Windows.Media.Animation.ClockState.Active> <xref:System.Windows.Media.Animation.Clock> ele atualiza o tempo de cada aplicativo. Se <xref:System.Windows.Media.Animation.Clock> for <xref:System.Windows.Media.Animation.AnimationClock>um , <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> ele usa <xref:System.Windows.Media.Animation.AnimationTimeline> o método do qual foi criado para calcular o seu valor de saída atual. O <xref:System.Windows.Media.Animation.AnimationClock> fornece <xref:System.Windows.Media.Animation.AnimationTimeline> o tempo local atual, um valor de entrada, que é tipicamente o valor base do imóvel, e um valor de destino padrão. Quando você recupera o valor de <xref:System.Windows.DependencyObject.GetValue%2A> uma animação por propriedade usando o método <xref:System.Windows.Media.Animation.AnimationClock>ou seu acessório CLR, você recebe a saída de seu .  
  
#### <a name="clock-groups"></a>Grupos de relógio  
 A seção anterior descreveu como <xref:System.Windows.Media.Animation.Clock> existem diferentes tipos de objetos para diferentes tipos de linhas temporais. A ilustração a seguir mostra a <xref:System.Windows.Media.Animation.ClockGroup>relação <xref:System.Windows.Media.Animation.AnimationClock>entre o gerenciador de tempo, a , um , e uma propriedade de dependência animada. A <xref:System.Windows.Media.Animation.ClockGroup> é criado para cronogramas que agrupam <xref:System.Windows.Media.Animation.Storyboard> outras linhas temporais, como a classe, que agrupa animações e outras linhas temporais.  
  
 ![Componentes do sistema de medição de tempo](./media/graphicsmm-clocks-2clock1clockgroup2prop.png "graphicsmm_clocks_2clock1clockgroup2prop")  
Um ClockGroup  
  
#### <a name="composition"></a>Composição  
 É possível associar vários relógios a uma única propriedade, caso em que cada relógio usa o valor de saída do relógio anterior como seu valor de base. A ilustração <xref:System.Windows.Media.Animation.AnimationClock> a seguir mostra três objetos aplicados à mesma propriedade. Relógio1 usa o valor base da propriedade animada como sua entrada e usa-o para gerar a saída. Relógio2 usa a saída do Relógio1 como sua entrada e usa-o para gerar a saída. Relógio3 usa a saída do Relógio2 como sua entrada e usa-o para gerar a saída. Quando vários relógios afetam a mesma propriedade simultaneamente, eles devem estar em uma cadeia de composição.  
  
 ![Componentes do sistema de medição de tempo](./media/graphicsmm-clocks-2clock1prop.png "graphicsmm_clocks_2clock1prop")  
Uma cadeia de composição  
  
 Observe que, embora seja criada uma relação <xref:System.Windows.Media.Animation.AnimationClock> entre a entrada e a saída dos objetos na cadeia de composição, seus comportamentos de cronometragem não são afetados; <xref:System.Windows.Media.Animation.Clock> objetos <xref:System.Windows.Media.Animation.AnimationClock> (incluindo objetos) têm uma <xref:System.Windows.Media.Animation.Clock> dependência hierárquica em seus objetos-pai.  
  
 Para aplicar vários relógios na mesma <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> <xref:System.Windows.Media.Animation.HandoffBehavior> propriedade, <xref:System.Windows.Media.Animation.Storyboard>use o <xref:System.Windows.Media.Animation.AnimationClock>ao aplicar uma animação ou .  
  
#### <a name="ticks-and-event-consolidation"></a>Tiques e consolidação de eventos  
 Além de calcular valores de saída, o Gerenciador de tempo faz outra tarefa toda vez que ele faz um tique: ele determina o estado de cada relógio e gera eventos conforme apropriado.  
  
 Enquanto tiques ocorrerem com frequência, é possível que muitas coisas ocorram entre tiques. Por exemplo, <xref:System.Windows.Media.Animation.Clock> um pode ser parado, iniciado e <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> parado novamente, nesse caso seu valor terá mudado três vezes. Em teoria, <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> o evento poderia ser levantado várias vezes em um único carrapato; no entanto, o mecanismo de cronometragem consolida eventos, para que o <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> evento possa ser levantado no máximo uma vez por carrapato. Isso é verdade para todos os eventos de cronometragem: no <xref:System.Windows.Media.Animation.Clock> máximo um evento de cada tipo é levantado para um determinado objeto.  
  
 Quando <xref:System.Windows.Media.Animation.Clock> um switches estados e retorna ao seu estado original <xref:System.Windows.Media.Animation.ClockState.Active> <xref:System.Windows.Media.Animation.ClockState.Stopped> entre carrapatos (como mudar de para e para trás para), <xref:System.Windows.Media.Animation.ClockState.Active>o evento associado ainda ocorre.  
  
 Para obter mais informações sobre eventos de temporização, consulte a [visão geral dos eventos de tempo](timing-events-overview.md).  
  
<a name="currentvaluesbasevaluesofproperties"></a>
## <a name="current-values-and-base-values-of-properties"></a>Valores atuais e valores base de propriedades  
 Uma propriedade animável pode ter dois valores: um valor base e um valor atual. Quando você define a propriedade usando <xref:System.Windows.DependencyObject.SetValue%2A> seu acessório CLR ou o método, você define seu valor base. Quando uma propriedade não é animada, seus valores atuais e base são os mesmos.  
  
 Quando você anima uma <xref:System.Windows.Media.Animation.AnimationClock> propriedade, define o valor *atual* da propriedade. Recuperar o valor da propriedade através de <xref:System.Windows.DependencyObject.GetValue%2A> seu acessório CLR <xref:System.Windows.Media.Animation.AnimationClock> ou <xref:System.Windows.Media.Animation.AnimationClock> <xref:System.Windows.Media.Animation.ClockState.Active> o <xref:System.Windows.Media.Animation.ClockState.Filling>método retorna a saída do quando é ou . Você pode recuperar o valor base <xref:System.Windows.Media.Animation.IAnimatable.GetAnimationBaseValue%2A> da propriedade usando o método.  
  
## <a name="see-also"></a>Confira também

- [Visão geral da animação](animation-overview.md)
- [Visão geral dos eventos de tempo](timing-events-overview.md)
- [Visão geral dos comportamentos de tempo](timing-behaviors-overview.md)
