---
title: "Implementando a camada de aplicativo de microsserviço usando a API da Web"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Implementando a camada de aplicativo de microsserviço usando a API da Web"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: d505a2561ae9b8dee05e803fd639387b63b28b70
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-the-microservice-application-layer-using-the-web-api"></a>Implementando a camada de aplicativo de microsserviço usando a API da Web

## <a name="using-dependency-injection-to-inject-infrastructure-objects-into-your-application-layer"></a>Usando a injeção de dependência para injetar objetos de infraestrutura em sua camada de aplicativo

Conforme mencionado anteriormente, a camada de aplicativo pode ser implementada como parte do artefato que você está criando, tal como em um projeto de API da Web ou um projeto de aplicativo web MVC. No caso de um microsserviço criado com o ASP.NET Core, a camada de aplicativo geralmente será a sua biblioteca de API da Web. Se você quiser separar quais são as novidades do ASP.NET Core (sua infraestrutura e os controladores) do seu código da camada de aplicativo personalizado, você também pode colocar sua camada de aplicativo em uma biblioteca de classe separada, mas que é opcional.

Por exemplo, o código da camada de aplicativo de microsserviço a ordenação diretamente é implementado como parte do **Ordering.API** projeto (um projeto de API da Web do ASP.NET Core), como mostrado na Figura 9 19.

![](./media/image20.png)

**Figura 9-19**. A camada de aplicativo no projeto de API da Web do Ordering.API ASP.NET Core

