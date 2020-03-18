---
title: Funções duráveis do Azure - Aplicativos sem servidor
description: As funções duráveis do Azure estendem o tempo de execução das funções do Azure para permitir fluxos de trabalho estaduais em código.
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 2c0ad086640409ac187c3aa882add4d6b39b6ff9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522857"
---
# <a name="durable-azure-functions"></a><span data-ttu-id="50cd5-103">Funções duráveis do Azure</span><span class="sxs-lookup"><span data-stu-id="50cd5-103">Durable Azure functions</span></span>

<span data-ttu-id="50cd5-104">Ao criar aplicativos sem servidor com funções do Azure, suas operações normalmente serão projetadas para serem executadas de forma apátrida.</span><span class="sxs-lookup"><span data-stu-id="50cd5-104">When creating serverless applications with Azure Functions, your operations will typically be designed to run in a stateless manner.</span></span> <span data-ttu-id="50cd5-105">A razão para essa escolha de design é porque, à medida que a plataforma é dimensionada, torna-se difícil saber em quais servidores o código está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="50cd5-105">The reason for this design choice is because as the platform scales, it becomes difficult to know what servers the code is running on.</span></span> <span data-ttu-id="50cd5-106">Também fica difícil saber quantas instâncias estão ativas em um dado momento.</span><span class="sxs-lookup"><span data-stu-id="50cd5-106">It also becomes difficult to know how many instances are active at any given point.</span></span> <span data-ttu-id="50cd5-107">No entanto, existem classes de aplicações que exigem que o estado atual de um processo seja conhecido.</span><span class="sxs-lookup"><span data-stu-id="50cd5-107">However, there are classes of applications that require the current state of a process to be known.</span></span> <span data-ttu-id="50cd5-108">Considere o processo de envio de um pedido para uma loja online.</span><span class="sxs-lookup"><span data-stu-id="50cd5-108">Consider the process of submitting an order to an online store.</span></span> <span data-ttu-id="50cd5-109">A operação de checkout pode ser um fluxo de trabalho que é composto por múltiplas operações que precisam saber o estado do processo.</span><span class="sxs-lookup"><span data-stu-id="50cd5-109">The checkout operation might be a workflow that is composed of multiple operations that need to know the state of the process.</span></span> <span data-ttu-id="50cd5-110">Essas informações podem incluir o inventário do produto, se o cliente tiver algum crédito em sua conta, e também os resultados do processamento do cartão de crédito.</span><span class="sxs-lookup"><span data-stu-id="50cd5-110">Such information may include the product inventory, if the customer has any credits on their account, and also the results of processing the credit card.</span></span> <span data-ttu-id="50cd5-111">Essas operações podem facilmente ser seus próprios fluxos de trabalho internos ou até mesmo serviços de sistemas de terceiros.</span><span class="sxs-lookup"><span data-stu-id="50cd5-111">These operations could easily be their own internal workflows or even services from third-party systems.</span></span>

<span data-ttu-id="50cd5-112">Existem hoje diversos padrões que auxiliam na coordenação do estado de aplicação entre sistemas internos e externos.</span><span class="sxs-lookup"><span data-stu-id="50cd5-112">Various patterns exist today that assist with the coordination of application state between internal and external systems.</span></span> <span data-ttu-id="50cd5-113">É comum encontrar soluções que dependem de sistemas centralizados de fila, lojas de valor de chave distribuídas ou bancos de dados compartilhados para gerenciar esse estado.</span><span class="sxs-lookup"><span data-stu-id="50cd5-113">It's common to come across solutions that rely on centralized queuing systems, distributed key-value stores, or shared databases to manage that state.</span></span> <span data-ttu-id="50cd5-114">No entanto, todos esses são recursos adicionais que agora precisam ser provisionados e gerenciados.</span><span class="sxs-lookup"><span data-stu-id="50cd5-114">However, these are all additional resources that now need to be provisioned and managed.</span></span> <span data-ttu-id="50cd5-115">Em um ambiente sem servidor, seu código pode se tornar complicado tentando coordenar com esses recursos manualmente.</span><span class="sxs-lookup"><span data-stu-id="50cd5-115">In a serverless environment, your code could become cumbersome trying to coordinate with these resources manually.</span></span> <span data-ttu-id="50cd5-116">O Azure Functions oferece uma alternativa para criar funções imponentes chamadas Funções Duráveis.</span><span class="sxs-lookup"><span data-stu-id="50cd5-116">Azure Functions offers an alternative for creating stateful functions called Durable Functions.</span></span>

