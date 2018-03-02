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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6c545f9ebc924c0a12ee2e76fdb6c725c25e2353
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="eventwaithandle-autoresetevent-countdownevent-manualresetevent"></a>EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent
Os identificadores de espera de evento permitem que os threads sincronizem atividades sinalizando uns aos outros e aguardando sinais uns dos outros. Esses eventos de sincronização baseiam-se em identificadores de espera do Win32 e podem ser divididos em dois tipos: aqueles que são redefinidos automaticamente quando sinalizados e aqueles que são redefinidos manualmente.  
  
 Os identificadores de espera de evento são úteis em muitos dos mesmos cenários de sincronização que a classe <xref:System.Threading.Monitor>. Os identificadores de espera de evento geralmente são mais fáceis de usar do que os métodos <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> e <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType>, e oferecem mais controle sobre a sinalização. Os identificadores de espera de evento nomeado também podem ser usados para sincronizar as atividades em domínios de aplicativos e processos, enquanto que os monitores são locais a um domínio de aplicativo.  
  
## <a name="in-this-section"></a>Nesta seção  
 [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md)  
 A classe <xref:System.Threading.EventWaitHandle> pode representar eventos de redefinição automáticos ou manuais, bem como eventos locais ou eventos de sistema nomeado.  
  
 [AutoResetEvent](../../../docs/standard/threading/autoresetevent.md)  
 A classe <xref:System.Threading.AutoResetEvent> deriva de <xref:System.Threading.EventWaitHandle> e representa um evento local que é redefinido automaticamente.  
  
 [ManualResetEvent e ManualResetEventSlim](../../../docs/standard/threading/manualresetevent-and-manualreseteventslim.md)  
 A classe <xref:System.Threading.ManualResetEvent> deriva de <xref:System.Threading.EventWaitHandle> e representa um evento local que deve ser redefinido manualmente. A classe <xref:System.Threading.ManualResetEventSlim> é uma versão leve e mais rápida, que pode ser usada para eventos dentro do mesmo processo.  
  
 [CountdownEvent](../../../docs/standard/threading/countdownevent.md)  
 A classe <xref:System.Threading.CountdownEvent> fornece uma maneira simplificada de implementar os padrões de paralelismo de bifurcação/junção no código que usa identificadores de espera.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Identificadores de espera](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 A classe <xref:System.Threading.WaitHandle> é a classe base para as classes <xref:System.Threading.EventWaitHandle>, <xref:System.Threading.Semaphore> e <xref:System.Threading.Mutex>. Contém métodos estáticos como <xref:System.Threading.WaitHandle.SignalAndWait%2A> e <xref:System.Threading.WaitHandle.WaitAll%2A> que são úteis quando se trabalha com todos os tipos de identificadores de espera.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading.EventWaitHandle>  
 <xref:System.Threading.WaitHandle>  
 <xref:System.Threading.AutoResetEvent>  
 <xref:System.Threading.ManualResetEvent>  
 [Objetos e recursos de threading](../../../docs/standard/threading/threading-objects-and-features.md)  
 [Noções básicas de threading gerenciado](../../../docs/standard/threading/managed-threading-basics.md)
