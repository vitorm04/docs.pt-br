---
title: Usar um servidor de banco de dados em execução como um contêiner
description: Entenda a importância de usar um servidor de banco de dados executando como um contêiner somente para desenvolvimento. Nunca para produção.
ms.date: 01/30/2020
ms.openlocfilehash: 38f77e195b184d57dcad5904674a0025ef6c2bd8
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539393"
---
# <a name="use-a-database-server-running-as-a-container"></a><span data-ttu-id="04c57-104">Usar um servidor de banco de dados em execução como um contêiner</span><span class="sxs-lookup"><span data-stu-id="04c57-104">Use a database server running as a container</span></span>

<span data-ttu-id="04c57-105">Você pode ter seus bancos de dados (SQL Server, PostgreSQL, MySQL etc.) em servidores autônomo regulares, em clusters locais ou em serviços de PaaS na nuvem como o BD SQL do Azure.</span><span class="sxs-lookup"><span data-stu-id="04c57-105">You can have your databases (SQL Server, PostgreSQL, MySQL, etc.) on regular standalone servers, in on-premises clusters, or in PaaS services in the cloud like Azure SQL DB.</span></span> <span data-ttu-id="04c57-106">No entanto, para ambientes de desenvolvimento e teste, ter seus bancos de dados em execução como contêineres é conveniente, porque você não tem nenhuma dependência externa e simplesmente executar o `docker-compose up` comando inicia todo o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="04c57-106">However, for development and test environments, having your databases running as containers is convenient, because you don't have any external dependency and simply running the `docker-compose up` command starts the whole application.</span></span> <span data-ttu-id="04c57-107">Ter esses bancos de dados como contêineres também é excelente para testes de integração, porque o banco de dados é iniciado no contêiner e sempre é preenchido com os dados de exemplo, assim, os testes podem ser mais previsíveis.</span><span class="sxs-lookup"><span data-stu-id="04c57-107">Having those databases as containers is also great for integration tests, because the database is started in the container and is always populated with the same sample data, so tests can be more predictable.</span></span>

## <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a><span data-ttu-id="04c57-108">SQL Server em execução como um contêiner com um banco de dados relacionado a microsserviço</span><span class="sxs-lookup"><span data-stu-id="04c57-108">SQL Server running as a container with a microservice-related database</span></span>

<span data-ttu-id="04c57-109">No eShopOnContainers, há um contêiner chamado `sqldata` , conforme definido no arquivo [Docker-Compose. yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) , que executa um SQL Server para a instância do Linux com os bancos de dados SQL para todos os microserviços que precisam de um.</span><span class="sxs-lookup"><span data-stu-id="04c57-109">In eShopOnContainers, there's a container named `sqldata`, as defined in the [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) file, that runs a SQL Server for Linux instance with the SQL databases for all microservices that need one.</span></span>

<span data-ttu-id="04c57-110">Um ponto importante nos microserviços é que cada Microservice possui seus dados relacionados, portanto, ele deve ter seu próprio banco.</span><span class="sxs-lookup"><span data-stu-id="04c57-110">A key point in microservices is that each microservice owns its related data, so it should have its own database.</span></span> <span data-ttu-id="04c57-111">No entanto, os bancos de dados podem ser em qualquer lugar.</span><span class="sxs-lookup"><span data-stu-id="04c57-111">However, the databases can be anywhere.</span></span> <span data-ttu-id="04c57-112">Nesse caso, eles estão todos no mesmo contêiner para manter os requisitos de memória do Docker o mais baixo possível.</span><span class="sxs-lookup"><span data-stu-id="04c57-112">In this case, they are all in the same container to keep Docker memory requirements as low as possible.</span></span> <span data-ttu-id="04c57-113">Tenha em mente que essa é uma solução boa o suficiente para o desenvolvimento e, talvez, teste, mas não para produção.</span><span class="sxs-lookup"><span data-stu-id="04c57-113">Keep in mind that this is a good-enough solution for development and, perhaps, testing but not for production.</span></span>

