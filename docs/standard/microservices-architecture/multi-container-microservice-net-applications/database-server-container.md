---
title: "Usando um servidor de banco de dados em execução como um contêiner"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Usando um servidor de banco de dados em execução como um contêiner"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 7e5f33c4e7edf9d0d4551c5125976fcb8fda392f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="using-a-database-server-running-as-a-container"></a><span data-ttu-id="3ca3b-104">Usando um servidor de banco de dados em execução como um contêiner</span><span class="sxs-lookup"><span data-stu-id="3ca3b-104">Using a database server running as a container</span></span>

<span data-ttu-id="3ca3b-105">Você pode ter seus bancos de dados (SQL Server, PostgreSQL, MySQL, etc.) em servidores autônomo regular, em clusters locais ou em serviços de PaaS na nuvem como banco de dados de SQL do Azure.</span><span class="sxs-lookup"><span data-stu-id="3ca3b-105">You can have your databases (SQL Server, PostgreSQL, MySQL, etc.) on regular standalone servers, in on-premises clusters, or in PaaS services in the cloud like Azure SQL DB.</span></span> <span data-ttu-id="3ca3b-106">No entanto, para ambientes de desenvolvimento e teste, ter seus bancos de dados em execução como contêineres é simplesmente em execução e conveniente, porque você não tem nenhuma dependência externa, a compor docker comando inicia o aplicativo inteiro.</span><span class="sxs-lookup"><span data-stu-id="3ca3b-106">However, for development and test environments, having your databases running as containers is convenient, because you do not have any external dependency, and simply running the docker-compose command starts the whole application.</span></span> <span data-ttu-id="3ca3b-107">Ter esses bancos de dados como contêineres também é excelente para testes de integração, porque o banco de dados é iniciado no contêiner e sempre é preenchido com dados de exemplo, para que testes possam ser mais previsíveis.</span><span class="sxs-lookup"><span data-stu-id="3ca3b-107">Having those databases as containers is also great for integration tests, because the database is started in the container and is always populated with the same sample data, so tests can be more predictable.</span></span>

### <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a><span data-ttu-id="3ca3b-108">SQL Server em execução como um contêiner com um banco de dados relacionados de microsserviço</span><span class="sxs-lookup"><span data-stu-id="3ca3b-108">SQL Server running as a container with a microservice-related database</span></span>

<span data-ttu-id="3ca3b-109">EShopOnContainers, há um contêiner denominado sql.data definido no [docker compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) arquivos que executa o SQL Server para Linux com todos os SQL Server bancos de dados necessários para o microservices.</span><span class="sxs-lookup"><span data-stu-id="3ca3b-109">In eShopOnContainers, there is a container named sql.data defined in the [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) file that runs SQL Server for Linux with all the SQL Server databases needed for the microservices.</span></span> <span data-ttu-id="3ca3b-110">(Você também pode ter um contêiner do SQL Server para cada banco de dados, mas que exigem mais memória atribuída ao Docker). O ponto importante microservices é que cada microsserviço possui seus dados relacionados, portanto, seu banco de dados SQL relacionado nesse caso.</span><span class="sxs-lookup"><span data-stu-id="3ca3b-110">(You could also have one SQL Server container for each database, but that would require more memory assigned to Docker.) The important point in microservices is that each microservice owns its related data, therefore its related SQL database in this case.</span></span> <span data-ttu-id="3ca3b-111">Mas os bancos de dados podem estar em qualquer lugar.</span><span class="sxs-lookup"><span data-stu-id="3ca3b-111">But the databases can be anywhere.</span></span>

<span data-ttu-id="3ca3b-112">Docker de contêiner no aplicativo de amostra está configurado com o código a seguir YAML no arquivo compose.yml docker, que é executado quando você executa o SQL Server-compor backup.</span><span class="sxs-lookup"><span data-stu-id="3ca3b-112">The SQL Server container in the sample application is configured with the following YAML code in the docker-compose.yml file, which is executed when you run docker-compose up.</span></span> <span data-ttu-id="3ca3b-113">Observe que o código YAML consolidou informações de configuração de arquivo genérico de compose.yml de docker e o arquivo de docker compose.override.yml.</span><span class="sxs-lookup"><span data-stu-id="3ca3b-113">Note that the YAML code has consolidated configuration information from the generic docker-compose.yml file and the docker-compose.override.yml file.</span></span> <span data-ttu-id="3ca3b-114">(Normalmente separe as configurações de ambiente com as informações de base ou estáticas relacionada à imagem do SQL Server.)</span><span class="sxs-lookup"><span data-stu-id="3ca3b-114">(Usually you would separate the environment settings from the base or static information related to the SQL Server image.)</span></span>

```yml
sql.data:
  image: microsoft/mssql-server-linux
  environment:
    - SA_PASSWORD=your@password
    - ACCEPT_EULA=Y
  ports:
    - "5434:1433"
```

