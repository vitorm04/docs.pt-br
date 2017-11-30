---
title: "Eventos de domínio. Design e implementação"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Eventos de domínio, design e implementação"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 2d98b302be4ee72d8225526944fc3e41cbadcb5f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="domain-events-design-and-implementation"></a>Eventos de domínio: design e implementação

Use eventos de domínio para implementar explicitamente os efeitos colaterais de alterações em seu domínio. Em outras palavras e usando terminologia DDD, use eventos de domínio para implementar explicitamente efeitos colaterais em várias agregações. Opcionalmente, para melhor desempenho e menos impacto em bloqueios de banco de dados, use consistência eventual entre agregações dentro do mesmo domínio.

## <a name="what-is-a-domain-event"></a>O que é um evento de domínio?

Um evento é algo que tenha ocorrido no passado. Um evento de domínio é, logicamente, algo que ocorreram em um domínio específico, e algo que você deseja que outras partes do mesmo domínio (em processo) para ficar atento e potencialmente reagir a.

Uma vantagem importante dos eventos de domínio é que os efeitos colaterais depois algo aconteceu em um domínio podem ser expressos explicitamente em vez de implicitamente. Esses efeitos devem ser consistentes para acontecem a todas as operações relacionadas à tarefa de negócios de lado, ou nenhum deles. Além disso, os eventos de domínio permitem uma melhor separação de preocupações entre classes dentro do mesmo domínio.

Por exemplo, se você estiver usando apenas apenas do Entity Framework e entidades ou até mesmo agregações, se deve haver efeitos colaterais provoked por um caso de uso, aqueles serão implementados como um conceito implícito no código acoplado depois algo aconteceu. No entanto, se você apenas vê esse código, você poderá não saber se esse código (o efeito colateral) é parte da operação de principal ou se ela é realmente um efeito colateral. Por outro lado, usando os eventos de domínio torna o conceito explícita e faz parte da linguagem onipresente. Por exemplo, no aplicativo eShopOnContainers, criar uma ordem não é praticamente a ordem; ela atualiza ou cria um comprador de agregação com base no usuário original, porque o usuário não é um comprador até que haja um pedido em vigor. Se você usar eventos de domínio, você pode expressar explicitamente essa regra de domínio com base no idioma onipresente fornecido pelos especialistas de domínio.

Eventos de domínio são um pouco semelhantes a eventos do estilo de mensagens, com uma diferença importante. Com a mensagem real, enfileiramento de mensagens, os agentes de mensagens ou um barramento de serviço usando AMPQ, uma mensagem é sempre enviada de forma assíncrona e comunicação entre processos e máquinas. Isso é útil para a integração de vários contextos limitada, microservices ou até mesmo diferentes aplicativos. No entanto, com os eventos de domínio, você deseja gerar um evento da operação de domínio em execução no momento, mas você deseja efeitos colaterais ocorrer dentro do mesmo domínio.

Os eventos de domínio e seus efeitos colaterais (as ações disparadas depois que são gerenciados pelo manipuladores de eventos) deve ocorrer quase imediatamente, geralmente em processo e dentro do mesmo domínio. Assim, os eventos de domínio podem ser síncronas ou assíncronas. Eventos de integração, no entanto, devem sempre ser assíncronos.

## <a name="domain-events-versus-integration-events"></a>Eventos de domínio em vez de eventos de integração

Semanticamente, eventos de integração e de domínio são a mesma coisa: notificações sobre algo que acabou. No entanto, sua implementação deve ser diferente. Eventos de domínio são apenas mensagens enviadas por push para um dispatcher de evento de domínio, que pode ser implementado como um mediador na memória com base em um contêiner IoC ou qualquer outro método.

Por outro lado, a finalidade de eventos de integração é a propagação de transações confirmadas e atualizações para outros subsistemas, independentemente de estarem outros microservices, contextos limitada ou aplicativos externos mesmo. Portanto, eles devem ocorrer somente se a entidade é persistente com êxito, pois em muitos cenários se isso falhar, toda a operação efetivamente nunca aconteceu.

