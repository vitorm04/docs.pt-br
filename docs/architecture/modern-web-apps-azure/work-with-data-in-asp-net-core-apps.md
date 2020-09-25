---
title: Trabalhar com os dados em aplicativos ASP.NET Core
description: Arquitetar aplicativos Web modernos com o ASP.NET Core e o Azure | Trabalhando com os dados em aplicativos ASP.NET Core
author: ardalis
ms.author: wiwagn
ms.date: 08/12/2020
no-loc:
- Blazor
- WebAssembly
ms.openlocfilehash: 4668922de8f0efc775acf6e505d56143b7ead8e7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169057"
---
# <a name="working-with-data-in-aspnet-core-apps"></a><span data-ttu-id="51f1c-103">Trabalhando com os dados em aplicativos ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="51f1c-103">Working with Data in ASP.NET Core Apps</span></span>

> <span data-ttu-id="51f1c-104">"Os dados são uma coisa preciosa e vão durar mais do que os próprios sistemas."</span><span class="sxs-lookup"><span data-stu-id="51f1c-104">"Data is a precious thing and will last longer than the systems themselves."</span></span>
>
> <span data-ttu-id="51f1c-105">Tim Berners-Lee</span><span class="sxs-lookup"><span data-stu-id="51f1c-105">Tim Berners-Lee</span></span>

<span data-ttu-id="51f1c-106">O acesso a dados é uma parte importante de praticamente qualquer aplicativo de software.</span><span class="sxs-lookup"><span data-stu-id="51f1c-106">Data access is an important part of almost any software application.</span></span> <span data-ttu-id="51f1c-107">O ASP.NET Core é compatível com uma variedade de opções de acesso a dados, incluindo o Entity Framework Core (e também o Entity Framework 6) e pode trabalhar com qualquer estrutura de acesso a dados do .NET.</span><span class="sxs-lookup"><span data-stu-id="51f1c-107">ASP.NET Core supports a variety of data access options, including Entity Framework Core (and Entity Framework 6 as well), and can work with any .NET data access framework.</span></span> <span data-ttu-id="51f1c-108">A escolha de qual estrutura de acesso a dados usar depende das necessidades do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="51f1c-108">The choice of which data access framework to use depends on the application's needs.</span></span> <span data-ttu-id="51f1c-109">A abstração dessas opções dos projetos de ApplicationCore e de interface do usuário e o encapsulamento dos detalhes de implementação na Infraestrutura ajudam a produzir um software testável e com acoplamento flexível.</span><span class="sxs-lookup"><span data-stu-id="51f1c-109">Abstracting these choices from the ApplicationCore and UI projects, and encapsulating implementation details in Infrastructure, helps to produce loosely coupled, testable software.</span></span>

## <a name="entity-framework-core-for-relational-databases"></a><span data-ttu-id="51f1c-110">Entity Framework Core (para bancos de dados relacionais)</span><span class="sxs-lookup"><span data-stu-id="51f1c-110">Entity Framework Core (for relational databases)</span></span>

<span data-ttu-id="51f1c-111">Caso você esteja escrevendo um novo aplicativo ASP.NET Core que precisa trabalhar com os dados relacionais, o EF Core (Entity Framework Core) é a maneira recomendada para que seu aplicativo acesse os dados.</span><span class="sxs-lookup"><span data-stu-id="51f1c-111">If you're writing a new ASP.NET Core application that needs to work with relational data, then Entity Framework Core (EF Core) is the recommended way for your application to access its data.</span></span> <span data-ttu-id="51f1c-112">O EF Core é um O/RM (mapeador relacional de objeto) que permite aos desenvolvedores do .NET persistir objetos bidirecionalmente em uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="51f1c-112">EF Core is an object-relational mapper (O/RM) that enables .NET developers to persist objects to and from a data source.</span></span> <span data-ttu-id="51f1c-113">Elimina a necessidade da maioria do código de acesso a dados que os desenvolvedores geralmente precisam escrever.</span><span class="sxs-lookup"><span data-stu-id="51f1c-113">It eliminates the need for most of the data access code developers would typically need to write.</span></span> <span data-ttu-id="51f1c-114">Assim como o ASP.NET Core, o EF Core foi totalmente reformulado para dar suporte a aplicativos modulares multiplataforma.</span><span class="sxs-lookup"><span data-stu-id="51f1c-114">Like ASP.NET Core, EF Core has been rewritten from the ground up to support modular cross-platform applications.</span></span> <span data-ttu-id="51f1c-115">Você adiciona-o ao aplicativo como um pacote NuGet, configura-o em Startup e solicita-o por meio da injeção de dependência sempre que precisar dela.</span><span class="sxs-lookup"><span data-stu-id="51f1c-115">You add it to your application as a NuGet package, configure it in Startup, and request it through dependency injection wherever you need it.</span></span>

<span data-ttu-id="51f1c-116">Para usar o EF Core com um banco de dados do SQL Server, execute o seguinte comando da CLI do dotnet:</span><span class="sxs-lookup"><span data-stu-id="51f1c-116">To use EF Core with a SQL Server database, run the following dotnet CLI command:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
```

<span data-ttu-id="51f1c-117">Para adicionar suporte para uma fonte de dados InMemory para teste:</span><span class="sxs-lookup"><span data-stu-id="51f1c-117">To add support for an InMemory data source, for testing:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore.InMemory
```

### <a name="the-dbcontext"></a><span data-ttu-id="51f1c-118">O DbContext</span><span class="sxs-lookup"><span data-stu-id="51f1c-118">The DbContext</span></span>

<span data-ttu-id="51f1c-119">Para trabalhar com o EF Core, você precisa de uma subclasse de <xref:Microsoft.EntityFrameworkCore.DbContext>.</span><span class="sxs-lookup"><span data-stu-id="51f1c-119">To work with EF Core, you need a subclass of <xref:Microsoft.EntityFrameworkCore.DbContext>.</span></span> <span data-ttu-id="51f1c-120">Essa classe contém propriedades que representam coleções de entidades com as quais seu aplicativo trabalhará.</span><span class="sxs-lookup"><span data-stu-id="51f1c-120">This class holds properties representing collections of the entities your application will work with.</span></span> <span data-ttu-id="51f1c-121">A amostra de eShopOnWeb inclui um CatalogContext com coleções de itens, marcas e tipos:</span><span class="sxs-lookup"><span data-stu-id="51f1c-121">The eShopOnWeb sample includes a CatalogContext with collections for items, brands, and types:</span></span>

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

<span data-ttu-id="51f1c-122">O DbContext deve ter um construtor que aceite DbContextOptions e passa esse argumento para o construtor DbContext base.</span><span class="sxs-lookup"><span data-stu-id="51f1c-122">Your DbContext must have a constructor that accepts DbContextOptions and pass this argument to the base DbContext constructor.</span></span> <span data-ttu-id="51f1c-123">Se você tiver apenas um DbContext em seu aplicativo, poderá passar uma instância de DbContextOptions, mas se você tiver mais de um, deverá usar o tipo DbContextOptions genérico \<T> , passando o tipo DbContext como o parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="51f1c-123">If you have only one DbContext in your application, you can pass an instance of DbContextOptions, but if you have more than one you must use the generic DbContextOptions\<T> type, passing in your DbContext type as the generic parameter.</span></span>

### <a name="configuring-ef-core"></a><span data-ttu-id="51f1c-124">Configurando o EF Core</span><span class="sxs-lookup"><span data-stu-id="51f1c-124">Configuring EF Core</span></span>

<span data-ttu-id="51f1c-125">No aplicativo ASP.NET Core, normalmente, você configurará o EF Core no método ConfigureServices.</span><span class="sxs-lookup"><span data-stu-id="51f1c-125">In your ASP.NET Core application, you'll typically configure EF Core in your ConfigureServices method.</span></span> <span data-ttu-id="51f1c-126">O EF Core usa um DbContextOptionsBuilder, que é compatível com vários métodos de extensão úteis para simplificar sua configuração.</span><span class="sxs-lookup"><span data-stu-id="51f1c-126">EF Core uses a DbContextOptionsBuilder, which supports several helpful extension methods to streamline its configuration.</span></span> <span data-ttu-id="51f1c-127">Para configurar o CatalogContext para que ele use um banco de dados do SQL Server com uma cadeia de conexão definida em Configuration, adicione o seguinte código ao ConfigureServices:</span><span class="sxs-lookup"><span data-stu-id="51f1c-127">To configure CatalogContext to use a SQL Server database with a connection string defined in Configuration, you would add the following code to ConfigureServices:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

<span data-ttu-id="51f1c-128">Para usar o banco de dados em memória:</span><span class="sxs-lookup"><span data-stu-id="51f1c-128">To use the in-memory database:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

<span data-ttu-id="51f1c-129">Depois de instalar o EF Core, criar um tipo filho do DbContext e configurá-lo em ConfigureServices, você estará pronto para usar o EF Core.</span><span class="sxs-lookup"><span data-stu-id="51f1c-129">Once you have installed EF Core, created a DbContext child type, and configured it in ConfigureServices, you are ready to use EF Core.</span></span> <span data-ttu-id="51f1c-130">Você pode solicitar uma instância do tipo DbContext em qualquer serviço que precisar dela e começar a trabalhar com as entidades persistentes usando o LINQ como se elas apenas estivessem em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="51f1c-130">You can request an instance of your DbContext type in any service that needs it, and start working with your persisted entities using LINQ as if they were simply in a collection.</span></span> <span data-ttu-id="51f1c-131">O EF Core faz o trabalho de converter as expressões LINQ em consultas SQL para armazenar e recuperar os dados.</span><span class="sxs-lookup"><span data-stu-id="51f1c-131">EF Core does the work of translating your LINQ expressions into SQL queries to store and retrieve your data.</span></span>

<span data-ttu-id="51f1c-132">Você pode ver as consultas executadas pelo EF Core configurando um agente e garantindo que seu nível está definido com, pelo menos, Informações, conforme mostrado na Figura 8-1.</span><span class="sxs-lookup"><span data-stu-id="51f1c-132">You can see the queries EF Core is executing by configuring a logger and ensuring its level is set to at least Information, as shown in Figure 8-1.</span></span>

![Registrando EF Core consultas no console](./media/image8-1.png)

<span data-ttu-id="51f1c-134">**Figura 8-1**.</span><span class="sxs-lookup"><span data-stu-id="51f1c-134">**Figure 8-1**.</span></span> <span data-ttu-id="51f1c-135">Registrando EF Core consultas no console</span><span class="sxs-lookup"><span data-stu-id="51f1c-135">Logging EF Core queries to the console</span></span>

### <a name="fetching-and-storing-data"></a><span data-ttu-id="51f1c-136">Buscando e armazenando dados</span><span class="sxs-lookup"><span data-stu-id="51f1c-136">Fetching and storing Data</span></span>

<span data-ttu-id="51f1c-137">Para recuperar dados do EF Core, acesse a propriedade apropriada e use o LINQ para filtrar o resultado.</span><span class="sxs-lookup"><span data-stu-id="51f1c-137">To retrieve data from EF Core, you access the appropriate property and use LINQ to filter the result.</span></span> <span data-ttu-id="51f1c-138">Também use o LINQ para executar a projeção, transformando o resultado de um tipo para outro.</span><span class="sxs-lookup"><span data-stu-id="51f1c-138">You can also use LINQ to perform projection, transforming the result from one type to another.</span></span> <span data-ttu-id="51f1c-139">O seguinte exemplo recupera CatalogBrands, ordenadas por nome, filtradas por sua propriedade Enabled e projetadas em um tipo SelectListItem:</span><span class="sxs-lookup"><span data-stu-id="51f1c-139">The following example would retrieve CatalogBrands, ordered by name, filtered by their Enabled property, and projected onto a SelectListItem type:</span></span>

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