<span data-ttu-id="3ca3b-115">O seguinte comando docker run pode executar esse contêiner:</span><span class="sxs-lookup"><span data-stu-id="3ca3b-115">The following docker run command can run that container:</span></span>

```
  docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD= your@password' -p 1433:1433 -d microsoft/mssql-server-linux
```

<span data-ttu-id="3ca3b-116">No entanto, se você estiver implantando um aplicativo de multi-contêiner como eShopOnContainers, é mais conveniente usar o docker-compor o comando para que ele implanta todos os contêineres necessários para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3ca3b-116">However, if you are deploying a multi-container application like eShopOnContainers, it is more convenient to use the docker-compose up command so that it deploys all the required containers for the application.</span></span>

<span data-ttu-id="3ca3b-117">Quando você inicia esse contêiner do SQL Server pela primeira vez, o contêiner inicia o SQL Server com a senha que você fornecer.</span><span class="sxs-lookup"><span data-stu-id="3ca3b-117">When you start this SQL Server container for the first time, the container initializes SQL Server with the password that you provide.</span></span> <span data-ttu-id="3ca3b-118">Depois que o SQL Server está em execução como um contêiner, você pode atualizar o banco de dados conectando através de qualquer conexão de SQL regular, como SQL Server Management Studio, o Visual Studio ou o C\# código.</span><span class="sxs-lookup"><span data-stu-id="3ca3b-118">Once SQL Server is running as a container, you can update the database by connecting through any regular SQL connection, such as from SQL Server Management Studio, Visual Studio, or C\# code.</span></span>

<span data-ttu-id="3ca3b-119">O aplicativo eShopOnContainers inicializa cada banco de dados com dados de exemplo microsserviço propagá-lo com dados na inicialização, conforme explicado na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="3ca3b-119">The eShopOnContainers application initializes each microservice database with sample data by seeding it with data on startup, as explained in the following section.</span></span>

<span data-ttu-id="3ca3b-120">Com o SQL Server em execução como um contêiner não é útil apenas para uma demonstração em que talvez você não tenha acesso a uma instância do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3ca3b-120">Having SQL Server running as a container is not just useful for a demo where you might not have access to an instance of SQL Server.</span></span> <span data-ttu-id="3ca3b-121">Como mencionado, também é ideal para ambientes de desenvolvimento e teste para que você pode executar testes de integração a partir de uma imagem do SQL Server limpar facilmente e dados conhecidos, propagando novos dados de exemplo.</span><span class="sxs-lookup"><span data-stu-id="3ca3b-121">As noted, it is also great for development and testing environments so that you can easily run integration tests starting from a clean SQL Server image and known data by seeding new sample data.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="3ca3b-122">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="3ca3b-122">Additional resources</span></span>

-   <span data-ttu-id="3ca3b-123">**Executar a imagem do Docker do SQL Server no Linux, Mac ou Windows**
    [*https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker*](https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker)</span><span class="sxs-lookup"><span data-stu-id="3ca3b-123">**Run the SQL Server Docker image on Linux, Mac, or Windows**
[*https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker*](https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker)</span></span>

-   <span data-ttu-id="3ca3b-124">**Conectar e consultar o SQL Server no Linux com sqlcmd**
    [*https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd*](https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd)</span><span class="sxs-lookup"><span data-stu-id="3ca3b-124">**Connect and query SQL Server on Linux with sqlcmd**
[*https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd*](https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd)</span></span>

### <a name="seeding-with-test-data-on-web-application-startup"></a><span data-ttu-id="3ca3b-125">A propagação com dados de teste na inicialização do aplicativo Web</span><span class="sxs-lookup"><span data-stu-id="3ca3b-125">Seeding with test data on Web application startup</span></span>

<span data-ttu-id="3ca3b-126">Para adicionar dados ao banco de dados quando o aplicativo é iniciado, você pode adicionar código como o seguinte ao configurar método na classe de inicialização do projeto de API da Web:</span><span class="sxs-lookup"><span data-stu-id="3ca3b-126">To add data to the database when the application starts up, you can add code like the following to the Configure method in the Startup class of the Web API project:</span></span>

```csharp
public class Startup
{
    // Other Startup code...
    public void Configure(IApplicationBuilder app,
        IHostingEnvironment env,
        ILoggerFactory loggerFactory)
    {
        // Other Configure code...
        // Seed data through our custom class
        CatalogContextSeed.SeedAsync(app)
            .Wait();
        // Other Configure code...
    }
}
```

<span data-ttu-id="3ca3b-127">O código a seguir na classe CatalogContextSeed personalizado preenche os dados.</span><span class="sxs-lookup"><span data-stu-id="3ca3b-127">The following code in the custom CatalogContextSeed class populates the data.</span></span>

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

