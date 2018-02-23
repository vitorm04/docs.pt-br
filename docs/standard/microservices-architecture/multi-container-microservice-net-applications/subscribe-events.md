---
title: Assinando eventos
description: "Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Assinando eventos"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7538c760d396349fe9b1e93a21839e3e59d7f046
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="subscribing-to-events"></a>Assinando eventos

A primeira etapa para usar o barramento de eventos é fazer com que os microsserviços assinem os eventos que eles desejam receber. Isso deve ser feito nos microsserviços destinatários.

O código simples a seguir mostra o que cada destinatário de microsserviço precisa implementar ao iniciar o serviço (ou seja, a classe `Startup`) para assinar os eventos que precisa. Nesse caso, o microsserviço `basket.api` precisa assinar as mensagens `ProductPriceChangedIntegrationEvent` e `OrderStartedIntegrationEvent`. 

Por exemplo, ao assinar o evento `ProductPriceChangedIntegrationEvent`, o microsserviço carrinho de compras tomará ciência de qualquer mudança no preço do produto e será capaz de avisar o usuário a respeito da alteração, caso o produto esteja em seu carrinho de compras.

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();

eventBus.Subscribe<ProductPriceChangedIntegrationEvent, 
                   ProductPriceChangedIntegrationEventHandler>();

eventBus.Subscribe<OrderStartedIntegrationEvent, 
                   OrderStartedIntegrationEventHandler>();

