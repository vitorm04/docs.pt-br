---
title: Coleta de lixo e desempenho
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, troubleshooting
- garbage collection, performance
ms.assetid: c203467b-e95c-4ccf-b30b-953eb3463134
ms.openlocfilehash: 8d40091420c29c86f2ebb25f14c17ae4f7a1c44a
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974760"
---
# <a name="garbage-collection-and-performance"></a><span data-ttu-id="b6ac2-102">Coleta de lixo e desempenho</span><span class="sxs-lookup"><span data-stu-id="b6ac2-102">Garbage Collection and Performance</span></span>

<span data-ttu-id="b6ac2-103">Este tópico descreve problemas relacionados à coleta de lixo e ao uso de memória.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-103">This topic describes issues related to garbage collection and memory usage.</span></span> <span data-ttu-id="b6ac2-104">Ele aborda problemas relacionados a heap gerenciado e explica como minimizar o efeito da coleta de lixo em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-104">It addresses issues that pertain to the managed heap and explains how to minimize the effect of garbage collection on your applications.</span></span> <span data-ttu-id="b6ac2-105">Cada problema tem links para procedimentos que podem ser usados para investigar problemas.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-105">Each issue has links to procedures that you can use to investigate problems.</span></span>

## <a name="performance-analysis-tools"></a><span data-ttu-id="b6ac2-106">Ferramentas de análise de desempenho</span><span class="sxs-lookup"><span data-stu-id="b6ac2-106">Performance Analysis Tools</span></span>

