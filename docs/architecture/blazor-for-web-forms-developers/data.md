---
title: Gerenciamento e acesso a dados
description: Saiba como acessar e manipular dados no ASP.NET Web Forms e Blazor .
author: csharpfritz
ms.author: jefritz
no-loc:
- Blazor
ms.date: 04/26/2020
ms.openlocfilehash: 8bd326e6952708b2099c3a575d6811990335df17
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267588"
---
# <a name="work-with-data"></a><span data-ttu-id="44946-103">Trabalhar com dados</span><span class="sxs-lookup"><span data-stu-id="44946-103">Work with data</span></span>

<span data-ttu-id="44946-104">Acesso a dados é o backbone de um aplicativo ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="44946-104">Data access is the backbone of an ASP.NET Web Forms app.</span></span> <span data-ttu-id="44946-105">Se você estiver criando formulários para a Web, o que acontecerá com esses dados?</span><span class="sxs-lookup"><span data-stu-id="44946-105">If you're building forms for the web, what happens to that data?</span></span> <span data-ttu-id="44946-106">Com Web Forms, havia várias técnicas de acesso a dados que podem ser usadas para interagir com um banco de dados:</span><span class="sxs-lookup"><span data-stu-id="44946-106">With Web Forms, there were multiple data access techniques you could use to interact with a database:</span></span>

- <span data-ttu-id="44946-107">Fontes de dados</span><span class="sxs-lookup"><span data-stu-id="44946-107">Data Sources</span></span>
- <span data-ttu-id="44946-108">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="44946-108">ADO.NET</span></span>
- <span data-ttu-id="44946-109">Entity Framework</span><span class="sxs-lookup"><span data-stu-id="44946-109">Entity Framework</span></span>

<span data-ttu-id="44946-110">Fontes de dados eram controles que você pode fazer em uma Web Forms página e configurar como outros controles.</span><span class="sxs-lookup"><span data-stu-id="44946-110">Data Sources were controls that you could place on a Web Forms page and configure like other controls.</span></span> <span data-ttu-id="44946-111">O Visual Studio forneceu um conjunto amigável de caixas de diálogo para configurar e associar os controles às suas páginas de Web Forms.</span><span class="sxs-lookup"><span data-stu-id="44946-111">Visual Studio provided a friendly set of dialogs to configure and bind the controls to your Web Forms pages.</span></span> <span data-ttu-id="44946-112">Os desenvolvedores que apreciam uma abordagem de "código baixo" ou "sem código" preferem essa técnica quando Web Forms foi lançado pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="44946-112">Developers who enjoy a "low code" or "no code" approach preferred this technique when Web Forms was first released.</span></span>

![Fontes de dados](media/data/datasources.png)

<span data-ttu-id="44946-114">ADO.NET é a abordagem de nível baixo para interagir com um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="44946-114">ADO.NET is the low-level approach to interacting with a database.</span></span> <span data-ttu-id="44946-115">Seus aplicativos podem criar uma conexão com o banco de dados com comandos, conjuntos de registros e conjuntos de dados para interação.</span><span class="sxs-lookup"><span data-stu-id="44946-115">Your apps could create a connection to the database with Commands, Recordsets, and Datasets for interacting.</span></span> <span data-ttu-id="44946-116">Os resultados podem então ser associados a campos na tela sem muito código.</span><span class="sxs-lookup"><span data-stu-id="44946-116">The results could then be bound to fields on screen without much code.</span></span> <span data-ttu-id="44946-117">A desvantagem dessa abordagem era que cada conjunto de objetos ADO.NET ( `Connection` , `Command` e `Recordset` ) foi associado a bibliotecas fornecidas por um fornecedor de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="44946-117">The drawback of this approach was that each set of ADO.NET objects (`Connection`, `Command`, and `Recordset`) was bound to libraries provided by a database vendor.</span></span> <span data-ttu-id="44946-118">O uso desses componentes tornou o código rígido e difícil de migrar para um banco de dados diferente.</span><span class="sxs-lookup"><span data-stu-id="44946-118">Use of these components made the code rigid and difficult to migrate to a different database.</span></span>

## <a name="entity-framework"></a><span data-ttu-id="44946-119">Entity Framework</span><span class="sxs-lookup"><span data-stu-id="44946-119">Entity Framework</span></span>

