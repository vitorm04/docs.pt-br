---
title: Threading de objetos e funcionalidades
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0cb36c004c46e22256928b3b2432da59fb3e6fa2
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="threading-objects-and-features"></a>Threading de objetos e funcionalidades
O .NET Framework fornece uma série de objetos que ajudam você a criar e gerenciar aplicativos multi-thread. Os threads gerenciados são representados pela classe <xref:System.Threading.Thread>. A classe <xref:System.Threading.ThreadPool> oferece fácil criação e gerenciamento de tarefas em segundo plano multi-thread. A classe <xref:System.ComponentModel.BackgroundWorker> faz o mesmo para tarefas que interagem com a interface do usuário. A classe <xref:System.Threading.Timer> executa tarefas em segundo plano em intervalos regulares.  
  
 Além disso, há uma série de classes que sincronizam atividades de threads, incluindo as classes <xref:System.Threading.Semaphore> e <xref:System.Threading.EventWaitHandle> apresentadas no .NET Framework versão 2.0. Os recursos dessas classes são comparados na [Visão geral dos primitivos de sincronização](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [O pool de threads gerenciados](../../../docs/standard/threading/the-managed-thread-pool.md)  
 Explica a classe **ThreadPool**, que permite que você solicite um thread para executar uma tarefa sem ter que fazer qualquer gerenciamento de thread por conta própria.  
  
 [Temporizadores](../../../docs/standard/threading/timers.md)  
 Explica como usar um **Temporizador** para especificar um delegado a ser chamado em um horário especificado.  
  
 [Monitores](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
 Explica como usar a classe **Monitor** para sincronizar o acesso a um membro ou criar seus próprios tipos de gerenciamento de threads.  
  
 [Identificadores de espera](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 Descreve a classe <xref:System.Threading.WaitHandle>, a classe base abstrata para identificadores de espera de eventos, exclusões mútuas e sinais, o que permite a espera de vários eventos de sincronização.  
  
 [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 Descreve os identificadores de espera de eventos gerenciados, que são usados para sincronizar atividades de thread, sinalizando e aguardando sinais.  
  
 [Mutexes](../../../docs/standard/threading/mutexes.md)  
 Explica como usar um <xref:System.Threading.Mutex> para sincronizar o acesso a um objeto ou criar seus próprios mecanismos de sincronização.  
  
 [Operações interconectadas](../../../docs/standard/threading/interlocked-operations.md)  
 Explica como usar a classe <xref:System.Threading.Interlocked> para incrementar ou diminuir um valor e armazenar o valor em uma única operação atômica.  
  
 [Bloqueios de leitor-gravador](../../../docs/standard/threading/reader-writer-locks.md)  
 Define um bloqueio que implementa a semântica de único gravador/vários leitores.  
  
 [Semaphore e SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)  
 Descreve objetos <xref:System.Threading.Semaphore> e explica como usá-los para controlar o acesso a recursos limitados.  
  
 [Visão geral dos primitivos de sincronização](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 Compara os recursos das classes .NET Framework fornecidas para bloquear e sincronizar threads gerenciados.  
  
 [Barreira](../../../docs/standard/threading/barrier.md)  
 Descreve objetos <xref:System.Threading.Barrier> que implementam o padrão de barreira para coordenação de threads em operações em fases.  
  
 [SpinLock](../../../docs/standard/threading/spinlock.md)  
 Descreve <xref:System.Threading.SpinLock>, uma alternativa leve para a classe Monitor para certos cenários de nível baixo.  
  
 [SpinWait](../../../docs/standard/threading/spinwait.md)  
 Descreve <xref:System.Threading.SpinWait>, um primitivo de sincronização de nível baixo que executa a rotação ocupada antes de iniciar uma espera baseada no kernel.  
  
## <a name="reference"></a>Referência  
 <xref:System.Threading.Thread>  
 Fornece documentação de referência para a classe **Thread**, que representa um thread gerenciado, seja ele proveniente de código não gerenciado ou criado em um aplicativo gerenciado.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Permite tarefas em segundo plano que interagem com a interface do usuário, comunicando-se através de eventos criados no thread da interface do usuário.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [E/S de arquivo assíncrona](../../../docs/standard/io/asynchronous-file-i-o.md)  
 Descreve como as portas de conclusão assíncronas de E/S usam o pool de threads para requerer o processamento somente quando uma operação de entrada/saída é concluída.  
  
 [TPL (Biblioteca de Paralelismo de Tarefas)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 Descreve a abordagem recomendada para a programação multi-thread no [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] e posterior.
