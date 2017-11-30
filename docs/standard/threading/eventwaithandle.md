---
title: EventWaitHandle
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], EventWaitHandle class
- EventWaitHandle class
- event wait handles [.NET Framework]
- threading [.NET Framework], cross-process synchronization
ms.assetid: 11ee0b38-d663-4617-b793-35eb6c64e9fc
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1bd248133bd95ff05246eb36a8e250247fd7ed61
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="eventwaithandle"></a>EventWaitHandle
O <xref:System.Threading.EventWaitHandle> classe permite que os threads para se comunicar entre si por sinalização e aguardando sinais. Identificadores de espera de eventos (também conhecidas simplesmente como eventos) são identificadores de espera que podem ser sinalizados para liberar um ou mais threads de espera. Depois que ela foi sinalizada, um identificador de espera de eventos é redefinido manualmente ou automaticamente. O <xref:System.Threading.EventWaitHandle> classe pode representar qualquer um evento local identificador de espera (evento local) ou um evento do sistema nomeado aguardar o identificador (chamado de evento ou evento do sistema, visível para todos os processos).  
  
> [!NOTE]
>  Identificadores de espera de eventos não são eventos no sentido geralmente significa palavra no .NET Framework. Não há nenhum delegados ou manipuladores de eventos envolvidos. "Evento" é usado para descrevê-los, pois eles têm sido conhecidos tradicionalmente como eventos do sistema operacional e o ato de sinalização do identificador de espera indica para threads de espera que um evento ocorreu.  
  
 Ambos os identificadores de espera de eventos local e nomeado usam objetos de sincronização do sistema, que são protegidos pelo <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle> wrappers para garantir que os recursos são liberados. Você pode usar o <xref:System.Threading.WaitHandle.Dispose%2A> método para liberar os recursos imediatamente quando você terminar de usar o objeto.  
  
## <a name="event-wait-handles-that-reset-automatically"></a>Identificadores de espera de eventos que redefinirem automaticamente  
 Criar um evento de redefinição automática especificando <xref:System.Threading.EventResetMode.AutoReset?displayProperty=nameWithType> quando você cria o <xref:System.Threading.EventWaitHandle> objeto. Como o nome sugere, esse evento de sincronização redefine automaticamente quando sinalizado, após o lançamento de um único thread de espera. Sinalizar o evento chamando seu <xref:System.Threading.EventWaitHandle.Set%2A> método.  
  
 Eventos de redefinição automática geralmente são usados para fornecer acesso exclusivo a um recurso para um único thread por vez. Um thread de solicita o recurso ao chamar o <xref:System.Threading.WaitHandle.WaitOne%2A> método. Se nenhum outro thread está mantendo o identificador de espera, o método retorna `true` e o thread de chamada tem o controle do recurso.  
  
> [!IMPORTANT]
>  Assim como acontece com todos os mecanismos de sincronização, você deve garantir que todos os caminhos de código aguardar o identificador de espera apropriado antes de acessar um recurso protegido. Sincronização de threads é cooperativa.  
  
 Se um evento de redefinição automática é sinalizado quando não há threads estão esperando, ele permanecerá sinalizado até que um thread tente esperar. O evento libera o thread e redefine imediatamente, bloqueando threads subsequentes.  
  
## <a name="event-wait-handles-that-reset-manually"></a>Identificadores de espera de eventos que redefinir manualmente  
 Criar um evento de redefinição manual especificando <xref:System.Threading.EventResetMode.ManualReset?displayProperty=nameWithType> quando você cria o <xref:System.Threading.EventWaitHandle> objeto. Como o nome sugere, esse evento de sincronização deve ser redefinido manualmente depois que ele tiver sido sinalizado. Até que ela seja redefinida, chamando seu <xref:System.Threading.EventWaitHandle.Reset%2A> método, os threads que aguardar o identificador de evento continuar imediatamente sem bloqueio.  
  
 Redefinição de um manual atos de evento como a porta de um corral. Quando o evento não será sinalizado, bloqueiam threads que esperam nele, como cavalos de um corral. Quando o evento é sinalizado, chamando seu <xref:System.Threading.EventWaitHandle.Set%2A> método, todos os threads de espera estão livres para continuar. O evento permanece sinalizado até que seu <xref:System.Threading.EventWaitHandle.Reset%2A> método é chamado. Isso torna o evento de redefinição manual de maneira ideal de threads que seja necessário aguardar até que um thread conclui uma tarefa em espera.  
  
 Como cavalos de deixar um corral leva tempo para os lançamento threads sejam agendadas pelo sistema operacional e continuar a execução. Se o <xref:System.Threading.EventWaitHandle.Reset%2A> método é chamado antes de todos os threads têm voltou a operar, os segmentos restantes bloqueiam novamente. Retomar os threads e o bloco de threads depende aleatórios fatores como a carga no sistema, o número de threads aguardando para o Agendador e assim por diante. Isso não é um problema se o thread que sinaliza o evento terminar depois de sinalizar, que é o padrão de uso mais comum. Se você quiser thread sinalizado o evento para iniciar uma nova tarefa depois que todos os aguardando threads retomou o funcionamento, você deve bloqueá-lo até que todos os threads de espera tem retomado. Caso contrário, você tem uma condição de corrida, e o comportamento do seu código é imprevisível.  
  
