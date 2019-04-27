---
title: Visão geral da animação e do sistema de tempo
ms.date: 03/30/2017
helpviewer_keywords:
- timing system [WPF]
- animation [WPF]
ms.assetid: 172cd5a8-a333-4c81-9456-fafccc19f382
ms.openlocfilehash: f64431e7804ba6e068a3d05f512c6ead089d7712
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62020319"
---
# <a name="animation-and-timing-system-overview"></a>Visão geral da animação e do sistema de tempo
Este tópico descreve como o sistema de temporização usa a animação <xref:System.Windows.Media.Animation.Timeline>, e <xref:System.Windows.Media.Animation.Clock> classes para animar propriedades.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Pré-requisitos  
 Para entender esse tópico, você deve ser capaz de usar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animações para animar propriedades, conforme descrito na [Visão geral da animação](animation-overview.md). Ele também ajuda a se familiarizar com as propriedades de dependência; para obter mais informações, consulte o [visão geral das propriedades de dependência](../advanced/dependency-properties-overview.md).  
  
<a name="timelinesandclocks"></a>   
## <a name="timelines-and-clocks"></a>Linhas de tempo e relógios  
 O [visão geral da animação](animation-overview.md) descrito como um <xref:System.Windows.Media.Animation.Timeline> representa um segmento de tempo e uma animação é um tipo de <xref:System.Windows.Media.Animation.Timeline> que produz valores de saída. Por si só, um <xref:System.Windows.Media.Animation.Timeline>, não faz nada além de apenas descrever um segmento de tempo. É a linha do tempo <xref:System.Windows.Media.Animation.Clock> objeto que faz o trabalho real. Da mesma forma, animação, na verdade, não anima propriedades: uma classe de animação descreve como valores de saída devem ser calculados, mas é o <xref:System.Windows.Media.Animation.Clock> que foi criado para a animação que conduz a saída da animação e a aplica às propriedades.  
  
 Um <xref:System.Windows.Media.Animation.Clock> é um tipo especial de objeto que mantém o estado de tempo de execução relacionado à temporização para a <xref:System.Windows.Media.Animation.Timeline>. Ele fornece três partes de informações que são essenciais para a animação e o sistema de temporização: <xref:System.Windows.Media.Animation.Clock.CurrentTime%2A>, <xref:System.Windows.Media.Animation.Clock.CurrentProgress%2A>, e <xref:System.Windows.Media.Animation.Clock.CurrentState%2A>. Um <xref:System.Windows.Media.Animation.Clock> determina sua hora atual, andamento e estado usando os comportamentos de temporização descritos pelo seu <xref:System.Windows.Media.Animation.Timeline>: <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>e assim por diante.  
  
 Na maioria dos casos, um <xref:System.Windows.Media.Animation.Clock> é criado automaticamente para sua linha do tempo. Quando você anima usando um <xref:System.Windows.Media.Animation.Storyboard> ou o <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> método, relógios são automaticamente criados para suas linhas do tempo e animações e aplicados às suas propriedades de destino. Você também pode criar uma <xref:System.Windows.Media.Animation.Clock> explicitamente, usando o <xref:System.Windows.Media.Animation.Timeline.CreateClock%2A> método do seu <xref:System.Windows.Media.Animation.Timeline>. O <xref:System.Windows.Media.MediaTimeline.CreateClock%2A?displayProperty=nameWithType> método cria um relógio do tipo apropriado para o <xref:System.Windows.Media.Animation.Timeline> no qual ele é chamado. Se o <xref:System.Windows.Media.Animation.Timeline> contém as linhas do tempo filho, ele cria <xref:System.Windows.Media.Animation.Clock> objetos para que eles também. Resultante <xref:System.Windows.Media.Animation.Clock> objetos são organizados em árvores que correspondam à estrutura do <xref:System.Windows.Media.Animation.Timeline> objetos de árvore da qual eles são criados.  
  
 Existem diferentes tipos de relógios para tipos diferentes de linhas de tempo. A tabela a seguir mostra a <xref:System.Windows.Media.Animation.Clock> tipos que correspondem a alguns dos diferentes <xref:System.Windows.Media.Animation.Timeline> tipos.  
  
