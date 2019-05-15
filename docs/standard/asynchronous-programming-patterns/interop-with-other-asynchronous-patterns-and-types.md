---
title: Interoperabilidade com outros tipos e padrões assíncronos
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: f120a5d9-933b-4d1d-acb6-f034a57c3749
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2736c4758cbaaeda902b43aeea55611a21ea38ba
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623805"
---
# <a name="interop-with-other-asynchronous-patterns-and-types"></a><span data-ttu-id="12432-102">Interoperabilidade com outros tipos e padrões assíncronos</span><span class="sxs-lookup"><span data-stu-id="12432-102">Interop with Other Asynchronous Patterns and Types</span></span>
<span data-ttu-id="12432-103">O .NET Framework 1.0 introduziu o padrão <xref:System.IAsyncResult>, também conhecido como o [Modelo de programação assíncrona (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) ou o padrão `Begin/End`.</span><span class="sxs-lookup"><span data-stu-id="12432-103">The .NET Framework 1.0 introduced the <xref:System.IAsyncResult> pattern, otherwise known as the [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md), or the `Begin/End` pattern.</span></span>  <span data-ttu-id="12432-104">O .NET Framework 2.0 adicionou o [EAP (Padrão Assíncrono Baseado em Evento)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span><span class="sxs-lookup"><span data-stu-id="12432-104">The .NET Framework 2.0 added the [Event-based Asynchronous Pattern (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span></span>  <span data-ttu-id="12432-105">A partir do .NET Framework 4, o [TAP (Padrão Assíncrono Baseado em Tarefa)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) substitui o APM e o EAP, mas oferece a capacidade de criar facilmente as rotinas de migração dos padrões anteriores.</span><span class="sxs-lookup"><span data-stu-id="12432-105">Starting with the .NET Framework 4, the [Task-based Asynchronous Pattern (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) supersedes both APM and EAP, but provides the ability to easily build migration routines from the earlier patterns.</span></span>  
  
 <span data-ttu-id="12432-106">Neste tópico:</span><span class="sxs-lookup"><span data-stu-id="12432-106">In this topic:</span></span>  
  
- <span data-ttu-id="12432-107">[Tarefas e APM](#APM) ([de APM para TAP](#ApmToTap) ou [de TAP para APM](#TapToApm))</span><span class="sxs-lookup"><span data-stu-id="12432-107">[Tasks and APM](#APM) ([from APM to TAP](#ApmToTap) or [from TAP to APM](#TapToApm))</span></span>  
  
- [<span data-ttu-id="12432-108">Tarefas e EAP</span><span class="sxs-lookup"><span data-stu-id="12432-108">Tasks and EAP</span></span>](#EAP)  
  
- <span data-ttu-id="12432-109">[Tarefas e identificadores de espera](#WaitHandles) ([de identificadores de espera para TAP](#WHToTap) ou [de TAP para identificadores de espera](#TapToWH))</span><span class="sxs-lookup"><span data-stu-id="12432-109">[Tasks and wait handles](#WaitHandles) ([from wait handles to TAP](#WHToTap) or [from TAP to wait handles](#TapToWH))</span></span>  
  
<a name="APM"></a>   
## <a name="tasks-and-the-asynchronous-programming-model-apm"></a><span data-ttu-id="12432-110">Tarefas e APM (Modelo Assíncrono de Programação)</span><span class="sxs-lookup"><span data-stu-id="12432-110">Tasks and the Asynchronous Programming Model (APM)</span></span>  
  
<a name="ApmToTap"></a>   
### <a name="from-apm-to-tap"></a><span data-ttu-id="12432-111">De APM para TAP</span><span class="sxs-lookup"><span data-stu-id="12432-111">From APM to TAP</span></span>  
 <span data-ttu-id="12432-112">Como o padrão [APM (Modelo de programação assíncrona)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) é muito estruturado, é muito fácil criar um wrapper para expor uma implementação do APM como uma implementação do TAP.</span><span class="sxs-lookup"><span data-stu-id="12432-112">Because the [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) pattern is very structured, it is quite easy to build a wrapper to expose an APM implementation as a TAP implementation.</span></span> <span data-ttu-id="12432-113">Na verdade, o .NET Framework, a partir do [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], inclui rotinas auxiliares na forma de sobrecargas do método <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> para fornecer essa tradução.</span><span class="sxs-lookup"><span data-stu-id="12432-113">In fact, the .NET Framework, starting with [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], includes helper routines in the form of <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> method overloads to provide this translation.</span></span>  
  
 <span data-ttu-id="12432-114">Considere a classe <xref:System.IO.Stream> e seus métodos <xref:System.IO.Stream.BeginRead%2A> e <xref:System.IO.Stream.EndRead%2A>, que representam a contrapartida do APM para o método síncrono <xref:System.IO.Stream.Read%2A>:</span><span class="sxs-lookup"><span data-stu-id="12432-114">Consider the <xref:System.IO.Stream> class and its <xref:System.IO.Stream.BeginRead%2A> and <xref:System.IO.Stream.EndRead%2A> methods, which represent the APM counterpart to the synchronous <xref:System.IO.Stream.Read%2A> method:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#1)]
 [!code-vb[Conceptual.AsyncInterop#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#1)]  
[!code-csharp[Conceptual.AsyncInterop#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#2)]
[!code-vb[Conceptual.AsyncInterop#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#2)]  
[!code-csharp[Conceptual.AsyncInterop#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#3)]
[!code-vb[Conceptual.AsyncInterop#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#3)]  
  
 <span data-ttu-id="12432-115">Você pode usar o método <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> para implementar um wrapper do TAP para essa operação da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="12432-115">You can use the <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> method to implement a TAP wrapper for this operation as follows:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap1.cs#4)]
 [!code-vb[Conceptual.AsyncInterop#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap1.vb#4)]  
  
 <span data-ttu-id="12432-116">Essa implementação é semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="12432-116">This implementation is similar to the following:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap2.cs#5)]
 [!code-vb[Conceptual.AsyncInterop#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap2.vb#5)]  
  
<a name="TapToApm"></a>   
### <a name="from-tap-to-apm"></a><span data-ttu-id="12432-117">De TAP para APM</span><span class="sxs-lookup"><span data-stu-id="12432-117">From TAP to APM</span></span>  
 <span data-ttu-id="12432-118">Se a infraestrutura existente esperar o padrão APM, convém também pegar uma implementação do TAP e usá-la onde uma implementação do APM é esperada.</span><span class="sxs-lookup"><span data-stu-id="12432-118">If your existing infrastructure expects the APM pattern, you'll also want to take a TAP implementation and use it where an APM implementation is expected.</span></span>  <span data-ttu-id="12432-119">Como as tarefas podem ser compostas e a classe <xref:System.Threading.Tasks.Task> implementa o <xref:System.IAsyncResult>, você pode usar uma função auxiliar simples para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="12432-119">Because tasks can be composed and  the <xref:System.Threading.Tasks.Task> class implements <xref:System.IAsyncResult>, you can use a straightforward helper function to do this.</span></span> <span data-ttu-id="12432-120">O código a seguir usa uma extensão da classe <xref:System.Threading.Tasks.Task%601>, mas você pode usar uma função quase idêntica para tarefas não genéricas.</span><span class="sxs-lookup"><span data-stu-id="12432-120">The following code uses an extension of the <xref:System.Threading.Tasks.Task%601> class, but you can use an almost identical function for non-generic tasks.</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM1.cs#6)]
 [!code-vb[Conceptual.AsyncInterop#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM1.vb#6)]  
  
 <span data-ttu-id="12432-121">Agora, considere um caso onde você tem a seguinte implementação do TAP:</span><span class="sxs-lookup"><span data-stu-id="12432-121">Now, consider a case where you have the following TAP implementation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#7)]
 [!code-vb[Conceptual.AsyncInterop#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#7)]  
  
 <span data-ttu-id="12432-122">e você deseja oferecer essa implementação do APM:</span><span class="sxs-lookup"><span data-stu-id="12432-122">and you want to provide this APM implementation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#8)]
 [!code-vb[Conceptual.AsyncInterop#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#8)]  
[!code-csharp[Conceptual.AsyncInterop#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#9)]
[!code-vb[Conceptual.AsyncInterop#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#9)]  
  
 <span data-ttu-id="12432-123">O exemplo a seguir demonstra uma migração para APM:</span><span class="sxs-lookup"><span data-stu-id="12432-123">The following example demonstrates one migration to APM:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#10)]
 [!code-vb[Conceptual.AsyncInterop#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#10)]  
  
<a name="EAP"></a>   
## <a name="tasks-and-the-event-based-asynchronous-pattern-eap"></a><span data-ttu-id="12432-124">Tarefas e o EAP (Padrão assíncrono baseado em evento)</span><span class="sxs-lookup"><span data-stu-id="12432-124">Tasks and the Event-based Asynchronous Pattern (EAP)</span></span>  
 <span data-ttu-id="12432-125">Dispor uma implementação do [EAP (Padrão assíncrono baseado em evento)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) é mais envolvente do que dispor um padrão do APM porque o padrão EAP possui mais variações e menos estrutura do que o padrão APM.</span><span class="sxs-lookup"><span data-stu-id="12432-125">Wrapping an [Event-based Asynchronous Pattern (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) implementation is more involved than wrapping an APM pattern, because the EAP pattern has more variation and less structure than the APM pattern.</span></span>  <span data-ttu-id="12432-126">Para demonstrar, o código a seguir se dispõe ao redor do método `DownloadStringAsync`.</span><span class="sxs-lookup"><span data-stu-id="12432-126">To demonstrate, the following code wraps the `DownloadStringAsync` method.</span></span>  <span data-ttu-id="12432-127">`DownloadStringAsync` aceita um URI, gera o evento `DownloadProgressChanged` durante o download para oferecer várias estatísticas sobre o andamento e, quando tiver terminado, gera o evento `DownloadStringCompleted`.</span><span class="sxs-lookup"><span data-stu-id="12432-127">`DownloadStringAsync` accepts a URI, raises the `DownloadProgressChanged` event while downloading in order to report multiple statistics on progress, and raises the `DownloadStringCompleted` event when it's done.</span></span>  <span data-ttu-id="12432-128">O resultado final é uma cadeia de caracteres que contém o conteúdo da página no URI especificado.</span><span class="sxs-lookup"><span data-stu-id="12432-128">The final result is a string that contains the contents of the page at the specified URI.</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/EAP1.cs#11)]
 [!code-vb[Conceptual.AsyncInterop#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/EAP1.vb#11)]  
  
<a name="WaitHandles"></a>   
## <a name="tasks-and-wait-handles"></a><span data-ttu-id="12432-129">Tarefas e identificadores de espera</span><span class="sxs-lookup"><span data-stu-id="12432-129">Tasks and Wait Handles</span></span>  
  
<a name="WHToTap"></a>   
### <a name="from-wait-handles-to-tap"></a><span data-ttu-id="12432-130">De Identificadores de espera para TAP</span><span class="sxs-lookup"><span data-stu-id="12432-130">From Wait Handles to TAP</span></span>  
 <span data-ttu-id="12432-131">Embora os identificadores de espera não implementem um padrão assíncrono, os desenvolvedores avançados podem usar a classe <xref:System.Threading.WaitHandle> e o método <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> em notificações assíncronas quando um identificador de espera estiver definido.</span><span class="sxs-lookup"><span data-stu-id="12432-131">Although wait handles don't implement an asynchronous pattern, advanced developers may use the <xref:System.Threading.WaitHandle> class and the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> method for asynchronous notifications when a wait handle is set.</span></span>  <span data-ttu-id="12432-132">Você pode dispor o método <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> para habilitar uma alternativa baseada em tarefa para qualquer espera síncrona em um identificador de espera:</span><span class="sxs-lookup"><span data-stu-id="12432-132">You can wrap the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> method to enable a task-based alternative to any synchronous wait on a wait handle:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#12)]
 [!code-vb[Conceptual.AsyncInterop#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#12)]  
  
 <span data-ttu-id="12432-133">Com esse método, você pode usar implementações <xref:System.Threading.WaitHandle> existentes em métodos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="12432-133">With this method, you can use existing <xref:System.Threading.WaitHandle> implementations in asynchronous methods.</span></span>  <span data-ttu-id="12432-134">Por exemplo, se quiser limitar o número de operações assíncronas que são executadas em um determinado momento, você pode utilizar um semáforo (um objeto <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="12432-134">For example, if you want to throttle the number of asynchronous operations that are executing at any particular time, you can utilize a semaphore (a <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> object).</span></span>  <span data-ttu-id="12432-135">Você pode limitar para *N* o número de operações executadas simultaneamente ao inicializar a contagem do semáforo em *N*, usar o semáforo sempre que quiser executar uma operação e liberar o semáforo quando terminar uma operação:</span><span class="sxs-lookup"><span data-stu-id="12432-135">You can throttle to *N* the number of operations that run concurrently by initializing the semaphore’s count to *N*, waiting on the semaphore any time you want to perform an operation, and releasing the semaphore when you’re done with an operation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Semaphore1.cs#13)]
 [!code-vb[Conceptual.AsyncInterop#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Semaphore1.vb#13)]  
  
 <span data-ttu-id="12432-136">Você também pode criar um semáforo assíncrono que não depende de identificadores de espera e só trabalha com tarefas.</span><span class="sxs-lookup"><span data-stu-id="12432-136">You can also build an asynchronous semaphore that does not rely on wait handles and instead works completely with tasks.</span></span> <span data-ttu-id="12432-137">Para fazer isso, você pode usar técnicas, como aquelas discutidas em [Consumir o Padrão assíncrono baseado em tarefa](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md), para criar estruturas de dados em cima de <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="12432-137">To do this, you can use techniques such as those discussed in [Consuming the Task-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md) for building data structures on top of <xref:System.Threading.Tasks.Task>.</span></span>  
  
<a name="TapToWH"></a>   
### <a name="from-tap-to-wait-handles"></a><span data-ttu-id="12432-138">De TAP para Identificadores de espera</span><span class="sxs-lookup"><span data-stu-id="12432-138">From TAP to Wait Handles</span></span>  
 <span data-ttu-id="12432-139">Conforme mencionado anteriormente, a classe <xref:System.Threading.Tasks.Task> implementa o <xref:System.IAsyncResult> e essa implementação expõe uma propriedade <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> que retorna um identificador de espera que será definido quando <xref:System.Threading.Tasks.Task> for concluído.</span><span class="sxs-lookup"><span data-stu-id="12432-139">As previously mentioned, the <xref:System.Threading.Tasks.Task> class implements <xref:System.IAsyncResult>, and that implementation exposes an <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> property that returns a wait handle that will be set when the <xref:System.Threading.Tasks.Task> completes.</span></span>  <span data-ttu-id="12432-140">Você pode obter um <xref:System.Threading.WaitHandle> para um <xref:System.Threading.Tasks.Task> da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="12432-140">You can get a <xref:System.Threading.WaitHandle> for a <xref:System.Threading.Tasks.Task> as follows:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#14)]
 [!code-vb[Conceptual.AsyncInterop#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="12432-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="12432-141">See also</span></span>

- [<span data-ttu-id="12432-142">TAP (Padrão Assíncrono Baseado em Tarefa)</span><span class="sxs-lookup"><span data-stu-id="12432-142">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [<span data-ttu-id="12432-143">Implementando o padrão assíncrono baseado em tarefa</span><span class="sxs-lookup"><span data-stu-id="12432-143">Implementing the Task-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)
- [<span data-ttu-id="12432-144">Consumindo o padrão assíncrono baseado em tarefa</span><span class="sxs-lookup"><span data-stu-id="12432-144">Consuming the Task-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)