<span data-ttu-id="04c57-114">O contêiner do SQL Server no aplicativo de exemplo é configurado com o seguinte código YAML no arquivo docker-compose.yml, que é executado quando você executa o `docker-compose up`.</span><span class="sxs-lookup"><span data-stu-id="04c57-114">The SQL Server container in the sample application is configured with the following YAML code in the docker-compose.yml file, which is executed when you run `docker-compose up`.</span></span> <span data-ttu-id="04c57-115">Observe que o código YAML consolidou informações de configuração do arquivo genérico docker-compose.yml e o arquivo docker-compose.override.yml.</span><span class="sxs-lookup"><span data-stu-id="04c57-115">Note that the YAML code has consolidated configuration information from the generic docker-compose.yml file and the docker-compose.override.yml file.</span></span> <span data-ttu-id="04c57-116">(Normalmente, separe as configurações de ambiente com as informações de base ou estáticas relacionada à imagem do SQL Server.)</span><span class="sxs-lookup"><span data-stu-id="04c57-116">(Usually you would separate the environment settings from the base or static information related to the SQL Server image.)</span></span>

```yml
  sqldata:
    image: mcr.microsoft.com/mssql/server:2017-latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"
```

<span data-ttu-id="04c57-117">De maneira semelhante, em vez de usar `docker-compose`, o seguinte comando `docker run` pode ser executado naquele contêiner:</span><span class="sxs-lookup"><span data-stu-id="04c57-117">In a similar way, instead of using `docker-compose`, the following `docker run` command can run that container:</span></span>

```powershell
docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Pass@word' -p 5433:1433 -d mcr.microsoft.com/mssql/server:2017-latest
```

<span data-ttu-id="04c57-118">No entanto, se você estiver implantando um aplicativo multicontêiner, como eShopOnContainers, será mais conveniente usar o comando `docker-compose up` para que ele implante todos os contêineres necessários para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="04c57-118">However, if you are deploying a multi-container application like eShopOnContainers, it is more convenient to use the `docker-compose up` command so that it deploys all the required containers for the application.</span></span>

<span data-ttu-id="04c57-119">Quando você inicia esse contêiner do SQL Server pela primeira vez, o contêiner inicializa o SQL Server com a senha que você fornece.</span><span class="sxs-lookup"><span data-stu-id="04c57-119">When you start this SQL Server container for the first time, the container initializes SQL Server with the password that you provide.</span></span> <span data-ttu-id="04c57-120">Depois que o SQL Server está em execução como um contêiner, você pode atualizar o banco de dados conectando por meio de qualquer conexão de SQL normal, como SQL Server Management Studio, Visual Studio ou código C\#.</span><span class="sxs-lookup"><span data-stu-id="04c57-120">Once SQL Server is running as a container, you can update the database by connecting through any regular SQL connection, such as from SQL Server Management Studio, Visual Studio, or C\# code.</span></span>

<span data-ttu-id="04c57-121">O aplicativo eShopOnContainers inicializa cada banco de dados de microsserviço usando dados de exemplo propagando-os com os dados na inicialização, conforme explica a seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="04c57-121">The eShopOnContainers application initializes each microservice database with sample data by seeding it with data on startup, as explained in the following section.</span></span>

<span data-ttu-id="04c57-122">Ter o SQL Server em execução como um contêiner não é apenas útil para uma demonstração em que você talvez não tenha acesso a uma instância do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="04c57-122">Having SQL Server running as a container is not just useful for a demo where you might not have access to an instance of SQL Server.</span></span> <span data-ttu-id="04c57-123">Como mencionado, também é ótimo para ambientes de desenvolvimento e teste para que você possa executar facilmente testes de integração começando com uma imagem limpa do SQL Server e dados conhecidos propagando novos dados de exemplo.</span><span class="sxs-lookup"><span data-stu-id="04c57-123">As noted, it is also great for development and testing environments so that you can easily run integration tests starting from a clean SQL Server image and known data by seeding new sample data.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="04c57-124">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="04c57-124">Additional resources</span></span>

- <span data-ttu-id="04c57-125">**Executar a imagem do Docker SQL Server no Linux, Mac ou Windows** </span><span class="sxs-lookup"><span data-stu-id="04c57-125">**Run the SQL Server Docker image on Linux, Mac, or Windows** </span></span>\
  <https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker>

