---
title: "Implementação de comunicação baseada em evento entre microservices (eventos de integração)"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Implementação de comunicação baseada em evento entre microservices (eventos de integração)"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: e438607ab3549d63b89bef6af64c6723a4cac950
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-event-based-communication-between-microservices-integration-events"></a>Implementação de comunicação baseada em evento entre microservices (eventos de integração)

Conforme descrito anteriormente, quando você usar a comunicação baseada em evento, um microsserviço publica um evento quando acontecer por algo importantes, como quando ele atualiza uma entidade de negócios. Outros microservices assinar esses eventos. Quando um microsserviço recebe um evento, ele pode atualizar suas próprias entidades de negócios, que podem levar a mais eventos que está sendo publicados. Este sistema de publicação/assinatura normalmente é executado por meio de uma implementação de um barramento de evento. O barramento de evento pode ser criado como uma interface com a API necessária para se inscrever e cancelar a eventos e publicar eventos. Ele também pode ter uma ou mais implementações com base em qualquer comunicação entre processos ou mensagens, como uma fila de mensagens ou um barramento de serviço que dá suporte à comunicação assíncrona e um modelo de publicação/assinatura.

Você pode usar eventos para implementar transações comerciais que abrangem vários serviços, que fornece consistência eventual entre esses serviços. Uma transação finalmente consistente consiste em uma série de ações distribuídas. Em cada ação, o microsserviço atualiza uma entidade de negócios e publica um evento que dispara a próxima ação.

![](./media/image19.PNG)

**Figura 8-18**. Comunicação controlada por evento, com base em um barramento de evento

Esta seção descreve como você pode implementar esse tipo de comunicação com o .NET usando uma interface de barramento de evento genérico, conforme mostrado na Figura 8-18. Há várias implementações possíveis, cada um usando uma tecnologia diferente ou infraestrutura como RabbitMQ, barramento de serviço do Azure, ou qualquer outro software livre de terceiros ou barramento de serviço comercial.

## <a name="using-message-brokers-and-services-buses-for-production-systems"></a>Usando barramentos de serviços e agentes de mensagens para sistemas de produção

Conforme observado na seção de arquitetura, você pode escolher entre várias tecnologias de mensagem para implementar o barramento do evento abstrato. Mas essas tecnologias estão em diferentes níveis. Por exemplo, RabbitMQ, um transporte de agente de mensagens, está em um nível inferior produtos comerciais, como o Azure Service Bus, NServiceBus, MassTransit ou Brighter. A maioria desses produtos pode trabalhar sobre RabbitMQ ou barramento de serviço do Azure. A escolha do produto depende de quantos recursos e escalabilidade quanto-de-prontos precisar para seu aplicativo.

