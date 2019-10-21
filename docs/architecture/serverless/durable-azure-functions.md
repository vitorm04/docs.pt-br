---
title: Azure Functions duráveis – aplicativos sem servidor
description: As Azure Functions duráveis estendem o tempo de execução de Azure Functions para habilitar fluxos de trabalho com estado no código.
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 2c0ad086640409ac187c3aa882add4d6b39b6ff9
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522857"
---
# <a name="durable-azure-functions"></a><span data-ttu-id="fff80-103">Funções duráveis do Azure</span><span class="sxs-lookup"><span data-stu-id="fff80-103">Durable Azure functions</span></span>

<span data-ttu-id="fff80-104">Ao criar aplicativos sem servidor com o Azure Functions, suas operações normalmente serão projetadas para serem executadas de maneira sem monitoração de estado.</span><span class="sxs-lookup"><span data-stu-id="fff80-104">When creating serverless applications with Azure Functions, your operations will typically be designed to run in a stateless manner.</span></span> <span data-ttu-id="fff80-105">A razão para essa escolha de design é porque, à medida que a plataforma é dimensionada, fica difícil saber em quais servidores o código está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="fff80-105">The reason for this design choice is because as the platform scales, it becomes difficult to know what servers the code is running on.</span></span> <span data-ttu-id="fff80-106">Também se torna difícil saber quantas instâncias estão ativas em qualquer ponto determinado.</span><span class="sxs-lookup"><span data-stu-id="fff80-106">It also becomes difficult to know how many instances are active at any given point.</span></span> <span data-ttu-id="fff80-107">No entanto, há classes de aplicativos que exigem que o estado atual de um processo seja conhecido.</span><span class="sxs-lookup"><span data-stu-id="fff80-107">However, there are classes of applications that require the current state of a process to be known.</span></span> <span data-ttu-id="fff80-108">Considere o processo de envio de um pedido para uma loja online.</span><span class="sxs-lookup"><span data-stu-id="fff80-108">Consider the process of submitting an order to an online store.</span></span> <span data-ttu-id="fff80-109">A operação de check-out pode ser um fluxo de trabalho composto por várias operações que precisam saber o estado do processo.</span><span class="sxs-lookup"><span data-stu-id="fff80-109">The checkout operation might be a workflow that is composed of multiple operations that need to know the state of the process.</span></span> <span data-ttu-id="fff80-110">Essas informações podem incluir o inventário do produto, se o cliente tiver créditos de sua conta e também os resultados do processamento do cartão de crédito.</span><span class="sxs-lookup"><span data-stu-id="fff80-110">Such information may include the product inventory, if the customer has any credits on their account, and also the results of processing the credit card.</span></span> <span data-ttu-id="fff80-111">Essas operações podem ser facilmente seus próprios fluxos de trabalho internos ou até mesmo serviços de sistemas de terceiros.</span><span class="sxs-lookup"><span data-stu-id="fff80-111">These operations could easily be their own internal workflows or even services from third-party systems.</span></span>

<span data-ttu-id="fff80-112">Existem vários padrões atualmente que ajudam na coordenação do estado do aplicativo entre sistemas internos e externos.</span><span class="sxs-lookup"><span data-stu-id="fff80-112">Various patterns exist today that assist with the coordination of application state between internal and external systems.</span></span> <span data-ttu-id="fff80-113">É comum entrar em soluções que dependem de sistemas de enfileiramento centralizados, repositórios de chave-valor distribuído ou bancos de dados compartilhados para gerenciar esse estado.</span><span class="sxs-lookup"><span data-stu-id="fff80-113">It's common to come across solutions that rely on centralized queuing systems, distributed key-value stores, or shared databases to manage that state.</span></span> <span data-ttu-id="fff80-114">No entanto, esses são todos os recursos adicionais que agora precisam ser provisionados e gerenciados.</span><span class="sxs-lookup"><span data-stu-id="fff80-114">However, these are all additional resources that now need to be provisioned and managed.</span></span> <span data-ttu-id="fff80-115">Em um ambiente sem servidor, seu código pode se tornar complicado tentando coordenar esses recursos manualmente.</span><span class="sxs-lookup"><span data-stu-id="fff80-115">In a serverless environment, your code could become cumbersome trying to coordinate with these resources manually.</span></span> <span data-ttu-id="fff80-116">Azure Functions oferece uma alternativa para a criação de funções com estado chamada Durable Functions.</span><span class="sxs-lookup"><span data-stu-id="fff80-116">Azure Functions offers an alternative for creating stateful functions called Durable Functions.</span></span>

