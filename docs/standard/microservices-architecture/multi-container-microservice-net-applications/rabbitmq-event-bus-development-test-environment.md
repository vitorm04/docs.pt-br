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
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a>Implementando um barramento de evento com RabbitMQ para o ambiente de desenvolvimento ou teste

Deve começar dizendo que, se você criar o barramento de evento personalizado com base em RabbitMQ em execução em um contêiner, que o aplicativo eShopOnContainers, ele deve ser usado somente para seus ambientes de desenvolvimento e teste. Você não deve usá-lo para o seu ambiente de produção, a menos que você está criando-o como parte de um barramento de serviço pronto para produção. Barramento de evento personalizado simples talvez não tenha muitos recursos críticos prontos para produção que tem um barramento de serviço comercial.

A implementação personalizada de eShopOnContainers de um barramento de evento é basicamente uma biblioteca usando a API RabbitMQ. A implementação permite microservices assinar eventos, publicar eventos e receber eventos, como mostrado na Figura 8-21.

![](./media/image22.png)

**Figura 8-21.** RabbitMQ implementação de um barramento de evento

No código, a classe de EventBusRabbitMQ implementa a interface IEventBus genérica. Isso se baseia na injeção de dependência para que você pode trocar dessa versão de desenvolvimento/teste para uma versão de produção.

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
```

A implementação de RabbitMQ do barramento de evento de desenvolvimento/teste de exemplo é código padronizado. Ele tem que lidar com a conexão ao servidor RabbitMQ e fornecer o código para a publicação de um evento de mensagem para filas. Ele também tem que implementar um dicionário de coleções de manipuladores de eventos de integração para cada tipo de evento; Esses tipos de evento podem ter uma instanciação diferente e diferentes assinaturas do microsserviço cada destinatário, conforme mostrado na Figura 8-21.

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a>Implementando um simples publicar método com RabbitMQ

O código a seguir é parte da implementação do barramento de evento eShopOnContainers para RabbitMQ, para que você normalmente não precisa codificá-la, a menos que você estiver fazendo aprimoramentos. O código obtém uma conexão e canal para RabbitMQ, cria uma mensagem e, em seguida, publica a mensagem na fila.

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

O [código real](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) de publicar método no aplicativo eShopOnContainers é aprimorado usando um [Polly](https://github.com/App-vNext/Polly) política, que repete a tarefa de um determinado número de vezes que no caso do contêiner de RabbitMQ é de repetição não está pronto. Isso pode ocorrer quando compor docker está iniciando os contêineres; Por exemplo, o contêiner de RabbitMQ pode iniciar mais lentamente do que os outros contêineres.

Como mencionado anteriormente, há muitas configurações possíveis em RabbitMQ, portanto esse código deve ser usado apenas para ambientes de desenvolvimento e teste.

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a>Implementar o código de assinatura com a API RabbitMQ

Como com o código de publicação, o código a seguir é uma simplificação de parte da implementação do barramento de eventos para RabbitMQ. Novamente, você normalmente não precisa alterá-la, a menos que são melhorá-lo.

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

Cada tipo de evento tem um canal relacionado para obter eventos do RabbitMQ. Em seguida, você pode ter tantos manipuladores de eventos por tipo de canal e de evento conforme necessário.

O método Subscribe aceita um objeto IIntegrationEventHandler, que é como um método de retorno de chamada no microsserviço atual, além de seu objeto IntegrationEvent relacionado. O código, em seguida, adiciona o manipulador de eventos à lista de manipuladores de eventos que cada tipo de evento de integração pode ter por cliente microsserviço. Se o código do cliente não já inscrito no evento, o código cria um canal para o tipo de evento para que ela possa receber eventos em um estilo de envio de RabbitMQ quando esse evento é publicado a partir de qualquer outro serviço.


>[!div class="step-by-step"]
[Anterior] (integração-evento-com base-microsserviço-communications.md) [Avançar] (events.md assinar)
