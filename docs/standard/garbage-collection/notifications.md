---
title: Notificações sobre a coleta de lixo
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- garbage collection, notifications
ms.assetid: e12d8e74-31e3-4035-a87d-f3e66f0a9b89
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 10f947fc44e69368e30614e0b41eaf7c73fb6563
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44084943"
---
# <a name="garbage-collection-notifications"></a><span data-ttu-id="0603d-102">Notificações sobre a coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="0603d-102">Garbage Collection Notifications</span></span>
<span data-ttu-id="0603d-103">Há situações em que uma coleta de lixo completa (ou seja, uma coleta de geração 2) pelo common language runtime pode afetar negativamente o desempenho.</span><span class="sxs-lookup"><span data-stu-id="0603d-103">There are situations in which a full garbage collection (that is, a generation 2 collection) by the common language runtime may adversely affect performance.</span></span> <span data-ttu-id="0603d-104">Isso pode ser um problema, especialmente com servidores que processam grandes volumes de solicitações. Nesse caso, uma coleta de lixo longa pode fazer com que o tempo limite de uma solicitação seja atingido. Para impedir que uma coleta completa ocorra durante um período crítico, você pode ser notificado que uma coleta de lixo completa está se aproximando e, em seguida, tomar medidas para redirecionar a carga de trabalho para outra instância do servidor.</span><span class="sxs-lookup"><span data-stu-id="0603d-104">This can be an issue particularly with servers that process large volumes of requests; in this case, a long garbage collection can cause a request time-out. To prevent a full collection from occurring during a critical period, you can be notified that a full garbage collection is approaching and then take action to redirect the workload to another server instance.</span></span> <span data-ttu-id="0603d-105">Você também pode induzir uma coleta por conta própria, desde que a instância atual do servidor não precise processar solicitações.</span><span class="sxs-lookup"><span data-stu-id="0603d-105">You can also induce a collection yourself, provided that the current server instance does not need to process requests.</span></span>  
  
 <span data-ttu-id="0603d-106">O método <xref:System.GC.RegisterForFullGCNotification%2A> registra uma notificação para ser gerado quando o tempo de execução detectar que uma coleta de lixo completa está se aproximando.</span><span class="sxs-lookup"><span data-stu-id="0603d-106">The <xref:System.GC.RegisterForFullGCNotification%2A> method registers for a notification to be raised when the runtime senses that a full garbage collection is approaching.</span></span> <span data-ttu-id="0603d-107">Essa notificação é composta por duas partes: quando a coleta de lixo completa está se aproximando e quando a coleta de lixo completa for concluída.</span><span class="sxs-lookup"><span data-stu-id="0603d-107">There are two parts to this notification: when the full garbage collection is approaching and when the full garbage collection has completed.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="0603d-108">Apenas o bloqueio de coletas de lixo geram notificações.</span><span class="sxs-lookup"><span data-stu-id="0603d-108">Only blocking garbage collections raise notifications.</span></span> <span data-ttu-id="0603d-109">Quando o elemento de configuração [\<gcConcurrent>](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) estiver habilitado, as coletas de lixo em segundo plano não gerarão notificações.</span><span class="sxs-lookup"><span data-stu-id="0603d-109">When the [\<gcConcurrent>](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) configuration element is enabled, background garbage collections will not raise notifications.</span></span>  
  
 <span data-ttu-id="0603d-110">Para determinar quando uma notificação foi gerada, use os métodos <xref:System.GC.WaitForFullGCApproach%2A> e <xref:System.GC.WaitForFullGCComplete%2A>.</span><span class="sxs-lookup"><span data-stu-id="0603d-110">To determine when a notification has been raised, use the <xref:System.GC.WaitForFullGCApproach%2A> and <xref:System.GC.WaitForFullGCComplete%2A> methods.</span></span> <span data-ttu-id="0603d-111">Normalmente, você pode usar esses métodos em um loop `while` para obter continuamente uma enumeração <xref:System.GCNotificationStatus> que mostra o status da notificação.</span><span class="sxs-lookup"><span data-stu-id="0603d-111">Typically, you use these methods in a `while` loop to continually obtain a <xref:System.GCNotificationStatus> enumeration that shows the status of the notification.</span></span> <span data-ttu-id="0603d-112">Se esse valor for <xref:System.GCNotificationStatus.Succeeded>, você pode fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="0603d-112">If that value is <xref:System.GCNotificationStatus.Succeeded>, you can do the following:</span></span>  
  
