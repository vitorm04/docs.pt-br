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
# <a name="orchestration-patterns"></a>Padrões de orquestração

As funções duráveis torna mais fácil criar fluxos de trabalho com monitoração de estado que são compostos por atividades discretas, de longa execução em um ambiente sem servidor. Uma vez que as funções duráveis pode acompanhar o progresso de seus fluxos de trabalho periodicamente pontos de verificação e o histórico de execução, ele é adaptado para implementar alguns padrões interessantes.

## <a name="function-chaining"></a>Encadeamento de funções

Em um processo sequencial típico, atividades precisam executar um após o outro em uma ordem específica. Opcionalmente, a próxima atividade pode exigir algumas saídas da função anterior. Essa dependência na classificação das atividades cria uma cadeia de função de execução.

A vantagem de usar as funções duráveis para implementar esse padrão de fluxo de trabalho vem de sua capacidade de fazer o ponto de verificação. Se o servidor falhar, a rede atinge o tempo limite ou se a algum outro problema ocorre, as funções duráveis podem retomar a partir do último estado conhecido e continuar a executar seu fluxo de trabalho, mesmo se ele estiver em outro servidor.

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

No exemplo de código anterior, o `CallActivityAsync` função é responsável por executar uma determinada atividade em uma máquina virtual no data center. Quando a expressão await retorna e a tarefa subjacente for concluído, a execução será registrada para a tabela de histórico. O código na função de orquestrador pode fazer uso de qualquer uma das construções familiares de biblioteca de tarefas paralelas e as palavras-chave async/await.

O código a seguir é um exemplo simplificado do que o `ProcessPayment` método pode se parecer com:

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

## <a name="asynchronous-http-apis"></a>APIs de HTTP assíncrono

Em alguns casos, os fluxos de trabalho podem conter atividades que recebem um relativamente longo período de tempo para ser concluída. Imagine que um processo que inicia o backup da mídia de arquivos no armazenamento de BLOBs. Dependendo do tamanho e quantidade de arquivos de mídia, esse processo de backup pode levar horas para ser concluído.

Nesse cenário, o `DurableOrchestrationClient`da capacidade de verificar o status de um fluxo de trabalho em execução se torna útil. Ao usar um `HttpTrigger` para iniciar um fluxo de trabalho, o `CreateCheckStatusResponse` método pode ser usado para retornar uma instância de `HttpResponseMessage`. Essa resposta fornece ao cliente com um URI no conteúdo que pode ser usado para verificar o status do processo em execução.

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

O resultado de exemplo abaixo mostra a estrutura da carga de resposta.

```json
{
    "id": "instanceId",
    "statusQueryGetUri": "http://host/statusUri",
    "sendEventPostUri": "http://host/eventUri",
    "terminatePostUri": "http://host/terminateUri"
}
```

Usando seu cliente HTTP preferida, as solicitações GET podem ser feitas ao URI no statusQueryGetUri para inspecionar o status do fluxo de trabalho em execução. A resposta de status retornado deve se parecer com o código a seguir.

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

Como o processo continua, a resposta de status será alterado para um **Failed** ou **concluído**. Após a conclusão bem-sucedida, o **saída** propriedade na carga irá conter todos os dados retornados.

## <a name="monitoring"></a>Monitoramento

Para tarefas recorrentes simples, o Azure Functions fornece o `TimerTrigger` que podem ser agendadas com base em uma expressão CRON. O temporizador funciona bem para tarefas simples de curta duração, mas pode haver situações em que o agendamento mais flexível é necessária. Esse cenário é quando o padrão de monitoramento e as funções duráveis podem ajudar.

Funções duráveis permite que os intervalos de agendamento flexíveis, gerenciamento de tempo de vida e a criação de vários processos do monitor de uma função única orquestração. Um caso de uso para essa funcionalidade pode ser para criar observadores para que as alterações de preço de estoque concluído depois que um determinado limite é atingido.

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

`DurableOrchestrationContext`do `CreateTimer` método define a agenda para a próxima invocação de loop para verificar se há alterações de preço de estoque. `DurableOrchestrationContext` também tem um `CurrentUtcDateTime` propriedade para obter o valor de data e hora atual em UTC. É melhor usar essa propriedade em vez de `DateTime.UtcNow` porque ele é facilmente simulado para teste.

## <a name="recommended-resources"></a>Recursos recomendados

* [Funções duráveis do Azure](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
* [Teste de unidade no .NET Core e no .NET Standard](../../core/testing/index.md)

>[!div class="step-by-step"]
>[Anterior](durable-azure-functions.md)
>[Próximo](serverless-business-scenarios.md)