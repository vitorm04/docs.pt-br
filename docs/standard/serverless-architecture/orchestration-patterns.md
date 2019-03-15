---
title: Padrões de orquestração - aplicativos sem servidor
description: Solicitação de pull de funções duráveis do Azure
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 8be499a24e2c5a94132ce07241e17f675e8a1274
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57843752"
---
# <a name="orchestration-patterns"></a><span data-ttu-id="45c94-103">Padrões de orquestração</span><span class="sxs-lookup"><span data-stu-id="45c94-103">Orchestration patterns</span></span>

<span data-ttu-id="45c94-104">As funções duráveis torna mais fácil criar fluxos de trabalho com monitoração de estado que são compostos por atividades discretas, de longa execução em um ambiente sem servidor.</span><span class="sxs-lookup"><span data-stu-id="45c94-104">Durable Functions makes it easier to create stateful workflows that are composed of discrete, long running activities in a serverless environment.</span></span> <span data-ttu-id="45c94-105">Uma vez que as funções duráveis pode acompanhar o progresso de seus fluxos de trabalho periodicamente pontos de verificação e o histórico de execução, ele é adaptado para implementar alguns padrões interessantes.</span><span class="sxs-lookup"><span data-stu-id="45c94-105">Since Durable Functions can track the progress of your workflows and periodically checkpoints the execution history, it lends itself to implementing some interesting patterns.</span></span>

## <a name="function-chaining"></a><span data-ttu-id="45c94-106">Encadeamento de funções</span><span class="sxs-lookup"><span data-stu-id="45c94-106">Function chaining</span></span>

<span data-ttu-id="45c94-107">Em um processo sequencial típico, atividades precisam executar um após o outro em uma ordem específica.</span><span class="sxs-lookup"><span data-stu-id="45c94-107">In a typical sequential process, activities need to execute one after the other in a particular order.</span></span> <span data-ttu-id="45c94-108">Opcionalmente, a próxima atividade pode exigir algumas saídas da função anterior.</span><span class="sxs-lookup"><span data-stu-id="45c94-108">Optionally, the upcoming activity may require some output from the previous function.</span></span> <span data-ttu-id="45c94-109">Essa dependência na classificação das atividades cria uma cadeia de função de execução.</span><span class="sxs-lookup"><span data-stu-id="45c94-109">This dependency on the ordering of activities creates a function chain of execution.</span></span>

<span data-ttu-id="45c94-110">A vantagem de usar as funções duráveis para implementar esse padrão de fluxo de trabalho vem de sua capacidade de fazer o ponto de verificação.</span><span class="sxs-lookup"><span data-stu-id="45c94-110">The benefit of using Durable Functions to implement this workflow pattern comes from its ability to do checkpointing.</span></span> <span data-ttu-id="45c94-111">Se o servidor falhar, a rede atinge o tempo limite ou se a algum outro problema ocorre, as funções duráveis podem retomar a partir do último estado conhecido e continuar a executar seu fluxo de trabalho, mesmo se ele estiver em outro servidor.</span><span class="sxs-lookup"><span data-stu-id="45c94-111">If the server crashes, the network times out or some other issue occurs, Durable functions can resume from the last known state and continue running your workflow even if it's on another server.</span></span>

```csharp
[FunctionName("PlaceOrder")]
public static async Task<string> PlaceOrder([OrchestrationTrigger] DurableOrchestrationContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    await context.CallActivityAsync<bool>("CheckAndReserveInventory", orderData);
    await context.CallActivityAsync<bool>("ProcessPayment", orderData);

    string trackingNumber = await context.CallActivityAsync<string>("ScheduleShipping", orderData);
    await context.CallActivityAsync<string>("EmailCustomer", trackingNumber);

    return trackingNumber;
}
```