<span data-ttu-id="3ca3b-128">Quando você executa testes de integração, é útil ter uma maneira de gerar dados consistentes com os testes de integração.</span><span class="sxs-lookup"><span data-stu-id="3ca3b-128">When you run integration tests, having a way to generate data consistent with your integration tests is useful.</span></span> <span data-ttu-id="3ca3b-129">Capacidade de criar tudo do zero, incluindo uma instância do SQL Server em execução em um contêiner, é ideal para ambientes de teste.</span><span class="sxs-lookup"><span data-stu-id="3ca3b-129">Being able to create everything from scratch, including an instance of SQL Server running on a container, is great for test environments.</span></span>

### <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a><span data-ttu-id="3ca3b-130">Banco de dados do EF InMemory Core em comparação com o SQL Server em execução como um contêiner</span><span class="sxs-lookup"><span data-stu-id="3ca3b-130">EF Core InMemory database versus SQL Server running as a container</span></span>

<span data-ttu-id="3ca3b-131">Outra boa opção para a execução de testes é usar o provedor de banco de dados do Entity Framework InMemory.</span><span class="sxs-lookup"><span data-stu-id="3ca3b-131">Another good choice when running tests is to use the Entity Framework InMemory database provider.</span></span> <span data-ttu-id="3ca3b-132">Você pode especificar que a configuração no método ConfigureServices da classe de inicialização em seu projeto de API da Web:</span><span class="sxs-lookup"><span data-stu-id="3ca3b-132">You can specify that configuration in the ConfigureServices method of the Startup class in your Web API project:</span></span>

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

<span data-ttu-id="3ca3b-133">Há um problema importante, embora.</span><span class="sxs-lookup"><span data-stu-id="3ca3b-133">There is an important catch, though.</span></span> <span data-ttu-id="3ca3b-134">O banco de dados na memória não oferece suporte a muitas restrições que são específicas para um determinado banco de dados.</span><span class="sxs-lookup"><span data-stu-id="3ca3b-134">The in-memory database does not support many constraints that are specific to a particular database.</span></span> <span data-ttu-id="3ca3b-135">Por exemplo, você pode adicionar um índice exclusivo em uma coluna em seu modelo EF principal e um teste de gravação no banco de dados na memória para verificar se ele não permite que você adicionar um valor duplicado.</span><span class="sxs-lookup"><span data-stu-id="3ca3b-135">For instance, you might add a unique index on a column in your EF Core model and write a test against your in-memory database to check that it does not let you add a duplicate value.</span></span> <span data-ttu-id="3ca3b-136">Mas quando você estiver usando o banco de dados na memória, você não pode manipular índices exclusivos em uma coluna.</span><span class="sxs-lookup"><span data-stu-id="3ca3b-136">But when you are using the in-memory database, you cannot handle unique indexes on a column.</span></span> <span data-ttu-id="3ca3b-137">Portanto, o banco de dados na memória não se comporta exatamente como um banco de dados real do SQL Server — não emula restrições específicas do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="3ca3b-137">Therefore, the in-memory database does not behave exactly the same as a real SQL Server database—it does not emulate database-specific constraints.</span></span>

<span data-ttu-id="3ca3b-138">Mesmo assim, um banco de dados na memória é útil para teste e de protótipos.</span><span class="sxs-lookup"><span data-stu-id="3ca3b-138">Even so, an in-memory database is still useful for testing and prototyping.</span></span> <span data-ttu-id="3ca3b-139">Mas se você quiser criar testes de integração precisas que levam em conta o comportamento de uma implementação do banco de dados específico, você precisa usar um banco de dados real como o SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3ca3b-139">But if you want to create accurate integration tests that take into account the behavior of a specific database implementation, you need to use a real database like SQL Server.</span></span> <span data-ttu-id="3ca3b-140">Para essa finalidade, executando o SQL Server em um contêiner é um ótimo choice e mais preciso do que o provedor de banco de dados do EF Core InMemory.</span><span class="sxs-lookup"><span data-stu-id="3ca3b-140">For that purpose, running SQL Server in a container is a great choice and more accurate than the EF Core InMemory database provider.</span></span>

### <a name="using-a-redis-cache-service-running-in-a-container"></a><span data-ttu-id="3ca3b-141">Usando um serviço de cache Redis em execução em um contêiner</span><span class="sxs-lookup"><span data-stu-id="3ca3b-141">Using a Redis cache service running in a container</span></span>