<span data-ttu-id="fff80-117">Durable Functions é uma extensão para o tempo de execução Azure Functions que permite a definição de fluxos de trabalho com estado no código.</span><span class="sxs-lookup"><span data-stu-id="fff80-117">Durable Functions is an extension to the Azure Functions runtime that enables the definition of stateful workflows in code.</span></span> <span data-ttu-id="fff80-118">Ao dividir os fluxos de trabalho em atividades, a extensão de Durable Functions pode gerenciar o estado, criar pontos de verificação de progresso e manipular a distribuição de chamadas de função entre servidores.</span><span class="sxs-lookup"><span data-stu-id="fff80-118">By breaking down workflows into activities, the Durable Functions extension can manage state, create progress checkpoints, and handle the distribution of function calls across servers.</span></span> <span data-ttu-id="fff80-119">Em segundo plano, ele faz uso de uma conta de armazenamento do Azure para manter o histórico de execução, agendar funções de atividade e recuperar respostas.</span><span class="sxs-lookup"><span data-stu-id="fff80-119">In the background, it makes use of an Azure Storage account to persist execution history, schedule activity functions and retrieve responses.</span></span> <span data-ttu-id="fff80-120">O código sem servidor nunca deve interagir com informações persistentes nessa conta de armazenamento e normalmente não é algo com o qual os desenvolvedores precisam interagir.</span><span class="sxs-lookup"><span data-stu-id="fff80-120">Your serverless code should never interact with persisted information in that storage account, and is typically not something with which developers need to interact.</span></span>

## <a name="triggering-a-stateful-workflow"></a><span data-ttu-id="fff80-121">Disparando um fluxo de trabalho com estado</span><span class="sxs-lookup"><span data-stu-id="fff80-121">Triggering a stateful workflow</span></span>

<span data-ttu-id="fff80-122">Fluxos de trabalho com estado no Durable Functions podem ser divididos em dois componentes intrínsecos; gatilhos de orquestração e de atividade.</span><span class="sxs-lookup"><span data-stu-id="fff80-122">Stateful workflows in Durable Functions can be broken down into two intrinsic components; orchestration and activity triggers.</span></span> <span data-ttu-id="fff80-123">Gatilhos e associações são componentes principais usados pelo Azure Functions para permitir que suas funções sem servidor sejam notificadas quando iniciar, receber entrada e retornar resultados.</span><span class="sxs-lookup"><span data-stu-id="fff80-123">Triggers and bindings are core components used by Azure Functions to enable your serverless functions to be notified when to start, receive input, and return results.</span></span>

### <a name="working-with-the-orchestration-client"></a><span data-ttu-id="fff80-124">Trabalhando com o cliente de orquestração</span><span class="sxs-lookup"><span data-stu-id="fff80-124">Working with the Orchestration client</span></span>

