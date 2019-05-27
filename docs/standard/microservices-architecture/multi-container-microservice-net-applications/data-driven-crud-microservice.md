---
title: Criando um microsserviço de CRUD simples controlado por dados
description: Arquitetura de microsserviços .NET para aplicativos .NET em contêineres | Entenda a criação de um microsserviço CRUD simples (controlado por dados) dentro do contexto de um aplicativo de microsserviço.
ms.date: 01/07/2019
ms.openlocfilehash: 53aba727c8dae35df8b34bc1558c0cc390fe2014
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053561"
---
# <a name="creating-a-simple-data-driven-crud-microservice"></a><span data-ttu-id="1da7a-103">Criando um microsserviço de CRUD simples controlado por dados</span><span class="sxs-lookup"><span data-stu-id="1da7a-103">Creating a simple data-driven CRUD microservice</span></span>

<span data-ttu-id="1da7a-104">Esta seção descreve como criar um microsserviço simples que execute operações de CRUD (criar, ler, atualizar e excluir) em uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="1da7a-104">This section outlines how to create a simple microservice that performs create, read, update, and delete (CRUD) operations on a data source.</span></span>

## <a name="designing-a-simple-crud-microservice"></a><span data-ttu-id="1da7a-105">Criando um microsserviço de CRUD simples</span><span class="sxs-lookup"><span data-stu-id="1da7a-105">Designing a simple CRUD microservice</span></span>

<span data-ttu-id="1da7a-106">Do ponto de vista do design, esse tipo de microsserviço em contêineres é muito simples.</span><span class="sxs-lookup"><span data-stu-id="1da7a-106">From a design point of view, this type of containerized microservice is very simple.</span></span> <span data-ttu-id="1da7a-107">Talvez o problema a ser resolvido seja simples ou talvez a implementação seja apenas uma prova de conceito.</span><span class="sxs-lookup"><span data-stu-id="1da7a-107">Perhaps the problem to solve is simple, or perhaps the implementation is only a proof of concept.</span></span>

![Um microsserviço CRUD simples é um padrão de design interno.](./media/image4.png)

<span data-ttu-id="1da7a-109">**Figura 6-4**.</span><span class="sxs-lookup"><span data-stu-id="1da7a-109">**Figure 6-4**.</span></span> <span data-ttu-id="1da7a-110">Design interno para microsserviços de CRUD simples</span><span class="sxs-lookup"><span data-stu-id="1da7a-110">Internal design for simple CRUD microservices</span></span>

<span data-ttu-id="1da7a-111">Um exemplo desse tipo de serviço de unidade de dados é o microsserviço de catálogo do aplicativo de exemplo eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="1da7a-111">An example of this kind of simple data-drive service is the catalog microservice from the eShopOnContainers sample application.</span></span> <span data-ttu-id="1da7a-112">Esse tipo de serviço implementa todas as suas funcionalidades em um único projeto da API Web ASP.NET Core que inclui classes para seu modelo de dados, sua lógica de negócios e seu código de acesso a dados.</span><span class="sxs-lookup"><span data-stu-id="1da7a-112">This type of service implements all its functionality in a single ASP.NET Core Web API project that includes classes for its data model, its business logic, and its data access code.</span></span> <span data-ttu-id="1da7a-113">Ele também armazena os dados relacionados em um banco de dados em execução no SQL Server (como outro contêiner para fins de Desenvolvimento/Teste), mas também pode ser qualquer host normal do SQL Server, conforme mostrado na Figura 6-5.</span><span class="sxs-lookup"><span data-stu-id="1da7a-113">It also stores its related data in a database running in SQL Server (as another container for dev/test purposes), but could also be any regular SQL Server host, as shown in Figure 6-5.</span></span>

![O microsserviço de Catálogo lógico inclui o banco de dados do Catálogo, que pode estar ou não no mesmo host do Docker.](./media/image5.png)

<span data-ttu-id="1da7a-116">**Figura 6-5**.</span><span class="sxs-lookup"><span data-stu-id="1da7a-116">**Figure 6-5**.</span></span> <span data-ttu-id="1da7a-117">Design de microsserviço controlado por dados/CRUD simples</span><span class="sxs-lookup"><span data-stu-id="1da7a-117">Simple data-driven/CRUD microservice design</span></span>