<span data-ttu-id="51f1c-140">É importante, no exemplo acima, adicionar a chamada a ToListAsync para executar a consulta imediatamente.</span><span class="sxs-lookup"><span data-stu-id="51f1c-140">It's important in the above example to add the call to ToListAsync in order to execute the query immediately.</span></span> <span data-ttu-id="51f1c-141">Caso contrário, a instrução atribuirá um IQueryable\<SelectListItem> a brandItems, que não será executado até que seja enumerado.</span><span class="sxs-lookup"><span data-stu-id="51f1c-141">Otherwise, the statement will assign an IQueryable\<SelectListItem> to brandItems, which will not be executed until it is enumerated.</span></span> <span data-ttu-id="51f1c-142">Há vantagens e desvantagens em retornar resultados IQueryable de métodos.</span><span class="sxs-lookup"><span data-stu-id="51f1c-142">There are pros and cons to returning IQueryable results from methods.</span></span> <span data-ttu-id="51f1c-143">Ele permite que a consulta construída pelo EF Core seja modificada ainda mais, mas também pode resultar em erros que ocorrem apenas em runtime, caso as operações sejam adicionadas à consulta que o EF Core não pode converter.</span><span class="sxs-lookup"><span data-stu-id="51f1c-143">It allows the query EF Core will construct to be further modified, but can also result in errors that only occur at runtime, if operations are added to the query that EF Core cannot translate.</span></span> <span data-ttu-id="51f1c-144">Em geral, é mais seguro passar todos os filtros para o método que executa o acesso a dados e retornar uma coleção em memória (por exemplo, List\<T>) como o resultado.</span><span class="sxs-lookup"><span data-stu-id="51f1c-144">It's generally safer to pass any filters into the method performing the data access, and return back an in-memory collection (for example, List\<T>) as the result.</span></span>

<span data-ttu-id="51f1c-145">O EF Core controla as alterações nas entidades que ele busca da persistência.</span><span class="sxs-lookup"><span data-stu-id="51f1c-145">EF Core tracks changes on entities it fetches from persistence.</span></span> <span data-ttu-id="51f1c-146">Para salvar as alterações em uma entidade controlada, basta chamar o método SaveChanges no DbContext, verificando se ela é a mesma instância de DbContext que foi usada para buscar a entidade.</span><span class="sxs-lookup"><span data-stu-id="51f1c-146">To save changes to a tracked entity, you just call the SaveChanges method on the DbContext, making sure it's the same DbContext instance that was used to fetch the entity.</span></span> <span data-ttu-id="51f1c-147">A adição e remoção de entidades é feita diretamente na propriedade DbSet apropriada, novamente com uma chamada a SaveChanges para executar os comandos de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="51f1c-147">Adding and removing entities is directly done on the appropriate DbSet property, again with a call to SaveChanges to execute the database commands.</span></span> <span data-ttu-id="51f1c-148">O exemplo a seguir demonstra como adicionar, atualizar e remover entidades da persistência.</span><span class="sxs-lookup"><span data-stu-id="51f1c-148">The following example demonstrates adding, updating, and removing entities from persistence.</span></span>

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

<span data-ttu-id="51f1c-149">O EF Core é compatível com métodos síncronos e assíncronos para busca e salvamento.</span><span class="sxs-lookup"><span data-stu-id="51f1c-149">EF Core supports both synchronous and async methods for fetching and saving.</span></span> <span data-ttu-id="51f1c-150">Em aplicativos Web, é recomendável usar o padrão async/await com os métodos async, de modo que os threads do servidor Web não sejam bloqueados enquanto aguardam a conclusão das operações de acesso a dados.</span><span class="sxs-lookup"><span data-stu-id="51f1c-150">In web applications, it's recommended to use the async/await pattern with the async methods, so that web server threads are not blocked while waiting for data access operations to complete.</span></span>

### <a name="fetching-related-data"></a><span data-ttu-id="51f1c-151">Buscando dados relacionados</span><span class="sxs-lookup"><span data-stu-id="51f1c-151">Fetching related data</span></span>

<span data-ttu-id="51f1c-152">Quando o EF Core recupera entidades, ele popula todas as propriedades armazenadas diretamente nessa entidade no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="51f1c-152">When EF Core retrieves entities, it populates all of the properties that are stored directly with that entity in the database.</span></span> <span data-ttu-id="51f1c-153">Propriedades de navegação, como listas de entidades relacionadas, não são populadas e podem ter seu valor definido como nulo.</span><span class="sxs-lookup"><span data-stu-id="51f1c-153">Navigation properties, such as lists of related entities, are not populated and may have their value set to null.</span></span> <span data-ttu-id="51f1c-154">Isso garante que o EF Core não busca mais dados do que necessário, o que é especialmente importante para aplicativos Web, que devem processar solicitações e retornar respostas de uma maneira eficiente e com agilidade.</span><span class="sxs-lookup"><span data-stu-id="51f1c-154">This ensures EF Core is not fetching more data than is needed, which is especially important for web applications, which must quickly process requests and return responses in an efficient manner.</span></span> <span data-ttu-id="51f1c-155">Para incluir relações com uma entidade usando o _carregamento adiantado_, especifique a propriedade usando o método de extensão Include na consulta, conforme mostrado:</span><span class="sxs-lookup"><span data-stu-id="51f1c-155">To include relationships with an entity using _eager loading_, you specify the property using the Include extension method on the query, as shown:</span></span>

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

<span data-ttu-id="51f1c-156">Você pode incluir várias relações, e também pode incluir subrelaçãos usando ThenInclude.</span><span class="sxs-lookup"><span data-stu-id="51f1c-156">You can include multiple relationships, and you can also include subrelationships using ThenInclude.</span></span> <span data-ttu-id="51f1c-157">O EF Core executará uma única consulta para recuperar o conjunto resultante de entidades.</span><span class="sxs-lookup"><span data-stu-id="51f1c-157">EF Core will execute a single query to retrieve the resulting set of entities.</span></span> <span data-ttu-id="51f1c-158">Como alternativa, você pode incluir propriedades de navegação de propriedades de navegação passando uma cadeia de caracteres separada por '.' para o método de extensão `.Include()`, da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="51f1c-158">Alternately you can include navigation properties of navigation properties by passing a '.'-separated string to the `.Include()` extension method, like so:</span></span>

```csharp
    .Include("Items.Products")
```

<span data-ttu-id="51f1c-159">Além de encapsular a lógica de filtragem, uma especificação pode especificar a forma dos dados a serem retornados, incluindo quais propriedades devem ser populadas.</span><span class="sxs-lookup"><span data-stu-id="51f1c-159">In addition to encapsulating filtering logic, a specification can specify the shape of the data to be returned, including which properties to populate.</span></span> <span data-ttu-id="51f1c-160">O exemplo eShopOnWeb inclui várias especificações que demonstram o encapsulamento das informações de carregamento adiantado dentro da especificação.</span><span class="sxs-lookup"><span data-stu-id="51f1c-160">The eShopOnWeb sample includes several specifications that demonstrate encapsulating eager loading information within the specification.</span></span> <span data-ttu-id="51f1c-161">Veja aqui como a especificação é usada como parte de uma consulta:</span><span class="sxs-lookup"><span data-stu-id="51f1c-161">You can see how the specification is used as part of a query here:</span></span>

```csharp
// Includes all expression-based includes
query = specification.Includes.Aggregate(query,
            (current, include) => current.Include(include));

// Include any string-based include statements
query = specification.IncludeStrings.Aggregate(query,
            (current, include) => current.Include(include));
```

<span data-ttu-id="51f1c-162">Outra opção para carregar dados relacionados é usar o _carregamento explícito_.</span><span class="sxs-lookup"><span data-stu-id="51f1c-162">Another option for loading related data is to use _explicit loading_.</span></span> <span data-ttu-id="51f1c-163">O carregamento explícito permite carregar dados adicionais em uma entidade que já foi recuperada.</span><span class="sxs-lookup"><span data-stu-id="51f1c-163">Explicit loading allows you to load additional data into an entity that has already been retrieved.</span></span> <span data-ttu-id="51f1c-164">Como isso envolve uma solicitação separada para o banco de dados, isso não é recomendado para aplicativos Web, que devem minimizar o número de viagens de ida e volta de banco de dados feitas por solicitação.</span><span class="sxs-lookup"><span data-stu-id="51f1c-164">Since this involves a separate request to the database, it's not recommended for web applications, which should minimize the number of database round trips made per request.</span></span>

<span data-ttu-id="51f1c-165">O _carregamento lento_ é um recurso que carrega automaticamente os dados relacionados conforme eles são referenciados pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="51f1c-165">_Lazy loading_ is a feature that automatically loads related data as it is referenced by the application.</span></span> <span data-ttu-id="51f1c-166">Foi adicionado o suporte para carregamento lento na versão 2.1 do EF Core.</span><span class="sxs-lookup"><span data-stu-id="51f1c-166">EF Core has added support for lazy loading in version 2.1.</span></span> <span data-ttu-id="51f1c-167">O carregamento lento não está habilitado por padrão e requer a instalação do `Microsoft.EntityFrameworkCore.Proxies`.</span><span class="sxs-lookup"><span data-stu-id="51f1c-167">Lazy loading is not enabled by default and requires installing the `Microsoft.EntityFrameworkCore.Proxies`.</span></span> <span data-ttu-id="51f1c-168">Assim como acontece com o carregamento explícito, o carregamento lento normalmente deve estar desabilitado para aplicativos Web, pois seu uso resulta em mais consultas de banco de dados em cada solicitação da Web.</span><span class="sxs-lookup"><span data-stu-id="51f1c-168">As with explicit loading, lazy loading should typically be disabled for web applications, since its use will result in additional database queries being made within each web request.</span></span> <span data-ttu-id="51f1c-169">Infelizmente, a sobrecarga causada pelo carregamento lento muitas vezes passa despercebida no momento do desenvolvimento, quando a latência é pequena e, geralmente, os conjuntos de dados usados para teste também são pequenos.</span><span class="sxs-lookup"><span data-stu-id="51f1c-169">Unfortunately, the overhead incurred by lazy loading often goes unnoticed at development time, when latency is small and often the data sets used for testing are small.</span></span> <span data-ttu-id="51f1c-170">No entanto, na produção, com mais usuários, mais dados e mais latência, as solicitações de banco de dados adicionais podem resultar em baixo desempenho dos aplicativos Web que usam o carregamento lento de forma intensiva.</span><span class="sxs-lookup"><span data-stu-id="51f1c-170">However, in production, with more users, more data, and more latency, the additional database requests can often result in poor performance for web applications that make heavy use of lazy loading.</span></span>

<span data-ttu-id="51f1c-171">[Avoid Lazy Loading Entities in Web Applications](https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications) (Evitar entidades de carregamento lento em aplicativos Web)</span><span class="sxs-lookup"><span data-stu-id="51f1c-171">[Avoid Lazy Loading Entities in Web Applications](https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications)</span></span>

