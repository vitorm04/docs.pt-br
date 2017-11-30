---
title: Pausando e retomando threads
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
- resuming threads
- threading [.NET Framework], pausing
- pausing threads
ms.assetid: 9fce4859-a19d-4506-b082-7dd0792688ca
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b146987d2491f044e1f5794eba17d02d8f5e478c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="pausing-and-resuming-threads"></a><span data-ttu-id="96604-102">Pausando e retomando threads</span><span class="sxs-lookup"><span data-stu-id="96604-102">Pausing and Resuming Threads</span></span>
<span data-ttu-id="96604-103">As formas mais comuns para sincronizar as atividades de threads são segmentos de bloco e versão, ou objetos de bloqueio ou regiões de código.</span><span class="sxs-lookup"><span data-stu-id="96604-103">The most common ways to synchronize the activities of threads are to block and release threads, or to lock objects or regions of code.</span></span> <span data-ttu-id="96604-104">Para obter mais informações sobre esses bloqueio e mecanismos de bloqueio, consulte [visão geral dos primitivos de sincronização](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="96604-104">For more information on these locking and blocking mechanisms, see [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="96604-105">Você também pode ter threads colocados-se no modo de suspensão.</span><span class="sxs-lookup"><span data-stu-id="96604-105">You can also have threads put themselves to sleep.</span></span> <span data-ttu-id="96604-106">Quando os threads estão bloqueados ou suspenso, você pode usar um <xref:System.Threading.ThreadInterruptedException> para interrompê-las fora de seus estados de espera.</span><span class="sxs-lookup"><span data-stu-id="96604-106">When threads are blocked or sleeping, you can use a <xref:System.Threading.ThreadInterruptedException> to break them out of their wait states.</span></span>  
  
## <a name="the-threadsleep-method"></a><span data-ttu-id="96604-107">O método Sleep</span><span class="sxs-lookup"><span data-stu-id="96604-107">The Thread.Sleep Method</span></span>  
 <span data-ttu-id="96604-108">Chamar o <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> método faz com que o thread atual bloquear imediatamente para o número de milissegundos ou o intervalo de tempo que você passa para o método e produz o resto do seu intervalo de tempo para outro thread.</span><span class="sxs-lookup"><span data-stu-id="96604-108">Calling the <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> method causes the current thread to immediately block for the number of milliseconds or the time interval you pass to the method, and yields the remainder of its time slice to another thread.</span></span> <span data-ttu-id="96604-109">Depois que o intervalo expira, o thread em suspensão retoma a execução.</span><span class="sxs-lookup"><span data-stu-id="96604-109">Once that interval elapses, the sleeping thread resumes execution.</span></span>  
  
 <span data-ttu-id="96604-110">Um thread não é possível chamar <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> em outro thread.</span><span class="sxs-lookup"><span data-stu-id="96604-110">One thread cannot call <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> on another thread.</span></span>  <span data-ttu-id="96604-111"><xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>é um método estático que sempre faz com que o thread atual no modo de suspensão.</span><span class="sxs-lookup"><span data-stu-id="96604-111"><xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> is a static method that always causes the current thread to sleep.</span></span>  
  
 <span data-ttu-id="96604-112">Chamando <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> com um valor de <xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType> faz com que um thread suspenso até que ele seja interrompido por outro thread que chama o <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> método no thread em suspensão ou até que ele seja encerrado por uma chamada para seu <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="96604-112">Calling <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> with a value of <xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType> causes a thread to sleep until it is interrupted by another thread that calls the  <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> method on the sleeping thread, or until it is terminated by a call to its <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method.</span></span>  <span data-ttu-id="96604-113">O exemplo a seguir ilustra os dois métodos de interromper um thread suspenso.</span><span class="sxs-lookup"><span data-stu-id="96604-113">The following example illustrates both methods of interrupting a sleeping thread.</span></span>  
  
 [!code-csharp[Conceptual.Threading.Resuming#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Threading.Resuming/cs/Sleep1.cs#1)]
 [!code-vb[Conceptual.Threading.Resuming#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Threading.Resuming/vb/Sleep1.vb#1)]  
  
## <a name="interrupting-threads"></a><span data-ttu-id="96604-114">Interromper Threads</span><span class="sxs-lookup"><span data-stu-id="96604-114">Interrupting Threads</span></span>  
 <span data-ttu-id="96604-115">Você pode interromper um thread de espera, chamando o <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> método no thread bloqueado para lançar um <xref:System.Threading.ThreadInterruptedException>, que interrompe o thread de chamada de bloqueio.</span><span class="sxs-lookup"><span data-stu-id="96604-115">You can interrupt a waiting thread by calling the <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> method on the blocked thread to throw a <xref:System.Threading.ThreadInterruptedException>, which breaks the thread out of the blocking call.</span></span> <span data-ttu-id="96604-116">O thread deve capturar o <xref:System.Threading.ThreadInterruptedException> e fazer o que for apropriado para continuar trabalhando.</span><span class="sxs-lookup"><span data-stu-id="96604-116">The thread should catch the <xref:System.Threading.ThreadInterruptedException> and do whatever is appropriate to continue working.</span></span> <span data-ttu-id="96604-117">Se o thread ignora a exceção, o runtime captura a exceção e interrompe o thread.</span><span class="sxs-lookup"><span data-stu-id="96604-117">If the thread ignores the exception, the runtime catches the exception and stops the thread.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="96604-118">Se o thread de destino não é bloqueada quando <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> é chamado, o thread não é interrompido até blocos.</span><span class="sxs-lookup"><span data-stu-id="96604-118">If the target thread is not blocked when <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> is called, the thread is not interrupted until it blocks.</span></span> <span data-ttu-id="96604-119">Se o thread nunca bloqueado, ele foi concluído sem nunca sejam interrompidos.</span><span class="sxs-lookup"><span data-stu-id="96604-119">If the thread never blocks, it could complete without ever being interrupted.</span></span>  
  
 <span data-ttu-id="96604-120">Se uma espera é uma espera gerenciada, em seguida, <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> e <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> ambos o thread de ativação imediatamente.</span><span class="sxs-lookup"><span data-stu-id="96604-120">If a wait is a managed wait, then <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> and <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> both wake the thread immediately.</span></span> <span data-ttu-id="96604-121">Se uma espera é uma espera não gerenciada (por exemplo, uma plataforma de invocar a chamada para o Win32 [WaitForSingleObject](https://msdn.microsoft.com/library/windows/desktop/ms687032\(v=vs.85\).aspx) função), nem <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> nem <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> pode assumir o controle do thread até que ele retorna ao ou chama código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="96604-121">If a wait is an unmanaged wait (for example, a platform invoke call to the Win32 [WaitForSingleObject](https://msdn.microsoft.com/library/windows/desktop/ms687032\(v=vs.85\).aspx) function), neither <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> nor <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> can take control of the thread until it returns to or calls into managed code.</span></span> <span data-ttu-id="96604-122">No código gerenciado, o comportamento é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="96604-122">In managed code, the behavior is as follows:</span></span>  
  
-   <span data-ttu-id="96604-123"><xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>Ativar um segmento sem qualquer espera que ele pode estar em e faz com que um <xref:System.Threading.ThreadInterruptedException> seja gerada no thread de destino.</span><span class="sxs-lookup"><span data-stu-id="96604-123"><xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> wakes a thread out of any wait it might be in and causes a <xref:System.Threading.ThreadInterruptedException> to be thrown in the destination thread.</span></span>  
  
-   <span data-ttu-id="96604-124"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>Ativar um segmento sem qualquer espera que ele pode estar em e faz com que um <xref:System.Threading.ThreadAbortException> seja gerada no thread.</span><span class="sxs-lookup"><span data-stu-id="96604-124"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> wakes a thread out of any wait it might be in and causes a <xref:System.Threading.ThreadAbortException> to be thrown on the thread.</span></span> <span data-ttu-id="96604-125">Para obter detalhes, consulte [destruindo Threads](../../../docs/standard/threading/destroying-threads.md).</span><span class="sxs-lookup"><span data-stu-id="96604-125">For details, see [Destroying Threads](../../../docs/standard/threading/destroying-threads.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96604-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96604-126">See Also</span></span>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadInterruptedException>  
 <xref:System.Threading.ThreadAbortException>  
 [<span data-ttu-id="96604-127">Threading</span><span class="sxs-lookup"><span data-stu-id="96604-127">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="96604-128">Usando threads e threading</span><span class="sxs-lookup"><span data-stu-id="96604-128">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)  
 [<span data-ttu-id="96604-129">Visão geral dos primitivos de sincronização</span><span class="sxs-lookup"><span data-stu-id="96604-129">Overview of Synchronization Primitives</span></span>](../../../docs/standard/threading/overview-of-synchronization-primitives.md)
