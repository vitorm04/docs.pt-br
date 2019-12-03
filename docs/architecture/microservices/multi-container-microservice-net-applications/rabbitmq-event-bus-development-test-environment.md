---
title: Implementando um barramento de eventos com o RabbitMQ para o ambiente de desenvolvimento ou de teste
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Use o RabbitMQ para implementar mensagens de barramento de eventos para eventos de integração para os ambientes de desenvolvimento ou de teste.
ms.date: 10/02/2018
ms.openlocfilehash: ba1cea9384893955ae0743ac8d6a34c350224cd5
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711193"
---
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a><span data-ttu-id="911c5-103">Implementando um barramento de eventos com o RabbitMQ para o ambiente de desenvolvimento ou de teste</span><span class="sxs-lookup"><span data-stu-id="911c5-103">Implementing an event bus with RabbitMQ for the development or test environment</span></span>

<span data-ttu-id="911c5-104">Devemos começar dizendo que, se você criar seu barramento de eventos personalizado com base no RabbitMQ em execução em um contêiner, como o aplicativo eShopOnContainers faz, ele deverá ser usado apenas para seus ambientes de desenvolvimento e teste.</span><span class="sxs-lookup"><span data-stu-id="911c5-104">We should start by saying that if you create your custom event bus based on RabbitMQ running in a container, as the eShopOnContainers application does, it should be used only for your development and test environments.</span></span> <span data-ttu-id="911c5-105">Você não deve usá-lo para o seu ambiente de produção, a menos que o esteja criando como parte de um barramento de serviço pronto para produção.</span><span class="sxs-lookup"><span data-stu-id="911c5-105">You should not use it for your production environment, unless you are building it as a part of a production-ready service bus.</span></span> <span data-ttu-id="911c5-106">Um barramento de eventos personalizado simples talvez não tenha muitos recursos críticos prontos para produção que um barramento de serviço comercial tem.</span><span class="sxs-lookup"><span data-stu-id="911c5-106">A simple custom event bus might be missing many production-ready critical features that a commercial service bus has.</span></span>

<span data-ttu-id="911c5-107">Uma da implementação personalizada do barramento de eventos no eShopOnContainers é basicamente uma biblioteca que usa a API do RabbitMQ (há outra implementação baseada no Barramento de Serviço do Azure).</span><span class="sxs-lookup"><span data-stu-id="911c5-107">One of the event bus custom implementation in eShopOnContainers is basically a library using the RabbitMQ API (There’s another implementation based on Azure Service Bus).</span></span>

<span data-ttu-id="911c5-108">A implementação do barramento de eventos com RabbitMQ permite que os microsserviços assinem, publiquem e recebam eventos, conforme mostrado na Figura 6-21.</span><span class="sxs-lookup"><span data-stu-id="911c5-108">The event bus implementation with RabbitMQ lets microservices subscribe to events, publish events, and receive events, as shown in Figure 6-21.</span></span>

![Diagrama mostrando RabbitMQ entre remetente de mensagem e receptor de mensagem.](./media/rabbitmq-event-bus-development-test-environment/rabbitmq-implementation.png)

<span data-ttu-id="911c5-110">**Figura 6-21.**</span><span class="sxs-lookup"><span data-stu-id="911c5-110">**Figure 6-21.**</span></span> <span data-ttu-id="911c5-111">Implementação de um barramento de eventos do RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="911c5-111">RabbitMQ implementation of an event bus</span></span>