<span data-ttu-id="1da7a-118">Quando estiver desenvolvendo esse tipo de serviço, você somente precisará do [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) e de uma API de acesso a dados ou de um ORM (mapeador relacional de objeto) como o [Entity Framework Core](https://docs.microsoft.com/ef/core/index).</span><span class="sxs-lookup"><span data-stu-id="1da7a-118">When you are developing this kind of service, you only need [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) and a data-access API or ORM like [Entity Framework Core](https://docs.microsoft.com/ef/core/index).</span></span> <span data-ttu-id="1da7a-119">Você também pode gerar metadados do [Swagger](https://swagger.io/) automaticamente por meio do [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) para fornecer uma descrição do que o serviço oferece, conforme será explicado na próxima seção.</span><span class="sxs-lookup"><span data-stu-id="1da7a-119">You could also generate [Swagger](https://swagger.io/) metadata automatically through [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) to provide a description of what your service offers, as explained in the next section.</span></span>

<span data-ttu-id="1da7a-120">Observe que executar um servidor de banco de dados como o SQL Server em um contêiner do Docker é ótimo para ambientes de desenvolvimento, porque todas as dependências podem funcionar sem precisar provisionar um banco de dados na nuvem ou localmente.</span><span class="sxs-lookup"><span data-stu-id="1da7a-120">Note that running a database server like SQL Server within a Docker container is great for development environments, because you can have all your dependencies up and running without needing to provision a database in the cloud or on-premises.</span></span> <span data-ttu-id="1da7a-121">Isso é muito conveniente ao executar testes de integração.</span><span class="sxs-lookup"><span data-stu-id="1da7a-121">This is very convenient when running integration tests.</span></span> <span data-ttu-id="1da7a-122">No entanto, para ambientes de produção, executar um servidor de banco de dados em um contêiner não é recomendável, porque, geralmente, essa abordagem não oferece alta disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="1da7a-122">However, for production environments, running a database server in a container is not recommended, because you usually do not get high availability with that approach.</span></span> <span data-ttu-id="1da7a-123">Para um ambiente de produção no Azure, é recomendável usar o BD SQL do Azure ou qualquer outra tecnologia de banco de dados que possa fornecer alta disponibilidade e alta escalabilidade.</span><span class="sxs-lookup"><span data-stu-id="1da7a-123">For a production environment in Azure, it is recommended that you use Azure SQL DB or any other database technology that can provide high availability and high scalability.</span></span> <span data-ttu-id="1da7a-124">Por exemplo, para uma abordagem NoSQL, você pode escolher o CosmosDB.</span><span class="sxs-lookup"><span data-stu-id="1da7a-124">For example, for a NoSQL approach, you might choose CosmosDB.</span></span>

<span data-ttu-id="1da7a-125">Por fim, editando os arquivos de metadados Dockerfile e docker-compose.yml, você pode configurar como a imagem desse contêiner será criada, ou seja, qual imagem base ele usará, além das configurações de design, como nomes internos e externos e portas TCP.</span><span class="sxs-lookup"><span data-stu-id="1da7a-125">Finally, by editing the Dockerfile and docker-compose.yml metadata files, you can configure how the image of this container will be created—what base image it will use, plus design settings such as internal and external names and TCP ports.</span></span>

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a><span data-ttu-id="1da7a-126">Implementando um microsserviço de CRUD simples com o ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1da7a-126">Implementing a simple CRUD microservice with ASP.NET Core</span></span>

<span data-ttu-id="1da7a-127">Para implementar um microsserviço CRUD simples usando o .NET Core e o Visual Studio, comece criando um projeto simples de API Web do ASP.NET Core (em execução no .NET Core, para que ele possa ser executado em um host Linux do Docker), como é mostrado na Figura 6-6.</span><span class="sxs-lookup"><span data-stu-id="1da7a-127">To implement a simple CRUD microservice using .NET Core and Visual Studio, you start by creating a simple ASP.NET Core Web API project (running on .NET Core so it can run on a Linux Docker host), as shown in Figure 6-6.</span></span>

![Para criar um Projeto de API Web do ASP.NET Core, primeiro selecione um Aplicativo Web do ASP.NET Core e, em seguida, selecione o tipo de API.](./media/image6.png)

<span data-ttu-id="1da7a-129">**Figura 6-6**.</span><span class="sxs-lookup"><span data-stu-id="1da7a-129">**Figure 6-6**.</span></span> <span data-ttu-id="1da7a-130">Criando um projeto de API Web ASP.NET Core no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1da7a-130">Creating an ASP.NET Core Web API project in Visual Studio</span></span>

<span data-ttu-id="1da7a-131">Depois de criar o projeto, você poderá implementar os controladores de MVC como faria em qualquer outro projeto de API Web, usando a API do Entity Framework ou uma outra API.</span><span class="sxs-lookup"><span data-stu-id="1da7a-131">After creating the project, you can implement your MVC controllers as you would in any other Web API project, using the Entity Framework API or other API.</span></span> <span data-ttu-id="1da7a-132">Em um novo projeto de API Web, você verá que a única dependência existente nesse microsserviço é em relação ao próprio ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="1da7a-132">In a new Web API project, you can see that the only dependency you have in that microservice is on ASP.NET Core itself.</span></span> <span data-ttu-id="1da7a-133">Internamente, na dependência *Microsoft.AspNetCore.All*, ela se refere ao Entity Framework e a muitos outros pacotes NuGet do .NET Core, como é mostrado na Figura 6-7.</span><span class="sxs-lookup"><span data-stu-id="1da7a-133">Internally, within the *Microsoft.AspNetCore.All* dependency, it is referencing Entity Framework and many other .NET Core Nuget packages, as shown in Figure 6-7.</span></span>

![O projeto de API inclui referências ao pacote NuGet Microsoft.AspNetCore.App, que inclui referências a todos os pacotes essenciais.](./media/image8.png)

<span data-ttu-id="1da7a-136">**Figura 6-7**.</span><span class="sxs-lookup"><span data-stu-id="1da7a-136">**Figure 6-7**.</span></span> <span data-ttu-id="1da7a-137">Dependências em um microsserviço de API Web de CRUD simples</span><span class="sxs-lookup"><span data-stu-id="1da7a-137">Dependencies in a simple CRUD Web API microservice</span></span>

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a><span data-ttu-id="1da7a-138">Implementando serviços da API Web de CRUD com o Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="1da7a-138">Implementing CRUD Web API services with Entity Framework Core</span></span>

<span data-ttu-id="1da7a-139">O Entity Framework (EF) Core é uma versão de multiplaforma leve, extensível e de plataforma cruzada da popular tecnologia de acesso a dados do Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="1da7a-139">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="1da7a-140">O EF Core é um ORM (mapeador relacional de objeto) que permite que os desenvolvedores do .NET trabalhem com um banco de dados usando objetos .NET.</span><span class="sxs-lookup"><span data-stu-id="1da7a-140">EF Core is an object-relational mapper (ORM) that enables .NET developers to work with a database using .NET objects.</span></span>

<span data-ttu-id="1da7a-141">O microsserviço de catálogo usa o EF e o provedor do SQL Server porque seu banco de dados está em execução em um contêiner com o SQL Server para a imagem do Docker do Linux.</span><span class="sxs-lookup"><span data-stu-id="1da7a-141">The catalog microservice uses EF and the SQL Server provider because its database is running in a container with the SQL Server for Linux Docker image.</span></span> <span data-ttu-id="1da7a-142">No entanto, o banco de dados poderia ser implantado em qualquer SQL Server, como o Windows local ou o BD SQL do Azure.</span><span class="sxs-lookup"><span data-stu-id="1da7a-142">However, the database could be deployed into any SQL Server, such as Windows on-premises or Azure SQL DB.</span></span> <span data-ttu-id="1da7a-143">A única coisa que você precisaria alterar seria a cadeia de conexão no microsserviço do ASP.NET Web API.</span><span class="sxs-lookup"><span data-stu-id="1da7a-143">The only thing you would need to change is the connection string in the ASP.NET Web API microservice.</span></span>

#### <a name="the-data-model"></a><span data-ttu-id="1da7a-144">O modelo de dados</span><span class="sxs-lookup"><span data-stu-id="1da7a-144">The data model</span></span>

<span data-ttu-id="1da7a-145">Com o EF Core, o acesso a dados é executado usando um modelo.</span><span class="sxs-lookup"><span data-stu-id="1da7a-145">With EF Core, data access is performed by using a model.</span></span> <span data-ttu-id="1da7a-146">Um modelo é composto por classes de entidade (modelo de domínio) e um contexto derivado (DbContext) que representa uma sessão com o banco de dados, permitindo que você consulte e salve os dados.</span><span class="sxs-lookup"><span data-stu-id="1da7a-146">A model is made up of (domain model) entity classes and a derived context (DbContext) that represents a session with the database, allowing you to query and save data.</span></span> <span data-ttu-id="1da7a-147">Gere um modelo usando um banco de dados existente, codifique manualmente um modelo para que ele corresponda ao seu banco de dados ou use migrações do EF para criar um banco de dados com base no modelo, usando a abordagem code-first (que facilita a evolução do banco de dados conforme o modelo muda ao longo do tempo).</span><span class="sxs-lookup"><span data-stu-id="1da7a-147">You can generate a model from an existing database, manually code a model to match your database, or use EF migrations to create a database from your model, using the code-first approach (that makes it easy to evolve the database as your model changes over time).</span></span> <span data-ttu-id="1da7a-148">Para o microsserviço de catálogo estamos usando a última abordagem.</span><span class="sxs-lookup"><span data-stu-id="1da7a-148">For the catalog microservice we are using the last approach.</span></span> <span data-ttu-id="1da7a-149">Veja um exemplo da classe de entidade CatalogItem no exemplo de código a seguir, que é uma classe de entidade [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object) (objeto CRL básico) simples.</span><span class="sxs-lookup"><span data-stu-id="1da7a-149">You can see an example of the CatalogItem entity class in the following code example, which is a simple Plain Old CLR Object ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) entity class.</span></span>

```csharp
public class CatalogItem
{
    public int Id { get; set; }
    public string Name { get; set; }
    public string Description { get; set; }
    public decimal Price { get; set; }
    public string PictureFileName { get; set; }
    public string PictureUri { get; set; }
    public int CatalogTypeId { get; set; }
    public CatalogType CatalogType { get; set; }
    public int CatalogBrandId { get; set; }
    public CatalogBrand CatalogBrand { get; set; }
    public int AvailableStock { get; set; }
    public int RestockThreshold { get; set; }
    public int MaxStockThreshold { get; set; }

    public bool OnReorder { get; set; }
    public CatalogItem() { }

    // Additional code ...
}
```

<span data-ttu-id="1da7a-150">Você também precisará de um DbContext que represente uma sessão com o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="1da7a-150">You also need a DbContext that represents a session with the database.</span></span> <span data-ttu-id="1da7a-151">Para o microsserviço de catálogo, a classe CatalogContext é derivada da classe base DbContext, conforme é mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="1da7a-151">For the catalog microservice, the CatalogContext class derives from the DbContext base class, as shown in the following example:</span></span>

