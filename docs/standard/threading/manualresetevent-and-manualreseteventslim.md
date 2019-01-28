---
title: ManualResetEvent e ManualResetEventSlim
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], ManualResetEvent class
- ManualResetEvent class, about ManualResetEvent class
ms.assetid: 465fdcf9-ba24-4d8d-a43f-d983b7cb0cc6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 864c39aa6673537d66d8402896bce5b4fa92e5ac
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54602437"
---
# <a name="manualresetevent-and-manualreseteventslim"></a>ManualResetEvent e ManualResetEventSlim
A classe <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> representa um evento de identificador de espera local que deve ser redefinido manualmente após ser sinalizado. Essa classe representa um caso especial de sua classe base, <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>. Veja a documentação conceitual de [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) para conhecer o uso e os recursos de eventos de redefinição manual.  
  
 Um objeto <xref:System.Threading.ManualResetEvent> permanece sinalizado até que seu método <xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=nameWithType> seja chamado. Qualquer número de threads em espera ou threads que esperam no evento depois de sinalizado, podem ser liberados enquanto o estado do objeto é sinalizado.
  
 No [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], você pode usar a classe <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> para melhorar o desempenho quando se espera que os tempos de espera sejam muito curtos, e quando o evento não cruza um limite de processo. O <xref:System.Threading.ManualResetEventSlim> usa a rotação ocupada por um curto período enquanto aguarda a sinalização do evento. Quando os tempos de espera são curtos, a rotação pode ser muito menos dispendiosa do que a espera usando os identificadores de espera. No entanto, se o evento não for sinalizado dentro de um determinado período de tempo, <xref:System.Threading.ManualResetEventSlim> recorre a uma espera de identificador de evento regular.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- [AutoResetEvent](autoresetevent.md)
- [SpinWait](spinwait.md)
- [Semaphore e SemaphoreSlim](semaphore-and-semaphoreslim.md)
- [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)
- [Objetos e recursos de threading](threading-objects-and-features.md)
- [Threading](index.md)
