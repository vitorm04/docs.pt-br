---
title: CountdownEvent
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronization primitives, CountdownEvent
ms.assetid: eec3812a-e20f-4ecd-bfef-6921d508b708
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49b01fdd14d1adfe0480f93150ab6e996aa84dee
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44194687"
---
# <a name="countdownevent"></a><span data-ttu-id="5001e-102">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="5001e-102">CountdownEvent</span></span>
<span data-ttu-id="5001e-103"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType> é um primitivo de sincronização que desbloqueia seus threads em espera após ser sinalizado um determinado número de vezes.</span><span class="sxs-lookup"><span data-stu-id="5001e-103"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType> is a synchronization primitive that unblocks its waiting threads after it has been signaled a certain number of times.</span></span> <span data-ttu-id="5001e-104"><xref:System.Threading.CountdownEvent> foi projetado para cenários em que, caso contrário, seria necessário usar um <xref:System.Threading.ManualResetEvent> ou um <xref:System.Threading.ManualResetEventSlim> e diminuir manualmente uma variável antes de sinalizar o evento.</span><span class="sxs-lookup"><span data-stu-id="5001e-104"><xref:System.Threading.CountdownEvent> is designed for scenarios in which you would otherwise have to use a <xref:System.Threading.ManualResetEvent> or <xref:System.Threading.ManualResetEventSlim> and manually decrement a variable before signaling the event.</span></span> <span data-ttu-id="5001e-105">Por exemplo, em um cenário de bifurcação/junção, basta criar um <xref:System.Threading.CountdownEvent> que tenha uma contagem de sinal de 5 e, em seguida, iniciar cinco itens de trabalho no pool de threads e fazer com que cada item de trabalho chame <xref:System.Threading.CountdownEvent.Signal%2A> quando ele for concluído.</span><span class="sxs-lookup"><span data-stu-id="5001e-105">For example, in a fork/join scenario, you can just create a <xref:System.Threading.CountdownEvent> that has a signal count of 5, and then start five work items on the thread pool and have each work item call <xref:System.Threading.CountdownEvent.Signal%2A> when it completes.</span></span> <span data-ttu-id="5001e-106">Cada chamada para <xref:System.Threading.CountdownEvent.Signal%2A> diminui a contagem de sinal em 1.</span><span class="sxs-lookup"><span data-stu-id="5001e-106">Each call to <xref:System.Threading.CountdownEvent.Signal%2A> decrements the signal count by 1.</span></span> <span data-ttu-id="5001e-107">No thread principal, a chamada para <xref:System.Threading.CountdownEvent.Wait%2A> será bloqueada até que a contagem de sinal seja zero.</span><span class="sxs-lookup"><span data-stu-id="5001e-107">On the main thread, the call to <xref:System.Threading.CountdownEvent.Wait%2A> will block until the signal count is zero.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5001e-108">No caso do código que não têm que interagir com as APIs de sincronização herdadas do .NET Framework, considere o uso de <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objetos ou o método <xref:System.Threading.Tasks.Parallel.Invoke%2A> para uma abordagem ainda mais fácil para expressar o paralelismo bifurcação-junção.</span><span class="sxs-lookup"><span data-stu-id="5001e-108">For code that does not have to interact with legacy .NET Framework synchronization APIs, consider using <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects or the <xref:System.Threading.Tasks.Parallel.Invoke%2A> method for an even easier approach to expressing fork-join parallelism.</span></span>  
  
 <span data-ttu-id="5001e-109"><xref:System.Threading.CountdownEvent> tem estes recursos adicionais:</span><span class="sxs-lookup"><span data-stu-id="5001e-109"><xref:System.Threading.CountdownEvent> has these additional features:</span></span>  
  
-   <span data-ttu-id="5001e-110">A operação de espera pode ser cancelada usando tokens de cancelamento.</span><span class="sxs-lookup"><span data-stu-id="5001e-110">The wait operation can be canceled by using cancellation tokens.</span></span>  
  
