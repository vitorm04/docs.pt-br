---
title: Visão geral dos eventos de tempo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- timelines [WPF]
- timing events [WPF]
ms.assetid: 597e3280-0867-4359-a97b-5b2f4149e350
ms.openlocfilehash: 91e335f4d5adaa5279fb16805604f2e2848eeb8b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59167161"
---
# <a name="timing-events-overview"></a>Visão geral dos eventos de tempo
Este tópico descreve como usar os cinco eventos de tempo disponíveis no <xref:System.Windows.Media.Animation.Timeline> e <xref:System.Windows.Media.Animation.Clock> objetos.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para entender este tópico, você deve entender como criar e usar animações. Para se familiarizar com a animação, consulte o [visão geral da animação](animation-overview.md).  
  
 Há várias maneiras de animar propriedades no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:  
  
-   **Usando objetos de storyboard** (marcação e código): Você pode usar <xref:System.Windows.Media.Animation.Storyboard> objetos para organizar e distribuir animações para um ou mais objetos. Por exemplo, consulte [animar uma propriedade usando um Storyboard](how-to-animate-a-property-by-using-a-storyboard.md).  
  
-   **Usando animações locais** (somente código): Você pode aplicar <xref:System.Windows.Media.Animation.AnimationTimeline> objetos diretamente para as propriedades que eles animam. Para obter um exemplo, consulte [Animar uma propriedade sem usar um storyboard](how-to-animate-a-property-without-using-a-storyboard.md).  
  
-   **Usando relógios** (somente código): Explicitamente, você pode gerenciar a criação de relógios e distribuir os relógios de animação por conta própria.  Por exemplo, consulte [animar uma propriedade usando um AnimationClock](how-to-animate-a-property-by-using-an-animationclock.md).  
  
 Porque você pode usá-los na marcação e código, os exemplos nesta visão geral usam <xref:System.Windows.Media.Animation.Storyboard> objetos. No entanto, os conceitos descritos podem ser aplicados aos outros métodos de animação de propriedades.  
  
### <a name="what-is-a-clock"></a>O que é um relógio?  
 Uma linha do tempo, por si só, não faz nada além de descrever um segmento de tempo. É a linha do tempo <xref:System.Windows.Media.Animation.Clock> objeto que faz o trabalho real: ele mantém o estado de tempo de execução relacionado à temporização para a linha do tempo. Na maioria dos casos, como ao usar storyboards, um relógio é criado automaticamente para a linha do tempo. Você também pode criar uma <xref:System.Windows.Media.Animation.Clock> explicitamente, usando o <xref:System.Windows.Media.Animation.Timeline.CreateClock%2A> método. Para obter mais informações sobre <xref:System.Windows.Media.Animation.Clock> objetos, consulte a [animação e visão geral do sistema de temporização](animation-and-timing-system-overview.md).  
  