<span data-ttu-id="44946-120">Entity Framework (EF) é a estrutura de mapeamento relacional de objeto de software livre mantida pelo .NET Foundation.</span><span class="sxs-lookup"><span data-stu-id="44946-120">Entity Framework (EF) is the open source object-relational mapping framework maintained by the .NET Foundation.</span></span> <span data-ttu-id="44946-121">Lançado inicialmente com .NET Framework, o EF permite gerar código para as conexões de banco de dados, esquemas de armazenamento e interações.</span><span class="sxs-lookup"><span data-stu-id="44946-121">Initially released with .NET Framework, EF allows for generating code for the database connections, storage schemas, and interactions.</span></span> <span data-ttu-id="44946-122">Com essa abstração, você pode se concentrar nas regras de negócios do seu aplicativo e permitir que o banco de dados seja gerenciado por um administrador de banco de dados confiável.</span><span class="sxs-lookup"><span data-stu-id="44946-122">With this abstraction, you can focus on your app's business rules and allow the database to be managed by a trusted database administrator.</span></span> <span data-ttu-id="44946-123">No .NET Core, você pode usar uma versão atualizada do EF chamada EF Core.</span><span class="sxs-lookup"><span data-stu-id="44946-123">In .NET Core, you can use an updated version of EF called EF Core.</span></span> <span data-ttu-id="44946-124">EF Core ajuda a gerar e manter as interações entre seu código e o banco de dados com uma série de comandos que estão disponíveis para você usando a `dotnet ef` ferramenta de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="44946-124">EF Core helps generate and maintain the interactions between your code and the database with a series of commands that are available for you using the `dotnet ef` command-line tool.</span></span> <span data-ttu-id="44946-125">Vamos dar uma olhada em alguns exemplos para ajudá-lo a trabalhar com um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="44946-125">Let's take a look at a few samples to get you working with a database.</span></span>

### <a name="ef-code-first"></a><span data-ttu-id="44946-126">Code First EF</span><span class="sxs-lookup"><span data-stu-id="44946-126">EF Code First</span></span>

<span data-ttu-id="44946-127">Uma maneira rápida de começar a criar suas interações de banco de dados é começar com os objetos de classe com os quais você deseja trabalhar.</span><span class="sxs-lookup"><span data-stu-id="44946-127">A quick way to get started building your database interactions is to start with the class objects you want to work with.</span></span> <span data-ttu-id="44946-128">O EF fornece uma ferramenta para ajudar a gerar o código de banco de dados apropriado para suas classes.</span><span class="sxs-lookup"><span data-stu-id="44946-128">EF provides a tool to help generate the appropriate database code for your classes.</span></span> <span data-ttu-id="44946-129">Essa abordagem é chamada de desenvolvimento "Code First".</span><span class="sxs-lookup"><span data-stu-id="44946-129">This approach is called "Code First" development.</span></span> <span data-ttu-id="44946-130">Considere a seguinte `Product` classe para um aplicativo de vitrine de exemplo que desejamos armazenar em um banco de dados relacional como Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="44946-130">Consider the following `Product` class for a sample storefront app that we want to store in a relational database like Microsoft SQL Server.</span></span>

```csharp
public class Product
{
    public int Id { get; set; }

    [Required]
    public string Name { get; set; }

    [MaxLength(4000)]
    public string Description { get; set; }

    [Range(0, 99999,99)]
    [DataType(DataType.Currency)]
    public decimal Price { get; set; }
}
```

<span data-ttu-id="44946-131">O produto tem uma chave primária e três campos adicionais que seriam criados em nosso banco de dados:</span><span class="sxs-lookup"><span data-stu-id="44946-131">Product has a primary key and three additional fields that would be created in our database:</span></span>  

