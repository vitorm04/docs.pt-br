---
title: Padrões de orquestração-aplicativos sem servidor
description: Funções duráveis do Azure PR
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 2bd81c29e727254af6c8ecf39ee4bfef1f39d009
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/08/2019
ms.locfileid: "72522640"
---
# <a name="orchestration-patterns"></a>Padrões de orquestração

Durable Functions facilita a criação de fluxos de trabalho com estado que são compostos por atividades de longa execução discretas em um ambiente sem servidor. Como Durable Functions pode acompanhar o progresso de seus fluxos de trabalho e, periodicamente, fazer o ponto de verificação do histórico de execução, ele se presta à implementação de alguns padrões interessantes.

## <a name="function-chaining"></a>Encadeamento de funções

Em um processo sequencial típico, as atividades precisam executar uma após a outra em uma ordem específica. Opcionalmente, a atividade futura pode exigir alguma saída da função anterior. Essa dependência na ordenação de atividades cria uma cadeia de função de execução.

O benefício de usar Durable Functions para implementar esse padrão de fluxo de trabalho vem da sua capacidade de fazer o ponto de verificação. Se o servidor falhar, a rede atinge o tempo limite ou algum outro problema ocorre, as funções duráveis podem retomar o último estado conhecido e continuar executando o fluxo de trabalho mesmo se ele estiver em outro servidor.

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

No exemplo de código anterior, a função `CallActivityAsync` é responsável por executar uma determinada atividade em uma máquina virtual na data center. Quando Await retornar e a tarefa subjacente for concluída, a execução será registrada na tabela de histórico. O código na função de orquestrador pode fazer uso de qualquer uma das construções familiares da biblioteca de tarefas paralelas e das palavras-chave Async/Await.

O código a seguir é um exemplo simplificado de como o método `ProcessPayment` pode ser:

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

## <a name="asynchronous-http-apis"></a>APIs HTTP assíncronas

Em alguns casos, os fluxos de trabalho podem conter atividades que levam um período de tempo relativamente longo para ser concluído. Imagine um processo que inicia o backup de arquivos de mídia no armazenamento de BLOBs. Dependendo do tamanho e da quantidade dos arquivos de mídia, esse processo de backup pode levar horas para ser concluído.

Nesse cenário, a capacidade do `DurableOrchestrationClient`de verificar o status de um fluxo de trabalho em execução se torna útil. Ao usar um `HttpTrigger` para iniciar um fluxo de trabalho, o método `CreateCheckStatusResponse` pode ser usado para retornar uma instância do `HttpResponseMessage`. Essa resposta fornece ao cliente um URI no conteúdo que pode ser usado para verificar o status do processo em execução.

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

Usando seu cliente HTTP preferencial, as solicitações GET podem ser feitas para o URI no statusQueryGetUri para inspecionar o status do fluxo de trabalho em execução. A resposta de status retornada deve ser semelhante ao código a seguir.

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

Conforme o processo continua, a resposta de status será alterada para **com falha** ou **concluída**. Após a conclusão bem-sucedida, a propriedade de **saída** na carga conterá todos os dados retornados.

## <a name="monitoring"></a>Monitoramento

Para tarefas recorrentes simples, Azure Functions fornece o `TimerTrigger` que pode ser agendado com base em uma expressão CRON. O temporizador funciona bem para tarefas simples e de curta duração, mas pode haver cenários onde é necessário um agendamento mais flexível. Esse cenário é quando o padrão de monitoramento e o Durable Functions podem ajudar.

Durable Functions permite intervalos de agendamento flexíveis, gerenciamento de tempo de vida e a criação de vários processos de monitor de uma única função de orquestração. Um caso de uso para essa funcionalidade pode ser criar observadores para alterações de preço de ações que são concluídas quando um determinado limite é atingido.

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

o método `CreateTimer` de `DurableOrchestrationContext`configura o agendamento para a próxima invocação do loop para verificar as alterações de preço de ações. `DurableOrchestrationContext` também tem uma propriedade `CurrentUtcDateTime` para obter o valor DateTime atual em UTC. É melhor usar essa propriedade em vez de `DateTime.UtcNow` porque ela é facilmente simulada para teste.

## <a name="recommended-resources"></a>Recursos recomendados

- [Durable Functions do Azure](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
- [Teste de unidade no .NET Core e no .NET Standard](../../core/testing/index.md)

>[!div class="step-by-step"]
>[Anterior](durable-azure-functions.md)
>[Próximo](serverless-business-scenarios.md)