ASP.NET Core inclui um simples [contêiner interno de IoC](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (representado pela interface IServiceProvider) que dá suporte a injeção de construtor por padrão, e ASP.NET disponibiliza por meio de DI determinados serviços. ASP.NET Core usa o termo *service* para qualquer um dos tipos que serão injetados pelo DI registrar. Configure os serviços do contêiner interno no método ConfigureServices na classe de inicialização do aplicativo. As dependências são implementadas nos serviços de que precisa de um tipo.

Normalmente, você deseja injetar dependências que implementam os objetos de infraestrutura. Uma dependência muito comum para injetar é um repositório. Mas você pode injetar qualquer outra dependência de infraestrutura que você pode ter. Para implementações mais simples, você poderia inserir diretamente o objeto de padrão de unidade de trabalho (o objeto EF DbContext), porque o DBContext também é a implementação de seus objetos de persistência de infraestrutura.

No exemplo a seguir, você pode ver como o .NET Core está injetando os objetos de repositório necessárias por meio do construtor. A classe é um manipulador de comando, o que abordaremos na próxima seção.

```csharp
// Sample command handler
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;

    // Constructor where Dependencies are injected
    public CreateOrderCommandHandler(IOrderRepository orderRepository)
    {
        if (orderRepository == null)
        {
            throw new ArgumentNullException(nameof(orderRepository));
        }
        _orderRepository = orderRepository;
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        //
        // ... Additional code
        //
        // Create the Order AggregateRoot
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic
        // make sure that consistency is preserved across the whole aggregate
        var address = new Address(message.Street, message.City, message.State,
            message.Country, message.ZipCode);
        var order = new Order(address, message.CardTypeId, message.CardNumber,
            message.CardSecurityNumber,
            message.CardHolderName,
            message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                item.Discount, item.PictureUrl, item.Units);
        }

        //Persist the Order through the Repository
        _orderRepository.Add(order);
        var result = await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
        return result > 0;
    }
}
```

A classe usa os repositórios injetados para executar a transação e manter as alterações de estado. Não importa se a classe é um manipulador de comandos, um método de controlador de API da Web do ASP.NET Core, ou uma [o serviço de aplicativo DDD](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/). Por fim, é uma classe simples que usa os repositórios, entidades de domínio e a coordenação de outros aplicativos de forma semelhante a um manipulador de comandos. Injeção de dependência funciona da mesma forma para todas as classes mencionadas, como no exemplo usando a injeção de dependência com base no construtor.

### <a name="registering-the-dependency-implementation-types-and-interfaces-or-abstractions"></a>Registrando tipos de implementação de dependência e interfaces ou abstrações

Antes de usar os objetos injetados por meio de construtores, você precisa saber onde se registrar as interfaces e classes que geram os objetos injetados suas classes de aplicativo por meio de injeção de dependência. (Como DI baseado no construtor, conforme mostrado anteriormente.)

#### <a name="using-the-built-in-ioc-container-provided-by-aspnet-core"></a>Usando o contêiner IoC interno fornecido pelo ASP.NET Core

Quando você usa o contêiner IoC interno fornecido pelo ASP.NET Core, você pode registrar os tipos que você deseja inserir no método ConfigureServices no arquivo Startup.cs, como no código a seguir:

```csharp
// Registration of types into ASP.NET Core built-in container
public void ConfigureServices(IServiceCollection services)
{
    // Register out-of-the-box framework services.
    services.AddDbContext<CatalogContext>(c =>
    {
        c.UseSqlServer(Configuration["ConnectionString"]);
    },
    ServiceLifetime.Scoped
    );
    services.AddMvc();
    // Register custom application dependencies.
    services.AddScoped<IMyCustomRepository, MyCustomSQLRepository>();
}
```

O padrão mais comum quando registrar tipos em um contêiner IoC é registrar um par de tipos — uma interface e sua classe de implementação relacionada. Em seguida, quando você solicitar um objeto de contêiner IoC por meio de nenhum construtor, você solicitar um objeto de um determinado tipo de interface. Por exemplo, no exemplo anterior, a última linha indica que, quando qualquer um dos seus construtores tem uma dependência no IMyCustomRepository (interface ou abstração), o contêiner IoC será injetar uma instância da implementação MyCustomSQLServerRepository classe.

#### <a name="using-the-scrutor-library-for-automatic-types-registration"></a>Usando a biblioteca de Scrutor para registro automático de tipos

Ao usar a DI no núcleo do .NET, você talvez queira ser capaz de verificar um assembly e registrar automaticamente seus tipos por convenção. Este recurso não está disponível atualmente no núcleo do ASP.NET. No entanto, você pode usar o [Scrutor](https://github.com/khellang/Scrutor) biblioteca para fazer isso. Essa abordagem é conveniente quando você tem dúzias de tipos que precisam ser registrados em seu contêiner IoC.

#### <a name="additional-resources"></a>Recursos adicionais

-   **Matthew rei. Registrando serviços Scrutor**
    [*https://mking.io/blog/registering-services-with-scrutor*](https://mking.io/blog/registering-services-with-scrutor)

<!-- -->

-   **Kristian Hellang. Scrutor.** Repositório do GitHub.
    [*https://GitHub.com/khellang/Scrutor*](https://github.com/khellang/Scrutor)

#### <a name="using-autofac-as-an-ioc-container"></a>Usando Autofac como um contêiner IoC

Você também pode usar contêineres de IoC adicionais e conectá-los no pipeline do ASP.NET Core, como o ordenação microsserviço em eShopOnContainers, que usa [Autofac](https://autofac.org/). Ao usar Autofac normalmente registrar tipos por meio de módulos, que permitem dividir os tipos de registro entre vários arquivos, dependendo de onde seus tipos são, exatamente como você pode ter os tipos de aplicativos distribuídos em várias bibliotecas de classe.

Por exemplo, o seguinte é o [módulo de aplicativo Autofac](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) para o [Ordering.API Web API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) projeto com os tipos que você pode inserir.

```csharp
public class ApplicationModule
    :Autofac.Module
{
    public string QueriesConnectionString { get; }
    public ApplicationModule(string qconstr)
    {
        QueriesConnectionString = qconstr;
    }

    protected override void Load(ContainerBuilder builder)
    {
        builder.Register(c => new OrderQueries(QueriesConnectionString))
            .As<IOrderQueries>()
            .InstancePerLifetimeScope();
        builder.RegisterType<BuyerRepository>()
            .As<IBuyerRepository>()
            .InstancePerLifetimeScope();
        builder.RegisterType<OrderRepository>()
            .As<IOrderRepository>()
            .InstancePerLifetimeScope();
        builder.RegisterType<RequestManager>()
            .As<IRequestManager>()
            .InstancePerLifetimeScope();
   }
}
```

O processo de registro e os conceitos são muito semelhantes à forma como você pode registrar tipos com o contêiner de iOS interno do ASP.NET Core, mas a sintaxe ao usar Autofac é um pouco diferente.

No código de exemplo, a abstração IOrderRepository é registrada junto com a classe de implementação OrderRepository. Isso significa que sempre que um construtor está declarando uma dependência por meio de abstração IOrderRepository ou interface, o contêiner IoC será injetar uma instância da classe OrderRepository.

O tipo de escopo de instância determina como uma instância é compartilhada entre as solicitações para o mesmo serviço ou dependência. Quando uma solicitação é feita em uma dependência, o contêiner IoC pode retornar o seguinte:

-   Uma única instância por escopo de tempo de vida (conhecido no contêiner do ASP.NET Core IoC como *escopo*).

-   Uma nova instância por dependência (conhecido no contêiner do ASP.NET Core IoC como *transitório*).

-   Uma única instância compartilhada entre todos os objetos usando o contêiner IoC (conhecido no contêiner do ASP.NET Core IoC como *singleton*).

#### <a name="additional-resources"></a>Recursos adicionais

-   **Introdução a injeção de dependência no núcleo do ASP.NET**
    [*https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection*](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)

-   **Autofac.** Documentação oficial.
    [*http://docs.autofac.org/en/Latest/*](http://docs.autofac.org/en/latest/)

-   **Cesar de la Torre. Comparando os tempos de vida do serviço de contêiner de ASP.NET Core IoC com escopos de instância de contêiner IoC Autofac**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/ Comparing-ASP-NET-Core-IoC-Service-Life-Times-and-autofac-IoC-Instance-Scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)

## <a name="implementing-the-command-and-command-handler-patterns"></a>Implementar os padrões de comando e o manipulador de comandos

No exemplo DI pelo construtor mostrado na seção anterior, o contêiner IoC foi injetando repositórios por meio de um construtor em uma classe. Mas exatamente onde foram eles injetado? Em uma API simples da Web (por exemplo, o catálogo de microsserviço em eShopOnContainers), colocá-los no nível de controladores MVC, em um construtor de controlador. No entanto, no código inicial desta seção (o [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) classe do serviço de Ordering.API no eShopOnContainers), a injeção de dependências é feita por meio do construtor de um comando específico manipulador. Vamos explicar o que um manipulador de comando é e por que você deseja usá-lo.

O padrão de comando intrinsecamente está relacionado ao padrão CQRS apresentada neste guia. CQRS tem dois lados. A primeira área é consultas, usando consultas simplificadas com o [Dapper](https://github.com/StackExchange/dapper-dot-net) micro ORM, o que foi explicado anteriormente. A segunda área é comandos, que são o ponto de partida para transações e o canal de entrada de fora do serviço.

Conforme mostrado na Figura 9-20, o padrão é baseado em aceitar comandos do lado do cliente, processá-las com base nas regras do modelo de domínio e, por fim, manter os estados com transações.

![](./media/image21.png)

**Figura 9-20**. Exibição de alto nível dos comandos ou "lado transacional" em um padrão CQRS

### <a name="the-command-class"></a>A classe de comando

Um comando é uma solicitação para o sistema executar uma ação que altera o estado do sistema. Comandos são obrigatório e devem ser processados apenas uma vez.

Como os comandos são obrigações, geralmente são nomeados com um verbo disposto obrigatório (por exemplo, "criar" ou "atualização") e elas podem incluir o tipo de agregação, como CreateOrderCommand. Ao contrário de um evento, um comando não é um fato do passado; ele é apenas uma solicitação e, portanto, pode ser recusado.

Comandos podem ser obtidos de interface do usuário como resultado de um usuário que inicia uma solicitação ou de um Gerenciador de processo quando o Gerenciador de processo é direcionar uma agregação para executar uma ação.

Uma característica importante de um comando é que ele deve ser processado apenas uma vez por um único destinatário. Isso ocorre porque um comando é uma ação única ou uma transação que você deseja executar no aplicativo. Por exemplo, o mesmo comando de criação de ordem não deve ser processado mais de uma vez. Isso é uma importante diferença entre os comandos e eventos. Eventos podem ser processados várias vezes, porque muitos sistemas ou microservices pode estar interessado no evento.

Além disso, é importante que um comando seja processada apenas uma vez caso o comando não é idempotente. Um comando é idempotente, se ele pode ser executado várias vezes sem alterar o resultado, devido à natureza do comando ou por causa da forma que o sistema manipula o comando.

Ele é uma boa prática fazer seus comandos e atualiza idempotente quando faz sentido em regras de negócios do seu domínio e invariáveis. Por exemplo, para usar o mesmo exemplo, se por algum motivo (lógica de repetição, hackers, etc.) o mesmo comando CreateOrder atingir seu sistema várias vezes, você deve ser capaz de identificá-lo e certifique-se de que você não crie vários pedidos. Para fazer isso, você precisa anexar algum tipo de identidade nas operações de e para identificar se o comando ou a atualização já foi processada.

Enviar um comando para um único destinatário; um comando não publicar. A publicação é para eventos de integração que o estado de um fato — que algo aconteceu e pode ser interessantes para receptores de evento. No caso de eventos, o publicador tem sem preocupações sobre quais destinatários obterem o evento ou o que eles fazem-lo. Mas os eventos de integração são outra história já introduzida nas seções anteriores.

Um comando é implementado com uma classe que contém campos de dados ou coleções com todas as informações necessárias para executar esse comando. Um comando é um tipo especial de dados transferidos objeto (DTO), que é usado especificamente para solicitar alterações ou transações. O próprio comando baseia-se exatamente as informações necessárias para processar o comando e nada mais.

O exemplo a seguir mostra a classe CreateOrderCommand simplificada. Este é um comando imutável que é usado no ordenação microsserviço em eShopOnContainers.

```csharp
// DDD and CQRS patterns comment
// Note that it is recommended that yuo implement immutable commands
// In this case, immutability is achieved by having all the setters as private
// plus being able to update the data just once, when creating the object
// through the constructor.
// References on immutable commands:
// http://cqrs.nu/Faq
// https://docs.spine3.org/motivation/immutability.html
// http://blog.gauffin.org/2012/06/griffin-container-introducing-command-support/
// https://msdn.microsoft.com/en-us/library/bb383979.aspx
[DataContract]
public class CreateOrderCommand
    :IAsyncRequest<bool>
{
    [DataMember]
    private readonly List<OrderItemDTO> _orderItems;

    [DataMember]
    public string City { get; private set; }

    [DataMember]
    public string Street { get; private set; }

    [DataMember]
    public string State { get; private set; }

    [DataMember]
    public string Country { get; private set; }

    [DataMember]
    public string ZipCode { get; private set; }

    [DataMember]
    public string CardNumber { get; private set; }

    [DataMember]
    public string CardHolderName { get; private set; }

    [DataMember]
    public DateTime CardExpiration { get; private set; }

    [DataMember]
    public string CardSecurityNumber { get; private set; }

    [DataMember]
    public int CardTypeId { get; private set; }

    [DataMember]
    public IEnumerable<OrderItemDTO> OrderItems => _orderItems;

    public CreateOrderCommand()
    {
        _orderItems = new List<OrderItemDTO>();
    }

    public CreateOrderCommand(List<OrderItemDTO> orderItems, string city,
        string street,
        string state, string country, string zipcode,
        string cardNumber, string cardHolderName, DateTime cardExpiration,
        string cardSecurityNumber, int cardTypeId) : this()
    {
        _orderItems = orderItems;
        City = city;
        Street = street;
        State = state;
        Country = country;
        ZipCode = zipcode;
        CardNumber = cardNumber;
        CardHolderName = cardHolderName;
        CardSecurityNumber = cardSecurityNumber;
        CardTypeId = cardTypeId;
        CardExpiration = cardExpiration;
    }

    public class OrderItemDTO
    {
        public int ProductId { get; set; }
        public string ProductName { get; set; }
        public decimal UnitPrice { get; set; }
        public decimal Discount { get; set; }
        public int Units { get; set; }
        public string PictureUrl { get; set; }
    }
}
```

Basicamente, a classe de comando contém todos os dados que você precisa para realizar uma transação comercial, usando os objetos de modelo de domínio. Assim, os comandos são simplesmente estruturas de dados que contêm dados somente leitura e nenhum comportamento. Nome do comando indica sua finalidade. Em vários idiomas, como C\#, comandos são representados como classes, mas eles não são true classes no sentido real orientada a objeto.

Como uma característica adicional, comandos são imutáveis, porque o uso esperado é que eles são processados diretamente pelo modelo de domínio. Eles não precisam alterar durante seu ciclo de vida projetado. Em um C\# classe imutabilidade pode ser obtida por não haver qualquer setters ou outros métodos que alteram o estado interno.

Por exemplo, a classe de comando para a criação de um pedido é provavelmente semelhante em termos de dados na ordem em que você deseja criar, mas você não tenha os mesmos atributos. Por exemplo, CreateOrderCommand não tem uma ID de ordem, porque a ordem ainda não foi criada.

Muitas classes de comando podem ser simples, exigindo somente alguns campos sobre algum estado que precisa ser alterado. Isso seria o caso se você estiver alterando apenas o status de um pedido de "processo" para "pago" ou "enviados" usando um comando semelhante ao seguinte:

```csharp
[DataContract]
public class UpdateOrderStatusCommand
    :IAsyncRequest<bool>
{
    [DataMember]
    public string Status { get; private set; }

    [DataMember]
    public string OrderId { get; private set; }

    [DataMember]
    public string BuyerIdentityGuid { get; private set; }
}
```

Alguns desenvolvedores fazem seus objetos de interface do usuário de solicitação separados de DTOs seu comando, mas que é apenas uma questão de preferência. É uma separação entediante não muito valor agregado, e os objetos são quase exatamente da mesma forma. Por exemplo, no eShopOnContainers, os comandos vêm diretamente do lado do cliente.

### <a name="the-command-handler-class"></a>A classe do manipulador de comando

Você deve implementar uma classe de manipulador de comando específicas para cada comando. Isso é como funciona o padrão e é onde você usará o objeto de comando, os objetos de domínio e os objetos de repositório de infraestrutura. O manipulador de comandos na verdade é a essência da camada de aplicativo em termos de CQRS e DDD. No entanto, toda a lógica do domínio deve estar contida em classes de domínio — as raízes de agregação (entidades raiz), dentro de entidades filho, ou [dos serviços de domínio](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), mas não dentro do manipulador de comando, que é uma classe do aplicativo camada.

Um manipulador de comandos recebe um comando e obtém um resultado de agregação que é usada. O resultado deve ser a execução bem-sucedida do comando ou uma exceção. No caso de uma exceção, o estado do sistema deve ser inalterado.

O manipulador de comandos geralmente executa as seguintes etapas:

-   Ele recebe o objeto de comando, como um DTO (da [mediador](https://en.wikipedia.org/wiki/Mediator_pattern) ou outro objeto de infraestrutura).

-   Ele valida que o comando é válido (se não validado pelo mediador).

-   Ele cria a instância de raiz de agregação que é o destino do comando atual.

-   Ele executa o método na instância de raiz de agregação, obtendo os dados necessários do comando.

-   Persistir o estado novo da agregação para seu banco de dados relacionado. Esta última operação é a transação atual.

Normalmente, um manipulador de comandos lida com uma única agregação orientada por sua raiz de agregação (entidade de raiz). Se várias agregações devem ser afetadas pela recepção de um único comando, você pode usar eventos de domínio para propagar estados ou ações em várias agregações

O ponto importante aqui é que, quando um comando está sendo processado, toda a lógica do domínio deve estar dentro do modelo de domínio (agregações), totalmente encapsulado e está pronto para teste de unidade. O manipulador de comando apenas atua como uma maneira de obter o modelo de domínio do banco de dados e a etapa final, para informar a camada de infraestrutura (repositórios) para manter as alterações quando o modelo é alterado. A vantagem dessa abordagem é que você pode refatorar a lógica do domínio em um modelo de domínio isolado, totalmente encapsulado, ricos e comportamentais sem alterar o código do aplicativo ou as camadas de infraestrutura, que são o nível de detalhes técnicos (manipuladores de comandos, API da Web, repositórios, etc.).

Quando manipuladores de comandos complexos, com muita lógica, que pode ser um cheiro de código. Examiná-los e, se você encontrar a lógica do domínio, refatorar o código para mover esse comportamento de domínio para os métodos dos objetos de domínio (agregação raiz e filho entidade).

Como um exemplo de uma classe de manipulador de comando, o código a seguir mostra a mesma classe CreateOrderCommandHandler que você viu no início deste capítulo. Nesse caso destacamos o identificador de método e as operações com o domínio objetos modelo agrega.

```csharp
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IBuyerRepository _buyerRepository;
    private readonly IOrderRepository _orderRepository;

    public CreateOrderCommandHandler(IBuyerRepository buyerRepository,
        IOrderRepository orderRepository)
    {
        if (buyerRepository == null)
        {
            throw new ArgumentNullException(nameof(buyerRepository));
        }
        if (orderRepository == null)
        {
            throw new ArgumentNullException(nameof(orderRepository));
        }

        _buyerRepository = buyerRepository;
        _orderRepository = orderRepository;
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        //
        // Additional code ...
        //
        // Create the Order aggregate root
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic
        // make sure that consistency is preserved across the whole aggregate
        var order = new Order(buyer.Id, payment.Id,
            new Address(message.Street,
            message.City, message.State,
            message.Country, message.ZipCode));

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                item.Discount, item.PictureUrl, item.Units);
        }

        // Persist the Order through the aggregate's repository
        _orderRepository.Add(order);
        return await _orderRepository.UnitOfWork.SaveChangesAsync();
    }
}
```

Estas são as etapas adicionais que deve ser seguidas por um manipulador de comandos:

-   Use dados do comando para operar com métodos e o comportamento da raiz de agregação.

-   Internamente dentro dos objetos de domínio, gere eventos de domínio enquanto a transação é executada, mas isso é transparente de um ponto de vista do comando manipulador.

-   Se o resultado da operação de agregação for bem-sucedida, e depois que a transação for concluída, aumente o manipulador de comando de eventos de integração. (Eles podem também ser gerados por classes de infraestrutura como repositórios.)

#### <a name="additional-resources"></a>Recursos adicionais

-   **Mark Seemann. Em limites, os aplicativos são orientados a objeto não**
    [*http://blog.ploeh.dk/2011/05/31/AttheBoundaries, orientado a ApplicationsareNotObject /*](http://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/)

-   **Comandos e eventos**
    [*http://cqrs.nu/Faq/commands-and-events*](http://cqrs.nu/Faq/commands-and-events)

-   **O que faz um manipulador de comando? ** 
     [ *http://cqrs.nu/Faq/command-handlers*](http://cqrs.nu/Faq/command-handlers)

-   **Jimmy Bogard. Padrões de comando do domínio – manipuladores**
    [*https://jimmybogard.com/domain-command-patterns-handlers/*](https://jimmybogard.com/domain-command-patterns-handlers/)

-   **Jimmy Bogard. Padrões de comando do domínio – validação**
    [*https://jimmybogard.com/domain-command-patterns-validation/*](https://jimmybogard.com/domain-command-patterns-validation/)

## <a name="the-command-process-pipeline-how-to-trigger-a-command-handler"></a>O pipeline de processo do comando: como acionar um manipulador de comandos

A próxima pergunta é como chamar um manipulador de comandos. Manualmente, você pode chamá-lo em cada controlador do ASP.NET Core relacionado. No entanto, o que abordagem seria muito acoplados e não é ideal.

As outras duas opções principais, que são as opções recomendadas, são:

-   Por meio de um artefato de padrão de mediador na memória.

-   Com uma fila de mensagens assíncronas, entre os controladores e manipuladores.

### <a name="using-the-mediator-pattern-in-memory-in-the-command-pipeline"></a>Usando o padrão de mediador (na memória) no pipeline de comando

Conforme mostrado na Figura 9-21, uma abordagem CQRS você usa um mediador inteligente, semelhante a um barramento de memória, que é inteligente para redirecionar para o manipulador de comando correta com base no tipo de comando ou DTO sendo recebidas. As setas pretas único entre componentes representam as dependências entre objetos (em muitos casos, inseridos por meio de DI) com suas interações relacionadas.

![](./media/image22.png)

**Figura 9-21**. Usando o padrão de mediador no processo em um único microsserviço CQRS

O motivo pelo qual usando o padrão de mediador faz sentido é se em aplicativos da empresa, as solicitações de processamento podem ficar complicadas. Você deseja adicionar um número aberto de resolvem preocupações com segurança, validações, auditoria e registro em log. Nesses casos, você pode confiar em um pipeline mediador (consulte [padrão mediador](https://en.wikipedia.org/wiki/Mediator_pattern)) para fornecer um meio para esses comportamentos extras ou resolvem preocupações.

Um mediador é um objeto que encapsula o "como" desse processo: coordena com base no estado de execução, a maneira como um manipulador de comandos é chamado ou a carga que você fornecer para o manipulador. Com um componente mediador você pode aplicar resolvem preocupações de forma centralizada e transparente aplicando decoradores (ou [pipeline comportamentos](https://github.com/jbogard/MediatR/wiki/Behaviors) desde mediador v3). (Para obter mais informações, consulte o [padrão de decorador](https://en.wikipedia.org/wiki/Decorator_pattern).)

Os decoradores e comportamentos são semelhantes às [programação orientada a aspecto (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming)somente aplicado a um pipeline de processo específico gerenciado pelo componente mediador. Aspectos AOP que implementam resolvem preocupações são aplicados com base em *weavers aspecto* injetado em tempo de compilação ou com base em interceptação de chamada de objeto. Ambas as abordagens AOP típicas, às vezes, são chamadas para funcionar "como"mágica, porque ele não é fácil ver como AOP faz seu trabalho. Ao lidar com problemas sérios ou bugs, AOP pode ser difícil de depurar. Por outro lado, esses decoradores/comportamentos são explícita e aplicadas apenas no contexto do mediador, modo de depuração é muito mais fácil e previsível.

Por exemplo, no eShopOnContainers ordenação microsserviço, implementamos dois decoradores de exemplo, um [LogDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/LogDecorator.cs) classe e um [ValidatorDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/ValidatorDecorator.cs) classe. Implementação do decorador é explicada na próxima seção. Observe que, em uma versão futura, eShopOnContainers migrará para [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) e mover para [comportamentos](https://github.com/jbogard/MediatR/wiki/Behaviors) em vez de usar os decoradores.

### <a name="using-message-queues-out-of-proc-in-the-commands-pipeline"></a>Usando filas de mensagens (fora de processo) no pipeline do comando

Outra opção é usar mensagens assíncronas com base em agentes ou filas de mensagens, conforme mostrado na Figura 9-22. Essa opção também pode ser combinada com o componente mediador antes do manipulador de comandos.

![](./media/image23.png)

**Figura 9-22**. Usando filas de mensagens (fora de processo e de comunicação entre processos) com comandos CQRS

Usar mensagens de filas para aceitar que os comandos podem mais complicam o pipeline do comando, porque você provavelmente precisará dividir o pipeline em dois processos conectados por meio da fila de mensagens externas. Ainda assim, ele deve ser usado se você precisa ter melhor escalabilidade e desempenho com base no sistema de mensagens assíncronas. Considere a possibilidade de que no caso de Figura 9-22, o controlador apenas envia a mensagem de comando na fila e retorna. Em seguida, o manipulador de comandos processa as mensagens em seu próprio ritmo. Isto é um grande benefício de filas — a fila de mensagens pode agir como um buffer em casos quando hyper escalabilidade é necessária, como para qualquer cenário com um alto volume de dados de entrada ou de ações.

No entanto, devido à natureza assíncrona de filas de mensagens, você precisa descobrir como se comunicar com o aplicativo cliente sobre o êxito ou falha do processo do comando. Como regra, você nunca deve usar comandos de "disparar e esquecer". Todos os aplicativos de negócios precisa saber se um comando foi processado com êxito, ou pelo menos validado e aceitos.

Portanto, ser capaz de responder ao cliente após a validação de uma mensagem de comando que foi enviada para uma fila assíncrona adiciona complexidade ao seu sistema, em comparação com um processo no processo de comando que retorna o resultado da operação depois de executar a transação. Uso de filas, talvez seja necessário retornar o resultado do processo de comando por meio de outras mensagens de resultado da operação, que exigirá a comunicação personalizada e componentes adicionais no seu sistema.

Além disso, async comandos são unidirecionais, que, em muitos casos, pode não ser necessário, como explicado no seguinte troca interessante entre Burtsev Alexey e Greg Young em um [conversa on-line](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):

\[Burtsev Alexey\] localizar muitos códigos de onde as pessoas usam o tratamento de comando assíncrono ou comando unidirecional de mensagens sem nenhuma razão para isso (eles não estão fazendo alguma operação longa, eles não estão executando o código de async externo, que não ultrapassem mesmo aplicativo limite usando o barramento de mensagem). Por que introduzem essa complexidade desnecessária? E, na verdade, não tiver visto um exemplo de código CQRS com bloqueio de manipuladores de comando até o momento, embora ele funcionará bem na maioria dos casos.

\[Greg Young\] \[... \] um comando assíncrono não existe; ela é realmente outro evento. Se deve aceitar o que você envie-me e gerar um evento se eu não concordo, ele não está mais você informando a fazer algo. É você informando que algo foi feito. Isso parece uma pequena diferença inicialmente, mas ele tem várias implicações.

Comandos assíncronos aumentam significativamente a complexidade de um sistema, porque não há nenhuma maneira simple de indicam falhas. Portanto, comandos assíncronos não são recomendados diferente de quando os requisitos de dimensionamento são necessários ou, em casos especiais ao comunicar-se a microservices interna por meio de mensagens. Nesses casos, você deve criar um sistema de emissão de relatórios e recuperação separado para falhas.

Na versão inicial do eShopOnContainers, decidimos usar processamento de comando síncrono, iniciado a partir de solicitações HTTP e orientadas por padrão o mediador. Que permite retornar o êxito ou falha do processo, como em facilmente o [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) implementação.

Em qualquer caso, isso deve ser uma decisão com base nos requisitos de negócios do aplicativo ou do microsserviço.

## <a name="implementing-the-command-process-pipeline-with-a-mediator-pattern-mediatr"></a>Implementando o pipeline de comando de processo com um padrão de mediador (MediatR)

Como um exemplo de implementação, este guia propõe usando o pipeline em processo baseado no padrão de mediador para inclusão de comando de unidade e roteamento, na memória, os manipuladores de comando correta. O guia também propõe aplicando decoradores ou [comportamentos](https://github.com/jbogard/MediatR/wiki/Behaviors) para separar resolvem preocupações.

Para a implementação no núcleo do .NET, há várias bibliotecas de código-fonte disponíveis que implementam o padrão de mediador. A biblioteca usada neste guia é o [MediatR](https://github.com/jbogard/MediatR) biblioteca de código-fonte aberto (criado pelo Jimmy Bogard), mas você pode usar outra abordagem. MediatR é uma biblioteca de pequena e simple que permite que você processe mensagens na memória como um comando, aplicando decoradores ou comportamentos.

Usando o padrão de mediador ajuda a reduzir o acoplamento e isolar as preocupações do trabalho solicitado, ao conectar-se automaticamente para o manipulador que executa esse trabalho — nesse caso, para manipuladores de comando.

Outra boa razão para usar o padrão de mediador foi explicada por Jimmy Bogard ao revisar este guia:

Acho que pode ser vale a pena mencionar teste aqui – fornece uma janela consistente adequada para o comportamento do seu sistema. Na solicitação, em resposta. Descobrimos que aspecto bastante valioso no prédio consistentemente se comportando testes.

Primeiro, vamos dar uma olhada no código do controlador quando você realmente usa o objeto mediador. Se você não estava usando o objeto mediador, você precisa inserir todas as dependências para esse controlador, como um objeto do agente de log e outras pessoas. Portanto, o construtor seria muito complicado. Por outro lado, se você usar o objeto mediador, o construtor do controlador pode ser muito mais simples, com apenas algumas dependências em vez de muitas dependências que seria necessário se você tivesse um por operação abrangentes, como no exemplo a seguir:

```csharp
public class OrdersController : Controller
{
    public OrdersController(IMediator mediator,
        IOrderQueries orderQueries)
    // ...
```

Você pode ver o mediador fornece um construtor de controlador Web API lean e limpo. Além disso, dentro do método do controlador, o código para enviar um comando para o objeto mediador é quase uma linha:

```csharp
[Route("new")]
[HttpPost]
public async Task<IActionResult> CreateOrder([FromBody]CreateOrderCommand
    createOrderCommand)
{
    var commandResult = await _mediator.SendAsync(createOrderCommand);
    return commandResult ? (IActionResult)Ok() : (IActionResult)BadRequest();
}
```

Para MediatR estar ciente das suas classes de manipulador de comando, é necessário registrar as classes de mediador e as classes de manipulador de comando em seu contêiner IoC. Por padrão, MediatR usa Autofac como o contêiner IoC, mas você também pode usar o contêiner do ASP.NET Core IoC interno ou qualquer outro contêiner MediatR com suporte.

O código a seguir mostra como registrar comandos e tipos do mediador ao usar módulos de Autofac.

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        builder.RegisterAssemblyTypes(typeof(IMediator).GetTypeInfo().Assembly)
            .AsImplementedInterfaces();
        builder.RegisterAssemblyTypes(typeof(CreateOrderCommand)
            .GetTypeInfo().Assembly)
            .As(o => o.GetInterfaces()
            .Where(i => i.IsClosedTypeOf(typeof(IAsyncRequestHandler<,>)))
            .Select(i => new KeyedService("IAsyncRequestHandler", i)));
        builder.RegisterGenericDecorator(typeof(LogDecorator<,>),
            typeof(IAsyncRequestHandler<,>), "IAsyncRequestHandler");

        // Other types registration
    }
}
```

Como cada manipulador de comando implementa a interface com genérico IAsyncRequestHandler&lt;T&gt; e, em seguida, inspeciona o RegisteredAssemblyTypes do objeto, o manipulador é capaz de relacionar cada comando com seu manipulador de comando, porque que relação é declarada na classe CommandHandler, como no exemplo a seguir:

```csharp
public class CreateOrderCommandHandler
  : IAsyncRequestHandler<CreateOrderCommand, bool>
{
```

Este é o código que se correlaciona comandos com manipuladores de comandos. O manipulador é apenas uma classe simples, mas ele herda de RequestHandler&lt;T&gt;, e MediatR torna-se de que ele será invocado com a carga correta.

## <a name="applying-cross-cutting-concerns-when-processing-commands-with-the-mediator-and-decorator-patterns"></a>Aplicando resolvem preocupações durante o processamento de comandos com os padrões mediador e decorador

Há algo mais: conseguir aplicar resolvem preocupações pipeline mediador. Você também pode ver no final do código do módulo de registro Autofac como ele está registrando um decorador de tipo, especificamente, uma classe LogDecorator personalizada.

Novamente, observe que uma versão futura do eShopOnContainers ele migrará para [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) e mover para [comportamentos](https://github.com/jbogard/MediatR/wiki/Behaviors) em vez de usar os decoradores.

Que [LogDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/LogDecorator.cs) classe pode ser implementada como o código a seguir, que registra informações sobre o manipulador de comando que está sendo executado e se ela foi bem-sucedida ou não.

```csharp
public class LogDecorator<TRequest, TResponse>
    : IAsyncRequestHandler<TRequest, TResponse>
    where TRequest : IAsyncRequest<TResponse>
{
    private readonly IAsyncRequestHandler<TRequest, TResponse> _inner;
    private readonly ILogger<LogDecorator<TRequest, TResponse>> _logger;

    public LogDecorator(
        IAsyncRequestHandler<TRequest, TResponse> inner,
        ILogger<LogDecorator<TRequest, TResponse>> logger)
    {
        _inner = inner;
        _logger = logger;
    }

    public async Task<TResponse> Handle(TRequest message)
    {
        _logger.LogInformation($"Executing command {_inner.GetType().FullName}");
        var response = await _inner.Handle(message);
        _logger.LogInformation($"Succeeded executed command{_inner.GetType().FullName}");
        return response;
    }
}
```

Basta implementar essa classe decorador e decorando pipeline com ele, todos os comandos processados por meio de MediatR fizerem logon informações sobre a execução.

O eShopOnContainers ordenação microsserviço também se aplica a um segundo decorador para validações básicas, o [ValidatorDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/ValidatorDecorator.cs) classe depende do [FluentValidation](https://github.com/JeremySkinner/FluentValidation) biblioteca, conforme mostrado no código a seguir:

```csharp
public class ValidatorDecorator<TRequest, TResponse>
    : IAsyncRequestHandler<TRequest, TResponse>
    where TRequest : IAsyncRequest<TResponse>
{
    private readonly IAsyncRequestHandler<TRequest, TResponse> _inner;
    private readonly IValidator<TRequest>[] _validators;

    public ValidatorDecorator(
        IAsyncRequestHandler<TRequest, TResponse> inner,
        IValidator<TRequest>[] validators)
    {
        _inner = inner;
        _validators = validators;
    }

    public async Task<TResponse> Handle(TRequest message)
    {
        var failures = _validators
            .Select(v => v.Validate(message))
            .SelectMany(result => result.Errors)
            .Where(error => error != null)
            .ToList();
            if (failures.Any())
            {
                throw new OrderingDomainException(
                $"Command Validation Errors for type {typeof(TRequest).Name}",
                new ValidationException("Validation exception", failures));
            }
            var response = await _inner.Handle(message);
        return response;
    }
}
```

Em seguida, com base no [FluentValidation](https://github.com/JeremySkinner/FluentValidation) biblioteca, criamos a validação para os dados passados com CreateOrderCommand, como no código a seguir:

```csharp
public class CreateOrderCommandValidator : AbstractValidator<CreateOrderCommand>
{
    public CreateOrderCommandValidator()
    {
        RuleFor(command => command.City).NotEmpty();
        RuleFor(command => command.Street).NotEmpty();
        RuleFor(command => command.State).NotEmpty();
        RuleFor(command => command.Country).NotEmpty();
        RuleFor(command => command.ZipCode).NotEmpty();
        RuleFor(command => command.CardNumber).NotEmpty().Length(12, 19);
        RuleFor(command => command.CardHolderName).NotEmpty();
        RuleFor(command => command.CardExpiration).NotEmpty().Must(BeValidExpirationDate).
            WithMessage("Please specify a valid card expiration date");
        RuleFor(command => command.CardSecurityNumber).NotEmpty().Length(3);
        RuleFor(command => command.CardTypeId).NotEmpty();
        RuleFor(command => command.OrderItems).
            Must(ContainOrderItems).WithMessage("No order items found");
    }

    private bool BeValidExpirationDate(DateTime dateTime)
    {
        return dateTime >= DateTime.UtcNow;
    }

    private bool ContainOrderItems(IEnumerable<OrderItemDTO> orderItems)
    {
        return orderItems.Any();
    }
}
```

Você pode criar validações adicionais. Isso é uma maneira muito claro e elegante para implementar seu validações de comando.

De maneira semelhante, você pode implementar outros decoradores para aspectos adicionais ou resolvem preocupações que você deseja aplicar aos comandos ao lidar com eles.

#### <a name="additional-resources"></a>Recursos adicionais

##### <a name="the-mediator-pattern"></a>O padrão de mediador

-   **Padrão de mediador**
    [*https://en.wikipedia.org/wiki/Mediator\_padrão*](https://en.wikipedia.org/wiki/Mediator_pattern)

##### <a name="the-decorator-pattern"></a>O padrão de decorador

-   **Padrão de decorador**
    [*https://en.wikipedia.org/wiki/Decorator\_padrão*](https://en.wikipedia.org/wiki/Decorator_pattern)

##### <a name="mediatr-jimmy-bogard"></a>MediatR (Jimmy Bogard)

-   **MediatR.** Repositório do GitHub.
    [*https://GitHub.com/jbogard/MediatR*](https://github.com/jbogard/MediatR)

-   **CQRS com MediatR e AutoMapper**
    [*https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/*](https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/)

-   **Coloque os controladores em uma dieta: postagens e comandos. ** 
     [ *https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/*](https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/)

-   **Lidar com resolvem preocupações com um pipeline mediador**
    [*https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/*](https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/)

-   **CQRS e REST: a correspondência perfeita**
    [*https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/*](https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/)

-   **Exemplos de Pipeline de MediatR**
    [*https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/*](https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/)

-   **Acessórios de teste de fatia vertical para MediatR e ASP.NET Core**
    *<https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/>*

-   **Extensões MediatR Microsoft para injeção de dependência liberado**
    [*https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/*](https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/)

##### <a name="fluent-validation"></a>Validação fluente

-   **Jeremy Skinner. FluentValidation.** Repositório do GitHub.
    [*https://GitHub.com/JeremySkinner/FluentValidation*](https://github.com/JeremySkinner/FluentValidation)

>[!div class="step-by-step"]
[Anterior] (microservice-application-layer-web-api-design.md) [Avançar] (... /Implement-resilient-Applications/Index.MD)