|Tipo de linha do tempo|Tipo de Relógio|Finalidade do relógio|  
|-------------------|----------------|-------------------|  
|Animação (herda de <xref:System.Windows.Media.Animation.AnimationTimeline>)|<xref:System.Windows.Media.Animation.AnimationClock>|Gera valores de saída para uma propriedade de dependência.|  
|<xref:System.Windows.Media.MediaTimeline>|<xref:System.Windows.Media.MediaClock>|Processa um arquivo de mídia.|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|<xref:System.Windows.Media.Animation.ClockGroup>|Agrupa e controla seu filho <xref:System.Windows.Media.Animation.Clock> objetos|  
|<xref:System.Windows.Media.Animation.Storyboard>|<xref:System.Windows.Media.Animation.ClockGroup>|Agrupa e controla seu filho <xref:System.Windows.Media.Animation.Clock> objetos|  
  
 Você pode aplicar qualquer <xref:System.Windows.Media.Animation.AnimationClock> objetos que você criar a propriedades de dependência compatíveis usando o <xref:System.Windows.Media.Animation.IAnimatable.ApplyAnimationClock%2A> método.  
  
 Em cenários de alto desempenho, como animação de grande número de objetos semelhantes, gerenciar seu próprio <xref:System.Windows.Media.Animation.Clock> uso pode fornecer benefícios de desempenho.  
  
