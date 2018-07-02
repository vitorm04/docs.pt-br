---
title: Trabalhar com os dados em aplicativos ASP.NET Core
description: Projetar aplicativos Web modernos com o ASP.NET Core e o Azure | trabalhando com os dados no ASP
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.openlocfilehash: c9f1350f57ed649b9bf53968c19ab652b3c74384
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106169"
---
# <a name="working-with-data-in-aspnet-core-apps"></a><span data-ttu-id="e5869-103">Trabalhando com os dados em aplicativos ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e5869-103">Working with Data in ASP.NET Core Apps</span></span>

> <span data-ttu-id="e5869-104">"Os dados são uma coisa preciosa e vão durar mais do que os próprios sistemas."</span><span class="sxs-lookup"><span data-stu-id="e5869-104">"Data is a precious thing and will last longer than the systems themselves."</span></span>

<span data-ttu-id="e5869-105">Tim Berners-Lee</span><span class="sxs-lookup"><span data-stu-id="e5869-105">Tim Berners-Lee</span></span>

## <a name="summary"></a><span data-ttu-id="e5869-106">Resumo</span><span class="sxs-lookup"><span data-stu-id="e5869-106">Summary</span></span>

<span data-ttu-id="e5869-107">O acesso a dados é uma parte importante de praticamente qualquer aplicativo de software.</span><span class="sxs-lookup"><span data-stu-id="e5869-107">Data access is an important part of almost any software application.</span></span> <span data-ttu-id="e5869-108">O ASP.NET Core é compatível com uma variedade de opções de acesso a dados, incluindo o Entity Framework Core (e também o Entity Framework 6) e pode trabalhar com qualquer estrutura de acesso a dados do .NET.</span><span class="sxs-lookup"><span data-stu-id="e5869-108">ASP.NET Core supports a variety of data access options, including Entity Framework Core (and Entity Framework 6 as well), and can work with any .NET data access framework.</span></span> <span data-ttu-id="e5869-109">A escolha de qual estrutura de acesso a dados usar depende das necessidades do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e5869-109">The choice of which data access framework to use depends on the application's needs.</span></span> <span data-ttu-id="e5869-110">A abstração dessas opções dos projetos de ApplicationCore e de interface do usuário e o encapsulamento dos detalhes de implementação na Infraestrutura ajudam a produzir um software testável e com acoplamento flexível.</span><span class="sxs-lookup"><span data-stu-id="e5869-110">Abstracting these choices from the ApplicationCore and UI projects, and encapsulating implementation details in Infrastructure, helps to produce loosely coupled, testable software.</span></span>

## <a name="entity-framework-core-for-relational-databases"></a><span data-ttu-id="e5869-111">Entity Framework Core (para bancos de dados relacionais)</span><span class="sxs-lookup"><span data-stu-id="e5869-111">Entity Framework Core (for relational databases)</span></span>

<span data-ttu-id="e5869-112">Caso você esteja escrevendo um novo aplicativo ASP.NET Core que precisa trabalhar com os dados relacionais, o EF Core (Entity Framework Core) é a maneira recomendada para que seu aplicativo acesse os dados.</span><span class="sxs-lookup"><span data-stu-id="e5869-112">If you're writing a new ASP.NET Core application that needs to work with relational data, then Entity Framework Core (EF Core) is the recommended way for your application to access its data.</span></span> <span data-ttu-id="e5869-113">O EF Core é um O/RM (mapeador relacional de objeto) que permite aos desenvolvedores do .NET persistir objetos bidirecionalmente em uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="e5869-113">EF Core is an object-relational mapper (O/RM) that enables .NET developers to persist objects to and from a data source.</span></span> <span data-ttu-id="e5869-114">Elimina a necessidade da maioria do código de acesso a dados que os desenvolvedores geralmente precisam escrever.</span><span class="sxs-lookup"><span data-stu-id="e5869-114">It eliminates the need for most of the data access code developers would typically need to write.</span></span> <span data-ttu-id="e5869-115">Assim como o ASP.NET Core, o EF Core foi totalmente reformulado para dar suporte a aplicativos modulares multiplataforma.</span><span class="sxs-lookup"><span data-stu-id="e5869-115">Like ASP.NET Core, EF Core has been rewritten from the ground up to support modular cross-platform applications.</span></span> <span data-ttu-id="e5869-116">Você adiciona-o ao aplicativo como um pacote NuGet, configura-o em Startup e solicita-o por meio da injeção de dependência sempre que precisar dela.</span><span class="sxs-lookup"><span data-stu-id="e5869-116">You add it to your application as a NuGet package, configure it in Startup, and request it through dependency injection wherever you need it.</span></span>

<span data-ttu-id="e5869-117">Para usar o EF Core com um banco de dados do SQL Server, execute o seguinte comando da CLI do dotnet:</span><span class="sxs-lookup"><span data-stu-id="e5869-117">To use EF Core with a SQL Server database, run the following dotnet CLI command:</span></span>

<span data-ttu-id="e5869-118">dotnet add package Microsoft.EntityFrameworkCore.SqlServer</span><span class="sxs-lookup"><span data-stu-id="e5869-118">dotnet add package Microsoft.EntityFrameworkCore.SqlServer</span></span>

<span data-ttu-id="e5869-119">Para adicionar suporte para uma fonte de dados InMemory para teste:</span><span class="sxs-lookup"><span data-stu-id="e5869-119">To add support for an InMemory data source, for testing:</span></span>

<span data-ttu-id="e5869-120">dotnet add package Microsoft.EntityFrameworkCore.InMemory</span><span class="sxs-lookup"><span data-stu-id="e5869-120">dotnet add package Microsoft.EntityFrameworkCore.InMemory</span></span>

### <a name="the-dbcontext"></a><span data-ttu-id="e5869-121">O DbContext</span><span class="sxs-lookup"><span data-stu-id="e5869-121">The DbContext</span></span>

<span data-ttu-id="e5869-122">Para trabalhar com o EF Core, você precisa de uma subclasse de DbContext.</span><span class="sxs-lookup"><span data-stu-id="e5869-122">To work with EF Core, you need a subclass of DbContext.</span></span> <span data-ttu-id="e5869-123">Essa classe contém propriedades que representam coleções de entidades com as quais seu aplicativo trabalhará.</span><span class="sxs-lookup"><span data-stu-id="e5869-123">This class holds properties representing collections of the entities your application will work with.</span></span> <span data-ttu-id="e5869-124">A amostra de eShopOnWeb inclui um CatalogContext com coleções de itens, marcas e tipos:</span><span class="sxs-lookup"><span data-stu-id="e5869-124">The eShopOnWeb sample includes a CatalogContext with collections for items, brands, and types:</span></span>

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

<span data-ttu-id="e5869-125">O DbContext deve ter um construtor que aceite DbContextOptions e passa esse argumento para o construtor DbContext base.</span><span class="sxs-lookup"><span data-stu-id="e5869-125">Your DbContext must have a constructor that accepts DbContextOptions and pass this argument to the base DbContext constructor.</span></span> <span data-ttu-id="e5869-126">Observe que, se você tiver apenas um DbContext no aplicativo, poderá passar uma instância de DbContextOptions, mas se tiver mais de um, deverá usar o tipo genérico DbContextOptions<T>, passando o tipo DbContext como o parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="e5869-126">Note that if you have only one DbContext in your application, you can pass an instance of DbContextOptions, but if you have more than one you must use the generic DbContextOptions<T> type, passing in your DbContext type as the generic parameter.</span></span>

### <a name="configuring-ef-core"></a><span data-ttu-id="e5869-127">Configurando o EF Core</span><span class="sxs-lookup"><span data-stu-id="e5869-127">Configuring EF Core</span></span>

<span data-ttu-id="e5869-128">No aplicativo ASP.NET Core, normalmente, você configurará o EF Core no método ConfigureServices.</span><span class="sxs-lookup"><span data-stu-id="e5869-128">In your ASP.NET Core application, you'll typically configure EF Core in your ConfigureServices method.</span></span> <span data-ttu-id="e5869-129">O EF Core usa um DbContextOptionsBuilder, que é compatível com vários métodos de extensão úteis para simplificar sua configuração.</span><span class="sxs-lookup"><span data-stu-id="e5869-129">EF Core uses a DbContextOptionsBuilder, which supports several helpful extension methods to streamline its configuration.</span></span> <span data-ttu-id="e5869-130">Para configurar o CatalogContext para que ele use um banco de dados do SQL Server com uma cadeia de conexão definida em Configuration, adicione o seguinte código ao ConfigureServices:</span><span class="sxs-lookup"><span data-stu-id="e5869-130">To configure CatalogContext to use a SQL Server database with a connection string defined in Configuration, you would add the following code to ConfigureServices:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