- <span data-ttu-id="44946-132">O EF identificará a `Id` propriedade como uma chave primária por convenção.</span><span class="sxs-lookup"><span data-stu-id="44946-132">EF will identify the `Id` property as a primary key by convention.</span></span>
- <span data-ttu-id="44946-133">`Name` será armazenado em uma coluna configurada para armazenamento de texto.</span><span class="sxs-lookup"><span data-stu-id="44946-133">`Name` will be stored in a column configured for text storage.</span></span> <span data-ttu-id="44946-134">O `[Required]` atributo decoração dessa propriedade irá adicionar uma `not null` restrição para ajudar a impor esse comportamento declarado da propriedade.</span><span class="sxs-lookup"><span data-stu-id="44946-134">The `[Required]` attribute decorating this property will add a `not null` constraint to help enforce this declared behavior of the property.</span></span>
- <span data-ttu-id="44946-135">`Description` será armazenado em uma coluna configurada para armazenamento de texto e terá um comprimento máximo configurado de 4000 caracteres, conforme determinado pelo `[MaxLength]` atributo.</span><span class="sxs-lookup"><span data-stu-id="44946-135">`Description` will be stored in a column configured for text storage, and have a maximum length configured of 4000 characters as dictated by the `[MaxLength]` attribute.</span></span> <span data-ttu-id="44946-136">O esquema de banco de dados será configurado com uma coluna chamada `MaxLength` usando o tipo de dados `varchar(4000)` .</span><span class="sxs-lookup"><span data-stu-id="44946-136">The database schema will be configured with a column named `MaxLength` using data type `varchar(4000)`.</span></span>
- <span data-ttu-id="44946-137">A `Price` propriedade será armazenada como moeda.</span><span class="sxs-lookup"><span data-stu-id="44946-137">The `Price` property will be stored as currency.</span></span> <span data-ttu-id="44946-138">O `[Range]` atributo irá gerar restrições apropriadas para impedir o armazenamento de dados fora dos valores mínimo e máximo declarados.</span><span class="sxs-lookup"><span data-stu-id="44946-138">The `[Range]` attribute will generate appropriate constraints to prevent data storage outside of the minimum and maximum values declared.</span></span>

<span data-ttu-id="44946-139">Precisamos adicionar essa `Product` classe a uma classe de contexto de banco de dados que define as operações de conexão e conversão com nosso banco de dados.</span><span class="sxs-lookup"><span data-stu-id="44946-139">We need to add this `Product` class to a database context class that defines the connection and translation operations with our database.</span></span>

```csharp
public class MyDbContext : DbContext
{
    public DbSet<Product> Products { get; set; }
}
```

<span data-ttu-id="44946-140">A `MyDbContext` classe fornece uma propriedade que define o acesso e a tradução da `Product` classe.</span><span class="sxs-lookup"><span data-stu-id="44946-140">The `MyDbContext` class provides the one property that defines the access and translation for the `Product` class.</span></span>  <span data-ttu-id="44946-141">Seu aplicativo configura essa classe para interação com o banco de dados usando as seguintes entradas no `Startup` método da classe `ConfigureServices` :</span><span class="sxs-lookup"><span data-stu-id="44946-141">Your application configures this class for interaction with the database using the following entries in the `Startup` class's `ConfigureServices` method:</span></span>

```csharp
services.AddDbContext<MyDbContext>(options =>
    options.UseSqlServer("MY DATABASE CONNECTION STRING"));
```

<span data-ttu-id="44946-142">O código anterior se conectará a um banco de dados SQL Server com a cadeia de conexão especificada.</span><span class="sxs-lookup"><span data-stu-id="44946-142">The preceding code will connect to a SQL Server database with the specified connection string.</span></span> <span data-ttu-id="44946-143">Você pode colocar a cadeia de conexão em seu *appsettings.jsem* arquivo, variáveis de ambiente ou outros locais de armazenamento de configuração e substituir essa cadeia de caracteres inserida adequadamente.</span><span class="sxs-lookup"><span data-stu-id="44946-143">You can place the connection string in your *appsettings.json* file, environment variables, or other configuration storage locations and replace this embedded string appropriately.</span></span>

<span data-ttu-id="44946-144">Em seguida, você pode gerar a tabela de banco de dados apropriada para essa classe usando os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="44946-144">You can then generate the database table appropriate for this class using the following commands:</span></span>

```dotnetcli
dotnet ef migrations add 'Create Product table'
dotnet ef database update
```

<span data-ttu-id="44946-145">O primeiro comando define as alterações que você está fazendo no esquema de banco de dados como uma nova migração do EF chamada `Create Product table` .</span><span class="sxs-lookup"><span data-stu-id="44946-145">The first command defines the changes you're making to the database schema as a new EF Migration called `Create Product table`.</span></span>  <span data-ttu-id="44946-146">Uma migração define como aplicar e remover as novas alterações no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="44946-146">A Migration defines how to apply and remove your new database changes.</span></span>