<span data-ttu-id="fff80-125">As orquestrações são exclusivas em comparação com outros estilos de operações disparadas no Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="fff80-125">Orchestrations are unique when compared to other styles of triggered operations in Azure Functions.</span></span> <span data-ttu-id="fff80-126">Durable Functions permite a execução de funções que podem levar horas ou até mesmo dias para serem concluídas.</span><span class="sxs-lookup"><span data-stu-id="fff80-126">Durable Functions enables the execution of functions that may take hours or even days to complete.</span></span> <span data-ttu-id="fff80-127">Esse tipo de comportamento vem com a necessidade de verificar o status de uma orquestração em execução, encerrar preempção ou enviar notificações de eventos externos.</span><span class="sxs-lookup"><span data-stu-id="fff80-127">That type of behavior comes with the need to able to check the status of a running orchestration, preemptively terminate, or send notifications of external events.</span></span>

<span data-ttu-id="fff80-128">Para esses casos, a extensão Durable Functions fornece a classe `DurableOrchestrationClient` que permite que você interaja com funções orquestradas.</span><span class="sxs-lookup"><span data-stu-id="fff80-128">For such cases, the Durable Functions extension provides the `DurableOrchestrationClient` class that allows you to interact with orchestrated functions.</span></span> <span data-ttu-id="fff80-129">Você obtém acesso ao cliente de orquestração usando a associação de `OrchestrationClientAttribute`.</span><span class="sxs-lookup"><span data-stu-id="fff80-129">You get access to the orchestration client by using the `OrchestrationClientAttribute` binding.</span></span> <span data-ttu-id="fff80-130">Em geral, você incluiria esse atributo com outro tipo de gatilho, como um `HttpTrigger` ou `ServiceBusTrigger`.</span><span class="sxs-lookup"><span data-stu-id="fff80-130">Generally, you would include this attribute with another trigger type, such as an `HttpTrigger` or `ServiceBusTrigger`.</span></span> <span data-ttu-id="fff80-131">Depois que a função de origem tiver sido disparada, o cliente de orquestração poderá ser usado para iniciar uma função de orquestrador.</span><span class="sxs-lookup"><span data-stu-id="fff80-131">Once the source function has been triggered, the orchestration client can be used to start an orchestrator function.</span></span>

```csharp
[FunctionName("KickOff")]
public static async Task<HttpResponseMessage> Run(
    [HttpTrigger(AuthorizationLevel.Function, "POST")]HttpRequestMessage req,
    [OrchestrationClient ] DurableOrchestrationClient<orchestrationClient>)
{
    OrderRequestData data = await req.Content.ReadAsAsync<OrderRequestData>();

    string instanceId = await orchestrationClient.StartNewAsync("PlaceOrder", data);

    return orchestrationClient.CreateCheckStatusResponse(req, instanceId);
}
```

### <a name="the-orchestrator-function"></a><span data-ttu-id="fff80-132">A função de orquestrador</span><span class="sxs-lookup"><span data-stu-id="fff80-132">The orchestrator function</span></span>

<span data-ttu-id="fff80-133">Anotar uma função com o OrchestrationTriggerAttribute em Azure Functions marca que funciona como uma função de orquestrador.</span><span class="sxs-lookup"><span data-stu-id="fff80-133">Annotating a function with the OrchestrationTriggerAttribute in Azure Functions marks that function as an orchestrator function.</span></span> <span data-ttu-id="fff80-134">É responsável por gerenciar as várias atividades que compõem seu fluxo de trabalho com estado.</span><span class="sxs-lookup"><span data-stu-id="fff80-134">It's responsible for managing the various activities that make up your stateful workflow.</span></span>

<span data-ttu-id="fff80-135">As funções de orquestrador não podem fazer uso de associações diferentes de OrchestrationTriggerAttribute.</span><span class="sxs-lookup"><span data-stu-id="fff80-135">Orchestrator functions are unable to make use of bindings other than the OrchestrationTriggerAttribute.</span></span> <span data-ttu-id="fff80-136">Esse atributo só pode ser usado com um tipo de parâmetro de DurableOrchestrationContext.</span><span class="sxs-lookup"><span data-stu-id="fff80-136">This attribute can only be used with a parameter type of DurableOrchestrationContext.</span></span> <span data-ttu-id="fff80-137">Nenhuma outra entrada pode ser usada, pois a desserialização de entradas na assinatura de função não tem suporte.</span><span class="sxs-lookup"><span data-stu-id="fff80-137">No other inputs can be used since deserialization of inputs in the function signature isn't supported.</span></span> <span data-ttu-id="fff80-138">Para obter as entradas fornecidas pelo cliente de orquestração, o método de \> de \<T de entrada deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="fff80-138">To get inputs provided by the orchestration client, the GetInput\<T\> method must be used.</span></span>

