---
title: "Criar um microsserviço CRUD simple controlada por dados"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Criar um microsserviço CRUD simple controlada por dados"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: b814d344f2c78e7cf57f9e2896cf1d6b52db38d9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="creating-a-simple-data-driven-crud-microservice"></a><span data-ttu-id="2335e-104">Criar um microsserviço CRUD simple controlada por dados</span><span class="sxs-lookup"><span data-stu-id="2335e-104">Creating a simple data-driven CRUD microservice</span></span>

<span data-ttu-id="2335e-105">Esta seção descreve como criar um simples microsserviço executa criar, ler, atualização e operações de exclusão (CRUD) em uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="2335e-105">This section outlines how to create a simple microservice that performs create, read, update, and delete (CRUD) operations on a data source.</span></span>

## <a name="designing-a-simple-crud-microservice"></a><span data-ttu-id="2335e-106">Criar um microsserviço CRUD simple</span><span class="sxs-lookup"><span data-stu-id="2335e-106">Designing a simple CRUD microservice</span></span>

<span data-ttu-id="2335e-107">Do ponto de vista do design, esse tipo de microsserviço em contêineres é muito simple.</span><span class="sxs-lookup"><span data-stu-id="2335e-107">From a design point of view, this type of containerized microservice is very simple.</span></span> <span data-ttu-id="2335e-108">Talvez o problema a resolver é simple ou talvez a implementação é apenas uma prova de conceito.</span><span class="sxs-lookup"><span data-stu-id="2335e-108">Perhaps the problem to solve is simple, or perhaps the implementation is only a proof of concept.</span></span>

![](./media/image4.png)

<span data-ttu-id="2335e-109">**Figura 8-4**.</span><span class="sxs-lookup"><span data-stu-id="2335e-109">**Figure 8-4**.</span></span> <span data-ttu-id="2335e-110">Design interno microservices CRUD simples</span><span class="sxs-lookup"><span data-stu-id="2335e-110">Internal design for simple CRUD microservices</span></span>

<span data-ttu-id="2335e-111">Um exemplo desse tipo de serviço simples de unidade de dados é o microsserviço de catálogo do aplicativo de exemplo eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="2335e-111">An example of this kind of simple data-drive service is the catalog microservice from the eShopOnContainers sample application.</span></span> <span data-ttu-id="2335e-112">Esse tipo de serviço implementa todos os seus recursos em um único projeto de API da Web do ASP.NET Core que inclui classes para seu modelo de dados, sua lógica de negócios e seu código de acesso a dados.</span><span class="sxs-lookup"><span data-stu-id="2335e-112">This type of service implements all its functionality in a single ASP.NET Core Web API project that includes classes for its data model, its business logic, and its data access code.</span></span> <span data-ttu-id="2335e-113">Ele também armazena seus dados relacionados em um banco de dados em execução no SQL Server (como outro contêiner para fins de desenvolvimento/teste), mas também pode ser qualquer host regular do SQL Server, conforme mostrado na Figura 8-5.</span><span class="sxs-lookup"><span data-stu-id="2335e-113">It also stores its related data in a database running in SQL Server (as another container for dev/test purposes), but could also be any regular SQL Server host, as shown in Figure 8-5.</span></span>

![](./media/image5.png)

<span data-ttu-id="2335e-114">**Figura 8-5**.</span><span class="sxs-lookup"><span data-stu-id="2335e-114">**Figure 8-5**.</span></span> <span data-ttu-id="2335e-115">Design de microsserviço simples de dados controlada por/CRUD</span><span class="sxs-lookup"><span data-stu-id="2335e-115">Simple data-driven/CRUD microservice design</span></span>

