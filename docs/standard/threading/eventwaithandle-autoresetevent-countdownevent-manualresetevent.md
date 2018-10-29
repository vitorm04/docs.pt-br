---
title: EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent
ms.date: 09/14/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- wait handles
- threading [.NET Framework], EventWaitHandle class
- event wait handles [.NET Framework]
ms.assetid: cd94fc34-ac15-427f-b723-a1240a4fab7d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be9c858d7c76fdcc1b3e02485eb0b459f4e7555c
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48583146"
---
# <a name="eventwaithandle-autoresetevent-countdownevent-manualresetevent"></a>EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent

Os identificadores de espera de evento permitem que os threads sincronizem atividades sinalizando uns aos outros e aguardando sinais uns dos outros. Esses eventos de sincronização baseiam-se em identificadores de espera do sistema operacional e podem ser divididos em dois tipos: aqueles que são redefinidos automaticamente quando sinalizados e aqueles que são redefinidos manualmente.  
  
Os identificadores de espera de evento são úteis em muitos dos mesmos cenários de sincronização que a classe <xref:System.Threading.Monitor>. Os identificadores de espera de evento geralmente são mais fáceis de usar do que os métodos <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> e <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType>, e oferecem mais controle sobre a sinalização. Os identificadores de espera de evento nomeado também podem ser usados para sincronizar as atividades em domínios de aplicativos e processos, enquanto que os monitores são locais a um domínio de aplicativo.  
  
## <a name="in-this-section"></a>Nesta seção

 [EventWaitHandle](eventwaithandle.md)  
 A classe <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> pode representar eventos de redefinição automáticos ou manuais, bem como eventos locais ou eventos de sistema nomeado.  
  
 [AutoResetEvent](autoresetevent.md)  
 A classe <xref:System.Threading.AutoResetEvent?displayProperty=nameWithType> deriva de <xref:System.Threading.EventWaitHandle> e representa um evento local que é redefinido automaticamente.  
  
 [ManualResetEvent e ManualResetEventSlim](manualresetevent-and-manualreseteventslim.md)  
 A classe <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> deriva de <xref:System.Threading.EventWaitHandle> e representa um evento local que deve ser redefinido manualmente. A classe <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> é uma versão leve e mais rápida, que pode ser usada para eventos dentro do mesmo processo.  
  
 [CountdownEvent](countdownevent.md)  
 A classe <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> fornece uma maneira simplificada de implementar os padrões de paralelismo de bifurcação/junção no código que usa identificadores de espera.  

## <a name="see-also"></a>Consulte também

- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- <xref:System.Threading.Barrier?displayProperty=nameWithType>
- [Objetos e recursos de threading](threading-objects-and-features.md)
- [Noções básicas de threading gerenciado](managed-threading-basics.md)