Para implementar apenas um evento barramento prova de conceito para seu ambiente de desenvolvimento, como no exemplo eShopOnContainers, uma implementação simples sobre RabbitMQ em execução como um contêiner pode ser suficiente. Mas para essenciais e sistemas de produção que precisam de alta escalabilidade, talvez você queira avaliar e usar o Azure Service Fabric. Se você precisar abstrações de alto nível e os recursos mais avançados, como [sagas](https://docs.particular.net/nservicebus/sagas/) para processos de execução demorada que tornam o desenvolvimento distribuído barramentos mais fácil, serviço comercial e código-fonte aberto como NServiceBus, MassTransit, e Mais interessantes são vale a pena avaliar. Naturalmente, você sempre pode criar seus próprios recursos de barramento de serviço sobre tecnologias de nível inferior, como RabbitMQ e o Docker, mas o trabalho necessário reinventar a roda pode ser muito alto para um aplicativo corporativo personalizado.

Para reiterar: o abstrações de barramento de evento de exemplo e a implementação exibido no exemplo eShopOnContainers devem ser usados apenas como uma prova de conceito. Depois de ter decidido que você deseja ter comunicação assíncrona e controlada por evento, conforme explicado na seção atual, você deve escolher o produto de barramento de serviço que melhor atenda às suas necessidades.

## <a name="integration-events"></a>Eventos de integração

Eventos de integração são usados para colocar o estado de domínio em sincronização em vários microservices ou sistemas externos. Isso é feito ao publicar eventos de integração fora de microsserviço. Quando um evento é publicado em vários microservices receptor (para tantos microservices como está inscrito no evento de integração), o manipulador de eventos apropriado em cada destinatário microsserviço manipula o evento.

Um evento de integração é basicamente uma classe de retenção de dados, como no exemplo a seguir:

```csharp
public class ProductPriceChangedIntegrationEvent : IntegrationEvent
{
    public int ProductId { get; private set; }
    public decimal NewPrice { get; private set; }
    public decimal OldPrice { get; private set; }

    public ProductPriceChangedIntegrationEvent(int productId, decimal newPrice,
        decimal oldPrice)
    {
        ProductId = productId;
        NewPrice = newPrice;
        OldPrice = oldPrice;
    }
}
```

A classe de evento de integração pode ser simple; Por exemplo, ele pode conter um GUID para sua ID.

Os eventos de integração podem ser definidos no nível do aplicativo de cada microsserviço para eles são separados de outros microservices, de forma comparável como ViewModels são definidas no cliente e servidor. O que não é recomendável está compartilhando uma biblioteca de eventos de integração comuns em vários microservices; fazer isso poderia ser acoplamento esses microservices com uma biblioteca de dados de definição de evento único. Você não deseja fazer isso para os mesmos motivos que você não deseja compartilhar um modelo de domínio comum entre vários microservices: microservices deve ser completamente autônoma.

Há apenas alguns tipos de bibliotecas, que você deve compartilhar em microservices. Um é bibliotecas são blocos de final do aplicativo, como o [API do cliente do barramento de evento](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/BuildingBlocks/EventBus), conforme mostrado no eShopOnContainers. Outra vantagem é que constituem ferramentas também podem ser compartilhadas como componentes do NuGet, como JSON serializadores bibliotecas.

## <a name="the-event-bus"></a>O barramento de evento

Um barramento de evento permite publicar/assinar-estilo comunicação entre microservices sem a necessidade dos componentes a serem explicitamente Lembre-se entre si, conforme mostrado na Figura 8-19.

![](./media/image20.png)

**Figura 8-19**. Noções básicas de um barramento de evento de publicação/assinatura

O barramento de evento está relacionado para o padrão Observer e a publicação-assinatura padrão.

### <a name="observer-pattern"></a>Padrão do observador

No [padrão Observer](https://en.wikipedia.org/wiki/Observer_pattern), o objeto primário (conhecido como o observável) notifica outros objetos de interessados (conhecidos como observadores) com informações relevantes (eventos).

### <a name="publish-subscribe-pubsub-pattern"></a>Padrão de publicação / assinatura (Pub/Sub) 

O objetivo do [padrão Pub/Sub](https://msdn.microsoft.com/en-us/library/ff649664.aspx) é o mesmo que o padrão Observer: você deseja notificar outros serviços quando determinados eventos ocorrem. Mas há uma importante diferença semântica entre os padrões de observador e Pub/Sub. No padrão de publicação/assinatura, o foco está em mensagens de difusão. Por outro lado, no padrão de observador, o observável não sabe que os eventos serão, assim que eles passaram-out. Em outras palavras, o observável (o Editor) não saber quem são os observadores (assinantes).

### <a name="the-middleman-or-event-bus"></a>O barramento intermediário ou evento 

Como você obter anonimato entre o publicador e assinante? Uma maneira fácil é permitir que um intermediário responsável por toda a comunicação. Um barramento de evento é um tal intermediário.

Um barramento de evento normalmente é composto de duas partes:

-   A abstração ou interface.

-   Uma ou mais implementações.

Figura 8-19 você pode ver como, de um ponto de vista de aplicativo, o barramento de evento é nada mais que um canal de publicação/assinatura. A maneira como você implementa essa comunicação assíncrona pode variar. Ele pode ter várias implementações de forma que você possa alternar entre eles, dependendo dos requisitos do ambiente (por exemplo, produção versus ambientes de desenvolvimento).

Figura 8-20, você pode ver uma abstração de um barramento de evento com várias implementações com base na infraestrutura de mensagens de tecnologias como RabbitMQ, barramento de serviço do Azure ou outros barramentos de serviço NServiceBus, MassTransit, etc.

![](./media/image21.png)

**Figura 8 - 20.** Várias implementações de um barramento de evento

No entanto, como destacado anteriormente, usando abstrações (interface de barramento do evento) é possível somente se você precisar de recursos de barramento de evento basic suportados pelo seu abstrações. Se você precisar de recursos mais avançados de barramento de serviço, provavelmente você deve usar a API fornecida pelo seu barramento de serviço preferenciais em vez de seus próprio abstrações.

### <a name="defining-an-event-bus-interface"></a>Define uma interface de barramento de evento

Vamos começar com um código de implementação para a interface de barramento de evento e implementações possíveis para fins de exploração. A interface deve ser genérico e simples, como a interface a seguir.

```csharp
public interface IEventBus
{
    void Publish(IntegrationEvent @event);
    void Subscribe<T>(IIntegrationEventHandler<T> handler)
        where T: IntegrationEvent;

    void Unsubscribe<T>(IIntegrationEventHandler<T> handler)
        where T : IntegrationEvent;
}
```

O método de publicação é simples. O barramento de evento irá transmitir o evento de integração passado a ele a qualquer microsserviço inscrito em que o evento. Esse método é usado, o que está publicando o evento microsserviço.

O método Subscribe é usado pelo microservices que deseja receber eventos. Esse método tem duas partes. A primeira é o evento de integração para assinar (IntegrationEvent). A segunda parte é o manipulador de eventos de integração (ou o método de retorno de chamada) a ser chamado (IIntegrationEventHandler&lt;T&gt;) quando o microsserviço recebe essa mensagem de evento de integração.


>[!div class="step-by-step"]
[Anterior] (banco de dados-server-container.md) [Avançar] (rabbitmq-event-bus-development-test-environment.md)
