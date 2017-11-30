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
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 62c207f6074e33813887c6903f5285ee72d14e85
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="managed-threading-basics"></a><span data-ttu-id="96da1-102">Noções básicas de threading gerenciado</span><span class="sxs-lookup"><span data-stu-id="96da1-102">Managed Threading Basics</span></span>
<span data-ttu-id="96da1-103">Os cinco primeiros tópicos desta seção são projetados para ajudá-lo a determinar quando usar threading gerenciado e explicar alguns recursos básicos.</span><span class="sxs-lookup"><span data-stu-id="96da1-103">The first five topics of this section are designed to help you determine when to use managed threading, and to explain some basic features.</span></span> <span data-ttu-id="96da1-104">Para obter informações sobre classes que fornecem recursos adicionais, consulte [recursos e objetos de Threading](../../../docs/standard/threading/threading-objects-and-features.md) e [visão geral dos primitivos de sincronização](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="96da1-104">For information on classes that provide additional features, see [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md) and [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="96da1-105">O restante da capa desta seção abordam os tópicos avançados tópicos, incluindo a interação de threading gerenciado com o sistema operacional Windows.</span><span class="sxs-lookup"><span data-stu-id="96da1-105">The rest of the topics in this section cover advanced topics, including the interaction of managed threading with the Windows operating system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="96da1-106">No [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], a biblioteca de tarefas paralelas e em PLINQ fornecem APIs para o paralelismo de tarefa e dados em programas multithread.</span><span class="sxs-lookup"><span data-stu-id="96da1-106">In the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the Task Parallel Library and PLINQ provide APIs for task and data parallelism in multi-threaded programs.</span></span> <span data-ttu-id="96da1-107">Para obter mais informações, consulte [Programação paralela](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="96da1-107">For more information, see [Parallel Programming](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="96da1-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="96da1-108">In This Section</span></span>  
 [<span data-ttu-id="96da1-109">Threads e threading</span><span class="sxs-lookup"><span data-stu-id="96da1-109">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)  
 <span data-ttu-id="96da1-110">Discute as vantagens e desvantagens de vários threads e descreve os cenários em que você pode criar threads ou use threads de pool.</span><span class="sxs-lookup"><span data-stu-id="96da1-110">Discusses the advantages and drawbacks of multiple threads, and outlines the scenarios in which you might create threads or use thread pool threads.</span></span>  
  
 [<span data-ttu-id="96da1-111">Exceções em threads gerenciados</span><span class="sxs-lookup"><span data-stu-id="96da1-111">Exceptions in Managed Threads</span></span>](../../../docs/standard/threading/exceptions-in-managed-threads.md)  
 <span data-ttu-id="96da1-112">Descreve o comportamento de exceções sem tratamento em threads para diferentes versões do .NET Framework, em particular as situações em que eles resultam no encerramento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="96da1-112">Describes the behavior of unhandled exceptions in threads for different versions of the .NET Framework, in particular the situations in which they result in termination of the application.</span></span>  
  
 [<span data-ttu-id="96da1-113">Sincronizando dados para multithreading</span><span class="sxs-lookup"><span data-stu-id="96da1-113">Synchronizing Data for Multithreading</span></span>](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 <span data-ttu-id="96da1-114">Descreve estratégias para sincronizar dados em classes que serão usados com vários threads.</span><span class="sxs-lookup"><span data-stu-id="96da1-114">Describes strategies for synchronizing data in classes that will be used with multiple threads.</span></span>  
  
 [<span data-ttu-id="96da1-115">Estados de thread gerenciado</span><span class="sxs-lookup"><span data-stu-id="96da1-115">Managed Thread States</span></span>](../../../docs/standard/threading/managed-thread-states.md)  
 <span data-ttu-id="96da1-116">Descreve os estados de thread básico e explica como detectar se um thread está em execução.</span><span class="sxs-lookup"><span data-stu-id="96da1-116">Describes the basic thread states, and explains how to detect whether a thread is running.</span></span>  
  
 [<span data-ttu-id="96da1-117">Threads em primeiro plano e em segundo plano</span><span class="sxs-lookup"><span data-stu-id="96da1-117">Foreground and Background Threads</span></span>](../../../docs/standard/threading/foreground-and-background-threads.md)  
 <span data-ttu-id="96da1-118">Explica as diferenças entre os threads de primeiro plano e plano de fundo.</span><span class="sxs-lookup"><span data-stu-id="96da1-118">Explains the differences between foreground and background threads.</span></span>  
  
 [<span data-ttu-id="96da1-119">Threading gerenciado e não gerenciado no Windows</span><span class="sxs-lookup"><span data-stu-id="96da1-119">Managed and Unmanaged Threading in Windows</span></span>](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)  
 <span data-ttu-id="96da1-120">Discute o relacionamento entre threading gerenciado e lista equivalentes gerenciados para threading de APIs do Windows e discute a interação de apartments COM e threads gerenciados.</span><span class="sxs-lookup"><span data-stu-id="96da1-120">Discusses the relationship between managed and unmanaged threading, lists managed equivalents for Windows threading APIs, and discusses the interaction of COM apartments and managed threads.</span></span>  
  
 [<span data-ttu-id="96da1-121">Thread.Suspend, coleta de lixo e pontos seguros</span><span class="sxs-lookup"><span data-stu-id="96da1-121">Thread.Suspend, Garbage Collection, and Safe Points</span></span>](../../../docs/standard/threading/thread-suspend-garbage-collection-and-safe-points.md)  
 <span data-ttu-id="96da1-122">Descreve o thread suspensão e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="96da1-122">Describes thread suspension and garbage collection.</span></span>  
  
 [<span data-ttu-id="96da1-123">Armazenamento local de thread: campos estáticos relativos a thread e slots de dados</span><span class="sxs-lookup"><span data-stu-id="96da1-123">Thread Local Storage: Thread-Relative Static Fields and Data Slots</span></span>](../../../docs/standard/threading/thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 <span data-ttu-id="96da1-124">Descreve os mecanismos de armazenamento relativos a thread.</span><span class="sxs-lookup"><span data-stu-id="96da1-124">Describes thread-relative storage mechanisms.</span></span>  
  
 [<span data-ttu-id="96da1-125">Cancelamento em threads gerenciados</span><span class="sxs-lookup"><span data-stu-id="96da1-125">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)  
 <span data-ttu-id="96da1-126">Descreve como assíncronas ou demoradas operações síncronas podem ser canceladas usando um token de cancelamento.</span><span class="sxs-lookup"><span data-stu-id="96da1-126">Describes how asynchronous or long-running synchronous operations can be canceled by using a cancellation token.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="96da1-127">Referência</span><span class="sxs-lookup"><span data-stu-id="96da1-127">Reference</span></span>  
 <xref:System.Threading.Thread>  
 <span data-ttu-id="96da1-128">Fornece documentação de referência para o **Thread** classe que representa um segmento gerenciado, se ele veio com código não gerenciado ou foi criado em um aplicativo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="96da1-128">Provides reference documentation for the **Thread** class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="96da1-129">Fornece uma maneira segura de implementar multithread juntamente com objetos de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="96da1-129">Provides a safe way to implement multithreading in conjunction with user-interface objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="96da1-130">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="96da1-130">Related Sections</span></span>  
 [<span data-ttu-id="96da1-131">Visão geral dos primitivos de sincronização</span><span class="sxs-lookup"><span data-stu-id="96da1-131">Overview of Synchronization Primitives</span></span>](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 <span data-ttu-id="96da1-132">Descreve as classes gerenciadas usadas para sincronizar as atividades de vários threads.</span><span class="sxs-lookup"><span data-stu-id="96da1-132">Describes the managed classes used to synchronize the activities of multiple threads.</span></span>  
  
 [<span data-ttu-id="96da1-133">Práticas recomendadas de threading gerenciado</span><span class="sxs-lookup"><span data-stu-id="96da1-133">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 <span data-ttu-id="96da1-134">Descreve problemas comuns com multithread e estratégias para evitar problemas.</span><span class="sxs-lookup"><span data-stu-id="96da1-134">Describes common problems with multithreading and strategies for avoiding problems.</span></span>  
  
 [<span data-ttu-id="96da1-135">Programação paralela</span><span class="sxs-lookup"><span data-stu-id="96da1-135">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 <span data-ttu-id="96da1-136">Descreve a biblioteca paralela de tarefas e PLINQ, que simplifica muito o trabalho de criação de aplicativos do .NET Framework multithread e assíncronos.</span><span class="sxs-lookup"><span data-stu-id="96da1-136">Describes the Task Parallel Library and PLINQ, which greatly simplify the work of creating asynchronous and multi-threaded .NET Framework applications.</span></span>
