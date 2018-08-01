---
title: Threading de objetos e funcionalidades
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d689aeb91ad79b776c3b93c1809ec46947ea60b
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874781"
---
# <a name="threading-objects-and-features"></a><span data-ttu-id="8be6b-102">Threading de objetos e funcionalidades</span><span class="sxs-lookup"><span data-stu-id="8be6b-102">Threading Objects and Features</span></span>
<span data-ttu-id="8be6b-103">O .NET Framework fornece uma série de objetos que ajudam você a criar e gerenciar aplicativos multi-thread.</span><span class="sxs-lookup"><span data-stu-id="8be6b-103">The .NET Framework provides a number of objects that help you create and manage multithreaded applications.</span></span> <span data-ttu-id="8be6b-104">Os threads gerenciados são representados pela classe <xref:System.Threading.Thread>.</span><span class="sxs-lookup"><span data-stu-id="8be6b-104">Managed threads are represented by the <xref:System.Threading.Thread> class.</span></span> <span data-ttu-id="8be6b-105">A classe <xref:System.Threading.ThreadPool> oferece fácil criação e gerenciamento de tarefas em segundo plano multi-thread.</span><span class="sxs-lookup"><span data-stu-id="8be6b-105">The <xref:System.Threading.ThreadPool> class provides easy creation and management of multithreaded background tasks.</span></span> <span data-ttu-id="8be6b-106">A classe <xref:System.ComponentModel.BackgroundWorker> faz o mesmo para tarefas que interagem com a interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="8be6b-106">The <xref:System.ComponentModel.BackgroundWorker> class does the same for tasks that interact with the user interface.</span></span> <span data-ttu-id="8be6b-107">A classe <xref:System.Threading.Timer> executa tarefas em segundo plano em intervalos regulares.</span><span class="sxs-lookup"><span data-stu-id="8be6b-107">The <xref:System.Threading.Timer> class executes background tasks at timed intervals.</span></span>  
  
 <span data-ttu-id="8be6b-108">Além disso, há uma série de classes que sincronizam atividades de threads, incluindo as classes <xref:System.Threading.Semaphore> e <xref:System.Threading.EventWaitHandle> apresentadas no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="8be6b-108">In addition, there are a number of classes that synchronize activities of threads, including the <xref:System.Threading.Semaphore> and <xref:System.Threading.EventWaitHandle> classes introduced in the .NET Framework version 2.0.</span></span> <span data-ttu-id="8be6b-109">Os recursos dessas classes são comparados na [Visão geral dos primitivos de sincronização](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="8be6b-109">The features of these classes are compared in [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8be6b-110">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="8be6b-110">In This Section</span></span>  
 [<span data-ttu-id="8be6b-111">O pool de threads gerenciados</span><span class="sxs-lookup"><span data-stu-id="8be6b-111">The Managed Thread Pool</span></span>](../../../docs/standard/threading/the-managed-thread-pool.md)  
 <span data-ttu-id="8be6b-112">Explica a classe **ThreadPool**, que permite que você solicite um thread para executar uma tarefa sem ter que fazer qualquer gerenciamento de thread por conta própria.</span><span class="sxs-lookup"><span data-stu-id="8be6b-112">Explains the **ThreadPool** class, which enables you to request a thread to execute a task without having to do any thread management yourself.</span></span>  
  
 [<span data-ttu-id="8be6b-113">Temporizadores</span><span class="sxs-lookup"><span data-stu-id="8be6b-113">Timers</span></span>](../../../docs/standard/threading/timers.md)  
 <span data-ttu-id="8be6b-114">Descreve os temporizadores que podem ser usados em um ambiente multi-threaded.</span><span class="sxs-lookup"><span data-stu-id="8be6b-114">Describes timers that can be used in a multithreaded environment.</span></span>  
  
 [<span data-ttu-id="8be6b-115">Monitores</span><span class="sxs-lookup"><span data-stu-id="8be6b-115">Monitors</span></span>](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
 <span data-ttu-id="8be6b-116">Explica como usar a classe **Monitor** para sincronizar o acesso a um membro ou criar seus próprios tipos de gerenciamento de threads.</span><span class="sxs-lookup"><span data-stu-id="8be6b-116">Explains how to use the **Monitor** class to synchronize access to a member or to build your own thread management types.</span></span>  
  
 [<span data-ttu-id="8be6b-117">Identificadores de espera</span><span class="sxs-lookup"><span data-stu-id="8be6b-117">Wait Handles</span></span>](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 <span data-ttu-id="8be6b-118">Descreve a classe <xref:System.Threading.WaitHandle>, a classe base abstrata para identificadores de espera de eventos, exclusões mútuas e sinais, o que permite a espera de vários eventos de sincronização.</span><span class="sxs-lookup"><span data-stu-id="8be6b-118">Describes the <xref:System.Threading.WaitHandle> class, the abstract base class for event wait handles, mutexes, and semaphores, which enables waiting for multiple synchronization events.</span></span>  
  
 [<span data-ttu-id="8be6b-119">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="8be6b-119">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 <span data-ttu-id="8be6b-120">Descreve os identificadores de espera de eventos gerenciados, que são usados para sincronizar atividades de thread, sinalizando e aguardando sinais.</span><span class="sxs-lookup"><span data-stu-id="8be6b-120">Describes managed event wait handles, which are used to synchronize thread activities by signaling and waiting for signals.</span></span>  
  
 [<span data-ttu-id="8be6b-121">Mutexes</span><span class="sxs-lookup"><span data-stu-id="8be6b-121">Mutexes</span></span>](../../../docs/standard/threading/mutexes.md)  
 <span data-ttu-id="8be6b-122">Explica como usar um <xref:System.Threading.Mutex> para sincronizar o acesso a um objeto ou criar seus próprios mecanismos de sincronização.</span><span class="sxs-lookup"><span data-stu-id="8be6b-122">Explains how to use a <xref:System.Threading.Mutex> to synchronize access to an object or to build your own synchronization mechanisms.</span></span>  
  
 [<span data-ttu-id="8be6b-123">Operações interconectadas</span><span class="sxs-lookup"><span data-stu-id="8be6b-123">Interlocked Operations</span></span>](../../../docs/standard/threading/interlocked-operations.md)  
 <span data-ttu-id="8be6b-124">Explica como usar a classe <xref:System.Threading.Interlocked> para incrementar ou diminuir um valor e armazenar o valor em uma única operação atômica.</span><span class="sxs-lookup"><span data-stu-id="8be6b-124">Explains how to use the <xref:System.Threading.Interlocked> class to increment or decrement a value and store the value in a single atomic operation.</span></span>  
  
 [<span data-ttu-id="8be6b-125">Bloqueios de leitor-gravador</span><span class="sxs-lookup"><span data-stu-id="8be6b-125">Reader-Writer Locks</span></span>](../../../docs/standard/threading/reader-writer-locks.md)  
 <span data-ttu-id="8be6b-126">Define um bloqueio que implementa a semântica de único gravador/vários leitores.</span><span class="sxs-lookup"><span data-stu-id="8be6b-126">Defines a lock that implements single-writer/multiple-reader semantics.</span></span>  
  
 [<span data-ttu-id="8be6b-127">Semaphore e SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="8be6b-127">Semaphore and SemaphoreSlim</span></span>](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)  
 <span data-ttu-id="8be6b-128">Descreve objetos <xref:System.Threading.Semaphore> e explica como usá-los para controlar o acesso a recursos limitados.</span><span class="sxs-lookup"><span data-stu-id="8be6b-128">Describes <xref:System.Threading.Semaphore> objects and explains how to use them to control access to limited resources.</span></span>  
  
 [<span data-ttu-id="8be6b-129">Visão geral dos primitivos de sincronização</span><span class="sxs-lookup"><span data-stu-id="8be6b-129">Overview of Synchronization Primitives</span></span>](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 <span data-ttu-id="8be6b-130">Compara os recursos das classes .NET Framework fornecidas para bloquear e sincronizar threads gerenciados.</span><span class="sxs-lookup"><span data-stu-id="8be6b-130">Compares the features of the .NET Framework classes provided for locking and synchronizing managed threads.</span></span>  
  
 [<span data-ttu-id="8be6b-131">Barreira</span><span class="sxs-lookup"><span data-stu-id="8be6b-131">Barrier</span></span>](../../../docs/standard/threading/barrier.md)  
 <span data-ttu-id="8be6b-132">Descreve objetos <xref:System.Threading.Barrier> que implementam o padrão de barreira para coordenação de threads em operações em fases.</span><span class="sxs-lookup"><span data-stu-id="8be6b-132">Describes <xref:System.Threading.Barrier> objects that implement the barrier pattern for coordination of threads in phased operations.</span></span>  
  
 [<span data-ttu-id="8be6b-133">SpinLock</span><span class="sxs-lookup"><span data-stu-id="8be6b-133">SpinLock</span></span>](../../../docs/standard/threading/spinlock.md)  
 <span data-ttu-id="8be6b-134">Descreve <xref:System.Threading.SpinLock>, uma alternativa leve para a classe Monitor para certos cenários de nível baixo.</span><span class="sxs-lookup"><span data-stu-id="8be6b-134">Describes <xref:System.Threading.SpinLock>, a lightweight alternative to the Monitor class for certain low-level scenarios.</span></span>  
  
 [<span data-ttu-id="8be6b-135">SpinWait</span><span class="sxs-lookup"><span data-stu-id="8be6b-135">SpinWait</span></span>](../../../docs/standard/threading/spinwait.md)  
 <span data-ttu-id="8be6b-136">Descreve <xref:System.Threading.SpinWait>, um primitivo de sincronização de nível baixo que executa a rotação ocupada antes de iniciar uma espera baseada no kernel.</span><span class="sxs-lookup"><span data-stu-id="8be6b-136">Describes <xref:System.Threading.SpinWait>, a low level synchronization primitive that performs busy spinning prior to initiating a kernel-based wait.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="8be6b-137">Referência</span><span class="sxs-lookup"><span data-stu-id="8be6b-137">Reference</span></span>  
 <xref:System.Threading.Thread>  
 <span data-ttu-id="8be6b-138">Fornece documentação de referência para a classe **Thread**, que representa um thread gerenciado, seja ele proveniente de código não gerenciado ou criado em um aplicativo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="8be6b-138">Provides reference documentation for the **Thread** class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="8be6b-139">Permite tarefas em segundo plano que interagem com a interface do usuário, comunicando-se através de eventos criados no thread da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="8be6b-139">Enables background tasks that interact with the user interface, communicating via events raised on the user-interface thread.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8be6b-140">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="8be6b-140">Related Sections</span></span>  
 [<span data-ttu-id="8be6b-141">E/S de arquivo assíncrona</span><span class="sxs-lookup"><span data-stu-id="8be6b-141">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 <span data-ttu-id="8be6b-142">Descreve como as portas de conclusão assíncronas de E/S usam o pool de threads para requerer o processamento somente quando uma operação de entrada/saída é concluída.</span><span class="sxs-lookup"><span data-stu-id="8be6b-142">Describes how I/O asynchronous completion ports use the thread pool to require processing only when an input/output operation completes.</span></span>  
  
 [<span data-ttu-id="8be6b-143">TPL (Biblioteca de Paralelismo de Tarefas)</span><span class="sxs-lookup"><span data-stu-id="8be6b-143">Task Parallel Library (TPL)</span></span>](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 <span data-ttu-id="8be6b-144">Descreve a abordagem recomendada para a programação multi-thread no [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] e posterior.</span><span class="sxs-lookup"><span data-stu-id="8be6b-144">Describes the recommended approach for multithreaded programming in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] and later.</span></span>
