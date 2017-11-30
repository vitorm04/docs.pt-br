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
# <a name="threading-objects-and-features"></a><span data-ttu-id="c0251-102">Threading de objetos e funcionalidades</span><span class="sxs-lookup"><span data-stu-id="c0251-102">Threading Objects and Features</span></span>
<span data-ttu-id="c0251-103">O .NET Framework fornece um número de objetos que o ajudarão a criar e gerenciar aplicativos multithread.</span><span class="sxs-lookup"><span data-stu-id="c0251-103">The .NET Framework provides a number of objects that help you create and manage multithreaded applications.</span></span> <span data-ttu-id="c0251-104">Threads gerenciados são representados pela <xref:System.Threading.Thread> classe.</span><span class="sxs-lookup"><span data-stu-id="c0251-104">Managed threads are represented by the <xref:System.Threading.Thread> class.</span></span> <span data-ttu-id="c0251-105">O <xref:System.Threading.ThreadPool> classe fornece facilitar a criação e gerenciamento de tarefas em segundo plano multi-threaded.</span><span class="sxs-lookup"><span data-stu-id="c0251-105">The <xref:System.Threading.ThreadPool> class provides easy creation and management of multithreaded background tasks.</span></span> <span data-ttu-id="c0251-106">O <xref:System.ComponentModel.BackgroundWorker> classe faz o mesmo para tarefas que interagem com a interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="c0251-106">The <xref:System.ComponentModel.BackgroundWorker> class does the same for tasks that interact with the user interface.</span></span> <span data-ttu-id="c0251-107">O <xref:System.Threading.Timer> classe executa tarefas em segundo plano em intervalos regulares.</span><span class="sxs-lookup"><span data-stu-id="c0251-107">The <xref:System.Threading.Timer> class executes background tasks at timed intervals.</span></span>  
  
 <span data-ttu-id="c0251-108">Além disso, há um número de classes que sincronizam atividades de threads, incluindo o <xref:System.Threading.Semaphore> e <xref:System.Threading.EventWaitHandle> classes introduzidos no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="c0251-108">In addition, there are a number of classes that synchronize activities of threads, including the <xref:System.Threading.Semaphore> and <xref:System.Threading.EventWaitHandle> classes introduced in the .NET Framework version 2.0.</span></span> <span data-ttu-id="c0251-109">Os recursos dessas classes são comparados em [visão geral dos primitivos de sincronização](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="c0251-109">The features of these classes are compared in [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c0251-110">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="c0251-110">In This Section</span></span>  
 [<span data-ttu-id="c0251-111">O pool de threads gerenciados</span><span class="sxs-lookup"><span data-stu-id="c0251-111">The Managed Thread Pool</span></span>](../../../docs/standard/threading/the-managed-thread-pool.md)  
 <span data-ttu-id="c0251-112">Explica o **ThreadPool** classe, que permite que você solicite um thread para executar uma tarefa sem precisar fazer qualquer gerenciamento de threads por conta própria.</span><span class="sxs-lookup"><span data-stu-id="c0251-112">Explains the **ThreadPool** class, which enables you to request a thread to execute a task without having to do any thread management yourself.</span></span>  
  
 [<span data-ttu-id="c0251-113">Temporizadores</span><span class="sxs-lookup"><span data-stu-id="c0251-113">Timers</span></span>](../../../docs/standard/threading/timers.md)  
 <span data-ttu-id="c0251-114">Explica como usar um **Timer** para especificar um delegado a ser chamado em um horário especificado.</span><span class="sxs-lookup"><span data-stu-id="c0251-114">Explains how to use a **Timer** to specify a delegate to be called at a specified time.</span></span>  
  
 [<span data-ttu-id="c0251-115">Monitores</span><span class="sxs-lookup"><span data-stu-id="c0251-115">Monitors</span></span>](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
 <span data-ttu-id="c0251-116">Explica como usar o **Monitor** classe para sincronizar o acesso a um membro ou criar seu próprio thread de tipos de gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="c0251-116">Explains how to use the **Monitor** class to synchronize access to a member or to build your own thread management types.</span></span>  
  
 [<span data-ttu-id="c0251-117">Identificadores de espera</span><span class="sxs-lookup"><span data-stu-id="c0251-117">Wait Handles</span></span>](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 <span data-ttu-id="c0251-118">Descreve o <xref:System.Threading.WaitHandle> classe, a classe base abstrata para evento espera identificadores, mutexes e semáforos, que permite que a espera para vários eventos de sincronização.</span><span class="sxs-lookup"><span data-stu-id="c0251-118">Describes the <xref:System.Threading.WaitHandle> class, the abstract base class for event wait handles, mutexes, and semaphores, which enables waiting for multiple synchronization events.</span></span>  
  
 [<span data-ttu-id="c0251-119">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="c0251-119">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 <span data-ttu-id="c0251-120">Descreve os identificadores de espera de eventos gerenciados, que são usados para sincronizar as atividades de thread de sinalização e esperando por sinais.</span><span class="sxs-lookup"><span data-stu-id="c0251-120">Describes managed event wait handles, which are used to synchronize thread activities by signaling and waiting for signals.</span></span>  
  
 [<span data-ttu-id="c0251-121">Mutexes</span><span class="sxs-lookup"><span data-stu-id="c0251-121">Mutexes</span></span>](../../../docs/standard/threading/mutexes.md)  
 <span data-ttu-id="c0251-122">Explica como usar um <xref:System.Threading.Mutex> para sincronizar o acesso a um objeto ou criar seus próprios mecanismos de sincronização.</span><span class="sxs-lookup"><span data-stu-id="c0251-122">Explains how to use a <xref:System.Threading.Mutex> to synchronize access to an object or to build your own synchronization mechanisms.</span></span>  
  
 [<span data-ttu-id="c0251-123">Operações interconectadas</span><span class="sxs-lookup"><span data-stu-id="c0251-123">Interlocked Operations</span></span>](../../../docs/standard/threading/interlocked-operations.md)  
 <span data-ttu-id="c0251-124">Explica como usar o <xref:System.Threading.Interlocked> classe para incrementar ou decrementar um valor e armazenar o valor em uma única operação atômica.</span><span class="sxs-lookup"><span data-stu-id="c0251-124">Explains how to use the <xref:System.Threading.Interlocked> class to increment or decrement a value and store the value in a single atomic operation.</span></span>  
  
 [<span data-ttu-id="c0251-125">Bloqueios de leitor-gravador</span><span class="sxs-lookup"><span data-stu-id="c0251-125">Reader-Writer Locks</span></span>](../../../docs/standard/threading/reader-writer-locks.md)  
 <span data-ttu-id="c0251-126">Define um bloqueio que implementa a semântica de único gravador/vários leitores.</span><span class="sxs-lookup"><span data-stu-id="c0251-126">Defines a lock that implements single-writer/multiple-reader semantics.</span></span>  
  
 [<span data-ttu-id="c0251-127">Semaphore e SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="c0251-127">Semaphore and SemaphoreSlim</span></span>](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)  
 <span data-ttu-id="c0251-128">Descreve <xref:System.Threading.Semaphore> objetos e explica como usá-las para controlar o acesso aos recursos limitados.</span><span class="sxs-lookup"><span data-stu-id="c0251-128">Describes <xref:System.Threading.Semaphore> objects and explains how to use them to control access to limited resources.</span></span>  
  
 [<span data-ttu-id="c0251-129">Visão geral dos primitivos de sincronização</span><span class="sxs-lookup"><span data-stu-id="c0251-129">Overview of Synchronization Primitives</span></span>](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 <span data-ttu-id="c0251-130">Compara os recursos de classes do .NET Framework fornecidos para bloqueio e sincronizar threads gerenciados.</span><span class="sxs-lookup"><span data-stu-id="c0251-130">Compares the features of the .NET Framework classes provided for locking and synchronizing managed threads.</span></span>  
  
 [<span data-ttu-id="c0251-131">Barreira</span><span class="sxs-lookup"><span data-stu-id="c0251-131">Barrier</span></span>](../../../docs/standard/threading/barrier.md)  
 <span data-ttu-id="c0251-132">Descreve <xref:System.Threading.Barrier> objetos que implementam o padrão de barreira para a coordenação de threads em operações em fases.</span><span class="sxs-lookup"><span data-stu-id="c0251-132">Describes <xref:System.Threading.Barrier> objects that implement the barrier pattern for coordination of threads in phased operations.</span></span>  
  
 [<span data-ttu-id="c0251-133">SpinLock</span><span class="sxs-lookup"><span data-stu-id="c0251-133">SpinLock</span></span>](../../../docs/standard/threading/spinlock.md)  
 <span data-ttu-id="c0251-134">Descreve <xref:System.Threading.SpinLock>, uma alternativa leve para a classe de Monitor para determinados cenários de nível inferior.</span><span class="sxs-lookup"><span data-stu-id="c0251-134">Describes <xref:System.Threading.SpinLock>, a lightweight alternative to the Monitor class for certain low-level scenarios.</span></span>  
  
 [<span data-ttu-id="c0251-135">SpinWait</span><span class="sxs-lookup"><span data-stu-id="c0251-135">SpinWait</span></span>](../../../docs/standard/threading/spinwait.md)  
 <span data-ttu-id="c0251-136">Descreve <xref:System.Threading.SpinWait>, um primitivo de sincronização de nível baixo que executa giratório ocupado antes de iniciar uma espera de kernel.</span><span class="sxs-lookup"><span data-stu-id="c0251-136">Describes <xref:System.Threading.SpinWait>, a low level synchronization primitive that performs busy spinning prior to initiating a kernel-based wait.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c0251-137">Referência</span><span class="sxs-lookup"><span data-stu-id="c0251-137">Reference</span></span>  
 <xref:System.Threading.Thread>  
 <span data-ttu-id="c0251-138">Fornece documentação de referência para o **Thread** classe que representa um segmento gerenciado, se ele veio com código não gerenciado ou foi criado em um aplicativo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="c0251-138">Provides reference documentation for the **Thread** class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="c0251-139">Permite que as tarefas em segundo plano que interagem com a interface do usuário, se comunicar por meio de eventos gerados no thread da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="c0251-139">Enables background tasks that interact with the user interface, communicating via events raised on the user-interface thread.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c0251-140">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="c0251-140">Related Sections</span></span>  
 [<span data-ttu-id="c0251-141">E/S de arquivo assíncrona</span><span class="sxs-lookup"><span data-stu-id="c0251-141">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 <span data-ttu-id="c0251-142">Descreve como as portas de conclusão assíncrona de e/s usam o pool de threads para exigir o processamento somente quando uma operação de entrada/saída é concluída.</span><span class="sxs-lookup"><span data-stu-id="c0251-142">Describes how I/O asynchronous completion ports use the thread pool to require processing only when an input/output operation completes.</span></span>  
  
 [<span data-ttu-id="c0251-143">TPL (Biblioteca de Paralelismo de Tarefas)</span><span class="sxs-lookup"><span data-stu-id="c0251-143">Task Parallel Library (TPL)</span></span>](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 <span data-ttu-id="c0251-144">Descreve a abordagem recomendada para a programação multi-threaded no [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] e posterior.</span><span class="sxs-lookup"><span data-stu-id="c0251-144">Describes the recommended approach for multithreaded programming in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] and later.</span></span>
