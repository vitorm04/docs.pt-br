---
title: Noções básicas de threading gerenciado
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- multiple threads
- threading [.NET Framework], multiple threads
- threading [.NET Framework], about threading
- managed threading
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7241dfb7e31ed2f83bf7af0ecc6bf0d97363b999
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65960364"
---
# <a name="managed-threading-basics"></a><span data-ttu-id="c7ba6-102">Noções básicas de threading gerenciado</span><span class="sxs-lookup"><span data-stu-id="c7ba6-102">Managed threading basics</span></span>

<span data-ttu-id="c7ba6-103">Os cinco primeiros tópicos desta seção destinam-se a ajudá-lo a determinar quando usar o threading gerenciado e explicar algumas funcionalidades básicas.</span><span class="sxs-lookup"><span data-stu-id="c7ba6-103">The first five topics of this section are designed to help you determine when to use managed threading and to explain some basic features.</span></span> <span data-ttu-id="c7ba6-104">Para obter informações sobre as classes que fornecem recursos adicionais, confira [Recursos e objetos de threading](../../../docs/standard/threading/threading-objects-and-features.md) e [Visão geral dos primitivos de sincronização](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="c7ba6-104">For information on classes that provide additional features, see [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md) and [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="c7ba6-105">O restante dos tópicos desta seção abordam tópicos avançados, incluindo a interação de threading gerenciado com o sistema operacional Windows.</span><span class="sxs-lookup"><span data-stu-id="c7ba6-105">The rest of the topics in this section cover advanced topics, including the interaction of managed threading with the Windows operating system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c7ba6-106">No [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], a biblioteca de paralelismo de tarefas e o PLINQ fornecem APIs para o paralelismo de tarefa e dados em programas multithreading.</span><span class="sxs-lookup"><span data-stu-id="c7ba6-106">In the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the Task Parallel Library and PLINQ provide APIs for task and data parallelism in multi-threaded programs.</span></span> <span data-ttu-id="c7ba6-107">Para obter mais informações, consulte [Programação paralela](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="c7ba6-107">For more information, see [Parallel Programming](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c7ba6-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="c7ba6-108">In this section</span></span>

 [<span data-ttu-id="c7ba6-109">Threads e threading</span><span class="sxs-lookup"><span data-stu-id="c7ba6-109">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)  
 <span data-ttu-id="c7ba6-110">São discutidas as vantagens e desvantagens de vários threads e são descritos os cenários em que você pode criar threads ou usar threads de pool.</span><span class="sxs-lookup"><span data-stu-id="c7ba6-110">Discusses the advantages and drawbacks of multiple threads, and outlines the scenarios in which you might create threads or use thread pool threads.</span></span>  
  
 [<span data-ttu-id="c7ba6-111">Exceções em threads gerenciados</span><span class="sxs-lookup"><span data-stu-id="c7ba6-111">Exceptions in Managed Threads</span></span>](../../../docs/standard/threading/exceptions-in-managed-threads.md)  
 <span data-ttu-id="c7ba6-112">É descrito o comportamento de exceções sem tratamento em threads para diferentes versões do .NET Framework, em particular as situações em que elas resultam no encerramento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c7ba6-112">Describes the behavior of unhandled exceptions in threads for different versions of the .NET Framework, in particular the situations in which they result in termination of the application.</span></span>  
  
 [<span data-ttu-id="c7ba6-113">Sincronizando dados para multithreading</span><span class="sxs-lookup"><span data-stu-id="c7ba6-113">Synchronizing Data for Multithreading</span></span>](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 <span data-ttu-id="c7ba6-114">São descritas as estratégias para sincronizar dados em classes que serão usadas com vários threads.</span><span class="sxs-lookup"><span data-stu-id="c7ba6-114">Describes strategies for synchronizing data in classes that will be used with multiple threads.</span></span>  
  
 [<span data-ttu-id="c7ba6-115">Threads em primeiro plano e em segundo plano</span><span class="sxs-lookup"><span data-stu-id="c7ba6-115">Foreground and Background Threads</span></span>](../../../docs/standard/threading/foreground-and-background-threads.md)  
 <span data-ttu-id="c7ba6-116">São explicadas as diferenças entre os threads de primeiro plano e segundo plano.</span><span class="sxs-lookup"><span data-stu-id="c7ba6-116">Explains the differences between foreground and background threads.</span></span>  
  
 [<span data-ttu-id="c7ba6-117">Threading gerenciado e não gerenciado no Windows</span><span class="sxs-lookup"><span data-stu-id="c7ba6-117">Managed and Unmanaged Threading in Windows</span></span>](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)  
 <span data-ttu-id="c7ba6-118">É discutido o relacionamento entre o threading gerenciado e não gerenciado, são listados os equivalentes gerenciados para APIs de threading do Windows e é discutida a interação de apartments COM e threads gerenciados.</span><span class="sxs-lookup"><span data-stu-id="c7ba6-118">Discusses the relationship between managed and unmanaged threading, lists managed equivalents for Windows threading APIs, and discusses the interaction of COM apartments and managed threads.</span></span>  
  
 [<span data-ttu-id="c7ba6-119">Armazenamento local de thread: Campos estáticos relativos a thread e slots de dados</span><span class="sxs-lookup"><span data-stu-id="c7ba6-119">Thread Local Storage: Thread-Relative Static Fields and Data Slots</span></span>](../../../docs/standard/threading/thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 <span data-ttu-id="c7ba6-120">São descritos os mecanismos de armazenamento relativos a threads.</span><span class="sxs-lookup"><span data-stu-id="c7ba6-120">Describes thread-relative storage mechanisms.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c7ba6-121">Referência</span><span class="sxs-lookup"><span data-stu-id="c7ba6-121">Reference</span></span>

 <xref:System.Threading.Thread>  
 <span data-ttu-id="c7ba6-122">Fornece documentação de referência para a classe **Thread**, que representa um thread gerenciado, seja ele proveniente de código não gerenciado ou criado em um aplicativo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="c7ba6-122">Provides reference documentation for the **Thread** class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="c7ba6-123">É fornecida uma maneira segura de implementar multithreading juntamente com objetos de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="c7ba6-123">Provides a safe way to implement multithreading in conjunction with user-interface objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c7ba6-124">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="c7ba6-124">Related sections</span></span>

 [<span data-ttu-id="c7ba6-125">Visão geral dos primitivos de sincronização</span><span class="sxs-lookup"><span data-stu-id="c7ba6-125">Overview of Synchronization Primitives</span></span>](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 <span data-ttu-id="c7ba6-126">São descritas as classes gerenciadas usadas para sincronizar as atividades de vários threads.</span><span class="sxs-lookup"><span data-stu-id="c7ba6-126">Describes the managed classes used to synchronize the activities of multiple threads.</span></span>  
  
 [<span data-ttu-id="c7ba6-127">Práticas recomendadas de threading gerenciado</span><span class="sxs-lookup"><span data-stu-id="c7ba6-127">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 <span data-ttu-id="c7ba6-128">São descritos problemas comuns com o multithreading e estratégias para evitar problemas.</span><span class="sxs-lookup"><span data-stu-id="c7ba6-128">Describes common problems with multithreading and strategies for avoiding problems.</span></span>  
  
 [<span data-ttu-id="c7ba6-129">Programação paralela</span><span class="sxs-lookup"><span data-stu-id="c7ba6-129">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 <span data-ttu-id="c7ba6-130">É descrita a biblioteca de paralelismo de tarefas e o PLINQ, que simplifica muito o trabalho de criação de aplicativos do .NET Framework de multithreading e assíncronos.</span><span class="sxs-lookup"><span data-stu-id="c7ba6-130">Describes the Task Parallel Library and PLINQ, which greatly simplify the work of creating asynchronous and multi-threaded .NET Framework applications.</span></span>
