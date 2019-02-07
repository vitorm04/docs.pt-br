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
ms.openlocfilehash: 745cd1e17e2c06a513c6fdafe8f6b5f464b95d5f
ms.sourcegitcommit: dcc8feeff4718664087747529638ec9b47e65234
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/31/2019
ms.locfileid: "55479653"
---
# <a name="threading-objects-and-features"></a><span data-ttu-id="7567a-102">Objetos e recursos de threading</span><span class="sxs-lookup"><span data-stu-id="7567a-102">Threading objects and features</span></span>

<span data-ttu-id="7567a-103">Juntamente com a classe <xref:System.Threading.Thread?displayProperty=nameWithType>, o .NET fornece várias classes que ajudam você a desenvolver aplicativos multithread.</span><span class="sxs-lookup"><span data-stu-id="7567a-103">Along with the <xref:System.Threading.Thread?displayProperty=nameWithType> class, .NET provides a number of classes that help you develop multithreaded applications.</span></span> <span data-ttu-id="7567a-104">Os artigos a seguir fornecem uma visão geral dessas classes:</span><span class="sxs-lookup"><span data-stu-id="7567a-104">The following articles provide overview of those classes:</span></span>

|<span data-ttu-id="7567a-105">Título</span><span class="sxs-lookup"><span data-stu-id="7567a-105">Title</span></span>|<span data-ttu-id="7567a-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="7567a-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="7567a-107">O pool de threads gerenciados</span><span class="sxs-lookup"><span data-stu-id="7567a-107">The managed thread pool</span></span>](the-managed-thread-pool.md)|<span data-ttu-id="7567a-108">Descreve a classe <xref:System.Threading.ThreadPool?displayProperty=nameWithType>, que fornece um pool de threads de trabalho que são gerenciados pelo .NET.</span><span class="sxs-lookup"><span data-stu-id="7567a-108">Describes the <xref:System.Threading.ThreadPool?displayProperty=nameWithType> class, which provides a pool of worker threads that are managed by .NET.</span></span>|  
|[<span data-ttu-id="7567a-109">Temporizadores</span><span class="sxs-lookup"><span data-stu-id="7567a-109">Timers</span></span>](timers.md)|<span data-ttu-id="7567a-110">Descreve os temporizadores do .NET que podem ser usados em um ambiente multi-threaded.</span><span class="sxs-lookup"><span data-stu-id="7567a-110">Describes .NET timers that can be used in a multithreaded environment.</span></span>|
|[<span data-ttu-id="7567a-111">Visão geral dos primitivos de sincronização</span><span class="sxs-lookup"><span data-stu-id="7567a-111">Overview of synchronization primitives</span></span>](overview-of-synchronization-primitives.md)|<span data-ttu-id="7567a-112">Descreve os tipos que podem ser usados para sincronizar o acesso a um recurso compartilhado ou uma interação de thread de controle.</span><span class="sxs-lookup"><span data-stu-id="7567a-112">Describes types that can be used to synchronize access to a shared resource or control thread interaction.</span></span>|
|[<span data-ttu-id="7567a-113">EventWaitHandle, CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="7567a-113">EventWaitHandle, CountdownEvent</span></span>](eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)|<span data-ttu-id="7567a-114">Descreve os identificadores de espera de eventos gerenciados, que são usados para sincronizar atividades de thread, sinalizando e aguardando sinais.</span><span class="sxs-lookup"><span data-stu-id="7567a-114">Describes managed event wait handles, which are used to synchronize thread activities by signaling and waiting for signals.</span></span>|
|[<span data-ttu-id="7567a-115">Mutexes</span><span class="sxs-lookup"><span data-stu-id="7567a-115">Mutexes</span></span>](mutexes.md)|<span data-ttu-id="7567a-116">Descreve <xref:System.Threading.Mutex?displayProperty=nameWithType>, que concede acesso exclusivo a um recurso compartilhado.</span><span class="sxs-lookup"><span data-stu-id="7567a-116">Describes <xref:System.Threading.Mutex?displayProperty=nameWithType>, which grants exclusive access to a shared resource.</span></span>|
|[<span data-ttu-id="7567a-117">Semaphore e SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="7567a-117">Semaphore and SemaphoreSlim</span></span>](semaphore-and-semaphoreslim.md)|<span data-ttu-id="7567a-118">Descreve a classe <xref:System.Threading.Semaphore?displayProperty=nameWithType>, que limita o número de threads que podem acessar um recurso compartilhado ou um pool de recursos simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="7567a-118">Describes the <xref:System.Threading.Semaphore?displayProperty=nameWithType> class, which limits number of threads that can access a shared resource or a pool of resources concurrently.</span></span>|
|[<span data-ttu-id="7567a-119">Barreira</span><span class="sxs-lookup"><span data-stu-id="7567a-119">Barrier</span></span>](barrier.md)|<span data-ttu-id="7567a-120">Descreve a classe <xref:System.Threading.Barrier?displayProperty=nameWithType> que implementa o padrão de barreira para coordenação de threads em operações em fases.</span><span class="sxs-lookup"><span data-stu-id="7567a-120">Describes the <xref:System.Threading.Barrier?displayProperty=nameWithType> class that implements the barrier pattern for coordination of threads in phased operations.</span></span>|
|[<span data-ttu-id="7567a-121">SpinLock</span><span class="sxs-lookup"><span data-stu-id="7567a-121">SpinLock</span></span>](spinlock.md)|<span data-ttu-id="7567a-122">Descreve a estrutura <xref:System.Threading.SpinLock?displayProperty=nameWithType>, que é uma alternativa leve à classe <xref:System.Threading.Monitor?displayProperty=nameWithType> para certos cenários de bloqueio de nível baixo.</span><span class="sxs-lookup"><span data-stu-id="7567a-122">Describes the <xref:System.Threading.SpinLock?displayProperty=nameWithType> structure, which is a lightweight alternative to the <xref:System.Threading.Monitor?displayProperty=nameWithType> class for certain low-level locking scenarios.</span></span>|
|[<span data-ttu-id="7567a-123">SpinWait</span><span class="sxs-lookup"><span data-stu-id="7567a-123">SpinWait</span></span>](spinwait.md)|<span data-ttu-id="7567a-124">Descreve a estrutura de <xref:System.Threading.SpinWait?displayProperty=nameWithType>, que fornece suporte para espera baseada em rotação.</span><span class="sxs-lookup"><span data-stu-id="7567a-124">Describes the <xref:System.Threading.SpinWait?displayProperty=nameWithType> structure, which provides support for spin-based waiting.</span></span>|

## <a name="see-also"></a><span data-ttu-id="7567a-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7567a-125">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- [<span data-ttu-id="7567a-126">Usando threads e threading</span><span class="sxs-lookup"><span data-stu-id="7567a-126">Using threads and threading</span></span>](using-threads-and-threading.md)
- [<span data-ttu-id="7567a-127">E/S de arquivo assíncrona</span><span class="sxs-lookup"><span data-stu-id="7567a-127">Asynchronous File I/O</span></span>](../io/asynchronous-file-i-o.md)
- [<span data-ttu-id="7567a-128">Programação paralela</span><span class="sxs-lookup"><span data-stu-id="7567a-128">Parallel Programming</span></span>](../parallel-programming/index.md)
- [<span data-ttu-id="7567a-129">TPL (Biblioteca de Paralelismo de Tarefas)</span><span class="sxs-lookup"><span data-stu-id="7567a-129">Task Parallel Library (TPL)</span></span>](../parallel-programming/task-parallel-library-tpl.md)
