---
title: Implementando a camada de persistência da infraestrutura com o Entity Framework Core
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Implementando a camada de persistência da infraestrutura com o Entity Framework Core
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.openlocfilehash: 6003252d7e87428c7f954b57c3b67a041e3f3b15
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106470"
---
# <a name="implementing-the-infrastructure-persistence-layer-with-entity-framework-core"></a><span data-ttu-id="40bb2-103">Implementando a camada de persistência da infraestrutura com o Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="40bb2-103">Implementing the infrastructure persistence layer with Entity Framework Core</span></span>

<span data-ttu-id="40bb2-104">Ao usar bancos de dados relacionais, como o SQL Server, o Oracle ou o PostgreSQL, uma abordagem recomendada é implementar a camada de persistência com base no EF (Entity Framework).</span><span class="sxs-lookup"><span data-stu-id="40bb2-104">When you use relational databases such as SQL Server, Oracle, or PostgreSQL, a recommended approach is to implement the persistence layer based on Entity Framework (EF).</span></span> <span data-ttu-id="40bb2-105">O EF é compatível com LINQ e fornece objetos fortemente tipados para o modelo, bem como uma persistência simplificada no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="40bb2-105">EF supports LINQ and provides strongly typed objects for your model, as well as simplified persistence into your database.</span></span>

<span data-ttu-id="40bb2-106">O Entity Framework tem uma longa história de participação no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="40bb2-106">Entity Framework has a long history as part of the .NET Framework.</span></span> <span data-ttu-id="40bb2-107">Ao usar o .NET Core, você também deve usar o Entity Framework Core, que é executado no Windows ou no Linux da mesma maneira que o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="40bb2-107">When you use .NET Core, you should also use Entity Framework Core, which runs on Windows or Linux in the same way as .NET Core.</span></span> <span data-ttu-id="40bb2-108">O EF Core é uma reformulação completa do Entity Framework, implementado com muito menos espaço e importantes melhorias no desempenho.</span><span class="sxs-lookup"><span data-stu-id="40bb2-108">EF Core is a complete rewrite of Entity Framework, implemented with a much smaller footprint and important improvements in performance.</span></span>

## <a name="introduction-to-entity-framework-core"></a><span data-ttu-id="40bb2-109">Introdução ao Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="40bb2-109">Introduction to Entity Framework Core</span></span>

<span data-ttu-id="40bb2-110">O Entity Framework (EF) Core é uma versão de multiplaforma leve, extensível e de plataforma cruzada da popular tecnologia de acesso a dados do Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="40bb2-110">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="40bb2-111">Ele foi introduzido com o .NET Core em meados de 2016.</span><span class="sxs-lookup"><span data-stu-id="40bb2-111">It was introduced with .NET Core in mid-2016.</span></span>

<span data-ttu-id="40bb2-112">Como uma introdução ao EF Core já está disponível na documentação da Microsoft, aqui nós vamos fornecer apenas os links para as informações.</span><span class="sxs-lookup"><span data-stu-id="40bb2-112">Since an introduction to EF Core is already available in Microsoft documentation, here we simply provide links to that information.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="40bb2-113">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="40bb2-113">Additional resources</span></span>

