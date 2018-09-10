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
ms.openlocfilehash: 69cd82ae2bd72db6a481188b3d7bf743e429f39c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864262"
---
# <a name="manualresetevent-and-manualreseteventslim"></a>ManualResetEvent e ManualResetEventSlim
A classe <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> representa um evento de identificador de espera local que deve ser redefinido manualmente após ser sinalizado. Essa classe representa um caso especial de sua classe base, <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>. Veja a documentação conceitual de [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) para conhecer o uso e os recursos de eventos de redefinição manual.  
  
 Um objeto <xref:System.Threading.ManualResetEvent> permanece sinalizado até que seu método <xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=nameWithType> seja chamado. Qualquer número de threads em espera ou threads que esperam no evento depois de sinalizado, podem ser liberados enquanto o estado do objeto é sinalizado. <xref:System.Threading.ManualResetEvent> corresponde a uma chamada Win32 `CreateEvent`, especificando `true` para o argumento `bManualReset`.  
  
 No [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], você pode usar a classe <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> para melhorar o desempenho quando se espera que os tempos de espera sejam muito curtos, e quando o evento não cruza um limite de processo. O <xref:System.Threading.ManualResetEventSlim> usa a rotação ocupada por um curto período enquanto aguarda a sinalização do evento. Quando os tempos de espera são curtos, a rotação pode ser muito menos dispendiosa do que a espera usando os identificadores de espera. No entanto, se o evento não for sinalizado dentro de um determinado período de tempo, <xref:System.Threading.ManualResetEventSlim> recorre a uma espera de identificador de evento regular.  
  
## <a name="see-also"></a>Consulte também

- [Threading](../../../docs/standard/threading/index.md)  
- [Objetos e recursos de threading](../../../docs/standard/threading/threading-objects-and-features.md)  
- [Identificadores de espera](https://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
- [AutoResetEvent](../../../docs/standard/threading/autoresetevent.md)  
- [SpinWait](../../../docs/standard/threading/spinwait.md)  
- [Semaphore e SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)
