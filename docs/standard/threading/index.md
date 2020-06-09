---
title: Threading gerenciado
description: Consulte links para artigos sobre threads gerenciados no .NET que abrangem as noções básicas, práticas recomendadas, objetos de Threading & recursos, páginas de referência & mais.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
ms.openlocfilehash: 570db45138c85c4252967404da4404d434660d69
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599744"
---
# <a name="managed-threading"></a><span data-ttu-id="57ebc-103">Threading gerenciado</span><span class="sxs-lookup"><span data-stu-id="57ebc-103">Managed Threading</span></span>
<span data-ttu-id="57ebc-104">Quer você esteja desenvolvendo para computadores com um processador, quer para com vários, é conveniente que seu aplicativo forneça uma interação mais dinâmica com o usuário, mesmo se o aplicativo, no momento, estiver realizando outro trabalho.</span><span class="sxs-lookup"><span data-stu-id="57ebc-104">Whether you are developing for computers with one processor or several, you want your application to provide the most responsive interaction with the user, even if the application is currently doing other work.</span></span> <span data-ttu-id="57ebc-105">Usar vários threads de execução é uma das maneiras mais eficazes de manter seu aplicativo responsivo ao usuário e, ao mesmo tempo, usar o processador entre ou, até mesmo, durante os eventos do usuário.</span><span class="sxs-lookup"><span data-stu-id="57ebc-105">Using multiple threads of execution is one of the most powerful ways to keep your application responsive to the user and at the same time make use of the processor in between or even during user events.</span></span> <span data-ttu-id="57ebc-106">Embora esta seção introduza os conceitos básicos de threading, ele se concentra nos conceitos de threading gerenciado e em como usá-lo.</span><span class="sxs-lookup"><span data-stu-id="57ebc-106">While this section introduces the basic concepts of threading, it focuses on managed threading concepts and using managed threading.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="57ebc-107">Começando no .NET Framework 4, a programação multi-threaded ficou bastante simplificada com as classes <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>, o [PLINQ (LINQ paralelo)](../parallel-programming/introduction-to-plinq.md), as novas classes de coleção simultânea no namespace <xref:System.Collections.Concurrent?displayProperty=nameWithType> e um novo modelo de programação que se baseia no conceito de tarefas e não em threads.</span><span class="sxs-lookup"><span data-stu-id="57ebc-107">Starting with the .NET Framework 4, multithreaded programming is greatly simplified with the <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> classes, [Parallel LINQ (PLINQ)](../parallel-programming/introduction-to-plinq.md), new concurrent collection classes in the <xref:System.Collections.Concurrent?displayProperty=nameWithType> namespace, and a new programming model that is based on the concept of tasks rather than threads.</span></span> <span data-ttu-id="57ebc-108">Para obter mais informações, consulte [programação paralela](../parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="57ebc-108">For more information, see [Parallel Programming](../parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="57ebc-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="57ebc-109">In This Section</span></span>  
 [<span data-ttu-id="57ebc-110">Noções básicas sobre Threading gerenciado</span><span class="sxs-lookup"><span data-stu-id="57ebc-110">Managed Threading Basics</span></span>](managed-threading-basics.md)  
 <span data-ttu-id="57ebc-111">Fornece uma visão geral de threading gerenciado e descreve quando usar vários threads.</span><span class="sxs-lookup"><span data-stu-id="57ebc-111">Provides an overview of managed threading and discusses when to use multiple threads.</span></span>  
  
 [<span data-ttu-id="57ebc-112">Usando threads e threading</span><span class="sxs-lookup"><span data-stu-id="57ebc-112">Using Threads and Threading</span></span>](using-threads-and-threading.md)  
 <span data-ttu-id="57ebc-113">Explica como criar, iniciar, pausar, retomar e abortar threads.</span><span class="sxs-lookup"><span data-stu-id="57ebc-113">Explains how to create, start, pause, resume, and abort threads.</span></span>  
  
 [<span data-ttu-id="57ebc-114">Práticas recomendadas de Threading gerenciado</span><span class="sxs-lookup"><span data-stu-id="57ebc-114">Managed Threading Best Practices</span></span>](managed-threading-best-practices.md)  
 <span data-ttu-id="57ebc-115">Aborda os níveis de sincronização, como evitar deadlocks e condições de corrida, além de outros problemas de threading.</span><span class="sxs-lookup"><span data-stu-id="57ebc-115">Discusses levels of synchronization, how to avoid deadlocks and race conditions, and other threading issues.</span></span>  
  
 [<span data-ttu-id="57ebc-116">Objetos e recursos de Threading</span><span class="sxs-lookup"><span data-stu-id="57ebc-116">Threading Objects and Features</span></span>](threading-objects-and-features.md)  
 <span data-ttu-id="57ebc-117">Descreve as classes gerenciadas que você pode usar para sincronizar as atividades de threads e os dados de objetos acessados em threads diferentes, bem como fornece uma visão geral dos threads de pool do thread.</span><span class="sxs-lookup"><span data-stu-id="57ebc-117">Describes the managed classes you can use to synchronize the activities of threads and the data of objects accessed on different threads, and provides an overview of thread pool threads.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="57ebc-118">Referência</span><span class="sxs-lookup"><span data-stu-id="57ebc-118">Reference</span></span>  
 <xref:System.Threading>  
 <span data-ttu-id="57ebc-119">Contém classes para uso e sincronização de threads gerenciados.</span><span class="sxs-lookup"><span data-stu-id="57ebc-119">Contains classes for using and synchronizing managed threads.</span></span>  
  
 <xref:System.Collections.Concurrent>  
 <span data-ttu-id="57ebc-120">Contém classes de coleção que são seguras para uso com vários threads.</span><span class="sxs-lookup"><span data-stu-id="57ebc-120">Contains collection classes that are safe for use with multiple threads.</span></span>  
  
 <xref:System.Threading.Tasks>  
 <span data-ttu-id="57ebc-121">Contém classes para criação e agendamento de tarefas de processamento simultâneo.</span><span class="sxs-lookup"><span data-stu-id="57ebc-121">Contains classes for creating and scheduling concurrent processing tasks.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="57ebc-122">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="57ebc-122">Related Sections</span></span>  
 [<span data-ttu-id="57ebc-123">Domínios do aplicativo</span><span class="sxs-lookup"><span data-stu-id="57ebc-123">Application Domains</span></span>](../../framework/app-domains/application-domains.md)  
 <span data-ttu-id="57ebc-124">Fornece uma visão geral de domínios do aplicativo e seu uso pelo Common Language Infrastructure.</span><span class="sxs-lookup"><span data-stu-id="57ebc-124">Provides an overview of application domains and their use by the Common Language Infrastructure.</span></span>  
  
 [<span data-ttu-id="57ebc-125">E/s de arquivo assíncrono</span><span class="sxs-lookup"><span data-stu-id="57ebc-125">Asynchronous File I/O</span></span>](../io/asynchronous-file-i-o.md)  
 <span data-ttu-id="57ebc-126">Descreve as vantagens de desempenho e a operação básica da E/S assíncrona.</span><span class="sxs-lookup"><span data-stu-id="57ebc-126">Describes the performance advantages and basic operation of asynchronous I/O.</span></span>  
  
 [<span data-ttu-id="57ebc-127">TAP (Padrão Assíncrono Baseado em Tarefa)</span><span class="sxs-lookup"><span data-stu-id="57ebc-127">Task-based Asynchronous Pattern (TAP)</span></span>](../asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 <span data-ttu-id="57ebc-128">Fornece uma visão geral do padrão recomendado para programação assíncrona no .NET.</span><span class="sxs-lookup"><span data-stu-id="57ebc-128">Provides an overview of the recommended pattern for asynchronous programming in .NET.</span></span>  
  
 [<span data-ttu-id="57ebc-129">Chamar métodos síncronos de forma assíncrona</span><span class="sxs-lookup"><span data-stu-id="57ebc-129">Calling Synchronous Methods Asynchronously</span></span>](../asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="57ebc-130">Explica como chamar métodos nos threads de pool do thread usando recursos internos de representantes.</span><span class="sxs-lookup"><span data-stu-id="57ebc-130">Explains how to call methods on thread pool threads using built-in features of delegates.</span></span>  
  
 [<span data-ttu-id="57ebc-131">Programação paralela</span><span class="sxs-lookup"><span data-stu-id="57ebc-131">Parallel Programming</span></span>](../parallel-programming/index.md)  
 <span data-ttu-id="57ebc-132">Descreve as bibliotecas de programação paralela, que simplificam o uso de vários threads em aplicativos.</span><span class="sxs-lookup"><span data-stu-id="57ebc-132">Describes the parallel programming libraries, which simplify the use of multiple threads in applications.</span></span>  
  
 [<span data-ttu-id="57ebc-133">LINQ paralelo (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="57ebc-133">Parallel LINQ (PLINQ)</span></span>](../parallel-programming/introduction-to-plinq.md)  
 <span data-ttu-id="57ebc-134">Descreve um sistema para executar consultas paralelamente, de modo a aproveitar vários processadores.</span><span class="sxs-lookup"><span data-stu-id="57ebc-134">Describes a system for running queries in parallel, to take advantage of multiple processors.</span></span>