- <span data-ttu-id="04c57-126">**Conectar e consultar SQL Server em Linux com o sqlcmd** </span><span class="sxs-lookup"><span data-stu-id="04c57-126">**Connect and query SQL Server on Linux with sqlcmd** </span></span>\
  <https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd>

## <a name="seeding-with-test-data-on-web-application-startup"></a><span data-ttu-id="04c57-127">Propagação com os dados de teste na inicialização do aplicativo Web</span><span class="sxs-lookup"><span data-stu-id="04c57-127">Seeding with test data on Web application startup</span></span>

<span data-ttu-id="04c57-128">Para adicionar dados ao banco de dado quando o aplicativo é iniciado, você pode adicionar um código como o seguinte ao `Main` método na `Program` classe do projeto de API Web:</span><span class="sxs-lookup"><span data-stu-id="04c57-128">To add data to the database when the application starts up, you can add code like the following to the `Main` method in the `Program` class of the Web API project:</span></span>

```csharp
public static int Main(string[] args)
{
    var configuration = GetConfiguration();

    Log.Logger = CreateSerilogLogger(configuration);

    try
    {
        Log.Information("Configuring web host ({ApplicationContext})...", AppName);
        var host = CreateHostBuilder(configuration, args);

        Log.Information("Applying migrations ({ApplicationContext})...", AppName);
        host.MigrateDbContext<CatalogContext>((context, services) =>
        {
            var env = services.GetService<IWebHostEnvironment>();
            var settings = services.GetService<IOptions<CatalogSettings>>();
            var logger = services.GetService<ILogger<CatalogContextSeed>>();

            new CatalogContextSeed()
                .SeedAsync(context, env, settings, logger)
                .Wait();
        })
        .MigrateDbContext<IntegrationEventLogContext>((_, __) => { });

        Log.Information("Starting web host ({ApplicationContext})...", AppName);
        host.Run();

        return 0;
    }
    catch (Exception ex)
    {
        Log.Fatal(ex, "Program terminated unexpectedly ({ApplicationContext})!", AppName);
        return 1;
    }
    finally
    {
        Log.CloseAndFlush();
    }
}
```

<span data-ttu-id="04c57-129">Há uma limitação importante ao aplicar migrações e propagar um banco de dados durante a inicialização do contêiner.</span><span class="sxs-lookup"><span data-stu-id="04c57-129">There's an important caveat when applying migrations and seeding a database during container startup.</span></span> <span data-ttu-id="04c57-130">Como o servidor de banco de dados pode não estar disponível por qualquer motivo, você deve lidar com novas tentativas enquanto aguarda o servidor estar disponível.</span><span class="sxs-lookup"><span data-stu-id="04c57-130">Since the database server might not be available for whatever reason, you must handle retries while waiting for the server to be available.</span></span> <span data-ttu-id="04c57-131">Essa lógica de repetição é tratada pelo `MigrateDbContext()` método de extensão, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="04c57-131">This retry logic is handled by the `MigrateDbContext()` extension method, as shown in the following code:</span></span>

```csharp
public static IWebHost MigrateDbContext<TContext>(
    this IWebHost host,
    Action<TContext,
    IServiceProvider> seeder)
      where TContext : DbContext
{
    var underK8s = host.IsInKubernetes();

    using (var scope = host.Services.CreateScope())
    {
        var services = scope.ServiceProvider;

        var logger = services.GetRequiredService<ILogger<TContext>>();

        var context = services.GetService<TContext>();

        try
        {
            logger.LogInformation("Migrating database associated with context {DbContextName}", typeof(TContext).Name);

            if (underK8s)
            {
                InvokeSeeder(seeder, context, services);
            }
            else
            {
                var retry = Policy.Handle<SqlException>()
                    .WaitAndRetry(new TimeSpan[]
                    {
                    TimeSpan.FromSeconds(3),
                    TimeSpan.FromSeconds(5),
                    TimeSpan.FromSeconds(8),
                    });

                //if the sql server container is not created on run docker compose this
                //migration can't fail for network related exception. The retry options for DbContext only
                //apply to transient exceptions
                // Note that this is NOT applied when running some orchestrators (let the orchestrator to recreate the failing service)
                retry.Execute(() => InvokeSeeder(seeder, context, services));
            }

            logger.LogInformation("Migrated database associated with context {DbContextName}", typeof(TContext).Name);
        }
        catch (Exception ex)
        {
            logger.LogError(ex, "An error occurred while migrating the database used on context {DbContextName}", typeof(TContext).Name);
            if (underK8s)
            {
                throw;          // Rethrow under k8s because we rely on k8s to re-run the pod
            }
        }
    }

    return host;
}
```