## <a name="why-use-events"></a>Por que usar eventos?  
 Com exceção de uma (busca alinhada ao último tique), todas as operações de tempo interativas são assíncronas. Não há nenhuma maneira de saber exatamente quando elas serão executadas. Isso pode ser um problema quando você tiver outro código que depende de sua operação de tempo. Suponha que você queira parar uma linha do tempo que anima um retângulo. Após a linha do tempo parar, você altera a cor do retângulo.  
  
 [!code-csharp[events_procedural#NeedForEventsFragment](~/samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#needforeventsfragment)]
 [!code-vb[events_procedural#NeedForEventsFragment](~/samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#needforeventsfragment)]  
  
 No exemplo anterior, a segunda linha de código pode ser executada antes que o storyboard pare. Isso acontece porque a interrupção é uma operação assíncrona. Dizer a uma linha do tempo ou relógio para parar cria uma "solicitação de parada" que não é processada até o próximo tique do mecanismo de tempo.  
  
 Para executar comandos após a conclusão de uma linha do tempo, use eventos de tempo. No exemplo a seguir, um manipulador de eventos é usado para alterar a cor de um retângulo após o fim da reprodução do storyboard.  
  
 [!code-csharp[events_procedural#RegisterForStoryboardCurrentStateInvalidatedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#registerforstoryboardcurrentstateinvalidatedevent)]
 [!code-vb[events_procedural#RegisterForStoryboardCurrentStateInvalidatedEvent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#registerforstoryboardcurrentstateinvalidatedevent)]  
[!code-csharp[events_procedural#StoryboardCurrentStateInvalidatedEvent2](~/samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#storyboardcurrentstateinvalidatedevent2)]
[!code-vb[events_procedural#StoryboardCurrentStateInvalidatedEvent2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#storyboardcurrentstateinvalidatedevent2)]  
  
 Para obter um exemplo mais completo, consulte [alterações de estado de receber notificação quando um relógio](how-to-receive-notification-when-clock-state-changes.md).  
  
## <a name="public-events"></a>Eventos Públicos  
 O <xref:System.Windows.Media.Animation.Timeline> e <xref:System.Windows.Media.Animation.Clock> classes fornecem cinco eventos de tempo. A tabela a seguir lista esses eventos e as condições que os disparam.  
  
|evento|Disparar a operação interativa|Outros gatilhos|  
|-----------|--------------------------------------|--------------------|  
|**Concluído**|Ir diretamente para o preenchimento|O relógio é concluído.|  
|**CurrentGlobalSpeedInvalidated**|Pausar, retomar, procurar, definir taxa de velocidade, ir diretamente para o preenchimento, parar|O relógio reverte, acelera, inicia ou interrompe.|  
|**CurrentStateInvalidated**|Começar, ir diretamente para o preenchimento, parar|O relógio inicia, para ou preenche.|  
|**CurrentTimeInvalidated**|Começar, procurar, ir diretamente para o preenchimento, parar|O relógio prossegue.|  
|**RemoveRequested**|Remover||  
  
## <a name="ticking-and-event-consolidation"></a>Consolidação de eventos e tiques  
 Quando você anima objetos em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], é o mecanismo de tempo que gerencia suas animações. O mecanismo de tempo monitora o andamento do tempo e calcula o estado de cada animação. Ele realiza muitas etapas de avaliação desse tipo em um segundo. Essas etapas de avaliação são conhecidas como "tiques".  
  
 Enquanto tiques ocorrerem com frequência, é possível que muitas coisas ocorram entre tiques. Por exemplo, uma linha do tempo pode ser interrompida, iniciada e interrompida novamente e nesse caso seu estado atual terá sido alterado três vezes. Em teoria, o evento poderia ser gerado várias vezes em um único tique. No entanto, o mecanismo de tempo consolida eventos, de modo que cada evento pode ser gerado no máximo uma vez por tique.  
  
## <a name="registering-for-events"></a>Registrar-se em eventos  
 Há duas maneiras de se registrar em eventos de tempo: você pode se registrar na linha do tempo ou no relógio criado da linha do tempo. Registrar-se para um evento diretamente em um relógio é bastante simples, embora só possa ser feito no código. Você pode se registrar em eventos com uma linha do tempo de marcação ou código. A próxima seção descreve como se registrar em eventos de relógio com uma linha do tempo.  
  
<a name="registeringforclockeventswithatimeline"></a>   
## <a name="registering-for-clock-events-with-a-timeline"></a>Registrando-se em eventos de relógio com uma linha do tempo  
 Embora um cronograma <xref:System.Windows.Media.Animation.Timeline.Completed>, <xref:System.Windows.Media.Animation.Timeline.CurrentGlobalSpeedInvalidated>, <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated>, <xref:System.Windows.Media.Animation.Timeline.CurrentTimeInvalidated>, e <xref:System.Windows.Media.Animation.Timeline.RemoveRequested> eventos parecem estar associado com o cronograma, registrando esses eventos realmente associa um manipulador de eventos com o <xref:System.Windows.Media.Animation.Clock> criado para a linha do tempo.  
  
 Quando você se registrar para o <xref:System.Windows.Media.Animation.Timeline.Completed> evento em uma linha do tempo, por exemplo, você está realmente dizendo ao sistema para se registrar para o <xref:System.Windows.Media.Animation.Clock.Completed> eventos de cada relógio que é criado para a linha do tempo. No código, você deve registrar este evento antes do <xref:System.Windows.Media.Animation.Clock> é criado para essa linha do tempo; caso contrário, você não receberá a notificação. Isso acontece automaticamente no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; o analisador registra automaticamente para o evento antes do <xref:System.Windows.Media.Animation.Clock> é criado.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral da animação e do sistema de tempo](animation-and-timing-system-overview.md)
- [Visão geral da animação](animation-overview.md)
- [Visão geral dos comportamentos de tempo](timing-behaviors-overview.md)
