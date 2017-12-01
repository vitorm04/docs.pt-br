---
title: Assinando eventos
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Assinando eventos"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: fe17b53a39ff2964cd60183e291e2936d3ba28df
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="subscribing-to-events"></a>Assinando eventos

A primeira etapa para usar o barramento de evento é assinar microservices os eventos que desejam receber. Isso deve ser feito em microservices o receptor.

O código simple a seguir mostra o que cada destinatário microsserviço precisa implementar ao iniciar o serviço (ou seja, na inicialização de classe) para que ela assina os eventos ele precisa. Por exemplo, o microsserviço basket.api precisa se inscrever em ProductPriceChangedIntegrationEvent mensagens. Isso torna o microsserviço reconhece as alterações para o preço do produto e permite que ele avisar o usuário sobre a alteração se o produto está em sua cesta do usuário.

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();
eventBus.Subscribe<ProductPriceChangedIntegrationEvent>(
    ProductPriceChangedIntegrationEventHandler);
```

Depois que esse código é executado, o assinante microsserviço estará escutando por meio de canais de RabbitMQ. Quando qualquer mensagem do tipo ProductPriceChangedIntegrationEvent chega, o código invoca o manipulador de eventos que é passado a ele e processa o evento.

## <a name="publishing-events-through-the-event-bus"></a>Publicar eventos por meio do barramento de evento

Por fim, o remetente da mensagem (origem microsserviço) publica os eventos de integração com o código semelhante ao exemplo a seguir. (Isso é um exemplo simplificado que não precise de atomicidade em conta). Você poderia implementar um código semelhante sempre que um evento deve ser propagado por vários microservices, geralmente logo após a confirmação de dados ou transações de microsserviço a origem.

Primeiro, o objeto de implementação de barramento de evento (com base em RabbitMQ ou em um barramento de serviço) seria injetado no construtor do controlador, como no código a seguir:

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    private readonly CatalogContext _context;
    private readonly IOptionsSnapshot<Settings> _settings;
    private readonly IEventBus _eventBus;

    public CatalogController(CatalogContext context,
        IOptionsSnapshot<Settings> settings,
        IEventBus eventBus)
    {
        _context = context;
        _settings = settings;
        _eventBus = eventBus;
    }
    // ...
}
```

Em seguida, você usá-lo de métodos do controlador, como no método UpdateProduct:

```csharp
[Route("update")]
[HttpPost]
public async Task<IActionResult> UpdateProduct([FromBody]CatalogItem product)
{
    var item = await _context.CatalogItems.SingleOrDefaultAsync(
        i => i.Id == product.Id);
    // ...
    if (item.Price != product.Price)
    {
        var oldPrice = item.Price;
        item.Price = product.Price;
        _context.CatalogItems.Update(item);
        var @event = new ProductPriceChangedIntegrationEvent(item.Id,
            item.Price,
            oldPrice);
        // Commit changes in original transaction
        await _context.SaveChangesAsync();
        // Publish integration event to the event bus
        // (RabbitMQ or a service bus underneath)
        _eventBus.Publish(@event);
        // ...
    }
    // ...
}
```

Nesse caso, como o microsserviço de origem é um microsserviço CRUD simple, que o código é colocado à direita em um controlador Web API. No microservices mais avançadas, ele pode ser implementado na classe CommandHandler, à direita depois que os dados originais são confirmados.

### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a>Criando a atomicidade e a resiliência durante a publicação para o barramento de evento