Além disso e como mencionada, integração eventos devem ser baseados em comunicação assíncrona entre vários microservices (outros contextos limitada) ou aplicativos/sistemas externamente. Assim, a interface de barramento do evento precisa de alguma infraestrutura que permite que o processo entre e distribuídas comunicação entre serviços potencialmente remotos. Ele pode ser baseada em um barramento de serviço comercial, filas, um banco de dados compartilhado usado como uma caixa de correio ou qualquer outro distribuídas e push idealmente o sistema de mensagens de baseado em.

## <a name="domain-events-as-a-preferred-way-to-trigger-side-effects-across-multiple-aggregates-within-the-same-domain"></a>Eventos de domínio como uma maneira preferida para disparar efeitos colaterais em várias agregações dentro do mesmo domínio

Se executar um comando relacionado a uma instância de agregação requer regras de domínio adicionais para ser executado em uma ou mais agregações adicionais, deve criar e implementar os efeitos colaterais deve ser disparada por eventos de domínio. Conforme mostrado na Figura 9-14 e como um dos mais importantes casos de uso, um evento de domínio deve ser usado para propagar alterações de estado entre várias agregações dentro do mesmo modelo de domínio.

![](./media/image15.png)

**Figura 9-14**. Eventos de domínio para impor a consistência entre várias agregações dentro do mesmo domínio

Na figura, quando o usuário inicia uma ordem, o evento de domínio OrderStarted dispara a criação de um objeto de compradores de microsserviço ordenação, com base nas informações de usuário original de microsserviço a identidade (com as informações fornecidas no comando CreateOrder). O evento de domínio é gerado pela agregação ordem quando ele é criado em primeiro lugar.

Como alternativa, você pode ter raiz agregada assinada para eventos gerados pelos membros de suas agregações (entidades filho). Por exemplo, cada entidade de filho ItemPedido pode gerar um evento quando o preço de item é maior do que um valor específico, ou quando o valor do item de produto é muito alto. A raiz de agregação, em seguida, pode receber os eventos e executar um cálculo global ou agregação.

É importante entender que essa comunicação baseada em evento não é implementada diretamente dentro de agregações; Você precisa implementar manipuladores de eventos do domínio. Manipular eventos de domínio é um problema de aplicativo. A camada de modelo de domínio só deve se concentrar na lógica do domínio — que possa entender um especialista em domínio, não a infraestrutura de aplicativo como manipuladores e ações de persistência de efeito colateral usando repositórios. Portanto, o nível de camada de aplicativo é onde você deve ter manipuladores de eventos de domínio disparar ações quando ocorre um evento de domínio.

Eventos de domínio também podem ser usados para acionar qualquer número de ações do aplicativo e o que é mais importante, deve estar aberta para aumentar esse número no futuro de maneira separada. Por exemplo, quando a ordem é iniciada, você deseja publicar um evento de domínio para propagar essas informações para outras agregações ou até mesmo gerar ações do aplicativo como as notificações.