-   <span data-ttu-id="0603d-113">Em resposta a uma notificação obtida com o método <xref:System.GC.WaitForFullGCApproach%2A>, você pode redirecionar a carga de trabalho e, possivelmente, induzir uma coleção por conta própria.</span><span class="sxs-lookup"><span data-stu-id="0603d-113">In response to a notification obtained with the <xref:System.GC.WaitForFullGCApproach%2A> method, you can redirect the workload and possibly induce a collection yourself.</span></span>  
  
-   <span data-ttu-id="0603d-114">Em resposta a uma notificação obtida com o método <xref:System.GC.WaitForFullGCComplete%2A>, você pode tornar a instância atual do servidor disponível para processar solicitações novamente.</span><span class="sxs-lookup"><span data-stu-id="0603d-114">In response to a notification obtained with the <xref:System.GC.WaitForFullGCComplete%2A> method, you can make the current server instance available to process requests again.</span></span> <span data-ttu-id="0603d-115">Você também pode coletar informações.</span><span class="sxs-lookup"><span data-stu-id="0603d-115">You can also gather information.</span></span> <span data-ttu-id="0603d-116">Por exemplo, você pode usar o método <xref:System.GC.CollectionCount%2A> para registrar o número de coleções.</span><span class="sxs-lookup"><span data-stu-id="0603d-116">For example, you can use the <xref:System.GC.CollectionCount%2A> method to record the number of collections.</span></span>  
  
 <span data-ttu-id="0603d-117">Os métodos <xref:System.GC.WaitForFullGCApproach%2A> e <xref:System.GC.WaitForFullGCComplete%2A> são projetados para trabalhar juntos.</span><span class="sxs-lookup"><span data-stu-id="0603d-117">The <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods are designed to work together.</span></span> <span data-ttu-id="0603d-118">Usar um sem o outro pode produzir resultados indeterminados.</span><span class="sxs-lookup"><span data-stu-id="0603d-118">Using one without the other can produce indeterminate results.</span></span>  
  
## <a name="full-garbage-collection"></a><span data-ttu-id="0603d-119">Coleta de lixo completa</span><span class="sxs-lookup"><span data-stu-id="0603d-119">Full Garbage Collection</span></span>  
 <span data-ttu-id="0603d-120">O tempo de execução resultará em uma coleta de lixo completa quando qualquer um dos cenários a seguir for verdadeiro:</span><span class="sxs-lookup"><span data-stu-id="0603d-120">The runtime causes a full garbage collection when any of the following scenarios are true:</span></span>  
  
-   <span data-ttu-id="0603d-121">Foi promovida memória suficiente para a geração 2 para gerar a próxima coleta de geração 2.</span><span class="sxs-lookup"><span data-stu-id="0603d-121">Enough memory has been promoted into generation 2 to cause the next generation 2 collection.</span></span>  
  
-   <span data-ttu-id="0603d-122">Foi promovida memória suficiente para o heap de objeto grande para gerar a próxima coleta de geração 2.</span><span class="sxs-lookup"><span data-stu-id="0603d-122">Enough memory has been promoted into the large object heap to cause the next generation 2 collection.</span></span>  
  