```

Depois que esse código for executado, o microsserviço assinante escutará por meio de canais RabbitMQ. Quando qualquer mensagem do tipo ProductPriceChangedIntegrationEvent chegar, o código invocará o manipulador de eventos, que será passado a ele e processará o evento.

## <a name="publishing-events-through-the-event-bus"></a>Publicando eventos por meio do barramento de eventos

Por fim, o remetente da mensagem (microsserviço de origem) publica os eventos de integração com um código semelhante ao exemplo a seguir. (Esse é um exemplo simplificado, que não leva a atomicidade em consideração). Você poderia implementar um código semelhante sempre que um evento tivesse que ser propagado por vários microsserviços, geralmente logo após a confirmação dos dados ou das transações do microsserviço de origem.

Primeiro, o objeto de implementação do barramento de eventos (baseado no RabbitMQ ou em um barramento de serviço) seria injetado no construtor do controlador, como no código a seguir:

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

Em seguida, você o usaria nos métodos do controlador, como no método UpdateProduct:

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

Nesse caso, como o microsserviço de origem é um microsserviço CRUD simples, o código é colocado diretamente em um controlador de API Web. 
 
Em microsserviços mais avançados, como ao usar abordagens de CQRS, ele pode ser implementado na classe `CommandHandler`, dentro do método `Handle()`. 


### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a>Criando atomicidade e resiliência ao publicar no barramento de eventos

Ao publicar eventos de integração por meio de um sistema de mensagens distribuído como o barramento de eventos, você tem o problema da atualização do banco de dados original e da publicação de um evento de forma atômica. Por exemplo, no exemplo simplificado mostrado anteriormente, o código confirma os dados no banco de dados quando o preço do produto é alterado e, em seguida, publica uma mensagem ProductPriceChangedIntegrationEvent. Inicialmente, pode parecer essencial que essas duas operações sejam executada atomicamente. No entanto, se você estivesse usando uma transação distribuída que envolvesse o banco de dados e o agente de mensagens, assim como faria em sistemas mais antigos, como o [MSMQ (Enfileiramento de Mensagens da Microsoft)](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx), isso não seria recomendado pelos motivos descritos pelo [Teorema CAP](https://www.quora.com/What-Is-CAP-Theorem-1).

Basicamente, você usa microsserviços para criar sistemas escalonáveis e altamente disponíveis. Simplificando um pouco, o Teorema CAP diz que você não pode criar um banco de dados (ou um microsserviço que seja proprietário desse modelo) que seja continuamente disponível, altamente consistente *e* tolerante a qualquer partição. Você deve escolher duas dessas três propriedades.

Em arquiteturas baseadas em microsserviços, você deve escolher a disponibilidade e a tolerância e deve tirar a ênfase da coerência forte. Portanto, na maioria dos aplicativos modernos baseados em microsserviços, geralmente não é interessante usar transações distribuídas no sistema de mensagens, como ao implementar [transações distribuídas](https://msdn.microsoft.com/library/ms978430.aspx#bdadotnetasync2_topic3c) com base no DTC (Coordenador de Transações Distribuídas) do Windows com o [MSMQ](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx).

Vamos voltar para o problema inicial e o respectivo exemplo. Se o serviço falhar após a atualização do banco de dados (nesse caso, logo após a linha de código com \_context.SaveChangesAsync()), mas antes que o evento de integração seja publicado, todo o sistema poderá se tornar inconsistente. Isso pode ser crítico, dependendo da operação de negócios específica com a qual você está lidando.

Como mencionado anteriormente na seção de arquitetura, você pode ter várias abordagens para lidar com esse problema:

-   Usando o padrão [Event Sourcing](https://msdn.microsoft.com/library/dn589792.aspx) completo.

-   Usando [mineração do log de transações](http://www.scoop.it/t/sql-server-transaction-log-mining).

-   Usando o [padrão Outbox](http://gistlabs.com/2014/05/the-outbox/). Essa é uma tabela transacional para armazenar os eventos de integração (estendendo a transação local).

Neste cenário, o uso do padrão ES (Event Sourcing) completo é uma das melhores abordagens, se não for *a* melhor. No entanto, em muitos cenários de aplicativo, pode ser impossível implementar um sistema completo de ES. O ES significa o armazenamento somente dos eventos de domínio em seu banco de dados transacional, em vez de armazenar dados do estado atual. Armazenar apenas os eventos de domínio pode ter grandes benefícios, como ter o histórico do sistema disponível e poder determinar o estado do sistema em qualquer momento no passado. No entanto, implementar um sistema de ES completo exige que você refaça a arquitetura da maior parte do seu sistema e também pode apresentar muitas outras complexidades e requisitos. Por exemplo, vai ser interessante usar um banco de dados criado especificamente para fornecimento de eventos, como o [Event Store](https://geteventstore.com/), ou um banco de dados orientado a documentos, como Azure Cosmos DB, MongoDB, Cassandra, CouchDB ou RavenDB. O ES é uma ótima abordagem para esse problema, mas não é a solução mais fácil, a menos que você já esteja familiarizado com fornecimento de eventos.

A opção de usar a mineração do log de transações pode, inicialmente, parecer muito transparente. No entanto, para usar essa abordagem, o microsserviço deverá ser acoplado ao seu log de transações do RDBMS, como o log de transações do SQL Server. Isso provavelmente não é interessante. Outra desvantagem é que as atualizações de baixo nível registradas no log de transações podem não estar no mesmo nível que seus eventos de integração de alto nível. Nesse caso, o processo de engenharia reversa dessas operações do log de transações poderá ser difícil.

Uma abordagem equilibrada é uma combinação de uma tabela de banco de dados transacional e um padrão de ES simplificado. Você pode usar um estado, como "pronto para publicar o evento," que você define no evento original ao confirmá-lo para a tabela de eventos de integração. Em seguida, você tenta publicar o evento no barramento de eventos. Se a ação publicar evento for bem sucedida, você iniciará outra transação no serviço de origem e mudará o estado de "pronto para publicar o evento" para "evento já publicado".

Se a ação publicar evento falhar no barramento de eventos, os dados ainda não estarão inconsistentes no microsserviço origem – ainda estarão marcados como "pronto para publicar o evento" e, em relação ao restante dos serviços, eles estarão eventualmente consistentes. Você sempre fazer com que trabalhos em segundo plano verifiquem o estado das transações ou dos eventos de integração. Se o trabalho encontrar um evento no estado "pronto para publicar o evento", ele poderá tentar publicá-lo novamente no barramento de eventos.

Observe que, com essa abordagem, você estará persistindo apenas os eventos de integração de cada microsserviço de origem e somente os eventos que você deseja comunicar para outros microsserviços ou sistemas externos. Por outro lado, em um sistema completo de ES, você também armazena todos os eventos de domínio.

Portanto, essa abordagem equilibrada é um sistema de ES simplificado. Você precisa de uma lista de eventos de integração com os respectivos estados atuais ("pronto para publicar" versus "publicado"). Mas você só precisa implementar esses estados para os eventos de integração. E, nessa abordagem, não é necessário armazenar todos os dados de domínio como eventos no banco de dados transacional, como você faria em um sistema completo de ES.

Se já está usando um banco de dados relacional, você pode usar uma tabela transacional para armazenar eventos de integração. Para obter a atomicidade em seu aplicativo, você usa um processo de duas etapas com base nas transações locais. Basicamente, você tem uma tabela IntegrationEvent no mesmo banco de dados em que estão as entidades de domínio. Essa tabela funciona como um seguro para a obtenção de atomicidade, para que você inclua eventos de integração persistidos nas mesmas transações que estão confirmando seus dados de domínio.

Passo a passo, o processo é o seguinte: o aplicativo dá início a uma transação de banco de dados local. Em seguida, ele atualiza o estado das suas entidades de domínio e insere um evento na tabela de eventos de integração. Finalmente, ele confirma a transação. E você obtém a atomicidade desejada.

Ao implementar as etapas de publicação dos eventos, você tem estas opções:

-   Publicar o evento de integração logo após a confirmação da transação e usar outra transação local para marcar os eventos na tabela como sendo publicados. Em seguida, usar a tabela apenas como um artefato para controlar os eventos de integração, em caso de problemas com os microsserviços remotos, e executar ações compensatórias com base nos eventos de integração armazenados.

-   Usar a tabela como um tipo de fila. Um thread ou processo do aplicativo separado consulta a tabela de eventos de integração, publica os eventos no barramento de eventos e, em seguida, usa uma transação local para marcar os eventos como publicados.

A figura 8-22 mostra a arquitetura da primeira dessas abordagens.

![](./media/image23.png)

**Figura 8-22**. Atomicidade ao publicar eventos no barramento de eventos

A abordagem ilustrada na Figura 8-22 não tem um microsserviço de trabalho adicional, que é responsável por verificar e confirmar o êxito dos eventos de integração publicados. Em caso de falha, esse microsserviço de trabalho verificador adicional pode ler os eventos na tabela e publicá-los novamente.

Em relação à segunda abordagem: você usa a tabela EventLog como uma fila e sempre usa um microsserviço de trabalho para publicar as mensagens. Nesse caso, o processo é como o mostrado na Figura 8-23. Ela mostra um microsserviço adicional, e a tabela é a única fonte durante a publicação de eventos.

![](./media/image24.png)

**Figura 8-23**. Atomicidade ao publicar eventos no barramento de eventos com um microsserviço de trabalho

Para simplificar, o exemplo eShopOnContainers usa a primeira abordagem (sem processos adicionais nem microsserviços verificadores) e o barramento de eventos. No entanto, o eShopOnContainers não trata todos os casos de falha possíveis. Em um aplicativo real implantado na nuvem, você deve aceitar o fato de que os problemas surgirão eventualmente, e você deverá implementar essa lógica de verificação e reenvio. O uso da tabela como uma fila poderá ser mais eficiente que a primeira abordagem se você tiver essa tabela como uma única fonte de eventos ao publicá-los por meio do barramento de eventos.

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a>Implementando atomicidade ao publicar eventos de integração por meio do barramento de eventos

O código a seguir mostra como criar uma única transação que envolva vários objetos DbContext: um contexto relacionados aos dados originais que estão sendo atualizados e o segundo contexto relacionado à tabela IntegrationEventLog.

Observe que a transação, no código de exemplo abaixo, não será resiliente se as conexões com o banco de dados enfrentarem qualquer problema no momento em que o código estiver sendo executado. Isso pode ocorrer em sistemas baseados em nuvem, como o BD SQL do Azure, que pode mover bancos de dados entre servidores. Para implementar transações resilientes em vários contextos, consulte a seção [Implementando conexões de SQL do Entity Framework Core resilientes](#implementing_resilient_EFCore_SQL_conns) mais adiante, neste guia.

Para maior clareza, o exemplo a seguir mostra todo o processo em um único segmento de código. No entanto, a implementação do eShopOnContainers refatorou e dividiu essa lógica em várias classes, sendo mais fácil de manter.

```csharp
// Update Product from the Catalog microservice
//
public async Task<IActionResult> UpdateProduct([FromBody]CatalogItem productToUpdate) 
{
  var catalogItem = 
       await _catalogContext.CatalogItems.SingleOrDefaultAsync(i => i.Id == 
                                                               productToUpdate.Id); 
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

  // Just save the updated product if the Product's Price hasn't changed.
  if !(raiseProductPriceChangedEvent) 
  {
      await _catalogContext.SaveChangesAsync();
  }
  else  // Publish to event bus only if product price changed
  {
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

      // Publish the intergation event through the event bus
      _eventBus.Publish(priceChangedEvent); 

      integrationEventLogService.MarkEventAsPublishedAsync(
                                                priceChangedEvent); 
  }

  return Ok();
}

