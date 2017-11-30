---
title: "Comunicação em uma arquitetura de microsserviço"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Comunicação em um arquiteturas de arquitetura de microsserviço"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 8d38095a151b7568619b17340d768eff684d3271
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="communication-in-a-microservice-architecture"></a>Comunicação em uma arquitetura de microsserviço

Em um aplicativo monolítico em execução em um único processo, componentes de chamar outro usando o método de nível de linguagem ou chamadas de função. Esses podem ser fortemente acoplados se você estiver criando objetos com o código de (por exemplo, `new ClassName()`), ou pode ser invocado de forma separada, se você estiver usando a injeção de dependência referenciando abstrações em vez de instâncias de objeto concreto. De qualquer forma, os objetos estão sendo executados no mesmo processo. O maior desafio durante a alteração de um aplicativo monolítico para um aplicativo baseado em microservices é alterar o mecanismo de comunicação. Uma conversão direta de chamadas de método em processo em chamadas RPC para serviços fará com que um verborrágica e ambientes distribuídos de comunicação não eficiente que não executará bem no. Desafios de criação de sistema distribuído corretamente bem conhecidos que ainda há um canon conhecido como o [fallacies de computação distribuída](https://en.wikipedia.org/wiki/Fallacies_of_distributed_computing) que lista as suposições que os desenvolvedores geralmente fazem quando movendo de monolítico designs distribuído.

Não há não é uma solução, mas várias. Uma solução envolve isolar o microservices de negócios tanto quanto possível. Você, em seguida, usa a comunicação assíncrona entre o microservices interno e substitua refinada comunicação típica na comunicação entre processos entre objetos com a comunicação mais rústico. Você pode fazer isso com o agrupamento de chamadas e retornando dados que agrega os resultados de várias chamadas internos, para o cliente.

Um aplicativo baseado em microservices é um sistema distribuído em execução em vários processos ou serviços, geralmente, até mesmo em vários servidores ou hosts. Cada instância de serviço geralmente é um processo. Portanto, os serviços devem interagir usando um protocolo de comunicação entre processos, como HTTP, AMQP ou um protocolo binário, como TCP, dependendo da natureza de cada serviço.

A comunidade de microsserviço promove a filosofia de "[inteligentes pontos de extremidade e pipes tolos](http://simplicable.com/new/smart-endpoints-and-dumb-pipes)." Este slogan incentiva um design que é separada possível entre microservices e como coesa possível dentro de um único microsserviço. Conforme explicado anteriormente, cada microsserviço possui sua própria lógica do domínio e seus próprios dados. Mas as composição de um aplicativo de ponta a ponta de microservices são geralmente simplesmente coreografados usando comunicações REST em vez de protocolos complexos, como WS -\* e comunicações flexíveis controlada por evento, em vez de centralizado processo orchestrators Business.

Os dois protocolos usados são de solicitação/resposta HTTP com recurso de APIs (quando a consulta de tudo), e mensagens assíncronas leve, ao se comunicar atualizações em vários microservices. Essas são explicadas em mais detalhes nas seções a seguir.

## <a name="communication-types"></a>Tipos de comunicação

Serviços de cliente e podem se comunicar por meio de vários tipos diferentes de comunicação, cada um deles direcionando um cenário diferente e metas. Inicialmente, esses tipos de comunicação podem ser classificados em dois eixos.

O primeiro eixo é definir se o protocolo é síncrona ou assíncrona:

-   Protocolo síncrono. HTTP é um protocolo síncrono. O cliente envia uma solicitação e aguarda uma resposta do serviço. Que é independente da execução de código do cliente que pode ser síncrona (o thread está bloqueado) ou assíncrona (thread não está bloqueado e a resposta alcançará eventualmente um retorno de chamada). O ponto importante aqui é que o protocolo (HTTP/HTTPS) é síncrono e o código de cliente só pode continuar sua tarefa quando ele recebe a resposta do servidor HTTP.

-   Protocolo assíncrono. Outros protocolos, como o AMQP (um protocolo com suporte por vários sistemas operacionais e ambientes de nuvem) usam mensagens assíncronas. O remetente da mensagem ou código de cliente geralmente não aguarda uma resposta. Ele apenas envia a mensagem como quando enviar uma mensagem para uma fila de RabbitMQ ou qualquer outro agente de mensagens.

O segundo eixo é definir se a comunicação com um único destinatário ou vários destinatários:

-   Único destinatário. Cada solicitação deve ser processada pelo exatamente um destinatário ou serviço. Um exemplo de como essa comunicação é o [padrão de comando](https://en.wikipedia.org/wiki/Command_pattern).

-   Vários destinatários. Cada solicitação pode ser processada por zero para vários destinatários. Esse tipo de comunicação deve ser assíncrono. Um exemplo é o [de publicação/assinatura](https://en.wikipedia.org/wiki/Publish%E2%80%93subscribe_pattern) mecanismo usado em padrões como [arquitetura orientada a eventos](http://microservices.io/patterns/data/event-driven-architecture.html). Isso se baseia em um agente de mensagem ou interface de barramento de evento ao propagar atualizações de dados entre vários microservices por meio de eventos; Ele geralmente é implementado por meio de um barramento de serviço ou artefato semelhante como [Azure Service Bus](https://azure.microsoft.com/services/service-bus/) usando [tópicos e assinaturas](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions).

Um aplicativo baseado em microsserviço geralmente usará uma combinação desses estilos de comunicação. O tipo mais comum é o único destinatário comunicação com um protocolo síncrona como HTTP/HTTPS ao invocar um serviço da Web API HTTP regular. Microservices também geralmente usam protocolos de mensagens para comunicação assíncrona entre microservices.

Esses eixos serão boas conhecer para ter maior clareza os mecanismos de comunicação possíveis, mas eles não são as questões importantes ao criar microservices. A natureza assíncrona de execução de thread de cliente nem a natureza assíncrona do protocolo selecionado são os pontos importantes ao integrar microservices. O que *é* importante é ser capaz de integrar seu microservices assincronamente, mantendo a independência de microservices, conforme explicado na seção a seguir.

## <a name="asynchronous-microservice-integration-enforces-microservices-autonomy"></a>Integração de microsserviço assíncrona impõe a autonomia do microsserviço

Conforme mencionado, o ponto importante ao criar um aplicativo baseado em microservices é a maneira como você integrar seu microservices. Idealmente, você deve tentar minimizar a comunicação entre o microservices interno. O menor comunicações entre microservices, melhor. Mas é claro que, em muitos casos você terá alguma forma integrar o microservices. Quando você precisar fazer isso, a regra crítica aqui é que a comunicação entre o microservices deve ser assíncrona. Isso não significa que você precisa usar um protocolo específico (por exemplo, sistema de mensagens assíncronas versus HTTP síncrona). Isso significa apenas que a comunicação entre microservices deve ser feito apenas pelo propagar dados de forma assíncrona, mas não dependem de outros microservices interno como parte da operação de solicitação/resposta HTTP do serviço inicial.

Se possível, nunca dependem síncrona (solicitação/resposta) de comunicação entre vários microservices, nem mesmo para consultas. O objetivo de cada microsserviço é ser autônoma e disponível para o consumidor de cliente, mesmo que outros serviços que fazem parte do aplicativo ponta a ponta para baixo ou não íntegro. Se você acha que você precisa fazer uma chamada de um microsserviço para outros microservices (como executar uma solicitação HTTP para uma consulta de dados) para ser capaz de fornecer uma resposta a um aplicativo cliente, você tem uma arquitetura que não devem ser resiliente quando alguns microservices falhar.

Além disso, ter dependências HTTP entre microservices, como ao criar longos ciclos de solicitação/resposta HTTP solicitarem cadeias, conforme mostrado na primeira parte da Figura 4-15, não apenas faz com que seu microservices não autônomo, mas também o seu desempenho é Assim que um dos serviços nessa cadeia não está executando também um impacto. 

Quanto mais você adicionar dependências síncronas entre microservices, como solicitações de consulta, pior o tempo de resposta geral é para os aplicativos cliente.

![](./media/image15.png)

**Figura 4-15**. Padrões e padrões de comunicação entre microservices

Se seu microsserviço precisar gerar uma ação adicional em outro microsserviço, se possível, não execute essa ação síncrona e como parte da operação original microsserviço solicitação e resposta. Em vez disso, fazer isso de maneira assíncrona (usando o serviço de mensagens assíncrono ou eventos de integração, filas, etc.). No entanto, tanto quanto possível, não chamar a ação de forma síncrona como parte da operação de solicitação e resposta síncrona original.

E, finalmente, (e isso é onde a maioria dos problemas podem surgir durante a criação de microservices), se o microsserviço inicial precisa de dados que é originalmente pertencentes a outros microservices, não confie em síncrona solicitar que os dados. Em vez disso, replicar ou para a propagação de dados (somente os atributos necessários) no banco de dados do serviço inicial usando consistência eventual (normalmente com eventos de integração, conforme explicado nas seções futuras).

Conforme observado anteriormente na seção [identificar limites de modelo de domínio para cada microsserviço](#identifying-domain-model-boundaries-for-each-microservice), duplicação de alguns dados em vários microservices não é um design incorreto, ao contrário, quando disso, você pode converter os dados na linguagem específica ou termos desse domínio adicional ou contexto associado. Por exemplo, no [eShopOnContainers](http://aka.ms/MicroservicesArchitecture) aplicativo tiver um microsserviço chamado identity.api que é responsável pela maioria dos dados do usuário com uma entidade chamada do usuário. No entanto, quando você precisar armazenar dados sobre o usuário dentro do microsserviço ordenação, você armazená-lo como uma entidade diferente denominada comprador. A entidade de comprador compartilha a mesma identidade com a entidade de usuário original, mas ele pode ter apenas alguns atributos necessários para o domínio de ordenação e não o perfil de usuário inteiro.

Você pode usar qualquer protocolo de comunicação e propagado dados assincronamente microservices para ter consistência eventual. Conforme mencionado, você pode usar eventos de integração usando um barramento de evento ou mensagem de agente, ou você pode até usar HTTP consultando os outros serviços em vez disso. Não importa. A regra importante é não criar síncronas dependências entre seu microservices.

As seções a seguir explicam os vários estilos de comunicação que você pode considerar o uso de um aplicativo baseado em microsserviço.

## <a name="communication-styles"></a>Estilos de comunicação

Há muitos protocolos e as opções que você pode usar para comunicação, dependendo do tipo de comunicação que você deseja usar. Se você estiver usando um mecanismo de comunicação baseada em solicitação/resposta síncrona, protocolos como HTTP e REST abordagens são as mais comuns, especialmente se você estiver publicando seus serviços fora do cluster de host ou microsserviço do Docker. Se você está se comunicando entre serviços internamente (no seu cluster de host ou microservices Docker) você também poderá usar os mecanismos de comunicação do formato binário (como remoting Service Fabric ou WCF usando TCP e o formato binário). Como alternativa, você pode usar mecanismos de comunicação assíncrona, com base em mensagem, como o AMQP.

Também há vários formatos de mensagem como JSON ou XML, ou até mesmo binários formatos, que podem ser mais eficientes. Se o formato binário escolhido não é um padrão, ele provavelmente não é uma boa ideia publicamente publicar seus serviços usando esse formato. Você pode usar um formato diferente do padrão para comunicação interna entre o microservices. Você pode fazer isso ao se comunicar entre microservices no Docker host ou microsserviço cluster (orchestrators Docker ou do Azure Service Fabric) ou para aplicativos cliente proprietárias que falar com o microservices.

### <a name="requestresponse-communication-with-http-and-rest"></a>Comunicação de solicitação/resposta com HTTP e REST 

Quando um cliente usa a comunicação de solicitação/resposta, ele envia uma solicitação para um serviço, em seguida, o serviço processa a solicitação e envia uma resposta. Comunicação de solicitação/resposta é especialmente adequada para consultar dados de uma interface de usuário em tempo real (uma interface do usuário em tempo real) dos aplicativos cliente. Portanto, em uma arquitetura de microsserviço você provavelmente usará esse mecanismo de comunicação para a maioria das consultas, conforme mostrado na Figura 4-16.

![](./media/image16.png)

**Figura 4-16**. Usando a comunicação de solicitação/resposta HTTP (síncrona ou assíncrona)

Quando um cliente usa a comunicação de solicitação/resposta, ele pressupõe que a resposta chegarão em um curto período de tempo, geralmente menos de um segundo ou alguns segundos no máximo. Para obter respostas atrasadas, você precisa implementar a comunicação assíncrona com base em [padrões de mensagens](https://docs.microsoft.com/azure/architecture/patterns/category/messaging) e [mensagens tecnologias](https://en.wikipedia.org/wiki/Message-oriented_middleware), que é uma abordagem diferente explicamos na próxima seção.

Um estilo popular de arquitetura para comunicação de solicitação/resposta é [REST](https://en.wikipedia.org/wiki/Representational_state_transfer). Essa abordagem é baseada e rigidamente acoplada, o [HTTP](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) protocolo, adotando verbos HTTP como GET, POST e colocar. REST é a abordagem de arquitetura de comunicação mais comumente usadas durante a criação de serviços. Você pode implementar serviços REST ao desenvolver serviços de API da Web do ASP.NET Core.

Há valor adicional ao usar serviços REST de HTTP como linguagem de definição de interface. Por exemplo, se você usar [Swagger metadados](http://swagger.io/) para descrever sua API de serviço, você pode usar ferramentas que geram stubs de cliente que podem descobrir e consumir seus serviços diretamente.

### <a name="additional-resources"></a>Recursos adicionais

-   **Martin Fowler. Modelo de maturidade Richardson.** Uma descrição do modelo de REST.
    [*http://martinfowler.com/articles/richardsonMaturityModel.HTML*](http://martinfowler.com/articles/richardsonMaturityModel.html)

-   **Swagger.** O site oficial.
    [*http://swagger.IO/*](http://swagger.io/)

### <a name="push-and-real-time-communication-based-on-http"></a>Envio e comunicação em tempo real com base em HTTP

Outra possibilidade (geralmente para finalidades diferentes REST) é uma comunicação em tempo real e um-para-muitos com estruturas de nível mais alto, como [ASP.NET SignalR](https://www.asp.net/signalr) e protocolos como [WebSockets](https://en.wikipedia.org/wiki/WebSocket).

Como mostra a Figura 4-17, a comunicação HTTP em tempo real significa que você pode ter o código de servidor Publicando conteúdo para clientes conectados, como os dados se torna disponíveis, em vez de ter o servidor espera para um cliente solicitar novos dados.

![](./media/image17.png)

**Figura 4-17**. Comunicação de um para um mensagem assíncrona em tempo real

Como a comunicação em tempo real, os aplicativos cliente mostram as alterações quase instantaneamente. Geralmente, isso é tratado por um protocolo como WebSockets, usando várias conexões WebSocket (um por cliente). Um exemplo típico é quando um serviço comunica-se uma alteração na partição de um jogo de esportes para muitos aplicativos de web do cliente simultaneamente.


>[!div class="step-by-step"]
[Anterior] (direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md) [Avançar] (assíncrona-mensagem-com base-communication.md)
