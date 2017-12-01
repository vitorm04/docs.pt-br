---
title: "Comunicação assíncrona baseada em mensagens"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Comunicação assíncrona baseada em mensagens"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: df39771295d12e122edbe27e91cd899e3318e301
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="asynchronous-message-based-communication"></a>Comunicação assíncrona baseada em mensagens

Sistema de mensagens assíncronas e comunicação controlada por evento são essenciais ao propagar alterações em várias microservices e seus modelos de domínio relacionadas. Conforme mencionado anteriormente na discussão microservices e contextos limitada (BCs), modelos (usuário, cliente, produto, conta, etc.) podem significar coisas diferentes para diferentes microservices ou BCs. Isso significa que quando ocorrem alterações, você precisa de algum modo para reconciliar as alterações entre diferentes modelos. Uma solução é consistência eventual e comunicação controlada por evento, com base no sistema de mensagens assíncronas.

Ao usar o sistema de mensagens, processos se comunicam trocando mensagens de forma assíncrona. Um cliente faz um comando ou uma solicitação para um serviço ao enviar uma mensagem. Se o serviço precisar responder, ele envia uma mensagem diferente para o cliente. Como é uma comunicação baseada em mensagens, o cliente presume que a resposta não será recebida imediatamente e que não pode haver nenhuma resposta em todos os.

Uma mensagem é composta por um cabeçalho (metadados, como informações de identificação ou de segurança) e um corpo. Geralmente são enviadas por meio de protocolos assíncronos como AMQP.

A infraestrutura preferencial para esse tipo de comunicação na comunidade de microservices é um agente de mensagem leve, que é diferente de agentes de grandes e orchestrators usadas na SOA. Em um agente de mensagem leve, a infraestrutura é normalmente "inútil," atuando somente como um agente de mensagens, com implantações simples como RabbitMQ ou um barramento de serviço escalonáveis na nuvem como o Azure Service Bus. Nesse cenário, a maioria do raciocínio "inteligente" ainda mora em pontos de extremidade que estão produzindo e consumir mensagens — ou seja, em que o microservices.

Outra regra que a seguir, tanto quanto possível, tente é usar mensagens assíncronas somente entre os serviços internos e para usar comunicação síncrona (como HTTP) apenas nos aplicativos de cliente para os serviços de front-end (Gateways de API e o primeiro nível de microservices).

Há dois tipos de comunicação assíncrona de mensagens: comunicação baseada em mensagens do receptor único e vários receptores mensagem uma comunicação. As seções a seguir fornecemos detalhes sobre elas.

## <a name="single-receiver-message-based-communication"></a>Comunicação baseada em mensagem único destinatário 

Comunicação assíncrona baseada em mensagem com um único destinatário significa que não há comunicação ponto a ponto que envia uma mensagem para exatamente um dos consumidores que está lendo do canal e a mensagem é processada apenas uma vez. No entanto, há situações especiais. Por exemplo, em um sistema de nuvem que tenta se recuperar automaticamente de falhas, a mesma mensagem pode ser enviada várias vezes. Devido à rede ou outras falhas, o cliente deve ser capaz de tentar o envio de mensagens e o servidor tem que implementar uma operação para ser idempotente para processar uma mensagem específica apenas uma vez.

A comunicação baseada em mensagem único destinatário é especialmente adequada para enviar comandos assíncronos de um microsserviço para outro, conforme mostrado na Figura 4-18 que mostra essa abordagem.

Depois de iniciar a comunicação baseada em mensagens (ou com comandos ou eventos) de envio, você deve evitar a mistura de comunicação baseada em mensagem com a comunicação HTTP síncrona.

![](./media/image18.PNG)

**Figura 4-18**. Um único microsserviço recebendo uma mensagem assíncrona

Observe que, quando os comandos provém de aplicativos cliente, elas podem ser implementadas como comandos síncronos HTTP. Quando você precisar maior escalabilidade ou quando você já estiver em um processo de negócios com base em mensagem, você deve usar comandos baseada em mensagem.

## <a name="multiple-receivers-message-based-communication"></a>Comunicação baseada em mensagens de vários destinatários 