-   <span data-ttu-id="5001e-111">Sua contagem de sinal pode ser incrementada depois que a instância for criada.</span><span class="sxs-lookup"><span data-stu-id="5001e-111">Its signal count can be incremented after the instance is created.</span></span>  
  
-   <span data-ttu-id="5001e-112">As instâncias podem ser reutilizadas após <xref:System.Threading.CountdownEvent.Wait%2A> ser retornado ao chamar o método <xref:System.Threading.CountdownEvent.Reset%2A>.</span><span class="sxs-lookup"><span data-stu-id="5001e-112">Instances can be reused after <xref:System.Threading.CountdownEvent.Wait%2A> has returned by calling the <xref:System.Threading.CountdownEvent.Reset%2A> method.</span></span>  
  
-   <span data-ttu-id="5001e-113">As instâncias expõem um <xref:System.Threading.WaitHandle> para integração com outra APIs de sincronização do .NET Framework, como <xref:System.Threading.WaitHandle.WaitAll%2A>.</span><span class="sxs-lookup"><span data-stu-id="5001e-113">Instances expose a <xref:System.Threading.WaitHandle> for integration with other .NET Framework synchronization APIs such as <xref:System.Threading.WaitHandle.WaitAll%2A>.</span></span>  
  
## <a name="basic-usage"></a><span data-ttu-id="5001e-114">Uso básico</span><span class="sxs-lookup"><span data-stu-id="5001e-114">Basic Usage</span></span>  
 <span data-ttu-id="5001e-115">O exemplo a seguir demonstra como usar um <xref:System.Threading.CountdownEvent> com itens de trabalho <xref:System.Threading.ThreadPool>.</span><span class="sxs-lookup"><span data-stu-id="5001e-115">The following example demonstrates how to use a <xref:System.Threading.CountdownEvent> with <xref:System.Threading.ThreadPool> work items.</span></span>  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## <a name="countdownevent-with-cancellation"></a><span data-ttu-id="5001e-116">CountdownEvent com cancelamento</span><span class="sxs-lookup"><span data-stu-id="5001e-116">CountdownEvent With Cancellation</span></span>  
 <span data-ttu-id="5001e-117">O exemplo a seguir mostra como cancelar a operação de espera em <xref:System.Threading.CountdownEvent> usando um token de cancelamento.</span><span class="sxs-lookup"><span data-stu-id="5001e-117">The following example shows how to cancel the wait operation on <xref:System.Threading.CountdownEvent> by using a cancellation token.</span></span> <span data-ttu-id="5001e-118">O padrão básico segue o modelo do cancelamento unificado introduzido em [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5001e-118">The basic pattern follows the model for unified cancellation, which is introduced in [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="5001e-119">Para saber mais, confira [Cancelamento em threads gerenciados](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="5001e-119">For more information, see [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 <span data-ttu-id="5001e-120">Observe que a operação de espera não cancela os threads que a estão sinalizando.</span><span class="sxs-lookup"><span data-stu-id="5001e-120">Note that the wait operation does not cancel the threads that are signaling it.</span></span> <span data-ttu-id="5001e-121">Normalmente, o cancelamento é aplicado a uma operação lógica e isso pode incluir aguardar o evento e todos os itens de trabalho que a espera está sincronizando.</span><span class="sxs-lookup"><span data-stu-id="5001e-121">Typically, cancellation is applied to a logical operation, and that can include waiting on the event as well as all the work items that the wait is synchronizing.</span></span> <span data-ttu-id="5001e-122">Neste exemplo, cada item de trabalho passa uma cópia do mesmo token de cancelamento para que ele possa responder à solicitação de cancelamento.</span><span class="sxs-lookup"><span data-stu-id="5001e-122">In this example, each work item is passed a copy of the same cancellation token so that it can respond to the cancellation request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5001e-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5001e-123">See also</span></span>

- [<span data-ttu-id="5001e-124">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="5001e-124">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)
