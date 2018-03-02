---
title: Estados de thread gerenciado
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], states
ms.assetid: 63890d5e-6025-4a7c-aaf0-d8bfd54b455f
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 956472ef0e3b0bab85a4eb0b5585f1a4d1e0a991
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="managed-thread-states"></a>Estados de thread gerenciado
A propriedade <xref:System.Threading.Thread.ThreadState%2A?displayProperty=nameWithType> fornece uma máscara de bits que indica o estado atual do thread. Um thread está sempre em pelo menos um dos estados possíveis na enumeração <xref:System.Threading.ThreadState> e pode estar em vários estados ao mesmo tempo.  
  
> [!IMPORTANT]
>  O estado do thread só é importante em alguns cenários de depuração. O código nunca deve usar o estado do thread para sincronizar as atividades de threads.  
  
 Quando você cria um thread gerenciado, ele está no estado <xref:System.Threading.ThreadState.Unstarted>. O thread permanece no estado <xref:System.Threading.ThreadState.Unstarted> até que o sistema operacional mova-o para o estado iniciado. Chamar <xref:System.Threading.Thread.Start%2A> informa o sistema operacional que o thread pode ser iniciado. Ele não altera o estado do thread.  
  
 Os threads não gerenciados que entram no ambiente gerenciado já estão no estado iniciado. Quando um thread está no estado iniciado, várias ações podem fazer com que ele altere os estados. A tabela a seguir lista as ações que levam a uma alteração de estado, juntamente com o novo estado correspondente.  
  
|Ação|Novo estado resultante|  
|------------|-------------------------|  
|O constructo da classe <xref:System.Threading.Thread> é chamado.|<xref:System.Threading.ThreadState.Unstarted>|  
|Outro thread chama <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.Unstarted>|  
|O thread responde a <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> e começa a ser executado.|<xref:System.Threading.ThreadState.Running>|  
|O thread chama <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|O thread chama <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> em outro objeto.|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|O thread chama <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> em outro thread.|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|Outro thread chama <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.SuspendRequested>|  
|O thread responde uma solicitação de <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.Suspended>|  
|Outro thread chama <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.Running>|  
|Outro thread chama <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.AbortRequested>|  
|O thread responde uma <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.Aborted> e, em seguida <xref:System.Threading.ThreadState.Stopped>|  
  
 Como o estado <xref:System.Threading.ThreadState.Running> tem um valor de 0, não é possível executar um teste de bits para descobrir esse estado. Em vez disso, o teste a seguir (em pseudocódigo) pode ser usado:  
  
```  
if ((state & (Unstarted | Stopped)) == 0)   // implies Running     
```  
  
 Geralmente, os threads estão em mais de um estado em um determinado momento. Por exemplo, se um thread estiver bloqueado em uma chamada <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> e outro thread chamar <xref:System.Threading.Thread.Abort%2A> nesse mesmo thread, o thread ficará nos estados <xref:System.Threading.ThreadState.WaitSleepJoin> e <xref:System.Threading.ThreadState.AbortRequested> ao mesmo tempo. Nesse caso, assim que o thread sair da chamada para <xref:System.Threading.Monitor.Wait%2A>, ou for interrompido, ele ficará com o estado <xref:System.Threading.ThreadAbortException>.  
  
 Depois que um thread sair do estado <xref:System.Threading.ThreadState.Unstarted> devido a uma chamada para <xref:System.Threading.Thread.Start%2A>, ele nunca poderá retornar para o estado <xref:System.Threading.ThreadState.Unstarted>. Um thread nunca pode deixar o estado <xref:System.Threading.ThreadState.Stopped>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading.ThreadAbortException>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadState>  
 [Threading](../../../docs/standard/threading/index.md)
