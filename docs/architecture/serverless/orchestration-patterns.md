---
title: Padrões de orquestração - Aplicativos sem servidor
description: Funções duráveis do Azure pr
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 2bd81c29e727254af6c8ecf39ee4bfef1f39d009
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522640"
---
# <a name="orchestration-patterns"></a>Padrões de orquestração

Funções duráveis facilitam a criação de fluxos de trabalho estaduais que são compostos de atividades discretas e de longa duração em um ambiente sem servidor. Uma vez que as Funções Duráveis podem acompanhar o progresso de seus fluxos de trabalho e periodicamente verifica o histórico de execução, ele se presta a implementar alguns padrões interessantes.

## <a name="function-chaining"></a>Encadeamento de funções

Em um processo seqüencial típico, as atividades precisam executar uma após a outra em uma ordem particular. Opcionalmente, a atividade futura pode exigir alguma saída da função anterior. Essa dependência da ordenação de atividades cria uma cadeia de funções de execução.

O benefício de usar funções duráveis para implementar esse padrão de fluxo de trabalho vem de sua capacidade de fazer pontos de verificação. Se o servidor falhar, o tempo de rede sair ou algum outro problema ocorrer, as funções duráveis podem ser retomadas a partir do último estado conhecido e continuar executando seu fluxo de trabalho mesmo que esteja em outro servidor.

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

Na amostra de código `CallActivityAsync` anterior, a função é responsável por executar uma determinada atividade em uma máquina virtual no data center. Quando a espera retornar e a Tarefa subjacente for concluída, a execução será registrada na tabela de história. O código na função orquestrador pode fazer uso de qualquer um dos construções familiares da Biblioteca Paralela da Tarefa e das palavras-chave assinuosas/aguardar.

O código a seguir é um `ProcessPayment` exemplo simplificado de como o método pode se parecer:

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

Em alguns casos, os fluxos de trabalho podem conter atividades que levam um período relativamente longo de tempo para serem concluídos. Imagine um processo que inicia o backup de arquivos de mídia em armazenamento blob. Dependendo do tamanho e quantidade dos arquivos de mídia, este processo de backup pode levar horas para ser concluído.

Neste cenário, `DurableOrchestrationClient`a capacidade de verificar o status de um fluxo de trabalho em execução torna-se útil. Ao usar `HttpTrigger` um para iniciar `CreateCheckStatusResponse` um fluxo de trabalho, `HttpResponseMessage`o método pode ser usado para retornar uma instância de . Essa resposta fornece ao cliente um URI na carga útil que pode ser usado para verificar o status do processo de execução.

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

O resultado amostral abaixo mostra a estrutura da carga de resposta.

```json
{
    "id": "instanceId",
    "statusQueryGetUri": "http://host/statusUri",
    "sendEventPostUri": "http://host/eventUri",
    "terminatePostUri": "http://host/terminateUri"
}
```

Usando seu cliente HTTP preferido, as solicitações GET podem ser feitas ao URI em statusQueryGetUri para inspecionar o status do fluxo de trabalho em execução. A resposta de status retornada deve se assemelhar ao seguinte código.

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

À medida que o processo continua, a resposta de status será alterado para **Falha** ou **Concluído**. Após a conclusão bem-sucedida, a propriedade **de saída** na carga útil conterá quaisquer dados retornados.

## <a name="monitoring"></a>Monitoramento

Para tarefas simples e recorrentes, `TimerTrigger` o Azure Functions fornece o que pode ser agendado com base em uma expressão CRON. O temporizador funciona bem para tarefas simples e de curta duração, mas pode haver cenários onde é necessário agendamento mais flexível. Este cenário é quando o padrão de monitoramento e funções duráveis podem ajudar.

Funções duráveis permitem intervalos de agendamento flexíveis, gerenciamento de vida e criação de múltiplos processos de monitor a partir de uma única função de orquestração. Um caso de uso para essa funcionalidade pode ser criar observadores para mudanças de preço de ações que se completam uma vez que um determinado limite é atingido.

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

`DurableOrchestrationContext`O `CreateTimer` método de 'configura o cronograma para a próxima invocação do loop para verificar as alterações no preço das ações. `DurableOrchestrationContext`também tem `CurrentUtcDateTime` uma propriedade para obter o valor datetime atual em UTC. É melhor usar esta propriedade `DateTime.UtcNow` em vez de porque ela é facilmente ridicularizada para testes.

## <a name="recommended-resources"></a>Recursos recomendados

- [Durable Functions do Azure](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
- [Teste unitário em .NET Core e .NET Standard](../../core/testing/index.md)

>[!div class="step-by-step"]
>[Próximo](durable-azure-functions.md)
>[anterior](serverless-business-scenarios.md)
