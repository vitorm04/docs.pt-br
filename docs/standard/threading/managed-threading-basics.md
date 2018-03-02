---
title: "Noções básicas de threading gerenciado"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multiple threads
- threading [.NET Framework], multiple threads
- threading [.NET Framework], about threading
- managed threading
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 035834959aa5f9340727327b22cae93b3f21b056
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="managed-threading-basics"></a><span data-ttu-id="4a251-102">Noções básicas de threading gerenciado</span><span class="sxs-lookup"><span data-stu-id="4a251-102">Managed Threading Basics</span></span>
<span data-ttu-id="4a251-103">Os cinco primeiros tópicos desta seção foram projetados para ajudá-lo a determinar quando usar threading gerenciado e explicar alguns recursos básicos.</span><span class="sxs-lookup"><span data-stu-id="4a251-103">The first five topics of this section are designed to help you determine when to use managed threading, and to explain some basic features.</span></span> <span data-ttu-id="4a251-104">Para obter informações sobre as classes que fornecem recursos adicionais, confira [Recursos e objetos de threading](../../../docs/standard/threading/threading-objects-and-features.md) e [Visão geral dos primitivos de sincronização](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="4a251-104">For information on classes that provide additional features, see [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md) and [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="4a251-105">O restante dos tópicos desta seção abordam tópicos avançados, incluindo a interação de threading gerenciado com o sistema operacional Windows.</span><span class="sxs-lookup"><span data-stu-id="4a251-105">The rest of the topics in this section cover advanced topics, including the interaction of managed threading with the Windows operating system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a251-106">No [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], a biblioteca de paralelismo de tarefas e o PLINQ fornecem APIs para o paralelismo de tarefa e dados em programas multithreading.</span><span class="sxs-lookup"><span data-stu-id="4a251-106">In the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the Task Parallel Library and PLINQ provide APIs for task and data parallelism in multi-threaded programs.</span></span> <span data-ttu-id="4a251-107">Para obter mais informações, consulte [Programação paralela](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="4a251-107">For more information, see [Parallel Programming](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4a251-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="4a251-108">In This Section</span></span>  
 [<span data-ttu-id="4a251-109">Threads e threading</span><span class="sxs-lookup"><span data-stu-id="4a251-109">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)  
 <span data-ttu-id="4a251-110">São discutidas as vantagens e desvantagens de vários threads e são descritos os cenários em que você pode criar threads ou usar threads de pool.</span><span class="sxs-lookup"><span data-stu-id="4a251-110">Discusses the advantages and drawbacks of multiple threads, and outlines the scenarios in which you might create threads or use thread pool threads.</span></span>  
  
 [<span data-ttu-id="4a251-111">Exceções em threads gerenciados</span><span class="sxs-lookup"><span data-stu-id="4a251-111">Exceptions in Managed Threads</span></span>](../../../docs/standard/threading/exceptions-in-managed-threads.md)  
 <span data-ttu-id="4a251-112">É descrito o comportamento de exceções sem tratamento em threads para diferentes versões do .NET Framework, em particular as situações em que elas resultam no encerramento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4a251-112">Describes the behavior of unhandled exceptions in threads for different versions of the .NET Framework, in particular the situations in which they result in termination of the application.</span></span>  
  
 [<span data-ttu-id="4a251-113">Sincronizando dados para multithreading</span><span class="sxs-lookup"><span data-stu-id="4a251-113">Synchronizing Data for Multithreading</span></span>](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 <span data-ttu-id="4a251-114">São descritas as estratégias para sincronizar dados em classes que serão usadas com vários threads.</span><span class="sxs-lookup"><span data-stu-id="4a251-114">Describes strategies for synchronizing data in classes that will be used with multiple threads.</span></span>  
  
 [<span data-ttu-id="4a251-115">Estados de thread gerenciado</span><span class="sxs-lookup"><span data-stu-id="4a251-115">Managed Thread States</span></span>](../../../docs/standard/threading/managed-thread-states.md)  
 <span data-ttu-id="4a251-116">São descritos os estados básicos de threads e é explicado como detectar se um thread está em execução.</span><span class="sxs-lookup"><span data-stu-id="4a251-116">Describes the basic thread states, and explains how to detect whether a thread is running.</span></span>  
  
 [<span data-ttu-id="4a251-117">Threads em primeiro plano e em segundo plano</span><span class="sxs-lookup"><span data-stu-id="4a251-117">Foreground and Background Threads</span></span>](../../../docs/standard/threading/foreground-and-background-threads.md)  
 <span data-ttu-id="4a251-118">São explicadas as diferenças entre os threads de primeiro plano e segundo plano.</span><span class="sxs-lookup"><span data-stu-id="4a251-118">Explains the differences between foreground and background threads.</span></span>  
  
 [<span data-ttu-id="4a251-119">Threading gerenciado e não gerenciado no Windows</span><span class="sxs-lookup"><span data-stu-id="4a251-119">Managed and Unmanaged Threading in Windows</span></span>](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)  
 <span data-ttu-id="4a251-120">É discutido o relacionamento entre o threading gerenciado e não gerenciado, são listados os equivalentes gerenciados para APIs de threading do Windows e é discutida a interação de apartments COM e threads gerenciados.</span><span class="sxs-lookup"><span data-stu-id="4a251-120">Discusses the relationship between managed and unmanaged threading, lists managed equivalents for Windows threading APIs, and discusses the interaction of COM apartments and managed threads.</span></span>  
  
 [<span data-ttu-id="4a251-121">Thread.Suspend, coleta de lixo e pontos seguros</span><span class="sxs-lookup"><span data-stu-id="4a251-121">Thread.Suspend, Garbage Collection, and Safe Points</span></span>](../../../docs/standard/threading/thread-suspend-garbage-collection-and-safe-points.md)  
 <span data-ttu-id="4a251-122">São descritas a suspensão de threads e a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="4a251-122">Describes thread suspension and garbage collection.</span></span>  
  
 [<span data-ttu-id="4a251-123">Armazenamento local de thread: campos estáticos relativos a thread e slots de dados</span><span class="sxs-lookup"><span data-stu-id="4a251-123">Thread Local Storage: Thread-Relative Static Fields and Data Slots</span></span>](../../../docs/standard/threading/thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 <span data-ttu-id="4a251-124">São descritos os mecanismos de armazenamento relativos a threads.</span><span class="sxs-lookup"><span data-stu-id="4a251-124">Describes thread-relative storage mechanisms.</span></span>  
  
 [<span data-ttu-id="4a251-125">Cancelamento em threads gerenciados</span><span class="sxs-lookup"><span data-stu-id="4a251-125">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)  
 <span data-ttu-id="4a251-126">É descrito como operações assíncronas ou síncronas de longa execução podem ser canceladas usando um token de cancelamento.</span><span class="sxs-lookup"><span data-stu-id="4a251-126">Describes how asynchronous or long-running synchronous operations can be canceled by using a cancellation token.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="4a251-127">Referência</span><span class="sxs-lookup"><span data-stu-id="4a251-127">Reference</span></span>  
 <xref:System.Threading.Thread>  
 <span data-ttu-id="4a251-128">Fornece documentação de referência para a classe **Thread**, que representa um thread gerenciado, seja ele proveniente de código não gerenciado ou criado em um aplicativo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="4a251-128">Provides reference documentation for the **Thread** class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="4a251-129">É fornecida uma maneira segura de implementar multithreading juntamente com objetos de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="4a251-129">Provides a safe way to implement multithreading in conjunction with user-interface objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4a251-130">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="4a251-130">Related Sections</span></span>  
 [<span data-ttu-id="4a251-131">Visão geral dos primitivos de sincronização</span><span class="sxs-lookup"><span data-stu-id="4a251-131">Overview of Synchronization Primitives</span></span>](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 <span data-ttu-id="4a251-132">São descritas as classes gerenciadas usadas para sincronizar as atividades de vários threads.</span><span class="sxs-lookup"><span data-stu-id="4a251-132">Describes the managed classes used to synchronize the activities of multiple threads.</span></span>  
  
 [<span data-ttu-id="4a251-133">Práticas recomendadas de threading gerenciado</span><span class="sxs-lookup"><span data-stu-id="4a251-133">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 <span data-ttu-id="4a251-134">São descritos problemas comuns com o multithreading e estratégias para evitar problemas.</span><span class="sxs-lookup"><span data-stu-id="4a251-134">Describes common problems with multithreading and strategies for avoiding problems.</span></span>  
  
 [<span data-ttu-id="4a251-135">Programação paralela</span><span class="sxs-lookup"><span data-stu-id="4a251-135">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 <span data-ttu-id="4a251-136">É descrita a biblioteca de paralelismo de tarefas e o PLINQ, que simplifica muito o trabalho de criação de aplicativos do .NET Framework de multithreading e assíncronos.</span><span class="sxs-lookup"><span data-stu-id="4a251-136">Describes the Task Parallel Library and PLINQ, which greatly simplify the work of creating asynchronous and multi-threaded .NET Framework applications.</span></span>