### <a name="encapsulating-data"></a><span data-ttu-id="51f1c-172">Encapsulando dados</span><span class="sxs-lookup"><span data-stu-id="51f1c-172">Encapsulating data</span></span>

<span data-ttu-id="51f1c-173">O EF Core é compatível com vários recursos que permitem que o modelo encapsule seu próprio estado corretamente.</span><span class="sxs-lookup"><span data-stu-id="51f1c-173">EF Core supports several features that allow your model to properly encapsulate its state.</span></span> <span data-ttu-id="51f1c-174">Um problema comum nos modelos de domínio é que eles expõem propriedades de navegação de coleção como tipos de lista publicamente acessíveis.</span><span class="sxs-lookup"><span data-stu-id="51f1c-174">A common problem in domain models is that they expose collection navigation properties as publicly accessible list types.</span></span> <span data-ttu-id="51f1c-175">Isso permite que qualquer colaborador manipule o conteúdo desses tipos de coleção, podendo ignorar regras de negócios importantes relacionadas à coleção e deixar o objeto em um estado inválido.</span><span class="sxs-lookup"><span data-stu-id="51f1c-175">This allows any collaborator to manipulate the contents of these collection types, which may bypass important business rules related to the collection, possibly leaving the object in an invalid state.</span></span> <span data-ttu-id="51f1c-176">A solução para isso é expor o acesso somente leitura às coleções relacionadas e fornecer métodos explicitamente definindo de que forma os clientes podem manipulá-las, como neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="51f1c-176">The solution to this is to expose read-only access to related collections, and explicitly provide methods defining ways in which clients can manipulate them, as in this example:</span></span>

```csharp
public class Basket : BaseEntity
{
    public string BuyerId { get; set; }
    private readonly List<BasketItem> _items = new List<BasketItem>();
    public IReadOnlyCollection<BasketItem> Items => _items.AsReadOnly();

    public void AddItem(int catalogItemId, decimal unitPrice, int quantity = 1)
    {
        if (!Items.Any(i => i.CatalogItemId == catalogItemId))
        {
            _items.Add(new BasketItem()
            {
                CatalogItemId = catalogItemId,
                Quantity = quantity,
                UnitPrice = unitPrice
            });
            return;
        }
        var existingItem = Items.FirstOrDefault(i => i.CatalogItemId == catalogItemId);
        existingItem.Quantity += quantity;
    }
}
```

<span data-ttu-id="51f1c-177">Esse tipo de entidade não expõe uma `List` propriedade ou pública `ICollection` , mas, em vez disso, expõe um `IReadOnlyCollection` tipo que encapsula o tipo de lista subjacente.</span><span class="sxs-lookup"><span data-stu-id="51f1c-177">This entity type doesn't expose a public `List` or `ICollection` property, but instead exposes an `IReadOnlyCollection` type that wraps the underlying List type.</span></span> <span data-ttu-id="51f1c-178">Ao usar esse padrão, é possível indicar ao Entity Framework Core que ele deve usar o campo de suporte da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="51f1c-178">When using this pattern, you can indicate to Entity Framework Core to use the backing field like so:</span></span>

```csharp
private void ConfigureBasket(EntityTypeBuilder<Basket> builder)
{
    var navigation = builder.Metadata.FindNavigation(nameof(Basket.Items));

    navigation.SetPropertyAccessMode(PropertyAccessMode.Field);
}
```

<span data-ttu-id="51f1c-179">Outra maneira de melhorar seu modelo de domínio é usar objetos de valor para os tipos que não têm identidade e são diferenciados apenas por suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="51f1c-179">Another way in which you can improve your domain model is through the use of value objects for types that lack identity and are only distinguished by their properties.</span></span> <span data-ttu-id="51f1c-180">O uso desses tipos como propriedades das entidades pode ajudar a manter a lógica específica do objeto de valor ao qual pertence e pode evitar a duplicação de lógica entre várias entidades que usam o mesmo conceito.</span><span class="sxs-lookup"><span data-stu-id="51f1c-180">Using such types as properties of your entities can help keep logic specific to the value object where it belongs, and can avoid duplicate logic between multiple entities that use the same concept.</span></span> <span data-ttu-id="51f1c-181">No Entity Framework Core, você pode manter os objetos de valor na mesma tabela que a entidade proprietária configurando o tipo como uma entidade própria, da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="51f1c-181">In Entity Framework Core, you can persist value objects in the same table as their owning entity by configuring the type as an owned entity, like so:</span></span>

```csharp
private void ConfigureOrder(EntityTypeBuilder<Order> builder)
{
    builder.OwnsOne(o => o.ShipToAddress);
}
```

<span data-ttu-id="51f1c-182">Neste exemplo, a propriedade `ShipToAddress` é do tipo `Address`.</span><span class="sxs-lookup"><span data-stu-id="51f1c-182">In this example, the `ShipToAddress` property is of type `Address`.</span></span> <span data-ttu-id="51f1c-183">`Address` é um objeto de valor com várias propriedades, como `Street` e `City`.</span><span class="sxs-lookup"><span data-stu-id="51f1c-183">`Address` is a value object with several properties such as `Street` and `City`.</span></span> <span data-ttu-id="51f1c-184">O EF Core mapeia o objeto `Order` à tabela dele com uma coluna por propriedade `Address`, prefixando cada nome de coluna com o nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="51f1c-184">EF Core maps the `Order` object to its table with one column per `Address` property, prefixing each column name with the name of the property.</span></span> <span data-ttu-id="51f1c-185">Neste exemplo, a tabela `Order` incluiria colunas, como `ShipToAddress_Street` e `ShipToAddress_City`.</span><span class="sxs-lookup"><span data-stu-id="51f1c-185">In this example, the `Order` table would include columns such as `ShipToAddress_Street` and `ShipToAddress_City`.</span></span> <span data-ttu-id="51f1c-186">Também é possível armazenar tipos de propriedade em tabelas separadas, se desejado.</span><span class="sxs-lookup"><span data-stu-id="51f1c-186">It's also possible to store owned types in separate tables, if desired.</span></span>

<span data-ttu-id="51f1c-187">Saiba mais sobre o [suporte a entidades pertencentes no EF Core](/ef/core/modeling/owned-entities).</span><span class="sxs-lookup"><span data-stu-id="51f1c-187">Learn more about owned [entity support in EF Core](/ef/core/modeling/owned-entities).</span></span>

### <a name="resilient-connections"></a><span data-ttu-id="51f1c-188">Conexões resilientes</span><span class="sxs-lookup"><span data-stu-id="51f1c-188">Resilient connections</span></span>

<span data-ttu-id="51f1c-189">Recursos externos, como bancos de dados SQL, ocasionalmente, podem não estar disponíveis.</span><span class="sxs-lookup"><span data-stu-id="51f1c-189">External resources like SQL databases may occasionally be unavailable.</span></span> <span data-ttu-id="51f1c-190">Em caso de indisponibilidade temporária, os aplicativos podem usar a lógica de repetição para evitar gerar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="51f1c-190">In cases of temporary unavailability, applications can use retry logic to avoid raising an exception.</span></span> <span data-ttu-id="51f1c-191">Em geral, essa técnica é conhecida como _resiliência de conexão_.</span><span class="sxs-lookup"><span data-stu-id="51f1c-191">This technique is commonly referred to as _connection resiliency_.</span></span> <span data-ttu-id="51f1c-192">Implemente sua [própria técnica de repetição com retirada exponencial](/azure/architecture/patterns/retry) pela tentativa de repetir com um tempo de espera que aumenta exponencialmente, até atingir um número máximo de repetições.</span><span class="sxs-lookup"><span data-stu-id="51f1c-192">You can implement your [own retry with exponential backoff](/azure/architecture/patterns/retry) technique by attempting to retry with an exponentially increasing wait time, until a maximum retry count has been reached.</span></span> <span data-ttu-id="51f1c-193">Essa técnica aceita o fato de que os recursos de nuvem podem estar intermitentemente não disponíveis por curtos períodos, resultando na falha de algumas solicitações.</span><span class="sxs-lookup"><span data-stu-id="51f1c-193">This technique embraces the fact that cloud resources might intermittently be unavailable for short periods of time, resulting in failure of some requests.</span></span>

<span data-ttu-id="51f1c-194">Para o BD SQL do Azure, o Entity Framework Core já fornece resiliência interna de conexão de banco de dados e lógica de repetição.</span><span class="sxs-lookup"><span data-stu-id="51f1c-194">For Azure SQL DB, Entity Framework Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="51f1c-195">Mas você precisará habilitar a estratégia de execução do Entity Framework para cada conexão de DbContext, caso deseje ter conexões do EF Core resilientes.</span><span class="sxs-lookup"><span data-stu-id="51f1c-195">But you need to enable the Entity Framework execution strategy for each DbContext connection if you want to have resilient EF Core connections.</span></span>

<span data-ttu-id="51f1c-196">Por exemplo, o código a seguir no nível de conexão do EF Core permite conexões SQL resilientes que serão repetidas se a conexão falhar.</span><span class="sxs-lookup"><span data-stu-id="51f1c-196">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

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

#### <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="51f1c-197">Estratégias de execução e transações explícitas que usam BeginTransaction e várias DbContexts</span><span class="sxs-lookup"><span data-stu-id="51f1c-197">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span>

<span data-ttu-id="51f1c-198">Quando as repetições estão habilitadas nas conexões do EF Core, cada operação executada que usa o EF Core se torna sua própria operação repetível.</span><span class="sxs-lookup"><span data-stu-id="51f1c-198">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retryable operation.</span></span> <span data-ttu-id="51f1c-199">Cada consulta e cada chamada a SaveChanges serão repetidas como uma unidade se ocorrer uma falha temporária.</span><span class="sxs-lookup"><span data-stu-id="51f1c-199">Each query and each call to SaveChanges will be retried as a unit if a transient failure occurs.</span></span>

<span data-ttu-id="51f1c-200">No entanto, se o código iniciar uma transação usando BeginTransaction, você estará definindo seu próprio grupo de operações que precisam ser tratadas como uma unidade: tudo dentro da transação precisará ser revertido caso ocorra uma falha.</span><span class="sxs-lookup"><span data-stu-id="51f1c-200">However, if your code initiates a transaction using BeginTransaction, you are defining your own group of operations that need to be treated as a unit; everything inside the transaction has to be rolled back if a failure occurs.</span></span> <span data-ttu-id="51f1c-201">Você verá uma exceção como a mostrada a seguir se tentar executar essa transação ao usar uma estratégia de execução do EF (política de repetição) e incluir várias chamadas SaveChanges de diversos DbContexts na transação.</span><span class="sxs-lookup"><span data-stu-id="51f1c-201">You will see an exception like the following if you attempt to execute that transaction when using an EF execution strategy (retry policy) and you include several SaveChanges from multiple DbContexts in it.</span></span>

<span data-ttu-id="51f1c-202">System.InvalidOperationException: a estratégia de execução configurada 'SqlServerRetryingExecutionStrategy' não dá suporte a transações iniciadas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="51f1c-202">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="51f1c-203">Use a estratégia de execução retornada por ' DbContext. Database. CreateExecutionStrategy () ' para executar todas as operações na transação como uma unidade com nova tentativa.</span><span class="sxs-lookup"><span data-stu-id="51f1c-203">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retryable unit.</span></span>