```csharp
public class CatalogContext : DbContext
{
    public CatalogContext(DbContextOptions<CatalogContext> options) : base(options)
    {
    }
    public DbSet<CatalogItem> CatalogItems { get; set; }
    public DbSet<CatalogBrand> CatalogBrands { get; set; }
    public DbSet<CatalogType> CatalogTypes { get; set; }

    // Additional code ...

}
```

<span data-ttu-id="1da7a-152">É possível ter implementações adicionais do `DbContext`.</span><span class="sxs-lookup"><span data-stu-id="1da7a-152">You can have additional `DbContext` implementations.</span></span> <span data-ttu-id="1da7a-153">Por exemplo, no microsserviço Catalog.API de exemplo, há um segundo `DbContext` chamado `CatalogContextSeed` no qual ele populará automaticamente os dados de exemplo na primeira vez que tentar acessar o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="1da7a-153">For example, in the sample Catalog.API microservice, there's a second `DbContext` named `CatalogContextSeed` where it automatically populates the sample data the first time it tries to access the database.</span></span> <span data-ttu-id="1da7a-154">Esse método é útil para dados de demonstração e também para cenários de teste automatizados.</span><span class="sxs-lookup"><span data-stu-id="1da7a-154">This method is useful for demo data and for automated testing scenarios, as well.</span></span>

<span data-ttu-id="1da7a-155">Dentro do `DbContext`, use o método `OnModelCreating` para personalizar os mapeamentos de entidade de banco de dados/objeto e outros [pontos de extensibilidade do EF](https://devblogs.microsoft.com/dotnet/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).</span><span class="sxs-lookup"><span data-stu-id="1da7a-155">Within the `DbContext`, you use the `OnModelCreating` method to customize object/database entity mappings and other [EF extensibility points](https://devblogs.microsoft.com/dotnet/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).</span></span>

##### <a name="querying-data-from-web-api-controllers"></a><span data-ttu-id="1da7a-156">Consultando dados de controladores da API Web</span><span class="sxs-lookup"><span data-stu-id="1da7a-156">Querying data from Web API controllers</span></span>

<span data-ttu-id="1da7a-157">As instâncias das classes de entidade normalmente são recuperadas do banco de dados usando LINQ (consulta integrada à linguagem), conforme é mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="1da7a-157">Instances of your entity classes are typically retrieved from the database using Language Integrated Query (LINQ), as shown in the following example:</span></span>

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    private readonly CatalogContext _catalogContext;
    private readonly CatalogSettings _settings;
    private readonly ICatalogIntegrationEventService _catalogIntegrationEventService;

    public CatalogController(CatalogContext context,
                             IOptionsSnapshot<CatalogSettings> settings,
                             ICatalogIntegrationEventService catalogIntegrationEventService)
    {
        _catalogContext = context ?? throw new ArgumentNullException(nameof(context));
        _catalogIntegrationEventService = catalogIntegrationEventService ?? throw new ArgumentNullException(nameof(catalogIntegrationEventService));

        _settings = settings.Value;
        ((DbContext)context).ChangeTracker.QueryTrackingBehavior = QueryTrackingBehavior.NoTracking;
    }

    // GET api/v1/[controller]/items[?pageSize=3&pageIndex=10]
    [HttpGet]
    [Route("[action]")]
    [ProducesResponseType(typeof(PaginatedItemsViewModel<CatalogItem>), (int)HttpStatusCode.OK)]
    public async Task<IActionResult> Items([FromQuery]int pageSize = 10,
                                           [FromQuery]int pageIndex = 0)

    {
        var totalItems = await _catalogContext.CatalogItems
            .LongCountAsync();

        var itemsOnPage = await _catalogContext.CatalogItems
            .OrderBy(c => c.Name)
            .Skip(pageSize * pageIndex)
            .Take(pageSize)
            .ToListAsync();

        itemsOnPage = ChangeUriPlaceholder(itemsOnPage);

        var model = new PaginatedItemsViewModel<CatalogItem>(
            pageIndex, pageSize, totalItems, itemsOnPage);

        return Ok(model);
    }
    //...
}
```

##### <a name="saving-data"></a><span data-ttu-id="1da7a-158">Salvar dados</span><span class="sxs-lookup"><span data-stu-id="1da7a-158">Saving data</span></span>

<span data-ttu-id="1da7a-159">Dados são criados, excluídos e modificados no banco de dados usando as instâncias de suas classes de entidade.</span><span class="sxs-lookup"><span data-stu-id="1da7a-159">Data is created, deleted, and modified in the database using instances of your entity classes.</span></span> <span data-ttu-id="1da7a-160">Você poderia adicionar um código como o exemplo embutido em código a seguir (dados fictícios, neste caso) aos controladores da API Web.</span><span class="sxs-lookup"><span data-stu-id="1da7a-160">You could add code like the following hard-coded example (mock data, in this case) to your Web API controllers.</span></span>

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
                                     Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a><span data-ttu-id="1da7a-161">Injeção de dependência nos controladores da API Web e do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1da7a-161">Dependency Injection in ASP.NET Core and Web API controllers</span></span>

<span data-ttu-id="1da7a-162">Na ASP.NET Core, você pode usar a DI (injeção de dependência) pronta para uso.</span><span class="sxs-lookup"><span data-stu-id="1da7a-162">In ASP.NET Core you can use Dependency Injection (DI) out of the box.</span></span> <span data-ttu-id="1da7a-163">Não é necessário configurar um contêiner de IoC (inversão de controle) de terceiros, embora seja possível conectar o contêiner de IoC de sua preferência à infraestrutura do ASP.NET Core, caso deseje.</span><span class="sxs-lookup"><span data-stu-id="1da7a-163">You do not need to set up a third-party Inversion of Control (IoC) container, although you can plug your preferred IoC container into the ASP.NET Core infrastructure if you want.</span></span> <span data-ttu-id="1da7a-164">Nesse caso, isso significa que você pode injetar diretamente o DBContext do EF necessário ou repositórios adicionais por meio do construtor do controlador.</span><span class="sxs-lookup"><span data-stu-id="1da7a-164">In this case, it means that you can directly inject the required EF DBContext or additional repositories through the controller constructor.</span></span>

<span data-ttu-id="1da7a-165">No exemplo da classe `CatalogController` acima, estamos injetando um objeto do tipo `CatalogContext` além de outros objetos por meio do construtor `CatalogController()`.</span><span class="sxs-lookup"><span data-stu-id="1da7a-165">In the example above of the `CatalogController` class, we are injecting an object of `CatalogContext` type plus other objects through the `CatalogController()` constructor.</span></span>

<span data-ttu-id="1da7a-166">Uma configuração importante a ser definida no projeto de API Web é o registro da classe DbContext no contêiner de IoC do serviço.</span><span class="sxs-lookup"><span data-stu-id="1da7a-166">An important configuration to set up in the Web API project is the DbContext class registration into the service's IoC container.</span></span> <span data-ttu-id="1da7a-167">Normalmente isso é feito na classe `Startup` chamando o método `services.AddDbContext<DbContext>()` dentro do método `ConfigureServices()`, conforme é mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="1da7a-167">You typically do so in the `Startup` class by calling the `services.AddDbContext<DbContext>()` method inside the `ConfigureServices()` method, as shown in the following example:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // Additional code...

    services.AddDbContext<CatalogContext>(options =>
    {
        options.UseSqlServer(Configuration["ConnectionString"],
        sqlServerOptionsAction: sqlOptions =>
        {
           sqlOptions.
               MigrationsAssembly(
                   typeof(Startup).
                    GetTypeInfo().
                     Assembly.
                      GetName().Name);

           //Configuring Connection Resiliency:
           sqlOptions.
               EnableRetryOnFailure(maxRetryCount: 5,
               maxRetryDelay: TimeSpan.FromSeconds(30),
               errorNumbersToAdd: null);

       });

       // Changing default behavior when client evaluation occurs to throw.
       // Default in EFCore would be to log warning when client evaluation is done.
       options.ConfigureWarnings(warnings => warnings.Throw(
           RelationalEventId.QueryClientEvaluationWarning));
   });

  //...

}
```

