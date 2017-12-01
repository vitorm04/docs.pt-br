---
title: "Implementando a camada de persistência de infraestrutura com o Entity Framework Core"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Implementando a camada de persistência de infraestrutura com o Entity Framework Core"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 508d60d73eb7c0f0cc2cc909613cc4f8712b4aba
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-the-infrastructure-persistence-layer-with-entity-framework-core"></a>Implementando a camada de persistência de infraestrutura com o Entity Framework Core

Quando você usa os bancos de dados relacionais, como o SQL Server, Oracle ou PostgreSQL, uma abordagem recomendada é implementar a camada de persistência com base no Entity Framework (EF). EF dá suporte a LINQ e fornece objetos fortemente tipados para seu modelo, bem como persistência simplificada em seu banco de dados.

Entity Framework tem uma longa história como parte do .NET Framework. Quando você usa o .NET Core, você também deve usar o Entity Framework Core, que é executado no Windows ou Linux da mesma maneira como o .NET Core. EF Core é uma regravação completa do Entity Framework, implementado com muito menos espaço e importantes melhorias no desempenho.

## <a name="introduction-to-entity-framework-core"></a>Introdução ao Entity Framework Core

Núcleo do Entity Framework (EF) é leve e extensível, e tecnologia de acesso de versão de plataforma cruzada dos dados do Entity Framework populares. Ele foi introduzido com o núcleo do .NET em meados de 2016.

Como uma introdução ao EF Core já está disponível na documentação da Microsoft, aqui é simplesmente fornecem links para informações.

#### <a name="additional-resources"></a>Recursos adicionais

