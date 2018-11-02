---
title: Objetos e recursos de threading
ms.date: 10/01/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ba47ece16c74555b58780733e14de9833718c33
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48873301"
---
# <a name="threading-objects-and-features"></a>Objetos e recursos de threading

Juntamente com a classe <xref:System.Threading.Thread?displayProperty=nameWithType>, o .NET fornece várias classes que ajudam você a desenvolver aplicativos multithread. Os artigos a seguir fornecem uma visão geral dessas classes:

|Título|Descrição|  
|-----------|-----------------|  
|[O pool de threads gerenciados](the-managed-thread-pool.md)|Descreve a classe <xref:System.Threading.ThreadPool?displayProperty=nameWithType>, que fornece um pool de threads de trabalho que são gerenciados pelo .NET.|  
|[Temporizadores](timers.md)|Descreve os temporizadores do .NET que podem ser usados em um ambiente multi-threaded.|
|[Visão geral dos primitivos de sincronização](overview-of-synchronization-primitives.md)|Descreve os tipos que podem ser usados para sincronizar o acesso a um recurso compartilhado ou uma interação de thread de controle.|
|[EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)|Descreve os identificadores de espera de eventos gerenciados, que são usados para sincronizar atividades de thread, sinalizando e aguardando sinais.|
|[Mutexes](mutexes.md)|Descreve <xref:System.Threading.Mutex?displayProperty=nameWithType>, que concede acesso exclusivo a um recurso compartilhado.|
|[Operações interconectadas](interlocked-operations.md)|Descreve a classe <xref:System.Threading.Interlocked?displayProperty=nameWithType>, que fornece operações atômicas para variáveis que são compartilhadas por vários threads.|
|[Bloqueios de leitor-gravador](reader-writer-locks.md)|Descreve a classe <xref:System.Threading.ReaderWriterLockSlim?displayProperty=nameWithType>, que fornece acesso de gravador único/leitores múltiplos a um recurso compartilhado.|
|[Semaphore e SemaphoreSlim](semaphore-and-semaphoreslim.md)|Descreve a classe <xref:System.Threading.Semaphore?displayProperty=nameWithType>, que limita o número de threads que podem acessar um recurso compartilhado ou um pool de recursos simultaneamente.|
|[Barreira](barrier.md)|Descreve a classe <xref:System.Threading.Barrier?displayProperty=nameWithType> que implementa o padrão de barreira para coordenação de threads em operações em fases.|
|[SpinLock](spinlock.md)|Descreve a estrutura <xref:System.Threading.SpinLock?displayProperty=nameWithType>, que é uma alternativa leve à classe <xref:System.Threading.Monitor?displayProperty=nameWithType> para certos cenários de bloqueio de nível baixo.|
|[SpinWait](spinwait.md)|Descreve a estrutura de <xref:System.Threading.SpinWait?displayProperty=nameWithType>, que fornece suporte para espera baseada em rotação.|

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