<span data-ttu-id="e5869-131">Para usar o banco de dados em memória:</span><span class="sxs-lookup"><span data-stu-id="e5869-131">To use the in-memory database:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

<span data-ttu-id="e5869-132">Depois de instalar o EF Core, criar um tipo filho do DbContext e configurá-lo em ConfigureServices, você estará pronto para usar o EF Core.</span><span class="sxs-lookup"><span data-stu-id="e5869-132">Once you have installed EF Core, created a DbContext child type, and configured it in ConfigureServices, you are ready to use EF Core.</span></span> <span data-ttu-id="e5869-133">Você pode solicitar uma instância do tipo DbContext em qualquer serviço que precisar dela e começar a trabalhar com as entidades persistentes usando o LINQ como se elas apenas estivessem em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="e5869-133">You can request an instance of your DbContext type in any service that needs it, and start working with your persisted entities using LINQ as if they were simply in a collection.</span></span> <span data-ttu-id="e5869-134">O EF Core faz o trabalho de converter as expressões LINQ em consultas SQL para armazenar e recuperar os dados.</span><span class="sxs-lookup"><span data-stu-id="e5869-134">EF Core does the work of translating your LINQ expressions into SQL queries to store and retrieve your data.</span></span>

<span data-ttu-id="e5869-135">Você pode ver as consultas executadas pelo EF Core configurando um agente e garantindo que seu nível está definido com, pelo menos, Informações, conforme mostrado na Figura 8-1.</span><span class="sxs-lookup"><span data-stu-id="e5869-135">You can see the queries EF Core is executing by configuring a logger and ensuring its level is set to at least Information, as shown in Figure 8-1.</span></span>

![](./media/image8-1.png)

<span data-ttu-id="e5869-136">Figura 8-1 Registrando em log consultas do EF Core no console</span><span class="sxs-lookup"><span data-stu-id="e5869-136">Figure 8-1 Logging EF Core queries to the console</span></span>

### <a name="fetching-and-storing-data"></a><span data-ttu-id="e5869-137">Buscando e armazenando dados</span><span class="sxs-lookup"><span data-stu-id="e5869-137">Fetching and Storing Data</span></span>

<span data-ttu-id="e5869-138">Para recuperar dados do EF Core, acesse a propriedade apropriada e use o LINQ para filtrar o resultado.</span><span class="sxs-lookup"><span data-stu-id="e5869-138">To retrieve data from EF Core, you access the appropriate property and use LINQ to filter the result.</span></span> <span data-ttu-id="e5869-139">Também use o LINQ para executar a projeção, transformando o resultado de um tipo para outro.</span><span class="sxs-lookup"><span data-stu-id="e5869-139">You can also use LINQ to perform projection, transforming the result from one type to another.</span></span> <span data-ttu-id="e5869-140">O seguinte exemplo recupera CatalogBrands, ordenadas por nome, filtradas por sua propriedade Enabled e projetadas em um tipo SelectListItem:</span><span class="sxs-lookup"><span data-stu-id="e5869-140">The following example would retrieve CatalogBrands, ordered by name, filtered by their Enabled property, and projected onto a SelectListItem type:</span></span>

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

<span data-ttu-id="e5869-141">É importante, no exemplo acima, adicionar a chamada a ToListAsync para executar a consulta imediatamente.</span><span class="sxs-lookup"><span data-stu-id="e5869-141">It's important in the above example to add the call to ToListAsync in order to execute the query immediately.</span></span> <span data-ttu-id="e5869-142">Caso contrário, a instrução atribuirá um IQueryable<SelectListItem> a brandItems, que não será executado até que seja enumerado.</span><span class="sxs-lookup"><span data-stu-id="e5869-142">Otherwise, the statement will assign an IQueryable<SelectListItem> to brandItems, which will not be executed until it is enumerated.</span></span> <span data-ttu-id="e5869-143">Há vantagens e desvantagens em retornar resultados IQueryable de métodos.</span><span class="sxs-lookup"><span data-stu-id="e5869-143">There are pros and cons to returning IQueryable results from methods.</span></span> <span data-ttu-id="e5869-144">Ele permite que a consulta construída pelo EF Core seja modificada ainda mais, mas também pode resultar em erros que ocorrem apenas em tempo de execução, caso as operações sejam adicionadas à consulta que o EF Core não pode converter.</span><span class="sxs-lookup"><span data-stu-id="e5869-144">It allows the query EF Core will construct to be further modified, but can also result in errors that only occur at runtime, if operations are added to the query that EF Core cannot translate.</span></span> <span data-ttu-id="e5869-145">Em geral, é mais seguro passar todos os filtros para o método que executa o acesso a dados e retornar uma coleção em memória (por exemplo, List<T>) como o resultado.</span><span class="sxs-lookup"><span data-stu-id="e5869-145">It's generally safer to pass any filters into the method performing the data access, and return back an in-memory collection (for example, List<T>) as the result.</span></span>

<span data-ttu-id="e5869-146">O EF Core controla as alterações nas entidades que ele busca da persistência.</span><span class="sxs-lookup"><span data-stu-id="e5869-146">EF Core tracks changes on entities it fetches from persistence.</span></span> <span data-ttu-id="e5869-147">Para salvar as alterações em uma entidade controlada, basta chamar o método SaveChanges no DbContext, verificando se ela é a mesma instância de DbContext que foi usada para buscar a entidade.</span><span class="sxs-lookup"><span data-stu-id="e5869-147">To save changes to a tracked entity, you just call the SaveChanges method on the DbContext, making sure it's the same DbContext instance that was used to fetch the entity.</span></span> <span data-ttu-id="e5869-148">A adição e remoção de entidades são feitas diretamente na propriedade DbSet apropriada, novamente com uma chamada a SaveChanges para executar os comandos de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="e5869-148">Adding and removing entities is directly on the appropriate DbSet property, again with a call to SaveChanges to execute the database commands.</span></span> <span data-ttu-id="e5869-149">O exemplo a seguir demonstra como adicionar, atualizar e remover entidades da persistência.</span><span class="sxs-lookup"><span data-stu-id="e5869-149">The following example demonstrates adding, updating, and removing entities from persistence.</span></span>

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

<span data-ttu-id="e5869-150">O EF Core é compatível com métodos síncronos e assíncronos para busca e salvamento.</span><span class="sxs-lookup"><span data-stu-id="e5869-150">EF Core supports both synchronous and async methods for fetching and saving.</span></span> <span data-ttu-id="e5869-151">Em aplicativos Web, é recomendável usar o padrão async/await com os métodos async, de modo que os threads do servidor Web não sejam bloqueados enquanto aguardam a conclusão das operações de acesso a dados.</span><span class="sxs-lookup"><span data-stu-id="e5869-151">In web applications, it's recommended to use the async/await pattern with the async methods, so that web server threads are not blocked while waiting for data access operations to complete.</span></span>

### <a name="fetching-related-data"></a><span data-ttu-id="e5869-152">Buscando dados relacionados</span><span class="sxs-lookup"><span data-stu-id="e5869-152">Fetching Related Data</span></span>

<span data-ttu-id="e5869-153">Quando o EF Core recupera entidades, ele popula todas as propriedades armazenadas diretamente nessa entidade no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="e5869-153">When EF Core retrieves entities, it populates all of the properties that are stored directly with that entity in the database.</span></span> <span data-ttu-id="e5869-154">Propriedades de navegação, como listas de entidades relacionadas, não são populadas e podem ter seu valor definido como nulo.</span><span class="sxs-lookup"><span data-stu-id="e5869-154">Navigation properties, such as lists of related entities, are not populated and may have their value set to null.</span></span> <span data-ttu-id="e5869-155">Isso garante que o EF Core não busca mais dados do que necessário, o que é especialmente importante para aplicativos Web, que devem processar solicitações e retornar respostas de uma maneira eficiente e com agilidade.</span><span class="sxs-lookup"><span data-stu-id="e5869-155">This ensures EF Core is not fetching more data than is needed, which is especially important for web applications, which must quickly process requests and return responses in an efficient manner.</span></span> <span data-ttu-id="e5869-156">Para incluir relações com uma entidade usando o *carregamento adiantado*, especifique a propriedade usando o método de extensão Include na consulta, conforme mostrado:</span><span class="sxs-lookup"><span data-stu-id="e5869-156">To include relationships with an entity using *eager loading*, you specify the property using the Include extension method on the query, as shown:</span></span>

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

