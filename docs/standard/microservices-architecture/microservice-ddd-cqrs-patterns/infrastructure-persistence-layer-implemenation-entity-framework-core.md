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
# <a name="implementing-the-infrastructure-persistence-layer-with-entity-framework-core"></a><span data-ttu-id="1ac94-104">Implementando a camada de persistência de infraestrutura com o Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="1ac94-104">Implementing the infrastructure persistence layer with Entity Framework Core</span></span>

<span data-ttu-id="1ac94-105">Quando você usa os bancos de dados relacionais, como o SQL Server, Oracle ou PostgreSQL, uma abordagem recomendada é implementar a camada de persistência com base no Entity Framework (EF).</span><span class="sxs-lookup"><span data-stu-id="1ac94-105">When you use relational databases such as SQL Server, Oracle, or PostgreSQL, a recommended approach is to implement the persistence layer based on Entity Framework (EF).</span></span> <span data-ttu-id="1ac94-106">EF dá suporte a LINQ e fornece objetos fortemente tipados para seu modelo, bem como persistência simplificada em seu banco de dados.</span><span class="sxs-lookup"><span data-stu-id="1ac94-106">EF supports LINQ and provides strongly typed objects for your model, as well as simplified persistence into your database.</span></span>

<span data-ttu-id="1ac94-107">Entity Framework tem uma longa história como parte do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1ac94-107">Entity Framework has a long history as part of the .NET Framework.</span></span> <span data-ttu-id="1ac94-108">Quando você usa o .NET Core, você também deve usar o Entity Framework Core, que é executado no Windows ou Linux da mesma maneira como o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1ac94-108">When you use .NET Core, you should also use Entity Framework Core, which runs on Windows or Linux in the same way as .NET Core.</span></span> <span data-ttu-id="1ac94-109">EF Core é uma regravação completa do Entity Framework, implementado com muito menos espaço e importantes melhorias no desempenho.</span><span class="sxs-lookup"><span data-stu-id="1ac94-109">EF Core is a complete rewrite of Entity Framework, implemented with a much smaller footprint and important improvements in performance.</span></span>

## <a name="introduction-to-entity-framework-core"></a><span data-ttu-id="1ac94-110">Introdução ao Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="1ac94-110">Introduction to Entity Framework Core</span></span>

<span data-ttu-id="1ac94-111">Núcleo do Entity Framework (EF) é leve e extensível, e tecnologia de acesso de versão de plataforma cruzada dos dados do Entity Framework populares.</span><span class="sxs-lookup"><span data-stu-id="1ac94-111">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="1ac94-112">Ele foi introduzido com o núcleo do .NET em meados de 2016.</span><span class="sxs-lookup"><span data-stu-id="1ac94-112">It was introduced with .NET Core in mid-2016.</span></span>

<span data-ttu-id="1ac94-113">Como uma introdução ao EF Core já está disponível na documentação da Microsoft, aqui é simplesmente fornecem links para informações.</span><span class="sxs-lookup"><span data-stu-id="1ac94-113">Since an introduction to EF Core is already available in Microsoft documentation, here we simply provide links to that information.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="1ac94-114">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="1ac94-114">Additional resources</span></span>

