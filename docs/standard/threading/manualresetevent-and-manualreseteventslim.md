---
title: ManualResetEvent e ManualResetEventSlim
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], ManualResetEvent class
- ManualResetEvent class, about ManualResetEvent class
ms.assetid: 465fdcf9-ba24-4d8d-a43f-d983b7cb0cc6
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f663dd17b063f77e2f9ce6bd4bbd0f8859ba4116
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="manualresetevent-and-manualreseteventslim"></a>ManualResetEvent e ManualResetEventSlim
O <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> classe representa um evento de identificador de espera local deve ser redefinido manualmente depois que ela for sinalizada. Essa classe representa um caso especial de sua classe base, <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>. Consulte o [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) eventos de redefinição de documentação conceitual para o uso e recursos de manual.  
  
 Um <xref:System.Threading.ManualResetEvent> objeto permanece sinalizado até que seu <xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=nameWithType> método é chamado. Qualquer número de threads ou threads que esperar o evento depois que ela foi sinalizada, de espera pode ser liberado enquanto o estado do objeto é sinalizado. <xref:System.Threading.ManualResetEvent>corresponde a um Win32 `CreateEvent` chamar, especificando `true` para o `bManualReset` argumento.  
  
 No [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], você pode usar o <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> de classe para melhorar o desempenho quando os tempos de espera devem ser muito curto, e quando o evento não se cruza um limite de processo. <xref:System.Threading.ManualResetEventSlim>usa ocupado girando por um curto período enquanto aguarda o evento tornou-se sinalizado. Quando os tempos de espera são curtos, girando pode ser muito menos dispendioso que espera usando identificadores de espera. No entanto, se o evento não ficar sinalizado dentro de um determinado período de tempo, <xref:System.Threading.ManualResetEventSlim> recorre uma espera de identificador de evento regular.  
  
## <a name="see-also"></a>Consulte também  
 [Threading](../../../docs/standard/threading/index.md)  
 [Objetos e recursos de threading](../../../docs/standard/threading/threading-objects-and-features.md)  
 [Identificadores de espera](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 [AutoResetEvent](../../../docs/standard/threading/autoresetevent.md)  
 [SpinWait](../../../docs/standard/threading/spinwait.md)  
 [Semaphore e SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)