-   <span data-ttu-id="0603d-123">Outros fatores escalam uma coleta de geração 1 para uma coleta de geração 2.</span><span class="sxs-lookup"><span data-stu-id="0603d-123">A collection of generation 1 is escalated to a collection of generation 2 due to other factors.</span></span>  
  
 <span data-ttu-id="0603d-124">Os limites que você especificar no método <xref:System.GC.RegisterForFullGCNotification%2A> serão aplicados aos primeiros dois cenários.</span><span class="sxs-lookup"><span data-stu-id="0603d-124">The thresholds you specify in the <xref:System.GC.RegisterForFullGCNotification%2A> method apply to the first two scenarios.</span></span> <span data-ttu-id="0603d-125">No entanto, no primeiro cenário, você nem sempre receberá a notificação no momento proporcional aos valores de limite que você especificar por dois motivos:</span><span class="sxs-lookup"><span data-stu-id="0603d-125">However, in the first scenario you will not always receive the notification at the time proportional to the threshold values you specify for two reasons:</span></span>  
  
-   <span data-ttu-id="0603d-126">O tempo de execução não verifica todas as alocações de objeto pequeno (por motivos de desempenho).</span><span class="sxs-lookup"><span data-stu-id="0603d-126">The runtime does not check each small object allocation (for performance reasons).</span></span>  
  
-   <span data-ttu-id="0603d-127">Somente as coletas da geração 1 promovem a memória na geração 2.</span><span class="sxs-lookup"><span data-stu-id="0603d-127">Only generation 1 collections promote memory into generation 2.</span></span>  
  
 <span data-ttu-id="0603d-128">O terceiro cenário também contribui para a incerteza de quando você receberá a notificação.</span><span class="sxs-lookup"><span data-stu-id="0603d-128">The third scenario also contributes to the uncertainty of when you will receive the notification.</span></span> <span data-ttu-id="0603d-129">Embora não seja uma garantia, essa é uma maneira útil de reduzir os efeitos de uma coleta de lixo completa inoportuna ao redirecionar as solicitações durante esse período ou você mesmo induzir a coleta para quando ela puder ser melhor hospedada.</span><span class="sxs-lookup"><span data-stu-id="0603d-129">Although this is not a guarantee, it does prove to be a useful way to mitigate the effects of an inopportune full garbage collection by redirecting the requests during this time or inducing the collection yourself when it can be better accommodated.</span></span>  
  
## <a name="notification-threshold-parameters"></a><span data-ttu-id="0603d-130">Parâmetros de limite de notificação</span><span class="sxs-lookup"><span data-stu-id="0603d-130">Notification Threshold Parameters</span></span>  
 <span data-ttu-id="0603d-131">O método <xref:System.GC.RegisterForFullGCNotification%2A> tem dois parâmetros para especificar os valores de limite do heap de objeto grande e dos objetos de geração 2.</span><span class="sxs-lookup"><span data-stu-id="0603d-131">The <xref:System.GC.RegisterForFullGCNotification%2A> method has two parameters to specify the threshold values of the generation 2 objects and the large object heap.</span></span> <span data-ttu-id="0603d-132">Quando esses valores forem atendidos, uma notificação de coleta de lixo deverá ser gerada.</span><span class="sxs-lookup"><span data-stu-id="0603d-132">When those values are met, a garbage collection notification should be raised.</span></span> <span data-ttu-id="0603d-133">A tabela a seguir descreve esses parâmetros.</span><span class="sxs-lookup"><span data-stu-id="0603d-133">The following table describes these parameters.</span></span>  
  