<span data-ttu-id="51f1c-204">A solução é invocar manualmente a estratégia de execução do EF com um delegado que representa tudo que precisa ser executado.</span><span class="sxs-lookup"><span data-stu-id="51f1c-204">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="51f1c-205">Se ocorrer uma falha transitória, a estratégia de execução invocará o representante novamente.</span><span class="sxs-lookup"><span data-stu-id="51f1c-205">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="51f1c-206">O seguinte código mostra como implementar essa abordagem:</span><span class="sxs-lookup"><span data-stu-id="51f1c-206">The following code shows how to implement this approach:</span></span>

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

<span data-ttu-id="51f1c-207">O primeiro DbContext é o \_catalogContext e o segundo DbContext está dentro do objeto \_integrationEventLogService.</span><span class="sxs-lookup"><span data-stu-id="51f1c-207">The first DbContext is the \_catalogContext and the second DbContext is within the \_integrationEventLogService object.</span></span> <span data-ttu-id="51f1c-208">Por fim, a ação de Confirmação é executada em vários DbContexts e usando uma Estratégia de Execução do EF.</span><span class="sxs-lookup"><span data-stu-id="51f1c-208">Finally, the Commit action would be performed multiple DbContexts and using an EF Execution Strategy.</span></span>

> ### <a name="references--entity-framework-core"></a><span data-ttu-id="51f1c-209">Referências – Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="51f1c-209">References – Entity Framework Core</span></span>
>
> - <span data-ttu-id="51f1c-210">**EF Core docs**
>   <https://docs.microsoft.com/ef/></span><span class="sxs-lookup"><span data-stu-id="51f1c-210">**EF Core Docs**
<https://docs.microsoft.com/ef/></span></span>
> - <span data-ttu-id="51f1c-211">**EF Core: dados relacionados**
>   <https://docs.microsoft.com/ef/core/querying/related-data></span><span class="sxs-lookup"><span data-stu-id="51f1c-211">**EF Core: Related Data**
<https://docs.microsoft.com/ef/core/querying/related-data></span></span>
> - <span data-ttu-id="51f1c-212">**Evite carregar entidades lentas em aplicativos ASPNET**
>   <https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications></span><span class="sxs-lookup"><span data-stu-id="51f1c-212">**Avoid Lazy Loading Entities in ASPNET Applications**
<https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications></span></span>

## <a name="ef-core-or-micro-orm"></a><span data-ttu-id="51f1c-213">EF Core ou micro-ORM?</span><span class="sxs-lookup"><span data-stu-id="51f1c-213">EF Core or micro-ORM?</span></span>

<span data-ttu-id="51f1c-214">Embora EF Core seja uma ótima opção para gerenciar a persistência, e para a maior parte encapsula os detalhes do banco de dados de desenvolvedores de aplicativos, não é a única opção.</span><span class="sxs-lookup"><span data-stu-id="51f1c-214">While EF Core is a great choice for managing persistence, and for the most part encapsulates database details from application developers, it isn't the only choice.</span></span> <span data-ttu-id="51f1c-215">Outra alternativa popular de software livre é [Dapper](https://github.com/StackExchange/Dapper), uma chamada de micro ORM.</span><span class="sxs-lookup"><span data-stu-id="51f1c-215">Another popular open-source alternative is [Dapper](https://github.com/StackExchange/Dapper), a so-called micro-ORM.</span></span> <span data-ttu-id="51f1c-216">Um micro-ORM é uma ferramenta leve e menos completa para o mapeamento de objetos para estruturas de dados.</span><span class="sxs-lookup"><span data-stu-id="51f1c-216">A micro-ORM is a lightweight, less full-featured tool for mapping objects to data structures.</span></span> <span data-ttu-id="51f1c-217">No caso do Dapper, seu design visa o foco no desempenho, em vez do encapsulamento total das consultas subjacentes usadas por ele para recuperar e atualizar os dados.</span><span class="sxs-lookup"><span data-stu-id="51f1c-217">In the case of Dapper, its design goals focus on performance, rather than fully encapsulating the underlying queries it uses to retrieve and update data.</span></span> <span data-ttu-id="51f1c-218">Como ele não abstrai o SQL do desenvolvedor, o Dapper fica "mais próximo do metal" e permite aos desenvolvedores escreverem as consultas exatas que desejam usar para determinada operação de acesso a dados.</span><span class="sxs-lookup"><span data-stu-id="51f1c-218">Because it doesn't abstract SQL from the developer, Dapper is "closer to the metal" and lets developers write the exact queries they want to use for a given data access operation.</span></span>

