---
title: "Interoperabilidade com outros tipos e padrões assíncronos"
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
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: f120a5d9-933b-4d1d-acb6-f034a57c3749
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2e30b562b4795717df526c143df96607686a7582
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="interop-with-other-asynchronous-patterns-and-types"></a><span data-ttu-id="81062-102">Interoperabilidade com outros tipos e padrões assíncronos</span><span class="sxs-lookup"><span data-stu-id="81062-102">Interop with Other Asynchronous Patterns and Types</span></span>
<span data-ttu-id="81062-103">O .NET Framework 1.0 introduziu o <xref:System.IAsyncResult> padrão, também conhecido como o [modelo de programação assíncrona (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md), ou o `Begin/End` padrão.</span><span class="sxs-lookup"><span data-stu-id="81062-103">The .NET Framework 1.0 introduced the <xref:System.IAsyncResult> pattern, otherwise known as the [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md), or the `Begin/End` pattern.</span></span>  <span data-ttu-id="81062-104">O .NET Framework 2.0 adicionado o [padrão assíncrono baseado em evento (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span><span class="sxs-lookup"><span data-stu-id="81062-104">The .NET Framework 2.0 added the [Event-based Asynchronous Pattern (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span></span>  <span data-ttu-id="81062-105">Começando com o .NET Framework 4, o [padrão assíncrono baseado em tarefa (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) substitui o APM e EAP, mas oferece a capacidade de criar facilmente as rotinas de migração dos padrões anteriores.</span><span class="sxs-lookup"><span data-stu-id="81062-105">Starting with the .NET Framework 4, the [Task-based Asynchronous Pattern (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) supersedes both APM and EAP, but provides the ability to easily build migration routines from the earlier patterns.</span></span>  
  
 <span data-ttu-id="81062-106">Neste tópico:</span><span class="sxs-lookup"><span data-stu-id="81062-106">In this topic:</span></span>  
  
-   <span data-ttu-id="81062-107">[Tarefas e APM](#APM) ([do APM para toque](#ApmToTap) ou [de toque para APM](#TapToApm))</span><span class="sxs-lookup"><span data-stu-id="81062-107">[Tasks and APM](#APM) ([from APM to TAP](#ApmToTap) or [from TAP to APM](#TapToApm))</span></span>  
  
-   [<span data-ttu-id="81062-108">Tarefas e EAP</span><span class="sxs-lookup"><span data-stu-id="81062-108">Tasks and EAP</span></span>](#EAP)  
  
-   <span data-ttu-id="81062-109">[Tarefas e identificadores de espera](#WaitHandles) ([de identificadores de espera para toque](#WHToTap) ou [de toque para identificadores de espera](#TapToWH))</span><span class="sxs-lookup"><span data-stu-id="81062-109">[Tasks and wait handles](#WaitHandles) ([from wait handles to TAP](#WHToTap) or [from TAP to wait handles](#TapToWH))</span></span>  
  
<a name="APM"></a>   
## <a name="tasks-and-the-asynchronous-programming-model-apm"></a><span data-ttu-id="81062-110">Tarefas e o modelo de programação assíncrona (APM)</span><span class="sxs-lookup"><span data-stu-id="81062-110">Tasks and the Asynchronous Programming Model (APM)</span></span>  
  
<a name="ApmToTap"></a>   
### <a name="from-apm-to-tap"></a><span data-ttu-id="81062-111">Do APM para toque</span><span class="sxs-lookup"><span data-stu-id="81062-111">From APM to TAP</span></span>  
 <span data-ttu-id="81062-112">Porque o [modelo de programação assíncrona (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) padrão é muito estruturado, é muito fácil criar um wrapper para expor uma implementação de APM como uma implementação de toque.</span><span class="sxs-lookup"><span data-stu-id="81062-112">Because the [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) pattern is very structured, it is quite easy to build a wrapper to expose an APM implementation as a TAP implementation.</span></span> <span data-ttu-id="81062-113">Na verdade, o .NET Framework, começando com [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], inclui rotinas auxiliares na forma de <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> sobrecargas do método para fornecer essa conversão.</span><span class="sxs-lookup"><span data-stu-id="81062-113">In fact, the .NET Framework, starting with [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], includes helper routines in the form of <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> method overloads to provide this translation.</span></span>  
  
 <span data-ttu-id="81062-114">Considere o <xref:System.IO.Stream> classe e seu <xref:System.IO.Stream.BeginRead%2A> e <xref:System.IO.Stream.EndRead%2A> métodos, que representam a contraparte APM para o síncrona <xref:System.IO.Stream.Read%2A> método:</span><span class="sxs-lookup"><span data-stu-id="81062-114">Consider the <xref:System.IO.Stream> class and its <xref:System.IO.Stream.BeginRead%2A> and <xref:System.IO.Stream.EndRead%2A> methods, which represent the APM counterpart to the synchronous <xref:System.IO.Stream.Read%2A> method:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#1)]
 [!code-vb[Conceptual.AsyncInterop#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#1)]  
[!code-csharp[Conceptual.AsyncInterop#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#2)]
[!code-vb[Conceptual.AsyncInterop#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#2)]  
[!code-csharp[Conceptual.AsyncInterop#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#3)]
[!code-vb[Conceptual.AsyncInterop#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#3)]  
  
 <span data-ttu-id="81062-115">Você pode usar o <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> método para implementar um wrapper de toque para essa operação da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="81062-115">You can use the <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> method to implement a TAP wrapper for this operation as follows:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap1.cs#4)]
 [!code-vb[Conceptual.AsyncInterop#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap1.vb#4)]  
  
 <span data-ttu-id="81062-116">Essa implementação é semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="81062-116">This implementation is similar to the following:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap2.cs#5)]
 [!code-vb[Conceptual.AsyncInterop#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap2.vb#5)]  
  
<a name="TapToApm"></a>   
### <a name="from-tap-to-apm"></a><span data-ttu-id="81062-117">De toque para APM</span><span class="sxs-lookup"><span data-stu-id="81062-117">From TAP to APM</span></span>  
 <span data-ttu-id="81062-118">Se sua infraestrutura existente espera o padrão do APM, você também vai querer levar uma implementação de toque e usá-lo em uma implementação de APM é esperada.</span><span class="sxs-lookup"><span data-stu-id="81062-118">If your existing infrastructure expects the APM pattern, you'll also want to take a TAP implementation and use it where an APM implementation is expected.</span></span>  <span data-ttu-id="81062-119">Como as tarefas podem ser compostas e <xref:System.Threading.Tasks.Task> classe implementa <xref:System.IAsyncResult>, você pode usar uma função auxiliar simples para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="81062-119">Because tasks can be composed and  the <xref:System.Threading.Tasks.Task> class implements <xref:System.IAsyncResult>, you can use a straightforward helper function to do this.</span></span> <span data-ttu-id="81062-120">O código a seguir usa uma extensão de <xref:System.Threading.Tasks.Task%601> classe, mas você pode usar uma função de quase idêntica para tarefas não genérico.</span><span class="sxs-lookup"><span data-stu-id="81062-120">The following code uses an extension of the <xref:System.Threading.Tasks.Task%601> class, but you can use an almost identical function for non-generic tasks.</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM1.cs#6)]
 [!code-vb[Conceptual.AsyncInterop#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM1.vb#6)]  
  
 <span data-ttu-id="81062-121">Agora, considere um caso em que a implementação de toque a seguir:</span><span class="sxs-lookup"><span data-stu-id="81062-121">Now, consider a case where you have the following TAP implementation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#7)]
 [!code-vb[Conceptual.AsyncInterop#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#7)]  
  
 <span data-ttu-id="81062-122">e você deseja fornecer essa implementação de APM:</span><span class="sxs-lookup"><span data-stu-id="81062-122">and you want to provide this APM implementation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#8)]
 [!code-vb[Conceptual.AsyncInterop#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#8)]  
[!code-csharp[Conceptual.AsyncInterop#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#9)]
[!code-vb[Conceptual.AsyncInterop#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#9)]  
  
 <span data-ttu-id="81062-123">O exemplo a seguir demonstra uma migração para o APM:</span><span class="sxs-lookup"><span data-stu-id="81062-123">The following example demonstrates one migration to APM:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#10)]
 [!code-vb[Conceptual.AsyncInterop#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#10)]  
  
<a name="EAP"></a>   
## <a name="tasks-and-the-event-based-asynchronous-pattern-eap"></a><span data-ttu-id="81062-124">Tarefas e o padrão assíncrono baseado em evento (EAP)</span><span class="sxs-lookup"><span data-stu-id="81062-124">Tasks and the Event-based Asynchronous Pattern (EAP)</span></span>  
 <span data-ttu-id="81062-125">Quebra automática de um [padrão assíncrono baseado em evento (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) implementação é mais envolvida que quebra automática de um padrão APM, porque o padrão EAP possui uma variação mais e menos estrutura que o padrão do APM.</span><span class="sxs-lookup"><span data-stu-id="81062-125">Wrapping an [Event-based Asynchronous Pattern (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) implementation is more involved than wrapping an APM pattern, because the EAP pattern has more variation and less structure than the APM pattern.</span></span>  <span data-ttu-id="81062-126">Para demonstrar, o código a seguir encapsula o `DownloadStringAsync` método.</span><span class="sxs-lookup"><span data-stu-id="81062-126">To demonstrate, the following code wraps the `DownloadStringAsync` method.</span></span>  <span data-ttu-id="81062-127">`DownloadStringAsync`aceita um URI, dispara o `DownloadProgressChanged` eventos durante o download para relatar várias estatísticas em andamento e gera o `DownloadStringCompleted` eventos quando tiver terminado.</span><span class="sxs-lookup"><span data-stu-id="81062-127">`DownloadStringAsync` accepts a URI, raises the `DownloadProgressChanged` event while downloading in order to report multiple statistics on progress, and raises the `DownloadStringCompleted` event when it's done.</span></span>  <span data-ttu-id="81062-128">O resultado final é uma cadeia de caracteres que contém o conteúdo da página no URI especificado.</span><span class="sxs-lookup"><span data-stu-id="81062-128">The final result is a string that contains the contents of the page at the specified URI.</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/EAP1.cs#11)]
 [!code-vb[Conceptual.AsyncInterop#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/EAP1.vb#11)]  
  
<a name="WaitHandles"></a>   
## <a name="tasks-and-wait-handles"></a><span data-ttu-id="81062-129">Tarefas e identificadores de espera</span><span class="sxs-lookup"><span data-stu-id="81062-129">Tasks and Wait Handles</span></span>  
  
<a name="WHToTap"></a>   
### <a name="from-wait-handles-to-tap"></a><span data-ttu-id="81062-130">De identificadores de espera para toque</span><span class="sxs-lookup"><span data-stu-id="81062-130">From Wait Handles to TAP</span></span>  
 <span data-ttu-id="81062-131">Embora os identificadores de espera não implementam um padrão assíncrono, os desenvolvedores avançados podem usar o <xref:System.Threading.WaitHandle> classe e o <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> método para notificações assíncronas quando um identificador de espera é definido.</span><span class="sxs-lookup"><span data-stu-id="81062-131">Although wait handles don't implement an asynchronous pattern, advanced developers may use the <xref:System.Threading.WaitHandle> class and the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> method for asynchronous notifications when a wait handle is set.</span></span>  <span data-ttu-id="81062-132">Você pode encapsular a <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> método para habilitar uma alternativa baseada em tarefa para qualquer espera síncrona em um identificador de espera:</span><span class="sxs-lookup"><span data-stu-id="81062-132">You can wrap the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> method to enable a task-based alternative to any synchronous wait on a wait handle:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#12)]
 [!code-vb[Conceptual.AsyncInterop#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#12)]  
  
 <span data-ttu-id="81062-133">Com esse método, você pode usar existente <xref:System.Threading.WaitHandle> implementações de métodos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="81062-133">With this method, you can use existing <xref:System.Threading.WaitHandle> implementations in asynchronous methods.</span></span>  <span data-ttu-id="81062-134">Por exemplo, se você deseja limitar o número de operações assíncronas que são executados em um determinado momento, você pode utilizar um semáforo (um <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> objeto).</span><span class="sxs-lookup"><span data-stu-id="81062-134">For example, if you want to throttle the number of asynchronous operations that are executing at any particular time, you can utilize a semaphore (a <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> object).</span></span>  <span data-ttu-id="81062-135">Você pode acelerar a *N* o número de operações executadas simultaneamente por inicializar a contagem do sinal para *N*, esperando o semáforo sempre que quiser executar uma operação e liberar o semáforo quando terminar com uma operação:</span><span class="sxs-lookup"><span data-stu-id="81062-135">You can throttle to *N* the number of operations that run concurrently by initializing the semaphore’s count to *N*, waiting on the semaphore any time you want to perform an operation, and releasing the semaphore when you’re done with an operation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Semaphore1.cs#13)]
 [!code-vb[Conceptual.AsyncInterop#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Semaphore1.vb#13)]  
  
 <span data-ttu-id="81062-136">Você também pode criar um semáforo assíncrono que não depende de identificadores de espera e trabalha completamente com tarefas.</span><span class="sxs-lookup"><span data-stu-id="81062-136">You can also build an asynchronous semaphore that does not rely on wait handles and instead works completely with tasks.</span></span> <span data-ttu-id="81062-137">Para fazer isso, você pode usar técnicas como discutido [consumindo o padrão assíncrono baseado em tarefa](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md) para a criação de estruturas de dados na parte superior do <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="81062-137">To do this, you can use techniques such as those discussed in [Consuming the Task-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md) for building data structures on top of <xref:System.Threading.Tasks.Task>.</span></span>  
  
<a name="TapToWH"></a>   
### <a name="from-tap-to-wait-handles"></a><span data-ttu-id="81062-138">De toque para identificadores de espera</span><span class="sxs-lookup"><span data-stu-id="81062-138">From TAP to Wait Handles</span></span>  
 <span data-ttu-id="81062-139">Como mencionado anteriormente, o <xref:System.Threading.Tasks.Task> classe implementa <xref:System.IAsyncResult>, e que a implementação expõe um <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> propriedade que retorna um identificador de espera será definido quando o <xref:System.Threading.Tasks.Task> é concluída.</span><span class="sxs-lookup"><span data-stu-id="81062-139">As previously mentioned, the <xref:System.Threading.Tasks.Task> class implements <xref:System.IAsyncResult>, and that implementation exposes an <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> property that returns a wait handle that will be set when the <xref:System.Threading.Tasks.Task> completes.</span></span>  <span data-ttu-id="81062-140">Você pode obter um <xref:System.Threading.WaitHandle> para um <xref:System.Threading.Tasks.Task> da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="81062-140">You can get a <xref:System.Threading.WaitHandle> for a <xref:System.Threading.Tasks.Task> as follows:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#14)]
 [!code-vb[Conceptual.AsyncInterop#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="81062-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="81062-141">See Also</span></span>  
 [<span data-ttu-id="81062-142">TAP (Padrão Assíncrono Baseado em Tarefa)</span><span class="sxs-lookup"><span data-stu-id="81062-142">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 [<span data-ttu-id="81062-143">Implementando o padrão assíncrono baseado em tarefa</span><span class="sxs-lookup"><span data-stu-id="81062-143">Implementing the Task-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)  
 [<span data-ttu-id="81062-144">Consumindo o padrão assíncrono baseado em tarefa</span><span class="sxs-lookup"><span data-stu-id="81062-144">Consuming the Task-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)