<span data-ttu-id="04c57-132">O código a seguir na classe CatalogContextSeed personalizada preenche os dados.</span><span class="sxs-lookup"><span data-stu-id="04c57-132">The following code in the custom CatalogContextSeed class populates the data.</span></span>

```csharp
public class CatalogContextSeed
{
    public static async Task SeedAsync(IApplicationBuilder applicationBuilder)
    {
        var context = (CatalogContext)applicationBuilder
            .ApplicationServices.GetService(typeof(CatalogContext));
        using (context)
        {
            context.Database.Migrate();
            if (!context.CatalogBrands.Any())
            {
                context.CatalogBrands.AddRange(
                    GetPreconfiguredCatalogBrands());
                await context.SaveChangesAsync();
            }
            if (!context.CatalogTypes.Any())
            {
                context.CatalogTypes.AddRange(
                    GetPreconfiguredCatalogTypes());
                await context.SaveChangesAsync();
            }
        }
    }

    static IEnumerable<CatalogBrand> GetPreconfiguredCatalogBrands()
    {
        return new List<CatalogBrand>()
       {
           new CatalogBrand() { Brand = "Azure"},
           new CatalogBrand() { Brand = ".NET" },
           new CatalogBrand() { Brand = "Visual Studio" },
           new CatalogBrand() { Brand = "SQL Server" }
       };
    }

    static IEnumerable<CatalogType> GetPreconfiguredCatalogTypes()
    {
        return new List<CatalogType>()
        {
            new CatalogType() { Type = "Mug"},
            new CatalogType() { Type = "T-Shirt" },
            new CatalogType() { Type = "Backpack" },
            new CatalogType() { Type = "USB Memory Stick" }
        };
    }
}
```

<span data-ttu-id="04c57-133">Quando você executa testes de integração, é útil ter uma maneira de gerar dados consistentes com seus testes de integração.</span><span class="sxs-lookup"><span data-stu-id="04c57-133">When you run integration tests, having a way to generate data consistent with your integration tests is useful.</span></span> <span data-ttu-id="04c57-134">Poder criar tudo do zero, incluindo uma instância do SQL Server em execução em um contêiner, é ótimo para ambientes de teste.</span><span class="sxs-lookup"><span data-stu-id="04c57-134">Being able to create everything from scratch, including an instance of SQL Server running on a container, is great for test environments.</span></span>

## <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a><span data-ttu-id="04c57-135">Banco de dados InMemory do EF Core versus SQL Server em execução como um contêiner</span><span class="sxs-lookup"><span data-stu-id="04c57-135">EF Core InMemory database versus SQL Server running as a container</span></span>

<span data-ttu-id="04c57-136">Outra boa opção para executar testes é usar o provedor de banco de dados do Entity Framework InMemory.</span><span class="sxs-lookup"><span data-stu-id="04c57-136">Another good choice when running tests is to use the Entity Framework InMemory database provider.</span></span> <span data-ttu-id="04c57-137">Você pode especificar essa configuração no método ConfigureServices da classe de Inicialização em seu projeto de API da Web:</span><span class="sxs-lookup"><span data-stu-id="04c57-137">You can specify that configuration in the ConfigureServices method of the Startup class in your Web API project:</span></span>

```csharp
public class Startup
{
    // Other Startup code ...
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddSingleton<IConfiguration>(Configuration);
        // DbContext using an InMemory database provider
        services.AddDbContext<CatalogContext>(opt => opt.UseInMemoryDatabase());
        //(Alternative: DbContext using a SQL Server provider
        //services.AddDbContext<CatalogContext>(c =>
        //{
            // c.UseSqlServer(Configuration["ConnectionString"]);
            //
        //});
    }

    // Other Startup code ...
}
```

