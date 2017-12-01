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
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2a73e5c60a661c171e9e46e6307484cf5e0e6b80
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="threading-objects-and-features"></a>Threading de objetos e funcionalidades
O .NET Framework fornece um número de objetos que o ajudarão a criar e gerenciar aplicativos multithread. Threads gerenciados são representados pela <xref:System.Threading.Thread> classe. O <xref:System.Threading.ThreadPool> classe fornece facilitar a criação e gerenciamento de tarefas em segundo plano multi-threaded. O <xref:System.ComponentModel.BackgroundWorker> classe faz o mesmo para tarefas que interagem com a interface do usuário. O <xref:System.Threading.Timer> classe executa tarefas em segundo plano em intervalos regulares.  
  
 Além disso, há um número de classes que sincronizam atividades de threads, incluindo o <xref:System.Threading.Semaphore> e <xref:System.Threading.EventWaitHandle> classes introduzidos no .NET Framework versão 2.0. Os recursos dessas classes são comparados em [visão geral dos primitivos de sincronização](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [O pool de threads gerenciados](../../../docs/standard/threading/the-managed-thread-pool.md)  
 Explica o **ThreadPool** classe, que permite que você solicite um thread para executar uma tarefa sem precisar fazer qualquer gerenciamento de threads por conta própria.  
  
 [Temporizadores](../../../docs/standard/threading/timers.md)  
 Explica como usar um **Timer** para especificar um delegado a ser chamado em um horário especificado.  
  
 [Monitores](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
 Explica como usar o **Monitor** classe para sincronizar o acesso a um membro ou criar seu próprio thread de tipos de gerenciamento.  
  
 [Identificadores de espera](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 Descreve o <xref:System.Threading.WaitHandle> classe, a classe base abstrata para evento espera identificadores, mutexes e semáforos, que permite que a espera para vários eventos de sincronização.  
  
 [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 Descreve os identificadores de espera de eventos gerenciados, que são usados para sincronizar as atividades de thread de sinalização e esperando por sinais.  
  
 [Mutexes](../../../docs/standard/threading/mutexes.md)  
 Explica como usar um <xref:System.Threading.Mutex> para sincronizar o acesso a um objeto ou criar seus próprios mecanismos de sincronização.  
  
 [Operações interconectadas](../../../docs/standard/threading/interlocked-operations.md)  
 Explica como usar o <xref:System.Threading.Interlocked> classe para incrementar ou decrementar um valor e armazenar o valor em uma única operação atômica.  
  
 [Bloqueios de leitor-gravador](../../../docs/standard/threading/reader-writer-locks.md)  
 Define um bloqueio que implementa a semântica de único gravador/vários leitores.  
  
 [Semaphore e SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)  
 Descreve <xref:System.Threading.Semaphore> objetos e explica como usá-las para controlar o acesso aos recursos limitados.  
  
 [Visão geral dos primitivos de sincronização](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 Compara os recursos de classes do .NET Framework fornecidos para bloqueio e sincronizar threads gerenciados.  
  
 [Barreira](../../../docs/standard/threading/barrier.md)  
 Descreve <xref:System.Threading.Barrier> objetos que implementam o padrão de barreira para a coordenação de threads em operações em fases.  
  
 [SpinLock](../../../docs/standard/threading/spinlock.md)  
 Descreve <xref:System.Threading.SpinLock>, uma alternativa leve para a classe de Monitor para determinados cenários de nível inferior.  
  
 [SpinWait](../../../docs/standard/threading/spinwait.md)  
 Descreve <xref:System.Threading.SpinWait>, um primitivo de sincronização de nível baixo que executa giratório ocupado antes de iniciar uma espera de kernel.  
  
## <a name="reference"></a>Referência  
 <xref:System.Threading.Thread>  
 Fornece documentação de referência para o **Thread** classe que representa um segmento gerenciado, se ele veio com código não gerenciado ou foi criado em um aplicativo gerenciado.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Permite que as tarefas em segundo plano que interagem com a interface do usuário, se comunicar por meio de eventos gerados no thread da interface do usuário.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [E/S de arquivo assíncrona](../../../docs/standard/io/asynchronous-file-i-o.md)  
 Descreve como as portas de conclusão assíncrona de e/s usam o pool de threads para exigir o processamento somente quando uma operação de entrada/saída é concluída.  
  
 [TPL (Biblioteca de Paralelismo de Tarefas)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 Descreve a abordagem recomendada para a programação multi-threaded no [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] e posterior.
