---
title: Estados de thread gerenciado
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: threading [.NET Framework], states
ms.assetid: 63890d5e-6025-4a7c-aaf0-d8bfd54b455f
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 073fb19ef34ba32ccb5d5664413718a436563770
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="managed-thread-states"></a><span data-ttu-id="9b073-102">Estados de thread gerenciado</span><span class="sxs-lookup"><span data-stu-id="9b073-102">Managed Thread States</span></span>
<span data-ttu-id="9b073-103">A propriedade <xref:System.Threading.Thread.ThreadState%2A?displayProperty=nameWithType> fornece uma máscara de bits que indica o estado atual do thread.</span><span class="sxs-lookup"><span data-stu-id="9b073-103">The property <xref:System.Threading.Thread.ThreadState%2A?displayProperty=nameWithType> provides a bit mask that indicates the thread's current state.</span></span> <span data-ttu-id="9b073-104">Um thread é sempre em pelo menos um dos possíveis estados de <xref:System.Threading.ThreadState> enumeração e pode estar em vários estados ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="9b073-104">A thread is always in at least one of the possible states in the <xref:System.Threading.ThreadState> enumeration, and can be in multiple states at the same time.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9b073-105">Estado do segmento é somente de interesse em alguns cenários de depuração.</span><span class="sxs-lookup"><span data-stu-id="9b073-105">Thread state is only of interest in a few debugging scenarios.</span></span> <span data-ttu-id="9b073-106">O código nunca deve usar o estado de thread para sincronizar as atividades de threads.</span><span class="sxs-lookup"><span data-stu-id="9b073-106">Your code should never use thread state to synchronize the activities of threads.</span></span>  
  
 <span data-ttu-id="9b073-107">Quando você cria um thread gerenciado, ele está no <xref:System.Threading.ThreadState.Unstarted> estado.</span><span class="sxs-lookup"><span data-stu-id="9b073-107">When you create a managed thread, it is in the <xref:System.Threading.ThreadState.Unstarted> state.</span></span> <span data-ttu-id="9b073-108">O thread permanece o <xref:System.Threading.ThreadState.Unstarted> estado até que ele é movido para o estado iniciado pelo sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="9b073-108">The thread remains in the <xref:System.Threading.ThreadState.Unstarted> state until it is moved into the started state by the operating system.</span></span> <span data-ttu-id="9b073-109">Chamando <xref:System.Threading.Thread.Start%2A> informa o sistema operacional que o thread pode ser iniciado; ele não altera o estado do thread.</span><span class="sxs-lookup"><span data-stu-id="9b073-109">Calling <xref:System.Threading.Thread.Start%2A> lets the operating system know that the thread can be started; it does not change the state of the thread.</span></span>  
  
 <span data-ttu-id="9b073-110">Threads não gerenciados que entrar no ambiente gerenciado já estão no estado iniciado.</span><span class="sxs-lookup"><span data-stu-id="9b073-110">Unmanaged threads that enter the managed environment are already in the started state.</span></span> <span data-ttu-id="9b073-111">Quando um thread estiver no estado iniciado, uma série de ações pode causar a mudança de estados.</span><span class="sxs-lookup"><span data-stu-id="9b073-111">Once a thread is in the started state, a number of actions can cause it to change states.</span></span> <span data-ttu-id="9b073-112">A tabela a seguir lista as ações que causam uma alteração de estado, juntamente com o novo estado correspondente.</span><span class="sxs-lookup"><span data-stu-id="9b073-112">The following table lists the actions that cause a change of state, along with the corresponding new state.</span></span>  
  