<span data-ttu-id="45c94-112">No exemplo de código anterior, o `CallActivityAsync` função é responsável por executar uma determinada atividade em uma máquina virtual no data center.</span><span class="sxs-lookup"><span data-stu-id="45c94-112">In the preceding code sample, the `CallActivityAsync` function is responsible for running a given activity on a virtual machine in the data center.</span></span> <span data-ttu-id="45c94-113">Quando a expressão await retorna e a tarefa subjacente for concluído, a execução será registrada para a tabela de histórico.</span><span class="sxs-lookup"><span data-stu-id="45c94-113">When the await returns and the underlying Task completes, the execution will be recorded to the history table.</span></span> <span data-ttu-id="45c94-114">O código na função de orquestrador pode fazer uso de qualquer uma das construções familiares de biblioteca de tarefas paralelas e as palavras-chave async/await.</span><span class="sxs-lookup"><span data-stu-id="45c94-114">The code in the orchestrator function can make use of any of the familiar constructs of the Task Parallel Library and the async/await keywords.</span></span>

<span data-ttu-id="45c94-115">O código a seguir é um exemplo simplificado do que o `ProcessPayment` método pode se parecer com:</span><span class="sxs-lookup"><span data-stu-id="45c94-115">The following code is a simplified example of what the `ProcessPayment` method may look like:</span></span>

```csharp
[FunctionName("ProcessPayment")]
public static bool ProcessPayment([ActivityTrigger] DurableActivityContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    ApplyCoupons(orderData);
    if(IssuePaymentRequest(orderData)) {
        return true;
    }

    return false;
}
```

## <a name="asynchronous-http-apis"></a><span data-ttu-id="45c94-116">APIs de HTTP assíncrono</span><span class="sxs-lookup"><span data-stu-id="45c94-116">Asynchronous HTTP APIs</span></span>

<span data-ttu-id="45c94-117">Em alguns casos, os fluxos de trabalho podem conter atividades que recebem um relativamente longo período de tempo para ser concluída.</span><span class="sxs-lookup"><span data-stu-id="45c94-117">In some cases, workflows may contain activities that take a relatively long period of time to complete.</span></span> <span data-ttu-id="45c94-118">Imagine que um processo que inicia o backup da mídia de arquivos no armazenamento de BLOBs.</span><span class="sxs-lookup"><span data-stu-id="45c94-118">Imagine a process that kicks off the backup of media files into blob storage.</span></span> <span data-ttu-id="45c94-119">Dependendo do tamanho e quantidade de arquivos de mídia, esse processo de backup pode levar horas para ser concluído.</span><span class="sxs-lookup"><span data-stu-id="45c94-119">Depending on the size and quantity of the media files, this backup process may take hours to complete.</span></span>

<span data-ttu-id="45c94-120">Nesse cenário, o `DurableOrchestrationClient`da capacidade de verificar o status de um fluxo de trabalho em execução se torna útil.</span><span class="sxs-lookup"><span data-stu-id="45c94-120">In this scenario, the `DurableOrchestrationClient`'s ability to check the status of a running workflow becomes useful.</span></span> <span data-ttu-id="45c94-121">Ao usar um `HttpTrigger` para iniciar um fluxo de trabalho, o `CreateCheckStatusResponse` método pode ser usado para retornar uma instância de `HttpResponseMessage`.</span><span class="sxs-lookup"><span data-stu-id="45c94-121">When using an `HttpTrigger` to start a workflow, the `CreateCheckStatusResponse` method can be used to return an instance of `HttpResponseMessage`.</span></span> <span data-ttu-id="45c94-122">Essa resposta fornece ao cliente com um URI no conteúdo que pode ser usado para verificar o status do processo em execução.</span><span class="sxs-lookup"><span data-stu-id="45c94-122">This response provides the client with a URI in the payload that can be used to check the status of the running process.</span></span>

