---
title: Trabalhar com dados em aplicativos do ASP.NET Core
description: Projetar aplicativos Web modernos com ASP.NET Core e o Azure | Trabalhando com dados no asp
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 648e0a4cdd388cf4a322f0fc049d5dcfca53d54b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="working-with-data-in-aspnet-core-apps"></a><span data-ttu-id="037a1-103">Trabalhando com dados em aplicativos ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="037a1-103">Working with Data in ASP.NET Core Apps</span></span>

> <span data-ttu-id="037a1-104">"Os dados é uma coisa preciosa e irão durar mais que os próprios sistemas de".</span><span class="sxs-lookup"><span data-stu-id="037a1-104">"Data is a precious thing and will last longer than the systems themselves."</span></span>

<span data-ttu-id="037a1-105">Tim Berners-Lee</span><span class="sxs-lookup"><span data-stu-id="037a1-105">Tim Berners-Lee</span></span>

## <a name="summary"></a><span data-ttu-id="037a1-106">Resumo</span><span class="sxs-lookup"><span data-stu-id="037a1-106">Summary</span></span>

<span data-ttu-id="037a1-107">Acesso a dados é uma parte importante de praticamente qualquer aplicativo de software.</span><span class="sxs-lookup"><span data-stu-id="037a1-107">Data access is an important part of almost any software application.</span></span> <span data-ttu-id="037a1-108">ASP.NET Core dá suporte a uma variedade de opções de acesso de dados, incluindo o Entity Framework Core (e também para o Entity Framework 6) e pode trabalhar com qualquer acesso de dados do .NET framework.</span><span class="sxs-lookup"><span data-stu-id="037a1-108">ASP.NET Core supports a variety of data access options, including Entity Framework Core (and Entity Framework 6 as well), and can work with any .NET data access framework.</span></span> <span data-ttu-id="037a1-109">A escolha do framework usar de acesso a dados dos quais depende necessidades do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="037a1-109">The choice of which data access framework to use depends on the application's needs.</span></span> <span data-ttu-id="037a1-110">Abstrair essas opções dos projetos ApplicationCore e interface de usuário e encapsula os detalhes de implementação na infraestrutura, ajudam a produzir um software acoplado, podem ser testado.</span><span class="sxs-lookup"><span data-stu-id="037a1-110">Abstracting these choices from the ApplicationCore and UI projects, and encapsulating implementation details in Infrastructure, helps to produce loosely coupled, testable software.</span></span>

## <a name="entity-framework-core-for-relational-databases"></a><span data-ttu-id="037a1-111">Entity Framework Core (para bancos de dados relacionais)</span><span class="sxs-lookup"><span data-stu-id="037a1-111">Entity Framework Core (for relational databases)</span></span>

<span data-ttu-id="037a1-112">Se você estiver escrevendo um novo aplicativo ASP.NET Core que precisa para trabalhar com dados relacionais, Entity Framework Core (EF Core) é a maneira recomendada para seu aplicativo acessar seus dados.</span><span class="sxs-lookup"><span data-stu-id="037a1-112">If you're writing a new ASP.NET Core application that needs to work with relational data, then Entity Framework Core (EF Core) is the recommended way for your application to access its data.</span></span> <span data-ttu-id="037a1-113">Núcleo do EF é mapeador relacional de objeto (O/RM) que permite que os desenvolvedores de .NET manter os objetos em uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="037a1-113">EF Core is an object-relational mapper (O/RM) that enables .NET developers to persist objects to and from a data source.</span></span> <span data-ttu-id="037a1-114">Elimina a necessidade para a maioria dos desenvolvedores normalmente precisa escrever código de acesso do dados.</span><span class="sxs-lookup"><span data-stu-id="037a1-114">It eliminates the need for most of the data access code developers would typically need to write.</span></span> <span data-ttu-id="037a1-115">Como o ASP.NET Core EF Core foi recriado desde o início para suporte a aplicativos de plataforma cruzada modular.</span><span class="sxs-lookup"><span data-stu-id="037a1-115">Like ASP.NET Core, EF Core has been rewritten from the ground up to support modular cross-platform applications.</span></span> <span data-ttu-id="037a1-116">Você adicioná-lo ao seu aplicativo como um pacote NuGet, configurá-lo na inicialização e solicitá-la por meio de injeção de dependência, onde for necessário.</span><span class="sxs-lookup"><span data-stu-id="037a1-116">You add it to your application as a NuGet package, configure it in Startup, and request it through dependency injection wherever you need it.</span></span>

<span data-ttu-id="037a1-117">Para usar o EF Core com um banco de dados do SQL Server, execute o seguinte comando CLI dotnet:</span><span class="sxs-lookup"><span data-stu-id="037a1-117">To use EF Core with a SQL Server database, run the following dotnet CLI command:</span></span>

<span data-ttu-id="037a1-118">dotnet Adicionar pacote Microsoft.EntityFrameworkCore.SqlServer</span><span class="sxs-lookup"><span data-stu-id="037a1-118">dotnet add package Microsoft.EntityFrameworkCore.SqlServer</span></span>

<span data-ttu-id="037a1-119">Para adicionar suporte para uma fonte de dados InMemory para teste:</span><span class="sxs-lookup"><span data-stu-id="037a1-119">To add support for an InMemory data source, for testing:</span></span>

<span data-ttu-id="037a1-120">dotnet Adicionar pacote Microsoft.EntityFrameworkCore.InMemory</span><span class="sxs-lookup"><span data-stu-id="037a1-120">dotnet add package Microsoft.EntityFrameworkCore.InMemory</span></span>

### <a name="the-dbcontext"></a><span data-ttu-id="037a1-121">O DbContext</span><span class="sxs-lookup"><span data-stu-id="037a1-121">The DbContext</span></span>

<span data-ttu-id="037a1-122">Para trabalhar com EF Core, você precisa de uma subclasse de DbContext.</span><span class="sxs-lookup"><span data-stu-id="037a1-122">To work with EF Core, you need a subclass of DbContext.</span></span> <span data-ttu-id="037a1-123">Essa classe contém propriedades que representam coleções de entidades que seu aplicativo funcionará com.</span><span class="sxs-lookup"><span data-stu-id="037a1-123">This class holds properties representing collections of the entities your application will work with.</span></span> <span data-ttu-id="037a1-124">O exemplo de eShopOnWeb inclui um CatalogContext com coleções de itens, marcas e tipos:</span><span class="sxs-lookup"><span data-stu-id="037a1-124">The eShopOnWeb sample includes a CatalogContext with collections for items, brands, and types:</span></span>

```csharp
public class CatalogContext : DbContext
{
    public CatalogContext(DbContextOptions<CatalogContext> options) : base(options)
    {

    }

    public DbSet<CatalogItem> CatalogItems { get; set; }

    public DbSet<CatalogBrand> CatalogBrands { get; set; }

    public DbSet<CatalogType> CatalogTypes { get; set; }
}
```

<span data-ttu-id="037a1-125">O DbContext deve ter um construtor que aceite DbContextOptions e passar esse argumento para o construtor DbContext base.</span><span class="sxs-lookup"><span data-stu-id="037a1-125">Your DbContext must have a constructor that accepts DbContextOptions and pass this argument to the base DbContext constructor.</span></span> <span data-ttu-id="037a1-126">Observe que, se você tiver apenas um DbContext em seu aplicativo, você pode passar uma instância de DbContextOptions, mas se você tiver mais de um você deve usar o genérico DbContextOptions<T> tipo, passando o tipo DbContext como o parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="037a1-126">Note that if you have only one DbContext in your application, you can pass an instance of DbContextOptions, but if you have more than one you must use the generic DbContextOptions<T> type, passing in your DbContext type as the generic parameter.</span></span>

### <a name="configuring-ef-core"></a><span data-ttu-id="037a1-127">Configurar os principais EF</span><span class="sxs-lookup"><span data-stu-id="037a1-127">Configuring EF Core</span></span>

<span data-ttu-id="037a1-128">Seu aplicativo ASP.NET Core, normalmente você vai configurar EF principal em seu método ConfigureServices.</span><span class="sxs-lookup"><span data-stu-id="037a1-128">In your ASP.NET Core application, you'll typically configure EF Core in your ConfigureServices method.</span></span> <span data-ttu-id="037a1-129">Núcleo EF usa um DbContextOptionsBuilder, que oferece suporte a vários métodos de extensão útil para simplificar sua configuração.</span><span class="sxs-lookup"><span data-stu-id="037a1-129">EF Core uses a DbContextOptionsBuilder, which supports several helpful extension methods to streamline its configuration.</span></span> <span data-ttu-id="037a1-130">Para configurar CatalogContext para usar um banco de dados do SQL Server com uma cadeia de caracteres de conexão definida na configuração, você adicionaria o código a seguir para ConfigureServices:</span><span class="sxs-lookup"><span data-stu-id="037a1-130">To configure CatalogContext to use a SQL Server database with a connection string defined in Configuration, you would add the following code to ConfigureServices:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