|<span data-ttu-id="9b073-113">Ação</span><span class="sxs-lookup"><span data-stu-id="9b073-113">Action</span></span>|<span data-ttu-id="9b073-114">Novo estado resultante</span><span class="sxs-lookup"><span data-stu-id="9b073-114">Resulting new state</span></span>|  
|------------|-------------------------|  
|<span data-ttu-id="9b073-115">O construtor para o <xref:System.Threading.Thread> classe é chamada.</span><span class="sxs-lookup"><span data-stu-id="9b073-115">The constructor for the <xref:System.Threading.Thread> class is called.</span></span>|<xref:System.Threading.ThreadState.Unstarted>|  
|<span data-ttu-id="9b073-116">Chamadas de outro thread <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9b073-116">Another thread calls <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>.</span></span>|<xref:System.Threading.ThreadState.Unstarted>|  
|<span data-ttu-id="9b073-117">O thread responde a <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> e começa a ser executado.</span><span class="sxs-lookup"><span data-stu-id="9b073-117">The thread responds to <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> and starts running.</span></span>|<xref:System.Threading.ThreadState.Running>|  
|<span data-ttu-id="9b073-118">As chamadas do thread <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9b073-118">The thread calls <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>.</span></span>|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|<span data-ttu-id="9b073-119">As chamadas do thread <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> em outro objeto.</span><span class="sxs-lookup"><span data-stu-id="9b073-119">The thread calls <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> on another object.</span></span>|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|<span data-ttu-id="9b073-120">As chamadas do thread <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> em outro thread.</span><span class="sxs-lookup"><span data-stu-id="9b073-120">The thread calls <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> on another thread.</span></span>|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|<span data-ttu-id="9b073-121">Chamadas de outro thread <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9b073-121">Another thread calls <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>.</span></span>|<xref:System.Threading.ThreadState.SuspendRequested>|  
|<span data-ttu-id="9b073-122">O thread responde a um <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> solicitação.</span><span class="sxs-lookup"><span data-stu-id="9b073-122">The thread responds to a <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> request.</span></span>|<xref:System.Threading.ThreadState.Suspended>|  
|<span data-ttu-id="9b073-123">Chamadas de outro thread <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9b073-123">Another thread calls <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType>.</span></span>|<xref:System.Threading.ThreadState.Running>|  
|<span data-ttu-id="9b073-124">Chamadas de outro thread <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9b073-124">Another thread calls <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span>|<xref:System.Threading.ThreadState.AbortRequested>|  
|<span data-ttu-id="9b073-125">O thread responde a um <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9b073-125">The thread responds to an <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span>|<span data-ttu-id="9b073-126"><xref:System.Threading.ThreadState.Aborted>, em seguida,<xref:System.Threading.ThreadState.Stopped></span><span class="sxs-lookup"><span data-stu-id="9b073-126"><xref:System.Threading.ThreadState.Aborted>, then <xref:System.Threading.ThreadState.Stopped></span></span>|  
  
 <span data-ttu-id="9b073-127">Porque o <xref:System.Threading.ThreadState.Running> estado tem um valor de 0, não é possível executar um teste de bits para descobrir esse estado.</span><span class="sxs-lookup"><span data-stu-id="9b073-127">Because the <xref:System.Threading.ThreadState.Running> state has a value of 0, it is not possible to perform a bit test to discover this state.</span></span> <span data-ttu-id="9b073-128">Em vez disso, o teste a seguir (em pseudocódigo) pode ser usado:</span><span class="sxs-lookup"><span data-stu-id="9b073-128">Instead, the following test (in pseudo-code) can be used:</span></span>  
  
```  
if ((state & (Unstarted | Stopped)) == 0)   // implies Running     
```  
  
 <span data-ttu-id="9b073-129">Threads são geralmente em mais de um estado em um determinado momento.</span><span class="sxs-lookup"><span data-stu-id="9b073-129">Threads are often in more than one state at any given time.</span></span> <span data-ttu-id="9b073-130">Por exemplo, se um thread está bloqueado em uma <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> chamadas de thread de chamada e outro <xref:System.Threading.Thread.Abort%2A> nesse mesmo thread, o thread será no <xref:System.Threading.ThreadState.WaitSleepJoin> e o <xref:System.Threading.ThreadState.AbortRequested> estados ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="9b073-130">For example, if a thread is blocked on a <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> call and another thread calls <xref:System.Threading.Thread.Abort%2A> on that same thread, the thread will be in both the <xref:System.Threading.ThreadState.WaitSleepJoin> and the <xref:System.Threading.ThreadState.AbortRequested> states at the same time.</span></span> <span data-ttu-id="9b073-131">Nesse caso, assim que o thread retorna da chamada para <xref:System.Threading.Monitor.Wait%2A> ou é interrompido, ele receberá o <xref:System.Threading.ThreadAbortException>.</span><span class="sxs-lookup"><span data-stu-id="9b073-131">In that case, as soon as the thread returns from the call to <xref:System.Threading.Monitor.Wait%2A> or is interrupted, it will receive the <xref:System.Threading.ThreadAbortException>.</span></span>  
  
 <span data-ttu-id="9b073-132">Depois que um thread deixa o <xref:System.Threading.ThreadState.Unstarted> estado como resultado de uma chamada para <xref:System.Threading.Thread.Start%2A>, ele nunca pode retornar para o <xref:System.Threading.ThreadState.Unstarted> estado.</span><span class="sxs-lookup"><span data-stu-id="9b073-132">Once a thread leaves the <xref:System.Threading.ThreadState.Unstarted> state as the result of a call to <xref:System.Threading.Thread.Start%2A>, it can never return to the <xref:System.Threading.ThreadState.Unstarted> state.</span></span> <span data-ttu-id="9b073-133">Um thread nunca pode deixar o <xref:System.Threading.ThreadState.Stopped> estado.</span><span class="sxs-lookup"><span data-stu-id="9b073-133">A thread can never leave the <xref:System.Threading.ThreadState.Stopped> state.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b073-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9b073-134">See Also</span></span>  
 <xref:System.Threading.ThreadAbortException>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadState>  
 [<span data-ttu-id="9b073-135">Threading</span><span class="sxs-lookup"><span data-stu-id="9b073-135">Threading</span></span>](../../../docs/standard/threading/index.md)