-   **Entity Framework Core**
    [*https://docs.microsoft.com/ef/core/*](https://docs.microsoft.com/ef/core/)

-   **Introdução ao ASP.NET Core e o Entity Framework Core usando o Visual Studio**
    [*https://docs.microsoft.com/aspnet/core/data/ef-mvc/*](https://docs.microsoft.com/aspnet/core/data/ef-mvc/)

-   **Classe DbContext**
    [*https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext*](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext)

-   **Comparar EF Core & EF6.x**
    [*https://docs.microsoft.com/ef/efcore-and-ef6/index*](https://docs.microsoft.com/ef/efcore-and-ef6/index)

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a>Infraestrutura no Entity Framework Core de uma perspectiva DDD

Do ponto de vista do DDD, um recurso importante do EF é a capacidade de usar as entidades de domínio POCO, também chamadas de terminologia EF como POCO *primeiro código entidades*. Se você usar as entidades POCO domínio, as classes de modelo de domínio são persistência desconhecem, seguindo o [ignorância de persistência](http://deviq.com/persistence-ignorance/) e [infraestrutura ignorância](https://ayende.com/blog/3137/infrastructure-ignorance) princípios.

Por padrões DDD encapsulam o regras dentro da classe de entidade em si e o comportamento do domínio, assim ele pode controlar invariáveis, validações e regras ao acessar de qualquer coleção. Portanto, não é uma prática recomendada no DDD para permitir acesso público a coleções de filho entidades ou objetos de valor. Em vez disso, você deseja expor métodos que controlam como e quando suas coleções de propriedade e os campos podem ser atualizadas, e o comportamento e as ações que devem ocorrer quando isso acontece.

No EF Core 1.1, para atender a esses requisitos DDD você pode ter campos simples em suas entidades em vez de propriedades com setters públicas e privadas. Se você não quiser que um campo de entidade para ser acessível externamente, você pode criar apenas o campo em vez de uma propriedade ou atributo. Não é necessário usar setters particulares, se você preferir essa abordagem de limpeza.

De maneira semelhante, agora você pode ter acesso somente leitura para coleções usando uma propriedade pública tipo IEnumerable&lt;T&gt;, que é apoiado por um membro do campo particular para a coleção (como uma lista&lt;&gt;) no seu entidade que se baseia no EF para persistência. Versões anteriores do Entity Framework necessário propriedades de coleção para dar suporte a ICollection&lt;T&gt;, que significa que qualquer desenvolvedor usando a classe da entidade pai pode adicionar ou remover itens de suas coleções de propriedade. Essa possibilidade seria contra os padrões recomendados DDD.

Você pode usar uma coleção privada durante a exposição de um objeto IEnumerable somente leitura, conforme mostrado no exemplo de código a seguir:

```csharp
public class Order : Entity
{
    // Using private fields, allowed since EF Core 1.1
    private DateTime _orderDate;
    // Other fields ...
    private readonly List<OrderItem> _orderItems;

    public IEnumerable<OrderItem> OrderItems => _orderItems.AsReadOnly();

    protected Order() { }

    public Order(int buyerId, int paymentMethodId, Address address)
    {
        // Initializations ...
    }

    public void AddOrderItem(int productId, string productName,
        decimal unitPrice, decimal discount,
        string pictureUrl, int units = 1)
    {
        // Validation logic...
        var orderItem = new OrderItem(productId, productName, unitPrice, discount,
            pictureUrl, units);
        _orderItems.Add(orderItem);
    }
}
```

Observe que a propriedade OrderItems só pode ser acessada como somente leitura usando a lista&lt;&gt;. AsReadOnly(). Esse método cria um wrapper de somente leitura ao redor da lista particular para que ele está protegido contra atualizações externas. É muito mais barato do que usando o método ToList, porque ele não precisa copiar todos os itens em uma nova coleção; em vez disso, ele executa apenas uma operação de alocação de heap para a instância do wrapper.

EF Core fornece uma maneira para mapear o modelo de domínio para o banco de dados físico sem contaminação por modelo de domínio. É .NET POCO código puro, pois a ação de mapeamento é implementada na camada de persistência. Em ação esse mapeamento, você precisa configurar o mapeamento de campos no banco de dados. No exemplo a seguir de um método OnModelCreating, o código realçado informa EF principal para acessar a propriedade OrderItems por meio do seu campo.

```csharp
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
    // ...
    modelBuilder.Entity<Order>(ConfigureOrder);
    // Other entities ...
}

void ConfigureOrder(EntityTypeBuilder<Order> orderConfiguration)
{
    // Other configuration ...
    var navigation = orderConfiguration.Metadata.
    FindNavigation(nameof(Order.OrderItems));
    navigation.SetPropertyAccessMode(PropertyAccessMode.Field);
    // Other configuration ...
}
```

Quando você usa campos em vez de propriedades, a entidade ItemPedido é mantida como se tivesse uma lista&lt;ItemPedido&gt; propriedade. No entanto, ela expõe um único acessador (o método AddOrderItem) para adicionar novos itens na ordem. Como resultado, comportamento e os dados são vinculados e sejam consistentes em toda a qualquer código de aplicativo que usa o modelo de domínio.

## <a name="implementing-custom-repositories-with-entity-framework-core"></a>Implementação de repositórios personalizados com o Entity Framework Core

No nível de implementação, um repositório é simplesmente uma classe com o código de persistência de dados coordenada por uma unidade de trabalho (DBContext no núcleo do EF) ao executar atualizações, como mostra a seguinte classe:

```csharp
// using statements...
namespace Microsoft.eShopOnContainers.Services.Ordering.Infrastructure.Repositories
{
    public class BuyerRepository : IBuyerRepository
    {
        private readonly OrderingContext _context;

        public IUnitOfWork UnitOfWork
        {
            get
            {
                return _context;
            }
        }
    }

    public BuyerRepository(OrderingContext context)
    {
        if (context == null)
        {
            throw new ArgumentNullException(
                nameof(context));
        }
        _context = context;
    }

    public Buyer Add(Buyer buyer)
    {
        return _context.Buyers.Add(buyer).Entity;
    }

    public async Task<Buyer> FindAsync(string BuyerIdentityGuid)
    {
        var buyer = await _context.Buyers.Include(b => b.Payments)
            .Where(b => b.FullName == BuyerIdentityGuid)
            .SingleOrDefaultAsync();
        return buyer;
    }
}
```

Observe que a interface IBuyerRepository vem da camada de modelo de domínio. No entanto, a implementação do repositório é feita na camada de infraestrutura e persistência.

O EF DbContext fornecido por meio do construtor injeção de dependência. Ele é compartilhado entre vários repositórios de dentro do mesmo escopo de solicitação HTTP, graças ao seu tempo de vida padrão (ServiceLifetime.Scoped) no contêiner IoC (que também pode ser explicitamente definido com os serviços. AddDbContext&lt;&gt;).

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a>Métodos para implementar em um repositório (transações versus consultas ou atualizações)

Em cada classe de repositório, você deve colocar os métodos de persistência que atualizar o estado de entidades contidas por seu agregação relacionada. Lembre-se de que há uma relação um para um entre uma agregação e seu repositório relacionado. Leve em consideração que um objeto de entidade raiz agregada pode ter inserido entidades filhas dentro de seu gráfico EF. Por exemplo, um comprador pode ter vários métodos de pagamento como entidades filho relacionados.

Como a abordagem para o pedido microsserviço em eShopOnContainers também se baseia em CQS/CQRS, a maioria das consultas não é implementadas no repositórios personalizados. Os desenvolvedores têm a liberdade de criar as consultas e junções que eles precisam para a camada de apresentação sem as restrições impostas pela agregações, os repositórios personalizados por agregação e DDD em geral. A maioria dos repositórios personalizados sugeridos por este guia tem vários update ou métodos transacionais, mas apenas os métodos de consulta necessário obter os dados a serem atualizados. Por exemplo, o repositório BuyerRepository implementa um método FindAsync, porque o aplicativo precisa saber se um cliente específico existe antes de criar um novo comprador relacionado à ordem de.

No entanto, os métodos de consulta real para obter dados para enviar para os aplicativos de cliente ou de camada de apresentação são implementados, conforme mencionado, nas consultas a CQRS com base em consultas flexíveis usando Dapper.

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a>Usando um repositório personalizado em vez de diretamente usando o EF DbContext

A classe DbContext do Entity Framework baseia-se nos padrões de unidade de trabalho e do repositório e pode ser usada diretamente no seu código, como de um controlador MVC do ASP.NET Core. Que é a maneira como você pode criar o código mais simples, como o microsserviço de catálogo CRUD em eShopOnContainers. Em casos onde você deseja o código mais simples possível, você talvez queira diretamente, use a classe DbContext, assim como muitos desenvolvedores.

No entanto, a implementação de repositórios personalizados oferece vários benefícios ao implementar mais complexa microservices ou aplicativos. Os padrões de unidade de trabalho e repositório destinam-se para encapsular a camada de persistência de infraestrutura para que ele será desacoplado do aplicativo e camadas do modelo de domínio. Implementar esses padrões pode facilitar o uso de repositórios de simulação com uma simulação de acesso ao banco de dados.

Figura 9-18, você pode ver as diferenças entre usar não repositórios (diretamente usando o EF DbContext) em comparação a utilizar repositórios que facilitam simular os repositórios.

![](./media/image19.png)

**Figura 9-18**. Uso de repositórios personalizados em vez de um DbContext simples

Existem várias alternativas na simulação. Você pode simular apenas repositórios ou você pode simular toda a unidade de trabalho. Geralmente fictícias apenas os repositórios são suficiente, e a complexidade de abstrair e simular toda a unidade de trabalho normalmente não é necessário.

Posteriormente, quando nos concentramos na camada de aplicativo, você verá como funciona a injeção de dependência no núcleo do ASP.NET e como ele é implementado quando o uso de repositórios.

Em resumo, os repositórios personalizados permitem que você testar o código mais facilmente com testes de unidade que não são afetadas por estado de camada de dados. Se você executar testes que também acessar o banco de dados real por meio do Entity Framework, eles não são testes de unidade, mas os testes de integração, que são muito mais lentos.

Se você estivesse usando DbContext diretamente, a única opção que você teria que seria executar testes de unidade usando um SQL Server na memória com dados previsíveis para testes de unidade. Você não poderá controlar objetos fictícios e dados falsos da mesma maneira no repositório. Naturalmente, você sempre pode testar os controladores MVC.

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a>Vida útil da instância EF DbContext e IUnitOfWork do seu contêiner IoC

O objeto DbContext (exposto como um objeto IUnitOfWork) talvez precise ser compartilhado entre vários repositórios de dentro do mesmo escopo de solicitação HTTP. Por exemplo, isso é verdadeiro quando a operação que está sendo executada deve lidar com várias agregações, ou simplesmente porque você está usando várias instâncias do repositório. Também é importante mencionar que a interface IUnitOfWork é parte do domínio, não um tipo EF.

Para fazer isso, a instância do objeto DbContext deve ter o seu tempo de vida de serviço definido como ServiceLifetime.Scoped. Este é o tempo de vida padrão ao registro de um DbContext com serviços. AddDbContext em seu contêiner IoC do método ConfigureServices do arquivo Startup.cs em seu projeto de API da Web do ASP.NET Core. O código a seguir ilustra isso.

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    // Add framework services.
    services.AddMvc(options =>
    {
        options.Filters.Add(typeof(HttpGlobalExceptionFilter));
    }).AddControllersAsServices();

    services.AddEntityFrameworkSqlServer()
    .AddDbContext<OrderingContext>(options =>
    {
        options.UseSqlServer(Configuration["ConnectionString"],
        sqlop => sqlop.MigrationsAssembly(typeof(Startup).GetTypeInfo().
        Assembly.GetName().Name));
    },
    ServiceLifetime.Scoped // Note that Scoped is the default choice
    // in AddDbContext. It is shown here only for
    // pedagogic purposes.
    );
}
```

O modo de instanciação DbContext não deve ser configurado como ServiceLifetime.Transient ou ServiceLifetime.Singleton.

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a>O tempo de vida de instância de repositório em seu contêiner IoC

De maneira semelhante, o tempo de vida do repositório normalmente deve ser definido como escopo (InstancePerLifetimeScope em Autofac). Ele também pode ser transitório (InstancePerDependency em Autofac), mas seu serviço será mais eficiente em memória que diz respeito ao usar o tempo de vida no escopo.

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

Observe que usando o tempo de vida de singleton para o repositório pode causar problemas graves de simultaneidade quando o DbContext é definido como escopo de tempo de vida (InstancePerLifetimeScope) (o padrão tempo de vida de um DBContext).

#### <a name="additional-resources"></a>Recursos adicionais

-   **Implementando o repositório e a unidade de trabalho padrões em um aplicativo ASP.NET MVC**
    [*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/ Implementing-the-Repository-and-Unit-of-Work-Patterns-in-an-ASP-NET-MVC-Application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)

-   **Jonathan Allen. Estratégias de implementação para o repositório padrão com o Entity Framework, Dapper e cadeia**
    [*https://www.infoq.com/articles/repository-implementation-strategies*](https://www.infoq.com/articles/repository-implementation-strategies)

-   **Cesar de la Torre. Comparando os tempos de vida do serviço de contêiner de ASP.NET Core IoC com escopos de instância de contêiner IoC Autofac**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/ Comparing-ASP-NET-Core-IoC-Service-Life-Times-and-autofac-IoC-Instance-Scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)

## <a name="table-mapping"></a>Mapeamento de tabela

Mapeamento de tabela identifica os dados da tabela a ser consultado do e salvo no banco de dados. Anteriormente, você viu como entidades de domínio (por exemplo, um domínio do produto ou ordem) podem ser usadas para gerar um esquema de banco de dados relacionado. EF fortemente foi projetada para o conceito de *convenções*. Perguntas de endereço de convenções como "Qual será o nome de uma tabela?" ou "qual propriedade é a chave primária?" Convenções normalmente se baseiam nos nomes convencionais — por exemplo, é comum para a chave primária para uma propriedade que termina com a ID.

Por convenção, cada entidade será configurada para mapear para uma tabela com o mesmo nome que o DbSet&lt;TEntity&gt; propriedade que expõe a entidade no contexto de derivada. Se nenhum DbSet&lt;TEntity&gt; valor é fornecido para a entidade especificada, o nome da classe é usado.

### <a name="data-annotations-versus-fluent-api"></a>Anotações de dados em comparação com a API fluente

Existem muitos convenções EF núcleos adicionais e a maioria deles pode ser alterada usando as anotações de dados ou a API fluente, implementado no método OnModelCreating.

As anotações de dados devem ser usadas nas classes de modelo de entidade, que é uma maneira mais invasiva de um ponto de vista DDD. Isso ocorre porque você é contaminação por seu modelo com anotações de dados relacionadas ao banco de dados de infraestrutura. Por outro lado, a API fluente é uma maneira conveniente para alterar a maioria das convenções e mapeamentos dentro de sua camada de infraestrutura de persistência de dados, para que o modelo de entidade será limpo e separado da infraestrutura de persistência.

### <a name="fluent-api-and-the-onmodelcreating-method"></a>API fluente e o método OnModelCreating

Conforme mencionado, para alterar as convenções e os mapeamentos, você pode usar o método OnModelCreating na classe DbContext. O exemplo a seguir mostra como podemos fazer isso no ordenação microsserviço em eShopOnContainers.

```csharp
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
    //Other entities
    modelBuilder.Entity<OrderStatus>(ConfigureOrderStatus);
    //Other entities
}

void ConfigureOrder(EntityTypeBuilder<Order> orderConfiguration)
{
    orderConfiguration.ToTable("orders", DEFAULT_SCHEMA);
    orderConfiguration.HasKey(o => o.Id);
    orderConfiguration.Property(o => o.Id).ForSqlServerUseSequenceHiLo("orderseq", DEFAULT_SCHEMA);
    orderConfiguration.Property<DateTime>("OrderDate").IsRequired();
    orderConfiguration.Property<string>("Street").IsRequired();
    orderConfiguration.Property<string>("State").IsRequired();
    orderConfiguration.Property<string>("City").IsRequired();
    orderConfiguration.Property<string>("ZipCode").IsRequired();
    orderConfiguration.Property<string>("Country").IsRequired();
    orderConfiguration.Property<int>("BuyerId").IsRequired();
    orderConfiguration.Property<int>("OrderStatusId").IsRequired();
    orderConfiguration.Property<int>("PaymentMethodId").IsRequired();

    var navigation =
    orderConfiguration.Metadata.FindNavigation(nameof(Order.OrderItems));
    // DDD Patterns comment:
    // Set as Field (new since EF 1.1) to access
    // the OrderItem collection property as a field
    navigation.SetPropertyAccessMode(PropertyAccessMode.Field);

    orderConfiguration.HasOne(o => o.PaymentMethod)
        .WithMany()
        .HasForeignKey("PaymentMethodId")
        .OnDelete(DeleteBehavior.Restrict);
        orderConfiguration.HasOne(o => o.Buyer)
        .WithMany()
        .HasForeignKey("BuyerId");
        orderConfiguration.HasOne(o => o.OrderStatus)
        .WithMany()
        .HasForeignKey("OrderStatusId");
}
```

Você pode definir os mapeamentos de API fluente no método OnModelCreating mesmo, mas é recomendável que o código de partição e ter vários submethods, um por entidade, conforme mostrado no exemplo. Para modelos muito grandes, ainda é recomendável ter arquivos de origem separados (classes estáticas) para configurar tipos de entidade diferente.

O código de exemplo é explícito. No entanto, convenções EF Core fazer a maioria disso automaticamente, portanto, o código real que você precisa gravar para alcançar a mesma coisa seria muito menor.

### <a name="the-hilo-algorithm-in-ef-core"></a>O algoritmo Hi/Lo no núcleo do EF

Um aspecto interessante de código no exemplo anterior é que ele usa o [algoritmo Hi/Lo](https://vladmihalcea.com/2014/06/23/the-hilo-algorithm/) como a estratégia de geração de chave.

O algoritmo Hi/Lo é útil quando você precisa de chaves exclusivas. Como obter um resumo, o algoritmo Hi-Lo atribui identificadores exclusivos para linhas da tabela enquanto não dependendo armazenar a linha no banco de dados imediatamente. Permite que você começar a usar os identificadores imediatamente, como acontece com o banco de dados sequencial regular IDs.

O algoritmo Hi/Lo descreve um mecanismo para gerar identificações de seguras no lado do cliente em vez de no banco de dados. *Segurança* neste contexto significa sem colisões. Esse algoritmo é interessante por esses motivos:

-   Ele não interrompem o padrão de unidade de trabalho.

-   Ele não requer a fazer viagens de ida e geradores de sequência de maneira em outros DBMSs.

-   Ele gera um identificador de legível humano, ao contrário das técnicas que usam GUIDs.

EF Core dá suporte [HiLo](http://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) com o método ForSqlServerUseSequenceHiLo, conforme mostrado no exemplo anterior.

### <a name="mapping-fields-instead-of-properties"></a>Mapeamento de campos, em vez de propriedades

Com o recurso do EF Core 1.1 que mapeia as colunas para campos, é possível para não usar as propriedades na classe de entidade e apenas para mapear colunas de uma tabela para campos. Um uso comum para isso seria campos privados para algum estado interno que não precisam ser acessados de fora da entidade.

EF 1.1 oferece suporte a uma maneira de mapear um campo sem uma propriedade relacionada a uma coluna no banco de dados. Você pode fazer isso com campos único ou também com coleções, como uma lista de&lt; &gt; campo. Esse ponto foi mencionado anteriormente, quando discutimos modelagem as classes de modelo de domínio, mas aqui você pode ver como esse mapeamento é executado com a configuração de PropertyAccessMode.Field realçada no código anterior.

### <a name="using-shadow-properties-in-value-objects-for-hidden-ids-at-the-infrastructure-level"></a>Usando propriedades de sombra nos objetos de valor de IDs ocultos no nível de infraestrutura

Propriedades de sombra no núcleo do EF são propriedades que não existem em seu modelo de classe de entidade. Os valores e estados dessas propriedades são mantidos em puramente o [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) classe no nível de infraestrutura.

Do ponto de vista do DDD, propriedades de sombra são uma maneira conveniente de implementar objetos de valor, ocultando a ID como uma chave primária de propriedade de sombra. Isso é importante, porque um objeto de valor não deve ter a identidade (pelo menos, você não deve ter a identificação da camada de modelo de domínio quando objetos de valor de formatação). O ponto aqui é que a partir da versão atual do EF Core, Core EF não tem uma maneira de implementar objetos de valor como [tipos complexos](https://msdn.microsoft.com/library/jj680147(v=vs.113).aspx), como é possível no EF 6. x. É por isso que você precisa implementar um objeto de valor como uma entidade com uma ID oculta (chave primária) definido como uma propriedade de sombra no momento.

Como você pode ver no [objeto de valor do endereço](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs) eShopOnContainers, no modelo de endereço você não vê uma ID:

```csharp
public class Address : ValueObject
{
    public String Street { get; private set; }
    public String City { get; private set; }
    public String State { get; private set; }
    public String Country { get; private set; }
    public String ZipCode { get; private set; }
    //Constructor initializing, etc
}
```

Mas nos bastidores, é necessário fornecer uma ID de forma que o EF Core é capaz de manter esses dados nas tabelas de banco de dados. Podemos fazer isso no método de ConfigureAddress a [OrderingContext.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Infrastructure/OrderingContext.cs) classe no nível de infraestrutura, portanto não podemos poluir o modelo de domínio com o código de infraestrutura EF.

```csharp
void ConfigureAddress(EntityTypeBuilder<Address> addressConfiguration)
{
    addressConfiguration.ToTable("address", DEFAULT_SCHEMA);
    // DDD pattern comment:
    // Implementing the Address ID as a shadow property, because the
    // address is a value object and an identity is not required for a
    // value object
    // EF Core just needs the ID so it can store it in a database table
    // See: https://docs.microsoft.com/ef/core/modeling/shadow-properties
    addressConfiguration.Property<int>("Id").IsRequired();
    addressConfiguration.HasKey("Id");
}
```

#### <a name="additional-resources"></a>Recursos adicionais

-   **Mapeamento de tabela**
    [*https://docs.microsoft.com/ef/core/modeling/relational/tables*](https://docs.microsoft.com/ef/core/modeling/relational/tables)

-   **Use HiLo para gerar chaves com o Entity Framework Core**
    [*http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/*](http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/)

-   **Fazendo campos**
    [*https://docs.microsoft.com/ef/core/modeling/backing-field*](https://docs.microsoft.com/ef/core/modeling/backing-field)

-   **Steve Smith. Encapsulado coleções no Entity Framework Core**
    [*http://ardalis.com/encapsulated-collections-in-entity-framework-core*](http://ardalis.com/encapsulated-collections-in-entity-framework-core)

-   **Propriedades de sombra**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)


>[!div class="step-by-step"]
[Anterior] (infraestrutura-persistência-camada-design.md) [Avançar] (nosql-banco de dados-persistência-infrastructure.md)