O ponto-chave é o número de open de ações a serem executadas quando ocorre um evento de domínio. Por fim, as ações e regras do domínio e o aplicativo aumentará. A complexidade ou o número de ações de efeito colateral quando acontecer algo crescerá, mas se o seu código foram juntamente com "colar" (ou seja, apenas instanciando objetos com a nova palavra-chave em C\#), e em seguida, sempre que necessário para adicionar uma nova ação seria necessário Altere o código original. Isso pode resultar em novos bugs, pois cada novo requisito, será necessário alterar o fluxo do código original. Isso vai contra o [abrir/fechado princípio](https://en.wikipedia.org/wiki/Open/closed_principle) de [sólido](https://en.wikipedia.org/wiki/SOLID_(object-oriented_design)). Não só que, a classe original que foi orquestrar as operações de crescimento e crescem, que vai contra o [princípio de responsabilidade única (SRP)](https://en.wikipedia.org/wiki/Single_responsibility_principle).

Por outro lado, se você usar eventos de domínio, você pode criar uma implementação refinada e desacoplada Segregando responsabilidades usando essa abordagem:

1.  Envie um comando (por exemplo, CreateOrder).
2.  Receba o comando em um manipulador de comando.
    -   Execute a transação de uma agregação único.
    -   (Opcional) Disparar eventos de domínio para efeitos colaterais (por exemplo, OrderStartedDomainDvent).
1.  Thast de eventos (dentro do processo atual) do identificador de domínio será executado um número aberto de efeitos colaterais em várias agregações ou ações do aplicativo. Por exemplo:
    -   Verificar ou criar um método de pagamento e compradores.
    -   Criar e enviar um evento relacionado a integração do barramento de evento seja propagado estados microservices ou gatilho ações externas como enviar um email para o comprador para.
    -   Lidar com outros efeitos colaterais.

Conforme mostrado na Figura 9-15, a partir do mesmo evento de domínio, você pode manipular várias ações relacionadas a outras agregações no domínio ou ações de aplicativos adicionais, que você precisa realizar em microservices conectar-se com o barramento de evento e eventos de integração.

![](./media/image16.png)

**Figura 9-15**. Manipulando várias ações por domínio

Os manipuladores de eventos são normalmente na camada de aplicativo, porque você usará os objetos de infra-estrutura como repositórios ou uma API de aplicativo para o comportamento do microsserviço. Nesse sentido, manipuladores de eventos são semelhantes aos manipuladores de comandos, portanto, ambos são parte da camada de aplicativo. A diferença importante é que um comando deve ser processado apenas uma vez. Um evento de domínio pode ser processada zero ou  *n*  vezes, porque se pode ser recebido por vários receptores ou manipuladores de eventos com uma finalidade diferente para cada manipulador.

A possibilidade de um número aberto de manipuladores por eventos de domínio permite que você adicionar várias regras de domínio mais sem afetar seu código atual. Por exemplo, implementar a seguinte regra de negócios que deve ocorrer direita após um evento pode ser tão fácil quanto adicionar alguns manipuladores de eventos (ou até mesmo uma):

Quando a quantidade total comprada por um cliente no armazenamento, em qualquer número de pedidos, excede r $6.000, aplicar um 10% de desconto desconto para cada nova ordem e notificar o cliente com um email sobre esse desconto para pedidos futuros.

## <a name="implementing-domain-events"></a>Implementar eventos de domínio

No c#, um evento de domínio é simplesmente uma retenção de dados de classe ou estrutura, como um DTO, com todas as informações relacionadas à ocorrência no domínio, conforme mostrado no exemplo a seguir:

```csharp
public class OrderStartedDomainEvent : IAsyncNotification
{
    public int CardTypeId { get; private set; }
    public string CardNumber { get; private set; }
    public string CardSecurityNumber { get; private set; }
    public string CardHolderName { get; private set; }
    public DateTime CardExpiration { get; private set; }
    public Order Order { get; private set; }

    public OrderStartedDomainEvent(Order order,
        int cardTypeId, string cardNumber,
        string cardSecurityNumber, string cardHolderName,
        DateTime cardExpiration)
    {
        Order = order;
        CardTypeId = cardTypeId;
        CardNumber = cardNumber;
        CardSecurityNumber = cardSecurityNumber;
        CardHolderName = cardHolderName;
        CardExpiration = cardExpiration;
    }
}
```

Isso é essencialmente uma classe que contém todos os dados relacionados ao evento OrderStarted.

Em termos de linguagem onipresente do domínio, como um evento é algo que ocorreram no passado, o nome da classe do evento deve ser representado como um verbo pretérito, como OrderStartedDomainEvent ou OrderShippedDomainEvent. Isso é como o evento de domínio é implementado no ordenação microsserviço em eShopOnContainers.

Como já observamos, uma característica importante de eventos é que uma vez que um evento é algo que ocorreram no passado, ele não deve ser alterada. Portanto, ele deve ser uma classe imutável. Você pode ver no código anterior, que as propriedades são somente leitura de fora do objeto. A única maneira de atualizar o objeto é por meio do construtor quando você cria o objeto de evento.

### <a name="raising-domain-events"></a>Gerando eventos de domínio

A próxima pergunta é como gerar um evento de domínio para alcançar seus manipuladores de eventos relacionados. Você pode usar várias abordagens.

Udi Dahan originalmente proposta (por exemplo, em vários relacionadas, como postagens, [eventos de domínio – demorar 2](http://udidahan.com/2008/08/25/domain-events-take-2/)) usando uma classe estática para gerenciar e gerando eventos. Isso pode incluir uma classe estática chamado DomainEvents que deve gerar eventos de domínio imediatamente quando ele é chamado, usando uma sintaxe semelhante DomainEvents.Raise (evento myEvent). Jimmy Bogard escreveu uma postagem de blog ([fortalecendo a seu domínio: eventos de domínio](https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/)) que recomenda uma abordagem semelhante.

No entanto, quando a classe de eventos de domínio é estática, ele também envia aos manipuladores imediatamente. Isso torna teste e depuração mais difícil, pois os manipuladores de eventos com a lógica de efeitos colaterais são executados imediatamente após o evento é gerado. Quando você está testando e depurando, deseja enfocam e apenas o que está acontecendo em classes de agregação atuais; Você não deseja repentinamente ser redirecionado para outros manipuladores de eventos para efeitos colaterais relacionados a outras agregações ou lógica do aplicativo. É por isso evoluíram outras abordagens, conforme explicado na próxima seção.

#### <a name="the-deferred-approach-for-raising-and-dispatching-events"></a>A abordagem adiada para gerar e envio de eventos

Em vez de expedição imediatamente para um manipulador de eventos de domínio, uma abordagem melhor é adicionar os eventos de domínio a uma coleção e, em seguida, os eventos de domínio de expedição *antes de* ou *direita*  *Depois de* confirmar a transação (como acontece com SaveChanges no EF). (Essa abordagem descrita por Jimmy Bogard nesta postagem [um padrão de eventos de domínio melhor](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/).)

Decidir se você enviar os eventos de domínio logo antes de ou para a direita após confirmar a transação é importante, pois ela determina se você incluirá os efeitos colaterais como parte da mesma transação ou em transações diferentes. No último caso, você precisa lidar com consistência eventual entre várias agregações. Este tópico é abordado na próxima seção.

A abordagem adiada é que eShopOnContainers usa. Primeiro, adicione os eventos que ocorrem nas suas entidades em uma coleção ou uma lista de eventos por entidade. Essa lista deve ser parte do objeto de entidade, ou melhor ainda, parte de sua classe de entidade base, conforme mostrado no exemplo a seguir:

```csharp
public abstract class Entity
{
    private List<IAsyncNotification> _domainEvents;

    public List<IAsyncNotification> DomainEvents => _domainEvents;

    public void AddDomainEvent(IAsyncNotification eventItem)
    {
        _domainEvents = _domainEvents ?? new List<IAsyncNotification>();
        _domainEvents.Add(eventItem);
    }

    public void RemoveDomainEvent(IAsyncNotification eventItem)
    {
        if (_domainEvents is null) return;
        _domainEvents.Remove(eventItem);
    }
    // ...
}
```

Quando você quiser gerar um evento, você apenas adicioná-lo à coleção de eventos sejam colocados dentro de um método de agregação de entidade, como mostra o seguinte código:

```csharp
var orderStartedDomainEvent = new OrderStartedDomainEvent(this, //Order object
    cardTypeId,
    cardNumber,
    cardSecurityNumber,
    cardHolderName,
    cardExpiration);
this.AddDomainEvent(orderStartedDomainEvent);
```

Observe que a única coisa que o método AddDomainEvent está fazendo é adicionar um evento à lista. Nenhum evento é gerado ainda, e nenhum manipulador de eventos é invocado ainda.

Você realmente deseja os eventos de expedição posterior no, quando você confirma a transação no banco de dados. Se você estiver usando o Entity Framework Core, que significa no método SaveChanges do seu EF DbContext, como no código a seguir:

```csharp
// EF Core DbContext
public class OrderingContext : DbContext, IUnitOfWork
{
    // ...
    public async Task<int> SaveEntitiesAsync()
    {
        // Dispatch Domain Events collection.
        // Choices:
        // A) Right BEFORE committing data (EF SaveChanges) into the DB. This makes
        // a single transaction including side effects from the domain event
        // handlers that are using the same DbContext with Scope lifetime
        // B) Right AFTER committing data (EF SaveChanges) into the DB. This makes
        // multiple transactions. You will need to handle eventual consistency and
        // compensatory actions in case of failures.
        await _mediator.DispatchDomainEventsAsync(this);
        // After this line runs, all the changes (from the Command Handler and Domain
        // event handlers) performed through the DbContext will be commited
        var result = await base.SaveChangesAsync();
    }
}
```

Com esse código, você enviar os eventos de entidade para seus manipuladores de eventos do respectivos.

O resultado geral é que você tenha desacoplado aumento de um evento de domínio (adição de um simples em uma lista na memória) de expedição-lo para um manipulador de eventos. Além disso, dependendo de qual tipo de dispatcher usando, você pôde expedir os eventos de forma síncrona ou assíncrona.

Lembre-se de que transacional limites entram em significativa brincar aqui. Se sua unidade de trabalho e a transação pode abranger mais de uma agregação (como ao usar o EF principal e um banco de dados relacional), isso pode funcionar bem. Mas se a transação não pode abranger agregações, como quando você estiver usando um banco de dados NoSQL como documentos do Azure, você precisa implementar etapas adicionais para obter consistência. Essa é outra razão por que não é universal; ignorância de persistência depende do sistema de armazenamento usado.

### <a name="single-transaction-across-aggregates-versus-eventual-consistency-across-aggregates"></a>Única transação em agregações versus consistência eventual em agregações

Se executar uma única transação em agregações em vez de depender de consistência eventual entre essas agregações é controverso. Muitos autores DDD como Eric Evans e Vaughn Vernon defendem a regra que uma transação = uma agregação e discutir, portanto, a consistência eventual em agregações. Por exemplo, em seu livro *Domain-Driven Design*, Eric Evans diz:

Qualquer regra que abrange as agregações não deverá ser atualizado em todos os momentos. Por meio do processamento de eventos, o processamento em lotes ou outros mecanismos de atualização, outras dependências podem ser resolvidas em um momento específico. (pg. 128)

Vaughn Vernon diz o seguinte no [efetivo de Design de agregação. Parte II: Fazer agrega trabalho juntos](http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf):

Portanto, se executar um comando em uma instância de agregação requer que as regras de negócio adicionais executar em uma ou mais agregações, use consistência eventual \[...\] Há uma maneira prática para dar suporte a consistência eventual em um modelo DDD. Um método de agregação publica um evento de domínio que está na hora entregue a um ou mais assinantes assíncronos.

Essa lógica é baseada nos adotando refinadas transações em vez de transações muitas agregações ou entidades. A ideia é que no segundo caso, o número de bloqueios de banco de dados será significativo em aplicativos em larga escala com necessidades de alta escalabilidade. Adotar o fato de que precisam de aplicativos escalonáveis de alto não tem instantânea consistência transacional entre várias agregações ajuda a aceitar o conceito de consistência eventual. Mudanças atômicas geralmente não são necessárias aos negócios, e em qualquer caso a responsabilidade de especialistas de domínio para dizer se operações específicas necessário transações atômicas ou não. Se uma operação sempre precisa de uma transação atômica entre várias agregações, você pode perguntar se a agregação deve ser maior ou não foi criada corretamente.

No entanto, outros desenvolvedores e arquitetos como Jimmy Bogard são okey com a abrangência de uma única transação em várias agregações, mas somente quando as agregações adicionais relacionadas a efeitos colaterais para o mesmo comando original. Por exemplo, em [um padrão de eventos de domínio melhor](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/), Bogard diz:

Normalmente, quero os efeitos colaterais de um evento de domínio para ocorrer dentro da mesma transação lógica, mas não necessariamente no mesmo escopo de disparar o evento de domínio \[...\] Antes de podemos confirmar nosso transação, podemos expedir nosso eventos para seus respectivos manipuladores.

Se você despachar o direito de eventos de domínio *antes de* confirmar a transação original, é porque você deseja que os efeitos colaterais dos eventos a serem incluídos na mesma transação. Por exemplo, se o método SaveChanges do EF DbContext falhar, a transação será reverter todas as alterações, incluindo o resultado de qualquer operação de efeito colateral implementado pelos manipuladores de eventos relacionados do domínio. Isso é porque o escopo de vida DbContext é por padrão definido como "com escopo." Portanto, o objeto DbContext é compartilhado entre vários objetos de repositório seja instanciados dentro do mesmo escopo ou um gráfico de objeto. Isso coincide com o escopo de HttpRequest ao desenvolver aplicativos de API da Web ou MVC.

Na realidade, ambas as abordagens (única transação atômica e consistência eventual) podem ser à direita. Isso realmente depende em seus requisitos de negócios ou de domínio e o que os especialistas de domínio lhe. Também depende de como escalonável necessário para o serviço (transações mais granulares tem menos impacto em relação a bloqueios do banco de dados). E depende de quanto investimento está disposto a fazer em seu código, pois consistência eventual requer código mais complexo para detectar possíveis inconsistências entre agregações e a necessidade de implementar compensatórios ações. Levar em conta se você confirmar as alterações para a agregação original e posteriormente, quando os eventos estão sendo despachados, há um problema e os manipuladores de eventos não é possível confirmar seus efeitos colaterais, você terá as inconsistências entre agregações.

Uma forma de permitir ações compensatórios seria armazenar os eventos de domínio nas tabelas de banco de dados adicionais para que eles possam ser parte da transação original. Posteriormente, você pode ter um processo em lote que detecta inconsistências e executa ações compensatórios comparando a lista de eventos com o estado atual das agregações. As ações compensatórios fazem parte de um tópico complexo que exige a análise detalhada do lado, o que inclui analisá-lo com o usuário empresarial e especialistas de domínio.

Em qualquer caso, você pode escolher a abordagem que você precisa. Mas inicial adiada abordagem — disparar os eventos antes de confirmar, para usar uma única transação – é a abordagem mais simples ao usar o EF principal e um banco de dados relacional. É mais fácil de implementar e válido em muitos casos de negócios. Também é a abordagem usada o ordenação microsserviço em eShopOnContainers.

Mas como você realmente expedição esses eventos para seus manipuladores de eventos do respectivos? O que é o \_objeto mediador que você vê no exemplo anterior? Que tem a ver com as técnicas e artefatos que você pode usar para mapear entre seus manipuladores de eventos e eventos.

### <a name="the-domain-event-dispatcher-mapping-from-events-to-event-handlers"></a>O dispatcher de evento de domínio: mapeamento de eventos para manipuladores de eventos

Depois que você é capaz de expedição ou publicar os eventos, você precisa de algum tipo de artefato que publicará o evento de forma que cada manipulador relacionado pode obtê-lo e efeitos colaterais de processo com base nesse evento.

Uma abordagem é um sistema de mensagens real ou até mesmo um barramento de evento, possivelmente com base em um barramento de serviço em vez de eventos na memória. No entanto, para o primeiro caso, real de mensagens pode ser um exagero para processar eventos de domínio, desde que você só precisa processar os eventos dentro do mesmo processo (ou seja, na mesma camada de aplicativo e de domínio).

É outra maneira de mapear os eventos para vários manipuladores de eventos usando o registro de tipos em um contêiner IoC para que você pode inferir dinamicamente onde os eventos de expedição. Em outras palavras, você precisa saber o que precisam de manipuladores de eventos para obter um evento específico. Figura 9 a 16 mostra um método simplificado para fazer isso.

![](./media/image17.png)

**Figura 9 a 16**. Dispatcher de evento de domínio usando IoC

Você pode criar todos os detalhes técnicos e artefatos para implementar essa abordagem, você mesmo. No entanto, você também pode usar as bibliotecas disponíveis como [MediatR](https://github.com/jbogard/MediatR), que nos bastidores usa o contêiner de IoT. Você, portanto, pode usar diretamente as interfaces predefinidas e métodos de expedição/publicar do objeto mediador.

No código, primeiro você precisa registrar os tipos de manipulador de eventos em seu contêiner IoC, conforme mostrado no exemplo a seguir:

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        // Other registrations ...
        // Register the DomainEventHandler classes (they implement
        // IAsyncNotificationHandler<>) in assembly holding the Domain Events
        builder.RegisterAssemblyTypes(
            typeof(ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler)
            .GetTypeInfo().Assembly)
            .Where(t => t.IsClosedTypeOf(typeof(IAsyncNotificationHandler<>)))
            .AsImplementedInterfaces();
        // Other registrations ...
    }
}
```

O código primeiro identifica o assembly que contém os manipuladores de eventos de domínio ao localizar o assembly que contém qualquer um dos manipuladores (usar typeof(ValidateOrAddBuyerAggregateWhenXxxx), mas você escolher qualquer outro manipulador de eventos para localizar o assembly). Como todos os manipuladores de eventos implementam a interface IAsyncNotificationHandler, em seguida, o código pesquisas apenas para os tipos e registra todos os manipuladores de eventos.

### <a name="how-to-subscribe-to-domain-events"></a>Como assinar eventos de domínio

Quando você usa MediatR, cada manipulador de eventos deve usar um tipo de evento que é fornecido no parâmetro genérico da interface IAsyncNotificationHandler, como você pode ver no código a seguir:

```csharp
public class ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler
  : IAsyncNotificationHandler<OrderStartedDomainEvent>
```

Com base na relação entre o evento e o manipulador de eventos, que pode ser considerado a assinatura, o artefato MediatR pode descobrir todos os manipuladores de eventos para cada evento e acionar cada um dos manipuladores de eventos.

### <a name="how-to-handle-domain-events"></a>Como manipular eventos de domínio

Por fim, o manipulador de eventos geralmente implementa o código de camada de aplicativo que usa os repositórios de infraestrutura para obter as agregações adicionais necessárias e executar a lógica do domínio de efeito colateral. O código a seguir mostra um exemplo.

```csharp
public class ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler
    : IAsyncNotificationHandler<OrderStartedDomainEvent>
{
    private readonly ILoggerFactory _logger;
    private readonly IBuyerRepository<Buyer> _buyerRepository;
    private readonly IIdentityService _identityService;
    public ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler(
        ILoggerFactory logger,
        IBuyerRepository<Buyer> buyerRepository,
        IIdentityService identityService)
    {
        // Parameter validations
        //...
    }

    public async Task Handle(OrderStartedDomainEvent orderStartedEvent)
    {
        var cardTypeId = (orderStartedEvent.CardTypeId != 0) ?
            orderStartedEvent.CardTypeId : 1;
        var userGuid = _identityService.GetUserIdentity();
        var buyer = await _buyerRepository.FindAsync(userGuid);
        bool buyerOriginallyExisted = (buyer == null) ? false : true;
        if (!buyerOriginallyExisted)
        {
            buyer = new Buyer(userGuid);
        }
        buyer.VerifyOrAddPaymentMethod(cardTypeId,
            $"Payment Method on {DateTime.UtcNow}",
            orderStartedEvent.CardNumber,
            orderStartedEvent.CardSecurityNumber,
            orderStartedEvent.CardHolderName,
            orderStartedEvent.CardExpiration,
            orderStartedEvent.Order.Id);
        var buyerUpdated = buyerOriginallyExisted ? _buyerRepository.Update(buyer) :
        _buyerRepository.Add(buyer);
        await _buyerRepository.UnitOfWork.SaveEntitiesAsync();
        // Logging code using buyerUpdated info, etc.
    }
}
```

Esse código de manipulador de eventos é considerado código da camada de aplicativo porque ele usa os repositórios de infraestrutura, como explicado na próxima seção sobre a camada de persistência de infraestrutura. Manipuladores de eventos também podem usar outros componentes de infraestrutura.

#### <a name="domain-events-can-generate-integration-events-to-be-published-outside-of-the-microservice-boundaries"></a>Eventos de domínio podem gerar eventos de integração a ser publicado fora dos limites de microsserviço

Por fim, é importante mencionar que, às vezes, convém propagado eventos microservices vários. Que é considerado um evento de integração e ele pode ser publicado por meio de um barramento de evento qualquer manipulador de eventos de domínio específico.

## <a name="conclusions-on-domain-events"></a>Conclusões sobre eventos de domínio 

Conforme mencionado, use eventos de domínio para implementar explicitamente os efeitos colaterais de alterações em seu domínio. Para usar a terminologia DDD, use eventos de domínio para implementar explicitamente efeitos colaterais em uma ou várias agregações. Além disso e para melhor desempenho e menos impacto nas bloqueios de banco de dados, use a consistência eventual entre agregações dentro do mesmo domínio.

#### <a name="additional-resources"></a>Recursos adicionais

-   **Greg Young. O que é um evento de domínio? ** 
     [ *http://codebetter.com/gregyoung/2010/04/11/what-is-a-domain-event/*](http://codebetter.com/gregyoung/2010/04/11/what-is-a-domain-event/)

-   **Jan Stenberg. Eventos de domínio e a consistência Eventual**
    [*https://www.infoq.com/news/2015/09/domain-events-consistency*](https://www.infoq.com/news/2015/09/domain-events-consistency)

-   **Jimmy Bogard. Um padrão de eventos de domínio melhor**
    [*https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/*](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/)

-   **Vaughn Vernon. Efetivo agregação Design parte II: Fazendo agregações trabalho juntos**
    [*http://dddcommunity.org/wp-content/uploads/files/pdf\_artigos/Vernon\_de2011\_ 2. pdf*](http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf)

-   **Jimmy Bogard. Reforçar a seu domínio: eventos de domínio**
    *<https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/>*

-   **Tony Truong. Exemplo de eventos de domínio padrão**
    [*http://www.tonytruong.net/domain-events-pattern-example/*](http://www.tonytruong.net/domain-events-pattern-example/)

-   **Udi Dahan. Como criar totalmente encapsulado modelos de domínio**
    [*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)

-   **Udi Dahan. Eventos de domínio – demorar 2**
    [*http://udidahan.com/2008/08/25/domain-events-take-2/*](http://udidahan.com/2008/08/25/domain-events-take-2/%20)

-   **Udi Dahan. Eventos de domínio – salvação**
    [*http://udidahan.com/2009/06/14/domain-events-salvation/*](http://udidahan.com/2009/06/14/domain-events-salvation/)

-   **Jan Kronquist. Não publicar eventos de domínio, retorne-as! ** 
     [ *https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/*](https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/)

-   **Cesar de la Torre. Domínio eventos vs. Eventos de integração em arquiteturas DDD e microservices**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/02/07/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/02/07/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/)


>[!div class="step-by-step"]
[Anterior] (cliente-lado-validation.md) [Avançar] (infraestrutura-persistência-camada-design.md)
