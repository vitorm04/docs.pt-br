---
title: Threading gerenciado
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 61cd2317b5690573532af2a25c0b84b1fe136fd9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="managed-threading"></a><span data-ttu-id="ce815-102">Threading gerenciado</span><span class="sxs-lookup"><span data-stu-id="ce815-102">Managed Threading</span></span>
<span data-ttu-id="ce815-103">Quer você esteja desenvolvendo para computadores com um processador, quer para com vários, é conveniente que seu aplicativo forneça uma interação mais dinâmica com o usuário, mesmo se o aplicativo, no momento, estiver realizando outro trabalho.</span><span class="sxs-lookup"><span data-stu-id="ce815-103">Whether you are developing for computers with one processor or several, you want your application to provide the most responsive interaction with the user, even if the application is currently doing other work.</span></span> <span data-ttu-id="ce815-104">Usar vários threads de execução é uma das maneiras mais eficazes de manter seu aplicativo responsivo ao usuário e, ao mesmo tempo, usar o processador entre ou, até mesmo, durante os eventos do usuário.</span><span class="sxs-lookup"><span data-stu-id="ce815-104">Using multiple threads of execution is one of the most powerful ways to keep your application responsive to the user and at the same time make use of the processor in between or even during user events.</span></span> <span data-ttu-id="ce815-105">Embora esta seção introduza os conceitos básicos de threading, ele se concentra nos conceitos de threading gerenciado e em como usá-lo.</span><span class="sxs-lookup"><span data-stu-id="ce815-105">While this section introduces the basic concepts of threading, it focuses on managed threading concepts and using managed threading.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ce815-106">A partir do [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], a programação multi-threaded é bastante simplificada com as classes <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>, [PLINQ (LINQ Paralelo)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md), novas classes de coleta simultânea no namespace <xref:System.Collections.Concurrent?displayProperty=nameWithType> e um novo modelo de programação com base no conceito de tarefas em vez de threads.</span><span class="sxs-lookup"><span data-stu-id="ce815-106">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], multithreaded programming is greatly simplified with the <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> classes, [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md), new concurrent collection classes in the <xref:System.Collections.Concurrent?displayProperty=nameWithType> namespace, and a new programming model that is based on the concept of tasks rather than threads.</span></span> <span data-ttu-id="ce815-107">Para obter mais informações, consulte [Programação paralela](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="ce815-107">For more information, see [Parallel Programming](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ce815-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="ce815-108">In This Section</span></span>  
 [<span data-ttu-id="ce815-109">Noções básicas de threading gerenciado</span><span class="sxs-lookup"><span data-stu-id="ce815-109">Managed Threading Basics</span></span>](../../../docs/standard/threading/managed-threading-basics.md)  
 <span data-ttu-id="ce815-110">Fornece uma visão geral de threading gerenciado e descreve quando usar vários threads.</span><span class="sxs-lookup"><span data-stu-id="ce815-110">Provides an overview of managed threading and discusses when to use multiple threads.</span></span>  
  
 [<span data-ttu-id="ce815-111">Usando threads e threading</span><span class="sxs-lookup"><span data-stu-id="ce815-111">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)  
 <span data-ttu-id="ce815-112">Explica como criar, iniciar, pausar, retomar e abortar threads.</span><span class="sxs-lookup"><span data-stu-id="ce815-112">Explains how to create, start, pause, resume, and abort threads.</span></span>  
  
 [<span data-ttu-id="ce815-113">Práticas recomendadas de threading gerenciado</span><span class="sxs-lookup"><span data-stu-id="ce815-113">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 <span data-ttu-id="ce815-114">Aborda os níveis de sincronização, como evitar deadlocks e condições de corrida, computadores com único processador e vários processadores, além de outros problemas de threading.</span><span class="sxs-lookup"><span data-stu-id="ce815-114">Discusses levels of synchronization, how to avoid deadlocks and race conditions, single-processor and multiprocessor computers, and other threading issues.</span></span>  
  
 [<span data-ttu-id="ce815-115">Objetos e recursos de threading</span><span class="sxs-lookup"><span data-stu-id="ce815-115">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 <span data-ttu-id="ce815-116">Descreve as classes gerenciadas que você pode usar para sincronizar as atividades de threads e os dados de objetos acessados em threads diferentes, bem como fornece uma visão geral dos threads de pool do thread.</span><span class="sxs-lookup"><span data-stu-id="ce815-116">Describes the managed classes you can use to synchronize the activities of threads and the data of objects accessed on different threads, and provides an overview of thread pool threads.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ce815-117">Referência</span><span class="sxs-lookup"><span data-stu-id="ce815-117">Reference</span></span>  
 <xref:System.Threading>  
 <span data-ttu-id="ce815-118">Contém classes para uso e sincronização de threads gerenciados.</span><span class="sxs-lookup"><span data-stu-id="ce815-118">Contains classes for using and synchronizing managed threads.</span></span>  
  
 <xref:System.Collections.Concurrent>  
 <span data-ttu-id="ce815-119">Contém classes de coleção que são seguras para uso com vários threads.</span><span class="sxs-lookup"><span data-stu-id="ce815-119">Contains collection classes that are safe for use with multiple threads.</span></span>  
  
 <xref:System.Threading.Tasks>  
 <span data-ttu-id="ce815-120">Contém classes para criação e agendamento de tarefas de processamento simultâneo.</span><span class="sxs-lookup"><span data-stu-id="ce815-120">Contains classes for creating and scheduling concurrent processing tasks.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ce815-121">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="ce815-121">Related Sections</span></span>  
 [<span data-ttu-id="ce815-122">Domínios do aplicativo</span><span class="sxs-lookup"><span data-stu-id="ce815-122">Application Domains</span></span>](../../../docs/framework/app-domains/application-domains.md)  
 <span data-ttu-id="ce815-123">Fornece uma visão geral de domínios do aplicativo e seu uso pelo Common Language Infrastructure.</span><span class="sxs-lookup"><span data-stu-id="ce815-123">Provides an overview of application domains and their use by the Common Language Infrastructure.</span></span>  
  
 [<span data-ttu-id="ce815-124">E/S de arquivo assíncrona</span><span class="sxs-lookup"><span data-stu-id="ce815-124">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 <span data-ttu-id="ce815-125">Descreve as vantagens de desempenho e a operação básica da E/S assíncrona.</span><span class="sxs-lookup"><span data-stu-id="ce815-125">Describes the performance advantages and basic operation of asynchronous I/O.</span></span>  
  
 [<span data-ttu-id="ce815-126">EAP (Padrão Assíncrono baseado em Evento)</span><span class="sxs-lookup"><span data-stu-id="ce815-126">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 <span data-ttu-id="ce815-127">Fornece uma visão geral da programação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="ce815-127">Provides an overview of asynchronous programming.</span></span>  
  
 [<span data-ttu-id="ce815-128">Chamando métodos síncronos de forma assíncrona</span><span class="sxs-lookup"><span data-stu-id="ce815-128">Calling Synchronous Methods Asynchronously</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="ce815-129">Explica como chamar métodos nos threads de pool do thread usando recursos internos de representantes.</span><span class="sxs-lookup"><span data-stu-id="ce815-129">Explains how to call methods on thread pool threads using built-in features of delegates.</span></span>  
  
 [<span data-ttu-id="ce815-130">Programação paralela</span><span class="sxs-lookup"><span data-stu-id="ce815-130">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 <span data-ttu-id="ce815-131">Descreve as bibliotecas de programação paralela, que simplificam o uso de vários threads em aplicativos.</span><span class="sxs-lookup"><span data-stu-id="ce815-131">Describes the parallel programming libraries, which simplify the use of multiple threads in applications.</span></span>  
  
 [<span data-ttu-id="ce815-132">PLINQ (LINQ paralelo)</span><span class="sxs-lookup"><span data-stu-id="ce815-132">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 <span data-ttu-id="ce815-133">Descreve um sistema para executar consultas paralelamente, de modo a aproveitar vários processadores.</span><span class="sxs-lookup"><span data-stu-id="ce815-133">Describes a system for running queries in parallel, to take advantage of multiple processors.</span></span>
