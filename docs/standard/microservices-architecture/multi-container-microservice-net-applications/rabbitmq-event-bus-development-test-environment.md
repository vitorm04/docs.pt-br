---
title: Implementando um barramento de eventos com o RabbitMQ para o ambiente de desenvolvimento ou de teste
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Implementando um barramento de eventos com RabbitMQ para o ambiente de desenvolvimento ou de teste
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: fb9bf51d947774cddd7b42ade0f05abc8fb3d7e9
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37104747"
---
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a><span data-ttu-id="d0870-103">Implementando um barramento de eventos com o RabbitMQ para o ambiente de desenvolvimento ou de teste</span><span class="sxs-lookup"><span data-stu-id="d0870-103">Implementing an event bus with RabbitMQ for the development or test environment</span></span>

<span data-ttu-id="d0870-104">Devemos começar dizendo que, se você criar seu barramento de eventos personalizado com base no RabbitMQ em execução em um contêiner, como o aplicativo eShopOnContainers faz, ele deverá ser usado apenas para seus ambientes de desenvolvimento e teste.</span><span class="sxs-lookup"><span data-stu-id="d0870-104">We should start by saying that if you create your custom event bus based on RabbitMQ running in a container, as the eShopOnContainers application does, it should be used only for your development and test environments.</span></span> <span data-ttu-id="d0870-105">Você não deve usá-lo para o seu ambiente de produção, a menos que o esteja criando como parte de um barramento de serviço pronto para produção.</span><span class="sxs-lookup"><span data-stu-id="d0870-105">You should not use it for your production environment, unless you are building it as a part of a production-ready service bus.</span></span> <span data-ttu-id="d0870-106">Um barramento de eventos personalizado simples talvez não tenha muitos recursos críticos prontos para produção que um barramento de serviço comercial tem.</span><span class="sxs-lookup"><span data-stu-id="d0870-106">A simple custom event bus might be missing many production-ready critical features that a commercial service bus has.</span></span>

<span data-ttu-id="d0870-107">Uma da implementação personalizada do barramento de eventos no eShopOnContainers é basicamente uma biblioteca que usa a API do RabbitMQ (há outra implementação baseada no Barramento de Serviço do Azure).</span><span class="sxs-lookup"><span data-stu-id="d0870-107">One of the event bus custom implementation in eShopOnContainers is basically a library using the RabbitMQ API (There’s another implementation based on Azure Service Bus).</span></span> 

<span data-ttu-id="d0870-108">A implementação do barramento de eventos com RabbitMQ permite que os microsserviços assinem, publiquem e recebam eventos, conforme mostrado na Figura 8-21.</span><span class="sxs-lookup"><span data-stu-id="d0870-108">The event bus implementation with RabbitMQ lets microservices subscribe to events, publish events, and receive events, as shown in Figure 8-21.</span></span>

![](./media/image22.png)

<span data-ttu-id="d0870-109">**Figura 8-21.**</span><span class="sxs-lookup"><span data-stu-id="d0870-109">**Figure 8-21.**</span></span> <span data-ttu-id="d0870-110">Implementação de um barramento de eventos do RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="d0870-110">RabbitMQ implementation of an event bus</span></span>

<span data-ttu-id="d0870-111">No código, a classe EventBusRabbitMQ implementa a interface IEventBus genérica.</span><span class="sxs-lookup"><span data-stu-id="d0870-111">In the code, the EventBusRabbitMQ class implements the generic IEventBus interface.</span></span> <span data-ttu-id="d0870-112">Isso se baseia na Injeção de dependência para que você possa trocar dessa versão de Desenvolvimento/Teste para uma versão de produção.</span><span class="sxs-lookup"><span data-stu-id="d0870-112">This is based on Dependency Injection so that you can swap from this dev/test version to a production version.</span></span>

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
```

<span data-ttu-id="d0870-113">A implementação do RabbitMQ de um barramento de eventos de Desenvolvimento/Teste de exemplo é um código clichê.</span><span class="sxs-lookup"><span data-stu-id="d0870-113">The RabbitMQ implementation of a sample dev/test event bus is boilerplate code.</span></span> <span data-ttu-id="d0870-114">Ele precisa lidar com a conexão com o servidor do RabbitMQ e fornecer o código para a publicação de um evento de mensagem nas filas.</span><span class="sxs-lookup"><span data-stu-id="d0870-114">It has to handle the connection to the RabbitMQ server and provide code for publishing a message event to the queues.</span></span> <span data-ttu-id="d0870-115">Ele também precisa implementar um dicionário de coleções de manipuladores de eventos de integração para cada tipo de evento; esses tipos de evento podem ter uma instanciação diferente e diferentes assinaturas para cada microsserviço receptor, conforme mostrado na Figura 8-21.</span><span class="sxs-lookup"><span data-stu-id="d0870-115">It also has to implement a dictionary of collections of integration event handlers for each event type; these event types can have a different instantiation and different subscriptions for each receiver microservice, as shown in Figure 8-21.</span></span>

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a><span data-ttu-id="d0870-116">Implementando um método de publicação simples com RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="d0870-116">Implementing a simple publish method with RabbitMQ</span></span>

<span data-ttu-id="d0870-117">O código a seguir faz parte de uma implementação de barramento de eventos simplificado para RabbitMQ, aprimorado no [código real](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) de eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="d0870-117">The following code is part is a simplified event bus implementation for RabbitMQ, improved in the [actual code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) of eShopOnContainers.</span></span> <span data-ttu-id="d0870-118">Normalmente, não é necessário codificá-lo, a menos que você esteja fazendo aprimoramentos.</span><span class="sxs-lookup"><span data-stu-id="d0870-118">You usually do not need to code it unless you are making improvements.</span></span> <span data-ttu-id="d0870-119">O código obtém uma conexão e um canal para o RabbitMQ, cria uma mensagem e, em seguida, publica-a na fila.</span><span class="sxs-lookup"><span data-stu-id="d0870-119">The code gets a connection and channel to RabbitMQ, creates a message, and then publishes the message into the queue.</span></span>

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Member objects and other methods ...
    // ...

    public void Publish(IntegrationEvent @event)
    {
        var eventName = @event.GetType().Name;
        var factory = new ConnectionFactory() { HostName = _connectionString };
        using (var connection = factory.CreateConnection())
        using (var channel = connection.CreateModel())
        {
            channel.ExchangeDeclare(exchange: _brokerName,
                type: "direct");
            string message = JsonConvert.SerializeObject(@event);
            var body = Encoding.UTF8.GetBytes(message);
            channel.BasicPublish(exchange: _brokerName,
                routingKey: eventName,
                basicProperties: null,
                body: body);
       }
    }
}
```

