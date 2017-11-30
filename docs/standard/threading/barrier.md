---
title: Barreira (.NET Framework)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: synchronization primitives, Barrier
ms.assetid: 613a8bc7-6a28-4795-bd6c-1abd9050478f
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a8111cc9f2798ff96be8b128f22a75d21b441178
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="barrier-net-framework"></a><span data-ttu-id="53c73-102">Barreira (.NET Framework)</span><span class="sxs-lookup"><span data-stu-id="53c73-102">Barrier (.NET Framework)</span></span>
<span data-ttu-id="53c73-103">Um *barreira* é um definido pelo usuário primitivo de sincronização que permite que vários threads (conhecido como *participantes*) para trabalhar simultaneamente em um algoritmo em fases.</span><span class="sxs-lookup"><span data-stu-id="53c73-103">A *barrier* is a user-defined synchronization primitive that enables multiple threads (known as *participants*) to work concurrently on an algorithm in phases.</span></span> <span data-ttu-id="53c73-104">Cada participante executa até atingir o ponto de barreira no código.</span><span class="sxs-lookup"><span data-stu-id="53c73-104">Each participant executes until it reaches the barrier point in the code.</span></span> <span data-ttu-id="53c73-105">A barreira representa o final de uma fase de trabalho.</span><span class="sxs-lookup"><span data-stu-id="53c73-105">The barrier represents the end of one phase of work.</span></span> <span data-ttu-id="53c73-106">Quando um participante alcança a barreira, ele bloqueia até que todos os participantes atingiu a barreira mesmo.</span><span class="sxs-lookup"><span data-stu-id="53c73-106">When a participant reaches the barrier, it blocks until all participants have reached the same barrier.</span></span> <span data-ttu-id="53c73-107">Depois que todos os participantes tiverem chegado a barreira, opcionalmente, você pode chamar uma ação pós-fase.</span><span class="sxs-lookup"><span data-stu-id="53c73-107">After all participants have reached the barrier, you can optionally invoke a post-phase action.</span></span> <span data-ttu-id="53c73-108">Nesta pós-fase de ação pode ser usada para executar ações por um único thread enquanto todos os outros threads ainda estão bloqueados.</span><span class="sxs-lookup"><span data-stu-id="53c73-108">This post-phase action can be used to perform actions by a single thread while all other threads are still blocked.</span></span> <span data-ttu-id="53c73-109">Depois que a ação é executada, os participantes são todos desbloqueados.</span><span class="sxs-lookup"><span data-stu-id="53c73-109">After the action has been executed, the participants are all unblocked.</span></span>  
  
 <span data-ttu-id="53c73-110">O trecho de código a seguir mostra um padrão de barreira básica.</span><span class="sxs-lookup"><span data-stu-id="53c73-110">The following code snippet shows a basic barrier pattern.</span></span>  
  
 [!code-csharp[CDS_Barrier#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#02)]
 [!code-vb[CDS_Barrier#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#02)]  
  
 <span data-ttu-id="53c73-111">Para obter um exemplo completo, consulte [como: sincronizar operações simultâneas com uma barreira](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).</span><span class="sxs-lookup"><span data-stu-id="53c73-111">For a complete example, see [How to: Synchronize Concurrent Operations with a Barrier](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).</span></span>  
  
## <a name="adding-and-removing-participants"></a><span data-ttu-id="53c73-112">Adicionando e removendo participantes</span><span class="sxs-lookup"><span data-stu-id="53c73-112">Adding and Removing Participants</span></span>  
 <span data-ttu-id="53c73-113">Quando você cria um <xref:System.Threading.Barrier>, especifique o número de participantes.</span><span class="sxs-lookup"><span data-stu-id="53c73-113">When you create a <xref:System.Threading.Barrier>, specify the number of participants.</span></span> <span data-ttu-id="53c73-114">Você também pode adicionar ou remover participantes dinamicamente a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="53c73-114">You can also add or remove participants dynamically at any time.</span></span> <span data-ttu-id="53c73-115">Por exemplo, se um participante resolver sua parte do problema, você pode armazenar o resultado, parar a execução no thread e chame <xref:System.Threading.Barrier.RemoveParticipant%2A> para diminuir o número de participantes a barreira.</span><span class="sxs-lookup"><span data-stu-id="53c73-115">For example, if one participant solves its part of the problem, you can store the result, stop execution on that thread, and call <xref:System.Threading.Barrier.RemoveParticipant%2A> to decrement the number of participants in the barrier.</span></span> <span data-ttu-id="53c73-116">Quando você adiciona um participante chamando <xref:System.Threading.Barrier.AddParticipant%2A>, o valor de retorno Especifica o número de fase atual, que pode ser útil para inicializar o trabalho do novo participante.</span><span class="sxs-lookup"><span data-stu-id="53c73-116">When you add a participant by calling <xref:System.Threading.Barrier.AddParticipant%2A>, the return value specifies the current phase number, which may be useful in order to initialize the work of the new participant.</span></span>  
  
## <a name="broken-barriers"></a><span data-ttu-id="53c73-117">Barreiras interrompidas</span><span class="sxs-lookup"><span data-stu-id="53c73-117">Broken Barriers</span></span>  
 <span data-ttu-id="53c73-118">Os deadlocks podem ocorrer se um participante não conseguir alcançar a barreira.</span><span class="sxs-lookup"><span data-stu-id="53c73-118">Deadlocks can occur if one participant fails to reach the barrier.</span></span> <span data-ttu-id="53c73-119">Para evitar esses deadlocks, use as sobrecargas do <xref:System.Threading.Barrier.SignalAndWait%2A> método para especificar um período de tempo limite e um token de cancelamento.</span><span class="sxs-lookup"><span data-stu-id="53c73-119">To avoid these deadlocks, use the overloads of the <xref:System.Threading.Barrier.SignalAndWait%2A> method to specify a time-out period and a cancellation token.</span></span> <span data-ttu-id="53c73-120">Essas sobrecargas retorno um valor booliano que cada participante pode verificar antes de ele continua para a próxima fase.</span><span class="sxs-lookup"><span data-stu-id="53c73-120">These overloads return a Boolean value that every participant can check before it continues to the next phase.</span></span>  
  
## <a name="post-phase-exceptions"></a><span data-ttu-id="53c73-121">Pós-fase de exceções</span><span class="sxs-lookup"><span data-stu-id="53c73-121">Post-Phase Exceptions</span></span>  
 <span data-ttu-id="53c73-122">Se o representante da pós-fase de lança uma exceção, ele é encapsulado em um <xref:System.Threading.BarrierPostPhaseException> objeto que será propagado para todos os participantes.</span><span class="sxs-lookup"><span data-stu-id="53c73-122">If the post-phase delegate throws an exception, it is wrapped in a <xref:System.Threading.BarrierPostPhaseException> object which is then propagated to all participants.</span></span>  
  
## <a name="barrier-versus-continuewhenall"></a><span data-ttu-id="53c73-123">Barreira Versus ContinueWhenAll</span><span class="sxs-lookup"><span data-stu-id="53c73-123">Barrier Versus ContinueWhenAll</span></span>  
 <span data-ttu-id="53c73-124">As barreiras são especialmente úteis quando os threads estão executando várias fases em loops.</span><span class="sxs-lookup"><span data-stu-id="53c73-124">Barriers are especially useful when the threads are performing multiple phases in loops.</span></span> <span data-ttu-id="53c73-125">Se seu código requer somente uma ou duas fases, considere usar <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objetos com qualquer tipo de junção implícita, incluindo:</span><span class="sxs-lookup"><span data-stu-id="53c73-125">If your code requires only one or two phases of work, consider whether to use <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects with any kind of implicit join, including:</span></span>  
  
-   <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.Invoke%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.ForEach%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.For%2A>  
  
 <span data-ttu-id="53c73-126">Para obter mais informações, consulte [Encadeando tarefas com tarefas de continuação](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="53c73-126">For more information, see [Chaining Tasks by Using Continuation Tasks](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53c73-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="53c73-127">See Also</span></span>  
 [<span data-ttu-id="53c73-128">Objetos e recursos de threading</span><span class="sxs-lookup"><span data-stu-id="53c73-128">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="53c73-129">Como sincronizar operações simultâneas com uma barreira</span><span class="sxs-lookup"><span data-stu-id="53c73-129">How to: Synchronize Concurrent Operations with a Barrier</span></span>](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md)
