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
ms.openlocfilehash: f25609bc3c4dd829c66a1a4514b7f1121f9c0909
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/06/2019
ms.locfileid: "55759022"
---
# <a name="threading-objects-and-features"></a><span data-ttu-id="94930-102">Objetos e recursos de threading</span><span class="sxs-lookup"><span data-stu-id="94930-102">Threading objects and features</span></span>

<span data-ttu-id="94930-103">Juntamente com a classe <xref:System.Threading.Thread?displayProperty=nameWithType>, o .NET fornece várias classes que ajudam você a desenvolver aplicativos multithread.</span><span class="sxs-lookup"><span data-stu-id="94930-103">Along with the <xref:System.Threading.Thread?displayProperty=nameWithType> class, .NET provides a number of classes that help you develop multithreaded applications.</span></span> <span data-ttu-id="94930-104">Os artigos a seguir fornecem uma visão geral dessas classes:</span><span class="sxs-lookup"><span data-stu-id="94930-104">The following articles provide overview of those classes:</span></span>

|<span data-ttu-id="94930-105">Título</span><span class="sxs-lookup"><span data-stu-id="94930-105">Title</span></span>|<span data-ttu-id="94930-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="94930-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="94930-107">O pool de threads gerenciados</span><span class="sxs-lookup"><span data-stu-id="94930-107">The managed thread pool</span></span>](the-managed-thread-pool.md)|<span data-ttu-id="94930-108">Descreve a classe <xref:System.Threading.ThreadPool?displayProperty=nameWithType>, que fornece um pool de threads de trabalho que são gerenciados pelo .NET.</span><span class="sxs-lookup"><span data-stu-id="94930-108">Describes the <xref:System.Threading.ThreadPool?displayProperty=nameWithType> class, which provides a pool of worker threads that are managed by .NET.</span></span>|  
|[<span data-ttu-id="94930-109">Temporizadores</span><span class="sxs-lookup"><span data-stu-id="94930-109">Timers</span></span>](timers.md)|<span data-ttu-id="94930-110">Descreve os temporizadores do .NET que podem ser usados em um ambiente multi-threaded.</span><span class="sxs-lookup"><span data-stu-id="94930-110">Describes .NET timers that can be used in a multithreaded environment.</span></span>|
|[<span data-ttu-id="94930-111">Visão geral dos primitivos de sincronização</span><span class="sxs-lookup"><span data-stu-id="94930-111">Overview of synchronization primitives</span></span>](overview-of-synchronization-primitives.md)|<span data-ttu-id="94930-112">Descreve os tipos que podem ser usados para sincronizar o acesso a um recurso compartilhado ou uma interação de thread de controle.</span><span class="sxs-lookup"><span data-stu-id="94930-112">Describes types that can be used to synchronize access to a shared resource or control thread interaction.</span></span>|
|[<span data-ttu-id="94930-113">EventWaitHandle</span><span class="sxs-lookup"><span data-stu-id="94930-113">EventWaitHandle</span></span>](eventwaithandle.md)|<span data-ttu-id="94930-114">Descreve a classe <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>, que representa um evento de sincronização de thread.</span><span class="sxs-lookup"><span data-stu-id="94930-114">Describes the <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> class, which represents a thread synchronization event.</span></span>|
|[<span data-ttu-id="94930-115">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="94930-115">CountdownEvent</span></span>](countdownevent.md)|<span data-ttu-id="94930-116">Descreve a classe <xref:System.Threading.CountdownEvent?displayProperty=nameWithType>, que representa um evento de sincronização de thread que é definido quando sua contagem é zero.</span><span class="sxs-lookup"><span data-stu-id="94930-116">Describes the <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> class, which represents a thread synchronization event that becomes set when its count is zero.</span></span>|
|[<span data-ttu-id="94930-117">Mutexes</span><span class="sxs-lookup"><span data-stu-id="94930-117">Mutexes</span></span>](mutexes.md)|<span data-ttu-id="94930-118">Descreve a classe <xref:System.Threading.Mutex?displayProperty=nameWithType>, que permite acesso exclusivo a um recurso compartilhado.</span><span class="sxs-lookup"><span data-stu-id="94930-118">Describes the <xref:System.Threading.Mutex?displayProperty=nameWithType> class, which grants exclusive access to a shared resource.</span></span>|
|[<span data-ttu-id="94930-119">Semaphore e SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="94930-119">Semaphore and SemaphoreSlim</span></span>](semaphore-and-semaphoreslim.md)|<span data-ttu-id="94930-120">Descreve a classe <xref:System.Threading.Semaphore?displayProperty=nameWithType>, que limita o número de threads que podem acessar um recurso compartilhado ou um pool de recursos simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="94930-120">Describes the <xref:System.Threading.Semaphore?displayProperty=nameWithType> class, which limits number of threads that can access a shared resource or a pool of resources concurrently.</span></span>|
|[<span data-ttu-id="94930-121">Barreira</span><span class="sxs-lookup"><span data-stu-id="94930-121">Barrier</span></span>](barrier.md)|<span data-ttu-id="94930-122">Descreve a classe <xref:System.Threading.Barrier?displayProperty=nameWithType> que implementa o padrão de barreira para a coordenação de threads em operações em fases.</span><span class="sxs-lookup"><span data-stu-id="94930-122">Describes the <xref:System.Threading.Barrier?displayProperty=nameWithType> class, which implements the barrier pattern for coordination of threads in phased operations.</span></span>|
|[<span data-ttu-id="94930-123">SpinLock</span><span class="sxs-lookup"><span data-stu-id="94930-123">SpinLock</span></span>](spinlock.md)|<span data-ttu-id="94930-124">Descreve a estrutura <xref:System.Threading.SpinLock?displayProperty=nameWithType>, que é uma alternativa leve à classe <xref:System.Threading.Monitor?displayProperty=nameWithType> para certos cenários de bloqueio de nível baixo.</span><span class="sxs-lookup"><span data-stu-id="94930-124">Describes the <xref:System.Threading.SpinLock?displayProperty=nameWithType> structure, which is a lightweight alternative to the <xref:System.Threading.Monitor?displayProperty=nameWithType> class for certain low-level locking scenarios.</span></span>|
|[<span data-ttu-id="94930-125">SpinWait</span><span class="sxs-lookup"><span data-stu-id="94930-125">SpinWait</span></span>](spinwait.md)|<span data-ttu-id="94930-126">Descreve a estrutura de <xref:System.Threading.SpinWait?displayProperty=nameWithType>, que fornece suporte para espera baseada em rotação.</span><span class="sxs-lookup"><span data-stu-id="94930-126">Describes the <xref:System.Threading.SpinWait?displayProperty=nameWithType> structure, which provides support for spin-based waiting.</span></span>|

## <a name="see-also"></a><span data-ttu-id="94930-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="94930-127">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- [<span data-ttu-id="94930-128">Usando threads e threading</span><span class="sxs-lookup"><span data-stu-id="94930-128">Using threads and threading</span></span>](using-threads-and-threading.md)
- [<span data-ttu-id="94930-129">E/S de arquivo assíncrona</span><span class="sxs-lookup"><span data-stu-id="94930-129">Asynchronous File I/O</span></span>](../io/asynchronous-file-i-o.md)
- [<span data-ttu-id="94930-130">Programação paralela</span><span class="sxs-lookup"><span data-stu-id="94930-130">Parallel Programming</span></span>](../parallel-programming/index.md)
- [<span data-ttu-id="94930-131">TPL (Biblioteca de Paralelismo de Tarefas)</span><span class="sxs-lookup"><span data-stu-id="94930-131">Task Parallel Library (TPL)</span></span>](../parallel-programming/task-parallel-library-tpl.md)