```

Depois que o evento de integração ProductPriceChangedIntegrationEvent é criado, a transação que armazena a operação de domínio original (atualizar o item de catálogo) também inclui a persistência do evento na tabela EventLog. Isso faz com que ele se torne uma única transação, e sempre será possível verificar se as mensagens de evento foram enviadas.

A tabela do log de eventos é atualizada atomicamente com a operação do banco de dados original, usando uma transação local no mesmo banco de dados. Se qualquer uma das operações falhar, uma exceção será lançada e a transação reverterá qualquer operação concluída, mantendo assim a consistência entre as operações de domínio e as mensagens de evento enviadas.

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a>Recebendo mensagens de assinaturas: manipuladores de eventos em microsserviços destinatários

Além da lógica de assinatura de evento, você precisa implementar o código interno para os manipuladores de eventos de integração (como um método de retorno de chamada). O manipulador de eventos é o local em que você especifica o local em que as mensagens de eventos de um determinado tipo serão recebidas e processadas.

Primeiro, um manipulador de eventos recebe uma instância de evento do barramento de eventos. Em seguida, ele localiza o componente a ser processado, relacionado a esse evento de integração, propagando e persistindo o evento como uma alteração no estado no microsserviço destinatário. Por exemplo, se um evento ProductPriceChanged se origina no microsserviço catálogo, ele é tratado no microsserviço carrinho de compras e também altera o estado nesse microsserviço destinatário de carrinho de compras, conforme mostrado no código a seguir.

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

O manipulador de eventos deve verificar se o produto existe em qualquer uma das instâncias do carrinho de compras. Ele também atualiza o preço do item para cada item de linha relacionado ao carrinho. Por fim, ele cria um alerta sobre a alteração de preço, que será exibido para o usuário, conforme mostrado na Figura 8-24.

![](./media/image25.png)

**Figura 8-24**. Exibindo uma alteração de preço de item em um carrinho de compras, conforme comunicado pelos eventos de integração

## <a name="idempotency-in-update-message-events"></a>Idempotência em eventos de mensagem de atualização

Um aspecto importante dos eventos de mensagem de atualização é que uma falha em qualquer ponto da comunicação deverá fazer com que a mensagem seja repetida. Caso contrário, uma tarefa em segundo plano poderá tentar publicar um evento que já tenha sido publicado, criando uma condição de corrida. Você precisa se certificar de que as atualizações sejam idempotentes ou que elas forneçam informações suficientes para garantir que você possa detectar uma duplicata, descartá-la e enviar apenas uma resposta de volta.

Conforme observado anteriormente, a idempotência significa que uma operação poderá ser executada várias vezes sem alterar o resultado. Em um ambiente de sistema de mensagens, como ao comunicar eventos, um evento será idempotente se ele puder ser entregue várias vezes sem alterar o resultado para o microsserviço destinatário. Isso pode ser necessário devido à natureza do evento em si ou devido à maneira como o sistema manipula o evento. A idempotência de mensagem é importante em qualquer aplicativo que use o sistema de mensagens, e não apenas em aplicativos que implementam o padrão do barramento de eventos.

Um exemplo de uma operação idempotente é uma instrução SQL que insere dados em uma tabela somente se os dados ainda não estiverem na tabela. Não importa quantas vezes você executa essa instrução insert do SQL; o resultado será o mesmo: a tabela conterá esses dados. Essa idempotência também poderá ser necessária ao lidar com mensagens se houver chances de que elas sejam enviadas e processadas mais de uma vez. Por exemplo, se a lógica de repetição fizer com que um remetente envie exatamente a mesma mensagem mais de uma vez, você precisará verificar se ela é idempotente.

É possível projetar mensagens idempotentes. Por exemplo, você pode criar um evento que diz "definir o preço do produto como \$25" em vez de "adicionar \$5 ao preço do produto". A primeira mensagem pode ser processada com segurança qualquer número de vezes e o resultado será o mesmo. Isso não é válido para a segunda mensagem. Mas, mesmo no primeiro caso, talvez não seja interessante processar o primeiro evento, porque o sistema também pode ter enviado um evento de alteração de preço mais recente, e o novo preço seria substituído.

Outro exemplo poderia ser o de um evento de pedido concluído propagado para vários assinantes. É importante que as informações de pedidos sejam atualizadas em outros sistemas apenas uma vez, mesmo que haja eventos de mensagem duplicada para o mesmo evento pedido concluído.

É conveniente ter algum tipo de identidade por evento, para que você possa criar uma lógica que imponha que cada evento seja processado apenas uma vez em cada destinatário.

Alguns processamentos de mensagens são inerentemente idempotentes. Por exemplo, se um sistema gerar miniaturas de imagem, não importará quantas vezes a mensagem sobre a miniatura gerada vai ser processada; o resultado será que as miniaturas foram geradas e elas serão sempre as mesmas. Por outro lado, operações como chamar um gateway de pagamento para cobrar um cartão de crédito jamais poderão ser idempotentes. Nesses casos, você precisa garantir que o processamento de uma mensagem várias vezes tenha o efeito que você espera.

### <a name="additional-resources"></a>Recursos adicionais

-   **Respeitando a idempotência de mensagem** (subtítulo nesta página) [*https://msdn.microsoft.com/library/jj591565.aspx*](https://msdn.microsoft.com/library/jj591565.aspx)

## <a name="deduplicating-integration-event-messages"></a>Eliminando a duplicação de mensagens de eventos de integração

Você pode se certificar de que os eventos de mensagem sejam enviados e processados apenas uma vez por assinante em diferentes níveis. Uma maneira é usar um recurso de eliminação de duplicação oferecido pela infraestrutura do sistema de mensagens que você está usando. Outra é implementar uma lógica personalizada no microsserviço de destino. A melhor opção é ter validações no nível de transporte e no nível do aplicativo.

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a>Eliminando a duplicação de eventos de mensagem no nível do EventHandler

Uma maneira de se certificar que um evento será processado apenas uma vez por qualquer destinatário é implementar alguma lógica durante o processamento de eventos de mensagem em manipuladores de eventos. Por exemplo, essa é a abordagem usada no aplicativo eShopOnContainers, como você pode ver no [código-fonte](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Controllers/OrdersController.cs) da classe OrdersController, quando ela recebe um comando CreateOrderCommand. (Nesse caso, usamos um comando de solicitação HTTP, e não um comando baseado em mensagem, mas a lógica que você precisa para tornar um comando baseado em mensagem idempotente é semelhante).

### <a name="deduplicating-messages-when-using-rabbitmq"></a>Eliminando a duplicação de mensagens ao usar RabbitMQ

Quando ocorrem falhas intermitentes na rede, as mensagens podem ser duplicadas e o destinatário da mensagem deve estar preparado para lidar com essas mensagens duplicadas. Sempre que possível, os destinatários devem lidar com as mensagens de maneira idempotente, pois isso é melhor que tratá-las explicitamente com a eliminação de duplicação.

De acordo com a [documentação do RabbitMQ](https://www.rabbitmq.com/reliability.html#consumer), "Se uma mensagem for entregue a um consumidor e, em seguida, recolocada na fila (porque ela não foi reconhecida antes que a conexão do consumidor caísse, por exemplo), o RabbitMQ definirá o sinalizador redelivered na mensagem quando ela for entregue novamente (tanto para o mesmo consumidor quanto para um consumidor diferente).

Se o sinalizador "redelivered" for definido, o destinatário deverá considerar que a mensagem poderá já ter sido processada. Mas isso não é garantido; a mensagem pode nunca ter alcançado o destinatário depois de deixar o agente de mensagens, talvez por causa de problemas de rede. Por outro lado, se o sinalizador "redelivered" não estiver definido, será uma certeza de que a mensagem não foi enviada mais de uma vez. Portanto, o destinatário deverá eliminar a duplicação de mensagens ou processar mensagens de maneira idempotente somente se o sinalizador "redelivered" estiver definido na mensagem.

### <a name="additional-resources"></a>Recursos adicionais

-   **eShopOnContainers ramificado usando NServiceBus (software específico)**
    [*http://go.particular.net/eShopOnContainers*](http://go.particular.net/eShopOnContainers)

-   **Mensagens controladas por eventos**
    [*http://soapatterns.org/design\_patterns/event\_driven\_messaging*](http://soapatterns.org/design_patterns/event_driven_messaging)

-   **Jimmy Bogard. Refactoring Towards Resilience: Evaluating Coupling (Refatoração para resiliência: avaliando o acoplamento)**
    [*https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/*](https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/)

-   **Canal Publish-Subscribe**
    [*http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html*](http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html)

-   **Communicating Between Bounded Contexts (Comunicação entre contextos limitados)**
    [*https://msdn.microsoft.com/library/jj591572.aspx*](https://msdn.microsoft.com/library/jj591572.aspx)

-   **Eventual consistency (Consistência eventual)**
    [*https://en.wikipedia.org/wiki/Eventual\_consistency*](https://en.wikipedia.org/wiki/Eventual_consistency)

-   **Philip Brown. Strategies for Integrating Bounded Contexts (Estratégias para a integração de contextos delimitados)**
    [*http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/*](http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/)

-   **Chris Richardson. Developing Transactional Microservices Using Aggregates, Event Sourcing and CQRS – Part 2 (Desenvolvendo microsserviços transacionais usando agregações, Event Sourcing e CQRS – parte 2)**
    [*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson)

-   **Chris Richardson. Padrão Event Sourcing**
    [*http://microservices.io/patterns/data/event-sourcing.html*](http://microservices.io/patterns/data/event-sourcing.html)

-   **Introdução ao Event Sourcing**
    [*https://msdn.microsoft.com/library/jj591559.aspx*](https://msdn.microsoft.com/library/jj591559.aspx)

-   **Banco de dados Event Store**. Site oficial.
    [*https://geteventstore.com/*](https://geteventstore.com/)

-   **Patrick Nommensen. Event-Driven Data Management for Microservices (Gerenciamento de dados controlados por eventos para microsserviços)**
    *<https://dzone.com/articles/event-driven-data-management-for-microservices-1> *

-   **Teorema CAP**
    [*https://en.wikipedia.org/wiki/CAP\_theorem*](https://en.wikipedia.org/wiki/CAP_theorem)

-   **O que é o Teorema CAP? **
    [*https://www.quora.com/What-Is-CAP-Theorem-1*](https://www.quora.com/What-Is-CAP-Theorem-1)

-   **Data Consistency Primer (Manual de consistência de dados)**
    [*https://msdn.microsoft.com/library/dn589800.aspx*](https://msdn.microsoft.com/library/dn589800.aspx)

-   **Rick Saling. The CAP Theorem: Why “Everything is Different” with the Cloud and Internet (O Teorema CAP: por que "tudo é diferente" com a nuvem e a Internet)**
    [*https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/*](https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/)

-   **Eric Brewer. CAP Twelve Years Later: How the "Rules" Have Changed (O CAP 12 anos mais tarde: como as "regras" mudaram)**
    [*https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed*](https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed)

-   **Participating in External (DTC) Transactions** (MSMQ) (Participar de transações (MSMQ) externas (DTC))[*https://msdn.microsoft.com/library/ms978430.aspx\#bdadotnetasync2\_topic3c*](https://msdn.microsoft.com/library/ms978430.aspx%23bdadotnetasync2_topic3c)

-   **Barramento de Serviço do Azure. Sistema de mensagens agenciado: detecção de duplicatas**
    [*https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25*](https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25)

-   **Guia de confiabilidade** (documentação do RabbitMQ) [*https://www.rabbitmq.com/reliability.html\#consumer*](https://www.rabbitmq.com/reliability.html%23consumer)




>[!div class="step-by-step"]
[Anterior] (rabbitmq-event-bus-development-test-environment.md) [Próximo] (test-aspnet-core-services-web-apps.md)