<a name="timemanager"></a>   
## <a name="clocks-and-the-time-manager"></a>Relógios e o Gerenciador de tempo  
 Quando você anima objetos em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], é o Gerenciador de tempo que gerencia o <xref:System.Windows.Media.MediaPlayer.Clock%2A> objetos criados para suas linhas do tempo. O Gerenciador de tempo é a raiz de uma árvore de <xref:System.Windows.Media.MediaPlayer.Clock%2A> objetos e controla o fluxo de tempo nesta árvore.  Um Gerenciador de tempo é automaticamente criado para cada [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo e é invisível para o desenvolvedor do aplicativo. O Gerenciador de tempo "faz tiques" muitas vezes por segundo; o número real de tiques que ocorrem em cada segundo varia dependendo dos recursos disponíveis no sistema. Durante cada um desses tiques, o Gerenciador de tempo calcula o estado de todos os <xref:System.Windows.Media.Animation.ClockState.Active> <xref:System.Windows.Media.Animation.Clock> objetos na árvore de temporização.  
  
 A ilustração a seguir mostra a relação entre o Gerenciador de tempo e <xref:System.Windows.Media.Animation.AnimationClock>e uma propriedade de dependência animada.  
  
 ![Componentes do sistema de tempo](./media/graphicsmm-clocks-1clock1prop.png "graphicsmm_clocks_1clock1prop")  
Animar uma propriedade  
  
 Quando o Gerenciador de tempo faz um tique, ele atualiza o tempo de cada <xref:System.Windows.Media.Animation.ClockState.Active> <xref:System.Windows.Media.Animation.Clock> no aplicativo. Se o <xref:System.Windows.Media.Animation.Clock> é um <xref:System.Windows.Media.Animation.AnimationClock>, ele usa o <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> método da <xref:System.Windows.Media.Animation.AnimationTimeline> do qual ele foi criado calcular seu valor de saída. O <xref:System.Windows.Media.Animation.AnimationClock> fornece o <xref:System.Windows.Media.Animation.AnimationTimeline> com a hora local atual, um valor de entrada, que normalmente é o valor base da propriedade e um valor de destino padrão. Quando você recuperar o valor de uma imagem por meio da propriedade a <xref:System.Windows.DependencyObject.GetValue%2A> método ou seu acessador CLR, você obtém a saída de seu <xref:System.Windows.Media.Animation.AnimationClock>.  
  
#### <a name="clock-groups"></a>Grupos de relógio  
 A seção anterior descreveu como existem diferentes tipos de <xref:System.Windows.Media.Animation.Clock> objetos para tipos diferentes de linhas do tempo. A ilustração a seguir mostra a relação entre o Gerenciador de tempo, uma <xref:System.Windows.Media.Animation.ClockGroup>, um <xref:System.Windows.Media.Animation.AnimationClock>e uma propriedade de dependência animada. Um <xref:System.Windows.Media.Animation.ClockGroup> é criado para linhas de tempo que agrupam outras linhas de tempo, como o <xref:System.Windows.Media.Animation.Storyboard> classe, que agrupa as animações e outras linhas de tempo.  
  
 ![Componentes do sistema de tempo](./media/graphicsmm-clocks-2clock1clockgroup2prop.png "graphicsmm_clocks_2clock1clockgroup2prop")  
Um ClockGroup  
  
#### <a name="composition"></a>Composição  
 É possível associar vários relógios a uma única propriedade, caso em que cada relógio usa o valor de saída do relógio anterior como seu valor de base. A ilustração a seguir mostra três <xref:System.Windows.Media.Animation.AnimationClock> objetos aplicados à mesma propriedade. Relógio1 usa o valor base da propriedade animada como sua entrada e usa-o para gerar a saída. Relógio2 usa a saída do Relógio1 como sua entrada e usa-o para gerar a saída. Relógio3 usa a saída do Relógio2 como sua entrada e usa-o para gerar a saída. Quando vários relógios afetam a mesma propriedade simultaneamente, eles devem estar em uma cadeia de composição.  
  
 ![Componentes do sistema de tempo](./media/graphicsmm-clocks-2clock1prop.png "graphicsmm_clocks_2clock1prop")  
Uma cadeia de composição  
  
 Observe que, embora uma relação é criada entre a entrada e saída do <xref:System.Windows.Media.Animation.AnimationClock> objetos na cadeia de composição, seus comportamentos de tempo não são afetados; <xref:System.Windows.Media.Animation.Clock> objetos (incluindo <xref:System.Windows.Media.Animation.AnimationClock> objetos) têm uma dependência hierárquica de seus pais <xref:System.Windows.Media.Animation.Clock> objetos.  
  
 Para aplicar vários relógios à mesma propriedade, use o <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> <xref:System.Windows.Media.Animation.HandoffBehavior> ao aplicar uma <xref:System.Windows.Media.Animation.Storyboard>, animação, ou <xref:System.Windows.Media.Animation.AnimationClock>.  
  
#### <a name="ticks-and-event-consolidation"></a>Tiques e consolidação de eventos  
 Além de calcular valores de saída, o Gerenciador de tempo faz outra tarefa toda vez que ele faz um tique: ele determina o estado de cada relógio e gera eventos conforme apropriado.  
  
 Enquanto tiques ocorrerem com frequência, é possível que muitas coisas ocorram entre tiques. Por exemplo, uma <xref:System.Windows.Media.Animation.Clock> pode ser interrompido, iniciado e interrompido novamente, caso em que seu <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> valor terá sido alterado três vezes. Em teoria, o <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> evento pode ser gerado várias vezes em um único tique; no entanto, o mecanismo de temporização consolida eventos, para que o <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> evento pode ser gerado no máximo uma vez por tique. Isso é verdadeiro para todos os eventos de temporização: no máximo um evento de cada tipo é gerado para um determinado <xref:System.Windows.Media.Animation.Clock> objeto.  
  
 Quando um <xref:System.Windows.Media.Animation.Clock> alterna estados e retorna ao estado original entre tiques (como alterar de <xref:System.Windows.Media.Animation.ClockState.Active> à <xref:System.Windows.Media.Animation.ClockState.Stopped> e de volta para <xref:System.Windows.Media.Animation.ClockState.Active>), o evento associado ainda ocorre.  
  
 Para obter mais informações sobre eventos de temporização, consulte a [visão geral dos eventos de tempo](timing-events-overview.md).  
  
<a name="currentvaluesbasevaluesofproperties"></a>   
## <a name="current-values-and-base-values-of-properties"></a>Valores atuais e valores base de propriedades  
 Uma propriedade animável pode ter dois valores: um valor base e um valor atual. Quando você define a propriedade usando seu acessador CLR ou o <xref:System.Windows.DependencyObject.SetValue%2A> método, você define seu valor base. Quando uma propriedade não é animada, seus valores atuais e base são os mesmos.  
  
 Ao animar uma propriedade, o <xref:System.Windows.Media.Animation.AnimationClock> define a propriedade *atual* valor. Recuperando o valor da propriedade por meio de seu acessador CLR ou o <xref:System.Windows.DependencyObject.GetValue%2A> método retorna a saída do <xref:System.Windows.Media.Animation.AnimationClock> quando o <xref:System.Windows.Media.Animation.AnimationClock> é <xref:System.Windows.Media.Animation.ClockState.Active> ou <xref:System.Windows.Media.Animation.ClockState.Filling>. Você pode recuperar o valor da propriedade base usando o <xref:System.Windows.Media.Animation.IAnimatable.GetAnimationBaseValue%2A> método.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral da animação](animation-overview.md)
- [Visão geral de eventos de tempo](timing-events-overview.md)
- [Visão geral dos comportamentos de tempo](timing-behaviors-overview.md)