<span data-ttu-id="037a1-131">Para usar o banco de dados na memória:</span><span class="sxs-lookup"><span data-stu-id="037a1-131">To use the in-memory database:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

<span data-ttu-id="037a1-132">Depois de instalado EF Core, criado um tipo filho DbContext e configurado no ConfigureServices, você está pronto para usar o EF Core.</span><span class="sxs-lookup"><span data-stu-id="037a1-132">Once you have installed EF Core, created a DbContext child type, and configured it in ConfigureServices, you are ready to use EF Core.</span></span> <span data-ttu-id="037a1-133">Você pode solicitar uma instância do seu tipo DbContext em qualquer serviço que precisa dele e começar a trabalhar com suas entidades persistentes usando LINQ como se estivesse em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="037a1-133">You can request an instance of your DbContext type in any service that needs it, and start working with your persisted entities using LINQ as if they were simply in a collection.</span></span> <span data-ttu-id="037a1-134">EF Core funciona a transferir suas expressões LINQ em consultas SQL para armazenar e recuperar seus dados.</span><span class="sxs-lookup"><span data-stu-id="037a1-134">EF Core does the work of translating your LINQ expressions into SQL queries to store and retrieve your data.</span></span>

<span data-ttu-id="037a1-135">Você pode ver as consultas EF principal está em execução, configurando um agente de log e garantindo seu nível é definido para pelo menos informações, como mostrado na Figura 8-1.</span><span class="sxs-lookup"><span data-stu-id="037a1-135">You can see the queries EF Core is executing by configuring a logger and ensuring its level is set to at least Information, as shown in Figure 8-1.</span></span>

![](./media/image8-1.png)

<span data-ttu-id="037a1-136">Consultas de log EF Core Figura 8-1 para o console</span><span class="sxs-lookup"><span data-stu-id="037a1-136">Figure 8-1 Logging EF Core queries to the console</span></span>

### <a name="fetching-and-storing-data"></a><span data-ttu-id="037a1-137">Buscando e armazenando dados</span><span class="sxs-lookup"><span data-stu-id="037a1-137">Fetching and Storing Data</span></span>

<span data-ttu-id="037a1-138">Para recuperar dados de EF Core, você acessa a propriedade apropriada e usa o LINQ para filtrar o resultados.</span><span class="sxs-lookup"><span data-stu-id="037a1-138">To retrieve data from EF Core, you access the appropriate property and use LINQ to filter the result.</span></span> <span data-ttu-id="037a1-139">Você também pode usar o LINQ para executar projeção, transformar o resultado de um tipo para outro.</span><span class="sxs-lookup"><span data-stu-id="037a1-139">You can also use LINQ to perform projection, transforming the result from one type to another.</span></span> <span data-ttu-id="037a1-140">O exemplo a seguir recuperaria CatalogBrands, ordenados por nome, filtrados por sua propriedade Enabled e projetado em um tipo SelectListItem:</span><span class="sxs-lookup"><span data-stu-id="037a1-140">The following example would retrieve CatalogBrands, ordered by name, filtered by their Enabled property, and projected onto a SelectListItem type:</span></span>

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

<span data-ttu-id="037a1-141">É importante no exemplo acima para adicionar a chamada para ToListAsync para executar a consulta imediatamente.</span><span class="sxs-lookup"><span data-stu-id="037a1-141">It's important in the above example to add the call to ToListAsync in order to execute the query immediately.</span></span> <span data-ttu-id="037a1-142">Caso contrário, a instrução atribuirá um IQueryable<SelectListItem> para brandItems, que não será executado até que ele é enumerado.</span><span class="sxs-lookup"><span data-stu-id="037a1-142">Otherwise, the statement will assign an IQueryable<SelectListItem> to brandItems, which will not be executed until it is enumerated.</span></span> <span data-ttu-id="037a1-143">Há vantagens e desvantagens para retornar resultados IQueryable de métodos.</span><span class="sxs-lookup"><span data-stu-id="037a1-143">There are pros and cons to returning IQueryable results from methods.</span></span> <span data-ttu-id="037a1-144">Ele permite que a consulta que EF Core criará para mais ser modificada, mas também pode resultar em erros que ocorrem apenas em tempo de execução, se as operações são adicionadas à consulta que EF principal não pode traduzir.</span><span class="sxs-lookup"><span data-stu-id="037a1-144">It allows the query EF Core will construct to be further modified, but can also result in errors that only occur at runtime, if operations are added to the query that EF Core cannot translate.</span></span> <span data-ttu-id="037a1-145">Ele geralmente é mais seguro passar todos os filtros para o método executar o acesso a dados e fazer o retorno de uma coleção de memória (por exemplo,<T>) como o resultado.</span><span class="sxs-lookup"><span data-stu-id="037a1-145">It's generally safer to pass any filters into the method performing the data access, and return back an in-memory collection (for example, List<T>) as the result.</span></span>

<span data-ttu-id="037a1-146">Núcleo EF rastreia as alterações nas entidades que ele busca de persistência.</span><span class="sxs-lookup"><span data-stu-id="037a1-146">EF Core tracks changes on entities it fetches from persistence.</span></span> <span data-ttu-id="037a1-147">Para salvar as alterações para uma entidade controlada, apenas você chamar o método SaveChanges no DbContext, tornando-se de que é a mesma instância de DbContext que foi usada para buscar a entidade.</span><span class="sxs-lookup"><span data-stu-id="037a1-147">To save changes to a tracked entity, you just call the SaveChanges method on the DbContext, making sure it's the same DbContext instance that was used to fetch the entity.</span></span> <span data-ttu-id="037a1-148">Adicionando e removendo entidades são diretamente na propriedade DbSet apropriada, novamente com uma chamada para SaveChanges para executar os comandos de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="037a1-148">Adding and removing entities is directly on the appropriate DbSet property, again with a call to SaveChanges to execute the database commands.</span></span> <span data-ttu-id="037a1-149">O exemplo a seguir demonstra a adicionar, atualizar e remover entidades de persistência.</span><span class="sxs-lookup"><span data-stu-id="037a1-149">The following example demonstrates adding, updating, and removing entities from persistence.</span></span>

```csharp
// create
var newBrand = new CatalogBrand() { Brand = "Acme" };
_context.Add(newBrand);
await _context.SaveChangesAsync();

// read and update
var existingBrand = _context.CatalogBrands.Find(1);
existingBrand.Brand = "Updated Brand";
await _context.SaveChangesAsync();

// read and delete (alternate Find syntax)
var brandToDelete = _context.Find<CatalogBrand>(2);
_context.CatalogBrands.Remove(brandToDelete);
await _context.SaveChangesAsync();
```

<span data-ttu-id="037a1-150">EF Core dá suporte a ambos síncrona e os métodos assíncronos para buscar e salvar.</span><span class="sxs-lookup"><span data-stu-id="037a1-150">EF Core supports both synchronous and async methods for fetching and saving.</span></span> <span data-ttu-id="037a1-151">Em aplicativos da web, é recomendável usar o padrão assíncrono/await com os métodos assíncronos, para que os threads de servidor da web não estão bloqueadas enquanto aguarda a conclusão das operações de acesso dados.</span><span class="sxs-lookup"><span data-stu-id="037a1-151">In web applications, it's recommended to use the async/await pattern with the async methods, so that web server threads are not blocked while waiting for data access operations to complete.</span></span>

### <a name="fetching-related-data"></a><span data-ttu-id="037a1-152">Buscando dados relacionados</span><span class="sxs-lookup"><span data-stu-id="037a1-152">Fetching Related Data</span></span>

<span data-ttu-id="037a1-153">Quando o EF Core recupera entidades, preenche todas as propriedades que são armazenadas diretamente com a entidade no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="037a1-153">When EF Core retrieves entities, it populates all of the properties that are stored directly with that entity in the database.</span></span> <span data-ttu-id="037a1-154">Propriedades de navegação, como listas de entidades relacionadas, não são preenchidas e pode ter seu valor definido como null.</span><span class="sxs-lookup"><span data-stu-id="037a1-154">Navigation properties, such as lists of related entities, are not populated and may have their value set to null.</span></span> <span data-ttu-id="037a1-155">Isso garante que o EF Core é não busca mais dados do que é necessário, que é especialmente importante para aplicativos web, que devem processar solicitações e respostas de retorno de uma maneira eficiente rapidamente.</span><span class="sxs-lookup"><span data-stu-id="037a1-155">This ensures EF Core is not fetching more data than is needed, which is especially important for web applications, which must quickly process requests and return responses in an efficient manner.</span></span> <span data-ttu-id="037a1-156">Para incluir relações com uma entidade usando *carregamento adiantado*, especifique a propriedade usando o método de extensão incluir na consulta, conforme mostrado:</span><span class="sxs-lookup"><span data-stu-id="037a1-156">To include relationships with an entity using *eager loading*, you specify the property using the Include extension method on the query, as shown:</span></span>

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