<span data-ttu-id="2335e-116">Quando você estiver desenvolvendo esse tipo de serviço, você só precisa [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) e uma API de acesso a dados ou ORM como [Entity Framework Core](https://docs.microsoft.com/ef/core/index).</span><span class="sxs-lookup"><span data-stu-id="2335e-116">When you are developing this kind of service, you only need [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) and a data-access API or ORM like [Entity Framework Core](https://docs.microsoft.com/ef/core/index).</span></span> <span data-ttu-id="2335e-117">Você também pode gerar [Swagger](http://swagger.io/) automaticamente por meio de metadados [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) para fornecer uma descrição do que o seu serviço oferece, conforme explicado na próxima seção.</span><span class="sxs-lookup"><span data-stu-id="2335e-117">You could also generate [Swagger](http://swagger.io/) metadata automatically through [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) to provide a description of what your service offers, as explained in the next section.</span></span>

<span data-ttu-id="2335e-118">Observe que a execução de um servidor de banco de dados como o SQL Server em um contêiner do Docker é ótimo para ambientes de desenvolvimento, porque você pode ter todas as suas dependências até e em execução sem a necessidade de provisionar um banco de dados na nuvem ou local.</span><span class="sxs-lookup"><span data-stu-id="2335e-118">Note that running a database server like SQL Server within a Docker container is great for development environments, because you can have all your dependencies up and running without needing to provision a database in the cloud or on-premises.</span></span> <span data-ttu-id="2335e-119">Isso é muito conveniente quando executando a integração de testes.</span><span class="sxs-lookup"><span data-stu-id="2335e-119">This is very convenient when running integration tests.</span></span> <span data-ttu-id="2335e-120">No entanto, para ambientes de produção, executar um servidor de banco de dados em um contêiner não é recomendável, porque você normalmente não tem alta disponibilidade com essa abordagem.</span><span class="sxs-lookup"><span data-stu-id="2335e-120">However, for production environments, running a database server in a container is not recommended, because you usually do not get high availability with that approach.</span></span> <span data-ttu-id="2335e-121">Para um ambiente de produção no Azure, é recomendável que você use o banco de dados de SQL Azure ou qualquer outra tecnologia de banco de dados que pode fornecer alta disponibilidade e alto desempenho.</span><span class="sxs-lookup"><span data-stu-id="2335e-121">For a production environment in Azure, it is recommended that you use Azure SQL DB or any other database technology that can provide high availability and high scalability.</span></span> <span data-ttu-id="2335e-122">Por exemplo, para uma abordagem NoSQL, você pode escolher documentos.</span><span class="sxs-lookup"><span data-stu-id="2335e-122">For example, for a NoSQL approach, you might choose DocumentDB.</span></span>

<span data-ttu-id="2335e-123">Por fim, editando os arquivos de metadados do Dockerfile e compose.yml docker, você pode configurar como a imagem desse contêiner será criada – qual imagem de base-la será usar, além de configurações, como nomes internos e externos e portas TCP de design.</span><span class="sxs-lookup"><span data-stu-id="2335e-123">Finally, by editing the Dockerfile and docker-compose.yml metadata files, you can configure how the image of this container will be created—what base image it will use, plus design settings such as internal and external names and TCP ports.</span></span> 

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a><span data-ttu-id="2335e-124">Implementando um microsserviço CRUD simple com o ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2335e-124">Implementing a simple CRUD microservice with ASP.NET Core</span></span>

<span data-ttu-id="2335e-125">Para implementar um microsserviço CRUD simple usando o .NET Core e o Visual Studio, você inicia criando um projeto de API da Web do ASP.NET Core simples (em execução no .NET Core para que ele pode ser executado em um host Linux Docker), como 8-6 mostrado na figura.</span><span class="sxs-lookup"><span data-stu-id="2335e-125">To implement a simple CRUD microservice using .NET Core and Visual Studio, you start by creating a simple ASP.NET Core Web API project (running on .NET Core so it can run on a Linux Docker host), as shown in Figure 8-6.</span></span>

  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------
  <span data-ttu-id="2335e-126">![](./media/image6.png)   ![](./media/image7.png)</span><span class="sxs-lookup"><span data-stu-id="2335e-126">![](./media/image6.png)   ![](./media/image7.png)</span></span>
  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------

<span data-ttu-id="2335e-127">**Figura 8-6**.</span><span class="sxs-lookup"><span data-stu-id="2335e-127">**Figure 8-6**.</span></span> <span data-ttu-id="2335e-128">Criando um projeto de API da Web do ASP.NET Core no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2335e-128">Creating an ASP.NET Core Web API project in Visual Studio</span></span>

<span data-ttu-id="2335e-129">Depois de criar o projeto, você pode implementar os controladores MVC como você faria em qualquer outro projeto de API da Web, usando a API do Entity Framework ou outros API.</span><span class="sxs-lookup"><span data-stu-id="2335e-129">After creating the project, you can implement your MVC controllers as you would in any other Web API project, using the Entity Framework API or other API.</span></span> <span data-ttu-id="2335e-130">No projeto eShopOnContainers.Catalog.API, você pode ver que as dependências principais para que microsserviço são apenas ASP.NET Core em si, Entity Framework e Swashbuckle, conforme mostrado na Figura 8-7.</span><span class="sxs-lookup"><span data-stu-id="2335e-130">In the eShopOnContainers.Catalog.API project, you can see that the main dependencies for that microservice are just ASP.NET Core itself, Entity Framework, and Swashbuckle, as shown in Figure 8-7.</span></span>

![](./media/image8.PNG)

<span data-ttu-id="2335e-131">**Figura 8-7**.</span><span class="sxs-lookup"><span data-stu-id="2335e-131">**Figure 8-7**.</span></span> <span data-ttu-id="2335e-132">Dependências em um microsserviço CRUD Web API simple</span><span class="sxs-lookup"><span data-stu-id="2335e-132">Dependencies in a simple CRUD Web API microservice</span></span>

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a><span data-ttu-id="2335e-133">Implementando serviços de API da Web de CRUD com o Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="2335e-133">Implementing CRUD Web API services with Entity Framework Core</span></span>

<span data-ttu-id="2335e-134">Núcleo do Entity Framework (EF) é leve e extensível, e tecnologia de acesso de versão de plataforma cruzada dos dados do Entity Framework populares.</span><span class="sxs-lookup"><span data-stu-id="2335e-134">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="2335e-135">Núcleo do EF é mapeador relacional de objeto (ORM) que permite que os desenvolvedores de .NET trabalhar com um banco de dados usando objetos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2335e-135">EF Core is an object-relational mapper (ORM) that enables .NET developers to work with a database using .NET objects.</span></span>

<span data-ttu-id="2335e-136">O catálogo microsserviço usa EF e o provedor do SQL Server porque seu banco de dados está em execução em um contêiner com o SQL Server para a imagem do Docker do Linux.</span><span class="sxs-lookup"><span data-stu-id="2335e-136">The catalog microservice uses EF and the SQL Server provider because its database is running in a container with the SQL Server for Linux Docker image.</span></span> <span data-ttu-id="2335e-137">No entanto, o banco de dados pode ser implantado em qualquer servidor SQL, como o local do Windows ou o banco de dados do Azure SQL.</span><span class="sxs-lookup"><span data-stu-id="2335e-137">However, the database could be deployed into any SQL Server, such as Windows on-premises or Azure SQL DB.</span></span> <span data-ttu-id="2335e-138">A única coisa que você precisa alterar é a cadeia de caracteres de conexão em microsserviço a API Web do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="2335e-138">The only thing you would need to change is the connection string in the ASP.NET Web API microservice.</span></span>

#### <a name="add-entity-framework-core-to-your-dependencies"></a><span data-ttu-id="2335e-139">Adicionar o Entity Framework Core para as suas dependências</span><span class="sxs-lookup"><span data-stu-id="2335e-139">Add Entity Framework Core to your dependencies</span></span>

<span data-ttu-id="2335e-140">Você pode instalar o pacote NuGet para o provedor de banco de dados que você deseja usar, no caso do SQL Server, de dentro do IDE do Visual Studio ou com o console do NuGet.</span><span class="sxs-lookup"><span data-stu-id="2335e-140">You can install the NuGet package for the database provider you want to use, in this case SQL Server, from within the Visual Studio IDE or with the NuGet console.</span></span> <span data-ttu-id="2335e-141">Use o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="2335e-141">Use the following command:</span></span>

```
  Install-Package Microsoft.EntityFrameworkCore.SqlServer
```

#### <a name="the-data-model"></a><span data-ttu-id="2335e-142">O modelo de dados</span><span class="sxs-lookup"><span data-stu-id="2335e-142">The data model</span></span>

<span data-ttu-id="2335e-143">Com o núcleo do EF, acesso a dados é executado usando um modelo.</span><span class="sxs-lookup"><span data-stu-id="2335e-143">With EF Core, data access is performed by using a model.</span></span> <span data-ttu-id="2335e-144">Um modelo é composto de classes de entidade e um contexto derivado que representa uma sessão com o banco de dados, permitindo que você consultar e salvar dados.</span><span class="sxs-lookup"><span data-stu-id="2335e-144">A model is made up of entity classes and a derived context that represents a session with the database, allowing you to query and save data.</span></span> <span data-ttu-id="2335e-145">Você pode gerar um modelo de banco de dados existente, manualmente um modelo para coincidir com seu banco de dados de código ou usar migrações EF para criar um banco de dados do seu modelo (e evolui-lo como o modelo é alterado ao longo do tempo).</span><span class="sxs-lookup"><span data-stu-id="2335e-145">You can generate a model from an existing database, manually code a model to match your database, or use EF migrations to create a database from your model (and evolve it as your model changes over time).</span></span> <span data-ttu-id="2335e-146">Para o catálogo microsserviço estamos usando a última abordagem.</span><span class="sxs-lookup"><span data-stu-id="2335e-146">For the catalog microservice we are using the last approach.</span></span> <span data-ttu-id="2335e-147">Você pode ver um exemplo da classe da entidade CatalogItem no exemplo de código a seguir, que é um simples objeto Plain Old CLR ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) classe da entidade.</span><span class="sxs-lookup"><span data-stu-id="2335e-147">You can see an example of the CatalogItem entity class in the following code example, which is a simple Plain Old CLR Object ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) entity class.</span></span>