<span data-ttu-id="04c57-138">No entanto, há um problema importante.</span><span class="sxs-lookup"><span data-stu-id="04c57-138">There is an important catch, though.</span></span> <span data-ttu-id="04c57-139">O banco de dados na memória não é compatível com muitas restrições específicas de um determinado banco de dados.</span><span class="sxs-lookup"><span data-stu-id="04c57-139">The in-memory database does not support many constraints that are specific to a particular database.</span></span> <span data-ttu-id="04c57-140">Por exemplo, você pode adicionar um índice exclusivo em uma coluna em seu modelo EF Core e escrever um teste com relação ao seu banco de dados na memória para verificar se ele não permite que você adicione um valor duplicado.</span><span class="sxs-lookup"><span data-stu-id="04c57-140">For instance, you might add a unique index on a column in your EF Core model and write a test against your in-memory database to check that it does not let you add a duplicate value.</span></span> <span data-ttu-id="04c57-141">Porém, quando você estiver usando o banco de dados na memória, não poderá manipular índices exclusivos em uma coluna.</span><span class="sxs-lookup"><span data-stu-id="04c57-141">But when you are using the in-memory database, you cannot handle unique indexes on a column.</span></span> <span data-ttu-id="04c57-142">Portanto, o banco de dados em memória não se comporta exatamente como um banco de dados real do SQL Server: ele não emula restrições específicas do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="04c57-142">Therefore, the in-memory database does not behave exactly the same as a real SQL Server database—it does not emulate database-specific constraints.</span></span>

<span data-ttu-id="04c57-143">Mesmo assim, um banco de dados na memória é útil para testes e protótipos.</span><span class="sxs-lookup"><span data-stu-id="04c57-143">Even so, an in-memory database is still useful for testing and prototyping.</span></span> <span data-ttu-id="04c57-144">Porém, se você quiser criar testes de integração precisos que levem em conta o comportamento de uma implementação do banco de dados específica, você precisará usar um banco de dados real como o SQL Server.</span><span class="sxs-lookup"><span data-stu-id="04c57-144">But if you want to create accurate integration tests that take into account the behavior of a specific database implementation, you need to use a real database like SQL Server.</span></span> <span data-ttu-id="04c57-145">Para essa finalidade, executar o SQL Server em um contêiner é uma ótima escolha e mais preciso do que o provedor de banco de dados do EF Core InMemory.</span><span class="sxs-lookup"><span data-stu-id="04c57-145">For that purpose, running SQL Server in a container is a great choice and more accurate than the EF Core InMemory database provider.</span></span>

## <a name="using-a-redis-cache-service-running-in-a-container"></a><span data-ttu-id="04c57-146">Usando um Serviço de Cache Redis em execução em um contêiner</span><span class="sxs-lookup"><span data-stu-id="04c57-146">Using a Redis cache service running in a container</span></span>

<span data-ttu-id="04c57-147">Você pode executar o Redis em um contêiner, especialmente para desenvolvimento e teste e para cenários de prova de conceito.</span><span class="sxs-lookup"><span data-stu-id="04c57-147">You can run Redis on a container, especially for development and testing and for proof-of-concept scenarios.</span></span> <span data-ttu-id="04c57-148">Este cenário é conveniente, porque você pode ter todas as suas dependências em execução em contêineres, não apenas para os computadores de desenvolvimento locais, mas para seus ambientes de teste em seus pipelines CI/CD.</span><span class="sxs-lookup"><span data-stu-id="04c57-148">This scenario is convenient, because you can have all your dependencies running on containers—not just for your local development machines, but for your testing environments in your CI/CD pipelines.</span></span>

<span data-ttu-id="04c57-149">No entanto, quando você executa o Redis em produção, é melhor procurar uma solução de alta disponibilidade, como o Redis Microsoft Azure, que é executado como uma PaaS (plataforma como serviço).</span><span class="sxs-lookup"><span data-stu-id="04c57-149">However, when you run Redis in production, it is better to look for a high-availability solution like Redis Microsoft Azure, which runs as a PaaS (Platform as a Service).</span></span> <span data-ttu-id="04c57-150">No seu código, basta alterar suas cadeias de caracteres de conexão.</span><span class="sxs-lookup"><span data-stu-id="04c57-150">In your code, you just need to change your connection strings.</span></span>

