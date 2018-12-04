---
title: Implementando um barramento de eventos com o RabbitMQ para o ambiente de desenvolvimento ou de teste
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Use o RabbitMQ para implementar mensagens de barramento de eventos para eventos de integração para os ambientes de desenvolvimento ou de teste.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: 6d855b56a7fd00b316dde599683900ad2db758d7
ms.sourcegitcommit: 7f7664837d35320a0bad3f7e4ecd68d6624633b2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2018
ms.locfileid: "52672339"
---
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a><span data-ttu-id="07256-103">Implementando um barramento de eventos com o RabbitMQ para o ambiente de desenvolvimento ou de teste</span><span class="sxs-lookup"><span data-stu-id="07256-103">Implementing an event bus with RabbitMQ for the development or test environment</span></span>

<span data-ttu-id="07256-104">Devemos começar dizendo que, se você criar seu barramento de eventos personalizado com base no RabbitMQ em execução em um contêiner, como o aplicativo eShopOnContainers faz, ele deverá ser usado apenas para seus ambientes de desenvolvimento e teste.</span><span class="sxs-lookup"><span data-stu-id="07256-104">We should start by saying that if you create your custom event bus based on RabbitMQ running in a container, as the eShopOnContainers application does, it should be used only for your development and test environments.</span></span> <span data-ttu-id="07256-105">Você não deve usá-lo para o seu ambiente de produção, a menos que o esteja criando como parte de um barramento de serviço pronto para produção.</span><span class="sxs-lookup"><span data-stu-id="07256-105">You should not use it for your production environment, unless you are building it as a part of a production-ready service bus.</span></span> <span data-ttu-id="07256-106">Um barramento de eventos personalizado simples talvez não tenha muitos recursos críticos prontos para produção que um barramento de serviço comercial tem.</span><span class="sxs-lookup"><span data-stu-id="07256-106">A simple custom event bus might be missing many production-ready critical features that a commercial service bus has.</span></span>

<span data-ttu-id="07256-107">Uma da implementação personalizada do barramento de eventos no eShopOnContainers é basicamente uma biblioteca que usa a API do RabbitMQ (há outra implementação baseada no Barramento de Serviço do Azure).</span><span class="sxs-lookup"><span data-stu-id="07256-107">One of the event bus custom implementation in eShopOnContainers is basically a library using the RabbitMQ API (There’s another implementation based on Azure Service Bus).</span></span>

<span data-ttu-id="07256-108">A implementação do barramento de eventos com RabbitMQ permite que os microsserviços assinem, publiquem e recebam eventos, conforme mostrado na Figura 6-21.</span><span class="sxs-lookup"><span data-stu-id="07256-108">The event bus implementation with RabbitMQ lets microservices subscribe to events, publish events, and receive events, as shown in Figure 6-21.</span></span>

![O RabbitMQ é um intermediário entre o publicador da mensagem e os assinantes, para tratar da distribuição.](./media/image22.png)

<span data-ttu-id="07256-110">**Figura 6-21.**</span><span class="sxs-lookup"><span data-stu-id="07256-110">**Figure 6-21.**</span></span> <span data-ttu-id="07256-111">Implementação de um barramento de eventos do RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="07256-111">RabbitMQ implementation of an event bus</span></span>

