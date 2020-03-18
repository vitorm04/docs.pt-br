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
# <a name="durable-azure-functions"></a>Funções duráveis do Azure

Ao criar aplicativos sem servidor com funções do Azure, suas operações normalmente serão projetadas para serem executadas de forma apátrida. A razão para essa escolha de design é porque, à medida que a plataforma é dimensionada, torna-se difícil saber em quais servidores o código está sendo executado. Também fica difícil saber quantas instâncias estão ativas em um dado momento. No entanto, existem classes de aplicações que exigem que o estado atual de um processo seja conhecido. Considere o processo de envio de um pedido para uma loja online. A operação de checkout pode ser um fluxo de trabalho que é composto por múltiplas operações que precisam saber o estado do processo. Essas informações podem incluir o inventário do produto, se o cliente tiver algum crédito em sua conta, e também os resultados do processamento do cartão de crédito. Essas operações podem facilmente ser seus próprios fluxos de trabalho internos ou até mesmo serviços de sistemas de terceiros.

Existem hoje diversos padrões que auxiliam na coordenação do estado de aplicação entre sistemas internos e externos. É comum encontrar soluções que dependem de sistemas centralizados de fila, lojas de valor de chave distribuídas ou bancos de dados compartilhados para gerenciar esse estado. No entanto, todos esses são recursos adicionais que agora precisam ser provisionados e gerenciados. Em um ambiente sem servidor, seu código pode se tornar complicado tentando coordenar com esses recursos manualmente. O Azure Functions oferece uma alternativa para criar funções imponentes chamadas Funções Duráveis.

Durable Functions é uma extensão do tempo de execução funções do Azure que permite a definição de fluxos de trabalho estatais em código. Ao dividir os fluxos de trabalho em atividades, a extensão Funções Duráveis pode gerenciar o estado, criar pontos de verificação de progresso e lidar com a distribuição de chamadas de função entre servidores. Em segundo plano, ele faz uso de uma conta do Azure Storage para persistir o histórico de execução, agendar funções de atividade e recuperar respostas. Seu código sem servidor nunca deve interagir com informações perpersistentes nessa conta de armazenamento, e normalmente não é algo com o qual os desenvolvedores precisam interagir.

## <a name="triggering-a-stateful-workflow"></a>Desencadeando um fluxo de trabalho imponente

Fluxos de trabalho estatais em Funções Duráveis podem ser divididos em dois componentes intrínsecos; orquestração e ativação de atividade. Gatilhos e vinculações são componentes principais usados pelas funções do Azure para permitir que suas funções sem servidor sejam notificadas quando iniciar, receber entradas e retornar resultados.

### <a name="working-with-the-orchestration-client"></a>Trabalhando com o cliente orchestration

As orquestrações são únicas quando comparadas com outros estilos de operações desencadeadas em Funções Azure. Funções duráveis permitem a execução de funções que podem levar horas ou até dias para serem concluídas. Esse tipo de comportamento vem com a necessidade de verificar o status de uma orquestração em execução, encerrar preventivamente ou enviar notificações de eventos externos.

Para esses casos, a extensão `DurableOrchestrationClient` Funções Duráveis fornece a classe que permite interagir com funções orquestradas. Você tem acesso ao cliente de `OrchestrationClientAttribute` orquestração usando a vinculação. Geralmente, você incluiria esse atributo com outro `HttpTrigger` tipo `ServiceBusTrigger`de gatilho, como um ou . Uma vez que a função de origem tenha sido acionada, o cliente de orquestração pode ser usado para iniciar uma função orquestradora.

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

### <a name="the-orchestrator-function"></a>A função orquestradora

Anotando uma função com o OrchestrationTriggerAttribute em Funções Azure marca que funcionam como uma função orquestradora. É responsável por gerenciar as diversas atividades que compõem seu fluxo de trabalho imponente.

As funções do orquestrador não podem fazer uso de amarras diferentes do OrchestrationTriggerAttribute. Este atributo só pode ser usado com um tipo de parâmetro de DurableOrchestrationContext. Nenhum outro inputs pode ser usado, uma vez que a desserialização de entradas na assinatura da função não é suportada. Para obter entradas fornecidas pelo cliente de\<\> orquestração, o método GetInput T deve ser usado.

Além disso, os tipos de retorno das funções de orquestração devem ser vazios, tarefa ou um valor serializável JSON.

> *O código de manipulação de erros foi deixado de fora por brevidade*

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

Várias instâncias de uma orquestração podem ser iniciadas e funcionando ao mesmo tempo. Chamar `StartNewAsync` o método `DurableOrchestrationClient` nos lançamentos é uma nova instância da orquestração. O método `Task<string>` retorna um que se completa quando a orquestração começou. Uma exceção `TimeoutException` do tipo é lançada se a orquestração não começou dentro de 30 segundos.

O `Task<string>` completo `StartNewAsync` deve conter o ID único da instância de orquestração. Este ID de instância pode ser usado para invocar operações nessa orquestração específica. A orquestração pode ser consultada para o status ou notificações de eventos enviadas.

### <a name="the-activity-functions"></a>As funções de atividade

As funções de atividade são as operações discretas que são compostas juntas dentro de uma função de orquestração para criar o fluxo de trabalho. Aqui é onde a maior parte do trabalho real ocorreria. Eles representam a lógica do negócio, os processos de longo prazo e as peças do quebra-cabeça para uma solução maior.

O `ActivityTriggerAttribute` é usado para anotar um parâmetro `DurableActivityContext`de função do tipo . O uso da anotação informa o tempo de execução de que a função deve ser usada como função de atividade. Os valores de entrada para `GetInput<T>` as funções de atividade são recuperados usando o método do `DurableActivityContext` parâmetro.

Semelhante às funções de orquestração, os tipos de retorno das funções de atividade devem ser vazios, tarefas ou um valor serializável JSON.

Quaisquer exceções não manuseadas que sejam jogadas dentro das funções de `TaskFailedException`atividade serão enviadas para a função de orquestrador de chamadas e apresentadas como um . Neste ponto, o erro pode ser pego e registrado no orquestrador, e a atividade pode ser repetida novamente.

```csharp
[FunctionName("CheckAndReserveInventory")]
public static bool CheckAndReserveInventory([ActivityTrigger] DurableActivityContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    // Connect to inventory system and try to reserve items
    return true;
}
```

## <a name="recommended-resources"></a>Recursos recomendados

- [Funções duráveis](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
- [Vinculações para funções duráveis](https://docs.microsoft.com/azure/azure-functions/durable-functions-bindings)
- [Gerenciar instâncias em funções duráveis](https://docs.microsoft.com/azure/azure-functions/durable-functions-instance-management)

>[!div class="step-by-step"]
>[Próximo](event-grid.md)
>[anterior](orchestration-patterns.md)