<span data-ttu-id="51f1c-219">O EF Core tem dois recursos significativos que os separam do Dapper, mas também contribuem com a sobrecarga de desempenho.</span><span class="sxs-lookup"><span data-stu-id="51f1c-219">EF Core has two significant features it provides which separate it from Dapper but also add to its performance overhead.</span></span> <span data-ttu-id="51f1c-220">O primeiro é a conversão de expressões LINQ em SQL.</span><span class="sxs-lookup"><span data-stu-id="51f1c-220">The first is translation from LINQ expressions into SQL.</span></span> <span data-ttu-id="51f1c-221">Essas conversões são armazenadas em cache, mas ainda assim há sobrecarga na execução na primeira vez.</span><span class="sxs-lookup"><span data-stu-id="51f1c-221">These translations are cached, but even so there is overhead in performing them the first time.</span></span> <span data-ttu-id="51f1c-222">O segundo é o controle de alterações em entidades (de forma que instruções de atualização eficientes possam ser geradas).</span><span class="sxs-lookup"><span data-stu-id="51f1c-222">The second is change tracking on entities (so that efficient update statements can be generated).</span></span> <span data-ttu-id="51f1c-223">Esse comportamento pode ser desativado para consultas específicas com a extensão AsNotTracking.</span><span class="sxs-lookup"><span data-stu-id="51f1c-223">This behavior can be turned off for specific queries by using the AsNotTracking extension.</span></span> <span data-ttu-id="51f1c-224">O EF Core também gera consultas SQL que geralmente são muito eficientes e, de qualquer modo, perfeitamente aceitáveis do ponto de vista de desempenho. No entanto, caso precise ter um controle refinado sobre a consulta precisa a ser executada, passe um SQL personalizado (ou execute um procedimento armazenado) usando o EF Core também.</span><span class="sxs-lookup"><span data-stu-id="51f1c-224">EF Core also generates SQL queries that usually are very efficient and in any case perfectly acceptable from a performance standpoint, but if you need fine control over the precise query to be executed, you can pass in custom SQL (or execute a stored procedure) using EF Core, too.</span></span> <span data-ttu-id="51f1c-225">Nesse caso, o Dapper ainda supera o EF Core, mas somente um pouco.</span><span class="sxs-lookup"><span data-stu-id="51f1c-225">In this case, Dapper still outperforms EF Core, but only slightly.</span></span> <span data-ttu-id="51f1c-226">Julie Lerman apresenta alguns dados de desempenho em seu artigo do MSDN de maio de 2016 [Dapper, Entity Framework e aplicativos híbridos](/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps).</span><span class="sxs-lookup"><span data-stu-id="51f1c-226">Julie Lerman presents some performance data in her May 2016 MSDN article [Dapper, Entity Framework, and Hybrid Apps](/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps).</span></span> <span data-ttu-id="51f1c-227">Encontre dados de parâmetro de comparação de desempenho adicionais para uma variedade de métodos de acesso a dados [no site do Dapper](https://github.com/StackExchange/Dapper).</span><span class="sxs-lookup"><span data-stu-id="51f1c-227">Additional performance benchmark data for a variety of data access methods can be found on [the Dapper site](https://github.com/StackExchange/Dapper).</span></span>

<span data-ttu-id="51f1c-228">Para ver a diferença entre a sintaxe do Dapper e do EF Core, considere estas duas versões do mesmo método para recuperar uma lista de itens:</span><span class="sxs-lookup"><span data-stu-id="51f1c-228">To see how the syntax for Dapper varies from EF Core, consider these two versions of the same method for retrieving a list of items:</span></span>

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

<span data-ttu-id="51f1c-229">Caso você precise criar gráficos de objetos mais complexos com o Dapper, precisará escrever as consultas associadas (em vez de adicionar um método Include como faria no EF Core).</span><span class="sxs-lookup"><span data-stu-id="51f1c-229">If you need to build more complex object graphs with Dapper, you need to write the associated queries yourself (as opposed to adding an Include as you would in EF Core).</span></span> <span data-ttu-id="51f1c-230">Isso é compatível com uma variedade de sintaxes, incluindo um recurso chamado Mapeamento Múltiplo, que permite mapear linhas individuais para vários objetos mapeados.</span><span class="sxs-lookup"><span data-stu-id="51f1c-230">This is supported through a variety of syntaxes, including a feature called Multi Mapping that lets you map individual rows to multiple mapped objects.</span></span> <span data-ttu-id="51f1c-231">Por exemplo, considerando uma classe Post com uma propriedade Owner do tipo User, o seguinte SQL retorna todos os dados necessários:</span><span class="sxs-lookup"><span data-stu-id="51f1c-231">For example, given a class Post with a property Owner of type User, the following SQL would return all of the necessary data:</span></span>

```sql
select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id
```

<span data-ttu-id="51f1c-232">Cada linha retornada inclui os dados de User e Post.</span><span class="sxs-lookup"><span data-stu-id="51f1c-232">Each returned row includes both User and Post data.</span></span> <span data-ttu-id="51f1c-233">Como os dados de User devem ser anexados aos dados de Post por meio de sua propriedade Owner, a seguinte função é usada:</span><span class="sxs-lookup"><span data-stu-id="51f1c-233">Since the User data should be attached to the Post data via its Owner property, the following function is used:</span></span>

```csharp
(post, user) => { post.Owner = user; return post; }
```

<span data-ttu-id="51f1c-234">A listagem de código completa para retornar uma coleção de postagens com a propriedade Owner populada com os dados de usuário associados é:</span><span class="sxs-lookup"><span data-stu-id="51f1c-234">The full code listing to return a collection of posts with their Owner property populated with the associated user data would be:</span></span>

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

<span data-ttu-id="51f1c-235">Como ele oferece menos encapsulamento, o Dapper exige que os desenvolvedores saibam mais sobre como seus dados são armazenados, como consultá-los de forma eficiente e codificar mais para buscá-los.</span><span class="sxs-lookup"><span data-stu-id="51f1c-235">Because it offers less encapsulation, Dapper requires developers know more about how their data is stored, how to query it efficiently, and write more code to fetch it.</span></span> <span data-ttu-id="51f1c-236">Quando o modelo é alterado, em vez de simplesmente criar uma nova migração (outro recurso do EF Core) e/ou atualizar as informações de mapeamento em um local em um DbContext, cada consulta afetada deve ser atualizada.</span><span class="sxs-lookup"><span data-stu-id="51f1c-236">When the model changes, instead of simply creating a new migration (another EF Core feature), and/or updating mapping information in one place in a DbContext, every query that is impacted must be updated.</span></span> <span data-ttu-id="51f1c-237">Essas consultas não têm garantias de tempo de compilação, portanto, elas podem ser interrompidas em tempo de execução em resposta a alterações no modelo ou banco de dados, tornando os erros mais difíceis de detectar rapidamente.</span><span class="sxs-lookup"><span data-stu-id="51f1c-237">These queries have no compile-time guarantees, so they may break at run time in response to changes to the model or database, making errors more difficult to detect quickly.</span></span> <span data-ttu-id="51f1c-238">Em compensação por essa vantagem, o Dapper oferece um desempenho extremamente rápido.</span><span class="sxs-lookup"><span data-stu-id="51f1c-238">In exchange for these tradeoffs, Dapper offers extremely fast performance.</span></span>

<span data-ttu-id="51f1c-239">Para a maioria dos aplicativos e a maioria das partes de quase todos os aplicativos, o EF Core oferece um desempenho aceitável.</span><span class="sxs-lookup"><span data-stu-id="51f1c-239">For most applications, and most parts of almost all applications, EF Core offers acceptable performance.</span></span> <span data-ttu-id="51f1c-240">Portanto, seus benefícios de produtividade do desenvolvedor provavelmente superam a sobrecarga de desempenho.</span><span class="sxs-lookup"><span data-stu-id="51f1c-240">Thus, its developer productivity benefits are likely to outweigh its performance overhead.</span></span> <span data-ttu-id="51f1c-241">Para consultas que podem se beneficiar com o cache, a consulta real pode ser executada apenas em um pequeno percentual do tempo, tornando irrelevantes as pequenas diferenças no desempenho da consulta.</span><span class="sxs-lookup"><span data-stu-id="51f1c-241">For queries that can benefit from caching, the actual query may only be executed a tiny percentage of the time, making relatively small query performance differences moot.</span></span>

## <a name="sql-or-nosql"></a><span data-ttu-id="51f1c-242">SQL ou NoSQL</span><span class="sxs-lookup"><span data-stu-id="51f1c-242">SQL or NoSQL</span></span>

<span data-ttu-id="51f1c-243">Tradicionalmente, bancos de dados relacionais como o SQL Server dominaram o marketplace em armazenamento de dados persistente, mas não são a única solução disponível.</span><span class="sxs-lookup"><span data-stu-id="51f1c-243">Traditionally, relational databases like SQL Server have dominated the marketplace for persistent data storage, but they are not the only solution available.</span></span> <span data-ttu-id="51f1c-244">Bancos de dados NoSQL, como o [MongoDB](https://www.mongodb.com/what-is-mongodb), oferecem uma abordagem diferente para armazenar objetos.</span><span class="sxs-lookup"><span data-stu-id="51f1c-244">NoSQL databases like [MongoDB](https://www.mongodb.com/what-is-mongodb) offer a different approach to storing objects.</span></span> <span data-ttu-id="51f1c-245">Em vez de mapear objetos para tabelas e linhas, outra opção é serializar o grafo de objeto inteiro e armazenar o resultado.</span><span class="sxs-lookup"><span data-stu-id="51f1c-245">Rather than mapping objects to tables and rows, another option is to serialize the entire object graph, and store the result.</span></span> <span data-ttu-id="51f1c-246">Os benefícios dessa abordagem são, pelo menos inicialmente, simplicidade e desempenho.</span><span class="sxs-lookup"><span data-stu-id="51f1c-246">The benefits of this approach, at least initially, are simplicity and performance.</span></span> <span data-ttu-id="51f1c-247">É mais simples armazenar um único objeto serializado com uma chave do que decompor o objeto em muitas tabelas com relações e atualizações e linhas que podem ter sido alteradas desde a última recuperação do objeto do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="51f1c-247">It's simpler to store a single serialized object with a key than to decompose the object into many tables with relationships and update and rows that may have changed since the object was last retrieved from the database.</span></span> <span data-ttu-id="51f1c-248">Da mesma forma, a busca e a desserialização de um único objeto de um repositório baseado em chaves geralmente são muito mais rápidas e mais fáceis do que junções complexas ou várias consultas de banco de dados necessárias para compor totalmente o mesmo objeto de um banco de dados relacional.</span><span class="sxs-lookup"><span data-stu-id="51f1c-248">Likewise, fetching and deserializing a single object from a key-based store is typically much faster and easier than complex joins or multiple database queries required to fully compose the same object from a relational database.</span></span> <span data-ttu-id="51f1c-249">A falta de bloqueios ou de transações ou um esquema fixo também faz com que os bancos de dados NoSQL receptivosm o dimensionamento em vários computadores, dando suporte a conjuntos muito grandes.</span><span class="sxs-lookup"><span data-stu-id="51f1c-249">The lack of locks or transactions or a fixed schema also makes NoSQL databases amenable to scaling across many machines, supporting very large datasets.</span></span>

<span data-ttu-id="51f1c-250">Por outro lado, os bancos de dados NoSQL (como são normalmente chamados) trazem algumas desvantagens.</span><span class="sxs-lookup"><span data-stu-id="51f1c-250">On the other hand, NoSQL databases (as they are typically called) have their drawbacks.</span></span> <span data-ttu-id="51f1c-251">Os bancos de dados relacionais usam a normalização para impor a consistência e evitar a duplicação de dados.</span><span class="sxs-lookup"><span data-stu-id="51f1c-251">Relational databases use normalization to enforce consistency and avoid duplication of data.</span></span> <span data-ttu-id="51f1c-252">Isso reduz o tamanho total do banco de dados e garante que as atualizações nos dados compartilhados estejam disponíveis imediatamente em todo o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="51f1c-252">This reduces the total size of the database and ensures that updates to shared data are available immediately throughout the database.</span></span> <span data-ttu-id="51f1c-253">Em um banco de dados relacional, uma tabela Address pode referenciar uma tabela Country por ID, de modo que, se o nome de um país/região for alterado, os registros de endereço se beneficiarão com a atualização sem que eles mesmos precisem ser atualizados.</span><span class="sxs-lookup"><span data-stu-id="51f1c-253">In a relational database, an Address table might reference a Country table by ID, such that if the name of a country/region were changed, the address records would benefit from the update without themselves having to be updated.</span></span> <span data-ttu-id="51f1c-254">No entanto, em um banco de dados NoSQL, Address e seu Country associado podem ser serializados como parte de muitos objetos armazenados.</span><span class="sxs-lookup"><span data-stu-id="51f1c-254">However, in a NoSQL database, Address and its associated Country might be serialized as part of many stored objects.</span></span> <span data-ttu-id="51f1c-255">Uma atualização em um nome de país/região exige que todos esses objetos sejam atualizados, em vez de uma única linha.</span><span class="sxs-lookup"><span data-stu-id="51f1c-255">An update to a country/region name would require all such objects to be updated, rather than a single row.</span></span> <span data-ttu-id="51f1c-256">Os bancos de dados relacionais também podem garantir a integridade relacional pela imposição de regras como chaves estrangeiras.</span><span class="sxs-lookup"><span data-stu-id="51f1c-256">Relational databases can also ensure relational integrity by enforcing rules like foreign keys.</span></span> <span data-ttu-id="51f1c-257">Normalmente, os bancos de dados NoSQL não oferecem essas restrições em seus dados.</span><span class="sxs-lookup"><span data-stu-id="51f1c-257">NoSQL databases typically do not offer such constraints on their data.</span></span>

<span data-ttu-id="51f1c-258">Outra complexidade com a qual os bancos de dados NoSQL precisar lidar é o controle de versão.</span><span class="sxs-lookup"><span data-stu-id="51f1c-258">Another complexity NoSQL databases must deal with is versioning.</span></span> <span data-ttu-id="51f1c-259">Quando as propriedades de um objeto são alteradas, ele pode não ser desserializado das versões anteriores que foram armazenadas.</span><span class="sxs-lookup"><span data-stu-id="51f1c-259">When an object's properties change, it may not be able to be deserialized from past versions that were stored.</span></span> <span data-ttu-id="51f1c-260">Portanto, todos os objetos existentes que têm uma versão (anterior) serializada do objeto precisam ser atualizados para que estejam em conformidade com seu novo esquema.</span><span class="sxs-lookup"><span data-stu-id="51f1c-260">Thus, all existing objects that have a serialized (previous) version of the object must be updated to conform to its new schema.</span></span> <span data-ttu-id="51f1c-261">Isso não é conceitualmente diferente de um banco de dados relacional, no qual as alterações de esquema às vezes exigem scripts de atualização ou atualizações de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="51f1c-261">This is not conceptually different from a relational database, where schema changes sometimes require update scripts or mapping updates.</span></span> <span data-ttu-id="51f1c-262">No entanto, o número de entradas que precisa ser modificado costuma ser muito maior na abordagem NoSQL, porque há mais duplicação de dados.</span><span class="sxs-lookup"><span data-stu-id="51f1c-262">However, the number of entries that must be modified is often much greater in the NoSQL approach, because there is more duplication of data.</span></span>

<span data-ttu-id="51f1c-263">Em bancos de dados NoSQL, é possível armazenar várias versões de objetos, algo para o qual os bancos de dados relacionais de esquema fixo normalmente não dão suporte.</span><span class="sxs-lookup"><span data-stu-id="51f1c-263">It's possible in NoSQL databases to store multiple versions of objects, something fixed schema relational databases typically do not support.</span></span> <span data-ttu-id="51f1c-264">No entanto, nesse caso, o código do aplicativo precisará levar em conta a existência de versões anteriores de objetos, adicionando mais complexidade.</span><span class="sxs-lookup"><span data-stu-id="51f1c-264">However, in this case your application code will need to account for the existence of previous versions of objects, adding additional complexity.</span></span>

<span data-ttu-id="51f1c-265">Normalmente, os bancos de dados NoSQL não impõem o [ACID](https://en.wikipedia.org/wiki/ACID), o que significa que eles trazem vantagens de desempenho e escalabilidade comparado aos bancos de dados relacionais.</span><span class="sxs-lookup"><span data-stu-id="51f1c-265">NoSQL databases typically do not enforce [ACID](https://en.wikipedia.org/wiki/ACID), which means they have both performance and scalability benefits over relational databases.</span></span> <span data-ttu-id="51f1c-266">Elas são adequadas a conjuntos de e objetos extremamente grandes que não são adequados para o armazenamento em estruturas de tabela normalizadas.</span><span class="sxs-lookup"><span data-stu-id="51f1c-266">They're well suited to extremely large datasets and objects that are not well suited to storage in normalized table structures.</span></span> <span data-ttu-id="51f1c-267">Não há nenhum motivo pelo qual um único aplicativo não possa aproveitar ambos os bancos de dados relacional e NoSQL, usando cada um deles nos casos em que for mais adequado.</span><span class="sxs-lookup"><span data-stu-id="51f1c-267">There is no reason why a single application cannot take advantage of both relational and NoSQL databases, using each where it is best suited.</span></span>

## <a name="azure-cosmos-db"></a><span data-ttu-id="51f1c-268">Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="51f1c-268">Azure Cosmos DB</span></span>

<span data-ttu-id="51f1c-269">O Azure Cosmos DB é um serviço de banco de dados NoSQL totalmente gerenciado que oferece armazenamento baseado em nuvem sem esquemas.</span><span class="sxs-lookup"><span data-stu-id="51f1c-269">Azure Cosmos DB is a fully managed NoSQL database service that offers cloud-based schema-free data storage.</span></span> <span data-ttu-id="51f1c-270">O Azure Cosmos DB é criado para desempenho rápido e previsível, alta disponibilidade, dimensionamento elástico e distribuição global.</span><span class="sxs-lookup"><span data-stu-id="51f1c-270">Azure Cosmos DB is built for fast and predictable performance, high availability, elastic scaling, and global distribution.</span></span> <span data-ttu-id="51f1c-271">Apesar de ser um banco de dados NoSQL, os desenvolvedores podem usar funcionalidades avançadas e conhecidas de consultas SQL em dados JSON.</span><span class="sxs-lookup"><span data-stu-id="51f1c-271">Despite being a NoSQL database, developers can use rich and familiar SQL query capabilities on JSON data.</span></span> <span data-ttu-id="51f1c-272">Todos os recursos no Azure Cosmos DB são armazenados como documentos JSON.</span><span class="sxs-lookup"><span data-stu-id="51f1c-272">All resources in Azure Cosmos DB are stored as JSON documents.</span></span> <span data-ttu-id="51f1c-273">Os recursos são gerenciados como _itens_, que são documentos que contém metadados, e _feeds_, que são coleções de itens.</span><span class="sxs-lookup"><span data-stu-id="51f1c-273">Resources are managed as _items_, which are documents containing metadata, and _feeds_, which are collections of items.</span></span> <span data-ttu-id="51f1c-274">A Figura 8-2 mostra a relação entre diferentes recursos de Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="51f1c-274">Figure 8-2 shows the relationship between different Azure Cosmos DB resources.</span></span>

![A relação hierárquica entre os recursos no Azure Cosmos DB, um banco de dados JSON NoSQL](./media/image8-2.png)

<span data-ttu-id="51f1c-276">**Figura 8-2.**</span><span class="sxs-lookup"><span data-stu-id="51f1c-276">**Figure 8-2.**</span></span> <span data-ttu-id="51f1c-277">Azure Cosmos DB organização de recursos.</span><span class="sxs-lookup"><span data-stu-id="51f1c-277">Azure Cosmos DB resource organization.</span></span>

<span data-ttu-id="51f1c-278">A linguagem de consulta Azure Cosmos DB é uma interface simples, mas poderosa, para consultar documentos JSON.</span><span class="sxs-lookup"><span data-stu-id="51f1c-278">The Azure Cosmos DB query language is a simple yet powerful interface for querying JSON documents.</span></span> <span data-ttu-id="51f1c-279">A linguagem suporta um subconjunto da gramática ANSI SQL e adiciona profunda integração do objeto JavaScript, matrizes, construção de objetos e invocação de funções.</span><span class="sxs-lookup"><span data-stu-id="51f1c-279">The language supports a subset of ANSI SQL grammar and adds deep integration of JavaScript object, arrays, object construction, and function invocation.</span></span>

<span data-ttu-id="51f1c-280">**Referências – Azure Cosmos DB**</span><span class="sxs-lookup"><span data-stu-id="51f1c-280">**References – Azure Cosmos DB**</span></span>

- <span data-ttu-id="51f1c-281">Introdução Azure Cosmos DB <https://docs.microsoft.com/azure/cosmos-db/introduction></span><span class="sxs-lookup"><span data-stu-id="51f1c-281">Azure Cosmos DB Introduction <https://docs.microsoft.com/azure/cosmos-db/introduction></span></span>

## <a name="other-persistence-options"></a><span data-ttu-id="51f1c-282">Outras opções de persistência</span><span class="sxs-lookup"><span data-stu-id="51f1c-282">Other persistence options</span></span>

<span data-ttu-id="51f1c-283">Além das opções de armazenamento relacional e NoSQL, os aplicativos ASP.NET Core podem usar o Armazenamento do Azure para armazenar uma variedade de formatos de dados e arquivos de forma escalonável e baseada em nuvem.</span><span class="sxs-lookup"><span data-stu-id="51f1c-283">In addition to relational and NoSQL storage options, ASP.NET Core applications can use Azure Storage to store a variety of data formats and files in a cloud-based, scalable fashion.</span></span> <span data-ttu-id="51f1c-284">O Armazenamento do Azure é altamente escalonável e, portanto, você pode começar armazenando pequenas quantidades de dados e aumentar até armazenar centenas ou terabytes, caso seu aplicativo precise.</span><span class="sxs-lookup"><span data-stu-id="51f1c-284">Azure Storage is massively scalable, so you can start out storing small amounts of data and scale up to storing hundreds or terabytes if your application requires it.</span></span> <span data-ttu-id="51f1c-285">O Armazenamento do Azure é compatível com quatro tipos de dados:</span><span class="sxs-lookup"><span data-stu-id="51f1c-285">Azure Storage supports four kinds of data:</span></span>

- <span data-ttu-id="51f1c-286">Armazenamento de Blobs para armazenamento de texto não estruturado ou binário, também conhecido como armazenamento de objeto.</span><span class="sxs-lookup"><span data-stu-id="51f1c-286">Blob Storage for unstructured text or binary storage, also referred to as object storage.</span></span>

- <span data-ttu-id="51f1c-287">Armazenamento de Tabelas para conjuntos de dados estruturados, acessíveis por meio de chaves de linha.</span><span class="sxs-lookup"><span data-stu-id="51f1c-287">Table Storage for structured datasets, accessible via row keys.</span></span>

- <span data-ttu-id="51f1c-288">Armazenamento de Filas para mensagens confiáveis baseadas em fila.</span><span class="sxs-lookup"><span data-stu-id="51f1c-288">Queue Storage for reliable queue-based messaging.</span></span>

- <span data-ttu-id="51f1c-289">Armazenamento de Arquivos para acesso a arquivos compartilhados entre aplicativos locais e as máquinas virtuais do Azure.</span><span class="sxs-lookup"><span data-stu-id="51f1c-289">File Storage for shared file access between Azure virtual machines and on-premises applications.</span></span>

<span data-ttu-id="51f1c-290">**Referências – Armazenamento do Azure**</span><span class="sxs-lookup"><span data-stu-id="51f1c-290">**References – Azure Storage**</span></span>

- <span data-ttu-id="51f1c-291">Introdução ao armazenamento do Azure <https://docs.microsoft.com/azure/storage/common/storage-introduction></span><span class="sxs-lookup"><span data-stu-id="51f1c-291">Azure Storage Introduction <https://docs.microsoft.com/azure/storage/common/storage-introduction></span></span>

## <a name="caching"></a><span data-ttu-id="51f1c-292">Cache</span><span class="sxs-lookup"><span data-stu-id="51f1c-292">Caching</span></span>

<span data-ttu-id="51f1c-293">Em aplicativos Web, cada solicitação da Web deve ser concluída no menor tempo possível.</span><span class="sxs-lookup"><span data-stu-id="51f1c-293">In web applications, each web request should be completed in the shortest time possible.</span></span> <span data-ttu-id="51f1c-294">Uma maneira de fazer isso é limitar o número de chamadas externas que o servidor deve fazer para concluir a solicitação.</span><span class="sxs-lookup"><span data-stu-id="51f1c-294">One way to achieve this is to limit the number of external calls the server must make to complete the request.</span></span> <span data-ttu-id="51f1c-295">O cache envolve o armazenamento de uma cópia dos dados no servidor (ou em outro armazenamento de dados que é consultado com mais facilidade do que a fonte dos dados).</span><span class="sxs-lookup"><span data-stu-id="51f1c-295">Caching involves storing a copy of data on the server (or another data store that is more easily queried than the source of the data).</span></span> <span data-ttu-id="51f1c-296">Os aplicativos Web, e especialmente aplicativos Web tradicionais não SPA, precisam criar toda a interface do usuário a cada solicitação.</span><span class="sxs-lookup"><span data-stu-id="51f1c-296">Web applications, and especially non-SPA traditional web applications, need to build the entire user interface with every request.</span></span> <span data-ttu-id="51f1c-297">Isso geralmente envolve fazer muitas das mesmas consultas de banco de dados repetidamente de uma solicitação de usuário para a próxima.</span><span class="sxs-lookup"><span data-stu-id="51f1c-297">This frequently involves making many of the same database queries repeatedly from one user request to the next.</span></span> <span data-ttu-id="51f1c-298">Na maioria dos casos, esses dados são raramente alterados e, portanto, há pouca justificativa para solicitá-los constantemente do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="51f1c-298">In most cases, this data changes rarely, so there is little reason to constantly request it from the database.</span></span> <span data-ttu-id="51f1c-299">O ASP.NET Core é compatível com cache de resposta, armazenamento em cache de páginas inteiras e cache de dados, que é compatível com um comportamento de cache mais granular.</span><span class="sxs-lookup"><span data-stu-id="51f1c-299">ASP.NET Core supports response caching, for caching entire pages, and data caching, which supports more granular caching behavior.</span></span>

<span data-ttu-id="51f1c-300">Ao implementar o cache, é importante ter em mente a separação de interesses.</span><span class="sxs-lookup"><span data-stu-id="51f1c-300">When implementing caching, it's important to keep in mind separation of concerns.</span></span> <span data-ttu-id="51f1c-301">Evite a implementação da lógica de cache na lógica de acesso a dados ou na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="51f1c-301">Avoid implementing caching logic in your data access logic, or in your user interface.</span></span> <span data-ttu-id="51f1c-302">Em vez disso, encapsule o cache em suas próprias classes e use a configuração para gerenciar seu comportamento.</span><span class="sxs-lookup"><span data-stu-id="51f1c-302">Instead, encapsulate caching in its own classes, and use configuration to manage its behavior.</span></span> <span data-ttu-id="51f1c-303">Isso segue os princípios de Aberto/Fechado e Responsabilidade Única e facilitará o gerenciamento de como você usa o cache em seu aplicativo à medida que ele cresce.</span><span class="sxs-lookup"><span data-stu-id="51f1c-303">This follows the Open/Closed and Single Responsibility principles, and will make it easier for you to manage how you use caching in your application as it grows.</span></span>

### <a name="aspnet-core-response-caching"></a><span data-ttu-id="51f1c-304">Cache de resposta do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="51f1c-304">ASP.NET Core response caching</span></span>

<span data-ttu-id="51f1c-305">O ASP.NET Core é compatível com dois níveis de cache de resposta.</span><span class="sxs-lookup"><span data-stu-id="51f1c-305">ASP.NET Core supports two levels of response caching.</span></span> <span data-ttu-id="51f1c-306">O primeiro nível não armazena nada em cache no servidor, mas adiciona cabeçalhos HTTP que instruem os clientes e servidores proxy a armazenar as respostas em cache.</span><span class="sxs-lookup"><span data-stu-id="51f1c-306">The first level does not cache anything on the server, but adds HTTP headers that instruct clients and proxy servers to cache responses.</span></span> <span data-ttu-id="51f1c-307">Isso é implementado pela adição do atributo ResponseCache a controladores ou ações individuais:</span><span class="sxs-lookup"><span data-stu-id="51f1c-307">This is implemented by adding the ResponseCache attribute to individual controllers or actions:</span></span>

```csharp
[ResponseCache(Duration = 60)]
public IActionResult Contact()
{
    ViewData["Message"] = "Your contact page.";
    return View();
}
```

<span data-ttu-id="51f1c-308">O exemplo anterior resultará no seguinte cabeçalho que está sendo adicionado à resposta, instruindo os clientes a armazenarem o resultado em cache por até 60 segundos.</span><span class="sxs-lookup"><span data-stu-id="51f1c-308">The previous example will result in the following header being added to the response, instructing clients to cache the result for up to 60 seconds.</span></span>

<span data-ttu-id="51f1c-309">Cache-Control: public,max-age=60</span><span class="sxs-lookup"><span data-stu-id="51f1c-309">Cache-Control: public,max-age=60</span></span>

<span data-ttu-id="51f1c-310">Para adicionar cache na memória do lado do servidor ao aplicativo, referencie o pacote NuGet Microsoft.AspNetCore.ResponseCaching e, em seguida, adicione o middleware de cache de resposta.</span><span class="sxs-lookup"><span data-stu-id="51f1c-310">In order to add server-side in-memory caching to the application, you must reference the Microsoft.AspNetCore.ResponseCaching NuGet package, and then add the Response Caching middleware.</span></span> <span data-ttu-id="51f1c-311">Este middleware é configurado em ConfigureServices e na Configuração de Inicialização:</span><span class="sxs-lookup"><span data-stu-id="51f1c-311">This middleware is configured in both ConfigureServices and Configure in Startup:</span></span>

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

<span data-ttu-id="51f1c-312">O middleware de cache de resposta armazenará em cache automaticamente as respostas baseadas em um conjunto de condições, que pode ser personalizado.</span><span class="sxs-lookup"><span data-stu-id="51f1c-312">The Response Caching Middleware will automatically cache responses based on a set of conditions, which you can customize.</span></span> <span data-ttu-id="51f1c-313">Por padrão, apenas respostas 200 (OK) solicitadas por meio de métodos GET ou HEAD são armazenadas em cache.</span><span class="sxs-lookup"><span data-stu-id="51f1c-313">By default, only 200 (OK) responses requested via GET or HEAD methods are cached.</span></span> <span data-ttu-id="51f1c-314">Além disso, as solicitações devem ter uma resposta com um cabeçalho público Cache-Control: e não pode incluir cabeçalhos de Authorization ou Set-Cookie.</span><span class="sxs-lookup"><span data-stu-id="51f1c-314">In addition, requests must have a response with a Cache-Control: public header, and cannot include headers for Authorization or Set-Cookie.</span></span> <span data-ttu-id="51f1c-315">Consulte uma [lista completa das condições de cache usadas pelo middleware de cache de resposta](/aspnet/core/performance/caching/middleware#conditions-for-caching).</span><span class="sxs-lookup"><span data-stu-id="51f1c-315">See a [complete list of the caching conditions used by the response caching middleware](/aspnet/core/performance/caching/middleware#conditions-for-caching).</span></span>

### <a name="data-caching"></a><span data-ttu-id="51f1c-316">Armazenamento de dados em cache</span><span class="sxs-lookup"><span data-stu-id="51f1c-316">Data caching</span></span>

<span data-ttu-id="51f1c-317">Em vez de (ou além de) armazenar em cache as respostas da Web completas, você pode armazenar em cache os resultados de consultas de dados individuais.</span><span class="sxs-lookup"><span data-stu-id="51f1c-317">Rather than (or in addition to) caching full web responses, you can cache the results of individual data queries.</span></span> <span data-ttu-id="51f1c-318">Para isso, você pode usar o cache em memória no servidor Web ou usar [um cache distribuído](/aspnet/core/performance/caching/distributed).</span><span class="sxs-lookup"><span data-stu-id="51f1c-318">For this, you can use in memory caching on the web server, or use [a distributed cache](/aspnet/core/performance/caching/distributed).</span></span> <span data-ttu-id="51f1c-319">Esta seção demonstrará como implementar o cache em memória.</span><span class="sxs-lookup"><span data-stu-id="51f1c-319">This section will demonstrate how to implement in memory caching.</span></span>

<span data-ttu-id="51f1c-320">Adicione suporte para o cache em memória (ou distribuído) em ConfigureServices:</span><span class="sxs-lookup"><span data-stu-id="51f1c-320">You add support for memory (or distributed) caching in ConfigureServices:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

<span data-ttu-id="51f1c-321">Lembre-se de adicionar também o pacote NuGet Microsoft.Extensions.Caching.Memory.</span><span class="sxs-lookup"><span data-stu-id="51f1c-321">Be sure to add the Microsoft.Extensions.Caching.Memory NuGet package as well.</span></span>

<span data-ttu-id="51f1c-322">Depois de adicionar o serviço, solicite IMemoryCache por meio da injeção de dependência sempre que precisar acessar o cache.</span><span class="sxs-lookup"><span data-stu-id="51f1c-322">Once you've added the service, you request IMemoryCache via dependency injection wherever you need to access the cache.</span></span> <span data-ttu-id="51f1c-323">Neste exemplo, o CachedCatalogService usa o padrão de design Proxy (ou Decorador), fornecendo uma implementação alternativa de ICatalogService que controla o acesso à implementação de CatalogService subjacente ou que adiciona um comportamento a ela.</span><span class="sxs-lookup"><span data-stu-id="51f1c-323">In this example, the CachedCatalogService is using the Proxy (or Decorator) design pattern, by providing an alternative implementation of ICatalogService that controls access to (or adds behavior to) the underlying CatalogService implementation.</span></span>

```csharp
public class CachedCatalogService : ICatalogService
{
    private readonly IMemoryCache _cache;
    private readonly CatalogService _catalogService;
    private static readonly string _brandsKey = "brands";
    private static readonly string _typesKey = "types";
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
        string cacheKey = $"items-{pageIndex}-{itemsPage}-{brandID}-{typeId}";
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

<span data-ttu-id="51f1c-324">Para configurar o aplicativo para usar a versão armazenada em cache do serviço, mas ainda permitir que o serviço obtenha a instância de CatalogService necessária em seu construtor, adicione o seguinte em ConfigureServices:</span><span class="sxs-lookup"><span data-stu-id="51f1c-324">To configure the application to use the cached version of the service, but still allow the service to get the instance of CatalogService it needs in its constructor, you would add the following in ConfigureServices:</span></span>

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

<span data-ttu-id="51f1c-325">Com isso em vigor, as chamadas de banco de dados para buscar os dados de catálogo serão feitas apenas uma vez por minuto, em vez de a cada solicitação.</span><span class="sxs-lookup"><span data-stu-id="51f1c-325">With this in place, the database calls to fetch the catalog data will only be made once per minute, rather than on every request.</span></span> <span data-ttu-id="51f1c-326">Dependendo do tráfego para o site, isso pode ter um impacto significativo no número de consultas feitas no banco de dados e no tempo médio de carregamento da página para o home page que, no momento, depende de todas as três consultas expostas por esse serviço.</span><span class="sxs-lookup"><span data-stu-id="51f1c-326">Depending on the traffic to the site, this can have a significant impact on the number of queries made to the database, and the average page load time for the home page that currently depends on all three of the queries exposed by this service.</span></span>

<span data-ttu-id="51f1c-327">Um problema que surge quando o Caching é implementado é _dados obsoletos_ – ou seja, dados que foram alterados na origem, mas uma versão desatualizada permanece no cache.</span><span class="sxs-lookup"><span data-stu-id="51f1c-327">An issue that arises when caching is implemented is _stale data_ – that is, data that has changed at the source but an out-of-date version remains in the cache.</span></span> <span data-ttu-id="51f1c-328">Uma maneira simples de atenuar esse problema é usar pequenas durações de cache, pois há benefícios adicionais limitados em estender a duração de armazenamento em cache dos dados para um aplicativo ocupado.</span><span class="sxs-lookup"><span data-stu-id="51f1c-328">A simple way to mitigate this issue is to use small cache durations, since for a busy application there is limited additional benefit to extending the length data is cached.</span></span> <span data-ttu-id="51f1c-329">Por exemplo, considere uma página que faz uma consulta de banco de dados individual e é solicitada 10 vezes por segundo.</span><span class="sxs-lookup"><span data-stu-id="51f1c-329">For example, consider a page that makes a single database query, and is requested 10 times per second.</span></span> <span data-ttu-id="51f1c-330">Se essa página for armazenada em cache por um minuto, isso resultará no número de consultas de banco de dados feitas por minuto para reduzir de 600 para 1, uma redução de 99,8%.</span><span class="sxs-lookup"><span data-stu-id="51f1c-330">If this page is cached for one minute, it will result in the number of database queries made per minute to drop from 600 to 1, a reduction of 99.8%.</span></span> <span data-ttu-id="51f1c-331">Se, em vez disso, a duração do cache foi feita em uma hora, a redução geral é de 99,997%, mas agora, a probabilidade e a idade potencial dos dados obsoletos são aumentadas consideravelmente.</span><span class="sxs-lookup"><span data-stu-id="51f1c-331">If instead the cache duration were made one hour, the overall reduction would be 99.997%, but now the likelihood and potential age of stale data are both increased dramatically.</span></span>

<span data-ttu-id="51f1c-332">Outra abordagem é remover as entradas de cache de forma proativa quando os dados que elas contêm são atualizados.</span><span class="sxs-lookup"><span data-stu-id="51f1c-332">Another approach is to proactively remove cache entries when the data they contain is updated.</span></span> <span data-ttu-id="51f1c-333">As entradas individuais podem ser removidas se sua chave é conhecida:</span><span class="sxs-lookup"><span data-stu-id="51f1c-333">Any individual entry can be removed if its key is known:</span></span>

```csharp
_cache.Remove(cacheKey);
```

<span data-ttu-id="51f1c-334">Se o aplicativo expõe a funcionalidade para atualizar as entradas que ele armazena em cache, você pode remover as entradas de cache correspondentes no código que executa as atualizações.</span><span class="sxs-lookup"><span data-stu-id="51f1c-334">If your application exposes functionality for updating entries that it caches, you can remove the corresponding cache entries in your code that performs the updates.</span></span> <span data-ttu-id="51f1c-335">Às vezes, pode haver muitas entradas diferentes que dependem de determinado conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="51f1c-335">Sometimes there may be many different entries that depend on a particular set of data.</span></span> <span data-ttu-id="51f1c-336">Nesse caso, pode ser útil criar dependências entre as entradas de cache, usando um CancellationChangeToken.</span><span class="sxs-lookup"><span data-stu-id="51f1c-336">In that case, it can be useful to create dependencies between cache entries, by using a CancellationChangeToken.</span></span> <span data-ttu-id="51f1c-337">Com um CancellationChangeToken, você pode expirar várias entradas de cache de uma vez, cancelando o token.</span><span class="sxs-lookup"><span data-stu-id="51f1c-337">With a CancellationChangeToken, you can expire multiple cache entries at once by canceling the token.</span></span>

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

<span data-ttu-id="51f1c-338">O cache pode melhorar consideravelmente o desempenho das páginas da Web que solicitam repetidamente os mesmos valores do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="51f1c-338">Caching can dramatically improve the performance of web pages that repeatedly request the same values from the database.</span></span> <span data-ttu-id="51f1c-339">Meça o desempenho da página e o acesso a dados antes de aplicar o cache e somente aplique o cache quando houver necessidade de melhoria.</span><span class="sxs-lookup"><span data-stu-id="51f1c-339">Be sure to measure data access and page performance before applying caching, and only apply caching where you see a need for improvement.</span></span> <span data-ttu-id="51f1c-340">O Caching consome recursos de memória do servidor Web e aumenta a complexidade do aplicativo, portanto, é importante que você não Otimize prematuramente usando essa técnica.</span><span class="sxs-lookup"><span data-stu-id="51f1c-340">Caching consumes web server memory resources and increases the complexity of the application, so it's important you don't prematurely optimize using this technique.</span></span>

## <a name="getting-data-to-no-locblazor-no-locwebassembly-apps"></a><span data-ttu-id="51f1c-341">Obtendo dados para Blazor WebAssembly aplicativos</span><span class="sxs-lookup"><span data-stu-id="51f1c-341">Getting data to Blazor WebAssembly apps</span></span>

<span data-ttu-id="51f1c-342">Se você estiver criando aplicativos que usam o Blazor servidor, poderá usar Entity Framework e outras tecnologias de acesso a dados diretos, já que eles foram discutidos até o momento neste capítulo.</span><span class="sxs-lookup"><span data-stu-id="51f1c-342">If you're building apps that use Blazor Server, you can use Entity Framework and other direct data access technologies as they've been discussed thus far in this chapter.</span></span> <span data-ttu-id="51f1c-343">No entanto, ao criar Blazor WebAssembly aplicativos, como outras estruturas de spa, você precisará de uma estratégia diferente para o acesso a dados.</span><span class="sxs-lookup"><span data-stu-id="51f1c-343">However, when building Blazor WebAssembly apps, like other SPA frameworks, you will need a different strategy for data access.</span></span> <span data-ttu-id="51f1c-344">Normalmente, esses aplicativos acessam dados e interagem com o servidor por meio de pontos de extremidade da API Web.</span><span class="sxs-lookup"><span data-stu-id="51f1c-344">Typically, these applications access data and interact with the server through web API endpoints.</span></span>

<span data-ttu-id="51f1c-345">Se os dados ou as operações que estão sendo executadas forem confidenciais, certifique-se de examinar a seção sobre segurança no [capítulo anterior](develop-asp-net-core-mvc-apps.md) e proteger suas APIs contra acesso não autorizado.</span><span class="sxs-lookup"><span data-stu-id="51f1c-345">If the data or operations being performed are sensitive, be sure to review the section on security in the [previous chapter](develop-asp-net-core-mvc-apps.md) and protect your APIs against unauthorized access.</span></span>

<span data-ttu-id="51f1c-346">Você encontrará um exemplo de um Blazor WebAssembly aplicativo no [aplicativo de referência do eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb), no Blazor projeto de administração.</span><span class="sxs-lookup"><span data-stu-id="51f1c-346">You'll find an example of a Blazor WebAssembly app in the [eShopOnWeb reference application](https://github.com/dotnet-architecture/eShopOnWeb), in the BlazorAdmin project.</span></span> <span data-ttu-id="51f1c-347">Esse projeto é hospedado no projeto Web eShopOnWeb e permite que os usuários no grupo administradores gerenciem os itens na loja.</span><span class="sxs-lookup"><span data-stu-id="51f1c-347">This project is hosted within the eShopOnWeb Web project, and allows users in the Administrators group to manage the items in the store.</span></span> <span data-ttu-id="51f1c-348">Você pode ver uma captura de tela do aplicativo na Figura 8-3.</span><span class="sxs-lookup"><span data-stu-id="51f1c-348">You can see a screenshot of the application in Figure 8-3.</span></span>

![Captura de tela do administrador do catálogo eShopOnWeb](./media/image8-3.jpg)

<span data-ttu-id="51f1c-350">**Figura 8-3.**</span><span class="sxs-lookup"><span data-stu-id="51f1c-350">**Figure 8-3.**</span></span> <span data-ttu-id="51f1c-351">Captura de tela do administrador do catálogo eShopOnWeb.</span><span class="sxs-lookup"><span data-stu-id="51f1c-351">eShopOnWeb Catalog Admin Screenshot.</span></span>

<span data-ttu-id="51f1c-352">Ao buscar dados de APIs Web em um Blazor WebAssembly aplicativo, basta usar uma instância do `HttpClient` como faria em qualquer aplicativo .net.</span><span class="sxs-lookup"><span data-stu-id="51f1c-352">When fetching data from web APIs within a Blazor WebAssembly app, you just use an instance of `HttpClient` as you would in any .NET application.</span></span> <span data-ttu-id="51f1c-353">As etapas básicas envolvidas são criar a solicitação para enviar (se necessário, geralmente para solicitações POST ou PUT), aguardar a solicitação em si, verificar o código de status e desserializar a resposta.</span><span class="sxs-lookup"><span data-stu-id="51f1c-353">The basic steps involved are to create the request to send (if required, usually for POST or PUT requests), await the request itself, verify the status code, and deserialize the response.</span></span> <span data-ttu-id="51f1c-354">Se você pretende fazer muitas solicitações para um determinado conjunto de APIs, é uma boa ideia encapsular suas APIs e configurar o `HttpClient` endereço base centralmente.</span><span class="sxs-lookup"><span data-stu-id="51f1c-354">If you're going to make many requests to a given set of APIs, it's a good idea to encapsulate your APIs and configure the `HttpClient` base address centrally.</span></span> <span data-ttu-id="51f1c-355">Dessa forma, se você precisar ajustar qualquer uma dessas configurações entre ambientes, poderá fazer as alterações em apenas um lugar.</span><span class="sxs-lookup"><span data-stu-id="51f1c-355">This way, if you need to adjust any of these settings between environments, you can make the changes in just one place.</span></span> <span data-ttu-id="51f1c-356">Você deve adicionar suporte para este serviço em seu `Program.Main` :</span><span class="sxs-lookup"><span data-stu-id="51f1c-356">You should add support for this service in your `Program.Main`:</span></span>

```csharp
builder.Services.AddScoped(sp =>
    new HttpClient
    {
        BaseAddress = new Uri(builder.HostEnvironment.BaseAddress)
    });
```

<span data-ttu-id="51f1c-357">Se você precisar acessar os serviços com segurança, deverá acessar um token seguro e configurar o `HttpClient` para passar esse token como um cabeçalho de autenticação com cada solicitação:</span><span class="sxs-lookup"><span data-stu-id="51f1c-357">If you need to access services securely, you should access a secure token and configure the `HttpClient` to pass this token as an Authentication header with every request:</span></span>

```csharp
_httpClient.DefaultRequestHeaders.Authorization =
    new AuthenticationHeaderValue("Bearer", token);
```

<span data-ttu-id="51f1c-358">Isso pode ser feito a partir de qualquer componente que tenha o `HttpClient` injetado, desde que `HttpClient` não tenha sido adicionado aos serviços do aplicativo com um `Transient` tempo de vida.</span><span class="sxs-lookup"><span data-stu-id="51f1c-358">This can be done from any component that has the `HttpClient` injected into it, provided that `HttpClient` wasn't added to the application's services with a `Transient` lifetime.</span></span> <span data-ttu-id="51f1c-359">Cada referência a `HttpClient` no aplicativo faz referência à mesma instância, portanto, muda para ela em um fluxo de componente por todo o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="51f1c-359">Every reference to `HttpClient` in the application references the same instance, so changes to it in one component flow through the entire application.</span></span> <span data-ttu-id="51f1c-360">Um bom local para executar essa verificação de autenticação (seguido pela especificação do token) está em um componente compartilhado, como a navegação principal para o site.</span><span class="sxs-lookup"><span data-stu-id="51f1c-360">A good place to perform this authentication check (followed by specifying the token) is in a shared component like the main navigation for the site.</span></span> <span data-ttu-id="51f1c-361">Saiba mais sobre essa abordagem no `BlazorAdmin` projeto no aplicativo de [referência do eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb).</span><span class="sxs-lookup"><span data-stu-id="51f1c-361">Learn more about this approach in the `BlazorAdmin` project in the [eShopOnWeb reference application](https://github.com/dotnet-architecture/eShopOnWeb).</span></span>

<span data-ttu-id="51f1c-362">Um dos benefícios do Blazor WebAssembly spas JavaScript tradicional é que você não precisa manter cópias de seus DTOs (objetos de transferência de dados) sincronizados.</span><span class="sxs-lookup"><span data-stu-id="51f1c-362">One benefit of Blazor WebAssembly over traditional JavaScript SPAs is that you don't need to keep to copies of your data transfer objects(DTOs) synchronized.</span></span> <span data-ttu-id="51f1c-363">Seu Blazor WebAssembly projeto e seu projeto de API Web podem compartilhar o mesmo DTOs em um projeto compartilhado comum.</span><span class="sxs-lookup"><span data-stu-id="51f1c-363">Your Blazor WebAssembly project and your web API project can both share the same DTOs in a common shared project.</span></span> <span data-ttu-id="51f1c-364">Isso elimina parte do conflito envolvido no desenvolvimento de SPAs.</span><span class="sxs-lookup"><span data-stu-id="51f1c-364">This eliminates some of the friction involved in developing SPAs.</span></span>

<span data-ttu-id="51f1c-365">Para obter dados rapidamente de um ponto de extremidade de API, você pode usar o método auxiliar interno, `GetFromJsonAsync` .</span><span class="sxs-lookup"><span data-stu-id="51f1c-365">To quickly get data from an API endpoint, you can use the built-in helper method, `GetFromJsonAsync`.</span></span> <span data-ttu-id="51f1c-366">Há métodos semelhantes para POST, PUT, etc. O seguinte mostra como obter um CatalogItem de um ponto de extremidade de API usando um configurado `HttpClient` em um Blazor WebAssembly aplicativo:</span><span class="sxs-lookup"><span data-stu-id="51f1c-366">There are similar methods for POST, PUT, etc. The following shows how to get a CatalogItem from an API endpoint using a configured `HttpClient` in a Blazor WebAssembly app:</span></span>

```csharp
var item = await _httpClient.GetFromJsonAsync<CatalogItem>($"catalog-items/{id}");
```

<span data-ttu-id="51f1c-367">Depois de obter os dados necessários, você normalmente controlará as alterações localmente.</span><span class="sxs-lookup"><span data-stu-id="51f1c-367">Once you have the data you need, you'll typically track changes locally.</span></span> <span data-ttu-id="51f1c-368">Quando desejar fazer atualizações no armazenamento de dados de back-end, você chamará APIs Web adicionais para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="51f1c-368">When you want to make updates to the backend data store, you'll call additional web APIs for this purpose.</span></span>

<span data-ttu-id="51f1c-369">**Referências – Blazor dados**</span><span class="sxs-lookup"><span data-stu-id="51f1c-369">**References – Blazor Data**</span></span>

- <span data-ttu-id="51f1c-370">Chamar uma API da Web de ASP.NET Core Blazor</span><span class="sxs-lookup"><span data-stu-id="51f1c-370">Call a web API from ASP.NET Core Blazor</span></span>
  <https://docs.microsoft.com/aspnet/core/blazor/call-web-api>

>[!div class="step-by-step"]
><span data-ttu-id="51f1c-371">[Anterior](develop-asp-net-core-mvc-apps.md) 
> [Avançar](test-asp-net-core-mvc-apps.md)</span><span class="sxs-lookup"><span data-stu-id="51f1c-371">[Previous](develop-asp-net-core-mvc-apps.md)
[Next](test-asp-net-core-mvc-apps.md)</span></span>