```csharp
public class CatalogItem
{
    public int Id { get; set; }
    public string Name { get; set; }
    public string Description { get; set; }
    public decimal Price { get; set; }
    public string PictureUri { get; set; }
    public int CatalogTypeId { get; set; }
    public CatalogType CatalogType { get; set; }
    public int CatalogBrandId { get; set; }
    public CatalogBrand CatalogBrand { get; set; }
    public CatalogItem() { }
}
```

<span data-ttu-id="2335e-148">Você também precisa de um DbContext que representa uma sessão com o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="2335e-148">You also need a DbContext that represents a session with the database.</span></span> <span data-ttu-id="2335e-149">Para o catálogo microsserviço, a classe de CatalogContext deriva da classe DbContext base, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="2335e-149">For the catalog microservice, the CatalogContext class derives from the DbContext base class, as shown in the following example:</span></span>

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

<span data-ttu-id="2335e-150">Você pode ter um código adicional na implementação do DbContext.</span><span class="sxs-lookup"><span data-stu-id="2335e-150">You can have additional code in the DbContext implementation.</span></span> <span data-ttu-id="2335e-151">Por exemplo, o aplicativo de exemplo, temos um método OnModelCreating na classe CatalogContext que preenche automaticamente os dados de exemplo na primeira vez que tentar acessar o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="2335e-151">For example, in the sample application, we have an OnModelCreating method in the CatalogContext class that automatically populates the sample data the first time it tries to access the database.</span></span> <span data-ttu-id="2335e-152">Esse método é útil para dados de demonstração.</span><span class="sxs-lookup"><span data-stu-id="2335e-152">This method is useful for demo data.</span></span> <span data-ttu-id="2335e-153">Você também pode usar o método OnModelCreating para personalizar os mapeamentos de entidades de objeto/banco de dados com muitos outros [pontos de extensibilidade do EF](https://blogs.msdn.microsoft.com/dotnet/2016/09/29/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).</span><span class="sxs-lookup"><span data-stu-id="2335e-153">You can also use the OnModelCreating method to customize object/database entity mappings with many other [EF extensibility points](https://blogs.msdn.microsoft.com/dotnet/2016/09/29/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).</span></span>

<span data-ttu-id="2335e-154">Você pode ver mais detalhes sobre OnModelCreating no [Implementando a camada de persistência de infraestrutura com o Entity Framework Core](#implementing_infrastructure_persistence) seção mais adiante neste manual.</span><span class="sxs-lookup"><span data-stu-id="2335e-154">You can see further details about OnModelCreating in the [Implementing the infrastructure-persistence layer with Entity Framework Core](#implementing_infrastructure_persistence) section later in this book.</span></span>

##### <a name="querying-data-from-web-api-controllers"></a><span data-ttu-id="2335e-155">Consultar dados de controladores de API da Web</span><span class="sxs-lookup"><span data-stu-id="2335e-155">Querying data from Web API controllers</span></span>

<span data-ttu-id="2335e-156">Instâncias de suas classes de entidade normalmente são recuperadas do banco de dados usando linguagem integrado LINQ (consulta), conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="2335e-156">Instances of your entity classes are typically retrieved from the database using Language Integrated Query (LINQ), as shown in the following example:</span></span>

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
        _catalogIntegrationEventService = catalogIntegrationEventService ??
           throw new ArgumentNullException(nameof(catalogIntegrationEventService));
        _settings = settings.Value;
        ((DbContext)context).ChangeTracker.QueryTrackingBehavior = QueryTrackingBehavior.NoTracking;
    }

    // GET api/v1/[controller]/items[?pageSize=3&pageIndex=10]
    [HttpGet]
    [Route("[action]")]
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

##### <a name="saving-data"></a><span data-ttu-id="2335e-157">Salvando dados</span><span class="sxs-lookup"><span data-stu-id="2335e-157">Saving data</span></span>

<span data-ttu-id="2335e-158">Dados são criados, excluídos e modificados no banco de dados usando as instâncias de suas classes de entidade.</span><span class="sxs-lookup"><span data-stu-id="2335e-158">Data is created, deleted, and modified in the database using instances of your entity classes.</span></span> <span data-ttu-id="2335e-159">Você pode adicionar código como o exemplo a seguir embutido (dados fictícios, neste caso) para os controladores de API da Web.</span><span class="sxs-lookup"><span data-stu-id="2335e-159">You could add code like the following hard-coded example (mock data, in this case) to your Web API controllers.</span></span>

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
   Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a><span data-ttu-id="2335e-160">Injeção de dependência em controladores de API da Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2335e-160">Dependency Injection in ASP.NET Core and Web API controllers</span></span>

<span data-ttu-id="2335e-161">No núcleo do ASP.NET, você pode usar injeção de dependência (DI) fora da caixa.</span><span class="sxs-lookup"><span data-stu-id="2335e-161">In ASP.NET Core you can use Dependency Injection (DI) out of the box.</span></span> <span data-ttu-id="2335e-162">Você não precisa configurar um contêiner de inversão de controle (IoC) de terceiros, embora você pode conectar seu contêiner IoC preferencial da infraestrutura do ASP.NET Core se você quiser.</span><span class="sxs-lookup"><span data-stu-id="2335e-162">You do not need to set up a third-party Inversion of Control (IoC) container, although you can plug your preferred IoC container into the ASP.NET Core infrastructure if you want.</span></span> <span data-ttu-id="2335e-163">Nesse caso, isso significa que você pode injetar diretamente o EF DBContext necessária ou repositórios adicionais por meio do construtor do controlador.</span><span class="sxs-lookup"><span data-stu-id="2335e-163">In this case, it means that you can directly inject the required EF DBContext or additional repositories through the controller constructor.</span></span> <span data-ttu-id="2335e-164">No exemplo acima da classe CatalogController, estamos injetando um objeto do tipo CatalogContext além de outros objetos por meio do construtor CatalogController.</span><span class="sxs-lookup"><span data-stu-id="2335e-164">In the example above of the CatalogController class, we are injecting an object of CatalogContext type plus other objects through the CatalogController constructor.</span></span>

<span data-ttu-id="2335e-165">Uma configuração importante para configurar o projeto de API da Web é o registro de classe DbContext no contêiner de IoC do serviço.</span><span class="sxs-lookup"><span data-stu-id="2335e-165">An important configuration to set up in the Web API project is the DbContext class registration into the service’s IoC container.</span></span> <span data-ttu-id="2335e-166">Você normalmente faz isso na classe de inicialização ao chamar os serviços. Método AddDbContext dentro do método ConfigureServices, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="2335e-166">You typically do so in the Startup class by calling the services.AddDbContext method inside the ConfigureServices method, as shown in the following example:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
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

### <a name="additional-resources"></a><span data-ttu-id="2335e-167">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="2335e-167">Additional resources</span></span>

-   <span data-ttu-id="2335e-168">**Consultando dados**
    [*https://docs.microsoft.com/ef/core/querying/index*](https://docs.microsoft.com/ef/core/querying/index)</span><span class="sxs-lookup"><span data-stu-id="2335e-168">**Querying Data**
[*https://docs.microsoft.com/ef/core/querying/index*](https://docs.microsoft.com/ef/core/querying/index)</span></span>

-   <span data-ttu-id="2335e-169">**Salvando dados**
    [*https://docs.microsoft.com/ef/core/saving/index*](https://docs.microsoft.com/ef/core/saving/index)</span><span class="sxs-lookup"><span data-stu-id="2335e-169">**Saving Data**
[*https://docs.microsoft.com/ef/core/saving/index*](https://docs.microsoft.com/ef/core/saving/index)</span></span>

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a><span data-ttu-id="2335e-170">As variáveis banco de dados de cadeia de caracteres e o ambiente de conexão usadas por contêineres do Docker</span><span class="sxs-lookup"><span data-stu-id="2335e-170">The DB connection string and environment variables used by Docker containers</span></span>

<span data-ttu-id="2335e-171">Você pode usar as configurações do ASP.NET Core e adicionar uma propriedade ConnectionString para o arquivo settings.json, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="2335e-171">You can use the ASP.NET Core settings and add a ConnectionString property to your settings.json file as shown in the following example:</span></span>

```csharp
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

<span data-ttu-id="2335e-172">O arquivo de settings.json pode ter valores padrão para a propriedade ConnectionString ou para qualquer outra propriedade.</span><span class="sxs-lookup"><span data-stu-id="2335e-172">The settings.json file can have default values for the ConnectionString property or for any other property.</span></span> <span data-ttu-id="2335e-173">No entanto, essas propriedades serão substituídas pelos valores de variáveis de ambiente que você especificar no arquivo compose.override.yml docker.</span><span class="sxs-lookup"><span data-stu-id="2335e-173">However, those properties will be overridden by the values of environment variables that you specify in the docker-compose.override.yml file.</span></span>

<span data-ttu-id="2335e-174">Dos seus arquivos de docker compose.yml ou compose.override.yml docker, é possível inicializar as variáveis de ambiente para que Docker configurará-los como variáveis de ambiente do sistema operacional, conforme mostrado no seguinte arquivo docker compose.override.yml (a conexão cadeia de caracteres e outras linhas quebrar neste exemplo, mas ele não seria quebrar em seu próprio arquivo).</span><span class="sxs-lookup"><span data-stu-id="2335e-174">From your docker-compose.yml or docker-compose.override.yml files, you can initialize those environment variables so that Docker will set them up as OS environment variables for you, as shown in the following docker-compose.override.yml file (the connection string and other lines wrap in this example, but it would not wrap in your own file).</span></span>

```yml
# docker-compose.override.yml

#
catalog.api:
  environment:
    - ConnectionString=Server=sql.data;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word
    - ExternalCatalogBaseUrl=http://10.0.75.1:5101
    #- ExternalCatalogBaseUrl=http://dockerhoststaging.westus.cloudapp.azure.com:5101
  
  ports:
    - "5101:5101"
```

<span data-ttu-id="2335e-175">Os arquivos de docker compose.yml no nível da solução apenas não são mais flexíveis do que os arquivos de configuração no nível do projeto ou microsserviço, mas também mais segura.</span><span class="sxs-lookup"><span data-stu-id="2335e-175">The docker-compose.yml files at the solution level are not only more flexible than configuration files at the project or microservice level, but also more secure.</span></span> <span data-ttu-id="2335e-176">Considere a possibilidade de que as imagens do Docker que você cria por microsserviço não contêm o docker-compose.yml arquivos, somente os arquivos binários e arquivos de configuração para cada microsserviço, incluindo o Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="2335e-176">Consider that the Docker images that you build per microservice do not contain the docker-compose.yml files, only binary files and configuration files for each microservice, including the Dockerfile.</span></span> <span data-ttu-id="2335e-177">Mas o arquivo compose.yml docker não está implantado juntamente com seu aplicativo. ele é usado somente no momento da implantação.</span><span class="sxs-lookup"><span data-stu-id="2335e-177">But the docker-compose.yml file is not deployed along with your application; it is used only at deployment time.</span></span> <span data-ttu-id="2335e-178">Portanto, é mais seguro do que colocar esses valores nos arquivos de configuração .NET regulares que são implantados com o código de colocar valores de variáveis de ambiente nesses arquivos de docker compose.yml (mesmo sem criptografar os valores).</span><span class="sxs-lookup"><span data-stu-id="2335e-178">Therefore, placing environment variables values in those docker-compose.yml files (even without encrypting the values) is more secure than placing those values in regular .NET configuration files that are deployed with your code.</span></span>

<span data-ttu-id="2335e-179">Por fim, você pode obter esse valor no seu código usando a configuração\["ConnectionString"\], conforme mostrado no método ConfigureServices em um exemplo de código anterior.</span><span class="sxs-lookup"><span data-stu-id="2335e-179">Finally, you can get that value from your code by using Configuration\["ConnectionString"\], as shown in the ConfigureServices method in an earlier code example.</span></span>

<span data-ttu-id="2335e-180">No entanto, para ambientes de produção, você talvez queira maneiras adicionais de explorer sobre como armazenar segredos, como as cadeias de caracteres de conexão.</span><span class="sxs-lookup"><span data-stu-id="2335e-180">However, for production environments, you might want to explorer additional ways on how to store secrets like the connection strings.</span></span> <span data-ttu-id="2335e-181">Geralmente que serão gerenciados pelo seu orchestrator escolhido, como você pode fazer com [Docker Swarm gerenciamento de segredos](https://docs.docker.com/engine/swarm/secrets/).</span><span class="sxs-lookup"><span data-stu-id="2335e-181">Usually that will be managed by your chosen orchestrator, like you can do with [Docker Swarm secrets management](https://docs.docker.com/engine/swarm/secrets/).</span></span>

### <a name="implementing-versioning-in-aspnet-web-apis"></a><span data-ttu-id="2335e-182">Implementar o controle de versão em APIs da Web de ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2335e-182">Implementing versioning in ASP.NET Web APIs</span></span>

<span data-ttu-id="2335e-183">Como alterarem os requisitos de negócios, novas coleções de recursos podem ser adicionadas, poderão alterar as relações entre os recursos e a estrutura dos dados de recursos pode ser corrigida.</span><span class="sxs-lookup"><span data-stu-id="2335e-183">As business requirements change, new collections of resources may be added, the relationships between resources might change, and the structure of the data in resources might be amended.</span></span> <span data-ttu-id="2335e-184">Uma API da Web para lidar com novos requisitos de atualização é um processo relativamente simples, mas você deve considerar os efeitos que tenham essas alterações em aplicativos cliente consumo da API da Web.</span><span class="sxs-lookup"><span data-stu-id="2335e-184">Updating a Web API to handle new requirements is a relatively straightforward process, but you must consider the effects that such changes will have on client applications consuming the Web API.</span></span> <span data-ttu-id="2335e-185">Embora o desenvolvedor Projetando e implementando uma API da Web tem controle total sobre essa API, o desenvolvedor não tem o mesmo nível de controle sobre os aplicativos cliente que podem ser criados por terceiros organizações operacional remotamente.</span><span class="sxs-lookup"><span data-stu-id="2335e-185">Although the developer designing and implementing a Web API has full control over that API, the developer does not have the same degree of control over client applications that might be built by third party organizations operating remotely.</span></span>

<span data-ttu-id="2335e-186">Controle de versão permite uma API da Web indicar os recursos e os recursos que ele expõe.</span><span class="sxs-lookup"><span data-stu-id="2335e-186">Versioning enables a Web API to indicate the features and resources that it exposes.</span></span> <span data-ttu-id="2335e-187">Um aplicativo cliente pode enviar solicitações para uma versão específica de um recurso ou recurso.</span><span class="sxs-lookup"><span data-stu-id="2335e-187">A client application can then submit requests to a specific version of a feature or resource.</span></span> <span data-ttu-id="2335e-188">Há várias abordagens para implementar o controle de versão:</span><span class="sxs-lookup"><span data-stu-id="2335e-188">There are several approaches to implement versioning:</span></span>

-   <span data-ttu-id="2335e-189">Controle de versão do URI</span><span class="sxs-lookup"><span data-stu-id="2335e-189">URI versioning</span></span>

-   <span data-ttu-id="2335e-190">Controle de versão de cadeia de caracteres de consulta</span><span class="sxs-lookup"><span data-stu-id="2335e-190">Query string versioning</span></span>

-   <span data-ttu-id="2335e-191">Controle de versão de cabeçalho</span><span class="sxs-lookup"><span data-stu-id="2335e-191">Header versioning</span></span>

<span data-ttu-id="2335e-192">Cadeia de caracteres de consulta e controle de versão do URI são mais simples de implementar.</span><span class="sxs-lookup"><span data-stu-id="2335e-192">Query string and URI versioning are the simplest to implement.</span></span> <span data-ttu-id="2335e-193">Controle de versão do cabeçalho é uma boa abordagem.</span><span class="sxs-lookup"><span data-stu-id="2335e-193">Header versioning is a good approach.</span></span> <span data-ttu-id="2335e-194">No entanto, controle de versão de cabeçalho não como explícita e simples como controle de versão do URI.</span><span class="sxs-lookup"><span data-stu-id="2335e-194">However, header versioning not as explicit and straightforward as URI versioning.</span></span> <span data-ttu-id="2335e-195">Como o controle de versão de URL é a mais simples e mais explícito, o aplicativo de exemplo eShopOnContainers usa controle de versão do URI.</span><span class="sxs-lookup"><span data-stu-id="2335e-195">Because URL versioning is the simplest and most explicit, the eShopOnContainers sample application uses URI versioning.</span></span>

<span data-ttu-id="2335e-196">Com controle de versão URI, como o aplicativo de exemplo eShopOnContainers, cada vez que você modifique a API da Web ou alterar o esquema de recursos, você adicionar um número de versão para o URI para cada recurso.</span><span class="sxs-lookup"><span data-stu-id="2335e-196">With URI versioning, as in the eShopOnContainers sample application, each time you modify the Web API or change the schema of resources, you add a version number to the URI for each resource.</span></span> <span data-ttu-id="2335e-197">URIs existentes devem continuar a operar como antes, retornando os recursos que estão de acordo com o esquema que corresponde à versão solicitada.</span><span class="sxs-lookup"><span data-stu-id="2335e-197">Existing URIs should continue to operate as before, returning resources that conform to the schema that matches the requested version.</span></span>

<span data-ttu-id="2335e-198">Conforme mostrado no exemplo de código a seguir, a versão pode ser definida usando o atributo da rota na API da Web, que torna a versão explícita no URI (v1 neste caso).</span><span class="sxs-lookup"><span data-stu-id="2335e-198">As shown in the following code example, the version can be set by using the Route attribute in the Web API, which makes the version explicit in the URI (v1 in this case).</span></span>

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

<span data-ttu-id="2335e-199">Esse mecanismo de controle de versão é simple e depende do servidor de roteamento de solicitação para o ponto de extremidade apropriado.</span><span class="sxs-lookup"><span data-stu-id="2335e-199">This versioning mechanism is simple and depends on the server routing the request to the appropriate endpoint.</span></span> <span data-ttu-id="2335e-200">No entanto, para uma versão mais sofisticada e o melhor método ao usar o REST, você deve usar hipermídia e implementar [HATEOAS (como o mecanismo de estado do aplicativo de hipertexto)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#using-the-hateoas-approach-to-enable-navigation-to-related-resources).</span><span class="sxs-lookup"><span data-stu-id="2335e-200">However, for a more sophisticated versioning and the best method when using REST, you should use hypermedia and implement [HATEOAS (Hypertext as the Engine of Application State)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#using-the-hateoas-approach-to-enable-navigation-to-related-resources).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="2335e-201">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="2335e-201">Additional resources</span></span>

-   <span data-ttu-id="2335e-202">**Scott Hanselman. Controle de versão do núcleo da API da Web RESTful ASP.NET facilitado**
    [*http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx*](http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx)</span><span class="sxs-lookup"><span data-stu-id="2335e-202">**Scott Hanselman. ASP.NET Core RESTful Web API versioning made easy**
[*http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx*](http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx)</span></span>

-   <span data-ttu-id="2335e-203">**Controle de versão de uma API da web RESTful**</span><span class="sxs-lookup"><span data-stu-id="2335e-203">**Versioning a RESTful web API**</span></span>

    [<span data-ttu-id="2335e-204">*https://docs.microsoft.com/Azure/Architecture/Best-Practices/API-design#Versioning-a-RESTful-Web-API*</span><span class="sxs-lookup"><span data-stu-id="2335e-204">*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*</span></span>](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)

-   <span data-ttu-id="2335e-205">**Roy Fielding. Controle de versão, hipermídia e REST**
    [*https://www.infoq.com/articles/roy-fielding-on-versioning*](https://www.infoq.com/articles/roy-fielding-on-versioning)</span><span class="sxs-lookup"><span data-stu-id="2335e-205">**Roy Fielding. Versioning, Hypermedia, and REST**
[*https://www.infoq.com/articles/roy-fielding-on-versioning*](https://www.infoq.com/articles/roy-fielding-on-versioning)</span></span>

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a><span data-ttu-id="2335e-206">Geração de metadados do Swagger descrição de sua API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2335e-206">Generating Swagger description metadata from your ASP.NET Core Web API</span></span> 

<span data-ttu-id="2335e-207">[Swagger](http://swagger.io/) é uma estrutura de código aberto usados com o apoio de um grande ecossistema de ferramentas que ajuda você a design, compilação, documento e consumir suas APIs RESTful.</span><span class="sxs-lookup"><span data-stu-id="2335e-207">[Swagger](http://swagger.io/) is a commonly used open source framework backed by a large ecosystem of tools that helps you design, build, document, and consume your RESTful APIs.</span></span> <span data-ttu-id="2335e-208">Ele está se tornando o padrão para o domínio de metadados de descrição de APIs.</span><span class="sxs-lookup"><span data-stu-id="2335e-208">It is becoming the standard for the APIs description metadata domain.</span></span> <span data-ttu-id="2335e-209">Você deve incluir os metadados do Swagger descrição com qualquer tipo de microsserviço, controlada por dados microservices ou mais avançados microservices controlado por domínio (conforme explicado na seção a seguir).</span><span class="sxs-lookup"><span data-stu-id="2335e-209">You should include Swagger description metadata with any kind of microservice, either data-driven microservices or more advanced domain-driven microservices (as explained in following section).</span></span>

<span data-ttu-id="2335e-210">A essência do Swagger é a especificação de Swagger, que metadados de descrição de API em um arquivo JSON ou YAML.</span><span class="sxs-lookup"><span data-stu-id="2335e-210">The heart of Swagger is the Swagger specification, which is API description metadata in a JSON or YAML file.</span></span> <span data-ttu-id="2335e-211">A especificação cria o contrato RESTful para sua API, detalhando a todos os seus recursos e operações em ambos os humanos e machine readable formato para fácil desenvolvimento, descoberta e integração.</span><span class="sxs-lookup"><span data-stu-id="2335e-211">The specification creates the RESTful contract for your API, detailing all its resources and operations in both a human- and machine-readable format for easy development, discovery, and integration.</span></span>

<span data-ttu-id="2335e-212">A especificação é a base da especificação OpenAPI (OAS) e é desenvolvida em uma comunidade transparente, colaboração e abrir para padronizar a maneira RESTful interfaces são definidas.</span><span class="sxs-lookup"><span data-stu-id="2335e-212">The specification is the basis of the OpenAPI Specification (OAS) and is developed in an open, transparent, and collaborative community to standardize the way RESTful interfaces are defined.</span></span>

<span data-ttu-id="2335e-213">A especificação define a estrutura de como um serviço pode ser descoberto e como seus recursos entendido.</span><span class="sxs-lookup"><span data-stu-id="2335e-213">The specification defines the structure for how a service can be discovered and how its capabilities understood.</span></span> <span data-ttu-id="2335e-214">Para obter mais informações, inclusive um editor de web e exemplos de especificações de Swagger de empresas como Spotify, Uber, atraso e Microsoft, consulte o site de Swagger (<http://swagger.io>).</span><span class="sxs-lookup"><span data-stu-id="2335e-214">For more information, including a web editor and examples of Swagger specifications from companies like Spotify, Uber, Slack, and Microsoft, see the Swagger site (<http://swagger.io>).</span></span>

### <a name="why-use-swagger"></a><span data-ttu-id="2335e-215">Por que usar Swagger?</span><span class="sxs-lookup"><span data-stu-id="2335e-215">Why use Swagger?</span></span>

<span data-ttu-id="2335e-216">As principais razões para gerar os metadados do Swagger para suas APIs são os seguintes.</span><span class="sxs-lookup"><span data-stu-id="2335e-216">The main reasons to generate Swagger metadata for your APIs are the following.</span></span>

<span data-ttu-id="2335e-217">**Capacidade para outros produtos consumir e integrar suas APIs automaticamente**.</span><span class="sxs-lookup"><span data-stu-id="2335e-217">**Ability for other products to automatically consume and integrate your APIs**.</span></span> <span data-ttu-id="2335e-218">Dezenas de produtos e [ferramentas comercial](http://swagger.io/commercial-tools/) e muitos [estruturas e bibliotecas](http://swagger.io/open-source-integrations/) Swagger de suporte.</span><span class="sxs-lookup"><span data-stu-id="2335e-218">Dozens of products and [commercial tools](http://swagger.io/commercial-tools/) and many [libraries and frameworks](http://swagger.io/open-source-integrations/) support Swagger.</span></span> <span data-ttu-id="2335e-219">A Microsoft tem alto nível produtos e ferramentas que podem consumir automaticamente o APIs Swagger, como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="2335e-219">Microsoft has high-level products and tools that can automatically consume Swagger-based APIs, such as the following:</span></span>

-   <span data-ttu-id="2335e-220">[AutoRest](https://github.com/Azure/AutoRest).</span><span class="sxs-lookup"><span data-stu-id="2335e-220">[AutoRest](https://github.com/Azure/AutoRest).</span></span> <span data-ttu-id="2335e-221">Você pode gerar automaticamente as classes de cliente .NET para chamar Swagger.</span><span class="sxs-lookup"><span data-stu-id="2335e-221">You can automatically generate .NET client classes for calling Swagger.</span></span> <span data-ttu-id="2335e-222">Este</span><span class="sxs-lookup"><span data-stu-id="2335e-222">This</span></span>

-   <span data-ttu-id="2335e-223">ferramenta pode ser usada da CLI e ele também se integra com o Visual Studio fácil de usar por meio da GUI.</span><span class="sxs-lookup"><span data-stu-id="2335e-223">tool can be used from the CLI and it also integrates with Visual Studio for easy use through the GUI.</span></span>

-   <span data-ttu-id="2335e-224">[Microsoft Flow](https://flow.microsoft.com/en-us/).</span><span class="sxs-lookup"><span data-stu-id="2335e-224">[Microsoft Flow](https://flow.microsoft.com/en-us/).</span></span> <span data-ttu-id="2335e-225">Você pode automaticamente [usar e integrar sua API](https://flow.microsoft.com/en-us/blog/integrating-custom-api/) em um fluxo de trabalho do Microsoft Flow alto nível, sem nenhum programação habilidades necessárias.</span><span class="sxs-lookup"><span data-stu-id="2335e-225">You can automatically [use and integrate your API](https://flow.microsoft.com/en-us/blog/integrating-custom-api/) into a high-level Microsoft Flow workflow, with no programming skills required.</span></span>

-   <span data-ttu-id="2335e-226">[Microsoft PowerApps](https://powerapps.microsoft.com/en-us/).</span><span class="sxs-lookup"><span data-stu-id="2335e-226">[Microsoft PowerApps](https://powerapps.microsoft.com/en-us/).</span></span> <span data-ttu-id="2335e-227">Automaticamente, você pode usar a API de [aplicativos móveis PowerApps](https://powerapps.microsoft.com/en-us/blog/register-and-use-custom-apis-in-powerapps/) criados com [PowerApps Studio](https://powerapps.microsoft.com/en-us/guided-learning/learning-powerapps-parts/), com nenhuma programação habilidades necessárias.</span><span class="sxs-lookup"><span data-stu-id="2335e-227">You can automatically consume your API from [PowerApps mobile apps](https://powerapps.microsoft.com/en-us/blog/register-and-use-custom-apis-in-powerapps/) built with [PowerApps Studio](https://powerapps.microsoft.com/en-us/guided-learning/learning-powerapps-parts/), with no programming skills required.</span></span>

-   <span data-ttu-id="2335e-228">[Aplicativos do serviço de aplicativo do Azure lógica](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span><span class="sxs-lookup"><span data-stu-id="2335e-228">[Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span></span> <span data-ttu-id="2335e-229">Você pode automaticamente [usar e integrar sua API em um aplicativo de lógica do serviço de aplicativo do Azure](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), com nenhuma programação habilidades necessárias.</span><span class="sxs-lookup"><span data-stu-id="2335e-229">You can automatically [use and integrate your API into an Azure App Service Logic App](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), with no programming skills required.</span></span>

<span data-ttu-id="2335e-230">**Capacidade de gerar automaticamente a documentação da API**.</span><span class="sxs-lookup"><span data-stu-id="2335e-230">**Ability to automatically generate API documentation**.</span></span> <span data-ttu-id="2335e-231">Quando você criar APIs RESTful em larga escala, como aplicativos baseados em microsserviço complexos, você precisa lidar com vários pontos de extremidade com modelos de dados diferentes usados nas cargas de solicitação e resposta.</span><span class="sxs-lookup"><span data-stu-id="2335e-231">When you create large-scale RESTful APIs, such as complex microservice-based applications, you need to handle many endpoints with different data models used in the request and response payloads.</span></span> <span data-ttu-id="2335e-232">Ter a documentação adequada e ter um Gerenciador de API sólido, como você pode obter com Swagger, são a chave para o sucesso da sua API e adoção pelos desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="2335e-232">Having proper documentation and having a solid API explorer, as you get with Swagger, is key for the success of your API and adoption by developers.</span></span>

<span data-ttu-id="2335e-233">Metadados do swagger são o que os aplicativos lógicos do Azure, PowerApps e Microsoft Flow usam para entender como usar APIs e conectá-los.</span><span class="sxs-lookup"><span data-stu-id="2335e-233">Swagger’s metadata is what Microsoft Flow, PowerApps, and Azure Logic Apps use to understand how to use APIs and connect to them.</span></span>

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a><span data-ttu-id="2335e-234">Como automatizar a geração de metadados Swagger de API com o pacote Swashbuckle NuGet</span><span class="sxs-lookup"><span data-stu-id="2335e-234">How to automate API Swagger metadata generation with the Swashbuckle NuGet package</span></span>

<span data-ttu-id="2335e-235">Geração de metadados Swagger manualmente (em um arquivo JSON ou YAML) pode ser entediante trabalho.</span><span class="sxs-lookup"><span data-stu-id="2335e-235">Generating Swagger metadata manually (in a JSON or YAML file) can be tedious work.</span></span> <span data-ttu-id="2335e-236">No entanto, você pode automatizar a descoberta de API de serviços de API da Web ASP.NET usando o [pacote Swashbuckle NuGet](http://aka.ms/swashbuckledotnetcore) gerar dinamicamente os metadados do Swagger API.</span><span class="sxs-lookup"><span data-stu-id="2335e-236">However, you can automate API discovery of ASP.NET Web API services by using the [Swashbuckle NuGet package](http://aka.ms/swashbuckledotnetcore) to dynamically generate Swagger API metadata.</span></span>

<span data-ttu-id="2335e-237">Swashbuckle gera automaticamente os metadados do Swagger para seus projetos ASP.NET Web API.</span><span class="sxs-lookup"><span data-stu-id="2335e-237">Swashbuckle automatically generates Swagger metadata for your ASP.NET Web API projects.</span></span> <span data-ttu-id="2335e-238">Ele dá suporte a projetos de API da Web do ASP.NET Core e o ASP.NET Web API tradicional e qualquer outro tipo, como aplicativo de API, aplicativo de celular do Azure, Azure Service Fabric microservices com base no ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="2335e-238">It supports ASP.NET Core Web API projects and the traditional ASP.NET Web API and any other flavor, such as Azure API App, Azure Mobile App, Azure Service Fabric microservices based on ASP.NET.</span></span> <span data-ttu-id="2335e-239">Ele também dá suporte a API da Web simples do implantado em contêineres, como para o aplicativo de referência.</span><span class="sxs-lookup"><span data-stu-id="2335e-239">It also supports plain Web API deployed on containers, as in for the reference application.</span></span>

<span data-ttu-id="2335e-240">Swashbuckle combina o Gerenciador de API e Swagger ou [swagger ui](https://github.com/swagger-api/swagger-ui) para fornecer a experiência de descoberta avançada e a documentação para seus consumidores de API.</span><span class="sxs-lookup"><span data-stu-id="2335e-240">Swashbuckle combines API Explorer and Swagger or [swagger-ui](https://github.com/swagger-api/swagger-ui) to provide a rich discovery and documentation experience for your API consumers.</span></span> <span data-ttu-id="2335e-241">Além de seu mecanismo de gerador de metadados Swagger, Swashbuckle também contém uma versão incorporada do swagger-interface do usuário, que automaticamente servirá backup uma vez Swashbuckle será instalado.</span><span class="sxs-lookup"><span data-stu-id="2335e-241">In addition to its Swagger metadata generator engine, Swashbuckle also contains an embedded version of swagger-ui, which it will automatically serve up once Swashbuckle is installed.</span></span>

<span data-ttu-id="2335e-242">Isso significa que você pode complementar a sua API com uma interface de usuário para ajudar os desenvolvedores a usar a API de descoberta adequada.</span><span class="sxs-lookup"><span data-stu-id="2335e-242">This means you can complement your API with a nice discovery UI to help developers to use your API.</span></span> <span data-ttu-id="2335e-243">Ele requer uma quantidade muito pequena de código e manutenção porque ela é gerada automaticamente, permitindo que você se concentre na sua API.</span><span class="sxs-lookup"><span data-stu-id="2335e-243">It requires a very small amount of code and maintenance because it is automatically generated, allowing you to focus on building your API.</span></span> <span data-ttu-id="2335e-244">O resultado para o Gerenciador de API é como a Figura 8-8.</span><span class="sxs-lookup"><span data-stu-id="2335e-244">The result for the API Explorer looks like Figure 8-8.</span></span>

![](./media/image9.png)

<span data-ttu-id="2335e-245">**Figura 8-8**.</span><span class="sxs-lookup"><span data-stu-id="2335e-245">**Figure 8-8**.</span></span> <span data-ttu-id="2335e-246">Gerenciador de API Swashbuckle com base nos metadados do Swagger — eShopOnContainers microsserviço do catálogo</span><span class="sxs-lookup"><span data-stu-id="2335e-246">Swashbuckle API Explorer based on Swagger metadata—eShopOnContainers catalog microservice</span></span>

<span data-ttu-id="2335e-247">O Gerenciador de API não é o mais importante aqui.</span><span class="sxs-lookup"><span data-stu-id="2335e-247">The API explorer is not the most important thing here.</span></span> <span data-ttu-id="2335e-248">Quando você tem uma API da Web que pode descrever-se nos metadados do Swagger, sua API pode ser usada diretamente do Swagger com ferramentas, incluindo geradores de código de classe de proxy de cliente que podem direcionar várias plataformas.</span><span class="sxs-lookup"><span data-stu-id="2335e-248">Once you have a Web API that can describe itself in Swagger metadata, your API can be used seamlessly from Swagger-based tools, including client proxy-class code generators that can target many platforms.</span></span> <span data-ttu-id="2335e-249">Por exemplo, conforme mencionado, [AutoRest](https://github.com/Azure/AutoRest) gera automaticamente as classes de cliente .NET.</span><span class="sxs-lookup"><span data-stu-id="2335e-249">For example, as mentioned, [AutoRest](https://github.com/Azure/AutoRest) automatically generates .NET client classes.</span></span> <span data-ttu-id="2335e-250">Mas, como ferramentas adicionais [swagger codegen](https://github.com/swagger-api/swagger-codegen) também estão disponíveis, que permite a geração de código do cliente de API de bibliotecas, stubs de servidor e documentação automaticamente.</span><span class="sxs-lookup"><span data-stu-id="2335e-250">But additional tools like [swagger-codegen](https://github.com/swagger-api/swagger-codegen) are also available, which allow code generation of API client libraries, server stubs, and documentation automatically.</span></span>

<span data-ttu-id="2335e-251">No momento, Swashbuckle consiste em dois pacotes do NuGet: Swashbuckle.SwaggerGen e Swashbuckle.SwaggerUi.</span><span class="sxs-lookup"><span data-stu-id="2335e-251">Currently, Swashbuckle consists of two NuGet packages: Swashbuckle.SwaggerGen and Swashbuckle.SwaggerUi.</span></span> <span data-ttu-id="2335e-252">O primeiro fornece funcionalidade para gerar um ou mais documentos de Swagger diretamente de sua implementação de API e expô-los como pontos de extremidade JSON.</span><span class="sxs-lookup"><span data-stu-id="2335e-252">The former provides functionality to generate one or more Swagger documents directly from your API implementation and expose them as JSON endpoints.</span></span> <span data-ttu-id="2335e-253">O último fornece uma versão incorporada da ferramenta de interface do usuário swagger que pode ser atendida por seu aplicativo e os documentos de Swagger gerados para descrever sua API da plataforma.</span><span class="sxs-lookup"><span data-stu-id="2335e-253">The latter provides an embedded version of the swagger-ui tool that can be served by your application and powered by the generated Swagger documents to describe your API.</span></span> <span data-ttu-id="2335e-254">No entanto, as versões mais recentes de Swashbuckle encapsulam esses recursos com o metapackage Swashbuckle.AspNetCore.</span><span class="sxs-lookup"><span data-stu-id="2335e-254">However, the latest versions of Swashbuckle wrap these with the Swashbuckle.AspNetCore metapackage.</span></span>

<span data-ttu-id="2335e-255">Observe que, para projetos Web API do .NET Core, você precisa usar [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore/1.0.0) versão 1.0.0 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="2335e-255">Note that for .NET Core Web API projects, you need to use [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore/1.0.0) version 1.0.0 or later.</span></span>

<span data-ttu-id="2335e-256">Depois de instalar esses pacotes do NuGet em seu projeto de API da Web, você precisa configurar Swagger na classe de inicialização, como no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="2335e-256">After you have installed these NuGet packages in your Web API project, you need to configure Swagger in the Startup class, as in the following code:</span></span>

```csharp
public class Startup
{
    public IConfigurationRoot Configuration { get; }
    // Other startup code...

    public void ConfigureServices(IServiceCollection services)
    {
        // Other ConfigureServices() code...
        services.AddSwaggerGen();
        services.ConfigureSwaggerGen(options =>
        {
            options.DescribeAllEnumsAsStrings();
            options.SingleApiVersion(new Swashbuckle.Swagger.Model.Info()
            {
                Title = "eShopOnContainers - Catalog HTTP API",
                Version = "v1",
                Description = "The Catalog Microservice HTTP API",
                TermsOfService = "eShopOnContainers terms of service"
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
            .UseSwaggerUi();
    }
}
```

<span data-ttu-id="2335e-257">Depois que isso for feito, você pode iniciar o aplicativo e procurar seguintes Swagger JSON e interface de usuário pontos de extremidade usando URLs como estes:</span><span class="sxs-lookup"><span data-stu-id="2335e-257">Once this is done, you can start your application and browse the following Swagger JSON and UI endpoints using URLs like these:</span></span>

```json
  http://<your-root-url>/swagger/v1/swagger.json
  
  http://<your-root-url>/swagger/ui
```

<span data-ttu-id="2335e-258">Anteriormente, você viu a interface do usuário gerado criado pelo Swashbuckle para uma URL como http://&lt;sua url raiz &gt; /swagger/interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="2335e-258">You previously saw the generated UI created by Swashbuckle for a URL like http://&lt;your-root-url&gt;/swagger/ui.</span></span> <span data-ttu-id="2335e-259">Figura 8 e 9 você também pode ver como você pode testar qualquer método de API.</span><span class="sxs-lookup"><span data-stu-id="2335e-259">In Figure 8-9 you can also see how you can test any API method.</span></span>

![](./media/image10.png)

<span data-ttu-id="2335e-260">**Figura 8 e 9**.</span><span class="sxs-lookup"><span data-stu-id="2335e-260">**Figure 8-9**.</span></span> <span data-ttu-id="2335e-261">Swashbuckle UI testar o método de API de itens do catálogo</span><span class="sxs-lookup"><span data-stu-id="2335e-261">Swashbuckle UI testing the Catalog/Items API method</span></span>

<span data-ttu-id="2335e-262">Figura 8-10 mostra os metadados do Swagger JSON gerado a partir de microsserviço eShopOnContainers (que é o que usam as ferramentas abaixo) quando você solicitar &lt;sua url raiz&gt;/swagger/v1/swagger.json usando [carteiro](https://www.getpostman.com/).</span><span class="sxs-lookup"><span data-stu-id="2335e-262">Figure 8-10 shows the Swagger JSON metadata generated from the eShopOnContainers microservice (which is what the tools use underneath) when you request &lt;your-root-url&gt;/swagger/v1/swagger.json using [Postman](https://www.getpostman.com/).</span></span>

![](./media/image11.png)

<span data-ttu-id="2335e-263">**Figura 8-10**.</span><span class="sxs-lookup"><span data-stu-id="2335e-263">**Figure 8-10**.</span></span> <span data-ttu-id="2335e-264">Metadados do swagger JSON</span><span class="sxs-lookup"><span data-stu-id="2335e-264">Swagger JSON metadata</span></span>

<span data-ttu-id="2335e-265">É simple.</span><span class="sxs-lookup"><span data-stu-id="2335e-265">It is that simple.</span></span> <span data-ttu-id="2335e-266">E como ela é gerada automaticamente, os metadados do Swagger aumentará quando você adicionar mais funcionalidade a sua API.</span><span class="sxs-lookup"><span data-stu-id="2335e-266">And because it is automatically generated, the Swagger metadata will grow when you add more functionality to your API.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="2335e-267">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="2335e-267">Additional resources</span></span>

-   <span data-ttu-id="2335e-268">**Páginas da Web ASP.NET API ajuda usando Swagger**
    [*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger*](https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger)</span><span class="sxs-lookup"><span data-stu-id="2335e-268">**ASP.NET Web API Help Pages using Swagger**
[*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger*](https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="2335e-269">[Anterior] (microsserviço-aplicativo-design.md) [Avançar] (multi-container-aplicativos-docker-compose.md)</span><span class="sxs-lookup"><span data-stu-id="2335e-269">[Previous] (microservice-application-design.md) [Next] (multi-container-applications-docker-compose.md)</span></span>
