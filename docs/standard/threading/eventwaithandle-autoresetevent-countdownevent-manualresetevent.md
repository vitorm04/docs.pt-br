---
title: EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wait handles
- threading [.NET Framework], EventWaitHandle class
- event wait handles [.NET Framework]
ms.assetid: cd94fc34-ac15-427f-b723-a1240a4fab7d
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5c0bcb27ed9c8981665a50c129dfbd824c9612f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="eventwaithandle-autoresetevent-countdownevent-manualresetevent"></a>EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent
Identificadores de espera de eventos permitem que os threads para sincronizar as atividades de sinalização entre si e aguardando sinais uns dos outros. Esses eventos de sincronização são baseados em identificadores de espera do Win32 e podem ser divididos em dois tipos: aqueles que redefinir automaticamente quando sinalizado e aqueles que são redefinidos manualmente.  
  
 Identificadores de espera de eventos são úteis para muitos dos cenários de sincronização mesmo como o <xref:System.Threading.Monitor> classe. Identificadores de espera de eventos geralmente são mais fáceis de usar do que o <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> e <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> métodos e oferecem mais controle sobre a sinalização. Identificadores de espera de evento nomeado também podem ser usados para sincronizar as atividades em domínios de aplicativos e processos, enquanto que os monitores são locais para um domínio de aplicativo.  
  
## <a name="in-this-section"></a>Nesta seção  
 [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md)  
 O <xref:System.Threading.EventWaitHandle> classe pode representar qualquer automático ou manual redefinir os eventos e o local ou chamada de eventos do sistema.  
  
 [AutoResetEvent](../../../docs/standard/threading/autoresetevent.md)  
 O <xref:System.Threading.AutoResetEvent> classe derivada de <xref:System.Threading.EventWaitHandle> e representa um evento local redefine automaticamente.  
  
 [ManualResetEvent e ManualResetEventSlim](../../../docs/standard/threading/manualresetevent-and-manualreseteventslim.md)  
 O <xref:System.Threading.ManualResetEvent> classe derivada de <xref:System.Threading.EventWaitHandle> e representa um evento local deverá ser redefinido manualmente. O <xref:System.Threading.ManualResetEventSlim> classe é uma versão leve e mais rápida, que pode ser usada para eventos dentro do mesmo processo.  
  
 [CountdownEvent](../../../docs/standard/threading/countdownevent.md)  
 O <xref:System.Threading.CountdownEvent> classe fornece uma maneira simplificada para implementar os padrões de paralelismo de bifurcação/junção no código que usa identificadores de espera.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Identificadores de espera](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 O <xref:System.Threading.WaitHandle> classe é a classe base para o <xref:System.Threading.EventWaitHandle>, <xref:System.Threading.Semaphore>, e <xref:System.Threading.Mutex> classes. Contém métodos estáticos como <xref:System.Threading.WaitHandle.SignalAndWait%2A> e <xref:System.Threading.WaitHandle.WaitAll%2A> que são úteis ao trabalhar com todos os tipos de identificadores de espera.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading.EventWaitHandle>  
 <xref:System.Threading.WaitHandle>  
 <xref:System.Threading.AutoResetEvent>  
 <xref:System.Threading.ManualResetEvent>  
 [Objetos e recursos de threading](../../../docs/standard/threading/threading-objects-and-features.md)  
 [Noções básicas de threading gerenciado](../../../docs/standard/threading/managed-threading-basics.md)