|<span data-ttu-id="0603d-134">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="0603d-134">Parameter</span></span>|<span data-ttu-id="0603d-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="0603d-135">Description</span></span>|  
|---------------|-----------------|  
|`maxGenerationThreshold`|<span data-ttu-id="0603d-136">Um número entre 1 e 99 que especifica quando a notificação deve ser gerada com base nos objetos promovidos na geração 2.</span><span class="sxs-lookup"><span data-stu-id="0603d-136">A number between 1 and 99 that specifies when the notification should be raised based on the objects promoted in generation 2.</span></span>|  
|`largeObjectHeapThreshold`|<span data-ttu-id="0603d-137">Um número entre 1 e 99 que especifica quando a notificação deve ser gerada com base nos objetos alocados no heap de objetos grandes.</span><span class="sxs-lookup"><span data-stu-id="0603d-137">A number between 1 and 99 that specifies when the notification should be raised based on the objects that are allocated in the large object heap.</span></span>|  
  
 <span data-ttu-id="0603d-138">Se você especificar um valor muito alto, a probabilidade de receber uma notificação será muito elevada. No entanto, pode demorar muito até que o tempo de execução gere uma coleta.</span><span class="sxs-lookup"><span data-stu-id="0603d-138">If you specify a value that is too high, there is a high probability that you will receive a notification, but it could be too long a period to wait before the runtime causes a collection.</span></span> <span data-ttu-id="0603d-139">Se você mesmo induzir uma coleta, poderá recuperar mais objetos que seriam recuperados se o tempo de execução gerasse a coleta.</span><span class="sxs-lookup"><span data-stu-id="0603d-139">If you induce a collection yourself, you may reclaim more objects than would be reclaimed if the runtime causes the collection.</span></span>  
  
 <span data-ttu-id="0603d-140">Se você especificar um valor muito baixo, o tempo de execução poderá gerar a coleta antes de você ter tido tempo suficiente para ser notificado.</span><span class="sxs-lookup"><span data-stu-id="0603d-140">If you specify a value that is too low, the runtime may cause the collection before you have had sufficient time to be notified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0603d-141">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0603d-141">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="0603d-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="0603d-142">Description</span></span>  
 <span data-ttu-id="0603d-143">No exemplo a seguir, um grupo de serviço de servidores controla as solicitações da Web recebidas.</span><span class="sxs-lookup"><span data-stu-id="0603d-143">In the following example, a group of servers service incoming Web requests.</span></span> <span data-ttu-id="0603d-144">Para simular a carga de trabalho de processamento de solicitações, matrizes de bytes são adicionadas a uma coleta <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="0603d-144">To simulate the workload of processing requests, byte arrays are added to a <xref:System.Collections.Generic.List%601> collection.</span></span> <span data-ttu-id="0603d-145">Cada servidor registra uma notificação de coleta de lixo e, em seguida, inicia um thread no método de usuário `WaitForFullGCProc` para monitorar continuamente a enumeração <xref:System.GCNotificationStatus> que é retornada pelos métodos <xref:System.GC.WaitForFullGCApproach%2A> e <xref:System.GC.WaitForFullGCComplete%2A>.</span><span class="sxs-lookup"><span data-stu-id="0603d-145">Each server registers for a garbage collection notification and then starts a thread on the `WaitForFullGCProc` user method to continuously monitor the <xref:System.GCNotificationStatus> enumeration that is returned by the <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods.</span></span>  
  
 <span data-ttu-id="0603d-146">Os métodos <xref:System.GC.WaitForFullGCApproach%2A> e <xref:System.GC.WaitForFullGCComplete%2A> chamam seus respectivos métodos de usuário de manipulação de eventos quando uma notificação é gerada:</span><span class="sxs-lookup"><span data-stu-id="0603d-146">The <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods call their respective event-handling user methods when a notification is raised:</span></span>  
  
-   `OnFullGCApproachNotify`  
  
     <span data-ttu-id="0603d-147">Este método chama o método de usuário `RedirectRequests` que instrui o servidor de enfileiramento de solicitações a suspender o envio de solicitações ao servidor.</span><span class="sxs-lookup"><span data-stu-id="0603d-147">This method calls the `RedirectRequests` user method, which instructs the request queuing server to suspend sending requests to the server.</span></span> <span data-ttu-id="0603d-148">Isso é simulado definindo a variável de nível de classe `bAllocate` como `false` para que nenhum outro objeto seja alocado.</span><span class="sxs-lookup"><span data-stu-id="0603d-148">This is simulated by setting the class-level variable `bAllocate` to `false` so that no more objects are allocated.</span></span>  
  
     <span data-ttu-id="0603d-149">Em seguida, o método de usuário `FinishExistingRequests` é chamado para concluir o processamento das solicitações pendentes do servidor.</span><span class="sxs-lookup"><span data-stu-id="0603d-149">Next, the `FinishExistingRequests` user method is called to finish processing the pending server requests.</span></span> <span data-ttu-id="0603d-150">Isso é simulado desmarcando a coleta <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="0603d-150">This is simulated by clearing the <xref:System.Collections.Generic.List%601> collection.</span></span>  
  
     <span data-ttu-id="0603d-151">Por fim, como a carga de trabalho é leve, uma coleta de lixo é induzida.</span><span class="sxs-lookup"><span data-stu-id="0603d-151">Finally, a garbage collection is induced because the workload is light.</span></span>  
  