<span data-ttu-id="50cd5-117">Durable Functions é uma extensão do tempo de execução funções do Azure que permite a definição de fluxos de trabalho estatais em código.</span><span class="sxs-lookup"><span data-stu-id="50cd5-117">Durable Functions is an extension to the Azure Functions runtime that enables the definition of stateful workflows in code.</span></span> <span data-ttu-id="50cd5-118">Ao dividir os fluxos de trabalho em atividades, a extensão Funções Duráveis pode gerenciar o estado, criar pontos de verificação de progresso e lidar com a distribuição de chamadas de função entre servidores.</span><span class="sxs-lookup"><span data-stu-id="50cd5-118">By breaking down workflows into activities, the Durable Functions extension can manage state, create progress checkpoints, and handle the distribution of function calls across servers.</span></span> <span data-ttu-id="50cd5-119">Em segundo plano, ele faz uso de uma conta do Azure Storage para persistir o histórico de execução, agendar funções de atividade e recuperar respostas.</span><span class="sxs-lookup"><span data-stu-id="50cd5-119">In the background, it makes use of an Azure Storage account to persist execution history, schedule activity functions and retrieve responses.</span></span> <span data-ttu-id="50cd5-120">Seu código sem servidor nunca deve interagir com informações perpersistentes nessa conta de armazenamento, e normalmente não é algo com o qual os desenvolvedores precisam interagir.</span><span class="sxs-lookup"><span data-stu-id="50cd5-120">Your serverless code should never interact with persisted information in that storage account, and is typically not something with which developers need to interact.</span></span>

## <a name="triggering-a-stateful-workflow"></a><span data-ttu-id="50cd5-121">Desencadeando um fluxo de trabalho imponente</span><span class="sxs-lookup"><span data-stu-id="50cd5-121">Triggering a stateful workflow</span></span>

<span data-ttu-id="50cd5-122">Fluxos de trabalho estatais em Funções Duráveis podem ser divididos em dois componentes intrínsecos; orquestração e ativação de atividade.</span><span class="sxs-lookup"><span data-stu-id="50cd5-122">Stateful workflows in Durable Functions can be broken down into two intrinsic components; orchestration and activity triggers.</span></span> <span data-ttu-id="50cd5-123">Gatilhos e vinculações são componentes principais usados pelas funções do Azure para permitir que suas funções sem servidor sejam notificadas quando iniciar, receber entradas e retornar resultados.</span><span class="sxs-lookup"><span data-stu-id="50cd5-123">Triggers and bindings are core components used by Azure Functions to enable your serverless functions to be notified when to start, receive input, and return results.</span></span>

### <a name="working-with-the-orchestration-client"></a><span data-ttu-id="50cd5-124">Trabalhando com o cliente orchestration</span><span class="sxs-lookup"><span data-stu-id="50cd5-124">Working with the Orchestration client</span></span>

<span data-ttu-id="50cd5-125">As orquestrações são únicas quando comparadas com outros estilos de operações desencadeadas em Funções Azure.</span><span class="sxs-lookup"><span data-stu-id="50cd5-125">Orchestrations are unique when compared to other styles of triggered operations in Azure Functions.</span></span> <span data-ttu-id="50cd5-126">Funções duráveis permitem a execução de funções que podem levar horas ou até dias para serem concluídas.</span><span class="sxs-lookup"><span data-stu-id="50cd5-126">Durable Functions enables the execution of functions that may take hours or even days to complete.</span></span> <span data-ttu-id="50cd5-127">Esse tipo de comportamento vem com a necessidade de verificar o status de uma orquestração em execução, encerrar preventivamente ou enviar notificações de eventos externos.</span><span class="sxs-lookup"><span data-stu-id="50cd5-127">That type of behavior comes with the need to able to check the status of a running orchestration, preemptively terminate, or send notifications of external events.</span></span>

<span data-ttu-id="50cd5-128">Para esses casos, a extensão `DurableOrchestrationClient` Funções Duráveis fornece a classe que permite interagir com funções orquestradas.</span><span class="sxs-lookup"><span data-stu-id="50cd5-128">For such cases, the Durable Functions extension provides the `DurableOrchestrationClient` class that allows you to interact with orchestrated functions.</span></span> <span data-ttu-id="50cd5-129">Você tem acesso ao cliente de `OrchestrationClientAttribute` orquestração usando a vinculação.</span><span class="sxs-lookup"><span data-stu-id="50cd5-129">You get access to the orchestration client by using the `OrchestrationClientAttribute` binding.</span></span> <span data-ttu-id="50cd5-130">Geralmente, você incluiria esse atributo com outro `HttpTrigger` tipo `ServiceBusTrigger`de gatilho, como um ou .</span><span class="sxs-lookup"><span data-stu-id="50cd5-130">Generally, you would include this attribute with another trigger type, such as an `HttpTrigger` or `ServiceBusTrigger`.</span></span> <span data-ttu-id="50cd5-131">Uma vez que a função de origem tenha sido acionada, o cliente de orquestração pode ser usado para iniciar uma função orquestradora.</span><span class="sxs-lookup"><span data-stu-id="50cd5-131">Once the source function has been triggered, the orchestration client can be used to start an orchestrator function.</span></span>

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

