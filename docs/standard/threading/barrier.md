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
helpviewer_keywords:
- synchronization primitives, Barrier
ms.assetid: 613a8bc7-6a28-4795-bd6c-1abd9050478f
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 392e975f6bf566c2ba36290940eb0daee03f004f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="barrier-net-framework"></a><span data-ttu-id="ed205-102">Barreira (.NET Framework)</span><span class="sxs-lookup"><span data-stu-id="ed205-102">Barrier (.NET Framework)</span></span>
<span data-ttu-id="ed205-103">Uma *barreira* é um primitivo de sincronização definido pelo usuário que permite que vários threads (conhecidos como *participantes*) trabalhem simultaneamente em um algoritmo em fases.</span><span class="sxs-lookup"><span data-stu-id="ed205-103">A *barrier* is a user-defined synchronization primitive that enables multiple threads (known as *participants*) to work concurrently on an algorithm in phases.</span></span> <span data-ttu-id="ed205-104">Cada participante executa até atingir o ponto de barreira no código.</span><span class="sxs-lookup"><span data-stu-id="ed205-104">Each participant executes until it reaches the barrier point in the code.</span></span> <span data-ttu-id="ed205-105">A barreira representa o final de uma fase de trabalho.</span><span class="sxs-lookup"><span data-stu-id="ed205-105">The barrier represents the end of one phase of work.</span></span> <span data-ttu-id="ed205-106">Quando um participante alcança a barreira, ela é bloqueada até que todos os participantes atinjam a mesma barreira.</span><span class="sxs-lookup"><span data-stu-id="ed205-106">When a participant reaches the barrier, it blocks until all participants have reached the same barrier.</span></span> <span data-ttu-id="ed205-107">Depois que todos os participantes tiverem chegado à barreira, opcionalmente, você poderá chamar uma ação pós-fase.</span><span class="sxs-lookup"><span data-stu-id="ed205-107">After all participants have reached the barrier, you can optionally invoke a post-phase action.</span></span> <span data-ttu-id="ed205-108">Esta ação pós-fase pode ser usada para executar ações por um único thread enquanto todos os outros threads ainda estiverem bloqueados.</span><span class="sxs-lookup"><span data-stu-id="ed205-108">This post-phase action can be used to perform actions by a single thread while all other threads are still blocked.</span></span> <span data-ttu-id="ed205-109">Após a ação ser executada, todos os participantes serão desbloqueados.</span><span class="sxs-lookup"><span data-stu-id="ed205-109">After the action has been executed, the participants are all unblocked.</span></span>  
  
 <span data-ttu-id="ed205-110">O trecho de código a seguir mostra um padrão de barreira básica.</span><span class="sxs-lookup"><span data-stu-id="ed205-110">The following code snippet shows a basic barrier pattern.</span></span>  
  
 [!code-csharp[CDS_Barrier#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#02)]
 [!code-vb[CDS_Barrier#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#02)]  
  
 <span data-ttu-id="ed205-111">Para um exemplo completo, veja [Como sincronizar operações simultâneas com uma barreira](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).</span><span class="sxs-lookup"><span data-stu-id="ed205-111">For a complete example, see [How to: Synchronize Concurrent Operations with a Barrier](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).</span></span>  
  
## <a name="adding-and-removing-participants"></a><span data-ttu-id="ed205-112">Como adicionar e remover participantes</span><span class="sxs-lookup"><span data-stu-id="ed205-112">Adding and Removing Participants</span></span>  
 <span data-ttu-id="ed205-113">Ao criar um <xref:System.Threading.Barrier>, especifique o número de participantes.</span><span class="sxs-lookup"><span data-stu-id="ed205-113">When you create a <xref:System.Threading.Barrier>, specify the number of participants.</span></span> <span data-ttu-id="ed205-114">Você também pode adicionar ou remover participantes dinamicamente a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="ed205-114">You can also add or remove participants dynamically at any time.</span></span> <span data-ttu-id="ed205-115">Por exemplo, se um participante resolver sua parte do problema, você poderá armazenar o resultado, parar a execução no thread e chamar <xref:System.Threading.Barrier.RemoveParticipant%2A> para diminuir o número de participantes na barreira.</span><span class="sxs-lookup"><span data-stu-id="ed205-115">For example, if one participant solves its part of the problem, you can store the result, stop execution on that thread, and call <xref:System.Threading.Barrier.RemoveParticipant%2A> to decrement the number of participants in the barrier.</span></span> <span data-ttu-id="ed205-116">Quando você adiciona um participante chamando <xref:System.Threading.Barrier.AddParticipant%2A>, o valor de retorno especifica o número de fase atual, que pode ser útil para inicializar o trabalho do novo participante.</span><span class="sxs-lookup"><span data-stu-id="ed205-116">When you add a participant by calling <xref:System.Threading.Barrier.AddParticipant%2A>, the return value specifies the current phase number, which may be useful in order to initialize the work of the new participant.</span></span>  
  
## <a name="broken-barriers"></a><span data-ttu-id="ed205-117">Barreiras interrompidas</span><span class="sxs-lookup"><span data-stu-id="ed205-117">Broken Barriers</span></span>  
 <span data-ttu-id="ed205-118">Os deadlocks podem ocorrer se um participante não conseguir alcançar a barreira.</span><span class="sxs-lookup"><span data-stu-id="ed205-118">Deadlocks can occur if one participant fails to reach the barrier.</span></span> <span data-ttu-id="ed205-119">Para evitar esses deadlocks, use as sobrecargas do método <xref:System.Threading.Barrier.SignalAndWait%2A> para especificar um período de tempo limite e um token de cancelamento.</span><span class="sxs-lookup"><span data-stu-id="ed205-119">To avoid these deadlocks, use the overloads of the <xref:System.Threading.Barrier.SignalAndWait%2A> method to specify a time-out period and a cancellation token.</span></span> <span data-ttu-id="ed205-120">Essas sobrecargas retorno um valor booliano que cada participante pode verificar antes de ele continuar para a próxima fase.</span><span class="sxs-lookup"><span data-stu-id="ed205-120">These overloads return a Boolean value that every participant can check before it continues to the next phase.</span></span>  
  
## <a name="post-phase-exceptions"></a><span data-ttu-id="ed205-121">Exceções pós-fase</span><span class="sxs-lookup"><span data-stu-id="ed205-121">Post-Phase Exceptions</span></span>  
 <span data-ttu-id="ed205-122">Se o representante da pós-fase lançar uma exceção, ele será encapsulado em um objeto <xref:System.Threading.BarrierPostPhaseException> que será, em seguida, propagado para todos os participantes.</span><span class="sxs-lookup"><span data-stu-id="ed205-122">If the post-phase delegate throws an exception, it is wrapped in a <xref:System.Threading.BarrierPostPhaseException> object which is then propagated to all participants.</span></span>  
  
## <a name="barrier-versus-continuewhenall"></a><span data-ttu-id="ed205-123">Barreira versus ContinueWhenAll</span><span class="sxs-lookup"><span data-stu-id="ed205-123">Barrier Versus ContinueWhenAll</span></span>  
 <span data-ttu-id="ed205-124">As barreiras são especialmente úteis quando os threads estão executando várias fases em loops.</span><span class="sxs-lookup"><span data-stu-id="ed205-124">Barriers are especially useful when the threads are performing multiple phases in loops.</span></span> <span data-ttu-id="ed205-125">Caso seu código requeira somente uma ou duas fases de trabalho, considere o uso de objetos <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> com qualquer tipo de junção implícita, incluindo:</span><span class="sxs-lookup"><span data-stu-id="ed205-125">If your code requires only one or two phases of work, consider whether to use <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects with any kind of implicit join, including:</span></span>  
  
-   <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.Invoke%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.ForEach%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.For%2A>  
  
 <span data-ttu-id="ed205-126">Para obter mais informações, consulte [Encadeando tarefas com tarefas de continuação](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="ed205-126">For more information, see [Chaining Tasks by Using Continuation Tasks](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed205-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ed205-127">See Also</span></span>  
 [<span data-ttu-id="ed205-128">Objetos e recursos de threading</span><span class="sxs-lookup"><span data-stu-id="ed205-128">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="ed205-129">Como sincronizar operações simultâneas com uma barreira</span><span class="sxs-lookup"><span data-stu-id="ed205-129">How to: Synchronize Concurrent Operations with a Barrier</span></span>](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md)