```csharp
[FunctionName("OrderWorkflow")]
public static async Task<HttpResponseMessage> Run(
    [HttpTrigger(AuthorizationLevel.Function, "POST")]HttpRequestMessage req,
    [OrchestrationClient ] DurableOrchestrationClient orchestrationClient)
{
    OrderRequestData data = await req.Content.ReadAsAsync<OrderRequestData>();

    string instanceId = await orchestrationClient.StartNewAsync("PlaceOrder", data);

    return orchestrationClient.CreateCheckStatusResponse(req, instanceId);
}
```

<span data-ttu-id="45c94-123">O resultado de exemplo abaixo mostra a estrutura da carga de resposta.</span><span class="sxs-lookup"><span data-stu-id="45c94-123">The sample result below shows the structure of the response payload.</span></span>

```json
{
    "id": "instanceId",
    "statusQueryGetUri": "http://host/statusUri",
    "sendEventPostUri": "http://host/eventUri",
    "terminatePostUri": "http://host/terminateUri"
}
```

<span data-ttu-id="45c94-124">Usando seu cliente HTTP preferida, as solicitações GET podem ser feitas ao URI no statusQueryGetUri para inspecionar o status do fluxo de trabalho em execução.</span><span class="sxs-lookup"><span data-stu-id="45c94-124">Using your preferred HTTP client, GET requests can be made to the URI in statusQueryGetUri to inspect the status of the running workflow.</span></span> <span data-ttu-id="45c94-125">A resposta de status retornado deve se parecer com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="45c94-125">The returned status response should resemble the following code.</span></span>

```json
{
    "runtimeStatus": "Running",
    "input": {
        "$type": "DurableFunctionsDemos.OrderRequestData, DurableFunctionsDemos"
    },
    "output": null,
    "createdTime": "2018-01-01T00:22:05Z",
    "lastUpdatedTime": "2018-01-01T00:22:09Z"
}
```

<span data-ttu-id="45c94-126">Como o processo continua, a resposta de status será alterado para um **Failed** ou **concluído**.</span><span class="sxs-lookup"><span data-stu-id="45c94-126">As the process continues, the status response will change to either **Failed** or **Completed**.</span></span> <span data-ttu-id="45c94-127">Após a conclusão bem-sucedida, o **saída** propriedade na carga irá conter todos os dados retornados.</span><span class="sxs-lookup"><span data-stu-id="45c94-127">On successful completion, the **output** property in the payload will contain any returned data.</span></span>

## <a name="monitoring"></a><span data-ttu-id="45c94-128">Monitoramento</span><span class="sxs-lookup"><span data-stu-id="45c94-128">Monitoring</span></span>

<span data-ttu-id="45c94-129">Para tarefas recorrentes simples, o Azure Functions fornece o `TimerTrigger` que podem ser agendadas com base em uma expressão CRON.</span><span class="sxs-lookup"><span data-stu-id="45c94-129">For simple recurring tasks, Azure Functions provides the `TimerTrigger` that can be scheduled based on a CRON expression.</span></span> <span data-ttu-id="45c94-130">O temporizador funciona bem para tarefas simples de curta duração, mas pode haver situações em que o agendamento mais flexível é necessária.</span><span class="sxs-lookup"><span data-stu-id="45c94-130">The timer works well for simple, short-lived tasks, but there might be scenarios where more flexible scheduling is needed.</span></span> <span data-ttu-id="45c94-131">Esse cenário é quando o padrão de monitoramento e as funções duráveis podem ajudar.</span><span class="sxs-lookup"><span data-stu-id="45c94-131">This scenario is when the monitoring pattern and Durable Functions can help.</span></span>

<span data-ttu-id="45c94-132">Funções duráveis permite que os intervalos de agendamento flexíveis, gerenciamento de tempo de vida e a criação de vários processos do monitor de uma função única orquestração.</span><span class="sxs-lookup"><span data-stu-id="45c94-132">Durable Functions allows for flexible scheduling intervals, lifetime management, and the creation of multiple monitor processes from a single orchestration function.</span></span> <span data-ttu-id="45c94-133">Um caso de uso para essa funcionalidade pode ser para criar observadores para que as alterações de preço de estoque concluído depois que um determinado limite é atingido.</span><span class="sxs-lookup"><span data-stu-id="45c94-133">One use case for this functionality might be to create watchers for stock price changes that complete once a certain threshold is met.</span></span>