### <a name="the-orchestrator-function"></a><span data-ttu-id="50cd5-132">A função orquestradora</span><span class="sxs-lookup"><span data-stu-id="50cd5-132">The orchestrator function</span></span>

<span data-ttu-id="50cd5-133">Anotando uma função com o OrchestrationTriggerAttribute em Funções Azure marca que funcionam como uma função orquestradora.</span><span class="sxs-lookup"><span data-stu-id="50cd5-133">Annotating a function with the OrchestrationTriggerAttribute in Azure Functions marks that function as an orchestrator function.</span></span> <span data-ttu-id="50cd5-134">É responsável por gerenciar as diversas atividades que compõem seu fluxo de trabalho imponente.</span><span class="sxs-lookup"><span data-stu-id="50cd5-134">It's responsible for managing the various activities that make up your stateful workflow.</span></span>

<span data-ttu-id="50cd5-135">As funções do orquestrador não podem fazer uso de amarras diferentes do OrchestrationTriggerAttribute.</span><span class="sxs-lookup"><span data-stu-id="50cd5-135">Orchestrator functions are unable to make use of bindings other than the OrchestrationTriggerAttribute.</span></span> <span data-ttu-id="50cd5-136">Este atributo só pode ser usado com um tipo de parâmetro de DurableOrchestrationContext.</span><span class="sxs-lookup"><span data-stu-id="50cd5-136">This attribute can only be used with a parameter type of DurableOrchestrationContext.</span></span> <span data-ttu-id="50cd5-137">Nenhum outro inputs pode ser usado, uma vez que a desserialização de entradas na assinatura da função não é suportada.</span><span class="sxs-lookup"><span data-stu-id="50cd5-137">No other inputs can be used since deserialization of inputs in the function signature isn't supported.</span></span> <span data-ttu-id="50cd5-138">Para obter entradas fornecidas pelo cliente de\<\> orquestração, o método GetInput T deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="50cd5-138">To get inputs provided by the orchestration client, the GetInput\<T\> method must be used.</span></span>

<span data-ttu-id="50cd5-139">Além disso, os tipos de retorno das funções de orquestração devem ser vazios, tarefa ou um valor serializável JSON.</span><span class="sxs-lookup"><span data-stu-id="50cd5-139">Also, the return types of orchestration functions must be either void, Task, or a JSON serializable value.</span></span>

> <span data-ttu-id="50cd5-140">*O código de manipulação de erros foi deixado de fora por brevidade*</span><span class="sxs-lookup"><span data-stu-id="50cd5-140">*Error handling code has been left out for brevity*</span></span>

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

<span data-ttu-id="50cd5-141">Várias instâncias de uma orquestração podem ser iniciadas e funcionando ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="50cd5-141">Multiple instances of an orchestration can be started and running at the same time.</span></span> <span data-ttu-id="50cd5-142">Chamar `StartNewAsync` o método `DurableOrchestrationClient` nos lançamentos é uma nova instância da orquestração.</span><span class="sxs-lookup"><span data-stu-id="50cd5-142">Calling the `StartNewAsync` method on the `DurableOrchestrationClient` launches a new instance of the orchestration.</span></span> <span data-ttu-id="50cd5-143">O método `Task<string>` retorna um que se completa quando a orquestração começou.</span><span class="sxs-lookup"><span data-stu-id="50cd5-143">The method returns a `Task<string>` that completes when the orchestration has started.</span></span> <span data-ttu-id="50cd5-144">Uma exceção `TimeoutException` do tipo é lançada se a orquestração não começou dentro de 30 segundos.</span><span class="sxs-lookup"><span data-stu-id="50cd5-144">An exception of type `TimeoutException` gets thrown if the orchestration hasn't started within 30 seconds.</span></span>

<span data-ttu-id="50cd5-145">O `Task<string>` completo `StartNewAsync` deve conter o ID único da instância de orquestração.</span><span class="sxs-lookup"><span data-stu-id="50cd5-145">The completed `Task<string>` from `StartNewAsync` should contain the unique ID of the orchestration instance.</span></span> <span data-ttu-id="50cd5-146">Este ID de instância pode ser usado para invocar operações nessa orquestração específica.</span><span class="sxs-lookup"><span data-stu-id="50cd5-146">This instance ID can be used to invoke operations on that specific orchestration.</span></span> <span data-ttu-id="50cd5-147">A orquestração pode ser consultada para o status ou notificações de eventos enviadas.</span><span class="sxs-lookup"><span data-stu-id="50cd5-147">The orchestration can be queried for the status or sent event notifications.</span></span>