<span data-ttu-id="07256-112">No código, a classe EventBusRabbitMQ implementa a interface IEventBus genérica.</span><span class="sxs-lookup"><span data-stu-id="07256-112">In the code, the EventBusRabbitMQ class implements the generic IEventBus interface.</span></span> <span data-ttu-id="07256-113">Isso se baseia na Injeção de dependência para que você possa trocar dessa versão de Desenvolvimento/Teste para uma versão de produção.</span><span class="sxs-lookup"><span data-stu-id="07256-113">This is based on Dependency Injection so that you can swap from this dev/test version to a production version.</span></span>

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
```

<span data-ttu-id="07256-114">A implementação do RabbitMQ de um barramento de eventos de Desenvolvimento/Teste de exemplo é um código clichê.</span><span class="sxs-lookup"><span data-stu-id="07256-114">The RabbitMQ implementation of a sample dev/test event bus is boilerplate code.</span></span> <span data-ttu-id="07256-115">Ele precisa lidar com a conexão com o servidor do RabbitMQ e fornecer o código para a publicação de um evento de mensagem nas filas.</span><span class="sxs-lookup"><span data-stu-id="07256-115">It has to handle the connection to the RabbitMQ server and provide code for publishing a message event to the queues.</span></span> <span data-ttu-id="07256-116">Ele também precisa implementar um dicionário de coleções de manipuladores de eventos de integração para cada tipo de evento; esses tipos de evento podem ter uma instanciação diferente e diferentes assinaturas para cada microsserviço receptor, conforme mostrado na Figura 6-21.</span><span class="sxs-lookup"><span data-stu-id="07256-116">It also has to implement a dictionary of collections of integration event handlers for each event type; these event types can have a different instantiation and different subscriptions for each receiver microservice, as shown in Figure 6-21.</span></span>

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a><span data-ttu-id="07256-117">Implementando um método de publicação simples com RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="07256-117">Implementing a simple publish method with RabbitMQ</span></span>

<span data-ttu-id="07256-118">O código a seguir faz parte de uma implementação de barramento de eventos simplificado para RabbitMQ, aprimorado no [código real](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) de eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="07256-118">The following code is part of a simplified event bus implementation for RabbitMQ, improved in the [actual code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) of eShopOnContainers.</span></span> <span data-ttu-id="07256-119">Normalmente, não é necessário codificá-lo, a menos que você esteja fazendo aprimoramentos.</span><span class="sxs-lookup"><span data-stu-id="07256-119">You usually do not need to code it unless you are making improvements.</span></span> <span data-ttu-id="07256-120">O código obtém uma conexão e um canal para o RabbitMQ, cria uma mensagem e, em seguida, publica-a na fila.</span><span class="sxs-lookup"><span data-stu-id="07256-120">The code gets a connection and channel to RabbitMQ, creates a message, and then publishes the message into the queue.</span></span>

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

<span data-ttu-id="07256-121">O [código real](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) do método de publicação no aplicativo eShopOnContainers é aprimorado usando uma política de repetição [Polly](https://github.com/App-vNext/Polly), que repete a tarefa um determinado número de vezes caso o contêiner do RabbitMQ não esteja pronto.</span><span class="sxs-lookup"><span data-stu-id="07256-121">The [actual code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) of the Publish method in the eShopOnContainers application is improved by using a [Polly](https://github.com/App-vNext/Polly) retry policy, which retries the task a certain number of times in case the RabbitMQ container is not ready.</span></span> <span data-ttu-id="07256-122">Isso pode ocorrer quando docker-compose está iniciando os contêineres; por exemplo, o contêiner do RabbitMQ pode ser iniciado mais lentamente do que outros contêineres.</span><span class="sxs-lookup"><span data-stu-id="07256-122">This can occur when docker-compose is starting the containers; for example, the RabbitMQ container might start more slowly than the other containers.</span></span>

<span data-ttu-id="07256-123">Conforme mencionado anteriormente, há muitas configurações possíveis no RabbitMQ. Portanto, esse código deve ser usado apenas para ambientes de Desenvolvimento/Teste.</span><span class="sxs-lookup"><span data-stu-id="07256-123">As mentioned earlier, there are many possible configurations in RabbitMQ, so this code should be used only for dev/test environments.</span></span>

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a><span data-ttu-id="07256-124">Implementando o código de assinatura com a API do RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="07256-124">Implementing the subscription code with the RabbitMQ API</span></span>

<span data-ttu-id="07256-125">Como acontece com o código de publicação, o código a seguir é uma simplificação de parte da implementação do barramento de eventos para RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="07256-125">As with the publish code, the following code is a simplification of part of the event bus implementation for RabbitMQ.</span></span> <span data-ttu-id="07256-126">Mais uma vez, geralmente não é necessário alterá-lo, a menos que você o esteja aprimorando.</span><span class="sxs-lookup"><span data-stu-id="07256-126">Again, you usually do not need to change it unless you are improving it.</span></span>

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

<span data-ttu-id="07256-127">Cada tipo de evento tem um canal relacionado para obter eventos do RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="07256-127">Each event type has a related channel to get events from RabbitMQ.</span></span> <span data-ttu-id="07256-128">Em seguida, é possível ter tantos manipuladores de eventos por tipo de evento e de canal conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="07256-128">You can then have as many event handlers per channel and event type as needed.</span></span>

<span data-ttu-id="07256-129">O método Subscribe aceita um objeto IIntegrationEventHandler, que é como um método de retorno de chamada no microsserviço atual, além de seu objeto IntegrationEvent relacionado.</span><span class="sxs-lookup"><span data-stu-id="07256-129">The Subscribe method accepts an IIntegrationEventHandler object, which is like a callback method in the current microservice, plus its related IntegrationEvent object.</span></span> <span data-ttu-id="07256-130">O código, então, adiciona o manipulador de eventos à lista de manipuladores de eventos que cada tipo de evento de integração pode ter por microsserviço do cliente.</span><span class="sxs-lookup"><span data-stu-id="07256-130">The code then adds that event handler to the list of event handlers that each integration event type can have per client microservice.</span></span> <span data-ttu-id="07256-131">Se o código do cliente ainda não tiver assinado o evento, o código criará um canal para o tipo de evento para que ele possa receber eventos em um estilo de push do RabbitMQ quando esse evento for publicado de qualquer outro serviço.</span><span class="sxs-lookup"><span data-stu-id="07256-131">If the client code has not already been subscribed to the event, the code creates a channel for the event type so it can receive events in a push style from RabbitMQ when that event is published from any other service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="07256-132">[Anterior](integration-event-based-microservice-communications.md)
>[Próximo](subscribe-events.md)</span><span class="sxs-lookup"><span data-stu-id="07256-132">[Previous](integration-event-based-microservice-communications.md)
[Next](subscribe-events.md)</span></span>