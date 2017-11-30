---
title: "Visão geral dos eventos de tempo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- timelines [WPF]
- timing events [WPF]
ms.assetid: 597e3280-0867-4359-a97b-5b2f4149e350
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8f50923d9e314d2f677e26416cef59fdf380213e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="timing-events-overview"></a>Visão geral dos eventos de tempo
Este tópico descreve como usar os cinco eventos de tempo disponíveis em <xref:System.Windows.Media.Animation.Timeline> e <xref:System.Windows.Media.Animation.Clock> objetos.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para entender este tópico, você deve entender como criar e usar animações. Para se familiarizar com animação, consulte o [visão geral de animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 Há várias maneiras de animar propriedades no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:  
  
-   **Usando objetos de storyboard** (marcação e código): você pode usar <xref:System.Windows.Media.Animation.Storyboard> objetos para organizar e distribuir animações para um ou mais objetos. Para obter um exemplo, consulte [animar uma propriedade usando um Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md).  
  
-   **Usando animações locais** (código somente): você pode aplicar <xref:System.Windows.Media.Animation.AnimationTimeline> objetos diretamente para as propriedades que eles animam. Para obter um exemplo, consulte [Animar uma propriedade sem usar um storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).  
  
-   **Usando relógios** (somente código): você pode gerenciar explicitamente a criação de relógios e distribuir os relógios de animação por conta própria.  Para obter um exemplo, consulte [animar uma propriedade usando um relógio de animação](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-an-animationclock.md).  
  
 Porque você pode usá-los na marcação e código, os exemplos nesta visão geral usam <xref:System.Windows.Media.Animation.Storyboard> objetos. No entanto, os conceitos descritos podem ser aplicados aos outros métodos de animação de propriedades.  
  
### <a name="what-is-a-clock"></a>O que é um relógio?  
 Uma linha do tempo, por si só, não faz nada além de descrever um segmento de tempo. É o cronograma <xref:System.Windows.Media.Animation.Clock> objeto que faz o trabalho real: ele mantém o estado de tempo de execução relacionados a tempo para a linha do tempo. Na maioria dos casos, como ao usar storyboards, um relógio é criado automaticamente para a linha do tempo. Você também pode criar um <xref:System.Windows.Media.Animation.Clock> explicitamente, usando o <xref:System.Windows.Media.Animation.Timeline.CreateClock%2A> método. Para obter mais informações sobre <xref:System.Windows.Media.Animation.Clock> objetos, consulte o [visão geral do sistema de controle de tempo e animação](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
## <a name="why-use-events"></a>Por que usar eventos?  
 Com exceção de uma (busca alinhada ao último tique), todas as operações de tempo interativas são assíncronas. Não há nenhuma maneira de saber exatamente quando elas serão executadas. Isso pode ser um problema quando você tiver outro código que depende de sua operação de tempo. Suponha que você queira parar uma linha do tempo que anima um retângulo. Após a linha do tempo parar, você altera a cor do retângulo.  
  
 [!code-csharp[events_procedural#NeedForEventsFragment](../../../../samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#needforeventsfragment)]
 [!code-vb[events_procedural#NeedForEventsFragment](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#needforeventsfragment)]  
  
 No exemplo anterior, a segunda linha de código pode ser executada antes que o storyboard pare. Isso acontece porque a interrupção é uma operação assíncrona. Dizer a uma linha do tempo ou relógio para parar cria uma "solicitação de parada" que não é processada até o próximo tique do mecanismo de tempo.  
  
 Para executar comandos após a conclusão de uma linha do tempo, use eventos de tempo. No exemplo a seguir, um manipulador de eventos é usado para alterar a cor de um retângulo após o fim da reprodução do storyboard.  
  
 [!code-csharp[events_procedural#RegisterForStoryboardCurrentStateInvalidatedEvent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#registerforstoryboardcurrentstateinvalidatedevent)]
 [!code-vb[events_procedural#RegisterForStoryboardCurrentStateInvalidatedEvent](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#registerforstoryboardcurrentstateinvalidatedevent)]  
[!code-csharp[events_procedural#StoryboardCurrentStateInvalidatedEvent2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#storyboardcurrentstateinvalidatedevent2)]
[!code-vb[events_procedural#StoryboardCurrentStateInvalidatedEvent2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#storyboardcurrentstateinvalidatedevent2)]  
  
 Para obter um exemplo mais completo, consulte [alterações de receber notificação quando um relógio de estado](../../../../docs/framework/wpf/graphics-multimedia/how-to-receive-notification-when-clock-state-changes.md).  
  
## <a name="public-events"></a>Eventos Públicos  
 O <xref:System.Windows.Media.Animation.Timeline> e <xref:System.Windows.Media.Animation.Clock> classes fornecem cinco eventos de tempo. A tabela a seguir lista esses eventos e as condições que os disparam.  
  
|Evento|Disparar a operação interativa|Outros gatilhos|  
|-----------|--------------------------------------|--------------------|  
|**Concluído**|Ir diretamente para o preenchimento|O relógio é concluído.|  
|**CurrentGlobalSpeedInvalidated**|Pausar, retomar, procurar, definir taxa de velocidade, ir diretamente para o preenchimento, parar|O relógio reverte, acelera, inicia ou interrompe.|  
|**CurrentStateInvalidated**|Começar, ir diretamente para o preenchimento, parar|O relógio inicia, para ou preenche.|  
|**CurrentTimeInvalidated**|Começar, procurar, ir diretamente para o preenchimento, parar|O relógio prossegue.|  
|**RemoveRequested**|Remover||  
  
## <a name="ticking-and-event-consolidation"></a>Consolidação de eventos e tiques  
 Quando você anima objetos no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], é o mecanismo de tempo que gerencia as suas animações. O mecanismo de tempo monitora o andamento do tempo e calcula o estado de cada animação. Ele realiza muitas etapas de avaliação desse tipo em um segundo. Essas etapas de avaliação são conhecidas como "tiques".  
  
 Enquanto tiques ocorrerem com frequência, é possível que muitas coisas ocorram entre tiques. Por exemplo, uma linha do tempo pode ser interrompida, iniciada e interrompida novamente e nesse caso seu estado atual terá sido alterado três vezes. Em teoria, o evento poderia ser gerado várias vezes em um único tique. No entanto, o mecanismo de tempo consolida eventos, de modo que cada evento pode ser gerado no máximo uma vez por tique.  
  
## <a name="registering-for-events"></a>Registrar-se em eventos  
 Há duas maneiras de se registrar em eventos de tempo: você pode se registrar na linha do tempo ou no relógio criado da linha do tempo. Registrar-se para um evento diretamente em um relógio é bastante simples, embora só possa ser feito no código. Você pode se registrar em eventos com uma linha do tempo de marcação ou código. A próxima seção descreve como se registrar em eventos de relógio com uma linha do tempo.  
  
<a name="registeringforclockeventswithatimeline"></a>   
## <a name="registering-for-clock-events-with-a-timeline"></a>Registrando-se em eventos de relógio com uma linha do tempo  
 Embora um cronograma <xref:System.Windows.Media.Animation.Timeline.Completed>, <xref:System.Windows.Media.Animation.Timeline.CurrentGlobalSpeedInvalidated>, <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated>, <xref:System.Windows.Media.Animation.Timeline.CurrentTimeInvalidated>, e <xref:System.Windows.Media.Animation.Timeline.RemoveRequested> eventos aparecem para ser associado com o cronograma, registrando esses eventos realmente associa um manipulador de eventos com o <xref:System.Windows.Media.Animation.Clock> criado para a linha do tempo.  
  
 Quando você registra o <xref:System.Windows.Media.Animation.Timeline.Completed> evento em uma linha do tempo, por exemplo, você está realmente dizendo o sistema para registrar o <xref:System.Windows.Media.Animation.Clock.Completed> eventos de cada relógio que é criado para a linha do tempo. No código, você deve registrar este evento antes de <xref:System.Windows.Media.Animation.Clock> é criado para essa linha do tempo; caso contrário, você não receberá a notificação. Isso acontece automaticamente no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; o analisador registra automaticamente o evento antes do <xref:System.Windows.Media.Animation.Clock> é criado.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da animação e do sistema de tempo](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)  
 [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Visão geral dos comportamentos de tempo](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md)
