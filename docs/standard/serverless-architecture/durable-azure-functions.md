---
title: Funções duráveis do Azure – aplicativos sem servidor
description: As funções duráveis do Azure estendem o tempo de execução do Azure Functions para permitir que os fluxos de trabalho com monitoração de estado no código.
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 8ad354e1708eb88f016130f8235f534b967eb122
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147295"
---
# <a name="durable-azure-functions"></a>Funções duráveis do Azure

Ao criar aplicativos sem servidor com o Azure Functions, suas operações normalmente serão criadas para executar de maneira sem monitoração de estado. O motivo para essa escolha de design é porque, como as escalas de plataforma, torna-se difícil saber quais servidores o código está em execução no. Também é difícil saber quantas instâncias estão ativas em qualquer momento determinado. No entanto, há classes de aplicativos que exigem o estado atual de um processo conhecido. Considere o processo de enviar um pedido para uma loja online. A operação de check-out pode ser um fluxo de trabalho é composto de várias operações que precisam saber o estado do processo. Essas informações podem incluir o estoque de produto, se o cliente tiver quaisquer créditos em sua conta e também os resultados do processamento de cartão de crédito. Essas operações pode ser facilmente seus próprios fluxos de trabalho internos ou até mesmo os serviços de sistemas de terceiros.

Vários padrões de hoje existem que ajudam com a coordenação do estado do aplicativo entre sistemas internos e externos. É comum ao se deparar com soluções que dependem de sistemas centralizados de enfileiramento de mensagens, repositórios de chave-valor distribuídos ou bancos de dados compartilhados para gerenciar esse estado. No entanto, esses são todos os outros recursos que agora precisam ser provisionados e gerenciados. Em um ambiente sem servidor, seu código pode se tornar complicado tentando coordenar com esses recursos manualmente. O Azure Functions oferece uma alternativa para a criação de funções com estado chamadas de funções duráveis.

As funções duráveis é uma extensão para o tempo de execução de funções do Azure que permite a definição de fluxos de trabalho com monitoração de estado no código. Ao dividir os fluxos de trabalho em atividades, a extensão funções duráveis pode gerenciar o estado, criar pontos de verificação de progresso e lidar com a distribuição das chamadas de função em servidores. Em segundo plano, ele torna o uso de uma conta de armazenamento do Azure para manter o histórico de execução, agendam funções de atividade e recuperar respostas. Seu código sem servidor nunca deve interagir com as informações persistentes na conta de armazenamento e normalmente não é algo com que os desenvolvedores precisam interagir.

## <a name="triggering-a-stateful-workflow"></a>Disparar um fluxo de trabalho com monitoração de estado

Fluxos de trabalho com monitoração de estado nas funções duráveis podem ser divididos em dois componentes intrínseco; gatilhos de orquestração e a atividade. Gatilhos e associações são os principais componentes usados pelas funções do Azure para habilitar funções sem servidor para ser notificado quando iniciar, receber de entrada e retornam os resultados.

### <a name="working-with-the-orchestration-client"></a>Trabalhando com o cliente de orquestração

Orquestrações são exclusivas em comparação com outros estilos de operações de disparadas no Azure Functions. As funções duráveis permitem a execução de funções que podem levar horas ou mesmo dias para ser concluída. Esse tipo de comportamento vem com a necessidade de capaz de verificar o status de uma orquestração em execução, preventivamente encerrar ou enviar notificações de eventos externos.

Para tais casos, a extensão de funções duráveis fornece o `DurableOrchestrationClient` orquestrada de classe que permite que você interaja com funções. Obter acesso ao cliente de orquestração usando o `OrchestrationClientAttribute` associação. Em geral, você deve incluir esse atributo com outro tipo de gatilho, como um `HttpTrigger` ou `ServiceBusTrigger`. Depois que a função de origem foi disparada, o cliente de orquestração pode ser usado para iniciar uma função de orquestrador.

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

### <a name="the-orchestrator-function"></a>A função de orquestrador

Anotar uma função com o OrchestrationTriggerAttribute nas marcas do Azure Functions que funcionam como uma função de orquestrador. Ele é responsável por gerenciar as várias atividades que compõem seu fluxo de trabalho com monitoração de estado.

Funções de orquestrador não consegue fazer uso de associações que não seja o OrchestrationTriggerAttribute. Esse atributo só pode ser usado com um tipo de parâmetro DurableOrchestrationContext. Não há outras entradas podem ser usadas, pois não há suporte para desserialização de entradas na assinatura de função. Para obter as entradas fornecidas pelo cliente de orquestração, o GetInput\<T\> método deve ser usado.

Além disso, os tipos de retorno das funções de orquestração devem ser vazio, Task ou um valor de serializável JSON.

> *Código de tratamento de erro foram deixado de fora para fins de brevidade*

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

Várias instâncias de uma orquestração podem ser iniciado e em execução ao mesmo tempo. Chamar o `StartNewAsync` método no `DurableOrchestrationClient` inicia uma nova instância da orquestração. O método retorna um `Task<string>` que é concluída quando a orquestração foi iniciada. Uma exceção do tipo `TimeoutException` obtém gerada se a orquestração ainda não começou dentro de 30 segundos.

Concluídas `Task<string>` de `StartNewAsync` deve conter a ID exclusiva da instância de orquestração. A ID da instância pode ser usada para invocar operações nessa orquestração específica. A orquestração pode ser consultada para obter o status ou enviada notificações de eventos.

### <a name="the-activity-functions"></a>As funções de atividade

Funções de atividade são as operações discretas que são compostas juntas em uma função de orquestração para criar o fluxo de trabalho. Aqui é onde a maior parte do trabalho real podem ocorrer. Eles representam a lógica de negócios, processos em execução e as peças do quebra-cabeça para uma solução mais ampla de comprimento.

O `ActivityTriggerAttribute` é usado para anotar um parâmetro de função do tipo `DurableActivityContext`. Usando a anotação informa o tempo de execução que a função destina-se a ser usado como uma função de atividade. Valores de entrada para funções de atividade são recuperados usando o `GetInput<T>` método da `DurableActivityContext` parâmetro.

Semelhante às funções de orquestração, os tipos de retorno de funções de atividade devem ser vazio, Task ou um valor de serializável JSON.

Todas as exceções sem tratamento que obterem geradas dentro de funções de atividade obterá enviadas para a função de orquestrador de chamada e apresentadas como um `TaskFailedException`. Neste ponto, o erro pode ser detectado e conectado o orchestrator e a atividade pode ser repetida.

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

* [Funções duráveis](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
* [Associações para funções duráveis](https://docs.microsoft.com/azure/azure-functions/durable-functions-bindings)
* [Gerenciar instâncias nas funções duráveis](https://docs.microsoft.com/azure/azure-functions/durable-functions-instance-management)

>[!div class="step-by-step"]
>[Anterior](event-grid.md)
>[Próximo](orchestration-patterns.md)