## <a name="features-common-to-automatic-and-manual-events"></a>Recursos comuns a eventos automáticos e Manual  
 Normalmente, um ou mais threads bloqueiam um <xref:System.Threading.EventWaitHandle> até que um thread desbloqueado chama o <xref:System.Threading.EventWaitHandle.Set%2A> método, o que libera um dos threads de espera (no caso de eventos de reinicialização automática) ou todos eles (no caso de manual redefinir eventos). Um thread pode sinalizar um <xref:System.Threading.EventWaitHandle> e, em seguida, bloquear, como uma operação atômica, chamando estático <xref:System.Threading.WaitHandle.SignalAndWait%2A?displayProperty=nameWithType> método.  
  
 <xref:System.Threading.EventWaitHandle>objetos podem ser usados com estático <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType> e <xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType> métodos. Porque o <xref:System.Threading.EventWaitHandle> e <xref:System.Threading.Mutex> derivam de classes <xref:System.Threading.WaitHandle>, você pode usar ambas as classes com esses métodos.  
  
### <a name="named-events"></a>Eventos nomeados  
 O sistema operacional Windows permite que os identificadores de espera do evento ter nomes. Um evento nomeado é todo o sistema. Ou seja, quando o evento nomeado é criado, é visível para todos os threads em todos os processos. Assim, os eventos nomeados podem ser usados para sincronizar as atividades de processos, bem como os threads.  
  
 Você pode criar um <xref:System.Threading.EventWaitHandle> objeto que representa um evento do sistema nomeado usando um dos construtores que especifica um nome de evento.  
  
> [!NOTE]
>  Como os eventos nomeados são todo o sistema, é possível ter vários <xref:System.Threading.EventWaitHandle> denominado de objetos que representam o mesmo evento. Cada vez que você chamar um construtor, ou o <xref:System.Threading.EventWaitHandle.OpenExisting%2A> método, um novo <xref:System.Threading.EventWaitHandle> objeto é criado. Especificando o mesmo nome repetidamente cria vários objetos que representam o mesmo evento nomeado.  
  
 Tenha cuidado usando eventos nomeados. Porque eles estão no sistema, outro processo que usa o mesmo nome pode bloquear seu threads inesperadamente. Código mal-intencionado em execução no mesmo computador pode usar isso como base de um ataque de negação de serviço.  
  
 Usar controle de acesso de segurança para proteger um <xref:System.Threading.EventWaitHandle> objeto que representa um evento nomeado, preferencialmente com um construtor que especifica um <xref:System.Security.AccessControl.EventWaitHandleSecurity> objeto. Você também pode aplicar a segurança de controle de acesso usando o <xref:System.Threading.EventWaitHandle.SetAccessControl%2A> método, mas isso deixa uma janela de vulnerabilidade entre a hora em que o identificador de espera de eventos é criado e a hora em que ele está protegido. Protegendo os eventos com controle de acesso de segurança ajuda a impedir ataques maliciosos, mas não resolver o problema de conflitos de nome não intencionais.  
  
> [!NOTE]
>  Ao contrário de <xref:System.Threading.EventWaitHandle> classe, as classes derivadas <xref:System.Threading.AutoResetEvent> e <xref:System.Threading.ManualResetEvent> pode representar local somente identificadores de espera. Eles não podem representar eventos do sistema nomeado.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading.EventWaitHandle>  
 <xref:System.Threading.WaitHandle>  
 <xref:System.Threading.AutoResetEvent>  
 <xref:System.Threading.ManualResetEvent>  
 [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)