```csharp
[FunctionName("CheckStockPrice")]
public static async Task CheckStockPrice([OrchestrationTrigger] DurableOrchestrationContext context)
{
    StockWatcherInfo stockInfo = context.GetInput<StockWatcherInfo>();
    const int checkIntervalSeconds = 120;
    StockPrice initialStockPrice = null;

    DateTime fireAt;
    DateTime exitTime = context.CurrentUtcDateTime.Add(stockInfo.TimeLimit);

    while (context.CurrentUtcDateTime < exitTime)
    {
        StockPrice currentStockPrice = await context.CallActivityAsync<StockPrice>("GetStockPrice", stockInfo);

        if (initialStockPrice == null)
        {
            initialStockPrice = currentStockPrice;
            fireAt = context.CurrentUtcDateTime.AddSeconds(checkIntervalSeconds);
            await context.CreateTimer(fireAt, CancellationToken.None);
            continue;
        }

        decimal percentageChange = (initialStockPrice.Price - currentStockPrice.Price) /
                               ((initialStockPrice.Price + currentStockPrice.Price) / 2);

        if (Math.Abs(percentageChange) >= stockInfo.PercentageChange)
        {
            // Change threshold detected
            await context.CallActivityAsync("NotifyStockPercentageChange", currentStockPrice);
            break;
        }

        // Sleep til next polling interval
        fireAt = context.CurrentUtcDateTime.AddSeconds(checkIntervalSeconds);
        await context.CreateTimer(fireAt, CancellationToken.None);
    }
}
```

<span data-ttu-id="45c94-134">`DurableOrchestrationContext`do `CreateTimer` método define a agenda para a próxima invocação de loop para verificar se há alterações de preço de estoque.</span><span class="sxs-lookup"><span data-stu-id="45c94-134">`DurableOrchestrationContext`'s `CreateTimer` method sets up the schedule for the next invocation of the loop to check for stock price changes.</span></span> <span data-ttu-id="45c94-135">`DurableOrchestrationContext` também tem um `CurrentUtcDateTime` propriedade para obter o valor de data e hora atual em UTC.</span><span class="sxs-lookup"><span data-stu-id="45c94-135">`DurableOrchestrationContext` also has a `CurrentUtcDateTime` property to get the current DateTime value in UTC.</span></span> <span data-ttu-id="45c94-136">É melhor usar essa propriedade em vez de `DateTime.UtcNow` porque ele é facilmente simulado para teste.</span><span class="sxs-lookup"><span data-stu-id="45c94-136">It's better to use this property instead of `DateTime.UtcNow` because it's easily mocked for testing.</span></span>

## <a name="recommended-resources"></a><span data-ttu-id="45c94-137">Recursos recomendados</span><span class="sxs-lookup"><span data-stu-id="45c94-137">Recommended resources</span></span>

* [<span data-ttu-id="45c94-138">Funções duráveis do Azure</span><span class="sxs-lookup"><span data-stu-id="45c94-138">Azure Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
* [<span data-ttu-id="45c94-139">Teste de unidade no .NET Core e no .NET Standard</span><span class="sxs-lookup"><span data-stu-id="45c94-139">Unit Testing in .NET Core and .NET Standard</span></span>](../../core/testing/index.md)

>[!div class="step-by-step"]
><span data-ttu-id="45c94-140">[Anterior](durable-azure-functions.md)
>[Próximo](serverless-business-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="45c94-140">[Previous](durable-azure-functions.md)
[Next](serverless-business-scenarios.md)</span></span>