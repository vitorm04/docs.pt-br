---
title: Interoperabilidade com outros tipos e padrões assíncronos
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous design patterns, .NET
- TAP, .NET support for
- Task-based Asynchronous Pattern, .NET support for
- .NET, asynchronous design patterns
ms.assetid: f120a5d9-933b-4d1d-acb6-f034a57c3749
ms.openlocfilehash: 5ad49c70aaa69d8a4f830851b80b6a4839388b0f
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888744"
---
# <a name="interop-with-other-asynchronous-patterns-and-types"></a><span data-ttu-id="96177-102">Interoperabilidade com outros tipos e padrões assíncronos</span><span class="sxs-lookup"><span data-stu-id="96177-102">Interop with Other Asynchronous Patterns and Types</span></span>

<span data-ttu-id="96177-103">Um breve histórico dos padrões assíncronos no .NET:</span><span class="sxs-lookup"><span data-stu-id="96177-103">A brief history of asynchronous patterns in .NET:</span></span>

- <span data-ttu-id="96177-104">.NET Framework 1,0 introduziu o <xref:System.IAsyncResult> padrão, também conhecido como o [modelo de programação assíncrona (APM)](asynchronous-programming-model-apm.md)ou o `Begin/End` padrão.</span><span class="sxs-lookup"><span data-stu-id="96177-104">.NET Framework 1.0 introduced the <xref:System.IAsyncResult> pattern, otherwise known as the [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md), or the `Begin/End` pattern.</span></span>
- <span data-ttu-id="96177-105">.NET Framework 2,0 adicionou o [padrão assíncrono baseado em evento (EAP)](event-based-asynchronous-pattern-eap.md).</span><span class="sxs-lookup"><span data-stu-id="96177-105">.NET Framework 2.0 added the [Event-based Asynchronous Pattern (EAP)](event-based-asynchronous-pattern-eap.md).</span></span>
- <span data-ttu-id="96177-106">O .NET Framework 4 introduziu o [padrão assíncrono baseado em tarefa (TAP)](task-based-asynchronous-pattern-tap.md), que substitui o APM e o EAP e fornece a capacidade de criar facilmente rotinas de migração a partir dos padrões anteriores.</span><span class="sxs-lookup"><span data-stu-id="96177-106">.NET Framework 4 introduced the [Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md), which supersedes both APM and EAP and provides the ability to easily build migration routines from the earlier patterns.</span></span>
  
## <a name="tasks-and-the-asynchronous-programming-model-apm"></a><span data-ttu-id="96177-107">Tarefas e APM (Modelo Assíncrono de Programação)</span><span class="sxs-lookup"><span data-stu-id="96177-107">Tasks and the Asynchronous Programming Model (APM)</span></span>