<span data-ttu-id="e5869-157">Você pode incluir várias relações e também incluir sub-relações usando ThenInclude.</span><span class="sxs-lookup"><span data-stu-id="e5869-157">You can include multiple relationships, and you can also include sub-relationships using ThenInclude.</span></span> <span data-ttu-id="e5869-158">O EF Core executará uma única consulta para recuperar o conjunto resultante de entidades.</span><span class="sxs-lookup"><span data-stu-id="e5869-158">EF Core will execute a single query to retrieve the resulting set of entities.</span></span>

<span data-ttu-id="e5869-159">Outra opção para carregar dados relacionados é usar o *carregamento explícito*.</span><span class="sxs-lookup"><span data-stu-id="e5869-159">Another option for loading related data is to use *explicit loading*.</span></span> <span data-ttu-id="e5869-160">O carregamento explícito permite carregar dados adicionais em uma entidade que já foi recuperada.</span><span class="sxs-lookup"><span data-stu-id="e5869-160">Explicit loading allows you to load additional data into an entity that has already been retrieved.</span></span> <span data-ttu-id="e5869-161">Como isso envolve uma solicitação separada para o banco de dados, isso não é recomendado para aplicativos Web, que devem minimizar o número de viagens de ida e volta de banco de dados feitas por solicitação.</span><span class="sxs-lookup"><span data-stu-id="e5869-161">Since this involves a separate request to the database, it's not recommended for web applications, which should minimize the number of database round trips made per request.</span></span>

<span data-ttu-id="e5869-162">O *carregamento lento* é um recurso que carrega automaticamente os dados relacionados conforme eles são referenciados pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e5869-162">*Lazy loading* is a feature that automatically loads related data as it is referenced by the application.</span></span> <span data-ttu-id="e5869-163">Atualmente, não há compatibilidade com ele no EF Core, mas assim como ocorre com o carregamento explícito, normalmente, ele deve ser desabilitado para aplicativos Web.</span><span class="sxs-lookup"><span data-stu-id="e5869-163">It's not currently supported by EF Core, but as with explicit loading it should typically be disabled for web applications.</span></span>

### <a name="resilient-connections"></a><span data-ttu-id="e5869-164">Conexões resilientes</span><span class="sxs-lookup"><span data-stu-id="e5869-164">Resilient Connections</span></span>