<span data-ttu-id="44946-147">Depois de aplicado, você tem uma `Product` tabela simples em seu banco de dados e algumas novas classes adicionadas ao projeto que ajudam a gerenciar o esquema de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="44946-147">Once applied, you have a simple `Product` table in your database and some new classes added to the project that help manage the database schema.</span></span>  <span data-ttu-id="44946-148">Você pode encontrar essas classes geradas, por padrão, em uma nova pasta chamada *migrações*.</span><span class="sxs-lookup"><span data-stu-id="44946-148">You can find these generated classes, by default, in a new folder called *Migrations*.</span></span>  <span data-ttu-id="44946-149">Ao fazer alterações na `Product` classe ou adicionar mais classes relacionadas que você gostaria de interagir com o banco de dados, você precisa executar os comandos de linha de comando novamente com um novo nome da migração.</span><span class="sxs-lookup"><span data-stu-id="44946-149">When you make changes to the `Product` class or add more related classes you would like interacting with your database, you need to run the command-line commands again with a new name of the migration.</span></span>  <span data-ttu-id="44946-150">Esse comando gerará outro conjunto de classes de migração para atualizar o esquema de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="44946-150">This command will generate another set of migration classes to update your database schema.</span></span>

### <a name="ef-database-first"></a><span data-ttu-id="44946-151">Database First EF</span><span class="sxs-lookup"><span data-stu-id="44946-151">EF Database First</span></span>

<span data-ttu-id="44946-152">Para bancos de dados existentes, você pode gerar as classes para EF Core usando as ferramentas de linha de comando do .NET.</span><span class="sxs-lookup"><span data-stu-id="44946-152">For existing databases, you can generate the classes for EF Core by using the .NET command-line tools.</span></span> <span data-ttu-id="44946-153">Para Scaffold as classes, use uma variação do seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="44946-153">To scaffold the classes, use a variation of the following command:</span></span>

```dotnetcli
dotnet ef dbcontext scaffold "CONNECTION STRING" Microsoft.EntityFrameworkCore.SqlServer -c MyDbContext -t Product -t Customer
```