-   <span data-ttu-id="1ac94-115">**Entity Framework Core**
    [*https://docs.microsoft.com/ef/core/*](https://docs.microsoft.com/ef/core/)</span><span class="sxs-lookup"><span data-stu-id="1ac94-115">**Entity Framework Core**
[*https://docs.microsoft.com/ef/core/*](https://docs.microsoft.com/ef/core/)</span></span>

-   <span data-ttu-id="1ac94-116">**Introdução ao ASP.NET Core e o Entity Framework Core usando o Visual Studio**
    [*https://docs.microsoft.com/aspnet/core/data/ef-mvc/*](https://docs.microsoft.com/aspnet/core/data/ef-mvc/)</span><span class="sxs-lookup"><span data-stu-id="1ac94-116">**Getting started with ASP.NET Core and Entity Framework Core using Visual Studio**
[*https://docs.microsoft.com/aspnet/core/data/ef-mvc/*](https://docs.microsoft.com/aspnet/core/data/ef-mvc/)</span></span>

-   <span data-ttu-id="1ac94-117">**Classe DbContext**
    [*https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext*](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext)</span><span class="sxs-lookup"><span data-stu-id="1ac94-117">**DbContext Class**
[*https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext*](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext)</span></span>

-   <span data-ttu-id="1ac94-118">**Comparar EF Core & EF6.x**
    [*https://docs.microsoft.com/ef/efcore-and-ef6/index*](https://docs.microsoft.com/ef/efcore-and-ef6/index)</span><span class="sxs-lookup"><span data-stu-id="1ac94-118">**Compare EF Core & EF6.x**
[*https://docs.microsoft.com/ef/efcore-and-ef6/index*](https://docs.microsoft.com/ef/efcore-and-ef6/index)</span></span>

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a><span data-ttu-id="1ac94-119">Infraestrutura no Entity Framework Core de uma perspectiva DDD</span><span class="sxs-lookup"><span data-stu-id="1ac94-119">Infrastructure in Entity Framework Core from a DDD perspective</span></span>

<span data-ttu-id="1ac94-120">Do ponto de vista do DDD, um recurso importante do EF é a capacidade de usar as entidades de domínio POCO, também chamadas de terminologia EF como POCO *primeiro código entidades*.</span><span class="sxs-lookup"><span data-stu-id="1ac94-120">From a DDD point of view, an important capability of EF is the ability to use POCO domain entities, also known in EF terminology as POCO *code-first entities*.</span></span> <span data-ttu-id="1ac94-121">Se você usar as entidades POCO domínio, as classes de modelo de domínio são persistência desconhecem, seguindo o [ignorância de persistência](http://deviq.com/persistence-ignorance/) e [infraestrutura ignorância](https://ayende.com/blog/3137/infrastructure-ignorance) princípios.</span><span class="sxs-lookup"><span data-stu-id="1ac94-121">If you use POCO domain entities, your domain model classes are persistence-ignorant, following the [Persistence Ignorance](http://deviq.com/persistence-ignorance/) and the [Infrastructure Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance) principles.</span></span>

<span data-ttu-id="1ac94-122">Por padrões DDD encapsulam o regras dentro da classe de entidade em si e o comportamento do domínio, assim ele pode controlar invariáveis, validações e regras ao acessar de qualquer coleção.</span><span class="sxs-lookup"><span data-stu-id="1ac94-122">Per DDD patterns, you should encapsulate domain behavior and rules within the entity class itself, so it can control invariants, validations, and rules when accessing any collection.</span></span> <span data-ttu-id="1ac94-123">Portanto, não é uma prática recomendada no DDD para permitir acesso público a coleções de filho entidades ou objetos de valor.</span><span class="sxs-lookup"><span data-stu-id="1ac94-123">Therefore, it is not a good practice in DDD to allow public access to collections of child entities or value objects.</span></span> <span data-ttu-id="1ac94-124">Em vez disso, você deseja expor métodos que controlam como e quando suas coleções de propriedade e os campos podem ser atualizadas, e o comportamento e as ações que devem ocorrer quando isso acontece.</span><span class="sxs-lookup"><span data-stu-id="1ac94-124">Instead, you want to expose methods that control how and when your fields and property collections can be updated, and what behavior and actions should occur when that happens.</span></span>

<span data-ttu-id="1ac94-125">No EF Core 1.1, para atender a esses requisitos DDD você pode ter campos simples em suas entidades em vez de propriedades com setters públicas e privadas.</span><span class="sxs-lookup"><span data-stu-id="1ac94-125">In EF Core 1.1, to satisfy those DDD requirements you can have plain fields in your entities instead of properties with public and private setters.</span></span> <span data-ttu-id="1ac94-126">Se você não quiser que um campo de entidade para ser acessível externamente, você pode criar apenas o campo em vez de uma propriedade ou atributo.</span><span class="sxs-lookup"><span data-stu-id="1ac94-126">If you do not want an entity field to be externally accessible, you can just create the attribute or field instead of a property.</span></span> <span data-ttu-id="1ac94-127">Não é necessário usar setters particulares, se você preferir essa abordagem de limpeza.</span><span class="sxs-lookup"><span data-stu-id="1ac94-127">There is no need to use private setters if you prefer this cleaner approach.</span></span>

<span data-ttu-id="1ac94-128">De maneira semelhante, agora você pode ter acesso somente leitura para coleções usando uma propriedade pública tipo IEnumerable&lt;T&gt;, que é apoiado por um membro do campo particular para a coleção (como uma lista&lt;&gt;) no seu entidade que se baseia no EF para persistência.</span><span class="sxs-lookup"><span data-stu-id="1ac94-128">In a similar way, you can now have read-only access to collections by using a public property typed as IEnumerable&lt;T&gt;, which is backed by a private field member for the collection (like a List&lt;&gt;) in your entity that relies on EF for persistence.</span></span> <span data-ttu-id="1ac94-129">Versões anteriores do Entity Framework necessário propriedades de coleção para dar suporte a ICollection&lt;T&gt;, que significa que qualquer desenvolvedor usando a classe da entidade pai pode adicionar ou remover itens de suas coleções de propriedade.</span><span class="sxs-lookup"><span data-stu-id="1ac94-129">Previous versions of Entity Framework required collection properties to support ICollection&lt;T&gt;, which meant that any developer using the parent entity class could add or remove items from its property collections.</span></span> <span data-ttu-id="1ac94-130">Essa possibilidade seria contra os padrões recomendados DDD.</span><span class="sxs-lookup"><span data-stu-id="1ac94-130">That possibility would be against the recommended patterns in DDD.</span></span>

<span data-ttu-id="1ac94-131">Você pode usar uma coleção privada durante a exposição de um objeto IEnumerable somente leitura, conforme mostrado no exemplo de código a seguir:</span><span class="sxs-lookup"><span data-stu-id="1ac94-131">You can use a private collection while exposing a read-only IEnumerable object, as shown in the following code example:</span></span>

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

<span data-ttu-id="1ac94-132">Observe que a propriedade OrderItems só pode ser acessada como somente leitura usando a lista&lt;&gt;. AsReadOnly().</span><span class="sxs-lookup"><span data-stu-id="1ac94-132">Note that the OrderItems property can only be accessed as read-only using List&lt;&gt;.AsReadOnly().</span></span> <span data-ttu-id="1ac94-133">Esse método cria um wrapper de somente leitura ao redor da lista particular para que ele está protegido contra atualizações externas.</span><span class="sxs-lookup"><span data-stu-id="1ac94-133">This method creates a read-only wrapper around the private list so that it is protected against external updates.</span></span> <span data-ttu-id="1ac94-134">É muito mais barato do que usando o método ToList, porque ele não precisa copiar todos os itens em uma nova coleção; em vez disso, ele executa apenas uma operação de alocação de heap para a instância do wrapper.</span><span class="sxs-lookup"><span data-stu-id="1ac94-134">It is much cheaper than using the ToList method, because it does not have to copy all the items in a new collection; instead, it performs just one heap alloc operation for the wrapper instance.</span></span>

<span data-ttu-id="1ac94-135">EF Core fornece uma maneira para mapear o modelo de domínio para o banco de dados físico sem contaminação por modelo de domínio.</span><span class="sxs-lookup"><span data-stu-id="1ac94-135">EF Core provides a way to map the domain model to the physical database without contaminating the domain model.</span></span> <span data-ttu-id="1ac94-136">É .NET POCO código puro, pois a ação de mapeamento é implementada na camada de persistência.</span><span class="sxs-lookup"><span data-stu-id="1ac94-136">It is pure .NET POCO code, because the mapping action is implemented in the persistence layer.</span></span> <span data-ttu-id="1ac94-137">Em ação esse mapeamento, você precisa configurar o mapeamento de campos no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="1ac94-137">In that mapping action, you need to configure the fields-to-database mapping.</span></span> <span data-ttu-id="1ac94-138">No exemplo a seguir de um método OnModelCreating, o código realçado informa EF principal para acessar a propriedade OrderItems por meio do seu campo.</span><span class="sxs-lookup"><span data-stu-id="1ac94-138">In the following example of an OnModelCreating method, the highlighted code tells EF Core to access the OrderItems property through its field.</span></span>

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

<span data-ttu-id="1ac94-139">Quando você usa campos em vez de propriedades, a entidade ItemPedido é mantida como se tivesse uma lista&lt;ItemPedido&gt; propriedade.</span><span class="sxs-lookup"><span data-stu-id="1ac94-139">When you use fields instead of properties, the OrderItem entity is persisted just as if it had a List&lt;OrderItem&gt; property.</span></span> <span data-ttu-id="1ac94-140">No entanto, ela expõe um único acessador (o método AddOrderItem) para adicionar novos itens na ordem.</span><span class="sxs-lookup"><span data-stu-id="1ac94-140">However, it exposes a single accessor (the AddOrderItem method) for adding new items to the order.</span></span> <span data-ttu-id="1ac94-141">Como resultado, comportamento e os dados são vinculados e sejam consistentes em toda a qualquer código de aplicativo que usa o modelo de domínio.</span><span class="sxs-lookup"><span data-stu-id="1ac94-141">As a result, behavior and data are tied together and will be consistent throughout any application code that uses the domain model.</span></span>

## <a name="implementing-custom-repositories-with-entity-framework-core"></a><span data-ttu-id="1ac94-142">Implementação de repositórios personalizados com o Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="1ac94-142">Implementing custom repositories with Entity Framework Core</span></span>

<span data-ttu-id="1ac94-143">No nível de implementação, um repositório é simplesmente uma classe com o código de persistência de dados coordenada por uma unidade de trabalho (DBContext no núcleo do EF) ao executar atualizações, como mostra a seguinte classe:</span><span class="sxs-lookup"><span data-stu-id="1ac94-143">At the implementation level, a repository is simply a class with data persistence code coordinated by a unit of work (DBContext in EF Core) when performing updates, as shown in the following class:</span></span>

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

<span data-ttu-id="1ac94-144">Observe que a interface IBuyerRepository vem da camada de modelo de domínio.</span><span class="sxs-lookup"><span data-stu-id="1ac94-144">Note that the IBuyerRepository interface comes from the domain model layer.</span></span> <span data-ttu-id="1ac94-145">No entanto, a implementação do repositório é feita na camada de infraestrutura e persistência.</span><span class="sxs-lookup"><span data-stu-id="1ac94-145">However, the repository implementation is done at the persistence and infrastructure layer.</span></span>

<span data-ttu-id="1ac94-146">O EF DbContext fornecido por meio do construtor injeção de dependência.</span><span class="sxs-lookup"><span data-stu-id="1ac94-146">The EF DbContext comes through the constructor through Dependency Injection.</span></span> <span data-ttu-id="1ac94-147">Ele é compartilhado entre vários repositórios de dentro do mesmo escopo de solicitação HTTP, graças ao seu tempo de vida padrão (ServiceLifetime.Scoped) no contêiner IoC (que também pode ser explicitamente definido com os serviços. AddDbContext&lt;&gt;).</span><span class="sxs-lookup"><span data-stu-id="1ac94-147">It is shared between multiple repositories within the same HTTP request scope, thanks to its default lifetime (ServiceLifetime.Scoped) in the IoC container (which can also be explicitly set with services.AddDbContext&lt;&gt;).</span></span>

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a><span data-ttu-id="1ac94-148">Métodos para implementar em um repositório (transações versus consultas ou atualizações)</span><span class="sxs-lookup"><span data-stu-id="1ac94-148">Methods to implement in a repository (updates or transactions versus queries)</span></span>

<span data-ttu-id="1ac94-149">Em cada classe de repositório, você deve colocar os métodos de persistência que atualizar o estado de entidades contidas por seu agregação relacionada.</span><span class="sxs-lookup"><span data-stu-id="1ac94-149">Within each repository class, you should put the persistence methods that update the state of entities contained by its related aggregate.</span></span> <span data-ttu-id="1ac94-150">Lembre-se de que há uma relação um para um entre uma agregação e seu repositório relacionado.</span><span class="sxs-lookup"><span data-stu-id="1ac94-150">Remember there is one-to-one relationship between an aggregate and its related repository.</span></span> <span data-ttu-id="1ac94-151">Leve em consideração que um objeto de entidade raiz agregada pode ter inserido entidades filhas dentro de seu gráfico EF.</span><span class="sxs-lookup"><span data-stu-id="1ac94-151">Take into account that an aggregate root entity object might have embedded child entities within its EF graph.</span></span> <span data-ttu-id="1ac94-152">Por exemplo, um comprador pode ter vários métodos de pagamento como entidades filho relacionados.</span><span class="sxs-lookup"><span data-stu-id="1ac94-152">For example, a buyer might have multiple payment methods as related child entities.</span></span>

<span data-ttu-id="1ac94-153">Como a abordagem para o pedido microsserviço em eShopOnContainers também se baseia em CQS/CQRS, a maioria das consultas não é implementadas no repositórios personalizados.</span><span class="sxs-lookup"><span data-stu-id="1ac94-153">Since the approach for the ordering microservice in eShopOnContainers is also based on CQS/CQRS, most of the queries are not implemented in custom repositories.</span></span> <span data-ttu-id="1ac94-154">Os desenvolvedores têm a liberdade de criar as consultas e junções que eles precisam para a camada de apresentação sem as restrições impostas pela agregações, os repositórios personalizados por agregação e DDD em geral.</span><span class="sxs-lookup"><span data-stu-id="1ac94-154">Developers have the freedom to create the queries and joins they need for the presentation layer without the restrictions imposed by aggregates, custom repositories per aggregate, and DDD in general.</span></span> <span data-ttu-id="1ac94-155">A maioria dos repositórios personalizados sugeridos por este guia tem vários update ou métodos transacionais, mas apenas os métodos de consulta necessário obter os dados a serem atualizados.</span><span class="sxs-lookup"><span data-stu-id="1ac94-155">Most of the custom repositories suggested by this guide have several update or transactional methods but just the query methods needed to get data to be updated.</span></span> <span data-ttu-id="1ac94-156">Por exemplo, o repositório BuyerRepository implementa um método FindAsync, porque o aplicativo precisa saber se um cliente específico existe antes de criar um novo comprador relacionado à ordem de.</span><span class="sxs-lookup"><span data-stu-id="1ac94-156">For example, the BuyerRepository repository implements a FindAsync method, because the application needs to know whether a particular buyer exists before creating a new buyer related to the order.</span></span>

<span data-ttu-id="1ac94-157">No entanto, os métodos de consulta real para obter dados para enviar para os aplicativos de cliente ou de camada de apresentação são implementados, conforme mencionado, nas consultas a CQRS com base em consultas flexíveis usando Dapper.</span><span class="sxs-lookup"><span data-stu-id="1ac94-157">However, the real query methods to get data to send to the presentation layer or client apps are implemented, as mentioned, in the CQRS queries based on flexible queries using Dapper.</span></span>

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a><span data-ttu-id="1ac94-158">Usando um repositório personalizado em vez de diretamente usando o EF DbContext</span><span class="sxs-lookup"><span data-stu-id="1ac94-158">Using a custom repository versus using EF DbContext directly</span></span>

<span data-ttu-id="1ac94-159">A classe DbContext do Entity Framework baseia-se nos padrões de unidade de trabalho e do repositório e pode ser usada diretamente no seu código, como de um controlador MVC do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="1ac94-159">The Entity Framework DbContext class is based on the Unit of Work and Repository patterns, and can be used directly from your code, such as from an ASP.NET Core MVC controller.</span></span> <span data-ttu-id="1ac94-160">Que é a maneira como você pode criar o código mais simples, como o microsserviço de catálogo CRUD em eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="1ac94-160">That is the way you can create the simplest code, as in the CRUD catalog microservice in eShopOnContainers.</span></span> <span data-ttu-id="1ac94-161">Em casos onde você deseja o código mais simples possível, você talvez queira diretamente, use a classe DbContext, assim como muitos desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="1ac94-161">In cases where you want the simplest code possible, you might want to directly use the DbContext class, as many developers do.</span></span>

<span data-ttu-id="1ac94-162">No entanto, a implementação de repositórios personalizados oferece vários benefícios ao implementar mais complexa microservices ou aplicativos.</span><span class="sxs-lookup"><span data-stu-id="1ac94-162">However, implementing custom repositories provides several benefits when implementing more complex microservices or applications.</span></span> <span data-ttu-id="1ac94-163">Os padrões de unidade de trabalho e repositório destinam-se para encapsular a camada de persistência de infraestrutura para que ele será desacoplado do aplicativo e camadas do modelo de domínio.</span><span class="sxs-lookup"><span data-stu-id="1ac94-163">The Unit of Work and Repository patterns are intended to encapsulate the infrastructure persistence layer so it is decoupled from the application and domain model layers.</span></span> <span data-ttu-id="1ac94-164">Implementar esses padrões pode facilitar o uso de repositórios de simulação com uma simulação de acesso ao banco de dados.</span><span class="sxs-lookup"><span data-stu-id="1ac94-164">Implementing these patterns can facilitate the use of mock repositories simulating access to the database.</span></span>

<span data-ttu-id="1ac94-165">Figura 9-18, você pode ver as diferenças entre usar não repositórios (diretamente usando o EF DbContext) em comparação a utilizar repositórios que facilitam simular os repositórios.</span><span class="sxs-lookup"><span data-stu-id="1ac94-165">In Figure 9-18 you can see the differences between not using repositories (directly using the EF DbContext) versus using repositories which make it easier to mock those repositories.</span></span>

![](./media/image19.png)

<span data-ttu-id="1ac94-166">**Figura 9-18**.</span><span class="sxs-lookup"><span data-stu-id="1ac94-166">**Figure 9-18**.</span></span> <span data-ttu-id="1ac94-167">Uso de repositórios personalizados em vez de um DbContext simples</span><span class="sxs-lookup"><span data-stu-id="1ac94-167">Using custom repositories versus a plain DbContext</span></span>

<span data-ttu-id="1ac94-168">Existem várias alternativas na simulação.</span><span class="sxs-lookup"><span data-stu-id="1ac94-168">There are multiple alternatives when mocking.</span></span> <span data-ttu-id="1ac94-169">Você pode simular apenas repositórios ou você pode simular toda a unidade de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1ac94-169">You could mock just repositories or you could mock a whole unit of work.</span></span> <span data-ttu-id="1ac94-170">Geralmente fictícias apenas os repositórios são suficiente, e a complexidade de abstrair e simular toda a unidade de trabalho normalmente não é necessário.</span><span class="sxs-lookup"><span data-stu-id="1ac94-170">Usually mocking just the repositories is enough, and the complexity to abstract and mock a whole unit of work is usually not needed.</span></span>

<span data-ttu-id="1ac94-171">Posteriormente, quando nos concentramos na camada de aplicativo, você verá como funciona a injeção de dependência no núcleo do ASP.NET e como ele é implementado quando o uso de repositórios.</span><span class="sxs-lookup"><span data-stu-id="1ac94-171">Later, when we focus on the application layer, you will see how Dependency Injection works in ASP.NET Core and how it is implemented when using repositories.</span></span>

<span data-ttu-id="1ac94-172">Em resumo, os repositórios personalizados permitem que você testar o código mais facilmente com testes de unidade que não são afetadas por estado de camada de dados.</span><span class="sxs-lookup"><span data-stu-id="1ac94-172">In short, custom repositories allow you to test code more easily with unit tests that are not impacted by the data tier state.</span></span> <span data-ttu-id="1ac94-173">Se você executar testes que também acessar o banco de dados real por meio do Entity Framework, eles não são testes de unidade, mas os testes de integração, que são muito mais lentos.</span><span class="sxs-lookup"><span data-stu-id="1ac94-173">If you run tests that also access the actual database through the Entity Framework, they are not unit tests but integration tests, which are a lot slower.</span></span>

<span data-ttu-id="1ac94-174">Se você estivesse usando DbContext diretamente, a única opção que você teria que seria executar testes de unidade usando um SQL Server na memória com dados previsíveis para testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="1ac94-174">If you were using DbContext directly, the only choice you would have would be to run unit tests by using an in-memory SQL Server with predictable data for unit tests.</span></span> <span data-ttu-id="1ac94-175">Você não poderá controlar objetos fictícios e dados falsos da mesma maneira no repositório.</span><span class="sxs-lookup"><span data-stu-id="1ac94-175">You would not be able to control mock objects and fake data in the same way at the repository level.</span></span> <span data-ttu-id="1ac94-176">Naturalmente, você sempre pode testar os controladores MVC.</span><span class="sxs-lookup"><span data-stu-id="1ac94-176">Of course, you could always test the MVC controllers.</span></span>

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="1ac94-177">Vida útil da instância EF DbContext e IUnitOfWork do seu contêiner IoC</span><span class="sxs-lookup"><span data-stu-id="1ac94-177">EF DbContext and IUnitOfWork instance lifetime in your IoC container</span></span>

<span data-ttu-id="1ac94-178">O objeto DbContext (exposto como um objeto IUnitOfWork) talvez precise ser compartilhado entre vários repositórios de dentro do mesmo escopo de solicitação HTTP.</span><span class="sxs-lookup"><span data-stu-id="1ac94-178">The DbContext object (exposed as an IUnitOfWork object) might need to be shared among multiple repositories within the same HTTP request scope.</span></span> <span data-ttu-id="1ac94-179">Por exemplo, isso é verdadeiro quando a operação que está sendo executada deve lidar com várias agregações, ou simplesmente porque você está usando várias instâncias do repositório.</span><span class="sxs-lookup"><span data-stu-id="1ac94-179">For example, this is true when the operation being executed must deal with multiple aggregates, or simply because you are using multiple repository instances.</span></span> <span data-ttu-id="1ac94-180">Também é importante mencionar que a interface IUnitOfWork é parte do domínio, não um tipo EF.</span><span class="sxs-lookup"><span data-stu-id="1ac94-180">It is also important to mention that the IUnitOfWork interface is part of the domain, not an EF type.</span></span>

<span data-ttu-id="1ac94-181">Para fazer isso, a instância do objeto DbContext deve ter o seu tempo de vida de serviço definido como ServiceLifetime.Scoped.</span><span class="sxs-lookup"><span data-stu-id="1ac94-181">In order to do that, the instance of the DbContext object has to have its service lifetime set to ServiceLifetime.Scoped.</span></span> <span data-ttu-id="1ac94-182">Este é o tempo de vida padrão ao registro de um DbContext com serviços. AddDbContext em seu contêiner IoC do método ConfigureServices do arquivo Startup.cs em seu projeto de API da Web do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="1ac94-182">This is the default lifetime when registering a DbContext with services.AddDbContext in your IoC container from the ConfigureServices method of the Startup.cs file in your ASP.NET Core Web API project.</span></span> <span data-ttu-id="1ac94-183">O código a seguir ilustra isso.</span><span class="sxs-lookup"><span data-stu-id="1ac94-183">The following code illustrates this.</span></span>

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

<span data-ttu-id="1ac94-184">O modo de instanciação DbContext não deve ser configurado como ServiceLifetime.Transient ou ServiceLifetime.Singleton.</span><span class="sxs-lookup"><span data-stu-id="1ac94-184">The DbContext instantiation mode should not be configured as ServiceLifetime.Transient or ServiceLifetime.Singleton.</span></span>

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="1ac94-185">O tempo de vida de instância de repositório em seu contêiner IoC</span><span class="sxs-lookup"><span data-stu-id="1ac94-185">The repository instance lifetime in your IoC container</span></span>

<span data-ttu-id="1ac94-186">De maneira semelhante, o tempo de vida do repositório normalmente deve ser definido como escopo (InstancePerLifetimeScope em Autofac).</span><span class="sxs-lookup"><span data-stu-id="1ac94-186">In a similar way, repository’s lifetime should usually be set as scoped (InstancePerLifetimeScope in Autofac).</span></span> <span data-ttu-id="1ac94-187">Ele também pode ser transitório (InstancePerDependency em Autofac), mas seu serviço será mais eficiente em memória que diz respeito ao usar o tempo de vida no escopo.</span><span class="sxs-lookup"><span data-stu-id="1ac94-187">It could also be transient (InstancePerDependency in Autofac), but your service will be more efficient in regards memory when using the scoped lifetime.</span></span>

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

<span data-ttu-id="1ac94-188">Observe que usando o tempo de vida de singleton para o repositório pode causar problemas graves de simultaneidade quando o DbContext é definido como escopo de tempo de vida (InstancePerLifetimeScope) (o padrão tempo de vida de um DBContext).</span><span class="sxs-lookup"><span data-stu-id="1ac94-188">Note that using the singleton lifetime for the repository could cause you serious concurrency problems when your DbContext is set to scoped (InstancePerLifetimeScope) lifetime (the default lifetimes for a DBContext).</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="1ac94-189">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="1ac94-189">Additional resources</span></span>

-   <span data-ttu-id="1ac94-190">**Implementando o repositório e a unidade de trabalho padrões em um aplicativo ASP.NET MVC**
    [*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/ Implementing-the-Repository-and-Unit-of-Work-Patterns-in-an-ASP-NET-MVC-Application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)</span><span class="sxs-lookup"><span data-stu-id="1ac94-190">**Implementing the Repository and Unit of Work Patterns in an ASP.NET MVC Application**
[*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)</span></span>

-   <span data-ttu-id="1ac94-191">**Jonathan Allen. Estratégias de implementação para o repositório padrão com o Entity Framework, Dapper e cadeia**
    [*https://www.infoq.com/articles/repository-implementation-strategies*](https://www.infoq.com/articles/repository-implementation-strategies)</span><span class="sxs-lookup"><span data-stu-id="1ac94-191">**Jonathan Allen. Implementation Strategies for the Repository Pattern with Entity Framework, Dapper, and Chain**
[*https://www.infoq.com/articles/repository-implementation-strategies*](https://www.infoq.com/articles/repository-implementation-strategies)</span></span>

-   <span data-ttu-id="1ac94-192">**Cesar de la Torre. Comparando os tempos de vida do serviço de contêiner de ASP.NET Core IoC com escopos de instância de contêiner IoC Autofac**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/ Comparing-ASP-NET-Core-IoC-Service-Life-Times-and-autofac-IoC-Instance-Scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span><span class="sxs-lookup"><span data-stu-id="1ac94-192">**Cesar de la Torre. Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes**
[*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span></span>

## <a name="table-mapping"></a><span data-ttu-id="1ac94-193">Mapeamento de tabela</span><span class="sxs-lookup"><span data-stu-id="1ac94-193">Table mapping</span></span>

<span data-ttu-id="1ac94-194">Mapeamento de tabela identifica os dados da tabela a ser consultado do e salvo no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="1ac94-194">Table mapping identifies the table data to be queried from and saved to the database.</span></span> <span data-ttu-id="1ac94-195">Anteriormente, você viu como entidades de domínio (por exemplo, um domínio do produto ou ordem) podem ser usadas para gerar um esquema de banco de dados relacionado.</span><span class="sxs-lookup"><span data-stu-id="1ac94-195">Previously you saw how domain entities (for example, a product or order domain) can be used to generate a related database schema.</span></span> <span data-ttu-id="1ac94-196">EF fortemente foi projetada para o conceito de *convenções*.</span><span class="sxs-lookup"><span data-stu-id="1ac94-196">EF is strongly designed around the concept of *conventions*.</span></span> <span data-ttu-id="1ac94-197">Perguntas de endereço de convenções como "Qual será o nome de uma tabela?"</span><span class="sxs-lookup"><span data-stu-id="1ac94-197">Conventions address questions like “What will the name of a table be?”</span></span> <span data-ttu-id="1ac94-198">ou "qual propriedade é a chave primária?"</span><span class="sxs-lookup"><span data-stu-id="1ac94-198">or “What property is the primary key?”</span></span> <span data-ttu-id="1ac94-199">Convenções normalmente se baseiam nos nomes convencionais — por exemplo, é comum para a chave primária para uma propriedade que termina com a ID.</span><span class="sxs-lookup"><span data-stu-id="1ac94-199">Conventions are typically based on conventional names—for example, it is typical for the primary key to be a property that ends with Id.</span></span>

<span data-ttu-id="1ac94-200">Por convenção, cada entidade será configurada para mapear para uma tabela com o mesmo nome que o DbSet&lt;TEntity&gt; propriedade que expõe a entidade no contexto de derivada.</span><span class="sxs-lookup"><span data-stu-id="1ac94-200">By convention, each entity will be set up to map to a table with the same name as the DbSet&lt;TEntity&gt; property that exposes the entity on the derived context.</span></span> <span data-ttu-id="1ac94-201">Se nenhum DbSet&lt;TEntity&gt; valor é fornecido para a entidade especificada, o nome da classe é usado.</span><span class="sxs-lookup"><span data-stu-id="1ac94-201">If no DbSet&lt;TEntity&gt; value is provided for the given entity, the class name is used.</span></span>

### <a name="data-annotations-versus-fluent-api"></a><span data-ttu-id="1ac94-202">Anotações de dados em comparação com a API fluente</span><span class="sxs-lookup"><span data-stu-id="1ac94-202">Data Annotations versus Fluent API</span></span>

<span data-ttu-id="1ac94-203">Existem muitos convenções EF núcleos adicionais e a maioria deles pode ser alterada usando as anotações de dados ou a API fluente, implementado no método OnModelCreating.</span><span class="sxs-lookup"><span data-stu-id="1ac94-203">There are many additional EF Core conventions, and most of them can be changed by using either data annotations or Fluent API, implemented within the OnModelCreating method.</span></span>

<span data-ttu-id="1ac94-204">As anotações de dados devem ser usadas nas classes de modelo de entidade, que é uma maneira mais invasiva de um ponto de vista DDD.</span><span class="sxs-lookup"><span data-stu-id="1ac94-204">Data annotations must be used on the entity model classes themselves, which is a more intrusive way from a DDD point of view.</span></span> <span data-ttu-id="1ac94-205">Isso ocorre porque você é contaminação por seu modelo com anotações de dados relacionadas ao banco de dados de infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="1ac94-205">This is because you are contaminating your model with data annotations related to the infrastructure database.</span></span> <span data-ttu-id="1ac94-206">Por outro lado, a API fluente é uma maneira conveniente para alterar a maioria das convenções e mapeamentos dentro de sua camada de infraestrutura de persistência de dados, para que o modelo de entidade será limpo e separado da infraestrutura de persistência.</span><span class="sxs-lookup"><span data-stu-id="1ac94-206">On the other hand, Fluent API is a convenient way to change most conventions and mappings within your data persistence infrastructure layer, so the entity model will be clean and decoupled from the persistence infrastructure.</span></span>

### <a name="fluent-api-and-the-onmodelcreating-method"></a><span data-ttu-id="1ac94-207">API fluente e o método OnModelCreating</span><span class="sxs-lookup"><span data-stu-id="1ac94-207">Fluent API and the OnModelCreating method</span></span>

<span data-ttu-id="1ac94-208">Conforme mencionado, para alterar as convenções e os mapeamentos, você pode usar o método OnModelCreating na classe DbContext.</span><span class="sxs-lookup"><span data-stu-id="1ac94-208">As mentioned, in order to change conventions and mappings, you can use the OnModelCreating method in the DbContext class.</span></span> <span data-ttu-id="1ac94-209">O exemplo a seguir mostra como podemos fazer isso no ordenação microsserviço em eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="1ac94-209">The following example shows how we do this in the ordering microservice in eShopOnContainers.</span></span>

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

<span data-ttu-id="1ac94-210">Você pode definir os mapeamentos de API fluente no método OnModelCreating mesmo, mas é recomendável que o código de partição e ter vários submethods, um por entidade, conforme mostrado no exemplo.</span><span class="sxs-lookup"><span data-stu-id="1ac94-210">You could set all the Fluent API mappings within the same OnModelCreating method, but it is advisable to partition that code and have multiple submethods, one per entity, as shown in the example.</span></span> <span data-ttu-id="1ac94-211">Para modelos muito grandes, ainda é recomendável ter arquivos de origem separados (classes estáticas) para configurar tipos de entidade diferente.</span><span class="sxs-lookup"><span data-stu-id="1ac94-211">For particularly large models, it can even be advisable to have separate source files (static classes) for configuring different entity types.</span></span>

<span data-ttu-id="1ac94-212">O código de exemplo é explícito.</span><span class="sxs-lookup"><span data-stu-id="1ac94-212">The code in the example is explicit.</span></span> <span data-ttu-id="1ac94-213">No entanto, convenções EF Core fazer a maioria disso automaticamente, portanto, o código real que você precisa gravar para alcançar a mesma coisa seria muito menor.</span><span class="sxs-lookup"><span data-stu-id="1ac94-213">However, EF Core conventions do most of this automatically, so the actual code you would need to write to achieve the same thing would be much smaller.</span></span>

### <a name="the-hilo-algorithm-in-ef-core"></a><span data-ttu-id="1ac94-214">O algoritmo Hi/Lo no núcleo do EF</span><span class="sxs-lookup"><span data-stu-id="1ac94-214">The Hi/Lo algorithm in EF Core</span></span>

<span data-ttu-id="1ac94-215">Um aspecto interessante de código no exemplo anterior é que ele usa o [algoritmo Hi/Lo](https://vladmihalcea.com/2014/06/23/the-hilo-algorithm/) como a estratégia de geração de chave.</span><span class="sxs-lookup"><span data-stu-id="1ac94-215">An interesting aspect of code in the preceding example is that it uses the [Hi/Lo algorithm](https://vladmihalcea.com/2014/06/23/the-hilo-algorithm/) as the key generation strategy.</span></span>

<span data-ttu-id="1ac94-216">O algoritmo Hi/Lo é útil quando você precisa de chaves exclusivas.</span><span class="sxs-lookup"><span data-stu-id="1ac94-216">The Hi/Lo algorithm is useful when you need unique keys.</span></span> <span data-ttu-id="1ac94-217">Como obter um resumo, o algoritmo Hi-Lo atribui identificadores exclusivos para linhas da tabela enquanto não dependendo armazenar a linha no banco de dados imediatamente.</span><span class="sxs-lookup"><span data-stu-id="1ac94-217">As a summary, the Hi-Lo algorithm assigns unique identifiers to table rows while not depending on storing the row in the database immediately.</span></span> <span data-ttu-id="1ac94-218">Permite que você começar a usar os identificadores imediatamente, como acontece com o banco de dados sequencial regular IDs.</span><span class="sxs-lookup"><span data-stu-id="1ac94-218">This lets you start using the identifiers right away, as happens with regular sequential database IDs.</span></span>

<span data-ttu-id="1ac94-219">O algoritmo Hi/Lo descreve um mecanismo para gerar identificações de seguras no lado do cliente em vez de no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="1ac94-219">The Hi/Lo algorithm describes a mechanism for generating safe IDs on the client side rather than in the database.</span></span> <span data-ttu-id="1ac94-220">*Segurança* neste contexto significa sem colisões.</span><span class="sxs-lookup"><span data-stu-id="1ac94-220">*Safe* in this context means without collisions.</span></span> <span data-ttu-id="1ac94-221">Esse algoritmo é interessante por esses motivos:</span><span class="sxs-lookup"><span data-stu-id="1ac94-221">This algorithm is interesting for these reasons:</span></span>

-   <span data-ttu-id="1ac94-222">Ele não interrompem o padrão de unidade de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1ac94-222">It does not break the Unit of Work pattern.</span></span>

-   <span data-ttu-id="1ac94-223">Ele não requer a fazer viagens de ida e geradores de sequência de maneira em outros DBMSs.</span><span class="sxs-lookup"><span data-stu-id="1ac94-223">It does not require round trips the way sequence generators do in other DBMSs.</span></span>

-   <span data-ttu-id="1ac94-224">Ele gera um identificador de legível humano, ao contrário das técnicas que usam GUIDs.</span><span class="sxs-lookup"><span data-stu-id="1ac94-224">It generates a human readable identifier, unlike techniques that use GUIDs.</span></span>

<span data-ttu-id="1ac94-225">EF Core dá suporte [HiLo](http://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) com o método ForSqlServerUseSequenceHiLo, conforme mostrado no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="1ac94-225">EF Core supports [HiLo](http://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) with the ForSqlServerUseSequenceHiLo method, as shown in the preceding example.</span></span>

### <a name="mapping-fields-instead-of-properties"></a><span data-ttu-id="1ac94-226">Mapeamento de campos, em vez de propriedades</span><span class="sxs-lookup"><span data-stu-id="1ac94-226">Mapping fields instead of properties</span></span>

<span data-ttu-id="1ac94-227">Com o recurso do EF Core 1.1 que mapeia as colunas para campos, é possível para não usar as propriedades na classe de entidade e apenas para mapear colunas de uma tabela para campos.</span><span class="sxs-lookup"><span data-stu-id="1ac94-227">With the feature of EF Core 1.1 that maps columns to fields, it is possible to not use any properties in the entity class, and just to map columns from a table to fields.</span></span> <span data-ttu-id="1ac94-228">Um uso comum para isso seria campos privados para algum estado interno que não precisam ser acessados de fora da entidade.</span><span class="sxs-lookup"><span data-stu-id="1ac94-228">A common use for that would be private fields for any internal state that do not need to be accessed from outside the entity.</span></span>

<span data-ttu-id="1ac94-229">EF 1.1 oferece suporte a uma maneira de mapear um campo sem uma propriedade relacionada a uma coluna no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="1ac94-229">EF 1.1 supports a way to map a field without a related property to a column in the database.</span></span> <span data-ttu-id="1ac94-230">Você pode fazer isso com campos único ou também com coleções, como uma lista de&lt; &gt; campo.</span><span class="sxs-lookup"><span data-stu-id="1ac94-230">You can do this with single fields or also with collections, like a List&lt;&gt; field.</span></span> <span data-ttu-id="1ac94-231">Esse ponto foi mencionado anteriormente, quando discutimos modelagem as classes de modelo de domínio, mas aqui você pode ver como esse mapeamento é executado com a configuração de PropertyAccessMode.Field realçada no código anterior.</span><span class="sxs-lookup"><span data-stu-id="1ac94-231">This point was mentioned earlier when we discussed modeling the domain model classes, but here you can see how that mapping is performed with the PropertyAccessMode.Field configuration highlighted in the previous code.</span></span>

### <a name="using-shadow-properties-in-value-objects-for-hidden-ids-at-the-infrastructure-level"></a><span data-ttu-id="1ac94-232">Usando propriedades de sombra nos objetos de valor de IDs ocultos no nível de infraestrutura</span><span class="sxs-lookup"><span data-stu-id="1ac94-232">Using shadow properties in value objects for hidden IDs at the infrastructure level</span></span>

<span data-ttu-id="1ac94-233">Propriedades de sombra no núcleo do EF são propriedades que não existem em seu modelo de classe de entidade.</span><span class="sxs-lookup"><span data-stu-id="1ac94-233">Shadow properties in EF Core are properties that do not exist in your entity class model.</span></span> <span data-ttu-id="1ac94-234">Os valores e estados dessas propriedades são mantidos em puramente o [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) classe no nível de infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="1ac94-234">The values and states of these properties are maintained purely in the [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) class at the infrastructure level.</span></span>

<span data-ttu-id="1ac94-235">Do ponto de vista do DDD, propriedades de sombra são uma maneira conveniente de implementar objetos de valor, ocultando a ID como uma chave primária de propriedade de sombra.</span><span class="sxs-lookup"><span data-stu-id="1ac94-235">From a DDD point of view, shadow properties are a convenient way to implement value objects by hiding the ID as a shadow property primary key.</span></span> <span data-ttu-id="1ac94-236">Isso é importante, porque um objeto de valor não deve ter a identidade (pelo menos, você não deve ter a identificação da camada de modelo de domínio quando objetos de valor de formatação).</span><span class="sxs-lookup"><span data-stu-id="1ac94-236">This is important, because a value object should not have identity (at least, you should not have the ID in the domain model layer when shaping value objects).</span></span> <span data-ttu-id="1ac94-237">O ponto aqui é que a partir da versão atual do EF Core, Core EF não tem uma maneira de implementar objetos de valor como [tipos complexos](https://msdn.microsoft.com/library/jj680147(v=vs.113).aspx), como é possível no EF 6. x.</span><span class="sxs-lookup"><span data-stu-id="1ac94-237">The point here is that as of the current version of EF Core, EF Core does not have a way to implement value objects as [complex types](https://msdn.microsoft.com/library/jj680147(v=vs.113).aspx), as is possible in EF 6.x.</span></span> <span data-ttu-id="1ac94-238">É por isso que você precisa implementar um objeto de valor como uma entidade com uma ID oculta (chave primária) definido como uma propriedade de sombra no momento.</span><span class="sxs-lookup"><span data-stu-id="1ac94-238">That is why you currently need to implement a value object as an entity with a hidden ID (primary key) set as a shadow property.</span></span>

<span data-ttu-id="1ac94-239">Como você pode ver no [objeto de valor do endereço](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs) eShopOnContainers, no modelo de endereço você não vê uma ID:</span><span class="sxs-lookup"><span data-stu-id="1ac94-239">As you can see in the [Address value object](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs) in eShopOnContainers, in the Address model you do not see an ID:</span></span>

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

<span data-ttu-id="1ac94-240">Mas nos bastidores, é necessário fornecer uma ID de forma que o EF Core é capaz de manter esses dados nas tabelas de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="1ac94-240">But under the covers, we need to provide an ID so that EF Core is able to persist this data in the database tables.</span></span> <span data-ttu-id="1ac94-241">Podemos fazer isso no método de ConfigureAddress a [OrderingContext.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Infrastructure/OrderingContext.cs) classe no nível de infraestrutura, portanto não podemos poluir o modelo de domínio com o código de infraestrutura EF.</span><span class="sxs-lookup"><span data-stu-id="1ac94-241">We do that in the ConfigureAddress method of the [OrderingContext.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Infrastructure/OrderingContext.cs) class at the infrastructure level, so we do not pollute the domain model with EF infrastructure code.</span></span>

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

#### <a name="additional-resources"></a><span data-ttu-id="1ac94-242">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="1ac94-242">Additional resources</span></span>

-   <span data-ttu-id="1ac94-243">**Mapeamento de tabela**
    [*https://docs.microsoft.com/ef/core/modeling/relational/tables*](https://docs.microsoft.com/ef/core/modeling/relational/tables)</span><span class="sxs-lookup"><span data-stu-id="1ac94-243">**Table Mapping**
[*https://docs.microsoft.com/ef/core/modeling/relational/tables*](https://docs.microsoft.com/ef/core/modeling/relational/tables)</span></span>

-   <span data-ttu-id="1ac94-244">**Use HiLo para gerar chaves com o Entity Framework Core**
    [*http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/*](http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/)</span><span class="sxs-lookup"><span data-stu-id="1ac94-244">**Use HiLo to generate keys with Entity Framework Core**
[*http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/*](http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/)</span></span>

-   <span data-ttu-id="1ac94-245">**Fazendo campos**
    [*https://docs.microsoft.com/ef/core/modeling/backing-field*](https://docs.microsoft.com/ef/core/modeling/backing-field)</span><span class="sxs-lookup"><span data-stu-id="1ac94-245">**Backing Fields**
[*https://docs.microsoft.com/ef/core/modeling/backing-field*](https://docs.microsoft.com/ef/core/modeling/backing-field)</span></span>

-   <span data-ttu-id="1ac94-246">**Steve Smith. Encapsulado coleções no Entity Framework Core**
    [*http://ardalis.com/encapsulated-collections-in-entity-framework-core*](http://ardalis.com/encapsulated-collections-in-entity-framework-core)</span><span class="sxs-lookup"><span data-stu-id="1ac94-246">**Steve Smith. Encapsulated Collections in Entity Framework Core**
[*http://ardalis.com/encapsulated-collections-in-entity-framework-core*](http://ardalis.com/encapsulated-collections-in-entity-framework-core)</span></span>

-   <span data-ttu-id="1ac94-247">**Propriedades de sombra**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span><span class="sxs-lookup"><span data-stu-id="1ac94-247">**Shadow Properties**
[*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="1ac94-248">[Anterior] (infraestrutura-persistência-camada-design.md) [Avançar] (nosql-banco de dados-persistência-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="1ac94-248">[Previous] (infrastructure-persistence-layer-design.md) [Next] (nosql-database-persistence-infrastructure.md)</span></span>