<span data-ttu-id="b6ac2-107">As seções a seguir descrevem as ferramentas que estão disponíveis para investigar problemas de coleta de lixo e de uso de memória.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-107">The following sections describe the tools that are available for investigating memory usage and garbage collection issues.</span></span> <span data-ttu-id="b6ac2-108">Os [procedimentos](#performance-check-procedures) fornecidos mais adiante neste tópico se referem a essas ferramentas.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-108">The [procedures](#performance-check-procedures) provided later in this topic refer to these tools.</span></span>

### <a name="memory-performance-counters"></a><span data-ttu-id="b6ac2-109">Contadores de desempenho da memória</span><span class="sxs-lookup"><span data-stu-id="b6ac2-109">Memory Performance Counters</span></span>

<span data-ttu-id="b6ac2-110">Você pode usar os contadores de desempenho para coletar dados de desempenho.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-110">You can use performance counters to gather performance data.</span></span> <span data-ttu-id="b6ac2-111">Para obter instruções, consulte [Criação de perfil do runtime](../../../docs/framework/debug-trace-profile/runtime-profiling.md).</span><span class="sxs-lookup"><span data-stu-id="b6ac2-111">For instructions, see [Runtime Profiling](../../../docs/framework/debug-trace-profile/runtime-profiling.md).</span></span> <span data-ttu-id="b6ac2-112">A categoria de contadores de desempenho de memória CLR do .NET, conforme descrito em [Contadores de desempenho no .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md), fornece informações sobre o coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-112">The .NET CLR Memory category of performance counters, as described in [Performance Counters in the .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md), provides information about the garbage collector.</span></span>

### <a name="debugging-with-sos"></a><span data-ttu-id="b6ac2-113">Depuração com SOS</span><span class="sxs-lookup"><span data-stu-id="b6ac2-113">Debugging with SOS</span></span>

<span data-ttu-id="b6ac2-114">Você pode usar o [Depurador do Windows (WinDbg)](/windows-hardware/drivers/debugger/index) para inspecionar objetos no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-114">You can use the [Windows Debugger (WinDbg)](/windows-hardware/drivers/debugger/index) to inspect objects on the managed heap.</span></span>

<span data-ttu-id="b6ac2-115">Para instalar o WinDbg, instale as Ferramentas de Depuração para Windows da página [Download Debugging Tools for Windows](/windows-hardware/drivers/debugger/debugger-download-tools) (Baixar Ferramentas de Depuração para Windows).</span><span class="sxs-lookup"><span data-stu-id="b6ac2-115">To install WinDbg, install Debugging Tools for Windows from the [Download Debugging Tools for Windows](/windows-hardware/drivers/debugger/debugger-download-tools) page.</span></span>

### <a name="garbage-collection-etw-events"></a><span data-ttu-id="b6ac2-116">Eventos ETW de coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="b6ac2-116">Garbage Collection ETW Events</span></span>

<span data-ttu-id="b6ac2-117">O ETW (Rastreamento de Eventos para Windows) é um sistema de rastreamento que complementa o suporte à criação de perfil e à depuração fornecido pelo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-117">Event tracing for Windows (ETW) is a tracing system that supplements the profiling and debugging support provided by the .NET Framework.</span></span> <span data-ttu-id="b6ac2-118">A partir do .NET Framework 4, os [eventos ETW de coleta de lixo](../../../docs/framework/performance/garbage-collection-etw-events.md) capturam informações úteis para analisar o heap gerenciado do ponto de vista estatístico.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-118">Starting with the .NET Framework 4, [garbage collection ETW events](../../../docs/framework/performance/garbage-collection-etw-events.md) capture useful information for analyzing the managed heap from a statistical point of view.</span></span> <span data-ttu-id="b6ac2-119">Por exemplo, o `GCStart_V1` evento, que é acionado quando uma coleta de lixo está prestes a ocorrer, fornece as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="b6ac2-119">For example, the `GCStart_V1` event, which is raised when a garbage collection is about to occur, provides the following information:</span></span>

- <span data-ttu-id="b6ac2-120">Qual geração de objetos está sendo coletada.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-120">Which generation of objects is being collected.</span></span>

- <span data-ttu-id="b6ac2-121">O que disparou a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-121">What triggered the garbage collection.</span></span>

- <span data-ttu-id="b6ac2-122">Tipo de coleta de lixo (simultânea ou não simultânea).</span><span class="sxs-lookup"><span data-stu-id="b6ac2-122">Type of garbage collection (concurrent or not concurrent).</span></span>

<span data-ttu-id="b6ac2-123">O log de eventos ETW é eficiente e não mascarará nenhum problema de desempenho associado à coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-123">ETW event logging is efficient and will not mask any performance problems associated with garbage collection.</span></span> <span data-ttu-id="b6ac2-124">Um processo pode fornecer seus próprios eventos junto com eventos ETW.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-124">A process can provide its own events in conjunction with ETW events.</span></span> <span data-ttu-id="b6ac2-125">Quando registrados em log, tanto os eventos de coleta de lixo quanto os eventos do aplicativo podem ser correlacionados para determinar como e quando os problemas de heap ocorrem.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-125">When logged, both the application's events and the garbage collection events can be correlated to determine how and when heap problems occur.</span></span> <span data-ttu-id="b6ac2-126">Por exemplo, um aplicativo para servidores pode fornecer eventos no início e no final de uma solicitação de cliente.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-126">For example, a server application could provide events at the start and end of a client request.</span></span>

### <a name="the-profiling-api"></a><span data-ttu-id="b6ac2-127">A API de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="b6ac2-127">The Profiling API</span></span>

<span data-ttu-id="b6ac2-128">As interfaces de criação de perfil do CLR (Common Language Runtime) fornecem informações detalhadas sobre os objetos que foram afetados durante a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-128">The common language runtime (CLR) profiling interfaces provide detailed information about the objects that were affected during garbage collection.</span></span> <span data-ttu-id="b6ac2-129">Um criador de perfil pode ser notificado sobre quando uma coleta de lixo começa e termina.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-129">A profiler can be notified when a garbage collection starts and ends.</span></span> <span data-ttu-id="b6ac2-130">Ele pode fornecer relatórios sobre os objetos no heap gerenciado, incluindo uma identificação de objetos em cada geração.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-130">It can provide reports about the objects on the managed heap, including an identification of objects in each generation.</span></span> <span data-ttu-id="b6ac2-131">Para obter mais informações, consulte [Visão geral de ferramentas de criação de perfil](../../../docs/framework/unmanaged-api/profiling/profiling-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b6ac2-131">For more information, see [Profiling Overview](../../../docs/framework/unmanaged-api/profiling/profiling-overview.md).</span></span>

<span data-ttu-id="b6ac2-132">Criadores de perfil podem fornecer informações abrangentes.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-132">Profilers can provide comprehensive information.</span></span> <span data-ttu-id="b6ac2-133">No entanto, criadores de perfil complexos têm o potencial de modificar o comportamento de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-133">However, complex profilers can potentially modify an application's behavior.</span></span>

### <a name="application-domain-resource-monitoring"></a><span data-ttu-id="b6ac2-134">Monitoramento de recursos de domínio de aplicativo</span><span class="sxs-lookup"><span data-stu-id="b6ac2-134">Application Domain Resource Monitoring</span></span>

<span data-ttu-id="b6ac2-135">Do .NET Framework 4 em diante, o ARM (monitoramento de recursos de domínio de aplicativo) permite que os hosts monitorem o uso de CPU e memória por domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-135">Starting with the .NET Framework 4, Application domain resource monitoring (ARM) enables hosts to monitor CPU and memory usage by application domain.</span></span> <span data-ttu-id="b6ac2-136">Para obter mais informações, consulte [Monitoramento de recursos de domínio do aplicativo](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md).</span><span class="sxs-lookup"><span data-stu-id="b6ac2-136">For more information, see [Application Domain Resource Monitoring](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md).</span></span>

## <a name="troubleshooting-performance-issues"></a><span data-ttu-id="b6ac2-137">Solucionando problemas de desempenho</span><span class="sxs-lookup"><span data-stu-id="b6ac2-137">Troubleshooting Performance Issues</span></span>

<span data-ttu-id="b6ac2-138">A primeira etapa é [determinar se o problema é realmente a coleta de lixo](#IsGC).</span><span class="sxs-lookup"><span data-stu-id="b6ac2-138">The first step is to [determine whether the issue is actually garbage collection](#IsGC).</span></span> <span data-ttu-id="b6ac2-139">Se você determinar que é, selecione um item da lista a seguir para solucionar o problema.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-139">If you determine that it is, select from the following list to troubleshoot the problem.</span></span>

- [<span data-ttu-id="b6ac2-140">Uma exceção de falta de memória é lançada</span><span class="sxs-lookup"><span data-stu-id="b6ac2-140">An out-of-memory exception is thrown</span></span>](#Issue_OOM)

- [<span data-ttu-id="b6ac2-141">O processo usa memória demais</span><span class="sxs-lookup"><span data-stu-id="b6ac2-141">The process uses too much memory</span></span>](#Issue_TooMuchMemory)

- [<span data-ttu-id="b6ac2-142">O coletor de lixo não recupera objetos com rapidez suficiente</span><span class="sxs-lookup"><span data-stu-id="b6ac2-142">The garbage collector does not reclaim objects fast enough</span></span>](#Issue_NotFastEnough)

- [<span data-ttu-id="b6ac2-143">O heap gerenciado está fragmentado demais</span><span class="sxs-lookup"><span data-stu-id="b6ac2-143">The managed heap is too fragmented</span></span>](#Issue_Fragmentation)

- [<span data-ttu-id="b6ac2-144">As pausas na coleta de lixo são longas demais</span><span class="sxs-lookup"><span data-stu-id="b6ac2-144">Garbage collection pauses are too long</span></span>](#Issue_LongPauses)

- [<span data-ttu-id="b6ac2-145">A geração 0 é grande demais</span><span class="sxs-lookup"><span data-stu-id="b6ac2-145">Generation 0 is too big</span></span>](#Issue_Gen0)

- [<span data-ttu-id="b6ac2-146">O uso da CPU durante uma coleta de lixo é alto demais</span><span class="sxs-lookup"><span data-stu-id="b6ac2-146">CPU usage during a garbage collection is too high</span></span>](#Issue_HighCPU)

<a name="Issue_OOM"></a>

### <a name="issue-an-out-of-memory-exception-is-thrown"></a><span data-ttu-id="b6ac2-147">Problema: uma exceção de falta de memória é lançada</span><span class="sxs-lookup"><span data-stu-id="b6ac2-147">Issue: An Out-of-Memory Exception Is Thrown</span></span>

<span data-ttu-id="b6ac2-148">Há dois casos legítimos para um <xref:System.OutOfMemoryException> gerenciado ser lançado:</span><span class="sxs-lookup"><span data-stu-id="b6ac2-148">There are two legitimate cases for a managed <xref:System.OutOfMemoryException> to be thrown:</span></span>

- <span data-ttu-id="b6ac2-149">Falta de memória virtual.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-149">Running out of virtual memory.</span></span>

  <span data-ttu-id="b6ac2-150">O coletor de lixo aloca memória do sistema em segmentos com tamanho predeterminado.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-150">The garbage collector allocates memory from the system in segments of a pre-determined size.</span></span> <span data-ttu-id="b6ac2-151">Se uma alocação requer um segmento adicional mas não há nenhum bloco contíguo livre restante no espaço de memória virtual do processo, a alocação de heap gerenciado falha.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-151">If an allocation requires an additional segment, but there is no contiguous free block left in the process's virtual memory space, the allocation for the managed heap will fail.</span></span>

- <span data-ttu-id="b6ac2-152">Não há memória física suficiente para alocar.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-152">Not having enough physical memory to allocate.</span></span>

|<span data-ttu-id="b6ac2-153">Verificações de desempenho</span><span class="sxs-lookup"><span data-stu-id="b6ac2-153">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="b6ac2-154">Determine se a exceção de falta de memória é gerenciada.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-154">Determine whether the out-of-memory exception is managed.</span></span>](#OOMIsManaged)<br /><br /> [<span data-ttu-id="b6ac2-155">Determine a quantidade de memória virtual que pode ser reservada.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-155">Determine how much virtual memory can be reserved.</span></span>](#GetVM)<br /><br /> [<span data-ttu-id="b6ac2-156">Determine se há memória física suficiente.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-156">Determine whether there is enough physical memory.</span></span>](#Physical)|

<span data-ttu-id="b6ac2-157">Se você determinar que a exceção não é legítima, entre em contato com o Serviço de Suporte e Atendimento ao Cliente Microsoft com as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="b6ac2-157">If you determine that the exception is not legitimate, contact Microsoft Customer Service and Support with the following information:</span></span>

- <span data-ttu-id="b6ac2-158">A pilha com a exceção de falta de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-158">The stack with the managed out-of-memory exception.</span></span>

- <span data-ttu-id="b6ac2-159">O despejo de memória completo.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-159">Full memory dump.</span></span>

- <span data-ttu-id="b6ac2-160">Dados que provam que não é uma exceção de memória insuficiente legítima, incluindo dados mostrando que a memória física ou virtual não são um problema.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-160">Data that proves that it is not a legitimate out-of-memory exception, including data that shows that virtual or physical memory is not an issue.</span></span>

<a name="Issue_TooMuchMemory"></a>

### <a name="issue-the-process-uses-too-much-memory"></a><span data-ttu-id="b6ac2-161">Problema: O processo usa memória demais</span><span class="sxs-lookup"><span data-stu-id="b6ac2-161">Issue: The Process Uses Too Much Memory</span></span>

<span data-ttu-id="b6ac2-162">Um pressuposto comum é que o uso de memória a exibir na guia **Desempenho** do Gerenciador de Tarefas do Windows pode indicar quando memória demais está sendo usada.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-162">A common assumption is that the memory usage display on the **Performance** tab of Windows Task Manager can indicate when too much memory is being used.</span></span> <span data-ttu-id="b6ac2-163">No entanto, essa exibição pertence ao conjunto de trabalho; ela não fornece informações sobre o uso de memória virtual.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-163">However, that display pertains to the working set; it does not provide information about virtual memory usage.</span></span>

<span data-ttu-id="b6ac2-164">Se você determinar que o problema é causado pelo heap gerenciado, meça o heap gerenciado ao longo do tempo para determinar eventuais padrões.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-164">If you determine that the issue is caused by the managed heap, you must measure the managed heap over time to determine any patterns.</span></span>

<span data-ttu-id="b6ac2-165">Se você determinar que o problema não é causado pelo heap gerenciado, use a depuração nativa.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-165">If you determine that the problem is not caused by the managed heap, you must use native debugging.</span></span>

|<span data-ttu-id="b6ac2-166">Verificações de desempenho</span><span class="sxs-lookup"><span data-stu-id="b6ac2-166">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="b6ac2-167">Determine a quantidade de memória virtual que pode ser reservada.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-167">Determine how much virtual memory can be reserved.</span></span>](#GetVM)<br /><br /> [<span data-ttu-id="b6ac2-168">Determine a quantidade de memória que o heap gerenciado está confirmando.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-168">Determine how much memory the managed heap is committing.</span></span>](#ManagedHeapCommit)<br /><br /> [<span data-ttu-id="b6ac2-169">Determine a quantidade de memória que o heap gerenciado reserva.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-169">Determine how much memory the managed heap reserves.</span></span>](#ManagedHeapReserve)<br /><br /> [<span data-ttu-id="b6ac2-170">Determine objetos grandes na geração 2.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-170">Determine large objects in generation 2.</span></span>](#ExamineGen2)<br /><br /> [<span data-ttu-id="b6ac2-171">Determine referências para os objetos.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-171">Determine references to objects.</span></span>](#ObjRef)|

<a name="Issue_NotFastEnough"></a>

### <a name="issue-the-garbage-collector-does-not-reclaim-objects-fast-enough"></a><span data-ttu-id="b6ac2-172">Problema: o coletor de lixo não recupera objetos com rapidez suficiente</span><span class="sxs-lookup"><span data-stu-id="b6ac2-172">Issue: The Garbage Collector Does Not Reclaim Objects Fast Enough</span></span>

<span data-ttu-id="b6ac2-173">Quando ele é exibido como se objetos não estivessem sendo recuperados conforme o esperado para coleta de lixo, determine se há quaisquer referências fortes a esses objetos.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-173">When it appears as if objects are not being reclaimed as expected for garbage collection, you must determine if there are any strong references to those objects.</span></span>

<span data-ttu-id="b6ac2-174">Você também poderá encontrar esse problema caso não tenha havido nenhuma coleta de lixo para a geração que contém um objeto inativo, o que indicará que o finalizador do objeto inativo não foi executado.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-174">You may also encounter this issue if there has been no garbage collection for the generation that contains a dead object, which indicates that the finalizer for the dead object has not been run.</span></span> <span data-ttu-id="b6ac2-175">Por exemplo, isso é possível quando você está executando um aplicativo STA (single-threaded apartment) e o thread que cuida da fila de finalizadores não é capaz de chamá-la.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-175">For example, this is possible when you are running a single-threaded apartment (STA) application and the thread that services the finalizer queue cannot call into it.</span></span>

|<span data-ttu-id="b6ac2-176">Verificações de desempenho</span><span class="sxs-lookup"><span data-stu-id="b6ac2-176">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="b6ac2-177">Verifique as referências para os objetos.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-177">Check references to objects.</span></span>](#ObjRef)<br /><br /> [<span data-ttu-id="b6ac2-178">Determine se um finalizador foi executado.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-178">Determine whether a finalizer has been run.</span></span>](#Induce)<br /><br /> [<span data-ttu-id="b6ac2-179">Determine se há objetos aguardando finalização.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-179">Determine whether there are objects waiting to be finalized.</span></span>](#Finalize)|

<a name="Issue_Fragmentation"></a>

### <a name="issue-the-managed-heap-is-too-fragmented"></a><span data-ttu-id="b6ac2-180">Problema: o heap gerenciado está fragmentado demais</span><span class="sxs-lookup"><span data-stu-id="b6ac2-180">Issue: The Managed Heap Is Too fragmented</span></span>

<span data-ttu-id="b6ac2-181">O nível de fragmentação é calculado como a proporção entre o espaço livre e o total de memória alocada para a geração.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-181">The fragmentation level is calculated as the ratio of free space over the total allocated memory for the generation.</span></span> <span data-ttu-id="b6ac2-182">Para a geração 2, um nível aceitável de fragmentação é de não mais que 20%.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-182">For generation 2, an acceptable level of fragmentation is no more than 20%.</span></span> <span data-ttu-id="b6ac2-183">Já que a geração 2 pode ficar muito grande, a taxa de fragmentação é mais importante do que o valor absoluto.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-183">Because generation 2 can get very big, the ratio of fragmentation is more important than the absolute value.</span></span>

<span data-ttu-id="b6ac2-184">Ter muito espaço livre na geração 0 não é um problema, pois esta é a geração em que novos objetos são alocados.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-184">Having lots of free space in generation 0 is not a problem because this is the generation where new objects are allocated.</span></span>

<span data-ttu-id="b6ac2-185">No heap de objetos grandes sempre ocorre fragmentação, porque ele não é compactado.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-185">Fragmentation always occurs in the large object heap because it is not compacted.</span></span> <span data-ttu-id="b6ac2-186">Objetos livres adjacentes são naturalmente recolhidos em um único espaço para atender a solicitações de alocação de objetos grandes.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-186">Free objects that are adjacent are naturally collapsed into a single space to satisfy large object allocation requests.</span></span>

<span data-ttu-id="b6ac2-187">A fragmentação pode se tornar um problema na geração 1 e geração 2.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-187">Fragmentation can become a problem in generation 1 and generation 2.</span></span> <span data-ttu-id="b6ac2-188">Se esses gerações tiverem uma grande quantidade de espaço livre após uma coleta de lixo, o uso de objetos de um aplicativo poderá precisar de modificações e você deverá considerar reavaliar o tempo de vida dos objetos de longo prazo.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-188">If these generations have a large amount of free space after a garbage collection, an application's object usage may need modification, and you should consider re-evaluating the lifetime of long-term objects.</span></span>

<span data-ttu-id="b6ac2-189">O excesso de fixação de objetos pode aumentar a fragmentação.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-189">Excessive pinning of objects can increase fragmentation.</span></span> <span data-ttu-id="b6ac2-190">Se a fragmentação for alta, poderá ocorrer fixação de objetos demais.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-190">If fragmentation is high, too many objects could be pinned.</span></span>

<span data-ttu-id="b6ac2-191">Se a fragmentação da memória virtual estiver impedindo que o coletor de lixo adicione segmentos, as causas poderão ser uma dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="b6ac2-191">If fragmentation of virtual memory is preventing the garbage collector from adding segments, the causes could be one of the following:</span></span>

- <span data-ttu-id="b6ac2-192">Carregamento e descarregamento frequente de muitos assemblies pequenos.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-192">Frequent loading and unloading of many small assemblies.</span></span>

- <span data-ttu-id="b6ac2-193">Retenção de um número excessivo de referências a objetos COM ao interoperar com código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-193">Holding too many references to COM objects when interoperating with unmanaged code.</span></span>

- <span data-ttu-id="b6ac2-194">Criação de objetos transitórios grandes, que faz com que o heap de objeto grande aloque e libere segmentos de heap frequentemente.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-194">Creation of large transient objects, which causes the large object heap to allocate and free heap segments frequently.</span></span>

  <span data-ttu-id="b6ac2-195">Ao hospedar o CLR, um aplicativo pode solicitar que o coletor de lixo retenha seus segmentos.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-195">When hosting the CLR, an application can request that the garbage collector retain its segments.</span></span> <span data-ttu-id="b6ac2-196">Isso reduz a frequência de alocações de segmento.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-196">This reduces the frequency of segment allocations.</span></span> <span data-ttu-id="b6ac2-197">Isso é feito usando o sinalizador STARTUP_HOARD_GC_VM na [Enumeração STARTUP_FLAGS](../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="b6ac2-197">This is accomplished by using the STARTUP_HOARD_GC_VM flag in the [STARTUP_FLAGS Enumeration](../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span></span>

|<span data-ttu-id="b6ac2-198">Verificações de desempenho</span><span class="sxs-lookup"><span data-stu-id="b6ac2-198">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="b6ac2-199">Determine a quantidade de espaço livre no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-199">Determine the amount of free space in the managed heap.</span></span>](#Fragmented)<br /><br /> [<span data-ttu-id="b6ac2-200">Determine o número de objetos fixados.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-200">Determine the number of pinned objects.</span></span>](#Pinned)|

<span data-ttu-id="b6ac2-201">Se você acha que não há nenhuma causa legítima para a fragmentação, entre em contato com o Serviço de Suporte e Atendimento ao Cliente Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-201">If you think that there is no legitimate cause for the fragmentation, contact Microsoft Customer Service and Support.</span></span>

<a name="Issue_LongPauses"></a>

### <a name="issue-garbage-collection-pauses-are-too-long"></a><span data-ttu-id="b6ac2-202">Problema: as pausas na coleta de lixo são longas demais</span><span class="sxs-lookup"><span data-stu-id="b6ac2-202">Issue: Garbage Collection Pauses Are Too Long</span></span>

<span data-ttu-id="b6ac2-203">A coleta de lixo opera em tempo real flexível, de modo que um aplicativo deve ser capaz de tolerar algumas pausas.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-203">Garbage collection operates in soft real time, so an application must be able to tolerate some pauses.</span></span> <span data-ttu-id="b6ac2-204">Um critério para o tempo real flexível é que 95% das operações deve terminar no prazo.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-204">A criterion for soft real time is that 95% of the operations must finish on time.</span></span>

<span data-ttu-id="b6ac2-205">Na coleta de lixo simultânea, a execução de threads gerenciados é permitida durante uma coleta, o que significa que as pausas são realmente mínimas.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-205">In concurrent garbage collection, managed threads are allowed to run during a collection, which means that pauses are very minimal.</span></span>

<span data-ttu-id="b6ac2-206">Coletas de lixo efêmero (gerações 0 e 1) duram somente alguns milissegundos, então diminuir as pausas geralmente não é viável.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-206">Ephemeral garbage collections (generations 0 and 1) last only a few milliseconds, so decreasing pauses is usually not feasible.</span></span> <span data-ttu-id="b6ac2-207">No entanto, você pode diminuir as pausas em coletas da geração 2 alterando o padrão de solicitações de alocação por um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-207">However, you can decrease the pauses in generation 2 collections by changing the pattern of allocation requests by an application.</span></span>

<span data-ttu-id="b6ac2-208">Outro método mais preciso é usar [eventos ETW de coleta de lixo](../../../docs/framework/performance/garbage-collection-etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="b6ac2-208">Another, more accurate, method is to use [garbage collection ETW events](../../../docs/framework/performance/garbage-collection-etw-events.md).</span></span> <span data-ttu-id="b6ac2-209">Você pode encontrar os intervalos para coletas adicionando as diferenças de carimbo de data/hora a uma sequência de eventos.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-209">You can find the timings for collections by adding the time stamp differences for a sequence of events.</span></span> <span data-ttu-id="b6ac2-210">A sequência de coleta inteira inclui a suspensão do mecanismo de execução, a própria coleta de lixo e a retomada do mecanismo de execução.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-210">The whole collection sequence includes suspension of the execution engine, the garbage collection itself, and the resumption of the execution engine.</span></span>

<span data-ttu-id="b6ac2-211">Você pode usar [notificações de coleta de lixo](../../../docs/standard/garbage-collection/notifications.md) para determinar se um servidor está prestes a ter uma coleta de geração 2 e se o redirecionamento solicitações para outro servidor pode reduzir os problemas com pausas.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-211">You can use [Garbage Collection Notifications](../../../docs/standard/garbage-collection/notifications.md) to determine whether a server is about to have a generation 2 collection, and whether rerouting requests to another server could ease any problems with pauses.</span></span>

|<span data-ttu-id="b6ac2-212">Verificações de desempenho</span><span class="sxs-lookup"><span data-stu-id="b6ac2-212">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="b6ac2-213">Determine a duração de uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-213">Determine the length of time in a garbage collection.</span></span>](#TimeInGC)<br /><br /> [<span data-ttu-id="b6ac2-214">Determine o que causou uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-214">Determine what caused a garbage collection.</span></span>](#Triggered)|

<a name="Issue_Gen0"></a>

### <a name="issue-generation-0-is-too-big"></a><span data-ttu-id="b6ac2-215">Problema: a geração 0 é grande demais</span><span class="sxs-lookup"><span data-stu-id="b6ac2-215">Issue: Generation 0 Is Too Big</span></span>

<span data-ttu-id="b6ac2-216">É provável que a geração 0 tenha um número maior de objetos em um sistema de 64 bits, especialmente quando você usa a coleta de lixo do servidor em vez de uma coleta de lixo de estação de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-216">Generation 0 is likely to have a larger number of objects on a 64-bit system, especially when you use server garbage collection instead of workstation garbage collection.</span></span> <span data-ttu-id="b6ac2-217">Isso ocorre porque o limite para disparar uma coleta de lixo de geração 0 é maior nesses ambientes e as coletas da geração 0 podem ficar muito maiores.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-217">This is because the threshold to trigger a generation 0 garbage collection is higher in these environments, and generation 0 collections can get much bigger.</span></span> <span data-ttu-id="b6ac2-218">O desempenho é aprimorado quando um aplicativo aloca mais memória antes de uma coleta de lixo ser disparada.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-218">Performance is improved when an application allocates more memory before a garbage collection is triggered.</span></span>

<a name="Issue_HighCPU"></a>

### <a name="issue-cpu-usage-during-a-garbage-collection-is-too-high"></a><span data-ttu-id="b6ac2-219">Problema: o uso da CPU durante uma coleta de lixo é alto demais</span><span class="sxs-lookup"><span data-stu-id="b6ac2-219">Issue: CPU Usage During a Garbage Collection Is Too High</span></span>

<span data-ttu-id="b6ac2-220">O uso da CPU será alto durante uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-220">CPU usage will be high during a garbage collection.</span></span> <span data-ttu-id="b6ac2-221">Se uma quantidade significativa de tempo de processamento é gasto em uma coleta de lixo, isso indica que o número de coletas é frequente demais ou que a coleta é longa demais.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-221">If a significant amount of process time is spent in a garbage collection, the number of collections is too frequent or the collection is lasting too long.</span></span> <span data-ttu-id="b6ac2-222">Uma maior taxa de alocação de objetos no heap gerenciado faz com que a coleta de lixo ocorra com mais frequência.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-222">An increased allocation rate of objects on the managed heap causes garbage collection to occur more frequently.</span></span> <span data-ttu-id="b6ac2-223">Diminuir a taxa de alocação reduz a frequência de coletas de lixo.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-223">Decreasing the allocation rate reduces the frequency of garbage collections.</span></span>

<span data-ttu-id="b6ac2-224">Você pode monitorar as taxas de alocação usando o contador de desempenho de `Allocated Bytes/second`.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-224">You can monitor allocation rates by using the `Allocated Bytes/second` performance counter.</span></span> <span data-ttu-id="b6ac2-225">Para obter mais informações, consulte [Contadores de desempenho no .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md).</span><span class="sxs-lookup"><span data-stu-id="b6ac2-225">For more information, see [Performance Counters in the .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md).</span></span>

<span data-ttu-id="b6ac2-226">A duração de uma coleta é essencialmente um fator do número de objetos que sobrevivem após a alocação.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-226">The duration of a collection is primarily a factor of the number of objects that survive after allocation.</span></span> <span data-ttu-id="b6ac2-227">O coletor de lixo deve passar por uma grande quantidade de memória se restam muitos objetos a serem coletados.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-227">The garbage collector must go through a large amount of memory if many objects remain to be collected.</span></span> <span data-ttu-id="b6ac2-228">O trabalho para compactar os sobreviventes é demorado.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-228">The work to compact the survivors is time-consuming.</span></span> <span data-ttu-id="b6ac2-229">Para determinar quantos objetos foram manipulados durante uma coleta, defina um ponto de interrupção no depurador no final de uma coleta de lixo para uma geração especificada.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-229">To determine how many objects were handled during a collection, set a breakpoint in the debugger at the end of a garbage collection for a specified generation.</span></span>

|<span data-ttu-id="b6ac2-230">Verificações de desempenho</span><span class="sxs-lookup"><span data-stu-id="b6ac2-230">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="b6ac2-231">Determine se o alto uso da CPU é causado pela coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-231">Determine if high CPU usage is caused by garbage collection.</span></span>](#HighCPU)<br /><br /> [<span data-ttu-id="b6ac2-232">Defina um ponto de interrupção no final da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-232">Set a breakpoint at the end of garbage collection.</span></span>](#GenBreak)|

## <a name="troubleshooting-guidelines"></a><span data-ttu-id="b6ac2-233">Diretrizes de solução de problemas</span><span class="sxs-lookup"><span data-stu-id="b6ac2-233">Troubleshooting Guidelines</span></span>

<span data-ttu-id="b6ac2-234">Esta seção descreve as diretrizes que você deve considerar ao começar suas investigações.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-234">This section describes guidelines that you should consider as you begin your investigations.</span></span>

### <a name="workstation-or-server-garbage-collection"></a><span data-ttu-id="b6ac2-235">Estação de trabalho ou coleta de lixo do servidor</span><span class="sxs-lookup"><span data-stu-id="b6ac2-235">Workstation or Server Garbage Collection</span></span>

<span data-ttu-id="b6ac2-236">Determine se você está usando o tipo correto de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-236">Determine if you are using the correct type of garbage collection.</span></span> <span data-ttu-id="b6ac2-237">Se seu aplicativo usa vários threads e instâncias de objeto, use a coleta de lixo do servidor em vez da coleta de lixo da estação de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-237">If your application uses multiple threads and object instances, use server garbage collection instead of workstation garbage collection.</span></span> <span data-ttu-id="b6ac2-238">A coleta de lixo do servidor funciona em vários threads, enquanto a coleta de lixo da estação de trabalho requer várias instâncias de um aplicativo para executar seus próprios threads de coleta de lixo e competir pelo tempo de CPU.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-238">Server garbage collection operates on multiple threads, whereas workstation garbage collection requires multiple instances of an application to run their own garbage collection threads and compete for CPU time.</span></span>

<span data-ttu-id="b6ac2-239">Um aplicativo que tem uma carga baixa e que realiza tarefas com pouca frequência em segundo plano, por exemplo, um serviço, poderia usar a coleta de lixo de estação de trabalho com a coleta de lixo simultânea desabilitada.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-239">An application that has a low load and that performs tasks infrequently in the background, such as a service, could use workstation garbage collection with concurrent garbage collection disabled.</span></span>

### <a name="when-to-measure-the-managed-heap-size"></a><span data-ttu-id="b6ac2-240">Quando medir o tamanho do heap gerenciado</span><span class="sxs-lookup"><span data-stu-id="b6ac2-240">When to Measure the Managed Heap Size</span></span>

<span data-ttu-id="b6ac2-241">A menos que você esteja usando um criador de perfil, você terá que estabelecer um padrão de medição consistente para diagnosticar problemas de desempenho de modo eficaz.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-241">Unless you are using a profiler, you will have to establish a consistent measuring pattern to effectively diagnose performance issues.</span></span> <span data-ttu-id="b6ac2-242">Considere os pontos a seguir ao estabelecer uma agenda:</span><span class="sxs-lookup"><span data-stu-id="b6ac2-242">Consider the following points to establish a schedule:</span></span>

- <span data-ttu-id="b6ac2-243">Se você medir após uma coleta de lixo da geração 2, todo o heap gerenciado estará livre de lixo (objetos inativos).</span><span class="sxs-lookup"><span data-stu-id="b6ac2-243">If you measure after a generation 2 garbage collection, the entire managed heap will be free of garbage (dead objects).</span></span>

- <span data-ttu-id="b6ac2-244">Se você medir imediatamente após uma coleta de lixo da geração 0, os objetos nas gerações 1 e 2 ainda não serão coletados.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-244">If you measure immediately after a generation 0 garbage collection, the objects in generations 1 and 2 will not be collected yet.</span></span>

- <span data-ttu-id="b6ac2-245">Se você medir imediatamente antes de uma coleta de lixo, você medirá o máximo de alocação possível antes do início da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-245">If you measure immediately before a garbage collection, you will measure as much allocation as possible before the garbage collection starts.</span></span>

- <span data-ttu-id="b6ac2-246">Medir durante uma coleta de lixo é problemático, pois as estruturas de dados do coletor de lixo não estão em um estado válido para passagem e podem não ser capazes de fornecer a você os resultados completos.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-246">Measuring during a garbage collection is problematic, because the garbage collector data structures are not in a valid state for traversal and may not be able to give you the complete results.</span></span> <span data-ttu-id="b6ac2-247">Esse comportamento é esperado.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-247">This is by design.</span></span>

- <span data-ttu-id="b6ac2-248">Quando você usa a coleta de lixo de estação de trabalho com coleta de lixo simultânea, os objetos recuperados não são compactados, portanto, o tamanho do heap pode ser igual ou maior (a fragmentação pode fazer com que pareça maior).</span><span class="sxs-lookup"><span data-stu-id="b6ac2-248">When you are using workstation garbage collection with concurrent garbage collection, the reclaimed objects are not compacted, so the heap size can be the same or larger (fragmentation can make it appear to be larger).</span></span>

- <span data-ttu-id="b6ac2-249">A coleta de lixo simultânea na geração 2 é atrasada quando a carga de memória física é alta demais.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-249">Concurrent garbage collection on generation 2 is delayed when the physical memory load is too high.</span></span>

<span data-ttu-id="b6ac2-250">O procedimento a seguir descreve como definir um ponto de interrupção para que você possa medir o heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-250">The following procedure describes how to set a breakpoint so that you can measure the managed heap.</span></span>

<a name="GenBreak"></a>

#### <a name="to-set-a-breakpoint-at-the-end-of-garbage-collection"></a><span data-ttu-id="b6ac2-251">Para definir um ponto de interrupção no final da coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="b6ac2-251">To set a breakpoint at the end of garbage collection</span></span>

- <span data-ttu-id="b6ac2-252">No WinDbg, com a extensão de depurador SOS carregada, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="b6ac2-252">In WinDbg with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="b6ac2-253">**bp mscorwks!WKS::GCHeap::RestartEE "j (dwo(mscorwks!WKS::GCHeap::GcCondemnedGeneration)==2) 'kb';'g'"**</span><span class="sxs-lookup"><span data-stu-id="b6ac2-253">**bp mscorwks!WKS::GCHeap::RestartEE "j (dwo(mscorwks!WKS::GCHeap::GcCondemnedGeneration)==2) 'kb';'g'"**</span></span>

  <span data-ttu-id="b6ac2-254">em que **GcCondemnedGeneration** é definido para a geração desejada.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-254">where **GcCondemnedGeneration** is set to the desired generation.</span></span> <span data-ttu-id="b6ac2-255">Esse comando requer símbolos privados.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-255">This command requires private symbols.</span></span>

  <span data-ttu-id="b6ac2-256">Esse comando força uma interrupção se **RestartEE** é executado após objetos da geração 2 serem recuperados para coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-256">This command forces a break if **RestartEE** is executed after generation 2 objects have been reclaimed for garbage collection.</span></span>

  <span data-ttu-id="b6ac2-257">Na coleta de lixo do servidor, apenas um thread chama **RestartEE**, portanto, o ponto de interrupção ocorrerá apenas uma vez durante uma coleta de lixo da geração 2.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-257">In server garbage collection, only one thread calls **RestartEE**, so the breakpoint will occur only once during a generation 2 garbage collection.</span></span>

## <a name="performance-check-procedures"></a><span data-ttu-id="b6ac2-258">Procedimentos de verificação de desempenho</span><span class="sxs-lookup"><span data-stu-id="b6ac2-258">Performance Check Procedures</span></span>

<span data-ttu-id="b6ac2-259">Esta seção descreve os procedimentos a seguir para isolar a causa do problema de desempenho:</span><span class="sxs-lookup"><span data-stu-id="b6ac2-259">This section describes the following procedures to isolate the cause of your performance issue:</span></span>

- [<span data-ttu-id="b6ac2-260">Determine se o problema é causado pela coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-260">Determine whether the problem is caused by garbage collection.</span></span>](#IsGC)

- [<span data-ttu-id="b6ac2-261">Determine se a exceção de falta de memória é gerenciada.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-261">Determine whether the out-of-memory exception is managed.</span></span>](#OOMIsManaged)

- [<span data-ttu-id="b6ac2-262">Determine a quantidade de memória virtual que pode ser reservada.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-262">Determine how much virtual memory can be reserved.</span></span>](#GetVM)

- [<span data-ttu-id="b6ac2-263">Determine se há memória física suficiente.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-263">Determine whether there is enough physical memory.</span></span>](#Physical)

- [<span data-ttu-id="b6ac2-264">Determine a quantidade de memória que o heap gerenciado está confirmando.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-264">Determine how much memory the managed heap is committing.</span></span>](#ManagedHeapCommit)

- [<span data-ttu-id="b6ac2-265">Determine a quantidade de memória que o heap gerenciado reserva.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-265">Determine how much memory the managed heap reserves.</span></span>](#ManagedHeapReserve)

- [<span data-ttu-id="b6ac2-266">Determine objetos grandes na geração 2.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-266">Determine large objects in generation 2.</span></span>](#ExamineGen2)

- [<span data-ttu-id="b6ac2-267">Determine referências para os objetos.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-267">Determine references to objects.</span></span>](#ObjRef)

- [<span data-ttu-id="b6ac2-268">Determine se um finalizador foi executado.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-268">Determine whether a finalizer has been run.</span></span>](#Induce)

- [<span data-ttu-id="b6ac2-269">Determine se há objetos aguardando finalização.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-269">Determine whether there are objects waiting to be finalized.</span></span>](#Finalize)

- [<span data-ttu-id="b6ac2-270">Determine a quantidade de espaço livre no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-270">Determine the amount of free space in the managed heap.</span></span>](#Fragmented)

- [<span data-ttu-id="b6ac2-271">Determine o número de objetos fixados.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-271">Determine the number of pinned objects.</span></span>](#Pinned)

- [<span data-ttu-id="b6ac2-272">Determine a duração de uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-272">Determine the length of time in a garbage collection.</span></span>](#TimeInGC)

- [<span data-ttu-id="b6ac2-273">Determine o que disparou uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-273">Determine what triggered a garbage collection.</span></span>](#Triggered)

- [<span data-ttu-id="b6ac2-274">Determine se o alto uso da CPU é causado pela coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-274">Determine whether high CPU usage is caused by garbage collection.</span></span>](#HighCPU)

<a name="IsGC"></a>

### <a name="to-determine-whether-the-problem-is-caused-by-garbage-collection"></a><span data-ttu-id="b6ac2-275">Para determinar se o problema é causado pela coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="b6ac2-275">To determine whether the problem is caused by garbage collection</span></span>

- <span data-ttu-id="b6ac2-276">Examine os dois contadores de desempenho de memória a seguir:</span><span class="sxs-lookup"><span data-stu-id="b6ac2-276">Examine the following two memory performance counters:</span></span>

  - <span data-ttu-id="b6ac2-277">**% de Tempo Gasto em GC**.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-277">**% Time in GC**.</span></span> <span data-ttu-id="b6ac2-278">Exibe o percentual de tempo decorrido que foi gasto na execução de uma coleta de lixo após o último ciclo de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-278">Displays the percentage of elapsed time that was spent performing a garbage collection after the last garbage collection cycle.</span></span> <span data-ttu-id="b6ac2-279">Use este contador para determinar se o coletor de lixo está gastando tempo demais para disponibilizar espaço de heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-279">Use this counter to determine whether the garbage collector is spending too much time to make managed heap space available.</span></span> <span data-ttu-id="b6ac2-280">Se o tempo gasto na coleta de lixo for relativamente baixo, isso poderá indicar um problema de recurso fora do heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-280">If the time spent in garbage collection is relatively low, that could indicate a resource problem outside the managed heap.</span></span> <span data-ttu-id="b6ac2-281">Esse contador pode não ser preciso quando coleta de lixo simultânea ou em segundo plano está envolvida.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-281">This counter may not be accurate when concurrent or background garbage collection is involved.</span></span>

  - <span data-ttu-id="b6ac2-282">**N. Total de Bytes Confirmados**.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-282">**# Total committed Bytes**.</span></span> <span data-ttu-id="b6ac2-283">Exibe a quantidade de memória virtual confirmada atualmente pelo coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-283">Displays the amount of virtual memory currently committed by the garbage collector.</span></span> <span data-ttu-id="b6ac2-284">Use este contador para determinar se a memória consumida pelo coletor de lixo é uma parte excessiva da memória usada pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-284">Use this counter to determine whether the memory consumed by the garbage collector is an excessive portion of the memory that your application uses.</span></span>

  <span data-ttu-id="b6ac2-285">A maioria dos contadores de desempenho de memória é atualizada no final de cada coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-285">Most of the memory performance counters are updated at the end of each garbage collection.</span></span> <span data-ttu-id="b6ac2-286">Portanto, eles podem não refletir as condições atuais sobre as quais você deseja obter informações.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-286">Therefore, they may not reflect the current conditions that you want information about.</span></span>

<a name="OOMIsManaged"></a>

### <a name="to-determine-whether-the-out-of-memory-exception-is-managed"></a><span data-ttu-id="b6ac2-287">Para determinar se a exceção de falta de memória é gerenciada</span><span class="sxs-lookup"><span data-stu-id="b6ac2-287">To determine whether the out-of-memory exception is managed</span></span>

1. <span data-ttu-id="b6ac2-288">No depurador do Visual Studio ou WinDbg com a extensão de depurador SOS carregada, digite o comando de exceção de impressão (**pe**):</span><span class="sxs-lookup"><span data-stu-id="b6ac2-288">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the print exception (**pe**) command:</span></span>

    <span data-ttu-id="b6ac2-289">**!pe**</span><span class="sxs-lookup"><span data-stu-id="b6ac2-289">**!pe**</span></span>

    <span data-ttu-id="b6ac2-290">Se a exceção for gerenciada, <xref:System.OutOfMemoryException> será exibido como o tipo de exceção, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-290">If the exception is managed, <xref:System.OutOfMemoryException> is displayed as the exception type, as shown in the following example.</span></span>

    ```console
    Exception object: 39594518
    Exception type: System.OutOfMemoryException
    Message: <none>
    InnerException: <none>
    StackTrace (generated):
    ```

2. <span data-ttu-id="b6ac2-291">Se a saída não especificar uma exceção, você precisará determinar de qual thread é a exceção de falta de memória.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-291">If the output does not specify an exception, you have to determine which thread the out-of-memory exception is from.</span></span> <span data-ttu-id="b6ac2-292">Digite o comando a seguir no depurador para mostrar todos os threads com suas pilhas de chamadas:</span><span class="sxs-lookup"><span data-stu-id="b6ac2-292">Type the following command in the debugger to show all the threads with their call stacks:</span></span>

    <span data-ttu-id="b6ac2-293">**~\*kb**</span><span class="sxs-lookup"><span data-stu-id="b6ac2-293">**~\*kb**</span></span>

    <span data-ttu-id="b6ac2-294">O thread com a pilha que tem chamadas de exceção é indicado pelo argumento `RaiseTheException`.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-294">The thread with the stack that has exception calls is indicated by the `RaiseTheException` argument.</span></span> <span data-ttu-id="b6ac2-295">Esse é o objeto de exceção gerenciada.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-295">This is the managed exception object.</span></span>

    ```console
    28adfb44 7923918f 5b61f2b4 00000000 5b61f2b4 mscorwks!RaiseTheException+0xa0
    ```

3. <span data-ttu-id="b6ac2-296">Você pode usar o comando a seguir para despejar exceções aninhadas.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-296">You can use the following command to dump nested exceptions.</span></span>

    <span data-ttu-id="b6ac2-297">**!pe -nested**</span><span class="sxs-lookup"><span data-stu-id="b6ac2-297">**!pe -nested**</span></span>

    <span data-ttu-id="b6ac2-298">Se você não encontrar nenhuma exceção, isso significará que a exceção de falta de memória se originou de código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-298">If you do not find any exceptions, the out-of-memory exception originated from unmanaged code.</span></span>

<a name="GetVM"></a>

### <a name="to-determine-how-much-virtual-memory-can-be-reserved"></a><span data-ttu-id="b6ac2-299">Para determinar a quantidade de memória virtual que pode ser reservada</span><span class="sxs-lookup"><span data-stu-id="b6ac2-299">To determine how much virtual memory can be reserved</span></span>

- <span data-ttu-id="b6ac2-300">No WinDbg, com a extensão de depurador SOS carregada, digite o seguinte comando para obter a maior região livre:</span><span class="sxs-lookup"><span data-stu-id="b6ac2-300">In WinDbg with the SOS debugger extension loaded, type the following command to get the largest free region:</span></span>

  <span data-ttu-id="b6ac2-301">**!address -summary**</span><span class="sxs-lookup"><span data-stu-id="b6ac2-301">**!address -summary**</span></span>

  <span data-ttu-id="b6ac2-302">A maior região livre é exibida conforme mostrado na saída a seguir.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-302">The largest free region is displayed as shown in the following output.</span></span>

  ```console
  Largest free region: Base 54000000 - Size 0003A980
  ```

  <span data-ttu-id="b6ac2-303">Neste exemplo, o tamanho da maior região livre é aproximadamente 24.000 KB (3A980 em hexadecimal).</span><span class="sxs-lookup"><span data-stu-id="b6ac2-303">In this example, the size of the largest free region is approximately 24000 KB (3A980 in hexadecimal).</span></span> <span data-ttu-id="b6ac2-304">Essa região é menor do que o tamanho requerido pelo coletor de lixo para um segmento.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-304">This region is much smaller than what the garbage collector needs for a segment.</span></span>

  <span data-ttu-id="b6ac2-305">\- ou -</span><span class="sxs-lookup"><span data-stu-id="b6ac2-305">-or-</span></span>

- <span data-ttu-id="b6ac2-306">Use o comando **vmstat**:</span><span class="sxs-lookup"><span data-stu-id="b6ac2-306">Use the **vmstat** command:</span></span>

  <span data-ttu-id="b6ac2-307">**!vmstat**</span><span class="sxs-lookup"><span data-stu-id="b6ac2-307">**!vmstat**</span></span>

  <span data-ttu-id="b6ac2-308">A maior região livre é o maior valor encontrado na coluna MAXIMUM, conforme mostrado na saída a seguir.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-308">The largest free region is the largest value in the MAXIMUM column, as shown in the following output.</span></span>

  ```console
  TYPE        MINIMUM   MAXIMUM     AVERAGE   BLK COUNT   TOTAL
  ~~~~        ~~~~~~~   ~~~~~~~     ~~~~~~~   ~~~~~~~~~~  ~~~~
  Free:
  Small       8K        64K         46K       36          1,671K
  Medium      80K       864K        349K      3           1,047K
  Large       1,384K    1,278,848K  151,834K  12          1,822,015K
  Summary     8K        1,278,848K  35,779K   51          1,824,735K
  ```

<a name="Physical"></a>

### <a name="to-determine-whether-there-is-enough-physical-memory"></a><span data-ttu-id="b6ac2-309">Para determinar se há memória física suficiente</span><span class="sxs-lookup"><span data-stu-id="b6ac2-309">To determine whether there is enough physical memory</span></span>

1. <span data-ttu-id="b6ac2-310">Inicie o Gerenciador de tarefas do Windows.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-310">Start Windows Task Manager.</span></span>

2. <span data-ttu-id="b6ac2-311">Na guia **Desempenho**, examine o valor confirmado.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-311">On the **Performance** tab, look at the committed value.</span></span> <span data-ttu-id="b6ac2-312">(No Windows 7, examine **Confirmar (KB)** no **grupo Sistema**.)</span><span class="sxs-lookup"><span data-stu-id="b6ac2-312">(In Windows 7, look at **Commit (KB)** in the **System group**.)</span></span>

    <span data-ttu-id="b6ac2-313">Se o **Total** está próximo do **Limite**, você está com pouca memória física.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-313">If the **Total** is close to the **Limit**, you are running low on physical memory.</span></span>

<a name="ManagedHeapCommit"></a>

### <a name="to-determine-how-much-memory-the-managed-heap-is-committing"></a><span data-ttu-id="b6ac2-314">Para determinar a quantidade de memória que o heap gerenciado está confirmando</span><span class="sxs-lookup"><span data-stu-id="b6ac2-314">To determine how much memory the managed heap is committing</span></span>

- <span data-ttu-id="b6ac2-315">Use o contador de desempenho de memória de `# Total committed bytes` para obter o número de bytes que o heap gerenciado está confirmando.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-315">Use the `# Total committed bytes` memory performance counter to get the number of bytes that the managed heap is committing.</span></span> <span data-ttu-id="b6ac2-316">O coletor de lixo confirma partes em um segmento conforme necessário, nem todas ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-316">The garbage collector commits chunks on a segment as needed, not all at the same time.</span></span>

  > [!NOTE]
  > <span data-ttu-id="b6ac2-317">Não use o contador de desempenho de `# Bytes in all Heaps`, porque ele não representa o uso de memória real pelo heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-317">Do not use the `# Bytes in all Heaps` performance counter, because it does not represent actual memory usage by the managed heap.</span></span> <span data-ttu-id="b6ac2-318">O tamanho de uma geração está incluído no valor e é na verdade seu tamanho limite, ou seja, o tamanho que induz uma coleta de lixo caso a geração esteja preenchida com objetos.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-318">The size of a generation is included in this value and is actually its threshold size, that is, the size that induces a garbage collection if the generation is filled with objects.</span></span> <span data-ttu-id="b6ac2-319">Portanto, esse valor geralmente é zero.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-319">Therefore, this value is usually zero.</span></span>

<a name="ManagedHeapReserve"></a>

### <a name="to-determine-how-much-memory-the-managed-heap-reserves"></a><span data-ttu-id="b6ac2-320">Para determinar a quantidade de memória que o heap gerenciado reserva</span><span class="sxs-lookup"><span data-stu-id="b6ac2-320">To determine how much memory the managed heap reserves</span></span>

- <span data-ttu-id="b6ac2-321">Use o contador de desempenho de memória de `# Total reserved bytes`.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-321">Use the `# Total reserved bytes` memory performance counter.</span></span>

  <span data-ttu-id="b6ac2-322">O coletor de lixo reserva de memória em segmentos, sendo que você pode determinar a localização do início de um segmento usando o comando **eeheap**.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-322">The garbage collector reserves memory in segments, and you can determine where a segment starts by using the **eeheap** command.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="b6ac2-323">Embora você possa determinar a quantidade de memória que o coletor de lixo aloca para cada segmento, o tamanho de segmento é específico da implementação e está sujeito a alterações a qualquer momento, incluindo atualizações periódicas.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-323">Although you can determine the amount of memory the garbage collector allocates for each segment, segment size is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="b6ac2-324">Seu aplicativo nunca deve fazer suposições sobre o tamanho de um segmento em particular nem depender dele, tampouco deve tentar configurar a quantidade de memória disponível para alocações de segmento.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-324">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>

- <span data-ttu-id="b6ac2-325">No depurador do Visual Studio ou WinDbg com a extensão de depurador SOS carregada, digite o comando a seguir:</span><span class="sxs-lookup"><span data-stu-id="b6ac2-325">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="b6ac2-326">**!eeheap -gc**</span><span class="sxs-lookup"><span data-stu-id="b6ac2-326">**!eeheap -gc**</span></span>

  <span data-ttu-id="b6ac2-327">O resultado é demonstrado a seguir.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-327">The result is as follows.</span></span>

  ```console
  Number of GC Heaps: 2
  ------------------------------
  Heap 0 (002db550)
  generation 0 starts at 0x02abe29c
  generation 1 starts at 0x02abdd08
  generation 2 starts at 0x02ab0038
  ephemeral segment allocation context: none
    segment    begin allocated     size
  02ab0000 02ab0038  02aceff4 0x0001efbc(126908)
  Large object heap starts at 0x0aab0038
    segment    begin allocated     size
  0aab0000 0aab0038  0aab2278 0x00002240(8768)
  Heap Size   0x211fc(135676)
  ------------------------------
  Heap 1 (002dc958)
  generation 0 starts at 0x06ab1bd8
  generation 1 starts at 0x06ab1bcc
  generation 2 starts at 0x06ab0038
  ephemeral segment allocation context: none
    segment    begin allocated     size
  06ab0000 06ab0038  06ab3be4 0x00003bac(15276)
  Large object heap starts at 0x0cab0038
    segment    begin allocated     size
  0cab0000 0cab0038  0cab0048 0x00000010(16)
  Heap Size    0x3bbc(15292)
  ------------------------------
  GC Heap Size   0x24db8(150968)
  ```

  <span data-ttu-id="b6ac2-328">Os endereços indicados por "segmento" são os endereços iniciais dos segmentos.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-328">The addresses indicated by "segment" are the starting addresses of the segments.</span></span>

<a name="ExamineGen2"></a>

### <a name="to-determine-large-objects-in-generation-2"></a><span data-ttu-id="b6ac2-329">Para determinar objetos grandes na geração 2</span><span class="sxs-lookup"><span data-stu-id="b6ac2-329">To determine large objects in generation 2</span></span>

- <span data-ttu-id="b6ac2-330">No depurador do Visual Studio ou WinDbg com a extensão de depurador SOS carregada, digite o comando a seguir:</span><span class="sxs-lookup"><span data-stu-id="b6ac2-330">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="b6ac2-331">**!dumpheap –stat**</span><span class="sxs-lookup"><span data-stu-id="b6ac2-331">**!dumpheap –stat**</span></span>

  <span data-ttu-id="b6ac2-332">Se o heap gerenciado é grande, **dumpheap** pode levar algum tempo para concluir.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-332">If the managed heap is big, **dumpheap** may take a while to finish.</span></span>

  <span data-ttu-id="b6ac2-333">Você pode começar a analisar pelas últimas poucas linhas da saída, pois elas listam os objetos que usam mais espaço.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-333">You can start analyzing from the last few lines of the output, because they list the objects that use the most space.</span></span> <span data-ttu-id="b6ac2-334">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="b6ac2-334">For example:</span></span>

  ```console
  2c6108d4   173712     14591808 DevExpress.XtraGrid.Views.Grid.ViewInfo.GridCellInfo
  00155f80      533     15216804      Free
  7a747c78   791070     15821400 System.Collections.Specialized.ListDictionary+DictionaryNode
  7a747bac   700930     19626040 System.Collections.Specialized.ListDictionary
  2c64e36c    78644     20762016 DevExpress.XtraEditors.ViewInfo.TextEditViewInfo
  79124228   121143     29064120 System.Object[]
  035f0ee4    81626     35588936 Toolkit.TlkOrder
  00fcae40     6193     44911636 WaveBasedStrategy.Tick_Snap[]
  791242ec    40182     90664128 System.Collections.Hashtable+bucket[]
  790fa3e0  3154024    137881448 System.String
  Total 8454945 objects
  ```

  <span data-ttu-id="b6ac2-335">O último objeto listado é uma cadeia de caracteres e ocupa mais espaço.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-335">The last object listed is a string and occupies the most space.</span></span> <span data-ttu-id="b6ac2-336">Você pode examinar o aplicativo para ver como os objetos de cadeia de caracteres podem ser otimizados.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-336">You can examine your application to see how your string objects can be optimized.</span></span> <span data-ttu-id="b6ac2-337">Para ver as cadeias de caracteres que têm entre 150 e 200 bytes, digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b6ac2-337">To see strings that are between 150 and 200 bytes, type the following:</span></span>

  <span data-ttu-id="b6ac2-338">**!dumpheap -type System.String -min 150 -max 200**</span><span class="sxs-lookup"><span data-stu-id="b6ac2-338">**!dumpheap -type System.String -min 150 -max 200**</span></span>

  <span data-ttu-id="b6ac2-339">Um exemplo dos resultados é conforme demonstrado a seguir.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-339">An example of the results is as follows.</span></span>

  ```console
  Address  MT           Size  Gen
  1875d2c0 790fa3e0      152    2 System.String HighlightNullStyle_Blotter_PendingOrder-11_Blotter_PendingOrder-11
  …
  ```

  <span data-ttu-id="b6ac2-340">Para uma ID, usar um número inteiro em vez de uma cadeia de caracteres pode ser mais eficiente.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-340">Using an integer instead of a string for an ID can be more efficient.</span></span> <span data-ttu-id="b6ac2-341">Se a mesma cadeia de caracteres está sendo repetida milhares de vezes, considere a centralização da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-341">If the same string is being repeated thousands of times, consider string interning.</span></span> <span data-ttu-id="b6ac2-342">Confira mais informações sobre a centralização da cadeia de caracteres no tópico de referência para o método <xref:System.String.Intern%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-342">For more information about string interning, see the reference topic for the <xref:System.String.Intern%2A?displayProperty=nameWithType> method.</span></span>

<a name="ObjRef"></a>

### <a name="to-determine-references-to-objects"></a><span data-ttu-id="b6ac2-343">Para determinar referências a objetos</span><span class="sxs-lookup"><span data-stu-id="b6ac2-343">To determine references to objects</span></span>

- <span data-ttu-id="b6ac2-344">No WinDbg, com a extensão de depurador SOS carregada, digite o seguinte comando para listar as referências a objetos:</span><span class="sxs-lookup"><span data-stu-id="b6ac2-344">In WinDbg with the SOS debugger extension loaded, type the following command to list references to objects:</span></span>

  <span data-ttu-id="b6ac2-345">**!gcroot**</span><span class="sxs-lookup"><span data-stu-id="b6ac2-345">**!gcroot**</span></span>

  `-or-`

- <span data-ttu-id="b6ac2-346">Para determinar as referências a um objeto específico, inclua o endereço:</span><span class="sxs-lookup"><span data-stu-id="b6ac2-346">To determine the references for a specific object, include the address:</span></span>

  <span data-ttu-id="b6ac2-347">**!gcroot 1c37b2ac**</span><span class="sxs-lookup"><span data-stu-id="b6ac2-347">**!gcroot 1c37b2ac**</span></span>

  <span data-ttu-id="b6ac2-348">Raízes encontradas em pilhas podem ser falsos positivos.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-348">Roots found on stacks may be false positives.</span></span> <span data-ttu-id="b6ac2-349">Para obter mais informações, use o comando `!help gcroot`.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-349">For more information, use the command `!help gcroot`.</span></span>

  ```console
  ebx:Root:19011c5c(System.Windows.Forms.Application+ThreadContext)->
  19010b78(DemoApp.FormDemoApp)->
  19011158(System.Windows.Forms.PropertyStore)->
  … [omitted]
  1c3745ec(System.Data.DataTable)->
  1c3747a8(System.Data.DataColumnCollection)->
  1c3747f8(System.Collections.Hashtable)->
  1c376590(System.Collections.Hashtable+bucket[])->
  1c376c98(System.Data.DataColumn)->
  1c37b270(System.Data.Common.DoubleStorage)->
  1c37b2ac(System.Double[])
  Scan Thread 0 OSTHread 99c
  Scan Thread 6 OSTHread 484
  ```

  <span data-ttu-id="b6ac2-350">O comando **gcroot** pode demorar muito tempo para concluir.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-350">The **gcroot** command can take a long time to finish.</span></span> <span data-ttu-id="b6ac2-351">Qualquer objeto que não é recuperado pela coleta de lixo é um objeto ativo.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-351">Any object that is not reclaimed by garbage collection is a live object.</span></span> <span data-ttu-id="b6ac2-352">Isso significa que alguma raiz está ligando-se direta ou indiretamente ao objeto, então **gcroot** deve retornar informações de caminho do objeto.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-352">This means that some root is directly or indirectly holding onto the object, so **gcroot** should return path information to the object.</span></span> <span data-ttu-id="b6ac2-353">Você deve examinar os grafos retornados e ver por que esses objetos ainda são referenciados.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-353">You should examine the graphs returned and see why these objects are still referenced.</span></span>

<a name="Induce"></a>

### <a name="to-determine-whether-a-finalizer-has-been-run"></a><span data-ttu-id="b6ac2-354">Para determinar se um finalizador foi executado</span><span class="sxs-lookup"><span data-stu-id="b6ac2-354">To determine whether a finalizer has been run</span></span>

- <span data-ttu-id="b6ac2-355">Execute um programa de teste que contenha o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="b6ac2-355">Run a test program that contains the following code:</span></span>

  ```csharp
  GC.Collect();
  GC.WaitForPendingFinalizers();
  GC.Collect();
  ```

  <span data-ttu-id="b6ac2-356">Se o teste resolve o problema, isso significa que o coletor de lixo não estava recuperando objetos, pois os finalizadores desses objetos tinham sido suspensos.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-356">If the test resolves the problem, this means that the garbage collector was not reclaiming objects, because the finalizers for those objects had been suspended.</span></span> <span data-ttu-id="b6ac2-357">O método <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> permite que os finalizadores concluam suas tarefas e corrige o problema.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-357">The <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> method enables the finalizers to complete their tasks, and fixes the problem.</span></span>

<a name="Finalize"></a>

### <a name="to-determine-whether-there-are-objects-waiting-to-be-finalized"></a><span data-ttu-id="b6ac2-358">Para determinar se há objetos aguardando a finalização</span><span class="sxs-lookup"><span data-stu-id="b6ac2-358">To determine whether there are objects waiting to be finalized</span></span>

1. <span data-ttu-id="b6ac2-359">No depurador do Visual Studio ou WinDbg com a extensão de depurador SOS carregada, digite o comando a seguir:</span><span class="sxs-lookup"><span data-stu-id="b6ac2-359">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

    <span data-ttu-id="b6ac2-360">**!finalizequeue**</span><span class="sxs-lookup"><span data-stu-id="b6ac2-360">**!finalizequeue**</span></span>

    <span data-ttu-id="b6ac2-361">Observe o número de objetos que estão prontos para finalização.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-361">Look at the number of objects that are ready for finalization.</span></span> <span data-ttu-id="b6ac2-362">Se o número for alto, você deverá examinar o motivo pelo qual esses finalizadores não são capazes de avançar em absoluto ou não são capazes de avançar suficientemente rápido.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-362">If the number is high, you must examine why these finalizers cannot progress at all or cannot progress fast enough.</span></span>

2. <span data-ttu-id="b6ac2-363">Para obter uma saída de threads, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="b6ac2-363">To get an output of threads, type the following command:</span></span>

    <span data-ttu-id="b6ac2-364">**threads -special**</span><span class="sxs-lookup"><span data-stu-id="b6ac2-364">**threads -special**</span></span>

    <span data-ttu-id="b6ac2-365">Esse comando fornece uma saída como a mostrada a seguir.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-365">This command provides output such as the following.</span></span>

    ```console
       OSID     Special thread type
    2    cd0    DbgHelper
    3    c18    Finalizer
    4    df0    GC SuspendEE
    ```

    <span data-ttu-id="b6ac2-366">O thread do finalizador indica qual finalizador, caso haja um, está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-366">The finalizer thread indicates which finalizer, if any, is currently being run.</span></span> <span data-ttu-id="b6ac2-367">Quando um thread do finalizador não está executando nenhum finalizador, ele está aguardando que um evento o diga para fazer seu trabalho.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-367">When a finalizer thread is not running any finalizers, it is waiting for an event to tell it to do its work.</span></span> <span data-ttu-id="b6ac2-368">Na maioria das vezes você verá o thread do finalizador nesse estado porque ele é executado em THREAD_HIGHEST_PRIORITY e deve concluir a execução de finalizadores, caso haja um, muito rapidamente.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-368">Most of the time you will see the finalizer thread in this state because it runs at THREAD_HIGHEST_PRIORITY and is supposed to finish running finalizers, if any, very quickly.</span></span>

<a name="Fragmented"></a>

### <a name="to-determine-the-amount-of-free-space-in-the-managed-heap"></a><span data-ttu-id="b6ac2-369">Para determinar a quantidade de espaço livre no heap gerenciado</span><span class="sxs-lookup"><span data-stu-id="b6ac2-369">To determine the amount of free space in the managed heap</span></span>

- <span data-ttu-id="b6ac2-370">No depurador do Visual Studio ou WinDbg com a extensão de depurador SOS carregada, digite o comando a seguir:</span><span class="sxs-lookup"><span data-stu-id="b6ac2-370">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="b6ac2-371">**!dumpheap -type Free -stat**</span><span class="sxs-lookup"><span data-stu-id="b6ac2-371">**!dumpheap -type Free -stat**</span></span>

  <span data-ttu-id="b6ac2-372">Esse comando exibe o tamanho total de todos os objetos livres no heap gerenciado, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-372">This command displays the total size of all the free objects on the managed heap, as shown in the following example.</span></span>

  ```console
  total 230 objects
  Statistics:
        MT    Count    TotalSize Class Name
  00152b18      230     40958584      Free
  Total 230 objects
  ```

- <span data-ttu-id="b6ac2-373">Para determinar o espaço livre na geração 0, digite o comando a seguir para obter informações de consumo de memória por geração:</span><span class="sxs-lookup"><span data-stu-id="b6ac2-373">To determine the free space in generation 0, type the following command for memory consumption information by generation:</span></span>

  <span data-ttu-id="b6ac2-374">**!eeheap -gc**</span><span class="sxs-lookup"><span data-stu-id="b6ac2-374">**!eeheap -gc**</span></span>

  <span data-ttu-id="b6ac2-375">Esse comando exibe uma saída semelhante à seguinte.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-375">This command displays output similar to the following.</span></span> <span data-ttu-id="b6ac2-376">A última linha mostra o segmento efêmero.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-376">The last line shows the ephemeral segment.</span></span>

  ```console
  Heap 0 (0015ad08)
  generation 0 starts at 0x49521f8c
  generation 1 starts at 0x494d7f64
  generation 2 starts at 0x007f0038
  ephemeral segment allocation context: none
  segment  begin     allocated  size
  00178250 7a80d84c  7a82f1cc   0x00021980(137600)
  00161918 78c50e40  78c7056c   0x0001f72c(128812)
  007f0000 007f0038  047eed28   0x03ffecf0(67103984)
  3a120000 3a120038  3a3e84f8   0x002c84c0(2917568)
  46120000 46120038  49e05d04   0x03ce5ccc(63855820)
  ```

- <span data-ttu-id="b6ac2-377">Calcule o espaço usado pela geração 0:</span><span class="sxs-lookup"><span data-stu-id="b6ac2-377">Calculate the space used by generation 0:</span></span>

  <span data-ttu-id="b6ac2-378">**? 49e05d04-0x49521f8c**</span><span class="sxs-lookup"><span data-stu-id="b6ac2-378">**? 49e05d04-0x49521f8c**</span></span>

  <span data-ttu-id="b6ac2-379">O resultado é demonstrado a seguir.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-379">The result is as follows.</span></span> <span data-ttu-id="b6ac2-380">A geração 0 usa aproximadamente 9 MB.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-380">Generation 0 is approximately 9 MB.</span></span>

  ```console
  Evaluate expression: 9321848 = 008e3d78
  ```

- <span data-ttu-id="b6ac2-381">O comando a seguir despeja o espaço livre dentro do intervalo de geração 0:</span><span class="sxs-lookup"><span data-stu-id="b6ac2-381">The following command dumps the free space within the generation 0 range:</span></span>

  <span data-ttu-id="b6ac2-382">**!dumpheap -type Free -stat 0x49521f8c 49e05d04**</span><span class="sxs-lookup"><span data-stu-id="b6ac2-382">**!dumpheap -type Free -stat 0x49521f8c 49e05d04**</span></span>

  <span data-ttu-id="b6ac2-383">O resultado é demonstrado a seguir.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-383">The result is as follows.</span></span>

  ```console
  ------------------------------
  Heap 0
  total 409 objects
  ------------------------------
  Heap 1
  total 0 objects
  ------------------------------
  Heap 2
  total 0 objects
  ------------------------------
  Heap 3
  total 0 objects
  ------------------------------
  total 409 objects
  Statistics:
        MT    Count TotalSize Class Name
  0015a498      409   7296540      Free
  Total 409 objects
  ```

  <span data-ttu-id="b6ac2-384">A saída mostra que a parte de geração 0 do heap está usando 9 MB de espaço para objetos e tem 7 MB livres.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-384">This output shows that the generation 0 portion of the heap is using 9 MB of space for objects and has 7 MB free.</span></span> <span data-ttu-id="b6ac2-385">Essa análise mostra a extensão para a qual a geração 0 contribui para a fragmentação.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-385">This analysis shows the extent to which generation 0 contributes to fragmentation.</span></span> <span data-ttu-id="b6ac2-386">Essa quantidade de uso do heap deve ser desconsiderada do valor total como a causa de fragmentação por objetos de longo prazo.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-386">This amount of heap usage should be discounted from the total amount as the cause of fragmentation by long-term objects.</span></span>

<a name="Pinned"></a>

### <a name="to-determine-the-number-of-pinned-objects"></a><span data-ttu-id="b6ac2-387">Para determinar o número de objetos fixados</span><span class="sxs-lookup"><span data-stu-id="b6ac2-387">To determine the number of pinned objects</span></span>

- <span data-ttu-id="b6ac2-388">No depurador do Visual Studio ou WinDbg com a extensão de depurador SOS carregada, digite o comando a seguir:</span><span class="sxs-lookup"><span data-stu-id="b6ac2-388">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="b6ac2-389">**!gchandles**</span><span class="sxs-lookup"><span data-stu-id="b6ac2-389">**!gchandles**</span></span>

  <span data-ttu-id="b6ac2-390">As estatísticas exibidas incluem o número de identificadores fixados, tal como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-390">The statistics displayed includes the number of pinned handles, as the following example shows.</span></span>

  ```console
  GC Handle Statistics:
  Strong Handles:      29
  Pinned Handles:      10
  ```

<a name="TimeInGC"></a>

### <a name="to-determine-the-length-of-time-in-a-garbage-collection"></a><span data-ttu-id="b6ac2-391">Para determinar a duração de uma coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="b6ac2-391">To determine the length of time in a garbage collection</span></span>

- <span data-ttu-id="b6ac2-392">Examine o contador de desempenho de memória de `% Time in GC`.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-392">Examine the `% Time in GC` memory performance counter.</span></span>

  <span data-ttu-id="b6ac2-393">O valor é calculado usando um intervalo de tempo de exemplo.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-393">The value is calculated by using a sample interval time.</span></span> <span data-ttu-id="b6ac2-394">Já que os contadores são atualizados ao final de cada coleta de lixo, a amostra atual terá o mesmo valor que a amostra anterior se nenhuma coleta tiver ocorrido durante o intervalo.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-394">Because the counters are updated at the end of each garbage collection, the current sample will have the same value as the previous sample if no collections occurred during the interval.</span></span>

  <span data-ttu-id="b6ac2-395">O tempo de coleta é obtido multiplicando o tempo de intervalo de exemplo pelo valor do percentual.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-395">Collection time is obtained by multiplying the sample interval time with the percentage value.</span></span>

  <span data-ttu-id="b6ac2-396">Os dados a seguir mostram quatro intervalos de amostragem de dois segundos, para um estudo de oito segundos.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-396">The following data shows four sampling intervals of two seconds, for an 8-second study.</span></span> <span data-ttu-id="b6ac2-397">As colunas `Gen0`, `Gen1` e `Gen2` mostram o número de coletas de lixo ocorridas durante esse intervalo para essa geração.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-397">The `Gen0`, `Gen1`, and `Gen2` columns show the number of garbage collections that occurred during that interval for that generation.</span></span>

  ```console
  Interval    Gen0    Gen1    Gen2    % Time in GC
          1       9       3       1              10
          2      10       3       1               1
          3      11       3       1               3
          4      11       3       1               3
  ```

  <span data-ttu-id="b6ac2-398">Essas informações não mostram quando a coleta de lixo ocorreu, mas você pode determinar o número de coletas de lixo que ocorreram em um intervalo de tempo.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-398">This information does not show when the garbage collection occurred, but you can determine the number of garbage collections that occurred in an interval of time.</span></span> <span data-ttu-id="b6ac2-399">Supondo o pior cenário possível, a décima coleta de lixo de geração 0 terminou no início do segundo intervalo e a décima primeira coleta de lixo de geração 0 foi concluída no final do quinto intervalo.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-399">Assuming the worst case, the tenth generation 0 garbage collection finished at the start of the second interval, and the eleventh generation 0 garbage collection finished at the end of the fifth interval.</span></span> <span data-ttu-id="b6ac2-400">O tempo entre o final da décima e o final da décima primeira coleta de lixo é cerca de dois segundos e o contador de desempenho mostra 3%, portanto, a duração da décima primeira coleta de lixo de geração 0 foi (dois segundos \* 3% = 60 ms).</span><span class="sxs-lookup"><span data-stu-id="b6ac2-400">The time between the end of the tenth and the end of the eleventh garbage collection is about 2 seconds, and the performance counter shows 3%, so the duration of the eleventh generation 0 garbage collection was (2 seconds \* 3% = 60ms).</span></span>

  <span data-ttu-id="b6ac2-401">Neste exemplo, há cinco períodos.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-401">In this example, there are 5 periods.</span></span>

  ```console
  Interval    Gen0    Gen1    Gen2     % Time in GC
          1       9       3       1                3
          2      10       3       1                1
          3      11       4       2                1
          4      11       4       2                1
          5      11       4       2               20
  ```

  <span data-ttu-id="b6ac2-402">A segunda coleta de lixo de geração 2 começou durante o terceiro intervalo e terminou no quinto intervalo.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-402">The second generation 2 garbage collection started during the third interval and finished at the fifth interval.</span></span> <span data-ttu-id="b6ac2-403">Supondo o pior cenário possível, a última coleta de lixo foi para uma coleta de geração 0 que terminou no início do segundo intervalo e a coleta de lixo de geração 2 terminou no final do quinto intervalo.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-403">Assuming the worst case, the last garbage collection was for a generation 0 collection that finished at the start of the second interval, and the generation 2 garbage collection finished at the end of the fifth interval.</span></span> <span data-ttu-id="b6ac2-404">Portanto, o tempo entre o fim da coleta de lixo de geração 0 e o fim da coleta de lixo de geração 2 é de quatro segundos.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-404">Therefore, the time between the end of the generation 0 garbage collection and the end of the generation 2 garbage collection is 4 seconds.</span></span> <span data-ttu-id="b6ac2-405">Já que o contador de `% Time in GC` é 20%, a quantidade máxima de tempo que a coleta de lixo de geração 2 poderia ter levado é (quatro segundos \* 20% = 800 ms).</span><span class="sxs-lookup"><span data-stu-id="b6ac2-405">Because the `% Time in GC` counter is 20%, the maximum amount of time the generation 2 garbage collection could have taken is (4 seconds \* 20% = 800ms).</span></span>

- <span data-ttu-id="b6ac2-406">Como alternativa, você pode determinar a duração de uma coleta de lixo usando [eventos ETW de coleta de lixo](../../../docs/framework/performance/garbage-collection-etw-events.md) e analisando as informações para determinar a duração da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-406">Alternatively, you can determine the length of a garbage collection by using [garbage collection ETW events](../../../docs/framework/performance/garbage-collection-etw-events.md), and analyze the information to determine the duration of garbage collection.</span></span>

  <span data-ttu-id="b6ac2-407">Por exemplo, os dados a seguir mostram uma sequência de eventos que ocorreram durante uma coleta de lixo não simultânea.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-407">For example, the following data shows an event sequence that occurred during a non-concurrent garbage collection.</span></span>

  ```console
  Timestamp    Event name
  513052        GCSuspendEEBegin_V1
  513078        GCSuspendEEEnd
  513090        GCStart_V1
  517890        GCEnd_V1
  517894        GCHeapStats
  517897        GCRestartEEBegin
  517918        GCRestartEEEnd
  ```

  <span data-ttu-id="b6ac2-408">Suspender o thread gerenciado levou 26 us (`GCSuspendEEEnd` – `GCSuspendEEBegin_V1`).</span><span class="sxs-lookup"><span data-stu-id="b6ac2-408">Suspending the managed thread took 26us (`GCSuspendEEEnd` – `GCSuspendEEBegin_V1`).</span></span>

  <span data-ttu-id="b6ac2-409">A coleta de lixo propriamente dita levou 4,8 ms (`GCEnd_V1` – `GCStart_V1`).</span><span class="sxs-lookup"><span data-stu-id="b6ac2-409">The actual garbage collection took 4.8ms (`GCEnd_V1` – `GCStart_V1`).</span></span>

  <span data-ttu-id="b6ac2-410">Retomar os threads gerenciados levou 21 us (`GCRestartEEEnd` – `GCRestartEEBegin`).</span><span class="sxs-lookup"><span data-stu-id="b6ac2-410">Resuming the managed threads took 21us (`GCRestartEEEnd` – `GCRestartEEBegin`).</span></span>

  <span data-ttu-id="b6ac2-411">A saída a seguir fornece um exemplo para coleta de lixo em segundo plano e inclui o processo, thread e campos de evento.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-411">The following output provides an example for background garbage collection, and includes the process, thread, and event fields.</span></span> <span data-ttu-id="b6ac2-412">(Nem todos os dados são mostrados.)</span><span class="sxs-lookup"><span data-stu-id="b6ac2-412">(Not all data is shown.)</span></span>

  ```console
  timestamp(us)    event name            process    thread    event field
  42504385        GCSuspendEEBegin_V1    Test.exe    4372             1
  42504648        GCSuspendEEEnd         Test.exe    4372
  42504816        GCStart_V1             Test.exe    4372        102019
  42504907        GCStart_V1             Test.exe    4372        102020
  42514170        GCEnd_V1               Test.exe    4372
  42514204        GCHeapStats            Test.exe    4372        102020
  42832052        GCRestartEEBegin       Test.exe    4372
  42832136        GCRestartEEEnd         Test.exe    4372
  63685394        GCSuspendEEBegin_V1    Test.exe    4744             6
  63686347        GCSuspendEEEnd         Test.exe    4744
  63784294        GCRestartEEBegin       Test.exe    4744
  63784407        GCRestartEEEnd         Test.exe    4744
  89931423        GCEnd_V1               Test.exe    4372        102019
  89931464        GCHeapStats            Test.exe    4372
  ```

  <span data-ttu-id="b6ac2-413">O evento `GCStart_V1` em 42504816 indica que esta é uma coleta de lixo em segundo plano, porque o último campo é `1`.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-413">The `GCStart_V1` event at 42504816 indicates that this is a background garbage collection, because the last field is `1`.</span></span> <span data-ttu-id="b6ac2-414">Essa torna-se a coleta de lixo Nº</span><span class="sxs-lookup"><span data-stu-id="b6ac2-414">This becomes garbage collection No.</span></span> <span data-ttu-id="b6ac2-415">102019.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-415">102019.</span></span>

  <span data-ttu-id="b6ac2-416">O evento `GCStart` ocorre porque há necessidade de uma coleta de lixo efêmero antes de você iniciar uma coleta de lixo em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-416">The `GCStart` event occurs because there is a need for an ephemeral garbage collection before you start a background garbage collection.</span></span> <span data-ttu-id="b6ac2-417">Essa torna-se a coleta de lixo Nº</span><span class="sxs-lookup"><span data-stu-id="b6ac2-417">This becomes garbage collection No.</span></span> <span data-ttu-id="b6ac2-418">102020.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-418">102020.</span></span>

  <span data-ttu-id="b6ac2-419">Em 42514170, a coleta de lixo Nº</span><span class="sxs-lookup"><span data-stu-id="b6ac2-419">At 42514170, garbage collection No.</span></span> <span data-ttu-id="b6ac2-420">102020 é concluída.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-420">102020 finishes.</span></span> <span data-ttu-id="b6ac2-421">Os threads gerenciados são reiniciados nesse momento.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-421">The managed threads are restarted at this point.</span></span> <span data-ttu-id="b6ac2-422">Isso é concluído no thread 4372, que disparou essa coleta de lixo em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-422">This is completed on thread 4372, which triggered this background garbage collection.</span></span>

  <span data-ttu-id="b6ac2-423">No thread 4744, ocorre uma suspensão.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-423">On thread 4744, a suspension occurs.</span></span> <span data-ttu-id="b6ac2-424">Essa é a única vez em que a coleta de lixo em segundo plano precisa suspender os threads gerenciados.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-424">This is the only time at which the background garbage collection has to suspend managed threads.</span></span> <span data-ttu-id="b6ac2-425">Essa duração é de aproximadamente 99 ms ((63784407-63685394)/1000).</span><span class="sxs-lookup"><span data-stu-id="b6ac2-425">This duration is approximately 99ms ((63784407-63685394)/1000).</span></span>

  <span data-ttu-id="b6ac2-426">O evento `GCEnd` para a coleta de lixo em segundo plano está em 89931423.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-426">The `GCEnd` event for the background garbage collection is at 89931423.</span></span> <span data-ttu-id="b6ac2-427">Isso significa que a coleta de lixo em segundo plano durou cerca de 47 segundos ((89931423-42504816)/1000).</span><span class="sxs-lookup"><span data-stu-id="b6ac2-427">This means that the background garbage collection lasted for about 47seconds ((89931423-42504816)/1000).</span></span>

  <span data-ttu-id="b6ac2-428">Enquanto os threads gerenciados estão em execução, você pode ver qualquer número de coletas de lixo efêmero ocorrendo.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-428">While the managed threads are running, you can see any number of ephemeral garbage collections occurring.</span></span>

<a name="Triggered"></a>

### <a name="to-determine-what-triggered-a-garbage-collection"></a><span data-ttu-id="b6ac2-429">Para determinar o que disparou uma coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="b6ac2-429">To determine what triggered a garbage collection</span></span>

- <span data-ttu-id="b6ac2-430">No depurador do Visual Studio ou WinDbg com a extensão de depurador SOS carregada, digite o comando a seguir para mostrar todos os threads com suas pilhas de chamadas:</span><span class="sxs-lookup"><span data-stu-id="b6ac2-430">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command to show all the threads with their call stacks:</span></span>

  <span data-ttu-id="b6ac2-431">**~\*kb**</span><span class="sxs-lookup"><span data-stu-id="b6ac2-431">**~\*kb**</span></span>

  <span data-ttu-id="b6ac2-432">Esse comando exibe uma saída semelhante à seguinte.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-432">This command displays output similar to the following.</span></span>

  ```console
  0012f3b0 79ff0bf8 mscorwks!WKS::GCHeap::GarbageCollect
  0012f454 30002894 mscorwks!GCInterface::CollectGeneration+0xa4
  0012f490 79fa22bd fragment_ni!request.Main(System.String[])+0x48
  ```

  <span data-ttu-id="b6ac2-433">Se a coleta de lixo tiver sido causada por uma notificação de falta de memória do sistema operacional, a pilha de chamadas será semelhante, exceto pelo fato de que o thread é o thread do finalizador.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-433">If the garbage collection was caused by a low memory notification from the operating system, the call stack is similar, except that the thread is the finalizer thread.</span></span> <span data-ttu-id="b6ac2-434">O thread do finalizador obtém uma notificação assíncrona de memória insuficiente e induz à coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-434">The finalizer thread gets an asynchronous low memory notification and induces the garbage collection.</span></span>

  <span data-ttu-id="b6ac2-435">Se a coleta de lixo tiver sido causada pela alocação de memória, a pilha será exibida da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="b6ac2-435">If the garbage collection was caused by memory allocation, the stack appears as follows:</span></span>

  ```console
  0012f230 7a07c551 mscorwks!WKS::GCHeap::GarbageCollectGeneration
  0012f2b8 7a07cba8 mscorwks!WKS::gc_heap::try_allocate_more_space+0x1a1
  0012f2d4 7a07cefb mscorwks!WKS::gc_heap::allocate_more_space+0x18
  0012f2f4 7a02a51b mscorwks!WKS::GCHeap::Alloc+0x4b
  0012f310 7a02ae4c mscorwks!Alloc+0x60
  0012f364 7a030e46 mscorwks!FastAllocatePrimitiveArray+0xbd
  0012f424 300027f4 mscorwks!JIT_NewArr1+0x148
  000af70f 3000299f fragment_ni!request..ctor(Int32, Single)+0x20c
  0000002a 79fa22bd fragment_ni!request.Main(System.String[])+0x153
  ```

  <span data-ttu-id="b6ac2-436">Um auxiliar just-in-time (`JIT_New*`) eventualmente chama `GCHeap::GarbageCollectGeneration`.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-436">A just-in-time helper (`JIT_New*`) eventually calls `GCHeap::GarbageCollectGeneration`.</span></span> <span data-ttu-id="b6ac2-437">Se você determinar que as coletas de lixo de geração 2 são causadas por alocações, você deverá determinar quais objetos são coletados por uma coleta de lixo de geração 2 e como evitá-los.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-437">If you determine that generation 2 garbage collections are caused by allocations, you must determine which objects are collected by a generation 2 garbage collection and how to avoid them.</span></span> <span data-ttu-id="b6ac2-438">Ou seja, você deseja determinar a diferença entre o início e o término de uma coleta de lixo de geração 2 e os objetos que causaram a coleta de geração 2.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-438">That is, you want to determine the difference between the start and the end of a generation 2 garbage collection, and the objects that caused the generation 2 collection.</span></span>

  <span data-ttu-id="b6ac2-439">Por exemplo, digite o seguinte comando no depurador para mostrar o início de uma coleta de geração 2:</span><span class="sxs-lookup"><span data-stu-id="b6ac2-439">For example, type the following command in the debugger to show the beginning of a generation 2 collection:</span></span>

  <span data-ttu-id="b6ac2-440">**!dumpheap –stat**</span><span class="sxs-lookup"><span data-stu-id="b6ac2-440">**!dumpheap –stat**</span></span>

  <span data-ttu-id="b6ac2-441">Saída de exemplo (abreviada para mostrar os objetos que usam mais espaço):</span><span class="sxs-lookup"><span data-stu-id="b6ac2-441">Example output (abridged to show the objects that use the most space):</span></span>

  ```console
  79124228    31857      9862328 System.Object[]
  035f0384    25668     11601936 Toolkit.TlkPosition
  00155f80    21248     12256296      Free
  79103b6c   297003     13068132 System.Threading.ReaderWriterLock
  7a747ad4   708732     14174640 System.Collections.Specialized.HybridDictionary
  7a747c78   786498     15729960 System.Collections.Specialized.ListDictionary+DictionaryNode
  7a747bac   700298     19608344 System.Collections.Specialized.ListDictionary
  035f0ee4    89192     38887712 Toolkit.TlkOrder
  00fcae40     6193     44911636 WaveBasedStrategy.Tick_Snap[]
  7912c444    91616     71887080 System.Double[]
  791242ec    32451     82462728 System.Collections.Hashtable+bucket[]
  790fa3e0  2459154    112128436 System.String
  Total 6471774 objects
  ```

  <span data-ttu-id="b6ac2-442">Repita o comando ao final da geração 2:</span><span class="sxs-lookup"><span data-stu-id="b6ac2-442">Repeat the command at the end of generation 2:</span></span>

  <span data-ttu-id="b6ac2-443">**!dumpheap –stat**</span><span class="sxs-lookup"><span data-stu-id="b6ac2-443">**!dumpheap –stat**</span></span>

  <span data-ttu-id="b6ac2-444">Saída de exemplo (abreviada para mostrar os objetos que usam mais espaço):</span><span class="sxs-lookup"><span data-stu-id="b6ac2-444">Example output (abridged to show the objects that use the most space):</span></span>

  ```console
  79124228    26648      9314256 System.Object[]
  035f0384    25668     11601936 Toolkit.TlkPosition
  79103b6c   296770     13057880 System.Threading.ReaderWriterLock
  7a747ad4   708730     14174600 System.Collections.Specialized.HybridDictionary
  7a747c78   786497     15729940 System.Collections.Specialized.ListDictionary+DictionaryNode
  7a747bac   700298     19608344 System.Collections.Specialized.ListDictionary
  00155f80    13806     34007212      Free
  035f0ee4    89187     38885532 Toolkit.TlkOrder
  00fcae40     6193     44911636 WaveBasedStrategy.Tick_Snap[]
  791242ec    32370     82359768 System.Collections.Hashtable+bucket[]
  790fa3e0  2440020    111341808 System.String
  Total 6417525 objects
  ```

  <span data-ttu-id="b6ac2-445">Os objetos `double[]` desapareceram do final da saída, o que significa que eles foram coletados.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-445">The `double[]` objects disappeared from the end of the output, which means that they were collected.</span></span> <span data-ttu-id="b6ac2-446">Esses objetos correspondem a aproximadamente 70 MB.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-446">These objects account for approximately 70 MB.</span></span> <span data-ttu-id="b6ac2-447">Os objetos restantes não mudaram muito.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-447">The remaining objects did not change much.</span></span> <span data-ttu-id="b6ac2-448">Sendo assim, esses objetos `double[]` foram o motivo pelo qual essa coleta de lixo de geração 2 ocorreu.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-448">Therefore, these `double[]` objects were the reason why this generation 2 garbage collection occurred.</span></span> <span data-ttu-id="b6ac2-449">A próxima etapa é determinar por que os objetos `double[]` estão lá e por que eles morreram.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-449">Your next step is to determine why the `double[]` objects are there and why they died.</span></span> <span data-ttu-id="b6ac2-450">Você pode perguntar ao desenvolvedor de código a origem desses objetos ou então você pode usar o comando **gcroot**.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-450">You can ask the code developer where these objects came from, or you can use the **gcroot** command.</span></span>

<a name="HighCPU"></a>

### <a name="to-determine-whether-high-cpu-usage-is-caused-by-garbage-collection"></a><span data-ttu-id="b6ac2-451">Para determinar se o alto uso da CPU é causado pela coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="b6ac2-451">To determine whether high CPU usage is caused by garbage collection</span></span>

- <span data-ttu-id="b6ac2-452">Correlacionar o valor do contador de desempenho de memória de `% Time in GC` com o tempo de processamento.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-452">Correlate the `% Time in GC` memory performance counter value with the process time.</span></span>

  <span data-ttu-id="b6ac2-453">Se o valor de `% Time in GC` subir ao mesmo tempo que o tempo de processamento, isso significará que a coleta de lixo está causando um alto uso da CPU.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-453">If the `% Time in GC` value spikes at the same time as process time, garbage collection is causing a high CPU usage.</span></span> <span data-ttu-id="b6ac2-454">Caso contrário, crie o perfil do aplicativo para encontrar o local de ocorrência do alto uso.</span><span class="sxs-lookup"><span data-stu-id="b6ac2-454">Otherwise, profile the application to find where the high usage is occurring.</span></span>

## <a name="see-also"></a><span data-ttu-id="b6ac2-455">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b6ac2-455">See also</span></span>

- [<span data-ttu-id="b6ac2-456">Coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="b6ac2-456">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