<span data-ttu-id="3ca3b-142">Você pode executar o Redis em um contêiner, especialmente para desenvolvimento e teste e para cenários de prova de conceito.</span><span class="sxs-lookup"><span data-stu-id="3ca3b-142">You can run Redis on a container, especially for development and testing and for proof-of-concept scenarios.</span></span> <span data-ttu-id="3ca3b-143">Este cenário é conveniente, porque você pode ter todas as suas dependências em execução em contêineres — não apenas para as máquinas de desenvolvimento local, mas para seus ambientes de teste em seu pipelines CI/CD.</span><span class="sxs-lookup"><span data-stu-id="3ca3b-143">This scenario is convenient, because you can have all your dependencies running on containers—not just for your local development machines, but for your testing environments in your CI/CD pipelines.</span></span>

<span data-ttu-id="3ca3b-144">No entanto, quando você executa o Redis em produção, é melhor procurar uma solução de alta disponibilidade, como o Redis Microsoft Azure, que é executado como um PaaS (plataforma como serviço).</span><span class="sxs-lookup"><span data-stu-id="3ca3b-144">However, when you run Redis in production, it is better to look for a high-availability solution like Redis Microsoft Azure, which runs as a PaaS (Platform as a Service).</span></span> <span data-ttu-id="3ca3b-145">No seu código, basta alterar suas cadeias de caracteres de conexão.</span><span class="sxs-lookup"><span data-stu-id="3ca3b-145">In your code, you just need to change your connection strings.</span></span>

<span data-ttu-id="3ca3b-146">Redis fornece uma imagem do Docker com Redis.</span><span class="sxs-lookup"><span data-stu-id="3ca3b-146">Redis provides a Docker image with Redis.</span></span> <span data-ttu-id="3ca3b-147">Essa imagem está disponível no Hub do Docker nesta URL:</span><span class="sxs-lookup"><span data-stu-id="3ca3b-147">That image is available from Docker Hub at this URL:</span></span>

<span data-ttu-id="3ca3b-148"><https://hub.docker.com/_/redis/></span><span class="sxs-lookup"><span data-stu-id="3ca3b-148"><https://hub.docker.com/_/redis/></span></span>

<span data-ttu-id="3ca3b-149">Você pode executar diretamente um contêiner de Docker Redis, executando o seguinte comando CLI do Docker em seu prompt de comando:</span><span class="sxs-lookup"><span data-stu-id="3ca3b-149">You can directly run a Docker Redis container by executing the following Docker CLI command in your command prompt:</span></span>

```
  docker run --name some-redis -d redis
```

<span data-ttu-id="3ca3b-150">A imagem de Redis inclui expor: 6379 (a porta usada pelo Redis), então padrão vinculação de contêiner será disponibilizá-lo automaticamente para os contêineres vinculados.</span><span class="sxs-lookup"><span data-stu-id="3ca3b-150">The Redis image includes expose:6379 (the port used by Redis), so standard container linking will make it automatically available to the linked containers.</span></span>

<span data-ttu-id="3ca3b-151">EShopOnContainers, o microsserviço basket.api usa um cache Redis em execução como um contêiner.</span><span class="sxs-lookup"><span data-stu-id="3ca3b-151">In eShopOnContainers, the basket.api microservice uses a Redis cache running as a container.</span></span> <span data-ttu-id="3ca3b-152">Esse contêiner basket.data é definido como parte do arquivo de multi-contêiner docker-compose.yml, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="3ca3b-152">That basket.data container is defined as part of the multi-container docker-compose.yml file, as shown in the following example:</span></span>

```yml
#docker-compose.yml file
#...
  basket.data:
    image: redis
    expose:
      - "6379"
```

<span data-ttu-id="3ca3b-153">Esse código no docker-compose.yml define um contêiner denominado basket.data com base na imagem do redis e publicando a porta 6379 internamente, que significa que eles poderão ser acessados somente de outros contêineres em execução dentro do host do Docker.</span><span class="sxs-lookup"><span data-stu-id="3ca3b-153">This code in the docker-compose.yml defines a container named basket.data based on the redis image and publishing the port 6379 internally, meaning that it will be accessible only from other containers running within the Docker host.</span></span>

<span data-ttu-id="3ca3b-154">Por fim, no arquivo compose.override.yml docker, o microsserviço basket.api para o exemplo eShopOnContainers define a cadeia de caracteres de conexão para usar para o contêiner Redis:</span><span class="sxs-lookup"><span data-stu-id="3ca3b-154">Finally, in the docker-compose.override.yml file, the basket.api microservice for the eShopOnContainers sample defines the connection string to use for that Redis container:</span></span>

```yml
  basket.api:
    environment:
      # Other data ...
      - ConnectionString=basket.data
      - EventBusConnection=rabbitmq
```


>[!div class="step-by-step"]
<span data-ttu-id="3ca3b-155">[Anterior] (multi-container-aplicativos-docker-compose.md) [Avançar] (integração-evento-com base-microsserviço-communications.md)</span><span class="sxs-lookup"><span data-stu-id="3ca3b-155">[Previous] (multi-container-applications-docker-compose.md) [Next] (integration-event-based-microservice-communications.md)</span></span>
