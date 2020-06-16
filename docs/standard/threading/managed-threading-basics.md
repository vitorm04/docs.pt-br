---
title: Noções básicas de threading gerenciado
description: Consulte links para outros artigos de Threading gerenciados, abrangendo tópicos como exceções, sincronizando dados, primeiro plano & threads de segundo plano, armazenamento local e muito mais.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- multiple threads
- threading [.NET Framework], multiple threads
- threading [.NET Framework], about threading
- managed threading
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
ms.openlocfilehash: d4a4ceabf29bd0f6f537e59ba477f9da686b1ef5
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769087"
---
# <a name="managed-threading-basics"></a><span data-ttu-id="1ac90-103">Noções básicas de threading gerenciado</span><span class="sxs-lookup"><span data-stu-id="1ac90-103">Managed threading basics</span></span>

<span data-ttu-id="1ac90-104">Os cinco primeiros tópicos desta seção destinam-se a ajudá-lo a determinar quando usar o threading gerenciado e explicar algumas funcionalidades básicas.</span><span class="sxs-lookup"><span data-stu-id="1ac90-104">The first five topics of this section are designed to help you determine when to use managed threading and to explain some basic features.</span></span> <span data-ttu-id="1ac90-105">Para obter informações sobre as classes que fornecem recursos adicionais, confira [Recursos e objetos de threading](threading-objects-and-features.md) e [Visão geral dos primitivos de sincronização](overview-of-synchronization-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="1ac90-105">For information on classes that provide additional features, see [Threading Objects and Features](threading-objects-and-features.md) and [Overview of Synchronization Primitives](overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="1ac90-106">O restante dos tópicos desta seção abordam tópicos avançados, incluindo a interação de threading gerenciado com o sistema operacional Windows.</span><span class="sxs-lookup"><span data-stu-id="1ac90-106">The rest of the topics in this section cover advanced topics, including the interaction of managed threading with the Windows operating system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1ac90-107">No .NET Framework 4, a biblioteca de paralelismo de tarefas e o PLINQ fornecem APIs para o paralelismo de tarefa e dados em programas multithreading.</span><span class="sxs-lookup"><span data-stu-id="1ac90-107">In the .NET Framework 4, the Task Parallel Library and PLINQ provide APIs for task and data parallelism in multi-threaded programs.</span></span> <span data-ttu-id="1ac90-108">Para obter mais informações, consulte [programação paralela](../parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="1ac90-108">For more information, see [Parallel Programming](../parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1ac90-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="1ac90-109">In this section</span></span>

 [<span data-ttu-id="1ac90-110">Threads e threading</span><span class="sxs-lookup"><span data-stu-id="1ac90-110">Threads and Threading</span></span>](threads-and-threading.md)  
 <span data-ttu-id="1ac90-111">São discutidas as vantagens e desvantagens de vários threads e são descritos os cenários em que você pode criar threads ou usar threads de pool.</span><span class="sxs-lookup"><span data-stu-id="1ac90-111">Discusses the advantages and drawbacks of multiple threads, and outlines the scenarios in which you might create threads or use thread pool threads.</span></span>  
  
 [<span data-ttu-id="1ac90-112">Exceções em threads gerenciados</span><span class="sxs-lookup"><span data-stu-id="1ac90-112">Exceptions in Managed Threads</span></span>](exceptions-in-managed-threads.md)  
 <span data-ttu-id="1ac90-113">É descrito o comportamento de exceções sem tratamento em threads para diferentes versões do .NET Framework, em particular as situações em que elas resultam no encerramento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ac90-113">Describes the behavior of unhandled exceptions in threads for different versions of the .NET Framework, in particular the situations in which they result in termination of the application.</span></span>  
  
 [<span data-ttu-id="1ac90-114">Sincronizando dados para multithreading</span><span class="sxs-lookup"><span data-stu-id="1ac90-114">Synchronizing Data for Multithreading</span></span>](synchronizing-data-for-multithreading.md)  
 <span data-ttu-id="1ac90-115">São descritas as estratégias para sincronizar dados em classes que serão usadas com vários threads.</span><span class="sxs-lookup"><span data-stu-id="1ac90-115">Describes strategies for synchronizing data in classes that will be used with multiple threads.</span></span>  
  
 [<span data-ttu-id="1ac90-116">Threads em primeiro plano e em segundo plano</span><span class="sxs-lookup"><span data-stu-id="1ac90-116">Foreground and Background Threads</span></span>](foreground-and-background-threads.md)  
 <span data-ttu-id="1ac90-117">São explicadas as diferenças entre os threads de primeiro plano e segundo plano.</span><span class="sxs-lookup"><span data-stu-id="1ac90-117">Explains the differences between foreground and background threads.</span></span>  
  
 [<span data-ttu-id="1ac90-118">Threads gerenciados e não gerenciados no Windows</span><span class="sxs-lookup"><span data-stu-id="1ac90-118">Managed and Unmanaged Threading in Windows</span></span>](managed-and-unmanaged-threading-in-windows.md)  
 <span data-ttu-id="1ac90-119">É discutido o relacionamento entre o threading gerenciado e não gerenciado, são listados os equivalentes gerenciados para APIs de threading do Windows e é discutida a interação de apartments COM e threads gerenciados.</span><span class="sxs-lookup"><span data-stu-id="1ac90-119">Discusses the relationship between managed and unmanaged threading, lists managed equivalents for Windows threading APIs, and discusses the interaction of COM apartments and managed threads.</span></span>  
  
 [<span data-ttu-id="1ac90-120">Armazenamento local de thread: campos estáticos relativos a thread e slots de dados</span><span class="sxs-lookup"><span data-stu-id="1ac90-120">Thread Local Storage: Thread-Relative Static Fields and Data Slots</span></span>](thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 <span data-ttu-id="1ac90-121">São descritos os mecanismos de armazenamento relativos a threads.</span><span class="sxs-lookup"><span data-stu-id="1ac90-121">Describes thread-relative storage mechanisms.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1ac90-122">Referência</span><span class="sxs-lookup"><span data-stu-id="1ac90-122">Reference</span></span>

 <xref:System.Threading.Thread>  
 <span data-ttu-id="1ac90-123">Fornece documentação de referência para a classe **Thread**, que representa um thread gerenciado, seja ele proveniente de código não gerenciado ou criado em um aplicativo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="1ac90-123">Provides reference documentation for the **Thread** class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="1ac90-124">É fornecida uma maneira segura de implementar multithreading juntamente com objetos de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="1ac90-124">Provides a safe way to implement multithreading in conjunction with user-interface objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1ac90-125">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="1ac90-125">Related sections</span></span>

 [<span data-ttu-id="1ac90-126">Visão geral de primitivos de sincronização</span><span class="sxs-lookup"><span data-stu-id="1ac90-126">Overview of Synchronization Primitives</span></span>](overview-of-synchronization-primitives.md)  
 <span data-ttu-id="1ac90-127">São descritas as classes gerenciadas usadas para sincronizar as atividades de vários threads.</span><span class="sxs-lookup"><span data-stu-id="1ac90-127">Describes the managed classes used to synchronize the activities of multiple threads.</span></span>  
  
 [<span data-ttu-id="1ac90-128">Práticas recomendadas de Threading gerenciado</span><span class="sxs-lookup"><span data-stu-id="1ac90-128">Managed Threading Best Practices</span></span>](managed-threading-best-practices.md)  
 <span data-ttu-id="1ac90-129">São descritos problemas comuns com o multithreading e estratégias para evitar problemas.</span><span class="sxs-lookup"><span data-stu-id="1ac90-129">Describes common problems with multithreading and strategies for avoiding problems.</span></span>  
  
 [<span data-ttu-id="1ac90-130">Programação paralela</span><span class="sxs-lookup"><span data-stu-id="1ac90-130">Parallel Programming</span></span>](../parallel-programming/index.md)  
 <span data-ttu-id="1ac90-131">É descrita a biblioteca de paralelismo de tarefas e o PLINQ, que simplifica muito o trabalho de criação de aplicativos do .NET Framework de multithreading e assíncronos.</span><span class="sxs-lookup"><span data-stu-id="1ac90-131">Describes the Task Parallel Library and PLINQ, which greatly simplify the work of creating asynchronous and multi-threaded .NET Framework applications.</span></span>