### <a name="from-apm-to-tap"></a><span data-ttu-id="96177-108">De APM para TAP</span><span class="sxs-lookup"><span data-stu-id="96177-108">From APM to TAP</span></span>  
 <span data-ttu-id="96177-109">Como o padrão do [modelo de programação assíncrona (APM)](asynchronous-programming-model-apm.md) é estruturado, é muito fácil criar um wrapper para expor uma implementação de APM como uma implementação de toque.</span><span class="sxs-lookup"><span data-stu-id="96177-109">Because the [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md) pattern is structured, it is quite easy to build a wrapper to expose an APM implementation as a TAP implementation.</span></span> <span data-ttu-id="96177-110">O .NET Framework 4 e versões posteriores incluem rotinas auxiliares na forma de <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> sobrecargas de método para fornecer essa tradução.</span><span class="sxs-lookup"><span data-stu-id="96177-110">.NET Framework 4 and later versions include helper routines in the form of <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> method overloads to provide this translation.</span></span>  
  
 <span data-ttu-id="96177-111">Considere a classe <xref:System.IO.Stream> e seus métodos <xref:System.IO.Stream.BeginRead%2A> e <xref:System.IO.Stream.EndRead%2A>, que representam a contrapartida do APM para o método síncrono <xref:System.IO.Stream.Read%2A>:</span><span class="sxs-lookup"><span data-stu-id="96177-111">Consider the <xref:System.IO.Stream> class and its <xref:System.IO.Stream.BeginRead%2A> and <xref:System.IO.Stream.EndRead%2A> methods, which represent the APM counterpart to the synchronous <xref:System.IO.Stream.Read%2A> method:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#1)]
 [!code-vb[Conceptual.AsyncInterop#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#1)]  
[!code-csharp[Conceptual.AsyncInterop#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#2)]
[!code-vb[Conceptual.AsyncInterop#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#2)]  
[!code-csharp[Conceptual.AsyncInterop#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#3)]
[!code-vb[Conceptual.AsyncInterop#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#3)]  
  
 <span data-ttu-id="96177-112">Você pode usar o método <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> para implementar um wrapper do TAP para essa operação da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="96177-112">You can use the <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> method to implement a TAP wrapper for this operation as follows:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap1.cs#4)]
 [!code-vb[Conceptual.AsyncInterop#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap1.vb#4)]  
  
 <span data-ttu-id="96177-113">Essa implementação é semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="96177-113">This implementation is similar to the following:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap2.cs#5)]
 [!code-vb[Conceptual.AsyncInterop#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap2.vb#5)]  
  
### <a name="from-tap-to-apm"></a><span data-ttu-id="96177-114">De TAP para APM</span><span class="sxs-lookup"><span data-stu-id="96177-114">From TAP to APM</span></span>  
 <span data-ttu-id="96177-115">Se a infraestrutura existente esperar o padrão APM, convém também pegar uma implementação do TAP e usá-la onde uma implementação do APM é esperada.</span><span class="sxs-lookup"><span data-stu-id="96177-115">If your existing infrastructure expects the APM pattern, you'll also want to take a TAP implementation and use it where an APM implementation is expected.</span></span>  <span data-ttu-id="96177-116">Como as tarefas podem ser compostas e a classe <xref:System.Threading.Tasks.Task> implementa o <xref:System.IAsyncResult>, você pode usar uma função auxiliar simples para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="96177-116">Because tasks can be composed and  the <xref:System.Threading.Tasks.Task> class implements <xref:System.IAsyncResult>, you can use a straightforward helper function to do this.</span></span> <span data-ttu-id="96177-117">O código a seguir usa uma extensão da classe <xref:System.Threading.Tasks.Task%601>, mas você pode usar uma função quase idêntica para tarefas não genéricas.</span><span class="sxs-lookup"><span data-stu-id="96177-117">The following code uses an extension of the <xref:System.Threading.Tasks.Task%601> class, but you can use an almost identical function for non-generic tasks.</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM1.cs#6)]
 [!code-vb[Conceptual.AsyncInterop#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM1.vb#6)]  
  
 <span data-ttu-id="96177-118">Agora, considere um caso onde você tem a seguinte implementação do TAP:</span><span class="sxs-lookup"><span data-stu-id="96177-118">Now, consider a case where you have the following TAP implementation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#7)]
 [!code-vb[Conceptual.AsyncInterop#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#7)]  
  
 <span data-ttu-id="96177-119">e você deseja oferecer essa implementação do APM:</span><span class="sxs-lookup"><span data-stu-id="96177-119">and you want to provide this APM implementation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#8)]
 [!code-vb[Conceptual.AsyncInterop#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#8)]  
[!code-csharp[Conceptual.AsyncInterop#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#9)]
[!code-vb[Conceptual.AsyncInterop#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#9)]  
  
 <span data-ttu-id="96177-120">O exemplo a seguir demonstra uma migração para APM:</span><span class="sxs-lookup"><span data-stu-id="96177-120">The following example demonstrates one migration to APM:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#10)]
 [!code-vb[Conceptual.AsyncInterop#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#10)]  
  
## <a name="tasks-and-the-event-based-asynchronous-pattern-eap"></a><span data-ttu-id="96177-121">Tarefas e o EAP (Padrão assíncrono baseado em evento)</span><span class="sxs-lookup"><span data-stu-id="96177-121">Tasks and the Event-based Asynchronous Pattern (EAP)</span></span>  
 <span data-ttu-id="96177-122">Dispor uma implementação do [EAP (Padrão assíncrono baseado em evento)](event-based-asynchronous-pattern-eap.md) é mais envolvente do que dispor um padrão do APM porque o padrão EAP possui mais variações e menos estrutura do que o padrão APM.</span><span class="sxs-lookup"><span data-stu-id="96177-122">Wrapping an [Event-based Asynchronous Pattern (EAP)](event-based-asynchronous-pattern-eap.md) implementation is more involved than wrapping an APM pattern, because the EAP pattern has more variation and less structure than the APM pattern.</span></span>  <span data-ttu-id="96177-123">Para demonstrar, o código a seguir se dispõe ao redor do método `DownloadStringAsync`.</span><span class="sxs-lookup"><span data-stu-id="96177-123">To demonstrate, the following code wraps the `DownloadStringAsync` method.</span></span>  <span data-ttu-id="96177-124">`DownloadStringAsync` aceita um URI, gera o evento `DownloadProgressChanged` durante o download para oferecer várias estatísticas sobre o andamento e, quando tiver terminado, gera o evento `DownloadStringCompleted`.</span><span class="sxs-lookup"><span data-stu-id="96177-124">`DownloadStringAsync` accepts a URI, raises the `DownloadProgressChanged` event while downloading in order to report multiple statistics on progress, and raises the `DownloadStringCompleted` event when it's done.</span></span>  <span data-ttu-id="96177-125">O resultado final é uma cadeia de caracteres que contém o conteúdo da página no URI especificado.</span><span class="sxs-lookup"><span data-stu-id="96177-125">The final result is a string that contains the contents of the page at the specified URI.</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/EAP1.cs#11)]
 [!code-vb[Conceptual.AsyncInterop#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/EAP1.vb#11)]  
  
## <a name="tasks-and-wait-handles"></a><span data-ttu-id="96177-126">Tarefas e identificadores de espera</span><span class="sxs-lookup"><span data-stu-id="96177-126">Tasks and Wait Handles</span></span>  
  
### <a name="from-wait-handles-to-tap"></a><span data-ttu-id="96177-127">De Identificadores de espera para TAP</span><span class="sxs-lookup"><span data-stu-id="96177-127">From Wait Handles to TAP</span></span>  
 <span data-ttu-id="96177-128">Embora os identificadores de espera não implementem um padrão assíncrono, os desenvolvedores avançados podem usar a classe <xref:System.Threading.WaitHandle> e o método <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> em notificações assíncronas quando um identificador de espera estiver definido.</span><span class="sxs-lookup"><span data-stu-id="96177-128">Although wait handles don't implement an asynchronous pattern, advanced developers may use the <xref:System.Threading.WaitHandle> class and the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> method for asynchronous notifications when a wait handle is set.</span></span>  <span data-ttu-id="96177-129">Você pode dispor o método <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> para habilitar uma alternativa baseada em tarefa para qualquer espera síncrona em um identificador de espera:</span><span class="sxs-lookup"><span data-stu-id="96177-129">You can wrap the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> method to enable a task-based alternative to any synchronous wait on a wait handle:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#12)]
 [!code-vb[Conceptual.AsyncInterop#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#12)]  
  
 <span data-ttu-id="96177-130">Com esse método, você pode usar implementações <xref:System.Threading.WaitHandle> existentes em métodos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="96177-130">With this method, you can use existing <xref:System.Threading.WaitHandle> implementations in asynchronous methods.</span></span>  <span data-ttu-id="96177-131">Por exemplo, se quiser limitar o número de operações assíncronas que são executadas em um determinado momento, você pode utilizar um semáforo (um objeto <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="96177-131">For example, if you want to throttle the number of asynchronous operations that are executing at any particular time, you can utilize a semaphore (a <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> object).</span></span>  <span data-ttu-id="96177-132">Você pode limitar a *N* o número de operações que são executadas simultaneamente inicializando a contagem do semáforo como *N* , aguardando o semáforo sempre que você desejar executar uma operação e liberando o semáforo quando terminar com uma operação:</span><span class="sxs-lookup"><span data-stu-id="96177-132">You can throttle to *N* the number of operations that run concurrently by initializing the semaphore's count to *N* , waiting on the semaphore any time you want to perform an operation, and releasing the semaphore when you're done with an operation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Semaphore1.cs#13)]
 [!code-vb[Conceptual.AsyncInterop#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Semaphore1.vb#13)]  
  
 <span data-ttu-id="96177-133">Você também pode criar um semáforo assíncrono que não depende de identificadores de espera e só trabalha com tarefas.</span><span class="sxs-lookup"><span data-stu-id="96177-133">You can also build an asynchronous semaphore that does not rely on wait handles and instead works completely with tasks.</span></span> <span data-ttu-id="96177-134">Para fazer isso, você pode usar técnicas, como aquelas discutidas em [Consumir o Padrão assíncrono baseado em tarefa](consuming-the-task-based-asynchronous-pattern.md), para criar estruturas de dados em cima de <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="96177-134">To do this, you can use techniques such as those discussed in [Consuming the Task-based Asynchronous Pattern](consuming-the-task-based-asynchronous-pattern.md) for building data structures on top of <xref:System.Threading.Tasks.Task>.</span></span>  
  
### <a name="from-tap-to-wait-handles"></a><span data-ttu-id="96177-135">De TAP para Identificadores de espera</span><span class="sxs-lookup"><span data-stu-id="96177-135">From TAP to Wait Handles</span></span>  
 <span data-ttu-id="96177-136">Conforme mencionado anteriormente, a classe <xref:System.Threading.Tasks.Task> implementa o <xref:System.IAsyncResult> e essa implementação expõe uma propriedade <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> que retorna um identificador de espera que será definido quando <xref:System.Threading.Tasks.Task> for concluído.</span><span class="sxs-lookup"><span data-stu-id="96177-136">As previously mentioned, the <xref:System.Threading.Tasks.Task> class implements <xref:System.IAsyncResult>, and that implementation exposes an <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> property that returns a wait handle that will be set when the <xref:System.Threading.Tasks.Task> completes.</span></span>  <span data-ttu-id="96177-137">Você pode obter um <xref:System.Threading.WaitHandle> para um <xref:System.Threading.Tasks.Task> da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="96177-137">You can get a <xref:System.Threading.WaitHandle> for a <xref:System.Threading.Tasks.Task> as follows:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#14)]
 [!code-vb[Conceptual.AsyncInterop#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="96177-138">Veja também</span><span class="sxs-lookup"><span data-stu-id="96177-138">See also</span></span>

- [<span data-ttu-id="96177-139">Padrão assíncrono baseado em tarefa (TAP)</span><span class="sxs-lookup"><span data-stu-id="96177-139">Task-based Asynchronous Pattern (TAP)</span></span>](task-based-asynchronous-pattern-tap.md)
- [<span data-ttu-id="96177-140">Implementando o padrão assíncrono baseado em tarefa</span><span class="sxs-lookup"><span data-stu-id="96177-140">Implementing the Task-based Asynchronous Pattern</span></span>](implementing-the-task-based-asynchronous-pattern.md)
- [<span data-ttu-id="96177-141">Consumindo o padrão assíncrono baseado em tarefa</span><span class="sxs-lookup"><span data-stu-id="96177-141">Consuming the Task-based Asynchronous Pattern</span></span>](consuming-the-task-based-asynchronous-pattern.md)
