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
helpviewer_keywords: threading [.NET Framework], states
ms.assetid: 63890d5e-6025-4a7c-aaf0-d8bfd54b455f
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 073fb19ef34ba32ccb5d5664413718a436563770
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="managed-thread-states"></a>Estados de thread gerenciado
A propriedade <xref:System.Threading.Thread.ThreadState%2A?displayProperty=nameWithType> fornece uma máscara de bits que indica o estado atual do thread. Um thread é sempre em pelo menos um dos possíveis estados de <xref:System.Threading.ThreadState> enumeração e pode estar em vários estados ao mesmo tempo.  
  
> [!IMPORTANT]
>  Estado do segmento é somente de interesse em alguns cenários de depuração. O código nunca deve usar o estado de thread para sincronizar as atividades de threads.  
  
 Quando você cria um thread gerenciado, ele está no <xref:System.Threading.ThreadState.Unstarted> estado. O thread permanece o <xref:System.Threading.ThreadState.Unstarted> estado até que ele é movido para o estado iniciado pelo sistema operacional. Chamando <xref:System.Threading.Thread.Start%2A> informa o sistema operacional que o thread pode ser iniciado; ele não altera o estado do thread.  
  
 Threads não gerenciados que entrar no ambiente gerenciado já estão no estado iniciado. Quando um thread estiver no estado iniciado, uma série de ações pode causar a mudança de estados. A tabela a seguir lista as ações que causam uma alteração de estado, juntamente com o novo estado correspondente.  
  
|Ação|Novo estado resultante|  
|------------|-------------------------|  
|O construtor para o <xref:System.Threading.Thread> classe é chamada.|<xref:System.Threading.ThreadState.Unstarted>|  
|Chamadas de outro thread <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.Unstarted>|  
|O thread responde a <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> e começa a ser executado.|<xref:System.Threading.ThreadState.Running>|  
|As chamadas do thread <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|As chamadas do thread <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> em outro objeto.|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|As chamadas do thread <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> em outro thread.|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|Chamadas de outro thread <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.SuspendRequested>|  
|O thread responde a um <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> solicitação.|<xref:System.Threading.ThreadState.Suspended>|  
|Chamadas de outro thread <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.Running>|  
|Chamadas de outro thread <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.AbortRequested>|  
|O thread responde a um <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.Aborted>, em seguida,<xref:System.Threading.ThreadState.Stopped>|  
  
 Porque o <xref:System.Threading.ThreadState.Running> estado tem um valor de 0, não é possível executar um teste de bits para descobrir esse estado. Em vez disso, o teste a seguir (em pseudocódigo) pode ser usado:  
  
```  
if ((state & (Unstarted | Stopped)) == 0)   // implies Running     
```  
  
 Threads são geralmente em mais de um estado em um determinado momento. Por exemplo, se um thread está bloqueado em uma <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> chamadas de thread de chamada e outro <xref:System.Threading.Thread.Abort%2A> nesse mesmo thread, o thread será no <xref:System.Threading.ThreadState.WaitSleepJoin> e o <xref:System.Threading.ThreadState.AbortRequested> estados ao mesmo tempo. Nesse caso, assim que o thread retorna da chamada para <xref:System.Threading.Monitor.Wait%2A> ou é interrompido, ele receberá o <xref:System.Threading.ThreadAbortException>.  
  
 Depois que um thread deixa o <xref:System.Threading.ThreadState.Unstarted> estado como resultado de uma chamada para <xref:System.Threading.Thread.Start%2A>, ele nunca pode retornar para o <xref:System.Threading.ThreadState.Unstarted> estado. Um thread nunca pode deixar o <xref:System.Threading.ThreadState.Stopped> estado.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading.ThreadAbortException>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadState>  
 [Threading](../../../docs/standard/threading/index.md)