Como uma abordagem mais flexível, você também poderá usar um mecanismo de publicação/assinatura para que a comunicação do remetente estará disponível para o assinante adicionais microservices ou para aplicativos externos. Portanto, ele ajuda a seguir o [abertura/fechamento princípio](https://en.wikipedia.org/wiki/Open/closed_principle) no serviço de envio. Dessa forma, assinantes adicionais podem ser adicionados no futuro sem a necessidade de modificar o serviço do remetente.

Quando você usar uma comunicação de publicação/assinatura, talvez você esteja usando uma interface de barramento de eventos para eventos de publicação a qualquer assinante.

## <a name="asynchronous-event-driven-communication"></a>Comunicação assíncrona controlada por evento

Ao usar comunicação assíncrona controlada por evento, um microsserviço publica um evento de integração quando acontecer algo em seu domínio e outro microsserviço precisa ser consideradas, como uma alteração de preço em um microsserviço do catálogo de produtos. Microservices adicionais assinar os eventos para eles podem recebê-las de forma assíncrona. Quando isso acontece, os receptores podem atualizar suas próprias entidades de domínio, o que podem causar mais eventos de integração a ser publicado. Este sistema de publicação/assinatura normalmente é executado por meio de uma implementação de um barramento de evento. O barramento de evento pode ser projetado como uma interface, com a API que é necessário para assinar ou cancelar a assinatura para eventos e publicar eventos ou de abstração. O barramento de evento também pode ter um ou mais implementações com base em qualquer agente entre processos e mensagens, como uma fila de mensagens ou o barramento de serviço que dá suporte à comunicação assíncrona e um modelo de publicação/assinatura.

Se um sistema usa consistência eventual orientada por eventos de integração, é recomendável que essa abordagem ficar completamente limpa para o usuário final. O sistema não deve usar uma abordagem que simule eventos de integração, como sistemas de sondagem do cliente ou SignalR. O usuário final e o proprietário da empresa precisam explicitamente adotar consistência eventual no sistema e observe que em muitos casos de negócios não tem nenhum problema com essa abordagem, desde que ele seja explícito.

Conforme observado anteriormente no [desafios e soluções para o gerenciamento de dados distribuídas](#challenges-and-solutions-for-distributed-data-management) seção, você pode usar eventos de integração para implementar as tarefas de negócios que abrangem vários microservices. Assim, você terá consistência eventual entre esses serviços. Uma transação finalmente consistente é composta de uma coleção de ações distribuídas. Em cada ação, o microsserviço relacionado atualiza uma entidade de domínio e publica outro evento de integração que gera a próxima ação dentro da mesma tarefa comercial de ponta a ponta.

Um ponto importante é que você deseja se comunicar com várias microservices que assinou o mesmo evento. Para fazer isso, você pode usar a publicação/assinatura de mensagens com base em comunicação controlada por evento, conforme mostrado na Figura 4-19. Esse mecanismo de publicação/assinatura não é exclusivo para a arquitetura de microsserviço. É semelhante à forma como [limitada contextos](http://martinfowler.com/bliki/BoundedContext.html) no DDD deve se comunicar ou à forma como você propagar atualizações do banco de dados de gravação no banco de dados de leitura no [comando e consulta responsabilidade CQRS (segregação)](http://martinfowler.com/bliki/CQRS.html)padrão de arquitetura. A meta é ter consistência eventual entre várias fontes de dados em seu sistema distribuído.

![](./media/image19.png)

**Figura 4-19**. Comunicação assíncrona de mensagem controlado por evento

Sua implementação determinará o protocolo a ser usado para comunicações com base na mensagem, controlada por evento. [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol) pode ajudar a obter uma comunicação confiável na fila.

Quando você usar um barramento de evento, talvez você queira usar um nível de abstração (como uma interface de barramento de evento) com base em uma implementação relacionada em classes com o código usando a API de um agente de mensagens como [RabbitMQ](https://www.rabbitmq.com/) ou um barramento de serviço como [Barramento de serviço do azure com tópicos](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions). Como alternativa, você talvez queira usar um barramento de serviço de nível superior como NServiceBus, MassTransit ou Brighter para enfatizar o barramento de evento e sistema de publicação/assinatura.

## <a name="a-note-about-messaging-technologies-for-production-systems"></a>Uma observação sobre tecnologias para sistemas de produção de mensagens

As tecnologias de mensagens disponíveis para implementar o barramento do evento abstrato estão em diferentes níveis. Por exemplo, produtos, como RabbitMQ (um transporte do broker mensagens) e o Azure Service Bus ficam em um nível inferior outros produtos como, NServiceBus, MassTransit ou Brighter, que pode funcionar sobre RabbitMQ e o barramento de serviço do Azure. Sua escolha depende de quantos recursos avançados no nível do aplicativo e escalabilidade de fora da caixa, que você precisa para seu aplicativo. Para implementar apenas um barramento de evento de prova de conceito para seu ambiente de desenvolvimento, como fizemos no exemplo de eShopOnContainers, pode ser uma implementação simples sobre RabbitMQ em execução em um contêiner do Docker suficiente.

No entanto, para essenciais e sistemas de produção que precisam hyper escalabilidade, talvez você queira avaliar o Azure Service Bus. Recursos que facilitam o desenvolvimento de aplicativos distribuídos e abstrações de alto nível, é recomendável que você avalie barramentos outros serviços comerciais e de código aberto, como NServiceBus, MassTransit e Brighter. Obviamente, você pode criar seus próprios recursos de barramento de serviço sobre tecnologias de nível inferior, como RabbitMQ e o Docker. Mas esse trabalho pode muito caro para um aplicativo da empresa personalizados.

## <a name="resiliently-publishing-to-the-event-bus"></a>Atenda com flexibilidade de publicação para o barramento de evento

Um desafio ao implementar uma arquitetura orientada a eventos em vários microservices é como atomicamente atualizar estado de microsserviço original durante a publicação atenda com flexibilidade de seu evento integração relacionados para o barramento de evento, com base em alguma forma em transações. A seguir estão algumas maneiras de fazer isso, embora haja outras abordagens também.

-   Usando uma fila transacional (baseado em DTC) como MSMQ. (No entanto, essa é uma abordagem herdada.)

-   Usando [mineração do log de transações](http://www.scoop.it/t/sql-server-transaction-log-mining).

-   Usando completo [fornecimento do evento](https://msdn.microsoft.com/en-us/library/dn589792.aspx) padrão.

-   Usando o [da caixa de saída padrão](http://gistlabs.com/2014/05/the-outbox/): uma tabela de banco de dados transacional como uma fila de mensagens que será a base de um componente do criador do evento que criar o evento e publicá-lo.

Tópicos adicionais a serem considerados ao usar comunicação assíncrona são idempotência de mensagem e a eliminação de duplicação de mensagem. Esses tópicos são abordados na seção [implementar a comunicação baseada em eventos entre microservices (eventos de integração)](#implementing_event_based_comms_microserv) posteriormente neste guia.

## <a name="additional-resources"></a>Recursos adicionais

-   **Mensagens de eventos controlada por**
    [*http://soapatterns.org/design\_padrões/evento\_controlados por\_de mensagens*](http://soapatterns.org/design_patterns/event_driven_messaging)

-   **Canal de publicação/assinatura**
    [*http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html*](http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html)

-   **Udi Dahan. Esclareceu CQRS**
    [*http://udidahan.com/2009/12/09/clarified-cqrs/*](http://udidahan.com/2009/12/09/clarified-cqrs/)

-   **Comando e consultar a segregação de responsabilidade (CQRS)**
    [*https://docs.microsoft.com/azure/architecture/patterns/cqrs*](https://docs.microsoft.com/azure/architecture/patterns/cqrs)

-   **Comunicação entre limitada contextos**
    [*https://msdn.microsoft.com/library/jj591572.aspx*](https://msdn.microsoft.com/library/jj591572.aspx)

-   **Consistência eventual**
    [*https://en.wikipedia.org/wiki/Eventual\_consistência*](https://en.wikipedia.org/wiki/Eventual_consistency)

-   **Jimmy Bogard. Refatoração em direção a resiliência: Avaliando acoplamento**
    [*https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/*](https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/)


>[!div class="step-by-step"]
[Anterior] (comunicação-em-microsserviço-architecture.md) [Avançar] (manter-microsserviço-apis.md)