Quando você publica os eventos de integração por meio de um sistema de mensagens distribuídas sistema como o barramento de evento, você tem o problema de forma atômica atualizando o banco de dados original e publicação de um evento. Por exemplo, no exemplo simplificado mostrado anteriormente, o código confirma dados o banco de dados quando o preço do produto é alterado e, em seguida, publica uma mensagem ProductPriceChangedIntegrationEvent. Inicialmente, ele pode ser essencial que essas duas operações ser executada atomicamente. No entanto, se você estiver usando uma transação distribuída que envolvem o banco de dados e a mensagem do agente, como faria em sistemas mais antigos como [Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx), isso não é recomendado pelos motivos descritos pela [Teorema de CAP](https://www.quora.com/What-Is-CAP-Theorem-1).

Basicamente, você deve usar microservices para criar sistemas escalonáveis e altamente disponíveis. Simplificando um pouco, o Teorema de CAP diz que você não pode criar um banco de dados (ou um microsserviço que possui seu modelo) que é continuamente disponíveis, altamente consistente, *e* tolerante a falhas para qualquer partição. Você deve escolher dois desses três propriedades.

Em arquiteturas de microservices, você deve escolher a disponibilidade e a tolerância e você deve remover consistência forte. Portanto, na maioria dos aplicativos baseados em microsserviço, geralmente não desejar usar transações distribuídas no sistema de mensagens, como faz quando você implementa [transações distribuídas](https://msdn.microsoft.com/library/ms978430.aspx#bdadotnetasync2_topic3c) com base em que a transação distribuída do Windows DTC (coordenador) com [MSMQ](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx).

Vamos voltar para o problema inicial e o seu exemplo. Se o serviço falhar após a atualização do banco de dados (nesse caso, logo após a linha de código com \_contexto. SaveChangesAsync()), mas antes do evento de integração é publicado, todo o sistema pode se tornar inconsistente. Isso pode ser crítico, dependendo da operação de negócios específicas que você está lidando com negócios.

Como mencionado anteriormente na seção de arquitetura, você pode ter várias abordagens para lidar com esse problema:

-   Usando o completo [padrão de evento de fornecimento](https://msdn.microsoft.com/en-us/library/dn589792.aspx).

-   Usando [mineração do log de transações](http://www.scoop.it/t/sql-server-transaction-log-mining).

-   Usando o [da caixa de saída padrão](http://gistlabs.com/2014/05/the-outbox/). Essa é uma tabela transacional para armazenar os eventos de integração (estendendo a transação local).

Para este cenário, usando o padrão de evento Sourcing (ES) completo é um dos melhores abordagens, se não *o* melhor. No entanto, em muitos cenários de aplicativo, você pode não ser capaz de implementar um sistema completo de ES. ES significa armazenar apenas os eventos de domínio em seu banco de dados transacional, em vez de armazenar dados de estado atual. Armazenar apenas os eventos de domínio pode ter grandes benefícios, como tendo o histórico do sistema disponível e ser capaz de determinar o estado do sistema em qualquer momento no passado. No entanto, implementar um sistema completo de ES exige que você Refaça a maior parte do seu sistema de arquitetura e apresenta muitas outras complexidades e os requisitos. Por exemplo, convém usar um banco de dados feito especificamente para fornecimento de evento, como [repositório de eventos](https://geteventstore.com/), ou um banco de dados orientado por documentos, como o banco de dados do Azure Cosmos, MongoDB, Cassandra, CouchDB ou RavenDB. ES é uma abordagem ótima para esse problema, mas não a solução mais fácil, a menos que você já estiver familiarizado com o fornecimento do evento.

A opção de usar o log de transações de mineração inicialmente parece muito transparente. No entanto, para usar essa abordagem, o microsserviço deve ser associada ao seu log de transações do RDBMS, como o log de transações do SQL Server. Isso provavelmente não é desejável. Outra desvantagem é que as atualizações de baixo nível registradas no log de transações podem não estar no mesmo nível como seus eventos de integração de alto nível. Nesse caso, o processo de engenharia reversa essas operações de log de transações podem ser difícil.

Uma abordagem equilibrada é uma combinação de uma tabela de banco de dados transacional e um padrão de ES simplificado. Você pode usar um estado, como "pronto para publicar o evento," que você definir no evento original quando confirmá-la para a tabela de eventos de integração. Em seguida, tentar publicar o evento para o barramento de evento. Se a ação de evento de publicação tiver êxito, iniciar outra transação no serviço de origem e mover o estado de "pronto para publicar o evento" para "evento" já foi publicado.

Se a ação de evento de publicação no evento de barramento falhar, os dados ainda não será inconsistentes dentro de microsserviço origem — ainda está marcado como "pronto para publicar o evento" e, em relação ao restante dos serviços, eventualmente será consistente. Você sempre pode ter trabalhos em segundo plano verificar o estado das transações ou eventos de integração. Se o trabalho de encontrar um evento no estado "pronto publicar o evento", pode tentar publicar novamente o evento para o barramento de evento.

Observe que, com essa abordagem, você é persistentes apenas os eventos de integração para cada microsserviço de origem e somente os eventos que você deseja se comunicar com outros microservices ou sistemas externos. Em contraste, em um sistema completo de ES, armazenar todos os eventos de domínio.

Portanto, essa abordagem equilibrada é um sistema de ES simplificado. Você precisa de uma lista de eventos de integração com seu estado atual ("pronto para publicar" versus "publicado"). Mas você só precisa implementar esses estados para os eventos de integração. E nessa abordagem, você não precisa armazenar todos os seus dados de domínio como eventos no banco de dados transacional, como você faria em um sistema completo de ES.

Se você já estiver usando um banco de dados relacional, você pode usar uma tabela transacional para armazenar eventos de integração. Para obter a atomicidade em seu aplicativo, você deve usar um processo de duas etapas com base em transações locais. Basicamente, você tem uma tabela de IntegrationEvent no mesmo banco de dados em que as entidades de domínio. Essa tabela funciona como um seguro para a obtenção de atomicidade para que você incluir persistentes eventos de integração para as mesmas transações que estejam sendo confirmadas seus dados de domínio.

Passo a passo, o processo é a seguinte: o aplicativo começa uma transação de banco de dados local. Em seguida, ele atualizará o estado de suas entidades de domínio e insere um evento na tabela de eventos de integração. Finalmente, ele confirma a transação. Você obtém a atomicidade desejada.

Ao implementar as etapas de publicação de eventos, você tem estas opções:

-   Publicar o evento de integração logo após a confirmação da transação e usar outra transação local para marcar os eventos na tabela que está sendo publicado. Em seguida, use a tabela como um artefato para controlar os eventos de integração em caso de problemas de microservices remoto e executar ações compensatórios com base em eventos de integração armazenado.

-   Use a tabela como um tipo de fila. Um thread de aplicativo separado ou o processo de consulta a tabela de eventos de integração, publica os eventos do barramento de evento e, em seguida, usa uma transação local para marcar os eventos como publicado.

Figura 8-22 mostra a arquitetura para a primeira dessas abordagens.

![](./media/image23.png)

**Figura 8-22**. Atomicidade ao publicar eventos do barramento de evento

A abordagem ilustrada na Figura 8-22 está faltando um microsserviço adicionais do trabalhador que é responsável por verificar e confirmar o êxito dos eventos de integração publicado. Em caso de falha, que microsserviço de trabalho adicionais verificador pode ler os eventos da tabela e publicá-los novamente.

Sobre a segunda abordagem: use a tabela de log de eventos como uma fila e sempre usar um microsserviço de trabalho para publicar as mensagens. Nesse caso, o processo de como é mostrado na Figura 8-23. Isso mostra um microsserviço adicional, e a tabela é a única fonte ao publicar eventos.

![](./media/image24.png)

**Figura 8-23**. Atomicidade ao publicar eventos do barramento de evento com um microsserviço de trabalho

Para simplificar, o exemplo de eShopOnContainers usa a primeira abordagem (sem nenhum processos adicionais ou verificador microservices) e o barramento de evento. No entanto, o eShopOnContainers não trata todos os casos de falha possíveis. Em um aplicativo real, implantado na nuvem, você deve adotar o fato de que problemas surgirão eventualmente, e você deve implementar que verifique e reenviar lógica. Usando a tabela como uma fila pode ser mais eficiente do que a primeira abordagem, se você tiver essa tabela como uma única fonte de eventos ao publicá-los por meio do barramento de evento.

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a>Implementando a atomicidade ao publicar eventos de integração por meio do barramento de evento

O código a seguir mostra como você pode criar uma única transação que envolve vários objetos DbContext — um contexto relacionados aos dados originais que está sendo atualizados e o contexto de segundo relacionada à tabela IntegrationEventLog.

Observe que a transação no código de exemplo a seguir não será resiliente se conexões ao banco de dados tem qualquer problema ao tempo quando o código está sendo executado. Isso pode ocorrer em sistemas baseados em nuvem como o Azure SQL DB, que pode mover bancos de dados entre servidores. Para implementar transações resilientes em vários contextos, consulte o [Implementando conexões Entity Framework Core SQL](#implementing_resilient_EFCore_SQL_conns) seção posteriormente neste guia.

Para maior clareza, o exemplo a seguir mostra todo o processo em um único segmento de código. No entanto, a implementação de eShopOnContainers, na verdade, é Refatorada e dividir essa lógica em várias classes, sendo mais fácil de manter.

```csharp
// Update Product from the Catalog microservice
//
public async Task<IActionResult>
    UpdateProduct([FromBody]CatalogItem productToUpdate)
{
    var catalogItem = await _catalogContext.CatalogItems
        .SingleOrDefaultAsync(i => i.Id == productToUpdate.Id);

    if (catalogItem == null) return NotFound();

    bool raiseProductPriceChangedEvent = false;

    IntegrationEvent priceChangedEvent = null;

    if (catalogItem.Price != productToUpdate.Price)
        raiseProductPriceChangedEvent = true;

    if (raiseProductPriceChangedEvent) // Create event if price has changed
    {
        var oldPrice = catalogItem.Price;
        priceChangedEvent = new ProductPriceChangedIntegrationEvent(catalogItem.Id,
            productToUpdate.Price,
            oldPrice);
    }

    // Update current product
    catalogItem = productToUpdate;
    // Achieving atomicity between original DB and the IntegrationEventLog
    // with a local transaction

    using (var transaction = _catalogContext.Database.BeginTransaction())
    {
        _catalogContext.CatalogItems.Update(catalogItem);

        await _catalogContext.SaveChangesAsync();

        // Save to EventLog only if product price changed
        if(raiseProductPriceChangedEvent)
            await _integrationEventLogService.SaveEventAsync(priceChangedEvent);
        transaction.Commit();
   }

   // Publish to event bus only if product price changed

   if (raiseProductPriceChangedEvent)
   {
       _eventBus.Publish(priceChangedEvent);
       integrationEventLogService.MarkEventAsPublishedAsync(
           priceChangedEvent);
   }

   return Ok();
}
```

Depois que o evento de integração ProductPriceChangedIntegrationEvent é criado, a transação que armazena a operação de domínio original (atualizar o item de catálogo) também inclui a persistência do evento na tabela de log de eventos. Isso faz com que uma única transação, e sempre será capaz de verificar se as mensagens de evento são enviadas.

A tabela de log de eventos é atualizada atomicamente com a operação de banco de dados original, usando uma transação local no mesmo banco de dados. Se qualquer uma das operações falhar, uma exceção será lançada e a transação reverte qualquer operação concluída, assim, manter a consistência entre as operações de domínio e as mensagens de eventos enviadas.

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a>Receber mensagens de assinaturas: manipuladores de eventos no destinatário microservices

Além da lógica de assinatura de evento, você precisa implementar o código interno para os manipuladores de eventos de integração (como um método de retorno de chamada). O manipulador de eventos é onde você especifica onde as mensagens de eventos de um determinado tipo serão recebidas e processadas.

Primeiro, um manipulador de eventos recebe uma instância de eventos do barramento de evento. Em seguida, ele localiza o componente a ser processado relacionados a esse evento de integração, propagando e a manter o evento como uma alteração no estado em que o destinatário microsserviço. Por exemplo, se um evento ProductPriceChanged se origina no microsserviço catálogo, ele é tratado no microsserviço carrinho e altera o estado de microsserviço de carrinho esse destinatário bem, conforme mostrado no código a seguir.

```csharp
namespace Microsoft.eShopOnContainers.Services.Basket.API.IntegrationEvents.EventHandling
{
    public class ProductPriceChangedIntegrationEventHandler :
        IIntegrationEventHandler<ProductPriceChangedIntegrationEvent>
    {
        private readonly IBasketRepository _repository;

        public ProductPriceChangedIntegrationEventHandler(
            IBasketRepository repository)
        {
            _repository = repository;
        }

        public async Task Handle(ProductPriceChangedIntegrationEvent @event)
        {
            var userIds = await _repository.GetUsers();
            foreach (var id in userIds)
            {
                var basket = await _repository.GetBasket(id);
                await UpdatePriceInBasketItems(@event.ProductId, @event.NewPrice, basket);
            }
        }

        private async Task UpdatePriceInBasketItems(int productId, decimal newPrice,
            CustomerBasket basket)
        {
            var itemsToUpdate = basket?.Items?.Where(x => int.Parse(x.ProductId) ==
                productId).ToList();
            if (itemsToUpdate != null)
            {
                foreach (var item in itemsToUpdate)
                {
                    if(item.UnitPrice != newPrice)
                    {
                        var originalPrice = item.UnitPrice;
                        item.UnitPrice = newPrice;
                        item.OldUnitPrice = originalPrice;
                    }
                }
                await _repository.UpdateBasket(basket);
            }
        }
    }
}
```

O manipulador de eventos deve verificar se o produto existe em qualquer uma das instâncias do carrinho. Ele também atualiza o preço de item para cada item de linha do carrinho relacionados. Por fim, ele cria um alerta a ser exibido para o usuário sobre a alteração de preço, conforme mostrado na Figura 8-24.

![](./media/image25.png)

**Figura 8-24**. Exibindo uma alteração de preço de item em um carrinho, como comunicação por eventos de integração

## <a name="idempotency-in-update-message-events"></a>Idempotência em eventos de mensagem de atualização

Um aspecto importante de eventos de mensagem de atualização é uma falha em qualquer ponto de comunicação deve fazer com que a mensagem a ser repetida. Caso contrário, uma tarefa em segundo plano pode tentar publicar um evento que já tenha sido publicado, criando uma condição de corrida. Você precisa para certificar-se de que as atualizações são idempotentes ou que eles fornecem informações suficientes para garantir que você pode detectar uma duplicata, descartá-lo e enviar a resposta de volta apenas um.

Conforme observado anteriormente, idempotência significa que uma operação pode ser executada várias vezes sem alterar o resultado. Em um ambiente de mensagens, como ao se comunicar eventos, um evento é idempotente, se ele pode ser fornecido várias vezes sem alterar o resultado para o receptor microsserviço. Isso pode ser necessário devido à natureza do evento em si, ou devido a maneira como o sistema manipula o evento. Mensagem idempotência é importante em qualquer aplicativo que usa a mensagem, não apenas em aplicativos que implementam o padrão de barramento de evento.

Um exemplo de uma operação idempotente é uma instrução SQL que insere dados em uma tabela somente se os dados não ainda estiver na tabela. Não importa quantas vezes você executar que inserir instrução SQL; o resultado será o mesmo — a tabela conterá esses dados. Idempotência como isso também pode ser necessário ao lidar com mensagens se as mensagens potencialmente enviadas e processados, portanto, mais de uma vez. Por exemplo, se a lógica de repetição faz com que um remetente envie exatamente a mesma mensagem mais de uma vez, você precisa certificar-se de que ele é idempotente.

É possível design idempotente mensagens. Por exemplo, você pode criar um evento que diz "definir o preço do produto \$25" em vez de "adicionar \$5 para o preço do produto." Foi possível processar a primeira mensagem com segurança qualquer número de vezes e o resultado será o mesmo. Não é válido para a segunda mensagem. Mas mesmo no primeiro caso, você pode não processar o primeiro evento, porque o sistema também pode ter enviado um evento de alteração de preço mais recente e você deve substituir o novo preço.

Outro exemplo pode ser um evento de pedido concluído foi propagado por vários assinantes. É importante que as informações de ordem sejam atualizados em outros sistemas apenas uma vez, mesmo se houver eventos de mensagem duplicada para o mesmo evento ordem concluída.

É conveniente ter algum tipo de identidade por evento para que você possa criar lógica que impõe que cada evento é processado apenas uma vez por destinatário.

Algum processamento de mensagem é inerentemente idempotentes. Por exemplo, se um sistema gera miniaturas de imagem, ele não pode importa quantas vezes a mensagem sobre a miniatura gerada é processada; o resultado é que as miniaturas são geradas e elas forem iguais sempre. Por outro lado, as operações como chamar um gateway de pagamento para cobrar o cartão de crédito podem não ser idempotentes em todos os. Nesses casos, você precisa garantir que o processamento de uma mensagem várias vezes tenha o efeito que você espera.

### <a name="additional-resources"></a>Recursos adicionais

-   **Para respeitar mensagem idempotência** (subtítulo nesta página) [ *https://msdn.microsoft.com/en-us/library/jj591565.aspx*](https://msdn.microsoft.com/en-us/library/jj591565.aspx)

## <a name="deduplicating-integration-event-messages"></a>Eliminação da duplicação de mensagens de eventos de integração

Você pode assegurar que os eventos de mensagem são enviados e processados apenas uma vez por assinante em diferentes níveis. Uma maneira é usar um recurso de eliminação de duplicação oferecido pela infraestrutura de mensagens que você está usando. Outra é implementar a lógica personalizada em seu destino microsserviço. A melhor opção é ter validações no nível de transporte e no nível do aplicativo.

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a>Eventos de eliminação da duplicação de mensagem no nível de EventHandler

Uma maneira para certificar-se de que um evento é processado apenas uma vez por qualquer receptor é implementar a lógica de determinadas durante o processamento de eventos de mensagem em manipuladores de eventos. Por exemplo, que é a abordagem usada no aplicativo eShopOnContainers, como você pode ver no [código-fonte](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Controllers/OrdersController.cs) da classe OrdersController quando ele recebe um comando CreateOrderCommand. (Nesse caso, usamos um comando de solicitação HTTP, não um mensagem de comando baseado, mas a lógica que você precisa fazer um comando baseado em mensagem idempotente é semelhante).

### <a name="deduplicating-messages-when-using-rabbitmq"></a>Eliminação da duplicação de mensagens ao usar RabbitMQ

Quando ocorrem falhas intermitentes de rede, as mensagens podem ser duplicadas e o destinatário da mensagem deve estar pronto para lidar com essas mensagens duplicadas. Se possível, receptores devem lidar com mensagens de forma idempotentes, é melhor que explicitamente tratá-los com eliminação de duplicação.

De acordo com o [RabbitMQ documentação](https://www.rabbitmq.com/reliability.html#consumer), "se uma mensagem é entregue a um cliente e, em seguida, retirada da fila (porque ele não foi confirmado antes de descartar a conexão do consumidor, por exemplo), RabbitMQ definirá o sinalizador redelivered em ele quando ele for entregue novamente (para o consumidor mesmo ou um diferente).

Se o sinalizador "redelivered" for definido, o receptor deve consideram que, porque a mensagem pode já ter sido processada. Mas que não é garantida; a mensagem pode nunca ter alcançado o destinatário depois que ele foi o agente de mensagens, talvez devido a problemas de rede. Por outro lado, se o sinalizador "redelivered" não está definido, é garantido que a mensagem não foi enviada mais de uma vez. Portanto, o receptor deve eliminar a duplicação de mensagens ou processar mensagens de uma maneira idempotente somente se o sinalizador "redelivered" está definido na mensagem.

### <a name="additional-resources"></a>Recursos adicionais

-   **Mensagens de eventos controlada por**
    [*http://soapatterns.org/design\_padrões/evento\_controlados por\_de mensagens*](http://soapatterns.org/design_patterns/event_driven_messaging)

-   **Jimmy Bogard. Refatoração em direção a resiliência: Avaliando acoplamento**
    [*https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/*](https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/)

-   **Canal de publicação / assinatura**
    [*http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html*](http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html)

-   **Comunicação entre limitada contextos**
    [*https://msdn.microsoft.com/en-us/library/jj591572.aspx*](https://msdn.microsoft.com/en-us/library/jj591572.aspx)

-   **Consistência eventual**
    [*https://en.wikipedia.org/wiki/Eventual\_consistência*](https://en.wikipedia.org/wiki/Eventual_consistency)

-   **Philip marrom. Estratégias para a integração limitada contextos**
    [*http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/*](http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/)

-   **Carlos Richardson. Desenvolvendo Microservices transacional usando agregações, fornecimento de evento e CQRS - parte 2**
    [*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson)

-   **Carlos Richardson. Evento originando padrão**
    [*http://microservices.io/patterns/data/event-sourcing.html*](http://microservices.io/patterns/data/event-sourcing.html)

-   **Introdução ao fornecimento de evento**
    [*https://msdn.microsoft.com/en-us/library/jj591559.aspx*](https://msdn.microsoft.com/en-us/library/jj591559.aspx)

-   **Banco de dados do repositório de eventos**. Site oficial.
    [*https://geteventstore.com/*](https://geteventstore.com/)

-   **Patrick Nommensen. Gerenciamento de dados para Microservices controlada por evento**
    *<https://dzone.com/articles/event-driven-data-management-for-microservices-1>*

-   **O Teorema de CAP**
    [*https://en.wikipedia.org/wiki/CAP\_Teorema*](https://en.wikipedia.org/wiki/CAP_theorem)

-   **O que é o Teorema de Extremidade? ** 
     [ *https://www.quora.com/What-Is-CAP-Theorem-1*](https://www.quora.com/What-Is-CAP-Theorem-1)

-   **Primer de consistência de dados**
    [*https://msdn.microsoft.com/en-us/library/dn589800.aspx*](https://msdn.microsoft.com/en-us/library/dn589800.aspx)

-   **Rick Saling. O Teorema de CAP: Por que "Tudo o que é diferente" com a nuvem e a Internet**
    [*https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/*](https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/)

-   **Eric Brewer. LIMITE de 12 anos mais tarde: como "Regras" mudaram**
    [*https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed*](https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed)

-   **Participar de transações externas (DTC)** (MSMQ) [ *https://msdn.microsoft.com/en-us/library/ms978430.aspx\#bdadotnetasync2\_topic3c*](https://msdn.microsoft.com/en-us/library/ms978430.aspx%23bdadotnetasync2_topic3c)

-   **Barramento de serviço do Azure. Mensagens orientadas: Detecção de duplicidades**
    [*https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25*](https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25)

-   **Guia de confiabilidade** (RabbitMQ documentação) [ *https://www.rabbitmq.com/reliability.html\#consumidor*](https://www.rabbitmq.com/reliability.html%23consumer)




>[!div class="step-by-step"]
[Anterior] (rabbitmq-event-bus-development-test-environment.md) [Avançar] (test-aspnet-core-services-web-apps.md)