<span data-ttu-id="fff80-139">Além disso, os tipos de retorno das funções de orquestração devem ser void, Task ou um valor serializável JSON.</span><span class="sxs-lookup"><span data-stu-id="fff80-139">Also, the return types of orchestration functions must be either void, Task, or a JSON serializable value.</span></span>

> <span data-ttu-id="fff80-140">*O código de tratamento de erros foi deixado para fins de brevidade*</span><span class="sxs-lookup"><span data-stu-id="fff80-140">*Error handling code has been left out for brevity*</span></span>

```csharp
[FunctionName("PlaceOrder")]
public static async Task<string> PlaceOrder([OrchestrationTrigger] DurableOrchestrationContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    await context.CallActivityAsync<bool>("CheckAndReserveInventory", orderData);
    await context.CallActivityAsync<string>("ProcessPayment", orderData);

    string trackingNumber = await context.CallActivityAsync<string>("ScheduleShipping", orderData);
    await context.CallActivityAsync<string>("EmailCustomer", trackingNumber);

    return trackingNumber;
}
```

<span data-ttu-id="fff80-141">Várias instâncias de uma orquestração podem ser iniciadas e executadas ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="fff80-141">Multiple instances of an orchestration can be started and running at the same time.</span></span> <span data-ttu-id="fff80-142">Chamar o método `StartNewAsync` na `DurableOrchestrationClient` inicia uma nova instância da orquestração.</span><span class="sxs-lookup"><span data-stu-id="fff80-142">Calling the `StartNewAsync` method on the `DurableOrchestrationClient` launches a new instance of the orchestration.</span></span> <span data-ttu-id="fff80-143">O método retorna um `Task<string>` que é concluído quando a orquestração é iniciada.</span><span class="sxs-lookup"><span data-stu-id="fff80-143">The method returns a `Task<string>` that completes when the orchestration has started.</span></span> <span data-ttu-id="fff80-144">Uma exceção do tipo `TimeoutException` será lançada se a orquestração não tiver começado dentro de 30 segundos.</span><span class="sxs-lookup"><span data-stu-id="fff80-144">An exception of type `TimeoutException` gets thrown if the orchestration hasn't started within 30 seconds.</span></span>

<span data-ttu-id="fff80-145">O `Task<string>` concluído de `StartNewAsync` deve conter a ID exclusiva da instância de orquestração.</span><span class="sxs-lookup"><span data-stu-id="fff80-145">The completed `Task<string>` from `StartNewAsync` should contain the unique ID of the orchestration instance.</span></span> <span data-ttu-id="fff80-146">Essa ID de instância pode ser usada para invocar operações nessa orquestração específica.</span><span class="sxs-lookup"><span data-stu-id="fff80-146">This instance ID can be used to invoke operations on that specific orchestration.</span></span> <span data-ttu-id="fff80-147">A orquestração pode ser consultada para o status ou notificações de eventos enviadas.</span><span class="sxs-lookup"><span data-stu-id="fff80-147">The orchestration can be queried for the status or sent event notifications.</span></span>

### <a name="the-activity-functions"></a><span data-ttu-id="fff80-148">As funções de atividade</span><span class="sxs-lookup"><span data-stu-id="fff80-148">The activity functions</span></span>

