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
ms.openlocfilehash: ee45441e9ad09c60d8b61ecce4ef08b0027ce29e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145404"
---
# <a name="timing-events-overview"></a>Visão geral dos eventos de tempo
Este tópico descreve como usar os cinco <xref:System.Windows.Media.Animation.Timeline> <xref:System.Windows.Media.Animation.Clock> eventos de cronometragem disponíveis em e objetos.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para entender este tópico, você deve entender como criar e usar animações. Para começar com animação, consulte a [visão geral da animação](animation-overview.md).  
  
 Existem várias maneiras [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]de animar propriedades em:  
  
- **Usando objetos de storyboard** (marcação <xref:System.Windows.Media.Animation.Storyboard> e código): Você pode usar objetos para organizar e distribuir animações para um ou mais objetos. Por exemplo, consulte [Animar uma propriedade usando um storyboard](how-to-animate-a-property-by-using-a-storyboard.md).  
  
- **Usando animações locais** (somente código): Você pode aplicar <xref:System.Windows.Media.Animation.AnimationTimeline> objetos diretamente nas propriedades que eles animam. Por exemplo, consulte [Animar uma propriedade sem usar um storyboard](how-to-animate-a-property-without-using-a-storyboard.md).  
  
- **Usando relógios** (somente código): você pode gerenciar explicitamente a criação de relógios e distribuir os relógios de animação por conta própria.  Por exemplo, consulte [Animar uma propriedade usando um AnimationClock](how-to-animate-a-property-by-using-an-animationclock.md).  
  
 Como você pode usá-los em marcação e código, <xref:System.Windows.Media.Animation.Storyboard> os exemplos nesta visão geral usam objetos. No entanto, os conceitos descritos podem ser aplicados aos outros métodos de animação de propriedades.  
  
### <a name="what-is-a-clock"></a>O que é um relógio?  
 Uma linha do tempo, por si só, não faz nada além de descrever um segmento de tempo. É o objeto da <xref:System.Windows.Media.Animation.Clock> linha do tempo que faz o trabalho real: ele mantém o estado de tempo de execução relacionado ao tempo para a linha do tempo. Na maioria dos casos, como ao usar storyboards, um relógio é criado automaticamente para a linha do tempo. Você também pode <xref:System.Windows.Media.Animation.Clock> criar um <xref:System.Windows.Media.Animation.Timeline.CreateClock%2A> explicitamente usando o método. Para obter <xref:System.Windows.Media.Animation.Clock> mais informações sobre objetos, consulte a visão geral do [sistema de animação e tempo](animation-and-timing-system-overview.md).  
  
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
  
 Para obter um exemplo mais completo, consulte [Receber notificação quando o estado de um relógio mudar](how-to-receive-notification-when-clock-state-changes.md).  
  
## <a name="public-events"></a>Eventos Públicos  
 As <xref:System.Windows.Media.Animation.Timeline> <xref:System.Windows.Media.Animation.Clock> aulas e as aulas oferecem cinco eventos de cronometragem. A tabela a seguir lista esses eventos e as condições que os disparam.  
  
|Evento|Disparar a operação interativa|Outros gatilhos|  
|-----------|--------------------------------------|--------------------|  
|**Concluído**|Ir diretamente para o preenchimento|O relógio é concluído.|  
|**CurrentGlobalSpeedInvalidated**|Pausar, retomar, procurar, definir taxa de velocidade, ir diretamente para o preenchimento, parar|O relógio reverte, acelera, inicia ou interrompe.|  
|**CurrentStateInvalidated**|Começar, ir diretamente para o preenchimento, parar|O relógio inicia, para ou preenche.|  
|**CurrentTimeInvalidated**|Começar, procurar, ir diretamente para o preenchimento, parar|O relógio prossegue.|  
|**RemoveRequested**|Remover||  
  
## <a name="ticking-and-event-consolidation"></a>Consolidação de eventos e tiques  
 Quando você anima [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]objetos, é o mecanismo de cronometragem que gerencia suas animações. O mecanismo de tempo monitora o andamento do tempo e calcula o estado de cada animação. Ele realiza muitas etapas de avaliação desse tipo em um segundo. Essas etapas de avaliação são conhecidas como "tiques".  
  
 Enquanto tiques ocorrerem com frequência, é possível que muitas coisas ocorram entre tiques. Por exemplo, uma linha do tempo pode ser interrompida, iniciada e interrompida novamente e nesse caso seu estado atual terá sido alterado três vezes. Em teoria, o evento poderia ser gerado várias vezes em um único tique. No entanto, o mecanismo de tempo consolida eventos, de modo que cada evento pode ser gerado no máximo uma vez por tique.  
  
## <a name="registering-for-events"></a>Registrar-se em eventos  
 Há duas maneiras de se registrar em eventos de tempo: você pode se registrar na linha do tempo ou no relógio criado da linha do tempo. Registrar-se para um evento diretamente em um relógio é bastante simples, embora só possa ser feito no código. Você pode se registrar em eventos com uma linha do tempo de marcação ou código. A próxima seção descreve como se registrar em eventos de relógio com uma linha do tempo.  
  
<a name="registeringforclockeventswithatimeline"></a>
## <a name="registering-for-clock-events-with-a-timeline"></a>Registrando-se em eventos de relógio com uma linha do tempo  
 Embora uma linha <xref:System.Windows.Media.Animation.Timeline.Completed> <xref:System.Windows.Media.Animation.Timeline.CurrentGlobalSpeedInvalidated>do <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> <xref:System.Windows.Media.Animation.Timeline.CurrentTimeInvalidated>tempo <xref:System.Windows.Media.Animation.Timeline.RemoveRequested> e eventos pareçam estar associados à linha do tempo, o <xref:System.Windows.Media.Animation.Clock> registro desses eventos realmente associa um manipulador de eventos com o criado para a linha do tempo.  
  
 Quando você se <xref:System.Windows.Media.Animation.Timeline.Completed> inscreve para o evento em um cronograma, por exemplo, você está realmente dizendo ao sistema para se registrar para o <xref:System.Windows.Media.Animation.Clock.Completed> evento de cada relógio que é criado para a linha do tempo. Em código, você deve se <xref:System.Windows.Media.Animation.Clock> registrar para este evento antes que o é criado para este cronograma; caso contrário, você não receberá notificação. Isso acontece automaticamente [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]em; o analisador se registra automaticamente para <xref:System.Windows.Media.Animation.Clock> o evento antes de ser criado.  
  
## <a name="see-also"></a>Confira também

- [Visão geral da animação e do sistema de tempo](animation-and-timing-system-overview.md)
- [Visão geral da animação](animation-overview.md)
- [Visão geral dos comportamentos de tempo](timing-behaviors-overview.md)