<span data-ttu-id="44946-154">O comando anterior se conecta ao banco de dados usando a cadeia de conexão especificada e o `Microsoft.EntityFrameworkCore.SqlServer` provedor.</span><span class="sxs-lookup"><span data-stu-id="44946-154">The preceding command connects to the database using the specified connection string and the `Microsoft.EntityFrameworkCore.SqlServer` provider.</span></span> <span data-ttu-id="44946-155">Uma vez conectado, uma classe de contexto de banco de dados chamada `MyDbContext` é criada.</span><span class="sxs-lookup"><span data-stu-id="44946-155">Once connected, a database context class named `MyDbContext` is created.</span></span> <span data-ttu-id="44946-156">Além disso, as classes de suporte são criadas para as `Product` `Customer` tabelas e que foram especificadas com as `-t` opções.</span><span class="sxs-lookup"><span data-stu-id="44946-156">Additionally, supporting classes are created for the `Product` and `Customer` tables that were specified with the `-t` options.</span></span> <span data-ttu-id="44946-157">Há muitas opções de configuração para esse comando gerar a hierarquia de classe apropriada para seu banco de dados.</span><span class="sxs-lookup"><span data-stu-id="44946-157">There are many configuration options for this command to generate the class hierarchy appropriate for your database.</span></span> <span data-ttu-id="44946-158">Para obter uma referência completa, consulte [a documentação do comando](/ef/core/miscellaneous/cli/dotnet#dotnet-ef-dbcontext-scaffold).</span><span class="sxs-lookup"><span data-stu-id="44946-158">For a complete reference, see [the command's documentation](/ef/core/miscellaneous/cli/dotnet#dotnet-ef-dbcontext-scaffold).</span></span>

<span data-ttu-id="44946-159">Mais informações sobre [EF Core](/ef/core/) podem ser encontradas no site do Microsoft docs.</span><span class="sxs-lookup"><span data-stu-id="44946-159">More information about [EF Core](/ef/core/) can be found on the Microsoft Docs site.</span></span>

## <a name="interact-with-web-services"></a><span data-ttu-id="44946-160">Interagir com os serviços Web</span><span class="sxs-lookup"><span data-stu-id="44946-160">Interact with web services</span></span>

<span data-ttu-id="44946-161">Quando o ASP.NET foi lançado pela primeira vez, os serviços SOAP eram a maneira preferida de servidores Web e clientes de trocar dados.</span><span class="sxs-lookup"><span data-stu-id="44946-161">When ASP.NET was first released, SOAP services were the preferred way for web servers and clients to exchange data.</span></span> <span data-ttu-id="44946-162">Muito mudou desde esse tempo, e as interações preferenciais com serviços mudaram para direcionar interações de cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="44946-162">Much has changed since that time, and the preferred interactions with services have shifted to direct HTTP client interactions.</span></span> <span data-ttu-id="44946-163">Com ASP.NET Core e Blazor , você pode registrar a configuração de seu `HttpClient` no `Startup` método da classe `ConfigureServices` .</span><span class="sxs-lookup"><span data-stu-id="44946-163">With ASP.NET Core and Blazor, you can register the configuration of your `HttpClient` in the `Startup` class's `ConfigureServices` method.</span></span> <span data-ttu-id="44946-164">Use essa configuração quando precisar interagir com o ponto de extremidade HTTP.</span><span class="sxs-lookup"><span data-stu-id="44946-164">Use that configuration when you need to interact with the HTTP endpoint.</span></span> <span data-ttu-id="44946-165">Considere o seguinte código de configuração:</span><span class="sxs-lookup"><span data-stu-id="44946-165">Consider the following configuration code:</span></span>

```csharp
services.AddHttpClient("github", client =>
{
    client.BaseAddress = new Uri("http://api.github.com/");
    // Github API versioning
    client.DefaultRequestHeaders.Add("Accept", "application/vnd.github.v3+json");
    // Github requires a user-agent
    client.DefaultRequestHeaders.Add("User-Agent", "BlazorWebForms-Sample");
});
```

<span data-ttu-id="44946-166">Sempre que você precisar acessar dados do GitHub, crie um cliente com um nome de `github` .</span><span class="sxs-lookup"><span data-stu-id="44946-166">Whenever you need to access data from GitHub, create a client with a name of `github`.</span></span> <span data-ttu-id="44946-167">O cliente é configurado com o endereço base e os cabeçalhos de solicitação são definidos adequadamente.</span><span class="sxs-lookup"><span data-stu-id="44946-167">The client is configured with the base address, and the request headers are set appropriately.</span></span> <span data-ttu-id="44946-168">Insira o `IHttpClientFactory` em seus Blazor componentes com a `@inject` diretiva ou um `[Inject]` atributo em uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="44946-168">Inject the `IHttpClientFactory` into your Blazor components with the `@inject` directive or an `[Inject]` attribute on a property.</span></span> <span data-ttu-id="44946-169">Crie seu cliente nomeado e interaja com os serviços usando a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="44946-169">Create your named client and interact with services using the following syntax:</span></span>

```razor
@inject IHttpClientFactory factory

...

@code {
    protected override async Task OnInitializedAsync()
    {
        var client = factory.CreateClient("github");
        var response = await client.GetAsync("repos/dotnet/docs/issues");
        response.EnsureStatusCode();
        var content = async response.Content.ReadAsStringAsync();
    }
}
```

<span data-ttu-id="44946-170">Esse método retorna a cadeia de caracteres que descreve a coleção de problemas no repositório do GitHub *dotnet/docs* .</span><span class="sxs-lookup"><span data-stu-id="44946-170">This method returns the string describing the collection of issues in the *dotnet/docs* GitHub repository.</span></span> <span data-ttu-id="44946-171">Ele retorna o conteúdo no formato JSON e é desserializado em objetos de problema do GitHub apropriados.</span><span class="sxs-lookup"><span data-stu-id="44946-171">It returns content in JSON format and is deserialized into appropriate GitHub issue objects.</span></span> <span data-ttu-id="44946-172">Há várias maneiras pelas quais você pode configurar o `HttpClientFactory` para entregar `HttpClient` objetos pré-configurados.</span><span class="sxs-lookup"><span data-stu-id="44946-172">There are many ways that you can configure the `HttpClientFactory` to deliver preconfigured `HttpClient` objects.</span></span> <span data-ttu-id="44946-173">Tente configurar várias `HttpClient` instâncias com nomes e pontos de extremidade diferentes para os vários serviços Web com os quais você trabalha.</span><span class="sxs-lookup"><span data-stu-id="44946-173">Try configuring multiple `HttpClient` instances with different names and endpoints for the various web services you work with.</span></span> <span data-ttu-id="44946-174">Essa abordagem fará com que as interações com esses serviços sejam mais fáceis de trabalhar em cada página.</span><span class="sxs-lookup"><span data-stu-id="44946-174">This approach will make your interactions with those services easier to work with on each page.</span></span> <span data-ttu-id="44946-175">Para obter mais detalhes, leia [a documentação do IHttpClientFactory](/aspnet/core/fundamentals/http-requests).</span><span class="sxs-lookup"><span data-stu-id="44946-175">For more details, read [the documentation for the IHttpClientFactory](/aspnet/core/fundamentals/http-requests).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="44946-176">[Anterior](forms-validation.md) 
> [Avançar](middleware.md)</span><span class="sxs-lookup"><span data-stu-id="44946-176">[Previous](forms-validation.md)
[Next](middleware.md)</span></span>