-   `OnFullGCCompleteNotify`  
  
     <span data-ttu-id="0603d-152">Este método chama o método de usuário `AcceptRequests` para retomar a aceitar de solicitações já que o servidor não está mais suscetível à coleta de lixo completa.</span><span class="sxs-lookup"><span data-stu-id="0603d-152">This method calls the user method `AcceptRequests` to resume accepting requests because the server is no longer susceptible to a full garbage collection.</span></span> <span data-ttu-id="0603d-153">Essa ação é simulada através da definição da variável `bAllocate` como `true` para que objetos possam continuar sendo adicionados à coleta <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="0603d-153">This action is simulated by setting the `bAllocate` variable to `true` so that objects can resume being added to the <xref:System.Collections.Generic.List%601> collection.</span></span>  
  
 <span data-ttu-id="0603d-154">O código a seguir contém o método `Main` do exemplo.</span><span class="sxs-lookup"><span data-stu-id="0603d-154">The following code contains the `Main` method of the example.</span></span>  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 <span data-ttu-id="0603d-155">O código a seguir contém o método de usuário `WaitForFullGCProc` que contém um loop while contínuo para verificar se há notificações de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="0603d-155">The following code contains the `WaitForFullGCProc` user method, that contains a continuous while loop to check for garbage collection notifications.</span></span>  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 <span data-ttu-id="0603d-156">O código a seguir contém o método `OnFullGCApproachNotify` como chamado no</span><span class="sxs-lookup"><span data-stu-id="0603d-156">The following code contains the `OnFullGCApproachNotify` method as called from the</span></span>  
  
 <span data-ttu-id="0603d-157">Método `WaitForFullGCProc`.</span><span class="sxs-lookup"><span data-stu-id="0603d-157">`WaitForFullGCProc` method.</span></span>  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 <span data-ttu-id="0603d-158">O código a seguir contém o método `OnFullGCApproachComplete` como chamado no</span><span class="sxs-lookup"><span data-stu-id="0603d-158">The following code contains the `OnFullGCApproachComplete` method as called from the</span></span>  
  
 <span data-ttu-id="0603d-159">Método `WaitForFullGCProc`.</span><span class="sxs-lookup"><span data-stu-id="0603d-159">`WaitForFullGCProc` method.</span></span>  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 <span data-ttu-id="0603d-160">O código a seguir contém os métodos de usuário que são chamados nos métodos `OnFullGCApproachNotify` e `OnFullGCCompleteNotify`.</span><span class="sxs-lookup"><span data-stu-id="0603d-160">The following code contains the user methods that are called from the `OnFullGCApproachNotify` and `OnFullGCCompleteNotify` methods.</span></span> <span data-ttu-id="0603d-161">Os métodos de usuário redirecionam as solicitações, concluem as solicitações existentes e, em seguida, retomam solicitações após a conclusão da coleta de lixo completa.</span><span class="sxs-lookup"><span data-stu-id="0603d-161">The user methods redirect requests, finish existing requests, and then resume requests after a full garbage collection has occurred.</span></span>  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 <span data-ttu-id="0603d-162">O exemplo de código completo é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="0603d-162">The entire code sample is as follows:</span></span>  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0603d-163">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0603d-163">See also</span></span>

- [<span data-ttu-id="0603d-164">Coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="0603d-164">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