### <a name="additional-resources"></a><span data-ttu-id="1da7a-168">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="1da7a-168">Additional resources</span></span>

- <span data-ttu-id="1da7a-169">**Consultando dados** \\</span><span class="sxs-lookup"><span data-stu-id="1da7a-169">**Querying Data** \\</span></span>
  [https://docs.microsoft.com/ef/core/querying/index](/ef/core/querying/index)

- <span data-ttu-id="1da7a-170">**Salvando dados** \\</span><span class="sxs-lookup"><span data-stu-id="1da7a-170">**Saving Data** \\</span></span>
  [https://docs.microsoft.com/ef/core/saving/index](/ef/core/saving/index)

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a><span data-ttu-id="1da7a-171">A cadeia de conexão e as variáveis de ambiente do BD usadas pelos contêineres do Docker</span><span class="sxs-lookup"><span data-stu-id="1da7a-171">The DB connection string and environment variables used by Docker containers</span></span>

<span data-ttu-id="1da7a-172">É possível usar as configurações do ASP.NET Core e adicionar uma propriedade ConnectionString no arquivo settings.json, conforme é mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="1da7a-172">You can use the ASP.NET Core settings and add a ConnectionString property to your settings.json file as shown in the following example:</span></span>

```json
{
    "ConnectionString": "Server=tcp:127.0.0.1,5433;Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word",
    "ExternalCatalogBaseUrl": "http://localhost:5101",
    "Logging": {
        "IncludeScopes": false,
        "LogLevel": {
            "Default": "Debug",
            "System": "Information",
            "Microsoft": "Information"
        }
    }
}
```

<span data-ttu-id="1da7a-173">O arquivo settings.json pode ter valores padrão para a propriedade ConnectionString ou para qualquer outra propriedade.</span><span class="sxs-lookup"><span data-stu-id="1da7a-173">The settings.json file can have default values for the ConnectionString property or for any other property.</span></span> <span data-ttu-id="1da7a-174">No entanto, essas propriedades serão substituídas pelos valores das variáveis de ambiente que você especificar no arquivo docker-compose.override.yml, ao usar o Docker.</span><span class="sxs-lookup"><span data-stu-id="1da7a-174">However, those properties will be overridden by the values of environment variables that you specify in the docker-compose.override.yml file, when using Docker.</span></span>

<span data-ttu-id="1da7a-175">Usando os arquivos docker-compose.yml ou docker-compose.override.yml, é possível inicializar essas variáveis de ambiente para que o Docker as configure como variáveis de ambiente do sistema operacional, como é mostrado no arquivo docker-compose.override.yml a seguir (a cadeia de conexão e as outras linhas são quebradas automaticamente neste exemplo, mas não são quebradas automaticamente em seu próprio arquivo).</span><span class="sxs-lookup"><span data-stu-id="1da7a-175">From your docker-compose.yml or docker-compose.override.yml files, you can initialize those environment variables so that Docker will set them up as OS environment variables for you, as shown in the following docker-compose.override.yml file (the connection string and other lines wrap in this example, but it would not wrap in your own file).</span></span>

```yml
# docker-compose.override.yml

#
catalog.api:
  environment:
    - ConnectionString=Server=sql.data;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word
    # Additional environment variables for this service
  ports:
    - "5101:80"
```

<span data-ttu-id="1da7a-176">Os arquivos docker-compose.yml no nível da solução não são apenas mais flexíveis do que arquivos de configuração no nível do projeto ou do microsserviço, mas também serão mais seguros se você substituir as variáveis de ambiente declaradas em arquivos docker-compose com valores definidos das suas ferramentas de implantação, como de tarefas de implantação do Docker do Azure DevOps Services.</span><span class="sxs-lookup"><span data-stu-id="1da7a-176">The docker-compose.yml files at the solution level are not only more flexible than configuration files at the project or microservice level, but also more secure if you override the environment variables declared at the docker-compose files with values set from your deployment tools, like from Azure DevOps Services Docker deployment tasks.</span></span>

<span data-ttu-id="1da7a-177">Por fim, você pode obter esse valor do código usando Configuration\["ConnectionString"\], como foi mostrado no método ConfigureServices em um exemplo de código anterior.</span><span class="sxs-lookup"><span data-stu-id="1da7a-177">Finally, you can get that value from your code by using Configuration\["ConnectionString"\], as shown in the ConfigureServices method in an earlier code example.</span></span>

<span data-ttu-id="1da7a-178">No entanto, para ambientes de produção, é recomendável explorar outras maneiras de armazenar segredos como as cadeias de conexão.</span><span class="sxs-lookup"><span data-stu-id="1da7a-178">However, for production environments, you might want to explore additional ways on how to store secrets like the connection strings.</span></span> <span data-ttu-id="1da7a-179">Uma excelente maneira de gerenciar segredos do aplicativo é usar o [Azure Key Vault](https://azure.microsoft.com/services/key-vault/).</span><span class="sxs-lookup"><span data-stu-id="1da7a-179">An excellent way to manage application secrets is using [Azure Key Vault](https://azure.microsoft.com/services/key-vault/).</span></span>

<span data-ttu-id="1da7a-180">O Azure Key Vault ajuda a armazenar e proteger as chaves de criptografia e os segredos usados por aplicativos e serviços de nuvem.</span><span class="sxs-lookup"><span data-stu-id="1da7a-180">Azure Key Vault helps to store and safeguard cryptographic keys and secrets used by your cloud applications and services.</span></span> <span data-ttu-id="1da7a-181">Um segredo é qualquer coisa sobre a qual você deseja manter controle estrito, como chaves de API, cadeias de conexão, senhas, etc., e o controle estrito inclui log de uso, definição de expiração, gerenciamento de acesso, *entre outros*.</span><span class="sxs-lookup"><span data-stu-id="1da7a-181">A secret is anything you want to keep strict control of, like API keys, connection strings, passwords, etc. and strict control includes usage logging, setting expiration, managing access, *among others*.</span></span>

<span data-ttu-id="1da7a-182">O Azure Key Vault permite um nível de controle muito detalhado do uso de segredos do aplicativo sem a necessidade de permitir que qualquer pessoa os conheça.</span><span class="sxs-lookup"><span data-stu-id="1da7a-182">Azure Key Vault allows a very detailed control level of the application secrets usage without the need to let anyone know them.</span></span> <span data-ttu-id="1da7a-183">Os segredos podem até mesmo ser girados para segurança avançada, sem interromper o desenvolvimento ou as operações.</span><span class="sxs-lookup"><span data-stu-id="1da7a-183">The secrets can even be rotated for enhanced security without disrupting development or operations.</span></span>

<span data-ttu-id="1da7a-184">Os aplicativos precisam ser registrados no Active Directory da organização, para que possam usar o Key Vault.</span><span class="sxs-lookup"><span data-stu-id="1da7a-184">Applications have to be registered in the organization's Active Directory, so they can use the Key Vault.</span></span>

<span data-ttu-id="1da7a-185">Confira a *documentação Conceitos do Key Vault* para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="1da7a-185">You can check the *Key Vault Concepts documentation* for more details.</span></span>

### <a name="implementing-versioning-in-aspnet-web-apis"></a><span data-ttu-id="1da7a-186">Implementando o controle de versão em APIs Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="1da7a-186">Implementing versioning in ASP.NET Web APIs</span></span>

<span data-ttu-id="1da7a-187">À medida que os requisitos de negócios mudam, novas coleções de recursos podem ser adicionadas, as relações entre os recursos podem mudar e a estrutura dos dados nos recursos pode ser corrigida.</span><span class="sxs-lookup"><span data-stu-id="1da7a-187">As business requirements change, new collections of resources may be added, the relationships between resources might change, and the structure of the data in resources might be amended.</span></span> <span data-ttu-id="1da7a-188">Atualizar uma API Web para lidar com novos requisitos é um processo relativamente simples, mas você precisa considerar os efeitos que essas alterações causarão nos aplicativos cliente que consomem a API Web.</span><span class="sxs-lookup"><span data-stu-id="1da7a-188">Updating a Web API to handle new requirements is a relatively straightforward process, but you must consider the effects that such changes will have on client applications consuming the Web API.</span></span> <span data-ttu-id="1da7a-189">Embora o desenvolvedor que projeta e implementa uma API Web tenha o controle total sobre essa API, ele não tem o mesmo nível de controle sobre aplicativos cliente que possam ter sido criados por organizações terceiras operando remotamente.</span><span class="sxs-lookup"><span data-stu-id="1da7a-189">Although the developer designing and implementing a Web API has full control over that API, the developer does not have the same degree of control over client applications that might be built by third party organizations operating remotely.</span></span>

<span data-ttu-id="1da7a-190">O controle de versão permite que uma API Web indique as funcionalidades e os recursos que ela expõe.</span><span class="sxs-lookup"><span data-stu-id="1da7a-190">Versioning enables a Web API to indicate the features and resources that it exposes.</span></span> <span data-ttu-id="1da7a-191">Assim, um aplicativo cliente pode enviar solicitações para uma versão específica de uma funcionalidade ou de um recurso.</span><span class="sxs-lookup"><span data-stu-id="1da7a-191">A client application can then submit requests to a specific version of a feature or resource.</span></span> <span data-ttu-id="1da7a-192">Há várias abordagens para implementar o controle de versão:</span><span class="sxs-lookup"><span data-stu-id="1da7a-192">There are several approaches to implement versioning:</span></span>

- <span data-ttu-id="1da7a-193">Controle de versão de URI</span><span class="sxs-lookup"><span data-stu-id="1da7a-193">URI versioning</span></span>

- <span data-ttu-id="1da7a-194">Controle de versão de cadeia de caracteres de consulta</span><span class="sxs-lookup"><span data-stu-id="1da7a-194">Query string versioning</span></span>

- <span data-ttu-id="1da7a-195">Controle de versão de cabeçalho</span><span class="sxs-lookup"><span data-stu-id="1da7a-195">Header versioning</span></span>

<span data-ttu-id="1da7a-196">O controle de versão de cadeia de caracteres de consulta e de URI são os mais simples de implementar.</span><span class="sxs-lookup"><span data-stu-id="1da7a-196">Query string and URI versioning are the simplest to implement.</span></span> <span data-ttu-id="1da7a-197">O controle de versão de cabeçalho é uma boa abordagem.</span><span class="sxs-lookup"><span data-stu-id="1da7a-197">Header versioning is a good approach.</span></span> <span data-ttu-id="1da7a-198">No entanto, o controle de versão de cabeçalho não é tão explícito e simples como o controle de versão de URI.</span><span class="sxs-lookup"><span data-stu-id="1da7a-198">However, header versioning not as explicit and straightforward as URI versioning.</span></span> <span data-ttu-id="1da7a-199">Como o controle de versão de URL é o mais simples e o mais explícito, o aplicativo de exemplo eShopOnContainers usa esse o controle de versão de URI.</span><span class="sxs-lookup"><span data-stu-id="1da7a-199">Because URL versioning is the simplest and most explicit, the eShopOnContainers sample application uses URI versioning.</span></span>

<span data-ttu-id="1da7a-200">Com o controle de versão de URI, como no aplicativo de exemplo eShopOnContainers, sempre que você modificar a API Web ou alterar o esquema de recursos, você adicionará um número de versão ao URI de cada recurso.</span><span class="sxs-lookup"><span data-stu-id="1da7a-200">With URI versioning, as in the eShopOnContainers sample application, each time you modify the Web API or change the schema of resources, you add a version number to the URI for each resource.</span></span> <span data-ttu-id="1da7a-201">Os URIs existentes devem continuar a operar como antes, retornando os recursos que estão em conformidade com o esquema que corresponde à versão solicitada.</span><span class="sxs-lookup"><span data-stu-id="1da7a-201">Existing URIs should continue to operate as before, returning resources that conform to the schema that matches the requested version.</span></span>

<span data-ttu-id="1da7a-202">Como mostrado no exemplo de código a seguir, a versão pode ser definida usando o atributo Rota no controlador de API Web, o que torna a versão explícita no URI (v1, neste caso).</span><span class="sxs-lookup"><span data-stu-id="1da7a-202">As shown in the following code example, the version can be set by using the Route attribute in the Web API controller, which makes the version explicit in the URI (v1 in this case).</span></span>

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

<span data-ttu-id="1da7a-203">Esse mecanismo de controle de versão é simples e depende do roteamento que o servidor faz da solicitação para o ponto de extremidade apropriado.</span><span class="sxs-lookup"><span data-stu-id="1da7a-203">This versioning mechanism is simple and depends on the server routing the request to the appropriate endpoint.</span></span> <span data-ttu-id="1da7a-204">No entanto, para obter um controle de versão mais sofisticado, e o melhor método ao usar o REST, você deve usar hipermídia e implementar o [HATEOAS (Hypertext as the Engine of Application State)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#use-hateoas-to-enable-navigation-to-related-resources).</span><span class="sxs-lookup"><span data-stu-id="1da7a-204">However, for a more sophisticated versioning and the best method when using REST, you should use hypermedia and implement [HATEOAS (Hypertext as the Engine of Application State)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#use-hateoas-to-enable-navigation-to-related-resources).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="1da7a-205">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="1da7a-205">Additional resources</span></span>

- <span data-ttu-id="1da7a-206">**Scott Hanselman. Facilitando o controle de versão da API Web RESTful do ASP.NET Core** \\</span><span class="sxs-lookup"><span data-stu-id="1da7a-206">**Scott Hanselman. ASP.NET Core RESTful Web API versioning made easy** \\</span></span>
  <https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx>

- <span data-ttu-id="1da7a-207">**Controle de versão de uma API Web RESTful** \\</span><span class="sxs-lookup"><span data-stu-id="1da7a-207">**Versioning a RESTful web API** \\</span></span>
  <https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api>

- <span data-ttu-id="1da7a-208">**Roy Fielding. Controle de versão, hipermídia e REST** \\</span><span class="sxs-lookup"><span data-stu-id="1da7a-208">**Roy Fielding. Versioning, Hypermedia, and REST** \\</span></span>
  <https://www.infoq.com/articles/roy-fielding-on-versioning>

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a><span data-ttu-id="1da7a-209">Gerando metadados de descrição do Swagger para a API Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1da7a-209">Generating Swagger description metadata from your ASP.NET Core Web API</span></span>

<span data-ttu-id="1da7a-210">O [Swagger](https://swagger.io/) é uma estrutura de software livre muito usada, apoiada por um grande ecossistema de ferramentas que ajuda a projetar, compilar, documentar e consumir APIs RESTful.</span><span class="sxs-lookup"><span data-stu-id="1da7a-210">[Swagger](https://swagger.io/) is a commonly used open source framework backed by a large ecosystem of tools that helps you design, build, document, and consume your RESTful APIs.</span></span> <span data-ttu-id="1da7a-211">Ele está se tornando o padrão no domínio de metadados de descrição de APIs.</span><span class="sxs-lookup"><span data-stu-id="1da7a-211">It is becoming the standard for the APIs description metadata domain.</span></span> <span data-ttu-id="1da7a-212">Você deve incluir os metadados de descrição do Swagger em qualquer tipo de microsserviço, seja ele um microsserviço controlado por dados ou um mais avançado orientado por domínio (conforme será explicado na seção a seguir).</span><span class="sxs-lookup"><span data-stu-id="1da7a-212">You should include Swagger description metadata with any kind of microservice, either data-driven microservices or more advanced domain-driven microservices (as explained in following section).</span></span>

<span data-ttu-id="1da7a-213">A essência do Swagger é a especificação do Swagger, que são metadados de descrição de API em um arquivo JSON ou YAML.</span><span class="sxs-lookup"><span data-stu-id="1da7a-213">The heart of Swagger is the Swagger specification, which is API description metadata in a JSON or YAML file.</span></span> <span data-ttu-id="1da7a-214">A especificação cria o contrato RESTful para a API, detalhando todos os recursos e as operações em dois formatos, legível por pessoas e legível por computadores, para facilitar o desenvolvimento, a descoberta e a integração.</span><span class="sxs-lookup"><span data-stu-id="1da7a-214">The specification creates the RESTful contract for your API, detailing all its resources and operations in both a human- and machine-readable format for easy development, discovery, and integration.</span></span>

<span data-ttu-id="1da7a-215">A especificação é a base da OAS (especificação OpenAPI) e é desenvolvida em uma comunidade aberta, transparente e colaborativa para padronizar a maneira que as interfaces RESTful são definidas.</span><span class="sxs-lookup"><span data-stu-id="1da7a-215">The specification is the basis of the OpenAPI Specification (OAS) and is developed in an open, transparent, and collaborative community to standardize the way RESTful interfaces are defined.</span></span>

<span data-ttu-id="1da7a-216">A especificação define a estrutura de como um serviço pode ser descoberto e como seus recursos são entendidos.</span><span class="sxs-lookup"><span data-stu-id="1da7a-216">The specification defines the structure for how a service can be discovered and how its capabilities understood.</span></span> <span data-ttu-id="1da7a-217">Para obter mais informações, incluindo um editor na Web e exemplos de especificações do Swagger de empresas como Spotify, Uber, Slack e Microsoft, consulte o site do Swagger (<https://swagger.io>).</span><span class="sxs-lookup"><span data-stu-id="1da7a-217">For more information, including a web editor and examples of Swagger specifications from companies like Spotify, Uber, Slack, and Microsoft, see the Swagger site (<https://swagger.io>).</span></span>

### <a name="why-use-swagger"></a><span data-ttu-id="1da7a-218">Por que usar Swagger?</span><span class="sxs-lookup"><span data-stu-id="1da7a-218">Why use Swagger?</span></span>

<span data-ttu-id="1da7a-219">As principais razões para gerar metadados do Swagger para suas APIs são as seguintes.</span><span class="sxs-lookup"><span data-stu-id="1da7a-219">The main reasons to generate Swagger metadata for your APIs are the following.</span></span>

<span data-ttu-id="1da7a-220">**Capacidade para outros produtos consumirem e integrarem suas APIs automaticamente**.</span><span class="sxs-lookup"><span data-stu-id="1da7a-220">**Ability for other products to automatically consume and integrate your APIs**.</span></span> <span data-ttu-id="1da7a-221">Dezenas de produtos e [ferramentas comerciais](https://swagger.io/commercial-tools/) e diversas [estruturas e bibliotecas](https://swagger.io/open-source-integrations/) são compatíveis com o Swagger.</span><span class="sxs-lookup"><span data-stu-id="1da7a-221">Dozens of products and [commercial tools](https://swagger.io/commercial-tools/) and many [libraries and frameworks](https://swagger.io/open-source-integrations/) support Swagger.</span></span> <span data-ttu-id="1da7a-222">A Microsoft tem produtos e ferramentas de alto nível que podem consumir automaticamente as APIs baseadas no Swagger, como os seguintes:</span><span class="sxs-lookup"><span data-stu-id="1da7a-222">Microsoft has high-level products and tools that can automatically consume Swagger-based APIs, such as the following:</span></span>

- <span data-ttu-id="1da7a-223">[AutoRest](https://github.com/Azure/AutoRest).</span><span class="sxs-lookup"><span data-stu-id="1da7a-223">[AutoRest](https://github.com/Azure/AutoRest).</span></span> <span data-ttu-id="1da7a-224">É possível gerar classes de cliente do .NET automaticamente para chamar o Swagger.</span><span class="sxs-lookup"><span data-stu-id="1da7a-224">You can automatically generate .NET client classes for calling Swagger.</span></span> <span data-ttu-id="1da7a-225">Essa ferramenta pode ser usada na CLI e também se integra ao Visual Studio, facilitando o uso por meio da GUI.</span><span class="sxs-lookup"><span data-stu-id="1da7a-225">This tool can be used from the CLI and it also integrates with Visual Studio for easy use through the GUI.</span></span>

- <span data-ttu-id="1da7a-226">[Microsoft Flow](https://flow.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="1da7a-226">[Microsoft Flow](https://flow.microsoft.com/).</span></span> <span data-ttu-id="1da7a-227">É possível [usar e integrar sua API](https://flow.microsoft.com/blog/integrating-custom-api/) automaticamente em um fluxo de trabalho do Microsoft Flow de alto nível, sem precisar de nenhuma habilidade de programação.</span><span class="sxs-lookup"><span data-stu-id="1da7a-227">You can automatically [use and integrate your API](https://flow.microsoft.com/blog/integrating-custom-api/) into a high-level Microsoft Flow workflow, with no programming skills required.</span></span>

- <span data-ttu-id="1da7a-228">[Microsoft PowerApps](https://powerapps.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="1da7a-228">[Microsoft PowerApps](https://powerapps.microsoft.com/).</span></span> <span data-ttu-id="1da7a-229">É possível consumir a API Automaticamente de [aplicativos móveis PowerApps](https://powerapps.microsoft.com/blog/register-and-use-custom-apis-in-powerapps/) criados com o [PowerApps Studio](https://powerapps.microsoft.com/build-powerapps/), sem precisar de nenhuma habilidade de programação.</span><span class="sxs-lookup"><span data-stu-id="1da7a-229">You can automatically consume your API from [PowerApps mobile apps](https://powerapps.microsoft.com/blog/register-and-use-custom-apis-in-powerapps/) built with [PowerApps Studio](https://powerapps.microsoft.com/build-powerapps/), with no programming skills required.</span></span>

- <span data-ttu-id="1da7a-230">[Aplicativos Lógicos do Serviço de Aplicativo do Azure](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span><span class="sxs-lookup"><span data-stu-id="1da7a-230">[Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span></span> <span data-ttu-id="1da7a-231">É possível [usar e integrar sua API a um Aplicativo Lógico do Serviço de Aplicativo do Azure](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api) automaticamente, sem precisar de nenhuma habilidade de programação.</span><span class="sxs-lookup"><span data-stu-id="1da7a-231">You can automatically [use and integrate your API into an Azure App Service Logic App](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), with no programming skills required.</span></span>

<span data-ttu-id="1da7a-232">**Capacidade de gerar a documentação da API automaticamente**.</span><span class="sxs-lookup"><span data-stu-id="1da7a-232">**Ability to automatically generate API documentation**.</span></span> <span data-ttu-id="1da7a-233">Ao criar APIs RESTful em grande escala, como aplicativos complexos baseados em microsserviços, você precisa lidar com vários pontos de extremidade com modelos de dados diferentes usados no conteúdo de solicitação e de resposta.</span><span class="sxs-lookup"><span data-stu-id="1da7a-233">When you create large-scale RESTful APIs, such as complex microservice-based applications, you need to handle many endpoints with different data models used in the request and response payloads.</span></span> <span data-ttu-id="1da7a-234">Ter uma documentação adequada e um gerenciador de API sólido, como o Swagger oferece, é fundamental para o sucesso da API e da adoção pelos desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="1da7a-234">Having proper documentation and having a solid API explorer, as you get with Swagger, is key for the success of your API and adoption by developers.</span></span>

<span data-ttu-id="1da7a-235">Os metadados do Swagger são o que o Microsoft Flow, o PowerApps e os Aplicativos Lógicos do Azure usam para entender como usar as APIs e conectar-se a elas.</span><span class="sxs-lookup"><span data-stu-id="1da7a-235">Swagger's metadata is what Microsoft Flow, PowerApps, and Azure Logic Apps use to understand how to use APIs and connect to them.</span></span>

<span data-ttu-id="1da7a-236">Há várias opções para automatizar a geração de metadados do Swagger para aplicativos de API REST do ASP.NET Core, na forma de páginas de ajuda de API funcional, baseadas na *swagger-ui*.</span><span class="sxs-lookup"><span data-stu-id="1da7a-236">There are several options to automate Swagger metadata generation for ASP.NET Core REST API applications, in the form of functional API help pages, based on *swagger-ui*.</span></span>

<span data-ttu-id="1da7a-237">Provavelmente, a melhor opção conhecida é o [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore), que está sendo usado no [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) e o qual abordaremos em detalhes neste guia, mas também há a opção de usar o [NSwag](https://github.com/RSuter/NSwag), que pode gerar clientes de API em Typescript e C\#, bem como em controladores em C\#, com base em uma especificação do Swagger ou do OpenAPI e, até mesmo, examinando a .dll que contém os controladores, usando o [NSwagStudio](https://github.com/RSuter/NSwag/wiki/NSwagStudio).</span><span class="sxs-lookup"><span data-stu-id="1da7a-237">Probably the best know is [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) which is currently used in [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) and we'll cover in some detail in this guide but there's also the option to use [NSwag](https://github.com/RSuter/NSwag), that can generate Typescript and C\# API clients, as well as C\# controllers, from a Swagger or OpenAPI specification and even by scanning the .dll that contains the controllers, using [NSwagStudio](https://github.com/RSuter/NSwag/wiki/NSwagStudio).</span></span>

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a><span data-ttu-id="1da7a-238">Como automatizar a geração de metadados do Swagger para a API com o pacote NuGet Swashbuckle</span><span class="sxs-lookup"><span data-stu-id="1da7a-238">How to automate API Swagger metadata generation with the Swashbuckle NuGet package</span></span>

<span data-ttu-id="1da7a-239">A geração manual de metadados do Swagger (em um arquivo JSON ou YAML) pode ser um trabalho entediante.</span><span class="sxs-lookup"><span data-stu-id="1da7a-239">Generating Swagger metadata manually (in a JSON or YAML file) can be tedious work.</span></span> <span data-ttu-id="1da7a-240">No entanto, é possível automatizar a descoberta de serviços do ASP.NET Web API usando o [pacote NuGet Swashbuckle](https://aka.ms/swashbuckledotnetcore) para gerar dinamicamente os metadados do Swagger para a API.</span><span class="sxs-lookup"><span data-stu-id="1da7a-240">However, you can automate API discovery of ASP.NET Web API services by using the [Swashbuckle NuGet package](https://aka.ms/swashbuckledotnetcore) to dynamically generate Swagger API metadata.</span></span>

<span data-ttu-id="1da7a-241">O Swashbuckle gera automaticamente os metadados do Swagger para os projetos do ASP.NET Web API.</span><span class="sxs-lookup"><span data-stu-id="1da7a-241">Swashbuckle automatically generates Swagger metadata for your ASP.NET Web API projects.</span></span> <span data-ttu-id="1da7a-242">Ele é compatível com projetos da API Web ASP.NET Core, do ASP.NET Web API tradicional e de outros tipos, como os microsserviços de Aplicativo de API do Azure, Aplicativo Móvel Azure, Azure Service Fabric com base no ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="1da7a-242">It supports ASP.NET Core Web API projects and the traditional ASP.NET Web API and any other flavor, such as Azure API App, Azure Mobile App, Azure Service Fabric microservices based on ASP.NET.</span></span> <span data-ttu-id="1da7a-243">Ele também é compatível com a API Web simples implantada em contêineres, como no aplicativo de referência.</span><span class="sxs-lookup"><span data-stu-id="1da7a-243">It also supports plain Web API deployed on containers, as in for the reference application.</span></span>

<span data-ttu-id="1da7a-244">O Swashbuckle combina o Gerenciador de API e o Swagger ou o [swagger-ui](https://github.com/swagger-api/swagger-ui) para fornecer uma experiência avançada de descoberta e de documentação aos consumidores da API.</span><span class="sxs-lookup"><span data-stu-id="1da7a-244">Swashbuckle combines API Explorer and Swagger or [swagger-ui](https://github.com/swagger-api/swagger-ui) to provide a rich discovery and documentation experience for your API consumers.</span></span> <span data-ttu-id="1da7a-245">Além do mecanismo gerador de metadados do Swagger, o Swashbuckle também contém uma versão incorporada do swagger-ui, que ele oferecerá automaticamente quando for instalado.</span><span class="sxs-lookup"><span data-stu-id="1da7a-245">In addition to its Swagger metadata generator engine, Swashbuckle also contains an embedded version of swagger-ui, which it will automatically serve up once Swashbuckle is installed.</span></span>

<span data-ttu-id="1da7a-246">Isso significa que você pode complementar a API com uma ótima interface do usuário de descoberta para ajudar os desenvolvedores a usarem a API.</span><span class="sxs-lookup"><span data-stu-id="1da7a-246">This means you can complement your API with a nice discovery UI to help developers to use your API.</span></span> <span data-ttu-id="1da7a-247">Isso exige uma quantidade muito pequena de código e manutenção porque ela é gerada automaticamente, permitindo que você se concentre na API.</span><span class="sxs-lookup"><span data-stu-id="1da7a-247">It requires a very small amount of code and maintenance because it is automatically generated, allowing you to focus on building your API.</span></span> <span data-ttu-id="1da7a-248">O resultado do Gerenciador de API é semelhante ao da Figura 6-8.</span><span class="sxs-lookup"><span data-stu-id="1da7a-248">The result for the API Explorer looks like Figure 6-8.</span></span>

![A documentação da API de interface do usuário do Swagger gerada pelo Swashbuckle inclui todas as ações publicadas.](./media/image9.png)

<span data-ttu-id="1da7a-250">**Figura 6-8**.</span><span class="sxs-lookup"><span data-stu-id="1da7a-250">**Figure 6-8**.</span></span> <span data-ttu-id="1da7a-251">Gerenciador de API do Swashbuckle baseado nos metadados do Swagger – microsserviço de catálogo do eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="1da7a-251">Swashbuckle API Explorer based on Swagger metadata—eShopOnContainers catalog microservice</span></span>

<span data-ttu-id="1da7a-252">O Gerenciador de API não é o mais importante aqui.</span><span class="sxs-lookup"><span data-stu-id="1da7a-252">The API explorer is not the most important thing here.</span></span> <span data-ttu-id="1da7a-253">Quando a API Web consegue se descrever nos metadados do Swagger, ela pode ser usada diretamente por meio das ferramentas baseadas no Swagger, incluindo geradores de código de classe de proxy de cliente que podem direcionar a várias plataformas.</span><span class="sxs-lookup"><span data-stu-id="1da7a-253">Once you have a Web API that can describe itself in Swagger metadata, your API can be used seamlessly from Swagger-based tools, including client proxy-class code generators that can target many platforms.</span></span> <span data-ttu-id="1da7a-254">Por exemplo, conforme mencionado, o [AutoRest](https://github.com/Azure/AutoRest) gera as classes de cliente do .NET automaticamente.</span><span class="sxs-lookup"><span data-stu-id="1da7a-254">For example, as mentioned, [AutoRest](https://github.com/Azure/AutoRest) automatically generates .NET client classes.</span></span> <span data-ttu-id="1da7a-255">Mas ferramentas adicionais como [swagger-codegen](https://github.com/swagger-api/swagger-codegen) também estão disponíveis, permitindo automaticamente a geração de código das bibliotecas clientes da API, de stubs de servidor e da documentação.</span><span class="sxs-lookup"><span data-stu-id="1da7a-255">But additional tools like [swagger-codegen](https://github.com/swagger-api/swagger-codegen) are also available, which allow code generation of API client libraries, server stubs, and documentation automatically.</span></span>

<span data-ttu-id="1da7a-256">Atualmente, o Swashbuckle consiste em vários pacotes NuGet internos no metapacote de alto nível [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore) para aplicativos ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="1da7a-256">Currently, Swashbuckle consists of five internal NuGet packages under the high-level meta- package [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore) for ASP.NET Core applications.</span></span>

<span data-ttu-id="1da7a-257">Depois de instalar esses pacotes NuGet no projeto de API Web, você precisará configurar o Swagger na classe de inicialização, como no seguinte código (simplificado):</span><span class="sxs-lookup"><span data-stu-id="1da7a-257">After you have installed these NuGet packages in your Web API project, you need to configure Swagger in the Startup class, as in the following code (simplified):</span></span>

```csharp
public class Startup
{
    public IConfigurationRoot Configuration { get; }
    // Other startup code...

    public void ConfigureServices(IServiceCollection services)
    {
        // Other ConfigureServices() code...

        // Add framework services.
        services.AddSwaggerGen(options =>
        {
            options.DescribeAllEnumsAsStrings();
            options.SwaggerDoc("v1", new Swashbuckle.AspNetCore.Swagger.Info
            {
                Title = "eShopOnContainers - Catalog HTTP API",
                Version = "v1",
                Description = "The Catalog Microservice HTTP API. This is a Data-Driven/CRUD microservice sample",
                TermsOfService = "Terms Of Service"
            });
        });

        // Other ConfigureServices() code...
    }

    public void Configure(IApplicationBuilder app,
        IHostingEnvironment env,
        ILoggerFactory loggerFactory)
    {
        // Other Configure() code...
        // ...
        app.UseSwagger()
            .UseSwaggerUI(c =>
            {
                c.SwaggerEndpoint("/swagger/v1/swagger.json", "My API V1");
            });
    }
}
```

<span data-ttu-id="1da7a-258">Depois que isso for feito, você poderá iniciar o aplicativo e procurar o JSON do Swagger e os pontos de extremidade da interface do usuário usando URLs como estas:</span><span class="sxs-lookup"><span data-stu-id="1da7a-258">Once this is done, you can start your application and browse the following Swagger JSON and UI endpoints using URLs like these:</span></span>

```url
  http://<your-root-url>/swagger/v1/swagger.json

  http://<your-root-url>/swagger/
```

<span data-ttu-id="1da7a-259">Você já viu a interface do usuário gerada, criada pelo Swashbuckle para uma URL como `http://<your-root-url>/swagger`.</span><span class="sxs-lookup"><span data-stu-id="1da7a-259">You previously saw the generated UI created by Swashbuckle for a URL like `http://<your-root-url>/swagger`.</span></span> <span data-ttu-id="1da7a-260">Na Figura 6-9, veja também como é possível testar qualquer método de API.</span><span class="sxs-lookup"><span data-stu-id="1da7a-260">In Figure 6-9 you can also see how you can test any API method.</span></span>

![O detalhe da API de interface do usuário do Swagger apresenta uma amostra da resposta e pode ser usado para executar a API real, que é ótima para a descoberta do desenvolvedor.](./media/image10.png)

<span data-ttu-id="1da7a-262">**Figura 6-9**.</span><span class="sxs-lookup"><span data-stu-id="1da7a-262">**Figure 6-9**.</span></span> <span data-ttu-id="1da7a-263">Interface do usuário do Swashbuckle testando o método da API de itens/catálogo</span><span class="sxs-lookup"><span data-stu-id="1da7a-263">Swashbuckle UI testing the Catalog/Items API method</span></span>

<span data-ttu-id="1da7a-264">A Figura 6-10 mostra os metadados JSON do Swagger gerados por meio do microsserviço eShopOnContainers (que é o que as ferramentas usam em segundo plano) quando você solicita `http://<your-root-url>/swagger/v1/swagger.json` usando o [Postman](https://www.getpostman.com/).</span><span class="sxs-lookup"><span data-stu-id="1da7a-264">Figure 6-10 shows the Swagger JSON metadata generated from the eShopOnContainers microservice (which is what the tools use underneath) when you request `http://<your-root-url>/swagger/v1/swagger.json` using [Postman](https://www.getpostman.com/).</span></span>

![Interface do usuário de exemplo do Postman mostrando metadados JSON do Swagger](./media/image11.png)

<span data-ttu-id="1da7a-266">**Figura 6-10**.</span><span class="sxs-lookup"><span data-stu-id="1da7a-266">**Figure 6-10**.</span></span> <span data-ttu-id="1da7a-267">Metadados JSON do Swagger</span><span class="sxs-lookup"><span data-stu-id="1da7a-267">Swagger JSON metadata</span></span>

<span data-ttu-id="1da7a-268">É simples assim.</span><span class="sxs-lookup"><span data-stu-id="1da7a-268">It is that simple.</span></span> <span data-ttu-id="1da7a-269">E como são gerados automaticamente, os metadados do Swagger aumentarão à medida que você adicionar mais funcionalidades à API.</span><span class="sxs-lookup"><span data-stu-id="1da7a-269">And because it is automatically generated, the Swagger metadata will grow when you add more functionality to your API.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="1da7a-270">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="1da7a-270">Additional resources</span></span>

- <span data-ttu-id="1da7a-271">**Páginas de Ajuda do ASP.NET Web API usando o Swagger** \\</span><span class="sxs-lookup"><span data-stu-id="1da7a-271">**ASP.NET Web API Help Pages using Swagger** \\</span></span>
  [https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger](/aspnet/core/tutorials/web-api-help-pages-using-swagger)

- <span data-ttu-id="1da7a-272">**Introdução ao Swashbuckle e ao ASP.NET Core** \\</span><span class="sxs-lookup"><span data-stu-id="1da7a-272">**Get started with Swashbuckle and ASP.NET Core** \\</span></span>
  [https://docs.microsoft.com/aspnet/core/tutorials/getting-started-with-swashbuckle](/aspnet/core/tutorials/getting-started-with-swashbuckle)

- <span data-ttu-id="1da7a-273">**Introdução ao NSwag e ao ASP.NET Core** \\</span><span class="sxs-lookup"><span data-stu-id="1da7a-273">**Get started with NSwag and ASP.NET Core** \\</span></span>
  [https://docs.microsoft.com/aspnet/core/tutorials/getting-started-with-nswag](/aspnet/core/tutorials/getting-started-with-nswag)

> [!div class="step-by-step"]
> <span data-ttu-id="1da7a-274">[Anterior](microservice-application-design.md)
> [Próximo](multi-container-applications-docker-compose.md)</span><span class="sxs-lookup"><span data-stu-id="1da7a-274">[Previous](microservice-application-design.md)
[Next](multi-container-applications-docker-compose.md)</span></span>