### <a name="the-activity-functions"></a><span data-ttu-id="50cd5-148">As funções de atividade</span><span class="sxs-lookup"><span data-stu-id="50cd5-148">The activity functions</span></span>

<span data-ttu-id="50cd5-149">As funções de atividade são as operações discretas que são compostas juntas dentro de uma função de orquestração para criar o fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="50cd5-149">Activity functions are the discrete operations that get composed together within an orchestration function to create the workflow.</span></span> <span data-ttu-id="50cd5-150">Aqui é onde a maior parte do trabalho real ocorreria.</span><span class="sxs-lookup"><span data-stu-id="50cd5-150">Here is where most of actual work would take place.</span></span> <span data-ttu-id="50cd5-151">Eles representam a lógica do negócio, os processos de longo prazo e as peças do quebra-cabeça para uma solução maior.</span><span class="sxs-lookup"><span data-stu-id="50cd5-151">They represent the business logic, long running processes, and the puzzle pieces to a larger solution.</span></span>

<span data-ttu-id="50cd5-152">O `ActivityTriggerAttribute` é usado para anotar um parâmetro `DurableActivityContext`de função do tipo .</span><span class="sxs-lookup"><span data-stu-id="50cd5-152">The `ActivityTriggerAttribute` is used to annotate a function parameter of type `DurableActivityContext`.</span></span> <span data-ttu-id="50cd5-153">O uso da anotação informa o tempo de execução de que a função deve ser usada como função de atividade.</span><span class="sxs-lookup"><span data-stu-id="50cd5-153">Using the annotation informs the runtime that the function is intended to be used as an activity function.</span></span> <span data-ttu-id="50cd5-154">Os valores de entrada para `GetInput<T>` as funções de atividade são recuperados usando o método do `DurableActivityContext` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="50cd5-154">Input values to activity functions are retrieved using the `GetInput<T>` method of the `DurableActivityContext` parameter.</span></span>

<span data-ttu-id="50cd5-155">Semelhante às funções de orquestração, os tipos de retorno das funções de atividade devem ser vazios, tarefas ou um valor serializável JSON.</span><span class="sxs-lookup"><span data-stu-id="50cd5-155">Similar to orchestration functions, the return types of activity functions must be either void, Task, or a JSON serializable value.</span></span>

<span data-ttu-id="50cd5-156">Quaisquer exceções não manuseadas que sejam jogadas dentro das funções de `TaskFailedException`atividade serão enviadas para a função de orquestrador de chamadas e apresentadas como um .</span><span class="sxs-lookup"><span data-stu-id="50cd5-156">Any unhandled exceptions that get thrown within activity functions will get sent up to the calling orchestrator function and presented as a `TaskFailedException`.</span></span> <span data-ttu-id="50cd5-157">Neste ponto, o erro pode ser pego e registrado no orquestrador, e a atividade pode ser repetida novamente.</span><span class="sxs-lookup"><span data-stu-id="50cd5-157">At this point, the error can be caught and logged in the orchestrator, and the activity can be retried.</span></span>

```csharp
[FunctionName("CheckAndReserveInventory")]
public static bool CheckAndReserveInventory([ActivityTrigger] DurableActivityContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    // Connect to inventory system and try to reserve items
    return true;
}
```

## <a name="recommended-resources"></a><span data-ttu-id="50cd5-158">Recursos recomendados</span><span class="sxs-lookup"><span data-stu-id="50cd5-158">Recommended resources</span></span>

- [<span data-ttu-id="50cd5-159">Funções duráveis</span><span class="sxs-lookup"><span data-stu-id="50cd5-159">Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
- [<span data-ttu-id="50cd5-160">Vinculações para funções duráveis</span><span class="sxs-lookup"><span data-stu-id="50cd5-160">Bindings for Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-bindings)
- [<span data-ttu-id="50cd5-161">Gerenciar instâncias em funções duráveis</span><span class="sxs-lookup"><span data-stu-id="50cd5-161">Manage instances in Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-instance-management)

>[!div class="step-by-step"]
><span data-ttu-id="50cd5-162">[Próximo](event-grid.md)
>[anterior](orchestration-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="50cd5-162">[Previous](event-grid.md)
[Next](orchestration-patterns.md)</span></span>