<span data-ttu-id="911c5-112">O RabbitMQ é um intermediário entre o publicador da mensagem e os assinantes, para tratar da distribuição.</span><span class="sxs-lookup"><span data-stu-id="911c5-112">RabbitMQ functions as an intermediary between message publisher and subscribers, to handle distribution.</span></span> <span data-ttu-id="911c5-113">No código, a classe EventBusRabbitMQ implementa a interface IEventBus genérica.</span><span class="sxs-lookup"><span data-stu-id="911c5-113">In the code, the EventBusRabbitMQ class implements the generic IEventBus interface.</span></span> <span data-ttu-id="911c5-114">Isso se baseia na Injeção de dependência para que você possa trocar dessa versão de Desenvolvimento/Teste para uma versão de produção.</span><span class="sxs-lookup"><span data-stu-id="911c5-114">This is based on Dependency Injection so that you can swap from this dev/test version to a production version.</span></span>

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
}
```

<span data-ttu-id="911c5-115">A implementação do RabbitMQ de um barramento de eventos de Desenvolvimento/Teste de exemplo é um código clichê.</span><span class="sxs-lookup"><span data-stu-id="911c5-115">The RabbitMQ implementation of a sample dev/test event bus is boilerplate code.</span></span> <span data-ttu-id="911c5-116">Ele precisa lidar com a conexão com o servidor do RabbitMQ e fornecer o código para a publicação de um evento de mensagem nas filas.</span><span class="sxs-lookup"><span data-stu-id="911c5-116">It has to handle the connection to the RabbitMQ server and provide code for publishing a message event to the queues.</span></span> <span data-ttu-id="911c5-117">Ele também precisa implementar um dicionário de coleções de manipuladores de eventos de integração para cada tipo de evento; esses tipos de evento podem ter uma instanciação diferente e diferentes assinaturas para cada microsserviço receptor, conforme mostrado na Figura 6-21.</span><span class="sxs-lookup"><span data-stu-id="911c5-117">It also has to implement a dictionary of collections of integration event handlers for each event type; these event types can have a different instantiation and different subscriptions for each receiver microservice, as shown in Figure 6-21.</span></span>

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a><span data-ttu-id="911c5-118">Implementando um método de publicação simples com RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="911c5-118">Implementing a simple publish method with RabbitMQ</span></span>

<span data-ttu-id="911c5-119">O código a seguir é uma versão ***simplificada*** de uma implementação de barramento de eventos do RabbitMQ, para demonstrar o cenário completo.</span><span class="sxs-lookup"><span data-stu-id="911c5-119">The following code is a ***simplified*** version of an event bus implementation for RabbitMQ, to showcase the whole scenario.</span></span> <span data-ttu-id="911c5-120">Na prática, a conexão não é tratada dessa maneira.</span><span class="sxs-lookup"><span data-stu-id="911c5-120">You don't really handle the connection this way.</span></span> <span data-ttu-id="911c5-121">Para ver a implementação completa, confira o código real no repositório [dotnet-architecture/eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs).</span><span class="sxs-lookup"><span data-stu-id="911c5-121">To see the full implementation, see the actual code in the [dotnet-architecture/eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) repository.</span></span>

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

<span data-ttu-id="911c5-122">O [código real](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) do método de publicação no aplicativo eShopOnContainers é aprimorado usando uma política de repetição [Polly](https://github.com/App-vNext/Polly), que repete a tarefa um determinado número de vezes caso o contêiner do RabbitMQ não esteja pronto.</span><span class="sxs-lookup"><span data-stu-id="911c5-122">The [actual code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) of the Publish method in the eShopOnContainers application is improved by using a [Polly](https://github.com/App-vNext/Polly) retry policy, which retries the task a certain number of times in case the RabbitMQ container is not ready.</span></span> <span data-ttu-id="911c5-123">Isso pode ocorrer quando docker-compose está iniciando os contêineres; por exemplo, o contêiner do RabbitMQ pode ser iniciado mais lentamente do que outros contêineres.</span><span class="sxs-lookup"><span data-stu-id="911c5-123">This can occur when docker-compose is starting the containers; for example, the RabbitMQ container might start more slowly than the other containers.</span></span>

<span data-ttu-id="911c5-124">Conforme mencionado anteriormente, há muitas configurações possíveis no RabbitMQ. Portanto, esse código deve ser usado apenas para ambientes de Desenvolvimento/Teste.</span><span class="sxs-lookup"><span data-stu-id="911c5-124">As mentioned earlier, there are many possible configurations in RabbitMQ, so this code should be used only for dev/test environments.</span></span>

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a><span data-ttu-id="911c5-125">Implementando o código de assinatura com a API do RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="911c5-125">Implementing the subscription code with the RabbitMQ API</span></span>

<span data-ttu-id="911c5-126">Como acontece com o código de publicação, o código a seguir é uma simplificação de parte da implementação do barramento de eventos para RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="911c5-126">As with the publish code, the following code is a simplification of part of the event bus implementation for RabbitMQ.</span></span> <span data-ttu-id="911c5-127">Mais uma vez, geralmente não é necessário alterá-lo, a menos que você o esteja aprimorando.</span><span class="sxs-lookup"><span data-stu-id="911c5-127">Again, you usually do not need to change it unless you are improving it.</span></span>

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

<span data-ttu-id="911c5-128">Cada tipo de evento tem um canal relacionado para obter eventos do RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="911c5-128">Each event type has a related channel to get events from RabbitMQ.</span></span> <span data-ttu-id="911c5-129">Em seguida, é possível ter tantos manipuladores de eventos por tipo de evento e de canal conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="911c5-129">You can then have as many event handlers per channel and event type as needed.</span></span>

<span data-ttu-id="911c5-130">O método Subscribe aceita um objeto IIntegrationEventHandler, que é como um método de retorno de chamada no microsserviço atual, além de seu objeto IntegrationEvent relacionado.</span><span class="sxs-lookup"><span data-stu-id="911c5-130">The Subscribe method accepts an IIntegrationEventHandler object, which is like a callback method in the current microservice, plus its related IntegrationEvent object.</span></span> <span data-ttu-id="911c5-131">O código, então, adiciona o manipulador de eventos à lista de manipuladores de eventos que cada tipo de evento de integração pode ter por microsserviço do cliente.</span><span class="sxs-lookup"><span data-stu-id="911c5-131">The code then adds that event handler to the list of event handlers that each integration event type can have per client microservice.</span></span> <span data-ttu-id="911c5-132">Se o código do cliente ainda não tiver assinado o evento, o código criará um canal para o tipo de evento para que ele possa receber eventos em um estilo de push do RabbitMQ quando esse evento for publicado de qualquer outro serviço.</span><span class="sxs-lookup"><span data-stu-id="911c5-132">If the client code has not already been subscribed to the event, the code creates a channel for the event type so it can receive events in a push style from RabbitMQ when that event is published from any other service.</span></span>

<span data-ttu-id="911c5-133">Conforme mencionado acima, o barramento de evento implementado em eShopOnContainers tem apenas e finalidade Education, já que trata apenas dos principais cenários, portanto, ele não está pronto para produção.</span><span class="sxs-lookup"><span data-stu-id="911c5-133">As mentioned above, the event bus implemented in eShopOnContainers has only and educational purpose, since it only handles the main scenarios, so it's not ready for production.</span></span>

<span data-ttu-id="911c5-134">Para cenários de produção, verifique os recursos adicionais abaixo, específicos para RabbitMQ e a seção [implementando a comunicação baseada em evento entre os microserviços](./integration-event-based-microservice-communications.md#additional-resources) .</span><span class="sxs-lookup"><span data-stu-id="911c5-134">For production scenarios check the additional resources below, specific for RabbitMQ, and the [Implementing event-based communication between microservices](./integration-event-based-microservice-communications.md#additional-resources) section.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="911c5-135">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="911c5-135">Additional resources</span></span>

<span data-ttu-id="911c5-136">Uma solução pronta para produção com suporte para RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="911c5-136">A production-ready solutions with support for RabbitMQ.</span></span>

- <span data-ttu-id="911c5-137">**EasyNetQ** -cliente de API .net de código aberto para RabbitMQ </span><span class="sxs-lookup"><span data-stu-id="911c5-137">**EasyNetQ** - Open Source .NET API client for RabbitMQ </span></span>\
  <http://easynetq.com/>

- <span data-ttu-id="911c5-138"> \ **MassTransit**</span><span class="sxs-lookup"><span data-stu-id="911c5-138">**MassTransit** \</span></span>
  <https://masstransit-project.com/>
  
>[!div class="step-by-step"]
><span data-ttu-id="911c5-139">[Anterior](integration-event-based-microservice-communications.md)
>[Próximo](subscribe-events.md)</span><span class="sxs-lookup"><span data-stu-id="911c5-139">[Previous](integration-event-based-microservice-communications.md)
[Next](subscribe-events.md)</span></span>