<span data-ttu-id="e5869-165">Recursos externos, como bancos de dados SQL, ocasionalmente, podem não estar disponíveis.</span><span class="sxs-lookup"><span data-stu-id="e5869-165">External resources like SQL databases may occasionally be unavailable.</span></span> <span data-ttu-id="e5869-166">Em caso de indisponibilidade temporária, os aplicativos podem usar a lógica de repetição para evitar gerar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="e5869-166">In cases of temporary unavailability, applications can use retry logic to avoid raising an exception.</span></span> <span data-ttu-id="e5869-167">Em geral, essa técnica é conhecida como *resiliência de conexão*.</span><span class="sxs-lookup"><span data-stu-id="e5869-167">This technique is commonly referred to as *connection resiliency*.</span></span> <span data-ttu-id="e5869-168">Implemente sua [própria técnica de repetição com retirada exponencial](https://docs.microsoft.com/azure/architecture/patterns/retry) pela tentativa de repetição com um tempo de espera aumentando exponencialmente, até atingir um número máximo de repetições.</span><span class="sxs-lookup"><span data-stu-id="e5869-168">You can implement your [own retry with exponential backoff](https://docs.microsoft.com/azure/architecture/patterns/retry) technique by attempting to rety with an exponentially increasing wait time, until a maximum retry count has been reached.</span></span> <span data-ttu-id="e5869-169">Essa técnica aceita o fato de que os recursos de nuvem podem estar intermitentemente não disponíveis por curtos períodos, resultando na falha de algumas solicitações.</span><span class="sxs-lookup"><span data-stu-id="e5869-169">This technique embraces the fact that cloud resources might intermittently be unavailable for short periods of time, resulting in failure of some requests.</span></span>

<span data-ttu-id="e5869-170">Para o BD SQL do Azure, o Entity Framework Core já fornece resiliência interna de conexão de banco de dados e lógica de repetição.</span><span class="sxs-lookup"><span data-stu-id="e5869-170">For Azure SQL DB, Entity Framework Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="e5869-171">Mas você precisará habilitar a estratégia de execução do Entity Framework para cada conexão de DbContext, caso deseje ter conexões do EF Core resilientes.</span><span class="sxs-lookup"><span data-stu-id="e5869-171">But you need to enable the Entity Framework execution strategy for each DbContext connection if you want to have resilient EF Core connections.</span></span>

<span data-ttu-id="e5869-172">Por exemplo, o código a seguir no nível de conexão do EF Core permite conexões SQL resilientes que serão repetidas se a conexão falhar.</span><span class="sxs-lookup"><span data-stu-id="e5869-172">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

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

  #### <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="e5869-173">Estratégias de execução e transações explícitas que usam BeginTransaction e várias DbContexts</span><span class="sxs-lookup"><span data-stu-id="e5869-173">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span> 
  
  <span data-ttu-id="e5869-174">Quando novas tentativas são habilitadas em conexões do EF Core, cada operação executada que usa o EF Core se torna sua própria operação repetível.</span><span class="sxs-lookup"><span data-stu-id="e5869-174">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retriable operation.</span></span> <span data-ttu-id="e5869-175">Cada consulta e cada chamada a SaveChanges serão repetidas como uma unidade se ocorrer uma falha temporária.</span><span class="sxs-lookup"><span data-stu-id="e5869-175">Each query and each call to SaveChanges will be retried as a unit if a transient failure occurs.</span></span>
  
  <span data-ttu-id="e5869-176">No entanto, se seu código iniciar uma transação usando BeginTransaction, você estará definindo seu próprio grupo de operações que precisam ser tratadas como uma unidade – tudo dentro da transação precisará ser revertido se ocorrer uma falha.</span><span class="sxs-lookup"><span data-stu-id="e5869-176">However, if your code initiates a transaction using BeginTransaction, you are defining your own group of operations that need to be treated as a unit—everything inside the transaction has be rolled back if a failure occurs.</span></span> <span data-ttu-id="e5869-177">Você verá uma exceção como a mostrada a seguir se tentar executar essa transação ao usar uma estratégia de execução do EF (política de repetição) e incluir várias chamadas SaveChanges de diversos DbContexts na transação.</span><span class="sxs-lookup"><span data-stu-id="e5869-177">You will see an exception like the following if you attempt to execute that transaction when using an EF execution strategy (retry policy) and you include several SaveChanges from multiple DbContexts in it.</span></span>

<span data-ttu-id="e5869-178">System.InvalidOperationException: a estratégia de execução configurada 'SqlServerRetryingExecutionStrategy' não dá suporte a transações iniciadas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="e5869-178">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="e5869-179">Use a estratégia de execução retornada por 'DbContext.Database.CreateExecutionStrategy()' para executar todas as operações na transação como uma unidade repetível.</span><span class="sxs-lookup"><span data-stu-id="e5869-179">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retriable unit.</span></span>

<span data-ttu-id="e5869-180">A solução é invocar manualmente a estratégia de execução do EF com um delegado que representa tudo que precisa ser executado.</span><span class="sxs-lookup"><span data-stu-id="e5869-180">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="e5869-181">Se ocorrer uma falha temporária, a estratégia de execução invocará o delegado novamente.</span><span class="sxs-lookup"><span data-stu-id="e5869-181">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="e5869-182">O seguinte código mostra como implementar essa abordagem:</span><span class="sxs-lookup"><span data-stu-id="e5869-182">The following code shows how to implement this approach:</span></span>

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

<span data-ttu-id="e5869-183">O primeiro DbContext é o \_catalogContext e o segundo DbContext está dentro do objeto \_integrationEventLogService.</span><span class="sxs-lookup"><span data-stu-id="e5869-183">The first DbContext is the \_catalogContext and the second DbContext is within the \_integrationEventLogService object.</span></span> <span data-ttu-id="e5869-184">Por fim, a ação de Confirmação é executada em vários DbContexts e usando uma Estratégia de Execução do EF.</span><span class="sxs-lookup"><span data-stu-id="e5869-184">Finally, the Commit action would be performed multiple DbContexts and using an EF Execution Strategy.</span></span>

> ### <a name="references--entity-framework-core"></a><span data-ttu-id="e5869-185">Referências – Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="e5869-185">References – Entity Framework Core</span></span>
> - <span data-ttu-id="e5869-186">**Documentação do EF Core**</span><span class="sxs-lookup"><span data-stu-id="e5869-186">**EF Core Docs**</span></span>  
> <https://docs.microsoft.com/ef/>
> - <span data-ttu-id="e5869-187">**EF Core: Dados relacionados**</span><span class="sxs-lookup"><span data-stu-id="e5869-187">**EF Core: Related Data**</span></span>  
> <https://docs.microsoft.com/ef/core/querying/related-data>
> - <span data-ttu-id="e5869-188">**Evitar entidades de carregamento lento em aplicativos ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="e5869-188">**Avoid Lazy Loading Entities in ASPNET Applications**</span></span>  
> <https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications>

## <a name="ef-core-or-micro-orm"></a><span data-ttu-id="e5869-189">EF Core ou micro-ORM?</span><span class="sxs-lookup"><span data-stu-id="e5869-189">EF Core or micro-ORM?</span></span>

<span data-ttu-id="e5869-190">Embora o EF Core seja uma ótima opção para o gerenciamento da persistência e, na maioria das vezes, encapsule os detalhes de banco de dados para abstraí-los dos desenvolvedores de aplicativos, ele não é a única opção.</span><span class="sxs-lookup"><span data-stu-id="e5869-190">While EF Core is a great choice for managing persistence, and for the most part encapsulates database details from application developers, it is not the only choice.</span></span> <span data-ttu-id="e5869-191">Outra alternativa de software livre popular é o [Dapper](https://github.com/StackExchange/Dapper), um assim chamado micro-ORM.</span><span class="sxs-lookup"><span data-stu-id="e5869-191">Another popular open source alternative is [Dapper](https://github.com/StackExchange/Dapper), a so-called micro-ORM.</span></span> <span data-ttu-id="e5869-192">Um micro-ORM é uma ferramenta leve e menos completa para o mapeamento de objetos para estruturas de dados.</span><span class="sxs-lookup"><span data-stu-id="e5869-192">A micro-ORM is a lightweight, less full-featured tool for mapping objects to data structures.</span></span> <span data-ttu-id="e5869-193">No caso do Dapper, seu design visa o foco no desempenho, em vez do encapsulamento total das consultas subjacentes usadas por ele para recuperar e atualizar os dados.</span><span class="sxs-lookup"><span data-stu-id="e5869-193">In the case of Dapper, its design goals focus on performance, rather than fully encapsulating the underlying queries it uses to retrieve and update data.</span></span> <span data-ttu-id="e5869-194">Como ele não abstrai o SQL do desenvolvedor, o Dapper fica "mais próximo do metal" e permite aos desenvolvedores escreverem as consultas exatas que desejam usar para determinada operação de acesso a dados.</span><span class="sxs-lookup"><span data-stu-id="e5869-194">Because it doesn't abstract SQL from the developer, Dapper is "closer to the metal" and lets developers write the exact queries they want to use for a given data access operation.</span></span>

<span data-ttu-id="e5869-195">O EF Core tem dois recursos significativos que os separam do Dapper, mas também contribuem com a sobrecarga de desempenho.</span><span class="sxs-lookup"><span data-stu-id="e5869-195">EF Core has two significant features it provides which separate it from Dapper but also add to its performance overhead.</span></span> <span data-ttu-id="e5869-196">O primeiro é a conversão de expressões LINQ em SQL.</span><span class="sxs-lookup"><span data-stu-id="e5869-196">The first is translation from LINQ expressions into SQL.</span></span> <span data-ttu-id="e5869-197">Essas conversões são armazenadas em cache, mas ainda assim há sobrecarga na execução na primeira vez.</span><span class="sxs-lookup"><span data-stu-id="e5869-197">These translations are cached, but even so there is overhead in performing them the first time.</span></span> <span data-ttu-id="e5869-198">O segundo é o controle de alterações em entidades (de forma que instruções de atualização eficientes possam ser geradas).</span><span class="sxs-lookup"><span data-stu-id="e5869-198">The second is change tracking on entities (so that efficient update statements can be generated).</span></span> <span data-ttu-id="e5869-199">Esse comportamento pode ser desativado para consultas específicas com a extensão AsNotTracking.</span><span class="sxs-lookup"><span data-stu-id="e5869-199">This behavior can be turned off for specific queries by using the AsNotTracking extension.</span></span> <span data-ttu-id="e5869-200">O EF Core também gera consultas SQL que geralmente são muito eficientes e, de qualquer modo, perfeitamente aceitáveis do ponto de vista de desempenho. No entanto, caso precise ter um controle refinado sobre a consulta precisa a ser executada, passe um SQL personalizado (ou execute um procedimento armazenado) usando o EF Core também.</span><span class="sxs-lookup"><span data-stu-id="e5869-200">EF Core also generates SQL queries that usually are very efficient and in any case perfectly acceptable from a performance standpoint, but if you need fine control over the precise query to be executed, you can pass in custom SQL (or execute a stored procedure) using EF Core, too.</span></span> <span data-ttu-id="e5869-201">Nesse caso, o Dapper ainda supera o EF Core, mas somente um pouco.</span><span class="sxs-lookup"><span data-stu-id="e5869-201">In this case, Dapper still outperforms EF Core, but only slightly.</span></span> <span data-ttu-id="e5869-202">Julie Lerman apresenta alguns dados de desempenho em seu artigo do MSDN de maio de 2016 [Dapper, Entity Framework e aplicativos híbridos](https://msdn.microsoft.com/magazine/mt703432.aspx).</span><span class="sxs-lookup"><span data-stu-id="e5869-202">Julie Lerman presents some performance data in her May 2016 MSDN article [Dapper, Entity Framework, and Hybrid Apps](https://msdn.microsoft.com/magazine/mt703432.aspx).</span></span> <span data-ttu-id="e5869-203">Encontre dados de parâmetro de comparação de desempenho adicionais para uma variedade de métodos de acesso a dados [no site do Dapper](https://github.com/StackExchange/Dapper).</span><span class="sxs-lookup"><span data-stu-id="e5869-203">Additional performance benchmark data for a variety of data access methods can be found on [the Dapper site](https://github.com/StackExchange/Dapper).</span></span>

<span data-ttu-id="e5869-204">Para ver a diferença entre a sintaxe do Dapper e do EF Core, considere estas duas versões do mesmo método para recuperar uma lista de itens:</span><span class="sxs-lookup"><span data-stu-id="e5869-204">To see how the syntax for Dapper varies from EF Core, consider these two versions of the same method for retrieving a list of items:</span></span>

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

<span data-ttu-id="e5869-205">Caso você precise criar gráficos de objetos mais complexos com o Dapper, precisará escrever as consultas associadas (em vez de adicionar um método Include como faria no EF Core).</span><span class="sxs-lookup"><span data-stu-id="e5869-205">If you need to build more complex object graphs with Dapper, you need to write the associated queries yourself (as opposed to adding an Include as you would in EF Core).</span></span> <span data-ttu-id="e5869-206">Isso é compatível com uma variedade de sintaxes, incluindo um recurso chamado Mapeamento Múltiplo, que permite mapear linhas individuais para vários objetos mapeados.</span><span class="sxs-lookup"><span data-stu-id="e5869-206">This is supported through a variety of syntaxes, including a feature called Multi Mapping that lets you map individual rows to multiple mapped objects.</span></span> <span data-ttu-id="e5869-207">Por exemplo, considerando uma classe Post com uma propriedade Owner do tipo User, o seguinte SQL retorna todos os dados necessários:</span><span class="sxs-lookup"><span data-stu-id="e5869-207">For example, given a class Post with a property Owner of type User, the following SQL would return all of the necessary data:</span></span>

```sql
select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id
```

<span data-ttu-id="e5869-208">Cada linha retornada inclui os dados de User e Post.</span><span class="sxs-lookup"><span data-stu-id="e5869-208">Each returned row includes both User and Post data.</span></span> <span data-ttu-id="e5869-209">Como os dados de User devem ser anexados aos dados de Post por meio de sua propriedade Owner, a seguinte função é usada:</span><span class="sxs-lookup"><span data-stu-id="e5869-209">Since the User data should be attached to the Post data via its Owner property, the following function is used:</span></span>

```csharp
(post, user) => { post.Owner = user; return post; }
```

<span data-ttu-id="e5869-210">A listagem de código completa para retornar uma coleção de postagens com a propriedade Owner populada com os dados de usuário associados é:</span><span class="sxs-lookup"><span data-stu-id="e5869-210">The full code listing to return a collection of posts with their Owner property populated with the associated user data would be:</span></span>

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

<span data-ttu-id="e5869-211">Como ele oferece menos encapsulamento, o Dapper exige que os desenvolvedores saibam mais sobre como seus dados são armazenados, como consultá-los de forma eficiente e codificar mais para buscá-los.</span><span class="sxs-lookup"><span data-stu-id="e5869-211">Because it offers less encapsulation, Dapper requires developers know more about how their data is stored, how to query it efficiently, and write more code to fetch it.</span></span> <span data-ttu-id="e5869-212">Quando o modelo é alterado, em vez de simplesmente criar uma nova migração (outro recurso do EF Core) e/ou atualizar as informações de mapeamento em um local em um DbContext, cada consulta afetada deve ser atualizada.</span><span class="sxs-lookup"><span data-stu-id="e5869-212">When the model changes, instead of simply creating a new migration (another EF Core feature), and/or updating mapping information in one place in a DbContext, every query that is impacted must be updated.</span></span> <span data-ttu-id="e5869-213">Essas consultas não têm garantias de tempo de compilação e, portanto, podem ser interrompidas em tempo de execução em resposta a alterações no modelo ou no banco de dados, tornando os erros mais difíceis de serem detectados rapidamente.</span><span class="sxs-lookup"><span data-stu-id="e5869-213">These queries have not compile time guarantees, so they may break at runtime in response to changes to the model or database, making errors more difficult to detect quickly.</span></span> <span data-ttu-id="e5869-214">Em compensação por essa vantagem, o Dapper oferece um desempenho extremamente rápido.</span><span class="sxs-lookup"><span data-stu-id="e5869-214">In exchange for these tradeoffs, Dapper offers extremely fast performance.</span></span>

<span data-ttu-id="e5869-215">Para a maioria dos aplicativos e a maioria das partes de quase todos os aplicativos, o EF Core oferece um desempenho aceitável.</span><span class="sxs-lookup"><span data-stu-id="e5869-215">For most applications, and most parts of almost all applications, EF Core offers acceptable performance.</span></span> <span data-ttu-id="e5869-216">Portanto, seus benefícios de produtividade do desenvolvedor provavelmente superam a sobrecarga de desempenho.</span><span class="sxs-lookup"><span data-stu-id="e5869-216">Thus, its developer productivity benefits are likely to outweigh its performance overhead.</span></span> <span data-ttu-id="e5869-217">Para consultas que podem se beneficiar com o cache, a consulta real pode ser executada apenas em um pequeno percentual do tempo, tornando irrelevantes as pequenas diferenças no desempenho da consulta.</span><span class="sxs-lookup"><span data-stu-id="e5869-217">For queries that can benefit from caching, the actual query may only be executed a tiny percentage of the time, making relatively small query performance differences moot.</span></span>

## <a name="sql-or-nosql"></a><span data-ttu-id="e5869-218">SQL ou NoSQL</span><span class="sxs-lookup"><span data-stu-id="e5869-218">SQL or NoSQL</span></span>

<span data-ttu-id="e5869-219">Tradicionalmente, bancos de dados relacionais como o SQL Server dominaram o marketplace em armazenamento de dados persistente, mas não são a única solução disponível.</span><span class="sxs-lookup"><span data-stu-id="e5869-219">Traditionally, relational databases like SQL Server have dominated the marketplace for persistent data storage, but they are not the only solution available.</span></span> <span data-ttu-id="e5869-220">Bancos de dados NoSQL, como o [MongoDB](https://www.mongodb.com/what-is-mongodb), oferecem uma abordagem diferente para armazenar objetos.</span><span class="sxs-lookup"><span data-stu-id="e5869-220">NoSQL databases like [MongoDB](https://www.mongodb.com/what-is-mongodb) offer a different approach to storing objects.</span></span> <span data-ttu-id="e5869-221">Em vez de mapear objetos para tabelas e linhas, outra opção é serializar o grafo de objeto inteiro e armazenar o resultado.</span><span class="sxs-lookup"><span data-stu-id="e5869-221">Rather than mapping objects to tables and rows, another option is to serialize the entire object graph, and store the result.</span></span> <span data-ttu-id="e5869-222">Os benefícios dessa abordagem são, pelo menos inicialmente, simplicidade e desempenho.</span><span class="sxs-lookup"><span data-stu-id="e5869-222">The benefits of this approach, at least initially, are simplicity and performance.</span></span> <span data-ttu-id="e5869-223">É certamente mais simples armazenar um único objeto serializado com uma chave do que decompor o objeto em muitas tabelas com relações e atualizar as linhas que podem ter sido alteradas desde a última recuperação do objeto do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="e5869-223">It's certainly simpler to store a single serialized object with a key than to decompose the object into many tables with relationships and update and rows that may have changed since the object was last retrieved from the database.</span></span> <span data-ttu-id="e5869-224">Da mesma forma, a busca e a desserialização de um único objeto de um repositório baseado em chaves geralmente são muito mais rápidas e mais fáceis do que junções complexas ou várias consultas de banco de dados necessárias para compor totalmente o mesmo objeto de um banco de dados relacional.</span><span class="sxs-lookup"><span data-stu-id="e5869-224">Likewise, fetching and deserializing a single object from a key-based store is typically much faster and easier than complex joins or multiple database queries required to fully compose the same object from a relational database.</span></span> <span data-ttu-id="e5869-225">A falta de bloqueios ou transações ou de um esquema fixo também torna os bancos de dados NoSQL muito receptivos ao dimensionamento em vários computadores, dando suporte a conjuntos de dados muito grandes.</span><span class="sxs-lookup"><span data-stu-id="e5869-225">The lack of locks or transactions or a fixed schema also makes NoSQL databases very amenable to scaling across many machines, supporting very large datasets.</span></span>

<span data-ttu-id="e5869-226">Por outro lado, os bancos de dados NoSQL (como são normalmente chamados) trazem algumas desvantagens.</span><span class="sxs-lookup"><span data-stu-id="e5869-226">On the other hand, NoSQL databases (as they are typically called) have their drawbacks.</span></span> <span data-ttu-id="e5869-227">Os bancos de dados relacionais usam a normalização para impor a consistência e evitar a duplicação de dados.</span><span class="sxs-lookup"><span data-stu-id="e5869-227">Relational databases use normalization to enforce consistency and avoid duplication of data.</span></span> <span data-ttu-id="e5869-228">Isso reduz o tamanho total do banco de dados e garante que as atualizações nos dados compartilhados estejam disponíveis imediatamente em todo o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="e5869-228">This reduces the total size of the database and ensures that updates to shared data are available immediately throughout the database.</span></span> <span data-ttu-id="e5869-229">Em um banco de dados relacional, uma tabela Address pode referenciar uma tabela Country por ID, de modo que, se o nome do país for alterado, os registros de endereço se beneficiarão com a atualização sem que eles mesmos precisem ser atualizados.</span><span class="sxs-lookup"><span data-stu-id="e5869-229">In a relational database, an Address table might reference a Country table by ID, such that if a country's name were changed, the address records would benefit from the update without themselves having to be updated.</span></span> <span data-ttu-id="e5869-230">No entanto, em um banco de dados NoSQL, Address e seu Country associado podem ser serializados como parte de muitos objetos armazenados.</span><span class="sxs-lookup"><span data-stu-id="e5869-230">However, in a NoSQL database, Address and its associated Country might be serialized as part of many stored objects.</span></span> <span data-ttu-id="e5869-231">Uma atualização em um nome de país exige que todos esses objetos sejam atualizados, em vez de uma única linha.</span><span class="sxs-lookup"><span data-stu-id="e5869-231">An update to a country name would require all such objects to be updated, rather than a single row.</span></span> <span data-ttu-id="e5869-232">Os bancos de dados relacionais também podem garantir a integridade relacional pela imposição de regras como chaves estrangeiras.</span><span class="sxs-lookup"><span data-stu-id="e5869-232">Relational databases can also ensure relational integrity by enforcing rules like foreign keys.</span></span> <span data-ttu-id="e5869-233">Normalmente, os bancos de dados NoSQL não oferecem essas restrições em seus dados.</span><span class="sxs-lookup"><span data-stu-id="e5869-233">NoSQL databases typically do not offer such constraints on their data.</span></span>

<span data-ttu-id="e5869-234">Outra complexidade com a qual os bancos de dados NoSQL precisar lidar é o controle de versão.</span><span class="sxs-lookup"><span data-stu-id="e5869-234">Another complexity NoSQL databases must deal with is versioning.</span></span> <span data-ttu-id="e5869-235">Quando as propriedades de um objeto são alteradas, ele pode não ser desserializado das versões anteriores que foram armazenadas.</span><span class="sxs-lookup"><span data-stu-id="e5869-235">When an object's properties change, it may not be able to be deserialized from past versions that were stored.</span></span> <span data-ttu-id="e5869-236">Portanto, todos os objetos existentes que têm uma versão (anterior) serializada do objeto precisam ser atualizados para que estejam em conformidade com seu novo esquema.</span><span class="sxs-lookup"><span data-stu-id="e5869-236">Thus, all existing objects that have a serialized (previous) version of the object must be updated to conform to its new schema.</span></span> <span data-ttu-id="e5869-237">Isso não é conceitualmente diferente de um banco de dados relacional, no qual as alterações de esquema às vezes exigem scripts de atualização ou atualizações de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="e5869-237">This is not conceptually different from a relational database, where schema changes sometimes require update scripts or mapping updates.</span></span> <span data-ttu-id="e5869-238">No entanto, o número de entradas que precisa ser modificado costuma ser muito maior na abordagem NoSQL, porque há mais duplicação de dados.</span><span class="sxs-lookup"><span data-stu-id="e5869-238">However, the number of entries that must be modified is often much greater in the NoSQL approach, because there is more duplication of data.</span></span>

<span data-ttu-id="e5869-239">Em bancos de dados NoSQL, é possível armazenar várias versões de objetos, algo para o qual os bancos de dados relacionais de esquema fixo normalmente não dão suporte.</span><span class="sxs-lookup"><span data-stu-id="e5869-239">It's possible in NoSQL databases to store multiple versions of objects, something fixed schema relational databases typically do not support.</span></span> <span data-ttu-id="e5869-240">No entanto, nesse caso, o código do aplicativo precisará levar em conta a existência de versões anteriores de objetos, adicionando mais complexidade.</span><span class="sxs-lookup"><span data-stu-id="e5869-240">However, in this case your application code will need to account for the existence of previous versions of objects, adding additional complexity.</span></span>

<span data-ttu-id="e5869-241">Normalmente, os bancos de dados NoSQL não impõem o [ACID](https://en.wikipedia.org/wiki/ACID), o que significa que eles trazem vantagens de desempenho e escalabilidade comparado aos bancos de dados relacionais.</span><span class="sxs-lookup"><span data-stu-id="e5869-241">NoSQL databases typically do not enforce [ACID](https://en.wikipedia.org/wiki/ACID), which means they have both performance and scalability benefits over relational databases.</span></span> <span data-ttu-id="e5869-242">Eles são adequados para conjuntos de dados extremamente grandes e objetos que não são apropriados para o armazenamento em estruturas de tabela normalizadas.</span><span class="sxs-lookup"><span data-stu-id="e5869-242">They're well-suited to extremely large datasets and objects that are not well-suited to storage in normalized table structures.</span></span> <span data-ttu-id="e5869-243">Não há nenhum motivo pelo qual um único aplicativo não possa aproveitar ambos os bancos de dados relacional e NoSQL, usando cada um deles nos casos em que for mais adequado.</span><span class="sxs-lookup"><span data-stu-id="e5869-243">There is no reason why a single application cannot take advantage of both relational and NoSQL databases, using each where it is best suited.</span></span>

## <a name="azure-documentdb"></a><span data-ttu-id="e5869-244">Azure DocumentDB</span><span class="sxs-lookup"><span data-stu-id="e5869-244">Azure DocumentDB</span></span>

<span data-ttu-id="e5869-245">O Azure DocumentDB é um serviço de banco de dados NoSQL totalmente gerenciado que oferece armazenamento de dados sem esquemas baseado em nuvem.</span><span class="sxs-lookup"><span data-stu-id="e5869-245">Azure DocumentDB is a fully managed NoSQL database service that offers cloud-based schema-free data storage.</span></span> <span data-ttu-id="e5869-246">O DocumentDB foi criado para desempenho rápido e previsível, alta disponibilidade, dimensionamento elástico e distribuição global.</span><span class="sxs-lookup"><span data-stu-id="e5869-246">DocumentDB is built for fast and predictable performance, high availability, elastic scaling, and global distribution.</span></span> <span data-ttu-id="e5869-247">Apesar de ser um banco de dados NoSQL, os desenvolvedores podem usar funcionalidades avançadas e conhecidas de consultas SQL em dados JSON.</span><span class="sxs-lookup"><span data-stu-id="e5869-247">Despite being a NoSQL database, developers can use rich and familiar SQL query capabilities on JSON data.</span></span> <span data-ttu-id="e5869-248">Todos os recursos do DocumentDB são armazenados como documentos JSON.</span><span class="sxs-lookup"><span data-stu-id="e5869-248">All resources in DocumentDB are stored as JSON documents.</span></span> <span data-ttu-id="e5869-249">Os recursos são gerenciados como *itens*, que são documentos que contém metadados, e *feeds*, que são coleções de itens.</span><span class="sxs-lookup"><span data-stu-id="e5869-249">Resources are managed as *items*, which are documents containing metadata, and *feeds*, which are collections of items.</span></span> <span data-ttu-id="e5869-250">A Figura 8-2 mostra a relação entre os diferentes recursos do DocumentDB.</span><span class="sxs-lookup"><span data-stu-id="e5869-250">Figure 8-2 shows the relationship between different DocumentDB resources.</span></span>


![A relação hierárquica entre os recursos do DocumentDB, um banco de dados JSON NoSQL](./media/image8-2.png)

<span data-ttu-id="e5869-252">**Figura 8-2.**</span><span class="sxs-lookup"><span data-stu-id="e5869-252">**Figure 8-2.**</span></span> <span data-ttu-id="e5869-253">Organização de recursos do DocumentDB.</span><span class="sxs-lookup"><span data-stu-id="e5869-253">DocumentDB resource organization.</span></span>

<span data-ttu-id="e5869-254">A linguagem de consulta do DocumentDB é uma interface simples mas avançada para a consulta de documentos JSON.</span><span class="sxs-lookup"><span data-stu-id="e5869-254">The DocumentDB query language is a simple yet powerful interface for querying JSON documents.</span></span> <span data-ttu-id="e5869-255">A linguagem é compatível com um subconjunto da gramática ANSI SQL e adiciona integração profunda de objeto JavaScript, matrizes, construção de objeto e invocação de função.</span><span class="sxs-lookup"><span data-stu-id="e5869-255">The language supports a subset of ANSI SQL grammar and adds deep integration of JavaScript object, arrays, object construction, and function invocation.</span></span>

<span data-ttu-id="e5869-256">**Referências – DocumentDB**</span><span class="sxs-lookup"><span data-stu-id="e5869-256">**References – DocumentDB**</span></span>

-   <span data-ttu-id="e5869-257">Introdução ao DocumentDB\\</span><span class="sxs-lookup"><span data-stu-id="e5869-257">DocumentDB Introduction\\</span></span>
    <https://docs.microsoft.com/azure/documentdb/documentdb-introduction>

## <a name="other-persistence-options"></a><span data-ttu-id="e5869-258">Outras opções de persistência</span><span class="sxs-lookup"><span data-stu-id="e5869-258">Other Persistence Options</span></span>

<span data-ttu-id="e5869-259">Além das opções de armazenamento relacional e NoSQL, os aplicativos ASP.NET Core podem usar o Armazenamento do Azure para armazenar uma variedade de formatos de dados e arquivos de forma escalonável e baseada em nuvem.</span><span class="sxs-lookup"><span data-stu-id="e5869-259">In addition to relational and NoSQL storage options, ASP.NET Core applications can use Azure Storage to store a variety of data formats and files in a cloud-based, scalable fashion.</span></span> <span data-ttu-id="e5869-260">O Armazenamento do Azure é altamente escalonável e, portanto, você pode começar armazenando pequenas quantidades de dados e aumentar até armazenar centenas ou terabytes, caso seu aplicativo precise.</span><span class="sxs-lookup"><span data-stu-id="e5869-260">Azure Storage is massively scalable, so you can start out storing small amounts of data and scale up to storing hundreds or terabytes if your application requires it.</span></span> <span data-ttu-id="e5869-261">O Armazenamento do Azure é compatível com quatro tipos de dados:</span><span class="sxs-lookup"><span data-stu-id="e5869-261">Azure Storage supports four kinds of data:</span></span>

-   <span data-ttu-id="e5869-262">Armazenamento de Blobs para armazenamento de texto não estruturado ou binário, também conhecido como armazenamento de objeto.</span><span class="sxs-lookup"><span data-stu-id="e5869-262">Blob Storage for unstructured text or binary storage, also referred to as object storage.</span></span>

-   <span data-ttu-id="e5869-263">Armazenamento de Tabelas para conjuntos de dados estruturados, acessíveis por meio de chaves de linha.</span><span class="sxs-lookup"><span data-stu-id="e5869-263">Table Storage for structured datasets, accessible via row keys.</span></span>

-   <span data-ttu-id="e5869-264">Armazenamento de Filas para mensagens confiáveis baseadas em fila.</span><span class="sxs-lookup"><span data-stu-id="e5869-264">Queue Storage for reliable queue-based messaging.</span></span>

-   <span data-ttu-id="e5869-265">Armazenamento de Arquivos para acesso a arquivos compartilhados entre aplicativos locais e as máquinas virtuais do Azure.</span><span class="sxs-lookup"><span data-stu-id="e5869-265">File Storage for shared file access between Azure virtual machines and on-premises applications.</span></span>

<span data-ttu-id="e5869-266">**Referências – Armazenamento do Azure**</span><span class="sxs-lookup"><span data-stu-id="e5869-266">**References – Azure Storage**</span></span>

-   <span data-ttu-id="e5869-267">Introdução ao Armazenamento do Azure\\</span><span class="sxs-lookup"><span data-stu-id="e5869-267">Azure Storage Introduction\\</span></span>
    <https://docs.microsoft.com/azure/storage/storage-introduction>

## <a name="caching"></a><span data-ttu-id="e5869-268">Cache</span><span class="sxs-lookup"><span data-stu-id="e5869-268">Caching</span></span>

<span data-ttu-id="e5869-269">Em aplicativos Web, cada solicitação da Web deve ser concluída no menor tempo possível.</span><span class="sxs-lookup"><span data-stu-id="e5869-269">In web applications, each web request should be completed in the shortest time possible.</span></span> <span data-ttu-id="e5869-270">Uma maneira de fazer isso é limitar o número de chamadas externas que o servidor deve fazer para concluir a solicitação.</span><span class="sxs-lookup"><span data-stu-id="e5869-270">One way to achieve this is to limit the number of external calls the server must make to complete the request.</span></span> <span data-ttu-id="e5869-271">O cache envolve o armazenamento de uma cópia dos dados no servidor (ou em outro armazenamento de dados que é consultado com mais facilidade do que a fonte dos dados).</span><span class="sxs-lookup"><span data-stu-id="e5869-271">Caching involves storing a copy of data on the server (or another data store that is more easily queried than the source of the data).</span></span> <span data-ttu-id="e5869-272">Os aplicativos Web, e especialmente aplicativos Web tradicionais não SPA, precisam criar toda a interface do usuário a cada solicitação.</span><span class="sxs-lookup"><span data-stu-id="e5869-272">Web applications, and especially non-SPA traditional web applications, need to build the entire user interface with every request.</span></span> <span data-ttu-id="e5869-273">Isso geralmente envolve fazer muitas das mesmas consultas de banco de dados repetidamente de uma solicitação de usuário para a próxima.</span><span class="sxs-lookup"><span data-stu-id="e5869-273">This frequently involves making many of the same database queries repeatedly from one user request to the next.</span></span> <span data-ttu-id="e5869-274">Na maioria dos casos, esses dados são raramente alterados e, portanto, há pouca justificativa para solicitá-los constantemente do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="e5869-274">In most cases, this data changes rarely, so there is little reason to constantly request it from the database.</span></span> <span data-ttu-id="e5869-275">O ASP.NET Core é compatível com cache de resposta, armazenamento em cache de páginas inteiras e cache de dados, que é compatível com um comportamento de cache mais granular.</span><span class="sxs-lookup"><span data-stu-id="e5869-275">ASP.NET Core supports response caching, for caching entire pages, and data caching, which supports more granular caching behavior.</span></span>

<span data-ttu-id="e5869-276">Ao implementar o cache, é importante ter em mente a separação de interesses.</span><span class="sxs-lookup"><span data-stu-id="e5869-276">When implementing caching, it's important to keep in mind separation of concerns.</span></span> <span data-ttu-id="e5869-277">Evite a implementação da lógica de cache na lógica de acesso a dados ou na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="e5869-277">Avoid implementing caching logic in your data access logic, or in your user interface.</span></span> <span data-ttu-id="e5869-278">Em vez disso, encapsule o cache em suas próprias classes e use a configuração para gerenciar seu comportamento.</span><span class="sxs-lookup"><span data-stu-id="e5869-278">Instead, encapsulate caching in its own classes, and use configuration to manage its behavior.</span></span> <span data-ttu-id="e5869-279">Isso segue os princípios de Aberto/Fechado e Responsabilidade Única e facilitará o gerenciamento de como você usa o cache em seu aplicativo à medida que ele cresce.</span><span class="sxs-lookup"><span data-stu-id="e5869-279">This follows the Open/Closed and Single Responsibility principles, and will make it easier for you to manage how you use caching in your application as it grows.</span></span>

### <a name="aspnet-core-response-caching"></a><span data-ttu-id="e5869-280">Cache de resposta do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e5869-280">ASP.NET Core Response Caching</span></span>

<span data-ttu-id="e5869-281">O ASP.NET Core é compatível com dois níveis de cache de resposta.</span><span class="sxs-lookup"><span data-stu-id="e5869-281">ASP.NET Core supports two levels of response caching.</span></span> <span data-ttu-id="e5869-282">O primeiro nível não armazena nada em cache no servidor, mas adiciona cabeçalhos HTTP que instruem os clientes e servidores proxy a armazenar as respostas em cache.</span><span class="sxs-lookup"><span data-stu-id="e5869-282">The first level does not cache anything on the server, but adds HTTP headers that instruct clients and proxy servers to cache responses.</span></span> <span data-ttu-id="e5869-283">Isso é implementado pela adição do atributo ResponseCache a controladores ou ações individuais:</span><span class="sxs-lookup"><span data-stu-id="e5869-283">This is implemented by adding the ResponseCache attribute to individual controllers or actions:</span></span>

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

<span data-ttu-id="e5869-284">O middleware de cache de resposta armazenará em cache automaticamente as respostas baseadas em um conjunto de condições, que pode ser personalizado.</span><span class="sxs-lookup"><span data-stu-id="e5869-284">The Response Caching Middleware will automatically cache responses based on a set of conditions, which you can customize.</span></span> <span data-ttu-id="e5869-285">Por padrão, apenas respostas 200 (OK) solicitadas por meio de métodos GET ou HEAD são armazenadas em cache.</span><span class="sxs-lookup"><span data-stu-id="e5869-285">By default, only 200 (OK) responses requested via GET or HEAD methods are cached.</span></span> <span data-ttu-id="e5869-286">Além disso, as solicitações devem ter uma resposta com um cabeçalho público Cache-Control: e não pode incluir cabeçalhos de Authorization ou Set-Cookie.</span><span class="sxs-lookup"><span data-stu-id="e5869-286">In addition, requests must have a response with a Cache-Control: public header, and cannot include headers for Authorization or Set-Cookie.</span></span> <span data-ttu-id="e5869-287">Consulte uma [lista completa das condições de cache usadas pelo middleware de cache de resposta](https://docs.microsoft.com/aspnet/core/performance/caching/middleware#conditions-for-caching).</span><span class="sxs-lookup"><span data-stu-id="e5869-287">See a [complete list of the caching conditions used by the response caching middleware](https://docs.microsoft.com/aspnet/core/performance/caching/middleware#conditions-for-caching).</span></span>

### <a name="data-caching"></a><span data-ttu-id="e5869-288">Cache de dados</span><span class="sxs-lookup"><span data-stu-id="e5869-288">Data Caching</span></span>

<span data-ttu-id="e5869-289">Em vez de (ou além de) armazenar em cache as respostas da Web completas, você pode armazenar em cache os resultados de consultas de dados individuais.</span><span class="sxs-lookup"><span data-stu-id="e5869-289">Rather than (or in addition to) caching full web responses, you can cache the results of individual data queries.</span></span> <span data-ttu-id="e5869-290">Para isso, você pode usar o cache em memória no servidor Web ou usar [um cache distribuído](https://docs.microsoft.com/aspnet/core/performance/caching/distributed).</span><span class="sxs-lookup"><span data-stu-id="e5869-290">For this, you can use in memory caching on the web server, or use [a distributed cache](https://docs.microsoft.com/aspnet/core/performance/caching/distributed).</span></span> <span data-ttu-id="e5869-291">Esta seção demonstrará como implementar o cache em memória.</span><span class="sxs-lookup"><span data-stu-id="e5869-291">This section will demonstrate how to implement in memory caching.</span></span>

<span data-ttu-id="e5869-292">Adicione suporte para o cache em memória (ou distribuído) em ConfigureServices:</span><span class="sxs-lookup"><span data-stu-id="e5869-292">You add support for memory (or distributed) caching in ConfigureServices:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

<span data-ttu-id="e5869-293">Lembre-se de adicionar também o pacote NuGet Microsoft.Extensions.Caching.Memory.</span><span class="sxs-lookup"><span data-stu-id="e5869-293">Be sure to add the Microsoft.Extensions.Caching.Memory NuGet package as well.</span></span>

<span data-ttu-id="e5869-294">Depois de adicionar o serviço, solicite IMemoryCache por meio da injeção de dependência sempre que precisar acessar o cache.</span><span class="sxs-lookup"><span data-stu-id="e5869-294">Once you've added the service, you request IMemoryCache via dependency injection wherever you need to access the cache.</span></span> <span data-ttu-id="e5869-295">Neste exemplo, o CachedCatalogService usa o padrão de design Proxy (ou Decorador), fornecendo uma implementação alternativa de ICatalogService que controla o acesso à implementação de CatalogService subjacente ou que adiciona um comportamento a ela.</span><span class="sxs-lookup"><span data-stu-id="e5869-295">In this example, the CachedCatalogService is using the Proxy (or Decorator) design pattern, by providing an alternative implementation of ICatalogService that controls access to (or adds behavior to) the underlying CatalogService implementation.</span></span>

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

<span data-ttu-id="e5869-296">Para configurar o aplicativo para usar a versão armazenada em cache do serviço, mas ainda permitir que o serviço obtenha a instância de CatalogService necessária em seu construtor, adicione o seguinte em ConfigureServices:</span><span class="sxs-lookup"><span data-stu-id="e5869-296">To configure the application to use the cached version of the service, but still allow the service to get the instance of CatalogService it needs in its constructor, you would add the following in ConfigureServices:</span></span>

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

<span data-ttu-id="e5869-297">Com isso em vigor, as chamadas de banco de dados para buscar os dados de catálogo serão feitas apenas uma vez por minuto, em vez de a cada solicitação.</span><span class="sxs-lookup"><span data-stu-id="e5869-297">With this in place, the database calls to fetch the catalog data will only be made once per minute, rather than on every request.</span></span> <span data-ttu-id="e5869-298">Dependendo do tráfego para o site, isso pode ter um impacto muito significativo no número de consultas feitas para o banco de dados e no tempo médio de carregamento de página da home page que atualmente depende de todas as três consultas expostas por esse serviço.</span><span class="sxs-lookup"><span data-stu-id="e5869-298">Depending on the traffic to the site, this can have a very significant impact on the number of queries made to the database, and the average page load time for the home page that currently depends on all three of the queries exposed by this service.</span></span>

<span data-ttu-id="e5869-299">Um problema que ocorre quando o cache é implementado são *dados obsoletos* – ou seja, dados que foram alterados na fonte, mas cuja versão desatualizada permanece no cache.</span><span class="sxs-lookup"><span data-stu-id="e5869-299">An issue that arises when caching is implemented is *stale data* – that is, data that has changed at the source but an out of date version remains in the cache.</span></span> <span data-ttu-id="e5869-300">Uma maneira simples de atenuar esse problema é usar pequenas durações de cache, pois há benefícios adicionais limitados em estender a duração de armazenamento em cache dos dados para um aplicativo ocupado.</span><span class="sxs-lookup"><span data-stu-id="e5869-300">A simple way to mitigate this issue is to use small cache durations, since for a busy application there is limited additional benefit to extending the length data is cached.</span></span> <span data-ttu-id="e5869-301">Por exemplo, considere uma página que faz uma consulta de banco de dados individual e é solicitada 10 vezes por segundo.</span><span class="sxs-lookup"><span data-stu-id="e5869-301">For example, consider a page that makes a single database query, and is requested 10 times per second.</span></span> <span data-ttu-id="e5869-302">Se essa página for armazenada em cache por um minuto, isso resultará no número de consultas de banco de dados feitas por minuto para reduzir de 600 para 1, uma redução de 99,8%.</span><span class="sxs-lookup"><span data-stu-id="e5869-302">If this page is cached for one minute, it will result in the number of database queries made per minute to drop from 600 to 1, a reduction of 99.8%.</span></span> <span data-ttu-id="e5869-303">Se, em vez disso, a duração do cache foi feita em uma hora, a redução geral é de 99,997%, mas agora, a probabilidade e a idade potencial dos dados obsoletos são aumentadas consideravelmente.</span><span class="sxs-lookup"><span data-stu-id="e5869-303">If instead the cache duration were made one hour, the overall reduction would be 99.997%, but now the likelihood and potential age of stale data are both increased dramatically.</span></span>

<span data-ttu-id="e5869-304">Outra abordagem é remover as entradas de cache de forma proativa quando os dados que elas contêm são atualizados.</span><span class="sxs-lookup"><span data-stu-id="e5869-304">Another approach is to proactively remove cache entries when the data they contain is updated.</span></span> <span data-ttu-id="e5869-305">As entradas individuais podem ser removidas se sua chave é conhecida:</span><span class="sxs-lookup"><span data-stu-id="e5869-305">Any individual entry can be removed if its key is known:</span></span>

```csharp
_cache.Remove(cacheKey);
```

<span data-ttu-id="e5869-306">Se o aplicativo expõe a funcionalidade para atualizar as entradas que ele armazena em cache, você pode remover as entradas de cache correspondentes no código que executa as atualizações.</span><span class="sxs-lookup"><span data-stu-id="e5869-306">If your application exposes functionality for updating entries that it caches, you can remove the corresponding cache entries in your code that performs the updates.</span></span> <span data-ttu-id="e5869-307">Às vezes, pode haver muitas entradas diferentes que dependem de determinado conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="e5869-307">Sometimes there may be many different entries that depend on a particular set of data.</span></span> <span data-ttu-id="e5869-308">Nesse caso, pode ser útil criar dependências entre as entradas de cache, usando um CancellationChangeToken.</span><span class="sxs-lookup"><span data-stu-id="e5869-308">In that case, it can be useful to create dependencies between cache entries, by using a CancellationChangeToken.</span></span> <span data-ttu-id="e5869-309">Com um CancellationChangeToken, você pode expirar várias entradas de cache de uma vez com o cancelamento do token.</span><span class="sxs-lookup"><span data-stu-id="e5869-309">With a CancellationChangeToken, you can expire multiple cache entries at once by cancelling the token.</span></span>

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
<span data-ttu-id="e5869-310">[Anterior](develop-asp-net-core-mvc-apps.md)
[Próximo](test-asp-net-core-mvc-apps.md)</span><span class="sxs-lookup"><span data-stu-id="e5869-310">[Previous](develop-asp-net-core-mvc-apps.md)
[Next](test-asp-net-core-mvc-apps.md)</span></span>
