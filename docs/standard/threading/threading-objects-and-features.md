---
title: Objetos e recursos de threading
ms.date: 08/16/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d56d962279120a03a6e4b89154ac1429ea5479e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43483652"
---
# <a name="threading-objects-and-features"></a>Objetos e recursos de threading

Juntamente com a classe <xref:System.Threading.Thread?displayProperty=nameWithType>, o .NET fornece várias classes que ajudam você a desenvolver aplicativos multithread. Os artigos a seguir fornecem uma visão geral dessas classes:

|Título|Descrição|  
|-----------|-----------------|  
|[O pool de threads gerenciados](the-managed-thread-pool.md)|Descreve a classe <xref:System.Threading.ThreadPool?displayProperty=nameWithType>, que fornece um pool de threads de trabalho que são gerenciados pelo .NET.|  
|[Temporizadores](timers.md)|Descreve os temporizadores que podem ser usados em um ambiente multi-threaded.|
|[Visão geral dos primitivos de sincronização](overview-of-synchronization-primitives.md)|Descreve classes que podem ser usadas para sincronizar o acesso a dados ou controlar a interação de thread.|
|[EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)|Descreve os identificadores de espera de eventos gerenciados, que são usados para sincronizar atividades de thread, sinalizando e aguardando sinais.|
|[Mutexes](mutexes.md)|Descreve como usar um <xref:System.Threading.Mutex?displayProperty=nameWithType> para sincronizar o acesso a um objeto ou compilar seus próprios mecanismos de sincronização.|
|[Operações interconectadas](interlocked-operations.md)|Descreve a classe <xref:System.Threading.Interlocked?displayProperty=nameWithType>, que fornece operações atômicas para variáveis que são compartilhadas por vários threads.|
|[Bloqueios de leitor-gravador](reader-writer-locks.md)|Descreve a classe <xref:System.Threading.ReaderWriterLockSlim?displayProperty=nameWithType>, que fornece a semântica de único gravador/vários leitores.|
|[Semaphore e SemaphoreSlim](semaphore-and-semaphoreslim.md)|Descreve a classe <xref:System.Threading.Semaphore?displayProperty=nameWithType> e explica como usá-la para controlar o acesso a recursos limitados.|
|[Barreira](barrier.md)|Descreve a classe <xref:System.Threading.Barrier?displayProperty=nameWithType> que implementa o padrão de barreira para coordenação de threads em operações em fases.|
|[SpinLock](spinlock.md)|Descreve a classe <xref:System.Threading.SpinLock?displayProperty=nameWithType>, que é uma alternativa leve para a classe <xref:System.Threading.Monitor?displayProperty=nameWithType> para certos cenários de nível baixo.|
|[SpinWait](spinwait.md)|Descreve a classe <xref:System.Threading.SpinWait?displayProperty=nameWithType>, que é um primitivo de sincronização de nível baixo que executa a rotação ocupada antes de iniciar uma espera baseada no kernel.|

## <a name="see-also"></a>Consulte também

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- [Usando threads e threading](using-threads-and-threading.md)
- [E/S de arquivo assíncrona](../io/asynchronous-file-i-o.md)
- [Programação paralela](../parallel-programming/index.md)
- [TPL (Biblioteca de Paralelismo de Tarefas)](../parallel-programming/task-parallel-library-tpl.md)