<span data-ttu-id="fff80-149">Funções de atividade são operações discretas que são compostas em uma função de orquestração para criar o fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="fff80-149">Activity functions are the discrete operations that get composed together within an orchestration function to create the workflow.</span></span> <span data-ttu-id="fff80-150">Aqui está o local em que a maior parte do trabalho real ocorre.</span><span class="sxs-lookup"><span data-stu-id="fff80-150">Here is where most of actual work would take place.</span></span> <span data-ttu-id="fff80-151">Eles representam a lógica de negócios, os processos de longa duração e as peças de quebra-cabeça para uma solução maior.</span><span class="sxs-lookup"><span data-stu-id="fff80-151">They represent the business logic, long running processes, and the puzzle pieces to a larger solution.</span></span>

<span data-ttu-id="fff80-152">O `ActivityTriggerAttribute` é usado para anotar um parâmetro de função do tipo `DurableActivityContext`.</span><span class="sxs-lookup"><span data-stu-id="fff80-152">The `ActivityTriggerAttribute` is used to annotate a function parameter of type `DurableActivityContext`.</span></span> <span data-ttu-id="fff80-153">O uso da anotação informa ao tempo de execução que a função destina-se a ser usada como uma função de atividade.</span><span class="sxs-lookup"><span data-stu-id="fff80-153">Using the annotation informs the runtime that the function is intended to be used as an activity function.</span></span> <span data-ttu-id="fff80-154">Os valores de entrada para as funções de atividade são recuperados usando o método `GetInput<T>` do parâmetro `DurableActivityContext`.</span><span class="sxs-lookup"><span data-stu-id="fff80-154">Input values to activity functions are retrieved using the `GetInput<T>` method of the `DurableActivityContext` parameter.</span></span>

<span data-ttu-id="fff80-155">Semelhante às funções de orquestração, os tipos de retorno das funções de atividade devem ser void, Task ou um valor serializável JSON.</span><span class="sxs-lookup"><span data-stu-id="fff80-155">Similar to orchestration functions, the return types of activity functions must be either void, Task, or a JSON serializable value.</span></span>

<span data-ttu-id="fff80-156">Todas as exceções sem tratamento que são lançadas em funções de atividade serão enviadas para a função de orquestrador de chamada e apresentadas como um `TaskFailedException`.</span><span class="sxs-lookup"><span data-stu-id="fff80-156">Any unhandled exceptions that get thrown within activity functions will get sent up to the calling orchestrator function and presented as a `TaskFailedException`.</span></span> <span data-ttu-id="fff80-157">Neste ponto, o erro pode ser capturado e registrado no orquestrador, e a atividade pode ser repetida.</span><span class="sxs-lookup"><span data-stu-id="fff80-157">At this point, the error can be caught and logged in the orchestrator, and the activity can be retried.</span></span>

```csharp
[FunctionName("CheckAndReserveInventory")]
public static bool CheckAndReserveInventory([ActivityTrigger] DurableActivityContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    // Connect to inventory system and try to reserve items
    return true;
}
```

## <a name="recommended-resources"></a><span data-ttu-id="fff80-158">Recursos recomendados</span><span class="sxs-lookup"><span data-stu-id="fff80-158">Recommended resources</span></span>

- [<span data-ttu-id="fff80-159">Durable Functions</span><span class="sxs-lookup"><span data-stu-id="fff80-159">Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
- [<span data-ttu-id="fff80-160">Associações para Durable Functions</span><span class="sxs-lookup"><span data-stu-id="fff80-160">Bindings for Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-bindings)
- [<span data-ttu-id="fff80-161">Gerenciar instâncias no Durable Functions</span><span class="sxs-lookup"><span data-stu-id="fff80-161">Manage instances in Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-instance-management)

>[!div class="step-by-step"]
><span data-ttu-id="fff80-162">[Anterior](event-grid.md)
>[Próximo](orchestration-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="fff80-162">[Previous](event-grid.md)
[Next](orchestration-patterns.md)</span></span>