<span data-ttu-id="04c57-151">O Redis fornece uma imagem do Docker com Redis.</span><span class="sxs-lookup"><span data-stu-id="04c57-151">Redis provides a Docker image with Redis.</span></span> <span data-ttu-id="04c57-152">Essa imagem está disponível no Hub do Docker nesta URL:</span><span class="sxs-lookup"><span data-stu-id="04c57-152">That image is available from Docker Hub at this URL:</span></span>

<https://hub.docker.com/_/redis/>

<span data-ttu-id="04c57-153">Você pode executar diretamente um contêiner do Docker Redis executando o seguinte comando da CLI do Docker em seu prompt de comando:</span><span class="sxs-lookup"><span data-stu-id="04c57-153">You can directly run a Docker Redis container by executing the following Docker CLI command in your command prompt:</span></span>

```console
docker run --name some-redis -d redis
```

<span data-ttu-id="04c57-154">A imagem do Redis inclui expose:6379 (a porta usada pelo Redis), de modo que a vinculação de contêiner padrão o tornará automaticamente disponível aos contêineres vinculados.</span><span class="sxs-lookup"><span data-stu-id="04c57-154">The Redis image includes expose:6379 (the port used by Redis), so standard container linking will make it automatically available to the linked containers.</span></span>

<span data-ttu-id="04c57-155">No eShopOnContainers, o `basket-api` Microservice usa um cache Redis em execução como um contêiner.</span><span class="sxs-lookup"><span data-stu-id="04c57-155">In eShopOnContainers, the `basket-api` microservice uses a Redis cache running as a container.</span></span> <span data-ttu-id="04c57-156">Esse `basketdata` contêiner é definido como parte do arquivo *Docker-Compose. yml* de vários contêineres, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="04c57-156">That `basketdata` container is defined as part of the multi-container *docker-compose.yml* file, as shown in the following example:</span></span>

```yml
#docker-compose.yml file
#...
  basketdata:
    image: redis
    expose:
      - "6379"
```

<span data-ttu-id="04c57-157">Esse código no Docker-Compose. yml define um contêiner nomeado `basketdata` com base na imagem do Redis e publicando a porta 6379 internamente.</span><span class="sxs-lookup"><span data-stu-id="04c57-157">This code in the docker-compose.yml defines a container named `basketdata` based on the redis image and publishing the port 6379 internally.</span></span> <span data-ttu-id="04c57-158">Isso significa que ele só poderá ser acessado de outros contêineres em execução no host do Docker.</span><span class="sxs-lookup"><span data-stu-id="04c57-158">This means that it will only be accessible from other containers running within the Docker host.</span></span>

<span data-ttu-id="04c57-159">Por fim, no arquivo *Docker-Compose. Override. yml* , o `basket-api` Microservice para o exemplo eShopOnContainers define a cadeia de conexão a ser usada para esse contêiner Redis:</span><span class="sxs-lookup"><span data-stu-id="04c57-159">Finally, in the *docker-compose.override.yml* file, the `basket-api` microservice for the eShopOnContainers sample defines the connection string to use for that Redis container:</span></span>

```yml
  basket-api:
    environment:
      # Other data ...
      - ConnectionString=basketdata
      - EventBusConnection=rabbitmq
```

<span data-ttu-id="04c57-160">Como mencionado anteriormente, o nome do microserviço `basketdata` é resolvido pelo DNS da rede interna do Docker.</span><span class="sxs-lookup"><span data-stu-id="04c57-160">As mentioned before, the name of the microservice `basketdata` is resolved by Docker's internal network DNS.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="04c57-161">[Anterior](multi-container-applications-docker-compose.md) 
> [Avançar](integration-event-based-microservice-communications.md)</span><span class="sxs-lookup"><span data-stu-id="04c57-161">[Previous](multi-container-applications-docker-compose.md)
[Next](integration-event-based-microservice-communications.md)</span></span>