<span data-ttu-id="037a1-157">Você pode incluir várias relações, e você também pode incluir relações sub usando ThenInclude.</span><span class="sxs-lookup"><span data-stu-id="037a1-157">You can include multiple relationships, and you can also include sub-relationships using ThenInclude.</span></span> <span data-ttu-id="037a1-158">EF Core será executado uma única consulta para recuperar o conjunto resultante de entidades.</span><span class="sxs-lookup"><span data-stu-id="037a1-158">EF Core will execute a single query to retrieve the resulting set of entities.</span></span>

<span data-ttu-id="037a1-159">Outra opção para carregar dados relacionados é usar *carregamento explícito*.</span><span class="sxs-lookup"><span data-stu-id="037a1-159">Another option for loading related data is to use *explicit loading*.</span></span> <span data-ttu-id="037a1-160">Carregamento explícito permite carregar dados adicionais em uma entidade que já foram recuperada.</span><span class="sxs-lookup"><span data-stu-id="037a1-160">Explicit loading allows you to load additional data into an entity that has already been retrieved.</span></span> <span data-ttu-id="037a1-161">Como isso envolve uma solicitação separada para o banco de dados, ele não é recomendado para aplicativos web, que devem minimizar o número de banco de dados viagens de ida e feitas por solicitação.</span><span class="sxs-lookup"><span data-stu-id="037a1-161">Since this involves a separate request to the database, it's not recommended for web applications, which should minimize the number of database round trips made per request.</span></span>

<span data-ttu-id="037a1-162">*Carregamento preguiçoso* é um recurso que carrega automaticamente os dados relacionados porque ele é referenciado pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="037a1-162">*Lazy loading* is a feature that automatically loads related data as it is referenced by the application.</span></span> <span data-ttu-id="037a1-163">EF Core atualmente não há suporte, mas como com carregamento explícito deve normalmente ser desabilitado para aplicativos da web.</span><span class="sxs-lookup"><span data-stu-id="037a1-163">It's not currently supported by EF Core, but as with explicit loading it should typically be disabled for web applications.</span></span>

### <a name="resilient-connections"></a><span data-ttu-id="037a1-164">Conexões</span><span class="sxs-lookup"><span data-stu-id="037a1-164">Resilient Connections</span></span>