<span data-ttu-id="d0870-120">O [código real](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) do método de publicação no aplicativo eShopOnContainers é aprimorado usando uma política de repetição [Polly](https://github.com/App-vNext/Polly), que repete a tarefa um determinado número de vezes caso o contêiner do RabbitMQ não esteja pronto.</span><span class="sxs-lookup"><span data-stu-id="d0870-120">The [actual code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) of the Publish method in the eShopOnContainers application is improved by using a [Polly](https://github.com/App-vNext/Polly) retry policy, which retries the task a certain number of times in case the RabbitMQ container is not ready.</span></span> <span data-ttu-id="d0870-121">Isso pode ocorrer quando docker-compose está iniciando os contêineres; por exemplo, o contêiner do RabbitMQ pode ser iniciado mais lentamente do que outros contêineres.</span><span class="sxs-lookup"><span data-stu-id="d0870-121">This can occur when docker-compose is starting the containers; for example, the RabbitMQ container might start more slowly than the other containers.</span></span>

<span data-ttu-id="d0870-122">Conforme mencionado anteriormente, há muitas configurações possíveis no RabbitMQ. Portanto, esse código deve ser usado apenas para ambientes de Desenvolvimento/Teste.</span><span class="sxs-lookup"><span data-stu-id="d0870-122">As mentioned earlier, there are many possible configurations in RabbitMQ, so this code should be used only for dev/test environments.</span></span>

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a><span data-ttu-id="d0870-123">Implementando o código de assinatura com a API do RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="d0870-123">Implementing the subscription code with the RabbitMQ API</span></span>

<span data-ttu-id="d0870-124">Como acontece com o código de publicação, o código a seguir é uma simplificação de parte da implementação do barramento de eventos para RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="d0870-124">As with the publish code, the following code is a simplification of part of the event bus implementation for RabbitMQ.</span></span> <span data-ttu-id="d0870-125">Mais uma vez, geralmente não é necessário alterá-lo, a menos que você o esteja aprimorando.</span><span class="sxs-lookup"><span data-stu-id="d0870-125">Again, you usually do not need to change it unless you are improving it.</span></span>

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Member objects and other methods ...
    // ...

    public void Subscribe<T, TH>()
        where T : IntegrationEvent
        where TH : IIntegrationEventHandler<T>
    {
        var eventName = _subsManager.GetEventKey<T>();
        
        var containsKey = _subsManager.HasSubscriptionsForEvent(eventName);
        if (!containsKey)
        {
            if (!_persistentConnection.IsConnected)
            {
                _persistentConnection.TryConnect();
            }

            using (var channel = _persistentConnection.CreateModel())
            {
                channel.QueueBind(queue: _queueName,
                                    exchange: BROKER_NAME,
                                    routingKey: eventName);
            }
        }

        _subsManager.AddSubscription<T, TH>();
    }
}
```

<span data-ttu-id="d0870-126">Cada tipo de evento tem um canal relacionado para obter eventos do RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="d0870-126">Each event type has a related channel to get events from RabbitMQ.</span></span> <span data-ttu-id="d0870-127">Em seguida, é possível ter tantos manipuladores de eventos por tipo de evento e de canal conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="d0870-127">You can then have as many event handlers per channel and event type as needed.</span></span>

<span data-ttu-id="d0870-128">O método Subscribe aceita um objeto IIntegrationEventHandler, que é como um método de retorno de chamada no microsserviço atual, além de seu objeto IntegrationEvent relacionado.</span><span class="sxs-lookup"><span data-stu-id="d0870-128">The Subscribe method accepts an IIntegrationEventHandler object, which is like a callback method in the current microservice, plus its related IntegrationEvent object.</span></span> <span data-ttu-id="d0870-129">O código, então, adiciona o manipulador de eventos à lista de manipuladores de eventos que cada tipo de evento de integração pode ter por microsserviço do cliente.</span><span class="sxs-lookup"><span data-stu-id="d0870-129">The code then adds that event handler to the list of event handlers that each integration event type can have per client microservice.</span></span> <span data-ttu-id="d0870-130">Se o código do cliente ainda não tiver assinado o evento, o código criará um canal para o tipo de evento para que ele possa receber eventos em um estilo de push do RabbitMQ quando esse evento for publicado de qualquer outro serviço.</span><span class="sxs-lookup"><span data-stu-id="d0870-130">If the client code has not already been subscribed to the event, the code creates a channel for the event type so it can receive events in a push style from RabbitMQ when that event is published from any other service.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="d0870-131">[Anterior](integration-event-based-microservice-communications.md)
[Próximo](subscribe-events.md)</span><span class="sxs-lookup"><span data-stu-id="d0870-131">[Previous](integration-event-based-microservice-communications.md)
[Next](subscribe-events.md)</span></span>
