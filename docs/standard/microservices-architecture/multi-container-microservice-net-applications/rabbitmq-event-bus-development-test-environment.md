---
title: Implementando um barramento de evento com RabbitMQ para o ambiente de desenvolvimento ou teste
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Implementando um barramento de evento com RabbitMQ para o ambiente de desenvolvimento ou teste"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: f58d355b6f5fd31a21791d3b072c77f70f90c387
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a><span data-ttu-id="c872e-104">Implementando um barramento de evento com RabbitMQ para o ambiente de desenvolvimento ou teste</span><span class="sxs-lookup"><span data-stu-id="c872e-104">Implementing an event bus with RabbitMQ for the development or test environment</span></span>

<span data-ttu-id="c872e-105">Deve começar dizendo que, se você criar o barramento de evento personalizado com base em RabbitMQ em execução em um contêiner, que o aplicativo eShopOnContainers, ele deve ser usado somente para seus ambientes de desenvolvimento e teste.</span><span class="sxs-lookup"><span data-stu-id="c872e-105">We should start by saying that if you create your custom event bus based on RabbitMQ running in a container, as the eShopOnContainers application does, it should be used only for your development and test environments.</span></span> <span data-ttu-id="c872e-106">Você não deve usá-lo para o seu ambiente de produção, a menos que você está criando-o como parte de um barramento de serviço pronto para produção.</span><span class="sxs-lookup"><span data-stu-id="c872e-106">You should not use it for your production environment, unless you are building it as a part of a production-ready service bus.</span></span> <span data-ttu-id="c872e-107">Barramento de evento personalizado simples talvez não tenha muitos recursos críticos prontos para produção que tem um barramento de serviço comercial.</span><span class="sxs-lookup"><span data-stu-id="c872e-107">A simple custom event bus might be missing many production-ready critical features that a commercial service bus has.</span></span>

<span data-ttu-id="c872e-108">A implementação personalizada de eShopOnContainers de um barramento de evento é basicamente uma biblioteca usando a API RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="c872e-108">The eShopOnContainers custom implementation of an event bus is basically a library using the RabbitMQ API.</span></span> <span data-ttu-id="c872e-109">A implementação permite microservices assinar eventos, publicar eventos e receber eventos, como mostrado na Figura 8-21.</span><span class="sxs-lookup"><span data-stu-id="c872e-109">The implementation lets microservices subscribe to events, publish events, and receive events, as shown in Figure 8-21.</span></span>

![](./media/image22.png)

<span data-ttu-id="c872e-110">**Figura 8-21.**</span><span class="sxs-lookup"><span data-stu-id="c872e-110">**Figure 8-21.**</span></span> <span data-ttu-id="c872e-111">RabbitMQ implementação de um barramento de evento</span><span class="sxs-lookup"><span data-stu-id="c872e-111">RabbitMQ implementation of an event bus</span></span>