<span data-ttu-id="037a1-165">Recursos externos, como bancos de dados SQL, ocasionalmente, podem estar indisponíveis.</span><span class="sxs-lookup"><span data-stu-id="037a1-165">External resources like SQL databases may occasionally be unavailable.</span></span> <span data-ttu-id="037a1-166">Em caso de indisponibilidade temporária, os aplicativos podem usar a lógica de repetição para não gerar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="037a1-166">In cases of temporary unavailability, applications can use retry logic to avoid raising an exception.</span></span> <span data-ttu-id="037a1-167">Essa técnica é conhecida como *resiliência de conexão*.</span><span class="sxs-lookup"><span data-stu-id="037a1-167">This technique is commonly referred to as *connection resiliency*.</span></span> <span data-ttu-id="037a1-168">Você pode implementar seu [própria repetição com retirada exponencial](https://docs.microsoft.com/azure/architecture/patterns/retry) técnica pela tentativa de repetição com um tempo de espera aumentando exponencialmente, até um máximo de tentativas foi atingida.</span><span class="sxs-lookup"><span data-stu-id="037a1-168">You can implement your [own retry with exponential backoff](https://docs.microsoft.com/azure/architecture/patterns/retry) technique by attempting to rety with an exponentially increasing wait time, until a maximum retry count has been reached.</span></span> <span data-ttu-id="037a1-169">Essa técnica adota o fato de que recursos de nuvem podem estar temporariamente indisponíveis por curtos períodos de tempo, resultando em falha de algumas solicitações.</span><span class="sxs-lookup"><span data-stu-id="037a1-169">This technique embraces the fact that cloud resources might intermittently be unavailable for short periods of time, resulting in failure of some requests.</span></span>

<span data-ttu-id="037a1-170">Para o Azure SQL DB, Entity Framework Core já fornece lógica de resiliência e repetição de conexão de banco de dados interno.</span><span class="sxs-lookup"><span data-stu-id="037a1-170">For Azure SQL DB, Entity Framework Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="037a1-171">Mas você precisa habilitar a estratégia de execução de Entity Framework para cada conexão DbContext se você quiser que têm conexões de EF Core.</span><span class="sxs-lookup"><span data-stu-id="037a1-171">But you need to enable the Entity Framework execution strategy for each DbContext connection if you want to have resilient EF Core connections.</span></span>

<span data-ttu-id="037a1-172">Por exemplo, o código a seguir no nível de conexão do EF Core permite conexões de SQL que são repetidas se a conexão falhar.</span><span class="sxs-lookup"><span data-stu-id="037a1-172">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

```csharp
// Startup.cs from any ASP.NET Core Web API
public class Startup
{
    public IServiceProvider ConfigureServices(IServiceCollection services)
    {
        //...
        services.AddDbContext<OrderingContext>(options =>
        {
            options.UseSqlServer(Configuration["ConnectionString"],
            sqlServerOptionsAction: sqlOptions =>
        {
            sqlOptions.EnableRetryOnFailure(
            maxRetryCount: 5,
            maxRetryDelay: TimeSpan.FromSeconds(30), 
            errorNumbersToAdd: null); 
        });
    });
}
//...
```

  #### <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="037a1-173">Estratégias de execução e transações explícitas usando BeginTransaction e vários DbContexts</span><span class="sxs-lookup"><span data-stu-id="037a1-173">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span> 
  
  <span data-ttu-id="037a1-174">Quando novas tentativas são habilitadas em conexões EF Core, cada operação que você executar usando EF principal se torna sua própria operação repetível.</span><span class="sxs-lookup"><span data-stu-id="037a1-174">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retriable operation.</span></span> <span data-ttu-id="037a1-175">Cada chamada para SaveChanges e cada consulta serão repetidas como uma unidade se ocorrer uma falha temporária.</span><span class="sxs-lookup"><span data-stu-id="037a1-175">Each query and each call to SaveChanges will be retried as a unit if a transient failure occurs.</span></span>
  
  <span data-ttu-id="037a1-176">No entanto, se seu código inicia uma transação usando BeginTransaction, você está definindo seu próprio grupo de operações que precisam ser tratados como uma unidade — tudo dentro da transação ser revertida se ocorrer uma falha.</span><span class="sxs-lookup"><span data-stu-id="037a1-176">However, if your code initiates a transaction using BeginTransaction, you are defining your own group of operations that need to be treated as a unit—everything inside the transaction has be rolled back if a failure occurs.</span></span> <span data-ttu-id="037a1-177">Se você tentar executar a transação ao usar uma estratégia de execução EF (política de repetição) e incluir várias SaveChanges de vários DbContexts nele, você verá uma exceção semelhante ao seguinte.</span><span class="sxs-lookup"><span data-stu-id="037a1-177">You will see an exception like the following if you attempt to execute that transaction when using an EF execution strategy (retry policy) and you include several SaveChanges from multiple DbContexts in it.</span></span>

<span data-ttu-id="037a1-178">System. InvalidOperationException: A estratégia de execução configurada 'SqlServerRetryingExecutionStrategy' não oferece suporte a transações iniciadas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="037a1-178">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="037a1-179">Use a estratégia de execução retornada por 'DbContext.Database.CreateExecutionStrategy()' para executar todas as operações na transação como uma unidade repetível.</span><span class="sxs-lookup"><span data-stu-id="037a1-179">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retriable unit.</span></span>

<span data-ttu-id="037a1-180">A solução é chamar a estratégia de execução EF manualmente com um delegado que representa tudo o que precisa ser executada.</span><span class="sxs-lookup"><span data-stu-id="037a1-180">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="037a1-181">Se ocorrer uma falha transitória, a estratégia de execução invocará o representante novamente.</span><span class="sxs-lookup"><span data-stu-id="037a1-181">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="037a1-182">O código a seguir mostra como implementar essa abordagem:</span><span class="sxs-lookup"><span data-stu-id="037a1-182">The following code shows how to implement this approach:</span></span>

```csharp
// Use of an EF Core resiliency strategy when using multiple DbContexts
// within an explicit transaction
// See:
// https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
var strategy = _catalogContext.Database.CreateExecutionStrategy(); 
await strategy.ExecuteAsync(async () =>
{
    // Achieving atomicity between original Catalog database operation and the
    // IntegrationEventLog thanks to a local transaction
    using (var transaction = _catalogContext.Database.BeginTransaction())
    {
        _catalogContext.CatalogItems.Update(catalogItem);
        await _catalogContext.SaveChangesAsync();
        
        // Save to EventLog only if product price changed
        if (raiseProductPriceChangedEvent)
        await _integrationEventLogService.SaveEventAsync(priceChangedEvent);
        transaction.Commit();
    }
});
```

<span data-ttu-id="037a1-183">É o primeiro DbContext o \_catalogContext e o segundo DbContext está dentro a \_integrationEventLogService objeto.</span><span class="sxs-lookup"><span data-stu-id="037a1-183">The first DbContext is the \_catalogContext and the second DbContext is within the \_integrationEventLogService object.</span></span> <span data-ttu-id="037a1-184">Por fim, a confirmação de ação deve ser executada várias DbContexts e usando uma estratégia de execução EF.</span><span class="sxs-lookup"><span data-stu-id="037a1-184">Finally, the Commit action would be performed multiple DbContexts and using an EF Execution Strategy.</span></span>

> ### <a name="references--entity-framework-core"></a><span data-ttu-id="037a1-185">Referências – Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="037a1-185">References – Entity Framework Core</span></span>
> - <span data-ttu-id="037a1-186">**Documentos principais EF**</span><span class="sxs-lookup"><span data-stu-id="037a1-186">**EF Core Docs**</span></span>  
> <span data-ttu-id="037a1-187"><https://docs.microsoft.com/ef/></span><span class="sxs-lookup"><span data-stu-id="037a1-187"><https://docs.microsoft.com/ef/></span></span>
> - <span data-ttu-id="037a1-188">**EF principal: Dados relacionados**</span><span class="sxs-lookup"><span data-stu-id="037a1-188">**EF Core: Related Data**</span></span>  
> <span data-ttu-id="037a1-189"><https://docs.microsoft.com/ef/core/querying/related-data></span><span class="sxs-lookup"><span data-stu-id="037a1-189"><https://docs.microsoft.com/ef/core/querying/related-data></span></span>
> - <span data-ttu-id="037a1-190">**Evite entidades de carregamento lento em aplicativos ASPNET**</span><span class="sxs-lookup"><span data-stu-id="037a1-190">**Avoid Lazy Loading Entities in ASPNET Applications**</span></span>  
> <span data-ttu-id="037a1-191"><http://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications></span><span class="sxs-lookup"><span data-stu-id="037a1-191"><http://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications></span></span>

## <a name="ef-core-or-micro-orm"></a><span data-ttu-id="037a1-192">EF Core ou MICRO-ORM?</span><span class="sxs-lookup"><span data-stu-id="037a1-192">EF Core or micro-ORM?</span></span>

<span data-ttu-id="037a1-193">Enquanto o EF Core é uma ótima opção para o gerenciamento de persistência e para a maior parte encapsula os detalhes de banco de dados de desenvolvedores de aplicativos, não é a única opção.</span><span class="sxs-lookup"><span data-stu-id="037a1-193">While EF Core is a great choice for managing persistence, and for the most part encapsulates database details from application developers, it is not the only choice.</span></span> <span data-ttu-id="037a1-194">Outra alternativa de código aberto popular é [Dapper](https://github.com/StackExchange/Dapper), um MICRO-ORM chamado.</span><span class="sxs-lookup"><span data-stu-id="037a1-194">Another popular open source alternative is [Dapper](https://github.com/StackExchange/Dapper), a so-called micro-ORM.</span></span> <span data-ttu-id="037a1-195">Um MICRO-ORM é uma leve, menos ferramenta completa para o mapeamento de objetos para estruturas de dados.</span><span class="sxs-lookup"><span data-stu-id="037a1-195">A micro-ORM is a lightweight, less full-featured tool for mapping objects to data structures.</span></span> <span data-ttu-id="037a1-196">No caso de Dapper, seu design metas foque no desempenho, em vez de consulta totalmente encapsular subjacente usa para recuperar e atualizar dados.</span><span class="sxs-lookup"><span data-stu-id="037a1-196">In the case of Dapper, its design goals focus on performance, rather than fully encapsulating the underlying queries it uses to retrieve and update data.</span></span> <span data-ttu-id="037a1-197">Porque ele não abstrata SQL do desenvolvedor, Dapper "mais próximo de metal" e permite que desenvolvedores gravem exato consultas que desejam usar para uma determinada data acessarem a operação.</span><span class="sxs-lookup"><span data-stu-id="037a1-197">Because it doesn't abstract SQL from the developer, Dapper is "closer to the metal" and lets developers write the exact queries they want to use for a given data access operation.</span></span>

<span data-ttu-id="037a1-198">EF Core tem dois recursos significativos fornece que separam de Dapper, mas também adicionar à sua sobrecarga de desempenho.</span><span class="sxs-lookup"><span data-stu-id="037a1-198">EF Core has two significant features it provides which separate it from Dapper but also add to its performance overhead.</span></span> <span data-ttu-id="037a1-199">A primeira é a tradução de expressões LINQ para SQL.</span><span class="sxs-lookup"><span data-stu-id="037a1-199">The first is translation from LINQ expressions into SQL.</span></span> <span data-ttu-id="037a1-200">Essas conversões são armazenados em cache, mas ainda assim há sobrecarga em execução na primeira vez.</span><span class="sxs-lookup"><span data-stu-id="037a1-200">These translations are cached, but even so there is overhead in performing them the first time.</span></span> <span data-ttu-id="037a1-201">A segunda é que o controle de alterações em entidades (de forma que as instruções update eficiente podem ser geradas).</span><span class="sxs-lookup"><span data-stu-id="037a1-201">The second is change tracking on entities (so that efficient update statements can be generated).</span></span> <span data-ttu-id="037a1-202">Esse comportamento pode ser desativado para consultas específicas usando a extensão AsNotTracking.</span><span class="sxs-lookup"><span data-stu-id="037a1-202">This behavior can be turned off for specific queries by using the AsNotTracking extension.</span></span> <span data-ttu-id="037a1-203">EF principal também gera consultas SQL que são geralmente muito eficiente e em qualquer caso perfeitamente aceitáveis de um ponto de vista de desempenho, mas se precisar excelente controle sobre a consulta precisa ser executada, você pode passar de SQL personalizados (ou executar um procedimento armazenado) usando EF Núcleo, muito.</span><span class="sxs-lookup"><span data-stu-id="037a1-203">EF Core also generates SQL queries that usually are very efficient and in any case perfectly acceptable from a performance standpoint, but if you need fine control over the precise query to be executed, you can pass in custom SQL (or execute a stored procedure) using EF Core, too.</span></span> <span data-ttu-id="037a1-204">Nesse caso, ainda Dapper supera EF Core, mas somente um pouco.</span><span class="sxs-lookup"><span data-stu-id="037a1-204">In this case, Dapper still outperforms EF Core, but only slightly.</span></span> <span data-ttu-id="037a1-205">Julie Lerman apresenta alguns dados de desempenho em sua podem artigo do MSDN 2016 [Dapper, Entity Framework e aplicativos híbridos](https://msdn.microsoft.com/magazine/mt703432.aspx).</span><span class="sxs-lookup"><span data-stu-id="037a1-205">Julie Lerman presents some performance data in her May 2016 MSDN article [Dapper, Entity Framework, and Hybrid Apps](https://msdn.microsoft.com/magazine/mt703432.aspx).</span></span> <span data-ttu-id="037a1-206">Dados de parâmetro de comparação de desempenho adicionais para uma variedade de métodos de acesso de dados podem ser encontrados no [o site Dapper](https://github.com/StackExchange/Dapper).</span><span class="sxs-lookup"><span data-stu-id="037a1-206">Additional performance benchmark data for a variety of data access methods can be found on [the Dapper site](https://github.com/StackExchange/Dapper).</span></span>

<span data-ttu-id="037a1-207">Para ver como a sintaxe para Dapper varia EF núcleo, considere estas duas versões do mesmo método para recuperar uma lista de itens:</span><span class="sxs-lookup"><span data-stu-id="037a1-207">To see how the syntax for Dapper varies from EF Core, consider these two versions of the same method for retrieving a list of items:</span></span>

```csharp
// EF Core
private readonly CatalogContext _context;
public async Task<IEnumerable<CatalogType>> GetCatalogTypes()
{
    return await _context.CatalogTypes.ToListAsync();
}

// Dapper
private readonly SqlConnection _conn;
public async Task<IEnumerable<CatalogType>> GetCatalogTypesWithDapper()
{
    return await _conn.QueryAsync<CatalogType>("SELECT * FROM CatalogType");
}
```

<span data-ttu-id="037a1-208">Se você precisar criar gráficos de objeto mais complexos com Dapper, você precisa gravar as consultas associadas (em vez de adicionar uma inclusão como você faria no núcleo do EF).</span><span class="sxs-lookup"><span data-stu-id="037a1-208">If you need to build more complex object graphs with Dapper, you need to write the associated queries yourself (as opposed to adding an Include as you would in EF Core).</span></span> <span data-ttu-id="037a1-209">Isso é suportado por meio de uma variedade de sintaxes, incluindo um recurso chamado várias mapeamento que lhe permite mapear as linhas individuais para vários objetos mapeados.</span><span class="sxs-lookup"><span data-stu-id="037a1-209">This is supported through a variety of syntaxes, including a feature called Multi Mapping that lets you map individual rows to multiple mapped objects.</span></span> <span data-ttu-id="037a1-210">Por exemplo, dada a classe Post com uma propriedade do proprietário do tipo de usuário, o SQL a seguir retornará todos os dados necessários:</span><span class="sxs-lookup"><span data-stu-id="037a1-210">For example, given a class Post with a property Owner of type User, the following SQL would return all of the necessary data:</span></span>

```sql
select * from #Posts p
left join \#Users u on u.Id = p.OwnerId
Order by p.Id
```

<span data-ttu-id="037a1-211">Cada linha retornada inclui dados de usuário e o Post.</span><span class="sxs-lookup"><span data-stu-id="037a1-211">Each returned row includes both User and Post data.</span></span> <span data-ttu-id="037a1-212">Como os dados de usuário devem ser conectados aos dados de postagem por meio de sua propriedade de proprietário, a função a seguir é usada:</span><span class="sxs-lookup"><span data-stu-id="037a1-212">Since the User data should be attached to the Post data via its Owner property, the following function is used:</span></span>

```csharp
(post, user) => { post.Owner = user; return post; }
```

<span data-ttu-id="037a1-213">A listagem de código completa para retornar uma coleção de postagens com a propriedade proprietário preenchida com os dados de usuário associada seria:</span><span class="sxs-lookup"><span data-stu-id="037a1-213">The full code listing to return a collection of posts with their Owner property populated with the associated user data would be:</span></span>

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

<span data-ttu-id="037a1-214">Porque ele oferece menos encapsulamento, Dapper exige que os desenvolvedores saber mais sobre como os dados são armazenados, como consultá-los de forma eficiente e escrever código mais para obtê-lo.</span><span class="sxs-lookup"><span data-stu-id="037a1-214">Because it offers less encapsulation, Dapper requires developers know more about how their data is stored, how to query it efficiently, and write more code to fetch it.</span></span> <span data-ttu-id="037a1-215">Quando o modelo for alterado, em vez de simplesmente criar uma nova migração (outro recurso principal do EF) e/ou atualizar informações de mapeamento em um local em um DbContext, cada consulta que é afetada deve ser atualizada.</span><span class="sxs-lookup"><span data-stu-id="037a1-215">When the model changes, instead of simply creating a new migration (another EF Core feature), and/or updating mapping information in one place in a DbContext, every query that is impacted must be updated.</span></span> <span data-ttu-id="037a1-216">Essas consultas tem não garantias de tempo de compilação, portanto, eles podem ser quebradas em tempo de execução em resposta a alterações no modelo ou banco de dados, tornando os erros mais difíceis de detectar rapidamente.</span><span class="sxs-lookup"><span data-stu-id="037a1-216">These queries have not compile time guarantees, so they may break at runtime in response to changes to the model or database, making errors more difficult to detect quickly.</span></span> <span data-ttu-id="037a1-217">Em compensação essa possibilidade, Dapper oferece um desempenho extremamente rápido.</span><span class="sxs-lookup"><span data-stu-id="037a1-217">In exchange for these tradeoffs, Dapper offers extremely fast performance.</span></span>

<span data-ttu-id="037a1-218">Para a maioria dos aplicativos e a maioria das partes de quase todos os aplicativos, Core EF oferece um desempenho aceitável.</span><span class="sxs-lookup"><span data-stu-id="037a1-218">For most applications, and most parts of almost all applications, EF Core offers acceptable performance.</span></span> <span data-ttu-id="037a1-219">Portanto, seus benefícios de produtividade do desenvolvedor são provavelmente superam sua sobrecarga de desempenho.</span><span class="sxs-lookup"><span data-stu-id="037a1-219">Thus, its developer productivity benefits are likely to outweigh its performance overhead.</span></span> <span data-ttu-id="037a1-220">Para consultas que podem se beneficiar do cache, a consulta real pode ser executada apenas uma pequena porcentagem do tempo, fazer relativamente pequeno questão de diferenças de desempenho de consulta.</span><span class="sxs-lookup"><span data-stu-id="037a1-220">For queries that can benefit from caching, the actual query may only be executed a tiny percentage of the time, making relatively small query performance differences moot.</span></span>

## <a name="sql-or-nosql"></a><span data-ttu-id="037a1-221">SQL ou NoSQL</span><span class="sxs-lookup"><span data-stu-id="037a1-221">SQL or NoSQL</span></span>

<span data-ttu-id="037a1-222">Tradicionalmente, bancos de dados relacionais, como o SQL Server tem influenciado mercado para armazenamento de dados persistentes, mas eles não são a única solução disponível.</span><span class="sxs-lookup"><span data-stu-id="037a1-222">Traditionally, relational databases like SQL Server have dominated the marketplace for persistent data storage, but they are not the only solution available.</span></span> <span data-ttu-id="037a1-223">Bancos de dados NoSQL, como [MongoDB](https://www.mongodb.com/what-is-mongodb) oferecem uma abordagem diferente para armazenar objetos.</span><span class="sxs-lookup"><span data-stu-id="037a1-223">NoSQL databases like [MongoDB](https://www.mongodb.com/what-is-mongodb) offer a different approach to storing objects.</span></span> <span data-ttu-id="037a1-224">Em vez de objetos de mapeamento para tabelas e linhas, outra opção é serializar o gráfico de objeto inteiro e armazenar o resultado.</span><span class="sxs-lookup"><span data-stu-id="037a1-224">Rather than mapping objects to tables and rows, another option is to serialize the entire object graph, and store the result.</span></span> <span data-ttu-id="037a1-225">Os benefícios dessa abordagem são pelo menos inicialmente, simplicidade e desempenho.</span><span class="sxs-lookup"><span data-stu-id="037a1-225">The benefits of this approach, at least initially, are simplicity and performance.</span></span> <span data-ttu-id="037a1-226">É certamente mais simples armazenar um único objeto serializado com uma chave ao decompor o objeto em muitas tabelas com relações e atualização e linhas que podem ter sido alterado desde que o objeto foi recuperado do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="037a1-226">It's certainly simpler to store a single serialized object with a key than to decompose the object into many tables with relationships and update and rows that may have changed since the object was last retrieved from the database.</span></span> <span data-ttu-id="037a1-227">Da mesma forma, busca e a desserialização de um único objeto de um repositório de chave é geralmente muito mais rápido e mais fácil do que as junções complexas ou várias consultas de banco de dados necessárias para compor totalmente o mesmo objeto de banco de dados relacional.</span><span class="sxs-lookup"><span data-stu-id="037a1-227">Likewise, fetching and deserializing a single object from a key-based store is typically much faster and easier than complex joins or multiple database queries required to fully compose the same object from a relational database.</span></span> <span data-ttu-id="037a1-228">A falta de bloqueios ou transações ou um esquema fixo também facilita a bancos de dados NoSQL muito receptivos ao dimensionamento em várias máquinas, dando suporte a conjuntos de dados muito grandes.</span><span class="sxs-lookup"><span data-stu-id="037a1-228">The lack of locks or transactions or a fixed schema also makes NoSQL databases very amenable to scaling across many machines, supporting very large datasets.</span></span>

<span data-ttu-id="037a1-229">Por outro lado, bancos de dados NoSQL (conforme eles normalmente são chamados) tem algumas desvantagens.</span><span class="sxs-lookup"><span data-stu-id="037a1-229">On the other hand, NoSQL databases (as they are typically called) have their drawbacks.</span></span> <span data-ttu-id="037a1-230">Bancos de dados relacionais usam a normalização para impor a consistência e evitar a duplicação de dados.</span><span class="sxs-lookup"><span data-stu-id="037a1-230">Relational databases use normalization to enforce consistency and avoid duplication of data.</span></span> <span data-ttu-id="037a1-231">Isso reduz o tamanho total do banco de dados e garante que as atualizações aos dados compartilhados estejam disponíveis imediatamente em todo o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="037a1-231">This reduces the total size of the database and ensures that updates to shared data are available immediately throughout the database.</span></span> <span data-ttu-id="037a1-232">Em um banco de dados relacional, uma tabela de endereço pode referenciar uma tabela de país por ID, de modo que, se o nome do país foram alterado, os registros de endereço pode se beneficiar da atualização sem se precisar ser atualizado.</span><span class="sxs-lookup"><span data-stu-id="037a1-232">In a relational database, an Address table might reference a Country table by ID, such that if a country's name were changed, the address records would benefit from the update without themselves having to be updated.</span></span> <span data-ttu-id="037a1-233">No entanto, em um banco de dados NoSQL, endereço e seu país associado podem ser serializado como parte do número de objetos armazenado.</span><span class="sxs-lookup"><span data-stu-id="037a1-233">However, in a NoSQL database, Address and its associated Country might be serialized as part of many stored objects.</span></span> <span data-ttu-id="037a1-234">Uma atualização para um nome de país requer que todos esses objetos a serem atualizados, em vez de uma única linha.</span><span class="sxs-lookup"><span data-stu-id="037a1-234">An update to a country name would require all such objects to be updated, rather than a single row.</span></span> <span data-ttu-id="037a1-235">Bancos de dados relacionais também podem garantir a integridade relacional através da aplicação de regras, como chaves estrangeiras.</span><span class="sxs-lookup"><span data-stu-id="037a1-235">Relational databases can also ensure relational integrity by enforcing rules like foreign keys.</span></span> <span data-ttu-id="037a1-236">Bancos de dados NoSQL normalmente não oferecem essas restrições em seus dados.</span><span class="sxs-lookup"><span data-stu-id="037a1-236">NoSQL databases typically do not offer such constraints on their data.</span></span>

<span data-ttu-id="037a1-237">Complexidade outra NoSQL bancos de dados devem lidar com é o controle de versão.</span><span class="sxs-lookup"><span data-stu-id="037a1-237">Another complexity NoSQL databases must deal with is versioning.</span></span> <span data-ttu-id="037a1-238">Quando alteram propriedades de um objeto, ele não poderá ser desserializado das versões anteriores que foram armazenadas.</span><span class="sxs-lookup"><span data-stu-id="037a1-238">When an object's properties change, it may not be able to be deserialized from past versions that were stored.</span></span> <span data-ttu-id="037a1-239">Assim, todos os objetos existentes que têm uma versão (anterior) serializada do objeto devem ser atualizados para estar de acordo com seu novo esquema.</span><span class="sxs-lookup"><span data-stu-id="037a1-239">Thus, all existing objects that have a serialized (previous) version of the object must be updated to conform to its new schema.</span></span> <span data-ttu-id="037a1-240">Isso não é conceitualmente diferente de um banco de dados relacional, onde as alterações de esquema às vezes exigem scripts de atualização ou atualizações de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="037a1-240">This is not conceptually different from a relational database, where schema changes sometimes require update scripts or mapping updates.</span></span> <span data-ttu-id="037a1-241">No entanto, o número de entradas que devem ser modificados geralmente é muito maior na abordagem NoSQL, porque não há mais de eliminação de duplicação de dados.</span><span class="sxs-lookup"><span data-stu-id="037a1-241">However, the number of entries that must be modified is often much greater in the NoSQL approach, because there is more duplication of data.</span></span>

<span data-ttu-id="037a1-242">É possível em bancos de dados NoSQL para armazenar várias versões de objetos, bancos de dados relacionais do esquema fixo algo normalmente não oferecem suporte.</span><span class="sxs-lookup"><span data-stu-id="037a1-242">It's possible in NoSQL databases to store multiple versions of objects, something fixed schema relational databases typically do not support.</span></span> <span data-ttu-id="037a1-243">No entanto, nesse caso o código do aplicativo precisará levar em conta a existência de versões anteriores de objetos, adicionando complexidade adicional.</span><span class="sxs-lookup"><span data-stu-id="037a1-243">However, in this case your application code will need to account for the existence of previous versions of objects, adding additional complexity.</span></span>

<span data-ttu-id="037a1-244">Bancos de dados NoSQL normalmente não impõem [ACID](http://en.wikipedia.org/wiki/ACID), que significa que eles têm vantagens de desempenho e escalabilidade em bancos de dados relacionais.</span><span class="sxs-lookup"><span data-stu-id="037a1-244">NoSQL databases typically do not enforce [ACID](http://en.wikipedia.org/wiki/ACID), which means they have both performance and scalability benefits over relational databases.</span></span> <span data-ttu-id="037a1-245">Eles são ideais para extremamente grandes conjuntos de dados e objetos que não são apropriados para o armazenamento em estruturas de tabela normalizada.</span><span class="sxs-lookup"><span data-stu-id="037a1-245">They're well-suited to extremely large datasets and objects that are not well-suited to storage in normalized table structures.</span></span> <span data-ttu-id="037a1-246">Não há nenhum motivo por que um único aplicativo não pode tirar proveito de ambas relacionais e bancos de dados NoSQL, usando cada um em que é melhor adequada.</span><span class="sxs-lookup"><span data-stu-id="037a1-246">There is no reason why a single application cannot take advantage of both relational and NoSQL databases, using each where it is best suited.</span></span>

## <a name="azure-documentdb"></a><span data-ttu-id="037a1-247">Azure DocumentDB</span><span class="sxs-lookup"><span data-stu-id="037a1-247">Azure DocumentDB</span></span>

<span data-ttu-id="037a1-248">Documentos do Azure é um serviço de banco de dados NoSQL totalmente gerenciado que oferece armazenamento baseado em nuvem os dados sem esquema.</span><span class="sxs-lookup"><span data-stu-id="037a1-248">Azure DocumentDB is a fully managed NoSQL database service that offers cloud-based schema-free data storage.</span></span> <span data-ttu-id="037a1-249">DocumentDB é criado para desempenho rápido e previsível, alta disponibilidade, dimensionamento Elástico e distribuição global.</span><span class="sxs-lookup"><span data-stu-id="037a1-249">DocumentDB is built for fast and predictable performance, high availability, elastic scaling, and global distribution.</span></span> <span data-ttu-id="037a1-250">Apesar de ser um banco de dados NoSQL, os desenvolvedores podem usar familiares e avançados recursos de consulta SQL em dados JSON.</span><span class="sxs-lookup"><span data-stu-id="037a1-250">Despite being a NoSQL database, developers can use rich and familiar SQL query capabilities on JSON data.</span></span> <span data-ttu-id="037a1-251">Todos os recursos em documentos são armazenados como documentos JSON.</span><span class="sxs-lookup"><span data-stu-id="037a1-251">All resources in DocumentDB are stored as JSON documents.</span></span> <span data-ttu-id="037a1-252">Os recursos são gerenciados como *itens*, que são documentos que contém metadados, e *feeds*, que são coleções de itens.</span><span class="sxs-lookup"><span data-stu-id="037a1-252">Resources are managed as *items*, which are documents containing metadata, and *feeds*, which are collections of items.</span></span> <span data-ttu-id="037a1-253">Figura 8-2 mostra a relação entre os diferentes recursos de DocumentDB.</span><span class="sxs-lookup"><span data-stu-id="037a1-253">Figure 8-2 shows the relationship between different DocumentDB resources.</span></span>


![A relação hierárquica entre os recursos no DocumentDB, um banco de dados NoSQL JSON](./media/image8-2.png)

<span data-ttu-id="037a1-255">**Figura 8-2.**</span><span class="sxs-lookup"><span data-stu-id="037a1-255">**Figure 8-2.**</span></span> <span data-ttu-id="037a1-256">Organização do recurso de documentos.</span><span class="sxs-lookup"><span data-stu-id="037a1-256">DocumentDB resource organization.</span></span>

<span data-ttu-id="037a1-257">A linguagem de consulta do DocumentDB é uma interface simple e poderosas para consultar documentos JSON.</span><span class="sxs-lookup"><span data-stu-id="037a1-257">The DocumentDB query language is a simple yet powerful interface for querying JSON documents.</span></span> <span data-ttu-id="037a1-258">A linguagem dá suporte a um subconjunto de gramática SQL ANSI e adiciona integração profunda do objeto, matrizes, construção de objeto e invocação de função JavaScript.</span><span class="sxs-lookup"><span data-stu-id="037a1-258">The language supports a subset of ANSI SQL grammar and adds deep integration of JavaScript object, arrays, object construction, and function invocation.</span></span>

<span data-ttu-id="037a1-259">**Referências a documentos**</span><span class="sxs-lookup"><span data-stu-id="037a1-259">**References – DocumentDB**</span></span>

-   <span data-ttu-id="037a1-260">Documentos Introduction\\</span><span class="sxs-lookup"><span data-stu-id="037a1-260">DocumentDB Introduction\\</span></span>
    <span data-ttu-id="037a1-261"><https://docs.microsoft.com/azure/documentdb/documentdb-introduction></span><span class="sxs-lookup"><span data-stu-id="037a1-261"><https://docs.microsoft.com/azure/documentdb/documentdb-introduction></span></span>

## <a name="other-persistence-options"></a><span data-ttu-id="037a1-262">Outras opções de persistência</span><span class="sxs-lookup"><span data-stu-id="037a1-262">Other Persistence Options</span></span>

<span data-ttu-id="037a1-263">Além relacionais e NoSQL opções de armazenamento, aplicativos do ASP.NET Core podem usar o armazenamento do Azure para armazenar uma variedade de formatos de dados e arquivos de forma escalonável, baseado em nuvem.</span><span class="sxs-lookup"><span data-stu-id="037a1-263">In addition to relational and NoSQL storage options, ASP.NET Core applications can use Azure Storage to store a variety of data formats and files in a cloud-based, scalable fashion.</span></span> <span data-ttu-id="037a1-264">Armazenamento do Azure é altamente escalonável, portanto, você pode iniciar out armazenar pequenas quantidades de dados e a escala até armazenar centenas ou terabytes, se seu aplicativo exija isso.</span><span class="sxs-lookup"><span data-stu-id="037a1-264">Azure Storage is massively scalable, so you can start out storing small amounts of data and scale up to storing hundreds or terabytes if your application requires it.</span></span> <span data-ttu-id="037a1-265">Armazenamento do Azure dá suporte a quatro tipos de dados:</span><span class="sxs-lookup"><span data-stu-id="037a1-265">Azure Storage supports four kinds of data:</span></span>

-   <span data-ttu-id="037a1-266">Armazenamento de blob para texto não estruturado ou armazenamento binário, também conhecido como armazenamento de objeto.</span><span class="sxs-lookup"><span data-stu-id="037a1-266">Blob Storage for unstructured text or binary storage, also referred to as object storage.</span></span>

-   <span data-ttu-id="037a1-267">Armazenamento de tabelas para conjuntos de dados estruturados, acessíveis por meio de chaves de linha.</span><span class="sxs-lookup"><span data-stu-id="037a1-267">Table Storage for structured datasets, accessible via row keys.</span></span>

-   <span data-ttu-id="037a1-268">Armazenamento de fila de mensagens confiáveis com base em fila.</span><span class="sxs-lookup"><span data-stu-id="037a1-268">Queue Storage for reliable queue-based messaging.</span></span>

-   <span data-ttu-id="037a1-269">Armazenamento de arquivo para acesso a arquivos compartilhados entre aplicativos locais e de máquinas virtuais do Azure.</span><span class="sxs-lookup"><span data-stu-id="037a1-269">File Storage for shared file access between Azure virtual machines and on-premises applications.</span></span>

<span data-ttu-id="037a1-270">**Referências – armazenamento do Azure**</span><span class="sxs-lookup"><span data-stu-id="037a1-270">**References – Azure Storage**</span></span>

-   <span data-ttu-id="037a1-271">Introduction\ de armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="037a1-271">Azure Storage Introduction\\</span></span>
    <span data-ttu-id="037a1-272"><https://docs.microsoft.com/azure/storage/storage-introduction></span><span class="sxs-lookup"><span data-stu-id="037a1-272"><https://docs.microsoft.com/azure/storage/storage-introduction></span></span>

## <a name="caching"></a><span data-ttu-id="037a1-273">Cache</span><span class="sxs-lookup"><span data-stu-id="037a1-273">Caching</span></span>

<span data-ttu-id="037a1-274">Em aplicativos web, cada solicitação da web deve ser concluída no menor tempo possível.</span><span class="sxs-lookup"><span data-stu-id="037a1-274">In web applications, each web request should be completed in the shortest time possible.</span></span> <span data-ttu-id="037a1-275">Uma maneira de fazer isso é limitar o número de chamadas externas, que o servidor deve fazer para concluir a solicitação.</span><span class="sxs-lookup"><span data-stu-id="037a1-275">One way to achieve this is to limit the number of external calls the server must make to complete the request.</span></span> <span data-ttu-id="037a1-276">Cache envolve armazenar uma cópia dos dados no servidor (ou outros de repositório de dados que é mais facilmente consultado que a fonte de dados).</span><span class="sxs-lookup"><span data-stu-id="037a1-276">Caching involves storing a copy of data on the server (or another data store that is more easily queried than the source of the data).</span></span> <span data-ttu-id="037a1-277">Aplicativos da Web e especialmente aplicativos web tradicionais não SPA, necessário criar a interface do usuário com cada solicitação.</span><span class="sxs-lookup"><span data-stu-id="037a1-277">Web applications, and especially non-SPA traditional web applications, need to build the entire user interface with every request.</span></span> <span data-ttu-id="037a1-278">Isso geralmente envolve muitas das mesmas consultas de banco de dados repetidamente da solicitação de um usuário para o próximo.</span><span class="sxs-lookup"><span data-stu-id="037a1-278">This frequently involves making many of the same database queries repeatedly from one user request to the next.</span></span> <span data-ttu-id="037a1-279">Na maioria dos casos, esses dados sejam alterados raramente, portanto, há justificam constantemente solicitá-la do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="037a1-279">In most cases, this data changes rarely, so there is little reason to constantly request it from the database.</span></span> <span data-ttu-id="037a1-280">ASP.NET Core dá suporte a cache de resposta, para armazenar em cache páginas inteiras e cache de dados, que dá suporte ao comportamento de cache mais granular.</span><span class="sxs-lookup"><span data-stu-id="037a1-280">ASP.NET Core supports response caching, for caching entire pages, and data caching, which supports more granular caching behavior.</span></span>

<span data-ttu-id="037a1-281">Ao implementar o armazenamento em cache, é importante manter na separação de ideia de problemas.</span><span class="sxs-lookup"><span data-stu-id="037a1-281">When implementing caching, it's important to keep in mind separation of concerns.</span></span> <span data-ttu-id="037a1-282">Evite implementando lógica de cache em sua lógica de acesso a dados, ou em sua interface de usuário.</span><span class="sxs-lookup"><span data-stu-id="037a1-282">Avoid implementing caching logic in your data access logic, or in your user interface.</span></span> <span data-ttu-id="037a1-283">Em vez disso, encapsular o cache em suas próprias classes e usar a configuração para gerenciar seu comportamento.</span><span class="sxs-lookup"><span data-stu-id="037a1-283">Instead, encapsulate caching in its own classes, and use configuration to manage its behavior.</span></span> <span data-ttu-id="037a1-284">Isso segue o aberto/fechado e princípios de responsabilidade única e tornará mais fácil para você gerenciar como você usa o cache em seu aplicativo à medida que cresce.</span><span class="sxs-lookup"><span data-stu-id="037a1-284">This follows the Open/Closed and Single Responsibility principles, and will make it easier for you to manage how you use caching in your application as it grows.</span></span>

### <a name="aspnet-core-response-caching"></a><span data-ttu-id="037a1-285">O cache de resposta do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="037a1-285">ASP.NET Core Response Caching</span></span>

<span data-ttu-id="037a1-286">ASP.NET Core dá suporte a dois níveis de cache de resposta.</span><span class="sxs-lookup"><span data-stu-id="037a1-286">ASP.NET Core supports two levels of response caching.</span></span> <span data-ttu-id="037a1-287">O primeiro nível não armazena em cache nada no servidor, mas adiciona cabeçalhos HTTP que instruem os clientes e servidores proxy para respostas de cache.</span><span class="sxs-lookup"><span data-stu-id="037a1-287">The first level does not cache anything on the server, but adds HTTP headers that instruct clients and proxy servers to cache responses.</span></span> <span data-ttu-id="037a1-288">Isso é implementado, adicionando o atributo ResponseCache controladores individuais ou ações:</span><span class="sxs-lookup"><span data-stu-id="037a1-288">This is implemented by adding the ResponseCache attribute to individual controllers or actions:</span></span>

```csharp
    [ResponseCache(Duration = 60)]
    public IActionResult Contact()
    { }
    
    ViewData["Message"] = "Your contact page.";
    return View();
}

The above example will result in the following header being added to the response, instructing clients to cache the result for up to 60 seconds.

Cache-Control: public,max-age=60

In order to add server-side in-memory caching to the application, you must reference the Microsoft.AspNetCore.ResponseCaching NuGet package, and then add the Response Caching middleware. This middleware is configured in both ConfigureServices and Configure in Startup:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddResponseCaching();
}

public void Configure(IApplicationBuilder app)
{
    app.UseResponseCaching();
}
```

<span data-ttu-id="037a1-289">O Middleware de cache de resposta automaticamente armazenará em cache respostas com base em um conjunto de condições que você pode personalizar.</span><span class="sxs-lookup"><span data-stu-id="037a1-289">The Response Caching Middleware will automatically cache responses based on a set of conditions, which you can customize.</span></span> <span data-ttu-id="037a1-290">Por padrão, apenas 200 respostas (Okey) solicitadas por meio de métodos GET ou HEAD são armazenadas em cache.</span><span class="sxs-lookup"><span data-stu-id="037a1-290">By default, only 200 (OK) responses requested via GET or HEAD methods are cached.</span></span> <span data-ttu-id="037a1-291">Além disso, as solicitações devem ter uma resposta com um Cache-Control: cabeçalho público e não pode incluir cabeçalhos de autorização ou Set-Cookie.</span><span class="sxs-lookup"><span data-stu-id="037a1-291">In addition, requests must have a response with a Cache-Control: public header, and cannot include headers for Authorization or Set-Cookie.</span></span> <span data-ttu-id="037a1-292">Consulte uma [lista completa das condições cache usada pela resposta de cache middleware](https://docs.microsoft.com/aspnet/core/performance/caching/middleware#conditions-for-caching).</span><span class="sxs-lookup"><span data-stu-id="037a1-292">See a [complete list of the caching conditions used by the response caching middleware](https://docs.microsoft.com/aspnet/core/performance/caching/middleware#conditions-for-caching).</span></span>

### <a name="data-caching"></a><span data-ttu-id="037a1-293">Cache de dados</span><span class="sxs-lookup"><span data-stu-id="037a1-293">Data Caching</span></span>

<span data-ttu-id="037a1-294">Em vez de (ou além) armazenar em cache respostas de web completo, você pode armazenar em cache os resultados de consultas de dados individuais.</span><span class="sxs-lookup"><span data-stu-id="037a1-294">Rather than (or in addition to) caching full web responses, you can cache the results of individual data queries.</span></span> <span data-ttu-id="037a1-295">Para isso, você pode usar no cache de memória no servidor web ou usar [um cache distribuído](https://docs.microsoft.com/aspnet/core/performance/caching/distributed).</span><span class="sxs-lookup"><span data-stu-id="037a1-295">For this, you can use in memory caching on the web server, or use [a distributed cache](https://docs.microsoft.com/aspnet/core/performance/caching/distributed).</span></span> <span data-ttu-id="037a1-296">Esta seção demonstrará como implementar no cache de memória.</span><span class="sxs-lookup"><span data-stu-id="037a1-296">This section will demonstrate how to implement in memory caching.</span></span>

<span data-ttu-id="037a1-297">Adicionar suporte para memória (ou distribuído) ConfigureServices de cache:</span><span class="sxs-lookup"><span data-stu-id="037a1-297">You add support for memory (or distributed) caching in ConfigureServices:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

<span data-ttu-id="037a1-298">Certifique-se de adicionar o pacote do Microsoft.Extensions.Caching.Memory NuGet também.</span><span class="sxs-lookup"><span data-stu-id="037a1-298">Be sure to add the Microsoft.Extensions.Caching.Memory NuGet package as well.</span></span>

<span data-ttu-id="037a1-299">Depois de adicionar o serviço, você solicitar IMemoryCache por meio de injeção de dependência sempre que você precisa acessar o cache.</span><span class="sxs-lookup"><span data-stu-id="037a1-299">Once you've added the service, you request IMemoryCache via dependency injection wherever you need to access the cache.</span></span> <span data-ttu-id="037a1-300">Neste exemplo, o CachedCatalogService está usando o padrão de design de Proxy (ou decorador), fornecendo uma implementação alternativa de ICatalogService que controla o acesso ao (ou adiciona um comportamento) a implementação CatalogService subjacente.</span><span class="sxs-lookup"><span data-stu-id="037a1-300">In this example, the CachedCatalogService is using the Proxy (or Decorator) design pattern, by providing an alternative implementation of ICatalogService that controls access to (or adds behavior to) the underlying CatalogService implementation.</span></span>

```csharp
public class CachedCatalogService : ICatalogService
{
    private readonly IMemoryCache _cache;
    private readonly CatalogService _catalogService;
    private static readonly string _brandsKey = "brands";
    private static readonly string _typesKey = "types";
    private static readonly string _itemsKeyTemplate = "items-{0}-{1}-{2}-{3}";
    private static readonly TimeSpan _defaultCacheDuration = TimeSpan.FromSeconds(30);
    public CachedCatalogService(IMemoryCache cache,
    CatalogService catalogService)
    {
        _cache = cache;
        _catalogService = catalogService;
    }
    
    public async Task<IEnumerable<SelectListItem>> GetBrands()
    {
        return await _cache.GetOrCreateAsync(_brandsKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetBrands();
        });
    }
    
    public async Task<Catalog> GetCatalogItems(int pageIndex, int itemsPage, int? brandID, int? typeId)
    {
        string cacheKey = String.Format(_itemsKeyTemplate, pageIndex, itemsPage, brandID, typeId);
        return await _cache.GetOrCreateAsync(cacheKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetCatalogItems(pageIndex, itemsPage, brandID, typeId);
        });
    }
    
    public async Task<IEnumerable<SelectListItem>> GetTypes()
    {
        return await _cache.GetOrCreateAsync(_typesKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetTypes();
        });
    }
}
```

<span data-ttu-id="037a1-301">Para configurar o aplicativo para usar a versão armazenada em cache do serviço, mas ainda permitir que o serviço obter a instância de CatalogService que precisa de seu construtor, adicione o seguinte no ConfigureServices:</span><span class="sxs-lookup"><span data-stu-id="037a1-301">To configure the application to use the cached version of the service, but still allow the service to get the instance of CatalogService it needs in its constructor, you would add the following in ConfigureServices:</span></span>

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

<span data-ttu-id="037a1-302">Com isso em vigor, as chamadas de banco de dados para buscar os dados de catálogo serão feitas apenas uma vez por minuto, em vez de em cada solicitação.</span><span class="sxs-lookup"><span data-stu-id="037a1-302">With this in place, the database calls to fetch the catalog data will only be made once per minute, rather than on every request.</span></span> <span data-ttu-id="037a1-303">Dependendo do tráfego para o site, isso pode ter um impacto significativo muito o número de consultas feitas para o banco de dados e o tempo de carregamento de página médio para a home page que depende de três das consultas expostas por este serviço no momento.</span><span class="sxs-lookup"><span data-stu-id="037a1-303">Depending on the traffic to the site, this can have a very significant impact on the number of queries made to the database, and the average page load time for the home page that currently depends on all three of the queries exposed by this service.</span></span>

<span data-ttu-id="037a1-304">É um problema que ocorre quando o cache é implementado *dados obsoletos* – ou seja, os dados que foram alterados em uma versão desatualizada, mas a fonte permanecem no cache.</span><span class="sxs-lookup"><span data-stu-id="037a1-304">An issue that arises when caching is implemented is *stale data* – that is, data that has changed at the source but an out of date version remains in the cache.</span></span> <span data-ttu-id="037a1-305">Uma maneira simples de atenuar esse problema é usar pequenas durações de cache, pois há benefícios adicionais limitados para estender o comprimento de dados é armazenado em cache para um aplicativo ocupado.</span><span class="sxs-lookup"><span data-stu-id="037a1-305">A simple way to mitigate this issue is to use small cache durations, since for a busy application there is limited additional benefit to extending the length data is cached.</span></span> <span data-ttu-id="037a1-306">Por exemplo, considere uma página que faz com que uma consulta de banco de dados único, e é solicitado 10 vezes por segundo.</span><span class="sxs-lookup"><span data-stu-id="037a1-306">For example, consider a page that makes a single database query, and is requested 10 times per second.</span></span> <span data-ttu-id="037a1-307">Se esta página é armazenada em cache por um minuto, resultará no número de consultas de banco de dados feitas por minuto para soltar de 600 para 1, uma redução de 99,8%.</span><span class="sxs-lookup"><span data-stu-id="037a1-307">If this page is cached for one minute, it will result in the number of database queries made per minute to drop from 600 to 1, a reduction of 99.8%.</span></span> <span data-ttu-id="037a1-308">Se em vez disso, a duração do cache foi feita uma hora, a redução global seria 99.997%, mas a idade de probabilidade e o potencial de dados obsoletos são ambos aumenta consideravelmente.</span><span class="sxs-lookup"><span data-stu-id="037a1-308">If instead the cache duration were made one hour, the overall reduction would be 99.997%, but now the likelihood and potential age of stale data are both increased dramatically.</span></span>

<span data-ttu-id="037a1-309">Outra abordagem é proativamente remover entradas de cache quando os dados que eles contêm são atualizados.</span><span class="sxs-lookup"><span data-stu-id="037a1-309">Another approach is to proactively remove cache entries when the data they contain is updated.</span></span> <span data-ttu-id="037a1-310">Todas as entradas individuais podem ser removidas se a chave for conhecida:</span><span class="sxs-lookup"><span data-stu-id="037a1-310">Any individual entry can be removed if its key is known:</span></span>

```csharp
_cache.Remove(cacheKey);
```

<span data-ttu-id="037a1-311">Se seu aplicativo expõe a funcionalidade para atualizar as entradas que ele armazena em cache, você pode remover as entradas de cache correspondentes no seu código que executa as atualizações.</span><span class="sxs-lookup"><span data-stu-id="037a1-311">If your application exposes functionality for updating entries that it caches, you can remove the corresponding cache entries in your code that performs the updates.</span></span> <span data-ttu-id="037a1-312">Às vezes, pode haver muitas entradas diferentes que dependem de um determinado conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="037a1-312">Sometimes there may be many different entries that depend on a particular set of data.</span></span> <span data-ttu-id="037a1-313">Nesse caso, pode ser útil criar dependências entre as entradas de cache, usando um CancellationChangeToken.</span><span class="sxs-lookup"><span data-stu-id="037a1-313">In that case, it can be useful to create dependencies between cache entries, by using a CancellationChangeToken.</span></span> <span data-ttu-id="037a1-314">Com um CancellationChangeToken, você pode expirar várias entradas de cache de uma vez ao cancelar o token.</span><span class="sxs-lookup"><span data-stu-id="037a1-314">With a CancellationChangeToken, you can expire multiple cache entries at once by cancelling the token.</span></span>

```csharp
// configure CancellationToken and add entry to cache
var cts = new CancellationTokenSource();
_cache.Set("cts", cts);
_cache.Set(cacheKey,
itemToCache,
new CancellationChangeToken(cts.Token));

// elsewhere, expire the cache by cancelling the token\
_cache.Get<CancellationTokenSource>("cts").Cancel();
```

>[!div class="step-by-step"]
<span data-ttu-id="037a1-315">[Anterior] (develop-asp-net-core-mvc-apps.md) [Avançar] (test-asp-net-core-mvc-apps.md)</span><span class="sxs-lookup"><span data-stu-id="037a1-315">[Previous] (develop-asp-net-core-mvc-apps.md) [Next] (test-asp-net-core-mvc-apps.md)</span></span>