-   <span data-ttu-id="40bb2-114">**Entity Framework Core**
    [*https://docs.microsoft.com/ef/core/*](https://docs.microsoft.com/ef/core/)</span><span class="sxs-lookup"><span data-stu-id="40bb2-114">**Entity Framework Core**
[*https://docs.microsoft.com/ef/core/*](https://docs.microsoft.com/ef/core/)</span></span>

-   <span data-ttu-id="40bb2-115">**Introdução ao ASP.NET Core e ao Entity Framework Core usando o Visual Studio**
    [*https://docs.microsoft.com/aspnet/core/data/ef-mvc/*](https://docs.microsoft.com/aspnet/core/data/ef-mvc/)</span><span class="sxs-lookup"><span data-stu-id="40bb2-115">**Getting started with ASP.NET Core and Entity Framework Core using Visual Studio**
[*https://docs.microsoft.com/aspnet/core/data/ef-mvc/*](https://docs.microsoft.com/aspnet/core/data/ef-mvc/)</span></span>

-   <span data-ttu-id="40bb2-116">**DbContext Class**
    [*https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext*](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext) (Classe DbContext)</span><span class="sxs-lookup"><span data-stu-id="40bb2-116">**DbContext Class**
[*https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext*](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext)</span></span>

-   <span data-ttu-id="40bb2-117">**Comparar o EF Core e o EF6.x**
    [*https://docs.microsoft.com/ef/efcore-and-ef6/index*](https://docs.microsoft.com/ef/efcore-and-ef6/index)</span><span class="sxs-lookup"><span data-stu-id="40bb2-117">**Compare EF Core & EF6.x**
[*https://docs.microsoft.com/ef/efcore-and-ef6/index*](https://docs.microsoft.com/ef/efcore-and-ef6/index)</span></span>

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a><span data-ttu-id="40bb2-118">Infraestrutura no Entity Framework Core da perspectiva do DDD</span><span class="sxs-lookup"><span data-stu-id="40bb2-118">Infrastructure in Entity Framework Core from a DDD perspective</span></span>

<span data-ttu-id="40bb2-119">Do ponto de vista do DDD, um recurso importante do EF é a capacidade de usar as entidades de domínio POCO (objeto CRL básico), também conhecidas na terminologia do EF como *entidades code-first* POCO.</span><span class="sxs-lookup"><span data-stu-id="40bb2-119">From a DDD point of view, an important capability of EF is the ability to use POCO domain entities, also known in EF terminology as POCO *code-first entities*.</span></span> <span data-ttu-id="40bb2-120">Se você usar as entidades de domínio POCO, as classes de modelo de domínio ignorarão a persistência, seguindo os princípios de [Ignorância de Persistência](http://deviq.com/persistence-ignorance/) e de [Ignorância de Infraestrutura](https://ayende.com/blog/3137/infrastructure-ignorance).</span><span class="sxs-lookup"><span data-stu-id="40bb2-120">If you use POCO domain entities, your domain model classes are persistence-ignorant, following the [Persistence Ignorance](http://deviq.com/persistence-ignorance/) and the [Infrastructure Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance) principles.</span></span>

<span data-ttu-id="40bb2-121">De acordo com os padrões do DDD você deve encapsular o comportamento e as regras do domínio dentro da própria classe de entidade, assim ela poderá controlar as invariáveis, as validações e as regras ao acessar qualquer coleção.</span><span class="sxs-lookup"><span data-stu-id="40bb2-121">Per DDD patterns, you should encapsulate domain behavior and rules within the entity class itself, so it can control invariants, validations, and rules when accessing any collection.</span></span> <span data-ttu-id="40bb2-122">Portanto, não é uma prática recomendada no DDD permitir o acesso público a coleções de entidades filhas ou a objetos de valor.</span><span class="sxs-lookup"><span data-stu-id="40bb2-122">Therefore, it is not a good practice in DDD to allow public access to collections of child entities or value objects.</span></span> <span data-ttu-id="40bb2-123">Em vez disso, é possível expor métodos que controlam como e quando as coleções de propriedade e os campos podem ser atualizados e qual comportamento e medidas deverão ser tomadas quando isso acontecer.</span><span class="sxs-lookup"><span data-stu-id="40bb2-123">Instead, you want to expose methods that control how and when your fields and property collections can be updated, and what behavior and actions should occur when that happens.</span></span>

<span data-ttu-id="40bb2-124">Desde o EF Core 1.1, para atender a esses requisitos de DDD, é possível ter campos simples nas entidades em vez de propriedades públicas.</span><span class="sxs-lookup"><span data-stu-id="40bb2-124">Since EF Core 1.1, to satisfy those DDD requirements, you can have plain fields in your entities instead of public properties.</span></span> <span data-ttu-id="40bb2-125">Se você não quiser que um campo de entidade fique acessível externamente, bastará criar o atributo ou o campo em vez de uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="40bb2-125">If you do not want an entity field to be externally accessible, you can just create the attribute or field instead of a property.</span></span> <span data-ttu-id="40bb2-126">Também é possível usar setters de propriedade privada.</span><span class="sxs-lookup"><span data-stu-id="40bb2-126">You can also use private property setters.</span></span>

<span data-ttu-id="40bb2-127">Da mesma forma, agora é possível ter acesso somente leitura a coleções usando uma propriedade pública digitada como `IReadOnlyCollection<T>`, com o apoio de um membro de campo privado para a coleção (como uma `List<T>`) na entidade, que se baseia no EF para persistência.</span><span class="sxs-lookup"><span data-stu-id="40bb2-127">In a similar way, you can now have read-only access to collections by using a public property typed as  `IReadOnlyCollection<T>`, which is backed by a private field member for the collection (like a `List<T>`) in your entity that relies on EF for persistence.</span></span> <span data-ttu-id="40bb2-128">As versões anteriores do Entity Framework exigiam que as propriedades da coleção fossem compatíveis com `ICollection<T>`, o que significava que qualquer desenvolvedor que usasse uma classe da entidade pai poderia adicionar ou remover itens por meio de suas coleções de propriedade.</span><span class="sxs-lookup"><span data-stu-id="40bb2-128">Previous versions of Entity Framework required collection properties to support `ICollection<T>`, which meant that any developer using the parent entity class could add or remove items through its property collections.</span></span> <span data-ttu-id="40bb2-129">Essa possibilidade seria em relação aos padrões recomendados no DDD.</span><span class="sxs-lookup"><span data-stu-id="40bb2-129">That possibility would be against the recommended patterns in DDD.</span></span>

<span data-ttu-id="40bb2-130">É possível usar uma coleção privada ao expor um objeto `IReadOnlyCollection<T>` somente leitura, como é mostrado no exemplo de código a seguir:</span><span class="sxs-lookup"><span data-stu-id="40bb2-130">You can use a private collection while exposing a read-only `IReadOnlyCollection<T>` object, as shown in the following code example:</span></span>

```csharp
public class Order : Entity
{
    // Using private fields, allowed since EF Core 1.1
    private DateTime _orderDate;
    // Other fields ...

    private readonly List<OrderItem> _orderItems; 
    public IReadOnlyCollection<OrderItem> OrderItems => _orderItems;

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

        var orderItem = new OrderItem(productId, productName, 
                                      unitPrice, discount,
                                      pictureUrl, units);
        _orderItems.Add(orderItem);
    }
}
```

<span data-ttu-id="40bb2-131">Observe que a propriedade `OrderItems` somente pode ser acessada como somente leitura usando `IReadOnlyCollection<OrderItem>`.</span><span class="sxs-lookup"><span data-stu-id="40bb2-131">Note that the `OrderItems` property can only be accessed as read-only using `IReadOnlyCollection<OrderItem>`.</span></span> <span data-ttu-id="40bb2-132">Esse tipo é somente leitura, portanto, ele está protegido contra as atualizações externas regulares.</span><span class="sxs-lookup"><span data-stu-id="40bb2-132">This type is read-only so it is protected against regular external updates.</span></span> 

<span data-ttu-id="40bb2-133">O EF Core fornece uma maneira de mapear o modelo de domínio para o banco de dados físico sem "contaminar" o modelo de domínio.</span><span class="sxs-lookup"><span data-stu-id="40bb2-133">EF Core provides a way to map the domain model to the physical database without "contaminating" the domain model.</span></span> <span data-ttu-id="40bb2-134">Trata-se de puro código POCO do .NET, pois a ação de mapeamento é implementada na camada de persistência.</span><span class="sxs-lookup"><span data-stu-id="40bb2-134">It is pure .NET POCO code, because the mapping action is implemented in the persistence layer.</span></span> <span data-ttu-id="40bb2-135">Nessa ação de mapeamento, você precisa configurar o mapeamento dos campos para o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="40bb2-135">In that mapping action, you need to configure the fields-to-database mapping.</span></span> <span data-ttu-id="40bb2-136">No seguinte exemplo de um método OnModelCreating, o código realçado solicita que o EF Core acesse a propriedade OrderItems por meio de seu campo.</span><span class="sxs-lookup"><span data-stu-id="40bb2-136">In the following example of an OnModelCreating method, the highlighted code tells EF Core to access the OrderItems property through its field.</span></span>

```csharp
// At OrderingContext.cs from eShopOnContainers
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
   // ...
   modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
   // Other entities’ configuration ...
}

// At OrderEntityTypeConfiguration.cs from eShopOnContainers
class OrderEntityTypeConfiguration : IEntityTypeConfiguration<Order>
{
    public void Configure(EntityTypeBuilder<Order> orderConfiguration)
    {
        orderConfiguration.ToTable("orders", OrderingContext.DEFAULT_SCHEMA);
        // Other configuration

        var navigation = 
              orderConfiguration.Metadata.FindNavigation(nameof(Order.OrderItems));

        //EF access the OrderItem collection property through its backing field
        navigation.SetPropertyAccessMode(PropertyAccessMode.Field);

        // Other configuration
    }
}
```

<span data-ttu-id="40bb2-137">Ao usar campos em vez de propriedades, a entidade OrderItem será persistida como se tivesse uma propriedade List&lt;OrderItem&gt;.</span><span class="sxs-lookup"><span data-stu-id="40bb2-137">When you use fields instead of properties, the OrderItem entity is persisted just as if it had a List&lt;OrderItem&gt; property.</span></span> <span data-ttu-id="40bb2-138">No entanto, ela expõe um único acessador, o método `AddOrderItem`, para adicionar novos itens ao pedido.</span><span class="sxs-lookup"><span data-stu-id="40bb2-138">However, it exposes a single accessor, the `AddOrderItem` method for adding new items to the order.</span></span> <span data-ttu-id="40bb2-139">Como resultado, o comportamento e os dados ficarão vinculados e serão consistentes em todos os códigos de aplicativo que usarem o modelo de domínio.</span><span class="sxs-lookup"><span data-stu-id="40bb2-139">As a result, behavior and data are tied together and will be consistent throughout any application code that uses the domain model.</span></span>

## <a name="implementing-custom-repositories-with-entity-framework-core"></a><span data-ttu-id="40bb2-140">Implementando repositórios personalizados com o Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="40bb2-140">Implementing custom repositories with Entity Framework Core</span></span>

<span data-ttu-id="40bb2-141">No nível da implementação, um repositório é simplesmente uma classe com o código de persistência de dados, coordenada por uma unidade de trabalho (DBContext no EF Core) ao executar atualizações, como mostra a seguinte classe:</span><span class="sxs-lookup"><span data-stu-id="40bb2-141">At the implementation level, a repository is simply a class with data persistence code coordinated by a unit of work (DBContext in EF Core) when performing updates, as shown in the following class:</span></span>

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

        public BuyerRepository(OrderingContext context)
        {
            _context = context ?? throw new ArgumentNullException(nameof(context));
        }

        public Buyer Add(Buyer buyer)
        {
            return _context.Buyers.Add(buyer).Entity; 
        }

        public async Task<Buyer> FindAsync(string BuyerIdentityGuid)
        {
            var buyer = await _context.Buyers
                .Include(b => b.Payments)
                .Where(b => b.FullName == BuyerIdentityGuid)
                .SingleOrDefaultAsync();

            return buyer;
        }
    }
}
```

<span data-ttu-id="40bb2-142">Observe que a interface IBuyerRepository vem da camada de modelo de domínio como um contrato.</span><span class="sxs-lookup"><span data-stu-id="40bb2-142">Note that the IBuyerRepository interface comes from the domain model layer as a contract.</span></span> <span data-ttu-id="40bb2-143">No entanto, a implementação do repositório é feita na camada de persistência e de infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="40bb2-143">However, the repository implementation is done at the persistence and infrastructure layer.</span></span>

<span data-ttu-id="40bb2-144">O DbContext do EF é fornecido pelo construtor por meio de injeção de dependência.</span><span class="sxs-lookup"><span data-stu-id="40bb2-144">The EF DbContext comes through the constructor through Dependency Injection.</span></span> <span data-ttu-id="40bb2-145">Ele é compartilhado entre vários repositórios no mesmo escopo de solicitação HTTP, graças ao seu tempo de vida padrão (ServiceLifetime.Scoped) no contêiner de IoC (inversão de controle) (que também pode ser definido explicitamente com services.AddDbContext&lt;&gt;).</span><span class="sxs-lookup"><span data-stu-id="40bb2-145">It is shared between multiple repositories within the same HTTP request scope, thanks to its default lifetime (ServiceLifetime.Scoped) in the IoC container (which can also be explicitly set with services.AddDbContext&lt;&gt;).</span></span>

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a><span data-ttu-id="40bb2-146">Métodos a serem implementados em um repositório (atualizações ou transações em comparação com consultas)</span><span class="sxs-lookup"><span data-stu-id="40bb2-146">Methods to implement in a repository (updates or transactions versus queries)</span></span>

<span data-ttu-id="40bb2-147">Em cada classe de repositório, você deve colocar os métodos de persistência que atualizam o estado das entidades contidas na agregação relacionada.</span><span class="sxs-lookup"><span data-stu-id="40bb2-147">Within each repository class, you should put the persistence methods that update the state of entities contained by its related aggregate.</span></span> <span data-ttu-id="40bb2-148">Lembre-se de que há uma relação um-para-um entre uma agregação e seu repositório relacionado.</span><span class="sxs-lookup"><span data-stu-id="40bb2-148">Remember there is one-to-one relationship between an aggregate and its related repository.</span></span> <span data-ttu-id="40bb2-149">Leve em consideração que um objeto de entidade de raiz de agregação pode ter entidades filhas inseridas no grafo do EF.</span><span class="sxs-lookup"><span data-stu-id="40bb2-149">Take into account that an aggregate root entity object might have embedded child entities within its EF graph.</span></span> <span data-ttu-id="40bb2-150">Por exemplo, um comprador pode ter vários métodos de pagamento como entidades filhas relacionadas.</span><span class="sxs-lookup"><span data-stu-id="40bb2-150">For example, a buyer might have multiple payment methods as related child entities.</span></span>

<span data-ttu-id="40bb2-151">Como a abordagem para o microsserviço de pedidos no eShopOnContainers também se baseia em CQS/CQRS, a maioria das consultas não são implementadas em repositórios personalizados.</span><span class="sxs-lookup"><span data-stu-id="40bb2-151">Since the approach for the ordering microservice in eShopOnContainers is also based on CQS/CQRS, most of the queries are not implemented in custom repositories.</span></span> <span data-ttu-id="40bb2-152">Os desenvolvedores têm a liberdade de criar as consultas e junções que precisam para a camada de apresentação sem as restrições impostas pelas agregações, pelos repositórios personalizados por agregação e pelo DDD em geral.</span><span class="sxs-lookup"><span data-stu-id="40bb2-152">Developers have the freedom to create the queries and joins they need for the presentation layer without the restrictions imposed by aggregates, custom repositories per aggregate, and DDD in general.</span></span> <span data-ttu-id="40bb2-153">A maioria dos repositórios personalizados sugeridos por este guia tem vários métodos de atualização ou transacionais, mas apenas os métodos de consulta necessários para fazer com que os dados sejam atualizados.</span><span class="sxs-lookup"><span data-stu-id="40bb2-153">Most of the custom repositories suggested by this guide have several update or transactional methods but just the query methods needed to get data to be updated.</span></span> <span data-ttu-id="40bb2-154">Por exemplo, o repositório BuyerRepository implementa um método FindAsync, porque o aplicativo precisa saber se um comprador específico existe antes de criar um novo comprador relacionado ao pedido.</span><span class="sxs-lookup"><span data-stu-id="40bb2-154">For example, the BuyerRepository repository implements a FindAsync method, because the application needs to know whether a particular buyer exists before creating a new buyer related to the order.</span></span>

<span data-ttu-id="40bb2-155">No entanto, os métodos de consulta reais para obter os dados a serem enviados à camada de apresentação ou aos aplicativos clientes são implementados, conforme mencionado, nas consultas de CQRS baseadas em consultas flexíveis usando Dapper.</span><span class="sxs-lookup"><span data-stu-id="40bb2-155">However, the real query methods to get data to send to the presentation layer or client apps are implemented, as mentioned, in the CQRS queries based on flexible queries using Dapper.</span></span>

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a><span data-ttu-id="40bb2-156">Usando um repositório personalizado em vez de usar o DbContext EF diretamente</span><span class="sxs-lookup"><span data-stu-id="40bb2-156">Using a custom repository versus using EF DbContext directly</span></span>

<span data-ttu-id="40bb2-157">A classe DbContext do Entity Framework baseia-se nos padrões de unidade de trabalho e de repositório e pode ser usada diretamente no código, como em um controlador MVC do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="40bb2-157">The Entity Framework DbContext class is based on the Unit of Work and Repository patterns, and can be used directly from your code, such as from an ASP.NET Core MVC controller.</span></span> <span data-ttu-id="40bb2-158">Essa é a maneira de criar o código mais simples possível, como o microsserviço de catálogo de CRUD (criar, ler, atualizar e excluir) no eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="40bb2-158">That is the way you can create the simplest code, as in the CRUD catalog microservice in eShopOnContainers.</span></span> <span data-ttu-id="40bb2-159">Nos casos em que você deseja o código mais simples possível, é possível usar diretamente a classe DbContext, como muitos desenvolvedores fazem.</span><span class="sxs-lookup"><span data-stu-id="40bb2-159">In cases where you want the simplest code possible, you might want to directly use the DbContext class, as many developers do.</span></span>

<span data-ttu-id="40bb2-160">No entanto, a implementação de repositórios personalizados oferece vários benefícios ao implementar microsserviços ou aplicativos mais complexos.</span><span class="sxs-lookup"><span data-stu-id="40bb2-160">However, implementing custom repositories provides several benefits when implementing more complex microservices or applications.</span></span> <span data-ttu-id="40bb2-161">Os padrões de unidade de trabalho e de repositório são indicados para encapsular a camada de persistência da infraestrutura para que ela fique desacoplada das camadas de aplicativo e de modelo de domínio.</span><span class="sxs-lookup"><span data-stu-id="40bb2-161">The Unit of Work and Repository patterns are intended to encapsulate the infrastructure persistence layer so it is decoupled from the application and domain model layers.</span></span> <span data-ttu-id="40bb2-162">A implementação desses padrões pode facilitar o uso de repositórios fictícios para simulação de acesso ao banco de dados.</span><span class="sxs-lookup"><span data-stu-id="40bb2-162">Implementing these patterns can facilitate the use of mock repositories simulating access to the database.</span></span>

<span data-ttu-id="40bb2-163">Na Figura 9-18, veja as diferenças entre não usar repositórios (usando diretamente o DbContext do EF) e usar repositórios, o que facilita a simulação desses repositórios.</span><span class="sxs-lookup"><span data-stu-id="40bb2-163">In Figure 9-18 you can see the differences between not using repositories (directly using the EF DbContext) versus using repositories which make it easier to mock those repositories.</span></span>

![](./media/image19.png)

<span data-ttu-id="40bb2-164">**Figura 9-18**.</span><span class="sxs-lookup"><span data-stu-id="40bb2-164">**Figure 9-18**.</span></span> <span data-ttu-id="40bb2-165">Usando repositórios personalizados em vez de um DbContext simples</span><span class="sxs-lookup"><span data-stu-id="40bb2-165">Using custom repositories versus a plain DbContext</span></span>

<span data-ttu-id="40bb2-166">Existem várias alternativas para simulação.</span><span class="sxs-lookup"><span data-stu-id="40bb2-166">There are multiple alternatives when mocking.</span></span> <span data-ttu-id="40bb2-167">Você pode simular apenas repositórios ou simular toda a unidade de trabalho.</span><span class="sxs-lookup"><span data-stu-id="40bb2-167">You could mock just repositories or you could mock a whole unit of work.</span></span> <span data-ttu-id="40bb2-168">Geralmente, simular apenas os repositórios já é suficiente e a complexidade de abstrair e simular toda a unidade de trabalho, normalmente, não é necessária.</span><span class="sxs-lookup"><span data-stu-id="40bb2-168">Usually mocking just the repositories is enough, and the complexity to abstract and mock a whole unit of work is usually not needed.</span></span>

<span data-ttu-id="40bb2-169">Mais adiante, quando nos concentramos na camada de aplicativo, você verá como funciona a injeção de dependência no ASP.NET Core e como ela é implementada ao usar repositórios.</span><span class="sxs-lookup"><span data-stu-id="40bb2-169">Later, when we focus on the application layer, you will see how Dependency Injection works in ASP.NET Core and how it is implemented when using repositories.</span></span>

<span data-ttu-id="40bb2-170">Em resumo, os repositórios personalizados permitem que você teste o código mais facilmente com testes de unidade que não são afetados pelo estado da camada de dados.</span><span class="sxs-lookup"><span data-stu-id="40bb2-170">In short, custom repositories allow you to test code more easily with unit tests that are not impacted by the data tier state.</span></span> <span data-ttu-id="40bb2-171">Se você executar testes que também acessem o banco de dados real por meio do Entity Framework, eles não serão testes de unidade, mas sim testes de integração, que são muito mais lentos.</span><span class="sxs-lookup"><span data-stu-id="40bb2-171">If you run tests that also access the actual database through the Entity Framework, they are not unit tests but integration tests, which are a lot slower.</span></span>

<span data-ttu-id="40bb2-172">Se você estivesse usando o DbContext diretamente, a única opção possível seria executar testes de unidade usando um SQL Server na memória, com os dados previsíveis para testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="40bb2-172">If you were using DbContext directly, the only choice you would have would be to run unit tests by using an in-memory SQL Server with predictable data for unit tests.</span></span> <span data-ttu-id="40bb2-173">Não seria possível controlar objetos fictícios e dados falsos da mesma maneira no nível do repositório.</span><span class="sxs-lookup"><span data-stu-id="40bb2-173">You would not be able to control mock objects and fake data in the same way at the repository level.</span></span> <span data-ttu-id="40bb2-174">Obviamente, sempre é possível testar os controladores MVC.</span><span class="sxs-lookup"><span data-stu-id="40bb2-174">Of course, you could always test the MVC controllers.</span></span>

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="40bb2-175">Tempo de vida da instância de DbContext e de IUnitOfWork do EF no contêiner de IoC</span><span class="sxs-lookup"><span data-stu-id="40bb2-175">EF DbContext and IUnitOfWork instance lifetime in your IoC container</span></span>

<span data-ttu-id="40bb2-176">O objeto DbContext (exposto como um objeto IUnitOfWork) talvez precise ser compartilhado entre vários repositórios dentro do mesmo escopo de solicitação HTTP.</span><span class="sxs-lookup"><span data-stu-id="40bb2-176">The DbContext object (exposed as an IUnitOfWork object) might need to be shared among multiple repositories within the same HTTP request scope.</span></span> <span data-ttu-id="40bb2-177">Por exemplo, isso é verdadeiro quando a operação que está sendo executada precisa lidar com várias agregações ou simplesmente porque você está usando várias instâncias do repositório.</span><span class="sxs-lookup"><span data-stu-id="40bb2-177">For example, this is true when the operation being executed must deal with multiple aggregates, or simply because you are using multiple repository instances.</span></span> <span data-ttu-id="40bb2-178">Também é importante mencionar que a interface IUnitOfWork faz parte da camada de domínio, ela não é um tipo do EF Core.</span><span class="sxs-lookup"><span data-stu-id="40bb2-178">It is also important to mention that the IUnitOfWork interface is part of your domain layer, not an EF Core type.</span></span>

<span data-ttu-id="40bb2-179">Para isso, o tempo de vida de serviço da instância do objeto DbContext precisa ser definido como ServiceLifetime.Scoped.</span><span class="sxs-lookup"><span data-stu-id="40bb2-179">In order to do that, the instance of the DbContext object has to have its service lifetime set to ServiceLifetime.Scoped.</span></span> <span data-ttu-id="40bb2-180">Este é o tempo de vida padrão ao registrar um DbContext no services.AddDbContext no contêiner de IoC (inversão de controle) do método ConfigureServices do arquivo Startup.cs, no projeto de API Web ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="40bb2-180">This is the default lifetime when registering a DbContext with services.AddDbContext in your IoC container from the ConfigureServices method of the Startup.cs file in your ASP.NET Core Web API project.</span></span> <span data-ttu-id="40bb2-181">O código a seguir ilustra isso.</span><span class="sxs-lookup"><span data-stu-id="40bb2-181">The following code illustrates this.</span></span>

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
                               sqlOptions => sqlOptions.MigrationsAssembly(typeof(Startup).GetTypeInfo().
                                                                                    Assembly.GetName().Name));
      },
      ServiceLifetime.Scoped // Note that Scoped is the default choice
                             // in AddDbContext. It is shown here only for
                             // pedagogic purposes.
      );
}
```

<span data-ttu-id="40bb2-182">O modo de criação de instância do DbContext não deve ser configurado como ServiceLifetime.Transient ou ServiceLifetime.Singleton.</span><span class="sxs-lookup"><span data-stu-id="40bb2-182">The DbContext instantiation mode should not be configured as ServiceLifetime.Transient or ServiceLifetime.Singleton.</span></span>

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="40bb2-183">O tempo de vida da instância de repositório no contêiner de IoC</span><span class="sxs-lookup"><span data-stu-id="40bb2-183">The repository instance lifetime in your IoC container</span></span>

<span data-ttu-id="40bb2-184">Da mesma forma, o tempo de vida do repositório normalmente deve ser definido como no escopo (InstancePerLifetimeScope no Autofac).</span><span class="sxs-lookup"><span data-stu-id="40bb2-184">In a similar way, repository’s lifetime should usually be set as scoped (InstancePerLifetimeScope in Autofac).</span></span> <span data-ttu-id="40bb2-185">Ele também pode ser transitório (InstancePerDependency no Autofac), mas o serviço será mais eficiente em relação à memória ao usar o tempo de vida no escopo.</span><span class="sxs-lookup"><span data-stu-id="40bb2-185">It could also be transient (InstancePerDependency in Autofac), but your service will be more efficient in regards memory when using the scoped lifetime.</span></span>

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

<span data-ttu-id="40bb2-186">Observe que usar o tempo de vida singleton para o repositório poderá causar problemas graves de simultaneidade quando o DbContext estiver definido como tempo de vida no escopo (InstancePerLifetimeScope) (os tempos de vida padrão de um DBContext).</span><span class="sxs-lookup"><span data-stu-id="40bb2-186">Note that using the singleton lifetime for the repository could cause you serious concurrency problems when your DbContext is set to scoped (InstancePerLifetimeScope) lifetime (the default lifetimes for a DBContext).</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="40bb2-187">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="40bb2-187">Additional resources</span></span>

-   <span data-ttu-id="40bb2-188">**Implementando os padrões de repositório e de unidade de trabalho em um aplicativo ASP.NET MVC**
    [*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)</span><span class="sxs-lookup"><span data-stu-id="40bb2-188">**Implementing the Repository and Unit of Work Patterns in an ASP.NET MVC Application**
[*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)</span></span>

-   <span data-ttu-id="40bb2-189">**Jonathan Allen. Implementation Strategies for the Repository Pattern with Entity Framework, Dapper, and Chain**
    [*https://www.infoq.com/articles/repository-implementation-strategies*](https://www.infoq.com/articles/repository-implementation-strategies) (Estratégias de implementação para o padrão de repositório com o Entity Framework, o Dapper e o Chain)</span><span class="sxs-lookup"><span data-stu-id="40bb2-189">**Jonathan Allen. Implementation Strategies for the Repository Pattern with Entity Framework, Dapper, and Chain**
[*https://www.infoq.com/articles/repository-implementation-strategies*](https://www.infoq.com/articles/repository-implementation-strategies)</span></span>

-   <span data-ttu-id="40bb2-190">**Cesar de la Torre. Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/) (Comparando os tempos de vida do serviço de contêiner de IoC do ASP.NET Core com os escopos de instância de contêiner de IoC do Autofac)</span><span class="sxs-lookup"><span data-stu-id="40bb2-190">**Cesar de la Torre. Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes**
[*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span></span>

## <a name="table-mapping"></a><span data-ttu-id="40bb2-191">Mapeamento de tabela</span><span class="sxs-lookup"><span data-stu-id="40bb2-191">Table mapping</span></span>

<span data-ttu-id="40bb2-192">O mapeamento de tabela identifica os dados de tabela a serem consultados e salvos no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="40bb2-192">Table mapping identifies the table data to be queried from and saved to the database.</span></span> <span data-ttu-id="40bb2-193">Você já viu como as entidades de domínio (por exemplo, um domínio de produto ou de pedido) podem ser usadas para gerar um esquema de banco de dados relacionado.</span><span class="sxs-lookup"><span data-stu-id="40bb2-193">Previously you saw how domain entities (for example, a product or order domain) can be used to generate a related database schema.</span></span> <span data-ttu-id="40bb2-194">O EF foi projetado rigidamente de acordo com o conceito de *convenções*.</span><span class="sxs-lookup"><span data-stu-id="40bb2-194">EF is strongly designed around the concept of *conventions*.</span></span> <span data-ttu-id="40bb2-195">As convenções abrangem perguntas como "Qual será o nome de uma tabela?"</span><span class="sxs-lookup"><span data-stu-id="40bb2-195">Conventions address questions like “What will the name of a table be?”</span></span> <span data-ttu-id="40bb2-196">ou "Qual propriedade é a chave primária?"</span><span class="sxs-lookup"><span data-stu-id="40bb2-196">or “What property is the primary key?”</span></span> <span data-ttu-id="40bb2-197">As convenções normalmente se baseiam nos nomes convencionais. Por exemplo, é comum que a chave primária seja uma propriedade que termine com Id.</span><span class="sxs-lookup"><span data-stu-id="40bb2-197">Conventions are typically based on conventional names—for example, it is typical for the primary key to be a property that ends with Id.</span></span>

<span data-ttu-id="40bb2-198">Por convenção, cada entidade será configurada para ser mapeada para uma tabela com o mesmo nome que a propriedade DbSet&lt;TEntity&gt; que expõe a entidade no contexto derivado.</span><span class="sxs-lookup"><span data-stu-id="40bb2-198">By convention, each entity will be set up to map to a table with the same name as the DbSet&lt;TEntity&gt; property that exposes the entity on the derived context.</span></span> <span data-ttu-id="40bb2-199">Se nenhum valor de DbSet&lt;TEntity&gt; for fornecido para a entidade especificada, o nome da classe será usado.</span><span class="sxs-lookup"><span data-stu-id="40bb2-199">If no DbSet&lt;TEntity&gt; value is provided for the given entity, the class name is used.</span></span>

### <a name="data-annotations-versus-fluent-api"></a><span data-ttu-id="40bb2-200">Anotações de dados em comparação com a API fluente</span><span class="sxs-lookup"><span data-stu-id="40bb2-200">Data Annotations versus Fluent API</span></span>

<span data-ttu-id="40bb2-201">Existem muitas convenções do EF Core adicionais e a maioria delas pode ser alterada usando anotações de dados ou a API fluente, implementada no método OnModelCreating.</span><span class="sxs-lookup"><span data-stu-id="40bb2-201">There are many additional EF Core conventions, and most of them can be changed by using either data annotations or Fluent API, implemented within the OnModelCreating method.</span></span>

<span data-ttu-id="40bb2-202">As anotações de dados devem ser usadas nas próprias classes de modelo de entidade, o que é uma maneira mais invasiva do ponto de vista de DDD.</span><span class="sxs-lookup"><span data-stu-id="40bb2-202">Data annotations must be used on the entity model classes themselves, which is a more intrusive way from a DDD point of view.</span></span> <span data-ttu-id="40bb2-203">Isso ocorre porque você está contaminando o modelo com anotações de dados relacionadas ao banco de dados de infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="40bb2-203">This is because you are contaminating your model with data annotations related to the infrastructure database.</span></span> <span data-ttu-id="40bb2-204">Por outro lado, a API fluente é uma maneira conveniente de alterar a maioria das convenções e dos mapeamentos dentro da camada de infraestrutura de persistência de dados, para que o modelo de entidade fique limpo e desacoplado da infraestrutura de persistência.</span><span class="sxs-lookup"><span data-stu-id="40bb2-204">On the other hand, Fluent API is a convenient way to change most conventions and mappings within your data persistence infrastructure layer, so the entity model will be clean and decoupled from the persistence infrastructure.</span></span>

### <a name="fluent-api-and-the-onmodelcreating-method"></a><span data-ttu-id="40bb2-205">API fluente e o método OnModelCreating</span><span class="sxs-lookup"><span data-stu-id="40bb2-205">Fluent API and the OnModelCreating method</span></span>

<span data-ttu-id="40bb2-206">Conforme mencionado, para alterar as convenções e os mapeamentos, você pode usar o método OnModelCreating na classe DbContext.</span><span class="sxs-lookup"><span data-stu-id="40bb2-206">As mentioned, in order to change conventions and mappings, you can use the OnModelCreating method in the DbContext class.</span></span> 

<span data-ttu-id="40bb2-207">O microsserviço de pedidos no eShopOnContainers implementa o mapeamento e configuração explícitos, quando necessário, conforme é mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="40bb2-207">The ordering microservice in eShopOnContainers implements explicit mapping and configuration, when needed, as shown in the following code.</span></span>

```csharp
// At OrderingContext.cs from eShopOnContainers
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
   // ...
   modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
   // Other entities’ configuration ...
}

// At OrderEntityTypeConfiguration.cs from eShopOnContainers
class OrderEntityTypeConfiguration : IEntityTypeConfiguration<Order>
{
    public void Configure(EntityTypeBuilder<Order> orderConfiguration)
    {
            orderConfiguration.ToTable("orders", OrderingContext.DEFAULT_SCHEMA);

            orderConfiguration.HasKey(o => o.Id);

            orderConfiguration.Ignore(b => b.DomainEvents);

            orderConfiguration.Property(o => o.Id)
                .ForSqlServerUseSequenceHiLo("orderseq", OrderingContext.DEFAULT_SCHEMA);

            //Address Value Object persisted as owned entity type supported since EF Core 2.0
            orderConfiguration.OwnsOne(o => o.Address);

            orderConfiguration.Property<DateTime>("OrderDate").IsRequired();
            orderConfiguration.Property<int?>("BuyerId").IsRequired(false);
            orderConfiguration.Property<int>("OrderStatusId").IsRequired();
            orderConfiguration.Property<int?>("PaymentMethodId").IsRequired(false);
            orderConfiguration.Property<string>("Description").IsRequired(false);

            var navigation = orderConfiguration.Metadata.FindNavigation(nameof(Order.OrderItems));
            
            // DDD Patterns comment:
            //Set as field (New since EF 1.1) to access the OrderItem collection property through its field
            navigation.SetPropertyAccessMode(PropertyAccessMode.Field);

            orderConfiguration.HasOne<PaymentMethod>()
                .WithMany()
                .HasForeignKey("PaymentMethodId")
                .IsRequired(false)
                .OnDelete(DeleteBehavior.Restrict);

            orderConfiguration.HasOne<Buyer>()
                .WithMany()
                .IsRequired(false)
                .HasForeignKey("BuyerId");

            orderConfiguration.HasOne(o => o.OrderStatus)
                .WithMany()
                .HasForeignKey("OrderStatusId");
    }
}
```

<span data-ttu-id="40bb2-208">É possível definir todos os mapeamentos da API fluente no mesmo método OnModelCreating, mas é recomendável particionar esse código e ter várias classes de configuração, uma por entidade, conforme é mostrado no exemplo.</span><span class="sxs-lookup"><span data-stu-id="40bb2-208">You could set all the Fluent API mappings within the same OnModelCreating method, but it is advisable to partition that code and have multiple configuration classes, one per entity, as shown in the example.</span></span> <span data-ttu-id="40bb2-209">Principalmente para modelos muito grandes, é recomendável ter classes de configuração separadas para configurar tipos de entidade diferentes.</span><span class="sxs-lookup"><span data-stu-id="40bb2-209">Especially for particularly large models, it is advisable to have separate configuration classes for configuring different entity types.</span></span>

<span data-ttu-id="40bb2-210">O código no exemplo mostra algumas declarações e mapeamentos explícitos.</span><span class="sxs-lookup"><span data-stu-id="40bb2-210">The code in the example shows a few explicit declarations and mapping.</span></span> <span data-ttu-id="40bb2-211">No entanto, as convenções do EF Core fazem muitos desses mapeamentos automaticamente, portanto, o código real necessário para o seu caso poderá ser menor.</span><span class="sxs-lookup"><span data-stu-id="40bb2-211">However, EF Core conventions do many of those mappings automatically, so the actual code you would need in your case might be smaller.</span></span>


### <a name="the-hilo-algorithm-in-ef-core"></a><span data-ttu-id="40bb2-212">O algoritmo Hi/Lo no EF Core</span><span class="sxs-lookup"><span data-stu-id="40bb2-212">The Hi/Lo algorithm in EF Core</span></span>

<span data-ttu-id="40bb2-213">Um aspecto interessante de código no exemplo anterior é que ele usa o [algoritmo Hi/Lo](https://vladmihalcea.com/the-hilo-algorithm/) como a estratégia de geração de chave.</span><span class="sxs-lookup"><span data-stu-id="40bb2-213">An interesting aspect of code in the preceding example is that it uses the [Hi/Lo algorithm](https://vladmihalcea.com/the-hilo-algorithm/) as the key generation strategy.</span></span>

<span data-ttu-id="40bb2-214">O algoritmo Hi/Lo é útil quando você precisa de chaves exclusivas.</span><span class="sxs-lookup"><span data-stu-id="40bb2-214">The Hi/Lo algorithm is useful when you need unique keys.</span></span> <span data-ttu-id="40bb2-215">Em resumo, o algoritmo Hi-Lo atribui identificadores exclusivos às linhas da tabela, embora ele não dependa de armazenar a linha no banco de dados imediatamente.</span><span class="sxs-lookup"><span data-stu-id="40bb2-215">As a summary, the Hi-Lo algorithm assigns unique identifiers to table rows while not depending on storing the row in the database immediately.</span></span> <span data-ttu-id="40bb2-216">Isso permite começar a usar os identificadores imediatamente, como acontece com as IDs de banco de dados sequenciais regulares.</span><span class="sxs-lookup"><span data-stu-id="40bb2-216">This lets you start using the identifiers right away, as happens with regular sequential database IDs.</span></span>

<span data-ttu-id="40bb2-217">O algoritmo Hi/Lo descreve um mecanismo para gerar IDs seguras no lado do cliente e não no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="40bb2-217">The Hi/Lo algorithm describes a mechanism for generating safe IDs on the client side rather than in the database.</span></span> <span data-ttu-id="40bb2-218">*Segurança* neste contexto significa sem colisões.</span><span class="sxs-lookup"><span data-stu-id="40bb2-218">*Safe* in this context means without collisions.</span></span> <span data-ttu-id="40bb2-219">Esse algoritmo é interessante por estes motivos:</span><span class="sxs-lookup"><span data-stu-id="40bb2-219">This algorithm is interesting for these reasons:</span></span>

-   <span data-ttu-id="40bb2-220">Ele não interrompe o padrão de unidade de trabalho.</span><span class="sxs-lookup"><span data-stu-id="40bb2-220">It does not break the Unit of Work pattern.</span></span>

-   <span data-ttu-id="40bb2-221">Ele não requer viagens de ida e volta como os geradores de sequência em outros DBMSs (gerenciadores de banco de dados).</span><span class="sxs-lookup"><span data-stu-id="40bb2-221">It does not require round trips the way sequence generators do in other DBMSs.</span></span>

-   <span data-ttu-id="40bb2-222">Ele gera um identificador legível por pessoas, ao contrário das técnicas que usam GUIDs.</span><span class="sxs-lookup"><span data-stu-id="40bb2-222">It generates a human readable identifier, unlike techniques that use GUIDs.</span></span>

<span data-ttu-id="40bb2-223">O EF Core é compatível com o [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) com o método ForSqlServerUseSequenceHiLo, conforme foi mostrado no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="40bb2-223">EF Core supports [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) with the ForSqlServerUseSequenceHiLo method, as shown in the preceding example.</span></span>

### <a name="mapping-fields-instead-of-properties"></a><span data-ttu-id="40bb2-224">Mapeamento de campos em vez de propriedades</span><span class="sxs-lookup"><span data-stu-id="40bb2-224">Mapping fields instead of properties</span></span>

<span data-ttu-id="40bb2-225">Com esse recurso, disponível desde o EF Core 1.1, você pode mapear colunas para campos diretamente.</span><span class="sxs-lookup"><span data-stu-id="40bb2-225">With this feature, available since EF Core 1.1, you can directly map columns to fields.</span></span> <span data-ttu-id="40bb2-226">É possível não usar as propriedades na classe de entidade e apenas mapear as colunas de uma tabela para os campos.</span><span class="sxs-lookup"><span data-stu-id="40bb2-226">It is possible to not use properties in the entity class, and just to map columns from a table to fields.</span></span> <span data-ttu-id="40bb2-227">Um caso de uso comum para isso seria os campos privados de algum estado interno que não precisam ser acessados de fora da entidade.</span><span class="sxs-lookup"><span data-stu-id="40bb2-227">A common use for that would be private fields for any internal state that do not need to be accessed from outside the entity.</span></span> 

<span data-ttu-id="40bb2-228">Você pode fazer isso com campos únicos ou também com coleções, como um campo `List<>`.</span><span class="sxs-lookup"><span data-stu-id="40bb2-228">You can do this with single fields or also with collections, like a `List<>` field.</span></span> <span data-ttu-id="40bb2-229">Esse ponto já foi mencionado quando discutimos a modelagem das classes de modelo de domínio, mas aqui você pode ver como esse mapeamento é realizado com a configuração `PropertyAccessMode.Field` realçada no código anterior.</span><span class="sxs-lookup"><span data-stu-id="40bb2-229">This point was mentioned earlier when we discussed modeling the domain model classes, but here you can see how that mapping is performed with the `PropertyAccessMode.Field` configuration highlighted in the previous code.</span></span>

### <a name="using-shadow-properties-in-ef-core-hidden-at-the-infrastructure-level"></a><span data-ttu-id="40bb2-230">Usando propriedades de sombra no EF Core, ocultas no nível da infraestrutura</span><span class="sxs-lookup"><span data-stu-id="40bb2-230">Using shadow properties in EF Core, hidden at the infrastructure level</span></span>

<span data-ttu-id="40bb2-231">As propriedades de sombra no EF Core são propriedades que não existem no modelo de classe de entidade.</span><span class="sxs-lookup"><span data-stu-id="40bb2-231">Shadow properties in EF Core are properties that do not exist in your entity class model.</span></span> <span data-ttu-id="40bb2-232">Os valores e os estados dessas propriedades são mantidos unicamente na classe [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) no nível da infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="40bb2-232">The values and states of these properties are maintained purely in the [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) class at the infrastructure level.</span></span>


## <a name="implementing-the-specification-pattern"></a><span data-ttu-id="40bb2-233">Implementando o padrão de especificação</span><span class="sxs-lookup"><span data-stu-id="40bb2-233">Implementing the Specification pattern</span></span>

<span data-ttu-id="40bb2-234">Conforme já foi apresentado na seção sobre design, o padrão de especificação (o nome completo é padrão de especificação de consulta) é um padrão de design orientado por domínio projetado para ser o local em que você pode colocar a definição de uma consulta com uma lógica opcional de classificação e paginação.</span><span class="sxs-lookup"><span data-stu-id="40bb2-234">As introduced earlier in the design section, the Specification pattern (its full name would be Query-specification pattern) is a Domain-Driven Design pattern designed as the place where you can put the definition of a query with optional sorting and paging logic.</span></span> <span data-ttu-id="40bb2-235">O padrão de especificação define uma consulta em um objeto.</span><span class="sxs-lookup"><span data-stu-id="40bb2-235">The Specification pattern defines a query in an object.</span></span> <span data-ttu-id="40bb2-236">Por exemplo, para encapsular uma consulta paginada que procura por alguns produtos, você poderia criar uma especificação PagedProduct que usasse os parâmetros de entrada necessários (pageNumber, pageSize, filtro, etc.).</span><span class="sxs-lookup"><span data-stu-id="40bb2-236">For example, in order to encapsulate a paged query that searches for some products you can create a PagedProduct specification that takes the necessary input parameters (pageNumber, pageSize, filter, etc.).</span></span> <span data-ttu-id="40bb2-237">Assim, qualquer método de repositório [geralmente uma sobrecarga List()] aceitaria uma ISpecification e executaria a consulta esperada com base nessa especificação.</span><span class="sxs-lookup"><span data-stu-id="40bb2-237">Then, any Repository’s method (usually a List() overload) would accept an ISpecification and run the expected query based on that specification.</span></span>

<span data-ttu-id="40bb2-238">Um exemplo de uma interface de especificação genérica é o código a seguir de [eShopOnweb](https://github.com/dotnet-architecture/eShopOnWeb).</span><span class="sxs-lookup"><span data-stu-id="40bb2-238">An example of a generic Specification interface is the following code from [eShopOnweb](https://github.com/dotnet-architecture/eShopOnWeb).</span></span> 

```csharp
// GENERIC SPECIFICATION INTERFACE
// https://github.com/dotnet-architecture/eShopOnWeb 

public interface ISpecification<T>
{
    Expression<Func<T, bool>> Criteria { get; }
    List<Expression<Func<T, object>>> Includes { get; }
    List<string> IncludeStrings { get; }
}
```

<span data-ttu-id="40bb2-239">Assim, a implementação de uma classe base de especificação genérica seria a seguinte.</span><span class="sxs-lookup"><span data-stu-id="40bb2-239">Then, the implementation of a generic specification base class is the following.</span></span>

```csharp
// GENERIC SPECIFICATION IMPLEMENTATION (BASE CLASS)
// https://github.com/dotnet-architecture/eShopOnWeb
 
public abstract class BaseSpecification<T> : ISpecification<T>
{
    public BaseSpecification(Expression<Func<T, bool>> criteria)
    {
        Criteria = criteria;
    }
    public Expression<Func<T, bool>> Criteria { get; }

    public List<Expression<Func<T, object>>> Includes { get; } = 
                                           new List<Expression<Func<T, object>>>();

    public List<string> IncludeStrings { get; } = new List<string>();
 
    protected virtual void AddInclude(Expression<Func<T, object>> includeExpression)
    {
        Includes.Add(includeExpression);
    }
    
    // string-based includes allow for including children of children
    // e.g. Basket.Items.Product
    protected virtual void AddInclude(string includeString)
    {
        IncludeStrings.Add(includeString);
    }
}
```

<span data-ttu-id="40bb2-240">A seguinte especificação carrega uma única entidade de cesta de compras de acordo com a ID da cesta de compras ou com a ID do comprador ao qual a cesta de compras pertence.</span><span class="sxs-lookup"><span data-stu-id="40bb2-240">The following specification loads a single basket entity given either the basket’s ID or the ID of the buyer to whom the basket belongs.</span></span> <span data-ttu-id="40bb2-241">Isso fará o [carregamento adiantado](https://docs.microsoft.com/en-us/ef/core/querying/related-data) da coleção de itens da cesta de compras.</span><span class="sxs-lookup"><span data-stu-id="40bb2-241">It will [eager load](https://docs.microsoft.com/en-us/ef/core/querying/related-data) the basket’s Items collection.</span></span>

```csharp
// SAMPLE QUERY SPECIFICATION IMPLEMENTATION

public class BasketWithItemsSpecification : BaseSpecification<Basket>
{
    public BasketWithItemsSpecification(int basketId)
        : base(b => b.Id == basketId)
    {
        AddInclude(b => b.Items);
    }
    public BasketWithItemsSpecification(string buyerId)
        : base(b => b.BuyerId == buyerId)
    {
        AddInclude(b => b.Items);
    }
}
```

<span data-ttu-id="40bb2-242">E, finalmente, veja abaixo como um repositório do EF genérico pode usar uma especificação desse tipo para filtrar e fazer o carregamento adiantado dos dados relacionados a um determinado tipo de entidade T.</span><span class="sxs-lookup"><span data-stu-id="40bb2-242">And finally, you can see below how a generic EF Repository can use such a specification to filter and eager-load data related to a given entity type T.</span></span>

```csharp
// GENERIC EF REPOSITORY WITH SPECIFICATION
// https://github.com/dotnet-architecture/eShopOnWeb

public IEnumerable<T> List(ISpecification<T> spec)
{
    // fetch a Queryable that includes all expression-based includes
    var queryableResultWithIncludes = spec.Includes
        .Aggregate(_dbContext.Set<T>().AsQueryable(),
            (current, include) => current.Include(include));
 
    // modify the IQueryable to include any string-based include statements
    var secondaryResult = spec.IncludeStrings
        .Aggregate(queryableResultWithIncludes,
            (current, include) => current.Include(include));
 
    // return the result of the query using the specification's criteria expression
    return secondaryResult
                    .Where(spec.Criteria)
                    .AsEnumerable();
}
```
<span data-ttu-id="40bb2-243">Além de encapsular a lógica de filtragem, a especificação pode especificar a forma dos dados a serem retornados, incluindo quais propriedades devem ser populadas.</span><span class="sxs-lookup"><span data-stu-id="40bb2-243">In addition to encapsulating filtering logic, the specification can specify the shape of the data to be returned, including which properties to populate.</span></span> 

<span data-ttu-id="40bb2-244">Embora não seja recomendado retornar IQueryable de um repositório, é perfeitamente normal usá-lo no repositório para criar um conjunto de resultados.</span><span class="sxs-lookup"><span data-stu-id="40bb2-244">Although we don't recommended to return IQueryable from a repository, it’s perfectly fine to use them within the repository to build up a set of results.</span></span> <span data-ttu-id="40bb2-245">Veja essa abordagem usada no método List acima, que usa expressões de IQueryable intermediárias para criar a lista de inclusões da consulta antes de executar a consulta com os critérios da especificação na última linha.</span><span class="sxs-lookup"><span data-stu-id="40bb2-245">You can see this approach used in the List method above, which uses intermediate IQueryable expressions to build up the query’s list of includes before executing the query with the specification’s criteria on the last line.</span></span>


#### <a name="additional-resources"></a><span data-ttu-id="40bb2-246">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="40bb2-246">Additional resources</span></span>

-   <span data-ttu-id="40bb2-247">**Mapeamento de tabela**
    [*https://docs.microsoft.com/ef/core/modeling/relational/tables*](https://docs.microsoft.com/ef/core/modeling/relational/tables)</span><span class="sxs-lookup"><span data-stu-id="40bb2-247">**Table Mapping**
[*https://docs.microsoft.com/ef/core/modeling/relational/tables*](https://docs.microsoft.com/ef/core/modeling/relational/tables)</span></span>

-   <span data-ttu-id="40bb2-248">**Use HiLo to generate keys with Entity Framework Core**
    [*http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/*](http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/) (Usar o HiLo para gerar chaves com o Entity Framework Core)</span><span class="sxs-lookup"><span data-stu-id="40bb2-248">**Use HiLo to generate keys with Entity Framework Core**
[*http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/*](http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/)</span></span>

-   <span data-ttu-id="40bb2-249">**Campos de backup**
    [*https://docs.microsoft.com/ef/core/modeling/backing-field*](https://docs.microsoft.com/ef/core/modeling/backing-field)</span><span class="sxs-lookup"><span data-stu-id="40bb2-249">**Backing Fields**
[*https://docs.microsoft.com/ef/core/modeling/backing-field*](https://docs.microsoft.com/ef/core/modeling/backing-field)</span></span>

-   <span data-ttu-id="40bb2-250">**Steve Smith. Encapsulated Collections in Entity Framework Core**
    [*https://ardalis.com/encapsulated-collections-in-entity-framework-core*](https://ardalis.com/encapsulated-collections-in-entity-framework-core) (Coleções encapsuladas no Entity Framework Core)</span><span class="sxs-lookup"><span data-stu-id="40bb2-250">**Steve Smith. Encapsulated Collections in Entity Framework Core**
[*https://ardalis.com/encapsulated-collections-in-entity-framework-core*](https://ardalis.com/encapsulated-collections-in-entity-framework-core)</span></span>

-   <span data-ttu-id="40bb2-251">**Propriedades de sombra**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span><span class="sxs-lookup"><span data-stu-id="40bb2-251">**Shadow Properties**
[*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span></span>

-   <span data-ttu-id="40bb2-252">**The Specification pattern**
    [*http://deviq.com/specification-pattern/*](http://deviq.com/specification-pattern/) (O padrão de especificação)</span><span class="sxs-lookup"><span data-stu-id="40bb2-252">**The Specification pattern**
[*http://deviq.com/specification-pattern/*](http://deviq.com/specification-pattern/)</span></span>
    

>[!div class="step-by-step"]
<span data-ttu-id="40bb2-253">[Anterior](infrastructure-persistence-layer-design.md)
[Próximo](nosql-database-persistence-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="40bb2-253">[Previous](infrastructure-persistence-layer-design.md)
[Next](nosql-database-persistence-infrastructure.md)</span></span>