<span data-ttu-id="c872e-112">No código, a classe de EventBusRabbitMQ implementa a interface IEventBus genérica.</span><span class="sxs-lookup"><span data-stu-id="c872e-112">In the code, the EventBusRabbitMQ class implements the generic IEventBus interface.</span></span> <span data-ttu-id="c872e-113">Isso se baseia na injeção de dependência para que você pode trocar dessa versão de desenvolvimento/teste para uma versão de produção.</span><span class="sxs-lookup"><span data-stu-id="c872e-113">This is based on Dependency Injection so that you can swap from this dev/test version to a production version.</span></span>

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
```

<span data-ttu-id="c872e-114">A implementação de RabbitMQ do barramento de evento de desenvolvimento/teste de exemplo é código padronizado.</span><span class="sxs-lookup"><span data-stu-id="c872e-114">The RabbitMQ implementation of a sample dev/test event bus is boilerplate code.</span></span> <span data-ttu-id="c872e-115">Ele tem que lidar com a conexão ao servidor RabbitMQ e fornecer o código para a publicação de um evento de mensagem para filas.</span><span class="sxs-lookup"><span data-stu-id="c872e-115">It has to handle the connection to the RabbitMQ server and provide code for publishing a message event to the queues.</span></span> <span data-ttu-id="c872e-116">Ele também tem que implementar um dicionário de coleções de manipuladores de eventos de integração para cada tipo de evento; Esses tipos de evento podem ter uma instanciação diferente e diferentes assinaturas do microsserviço cada destinatário, conforme mostrado na Figura 8-21.</span><span class="sxs-lookup"><span data-stu-id="c872e-116">It also has to implement a dictionary of collections of integration event handlers for each event type; these event types can have a different instantiation and different subscriptions for each receiver microservice, as shown in Figure 8-21.</span></span>

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a><span data-ttu-id="c872e-117">Implementando um simples publicar método com RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="c872e-117">Implementing a simple publish method with RabbitMQ</span></span>

<span data-ttu-id="c872e-118">O código a seguir é parte da implementação do barramento de evento eShopOnContainers para RabbitMQ, para que você normalmente não precisa codificá-la, a menos que você estiver fazendo aprimoramentos.</span><span class="sxs-lookup"><span data-stu-id="c872e-118">The following code is part of the eShopOnContainers event bus implementation for RabbitMQ, so you usually do not need to code it unless you are making improvements.</span></span> <span data-ttu-id="c872e-119">O código obtém uma conexão e canal para RabbitMQ, cria uma mensagem e, em seguida, publica a mensagem na fila.</span><span class="sxs-lookup"><span data-stu-id="c872e-119">The code gets a connection and channel to RabbitMQ, creates a message, and then publishes the message into the queue.</span></span>

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

<span data-ttu-id="c872e-120">O [código real](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) de publicar método no aplicativo eShopOnContainers é aprimorado usando um [Polly](https://github.com/App-vNext/Polly) política, que repete a tarefa de um determinado número de vezes que no caso do contêiner de RabbitMQ é de repetição não está pronto.</span><span class="sxs-lookup"><span data-stu-id="c872e-120">The [actual code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) of the Publish method in the eShopOnContainers application is improved by using a [Polly](https://github.com/App-vNext/Polly) retry policy, which retries the task a certain number of times in case the RabbitMQ container is not ready.</span></span> <span data-ttu-id="c872e-121">Isso pode ocorrer quando compor docker está iniciando os contêineres; Por exemplo, o contêiner de RabbitMQ pode iniciar mais lentamente do que os outros contêineres.</span><span class="sxs-lookup"><span data-stu-id="c872e-121">This can occur when docker-compose is starting the containers; for example, the RabbitMQ container might start more slowly than the other containers.</span></span>

<span data-ttu-id="c872e-122">Como mencionado anteriormente, há muitas configurações possíveis em RabbitMQ, portanto esse código deve ser usado apenas para ambientes de desenvolvimento e teste.</span><span class="sxs-lookup"><span data-stu-id="c872e-122">As mentioned earlier, there are many possible configurations in RabbitMQ, so this code should be used only for dev/test environments.</span></span>

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a><span data-ttu-id="c872e-123">Implementar o código de assinatura com a API RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="c872e-123">Implementing the subscription code with the RabbitMQ API</span></span>

<span data-ttu-id="c872e-124">Como com o código de publicação, o código a seguir é uma simplificação de parte da implementação do barramento de eventos para RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="c872e-124">As with the publish code, the following code is a simplification of part of the event bus implementation for RabbitMQ.</span></span> <span data-ttu-id="c872e-125">Novamente, você normalmente não precisa alterá-la, a menos que são melhorá-lo.</span><span class="sxs-lookup"><span data-stu-id="c872e-125">Again, you usually do not need to change it unless you are improving it.</span></span>

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Member objects and other methods ...
    // ...
    public void Subscribe<T>(IIntegrationEventHandler<T> handler)
        where T : IntegrationEvent
    {
        var eventName = typeof(T).Name;
        if (_handlers.ContainsKey(eventName))
        {
            _handlers[eventName].Add(handler);
        }
        else
        {
            var channel = GetChannel();
            channel.QueueBind(queue: _queueName,
                exchange: _brokerName,
                routingKey: eventName);
            _handlers.Add(eventName, new List<IIntegrationEventHandler>());
            _handlers[eventName].Add(handler);
            _eventTypes.Add(typeof(T));
        }
    }
}
```

<span data-ttu-id="c872e-126">Cada tipo de evento tem um canal relacionado para obter eventos do RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="c872e-126">Each event type has a related channel to get events from RabbitMQ.</span></span> <span data-ttu-id="c872e-127">Em seguida, você pode ter tantos manipuladores de eventos por tipo de canal e de evento conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="c872e-127">You can then have as many event handlers per channel and event type as needed.</span></span>

<span data-ttu-id="c872e-128">O método Subscribe aceita um objeto IIntegrationEventHandler, que é como um método de retorno de chamada no microsserviço atual, além de seu objeto IntegrationEvent relacionado.</span><span class="sxs-lookup"><span data-stu-id="c872e-128">The Subscribe method accepts an IIntegrationEventHandler object, which is like a callback method in the current microservice, plus its related IntegrationEvent object.</span></span> <span data-ttu-id="c872e-129">O código, em seguida, adiciona o manipulador de eventos à lista de manipuladores de eventos que cada tipo de evento de integração pode ter por cliente microsserviço.</span><span class="sxs-lookup"><span data-stu-id="c872e-129">The code then adds that event handler to the list of event handlers that each integration event type can have per client microservice.</span></span> <span data-ttu-id="c872e-130">Se o código do cliente não já inscrito no evento, o código cria um canal para o tipo de evento para que ela possa receber eventos em um estilo de envio de RabbitMQ quando esse evento é publicado a partir de qualquer outro serviço.</span><span class="sxs-lookup"><span data-stu-id="c872e-130">If the client code has not already been subscribed to the event, the code creates a channel for the event type so it can receive events in a push style from RabbitMQ when that event is published from any other service.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="c872e-131">[Anterior] (integração-evento-com base-microsserviço-communications.md) [Avançar] (events.md assinar)</span><span class="sxs-lookup"><span data-stu-id="c872e-131">[Previous] (integration-event-based-microservice-communications.md) [Next] (subscribe-events.md)</span></span>
