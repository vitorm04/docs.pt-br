---
title: Usando um servidor de banco de dados em execução como contêiner
description: Arquitetura de Microsserviços .NET para aplicativos .NET em contêineres | Usando um servidor de banco de dados em execução como um contêiner? Apenas para desenvolvimento! Entenda o porquê.
ms.date: 10/02/2018
ms.openlocfilehash: 5fd92a28a09cab041225c4c817a10f5ecfedc038
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68676193"
---
# <a name="using-a-database-server-running-as-a-container"></a><span data-ttu-id="079bb-104">Usando um servidor de banco de dados em execução como contêiner</span><span class="sxs-lookup"><span data-stu-id="079bb-104">Using a database server running as a container</span></span>

<span data-ttu-id="079bb-105">Você pode ter seus bancos de dados (SQL Server, PostgreSQL, MySQL etc.) em servidores autônomo regulares, em clusters locais ou em serviços de PaaS na nuvem como o BD SQL do Azure.</span><span class="sxs-lookup"><span data-stu-id="079bb-105">You can have your databases (SQL Server, PostgreSQL, MySQL, etc.) on regular standalone servers, in on-premises clusters, or in PaaS services in the cloud like Azure SQL DB.</span></span> <span data-ttu-id="079bb-106">No entanto, para ambientes de desenvolvimento e teste, ter os bancos de dados em execução como contêineres é conveniente, porque você não precisa de nenhuma dependência externa e basta executar o comando `docker-compose up` para iniciar todo o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="079bb-106">However, for development and test environments, having your databases running as containers is convenient, because you do not have any external dependency and simply running the `docker-compose up` command starts the whole application.</span></span> <span data-ttu-id="079bb-107">Ter esses bancos de dados como contêineres também é excelente para testes de integração, porque o banco de dados é iniciado no contêiner e sempre é preenchido com os dados de exemplo, assim, os testes podem ser mais previsíveis.</span><span class="sxs-lookup"><span data-stu-id="079bb-107">Having those databases as containers is also great for integration tests, because the database is started in the container and is always populated with the same sample data, so tests can be more predictable.</span></span>

### <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a><span data-ttu-id="079bb-108">SQL Server em execução como um contêiner com um banco de dados relacionado a microsserviço</span><span class="sxs-lookup"><span data-stu-id="079bb-108">SQL Server running as a container with a microservice-related database</span></span>

<span data-ttu-id="079bb-109">Em eShopOnContainers, há um contêiner denominado sql.data definido no arquivo [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) que executa o SQL Server para Linux com todos os bancos de dados SQL Server necessários para os microsserviços.</span><span class="sxs-lookup"><span data-stu-id="079bb-109">In eShopOnContainers, there is a container named sql.data defined in the [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) file that runs SQL Server for Linux with all the SQL Server databases needed for the microservices.</span></span> <span data-ttu-id="079bb-110">(Você também pode ter um contêiner SQL Server para cada banco de dados, mas isso exigiria mais memória atribuída ao Docker.) O ponto importante em microsserviços é que cada microsserviço tem seus dados relacionados, portanto, seu Banco de Dados SQL relacionado neste caso.</span><span class="sxs-lookup"><span data-stu-id="079bb-110">(You could also have one SQL Server container for each database, but that would require more memory assigned to Docker.) The important point in microservices is that each microservice owns its related data, therefore its related SQL database in this case.</span></span> <span data-ttu-id="079bb-111">Porém, os bancos de dados podem estar em qualquer lugar.</span><span class="sxs-lookup"><span data-stu-id="079bb-111">But the databases can be anywhere.</span></span>

<span data-ttu-id="079bb-112">O contêiner do SQL Server no aplicativo de exemplo é configurado com o seguinte código YAML no arquivo docker-compose.yml, que é executado quando você executa o `docker-compose up`.</span><span class="sxs-lookup"><span data-stu-id="079bb-112">The SQL Server container in the sample application is configured with the following YAML code in the docker-compose.yml file, which is executed when you run `docker-compose up`.</span></span> <span data-ttu-id="079bb-113">Observe que o código YAML consolidou informações de configuração do arquivo genérico docker-compose.yml e o arquivo docker-compose.override.yml.</span><span class="sxs-lookup"><span data-stu-id="079bb-113">Note that the YAML code has consolidated configuration information from the generic docker-compose.yml file and the docker-compose.override.yml file.</span></span> <span data-ttu-id="079bb-114">(Normalmente, separe as configurações de ambiente com as informações de base ou estáticas relacionada à imagem do SQL Server.)</span><span class="sxs-lookup"><span data-stu-id="079bb-114">(Usually you would separate the environment settings from the base or static information related to the SQL Server image.)</span></span>

```yml
  sql.data:
    image: microsoft/mssql-server-linux:2017-latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"
```

<span data-ttu-id="079bb-115">De maneira semelhante, em vez de usar `docker-compose`, o seguinte comando `docker run` pode ser executado naquele contêiner:</span><span class="sxs-lookup"><span data-stu-id="079bb-115">In a similar way, instead of using `docker-compose`, the following `docker run` command can run that container:</span></span>

```
  docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Pass@word' -p 5433:1433 -d microsoft/mssql-server-linux:2017-latest
```

<span data-ttu-id="079bb-116">No entanto, se você estiver implantando um aplicativo multicontêiner, como eShopOnContainers, será mais conveniente usar o comando `docker-compose up` para que ele implante todos os contêineres necessários para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="079bb-116">However, if you are deploying a multi-container application like eShopOnContainers, it is more convenient to use the `docker-compose up` command so that it deploys all the required containers for the application.</span></span>

<span data-ttu-id="079bb-117">Quando você inicia esse contêiner do SQL Server pela primeira vez, o contêiner inicializa o SQL Server com a senha que você fornece.</span><span class="sxs-lookup"><span data-stu-id="079bb-117">When you start this SQL Server container for the first time, the container initializes SQL Server with the password that you provide.</span></span> <span data-ttu-id="079bb-118">Depois que o SQL Server está em execução como um contêiner, você pode atualizar o banco de dados conectando por meio de qualquer conexão de SQL normal, como SQL Server Management Studio, Visual Studio ou código C\#.</span><span class="sxs-lookup"><span data-stu-id="079bb-118">Once SQL Server is running as a container, you can update the database by connecting through any regular SQL connection, such as from SQL Server Management Studio, Visual Studio, or C\# code.</span></span>

<span data-ttu-id="079bb-119">O aplicativo eShopOnContainers inicializa cada banco de dados de microsserviço usando dados de exemplo propagando-os com os dados na inicialização, conforme explica a seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="079bb-119">The eShopOnContainers application initializes each microservice database with sample data by seeding it with data on startup, as explained in the following section.</span></span>

<span data-ttu-id="079bb-120">Ter o SQL Server em execução como um contêiner não é apenas útil para uma demonstração em que você talvez não tenha acesso a uma instância do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="079bb-120">Having SQL Server running as a container is not just useful for a demo where you might not have access to an instance of SQL Server.</span></span> <span data-ttu-id="079bb-121">Como mencionado, também é ótimo para ambientes de desenvolvimento e teste para que você possa executar facilmente testes de integração começando com uma imagem limpa do SQL Server e dados conhecidos propagando novos dados de exemplo.</span><span class="sxs-lookup"><span data-stu-id="079bb-121">As noted, it is also great for development and testing environments so that you can easily run integration tests starting from a clean SQL Server image and known data by seeding new sample data.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="079bb-122">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="079bb-122">Additional resources</span></span>

- <span data-ttu-id="079bb-123">**Executar a imagem do Docker do SQL Server no Linux, no Mac ou no Windows** </span><span class="sxs-lookup"><span data-stu-id="079bb-123">**Run the SQL Server Docker image on Linux, Mac, or Windows** </span></span>\
    [https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker](/sql/linux/sql-server-linux-setup-docker)

- <span data-ttu-id="079bb-124">**Conectar e consultar o SQL Server em Linux com sqlcmd** </span><span class="sxs-lookup"><span data-stu-id="079bb-124">**Connect and query SQL Server on Linux with sqlcmd** </span></span>\
    [https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd](/sql/linux/sql-server-linux-connect-and-query-sqlcmd)

### <a name="seeding-with-test-data-on-web-application-startup"></a><span data-ttu-id="079bb-125">Propagação com os dados de teste na inicialização do aplicativo Web</span><span class="sxs-lookup"><span data-stu-id="079bb-125">Seeding with test data on Web application startup</span></span>

<span data-ttu-id="079bb-126">Para adicionar dados ao banco de dados quando o aplicativo é iniciado, você pode adicionar código como o seguinte ao método Configurar na classe Inicialização do projeto da API da Web:</span><span class="sxs-lookup"><span data-stu-id="079bb-126">To add data to the database when the application starts up, you can add code like the following to the Configure method in the Startup class of the Web API project:</span></span>

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

<span data-ttu-id="079bb-127">O código a seguir na classe CatalogContextSeed personalizada preenche os dados.</span><span class="sxs-lookup"><span data-stu-id="079bb-127">The following code in the custom CatalogContextSeed class populates the data.</span></span>

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

<span data-ttu-id="079bb-128">Quando você executa testes de integração, é útil ter uma maneira de gerar dados consistentes com seus testes de integração.</span><span class="sxs-lookup"><span data-stu-id="079bb-128">When you run integration tests, having a way to generate data consistent with your integration tests is useful.</span></span> <span data-ttu-id="079bb-129">Poder criar tudo do zero, incluindo uma instância do SQL Server em execução em um contêiner, é ótimo para ambientes de teste.</span><span class="sxs-lookup"><span data-stu-id="079bb-129">Being able to create everything from scratch, including an instance of SQL Server running on a container, is great for test environments.</span></span>

### <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a><span data-ttu-id="079bb-130">Banco de dados InMemory do EF Core versus SQL Server em execução como um contêiner</span><span class="sxs-lookup"><span data-stu-id="079bb-130">EF Core InMemory database versus SQL Server running as a container</span></span>

<span data-ttu-id="079bb-131">Outra boa opção para executar testes é usar o provedor de banco de dados do Entity Framework InMemory.</span><span class="sxs-lookup"><span data-stu-id="079bb-131">Another good choice when running tests is to use the Entity Framework InMemory database provider.</span></span> <span data-ttu-id="079bb-132">Você pode especificar essa configuração no método ConfigureServices da classe de Inicialização em seu projeto de API da Web:</span><span class="sxs-lookup"><span data-stu-id="079bb-132">You can specify that configuration in the ConfigureServices method of the Startup class in your Web API project:</span></span>

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

<span data-ttu-id="079bb-133">No entanto, há um problema importante.</span><span class="sxs-lookup"><span data-stu-id="079bb-133">There is an important catch, though.</span></span> <span data-ttu-id="079bb-134">O banco de dados na memória não é compatível com muitas restrições específicas de um determinado banco de dados.</span><span class="sxs-lookup"><span data-stu-id="079bb-134">The in-memory database does not support many constraints that are specific to a particular database.</span></span> <span data-ttu-id="079bb-135">Por exemplo, você pode adicionar um índice exclusivo em uma coluna em seu modelo EF Core e escrever um teste com relação ao seu banco de dados na memória para verificar se ele não permite que você adicione um valor duplicado.</span><span class="sxs-lookup"><span data-stu-id="079bb-135">For instance, you might add a unique index on a column in your EF Core model and write a test against your in-memory database to check that it does not let you add a duplicate value.</span></span> <span data-ttu-id="079bb-136">Porém, quando você estiver usando o banco de dados na memória, não poderá manipular índices exclusivos em uma coluna.</span><span class="sxs-lookup"><span data-stu-id="079bb-136">But when you are using the in-memory database, you cannot handle unique indexes on a column.</span></span> <span data-ttu-id="079bb-137">Portanto, o banco de dados em memória não se comporta exatamente como um banco de dados real do SQL Server: ele não emula restrições específicas do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="079bb-137">Therefore, the in-memory database does not behave exactly the same as a real SQL Server database—it does not emulate database-specific constraints.</span></span>

<span data-ttu-id="079bb-138">Mesmo assim, um banco de dados na memória é útil para testes e protótipos.</span><span class="sxs-lookup"><span data-stu-id="079bb-138">Even so, an in-memory database is still useful for testing and prototyping.</span></span> <span data-ttu-id="079bb-139">Porém, se você quiser criar testes de integração precisos que levem em conta o comportamento de uma implementação do banco de dados específica, você precisará usar um banco de dados real como o SQL Server.</span><span class="sxs-lookup"><span data-stu-id="079bb-139">But if you want to create accurate integration tests that take into account the behavior of a specific database implementation, you need to use a real database like SQL Server.</span></span> <span data-ttu-id="079bb-140">Para essa finalidade, executar o SQL Server em um contêiner é uma ótima escolha e mais preciso do que o provedor de banco de dados do EF Core InMemory.</span><span class="sxs-lookup"><span data-stu-id="079bb-140">For that purpose, running SQL Server in a container is a great choice and more accurate than the EF Core InMemory database provider.</span></span>

### <a name="using-a-redis-cache-service-running-in-a-container"></a><span data-ttu-id="079bb-141">Usando um Serviço de Cache Redis em execução em um contêiner</span><span class="sxs-lookup"><span data-stu-id="079bb-141">Using a Redis cache service running in a container</span></span>

<span data-ttu-id="079bb-142">Você pode executar o Redis em um contêiner, especialmente para desenvolvimento e teste e para cenários de prova de conceito.</span><span class="sxs-lookup"><span data-stu-id="079bb-142">You can run Redis on a container, especially for development and testing and for proof-of-concept scenarios.</span></span> <span data-ttu-id="079bb-143">Este cenário é conveniente, porque você pode ter todas as suas dependências em execução em contêineres, não apenas para os computadores de desenvolvimento locais, mas para seus ambientes de teste em seus pipelines CI/CD.</span><span class="sxs-lookup"><span data-stu-id="079bb-143">This scenario is convenient, because you can have all your dependencies running on containers—not just for your local development machines, but for your testing environments in your CI/CD pipelines.</span></span>

<span data-ttu-id="079bb-144">No entanto, quando você executa o Redis em produção, é melhor procurar uma solução de alta disponibilidade, como o Redis Microsoft Azure, que é executado como uma PaaS (plataforma como serviço).</span><span class="sxs-lookup"><span data-stu-id="079bb-144">However, when you run Redis in production, it is better to look for a high-availability solution like Redis Microsoft Azure, which runs as a PaaS (Platform as a Service).</span></span> <span data-ttu-id="079bb-145">No seu código, basta alterar suas cadeias de caracteres de conexão.</span><span class="sxs-lookup"><span data-stu-id="079bb-145">In your code, you just need to change your connection strings.</span></span>

<span data-ttu-id="079bb-146">O Redis fornece uma imagem do Docker com Redis.</span><span class="sxs-lookup"><span data-stu-id="079bb-146">Redis provides a Docker image with Redis.</span></span> <span data-ttu-id="079bb-147">Essa imagem está disponível no Hub do Docker nesta URL:</span><span class="sxs-lookup"><span data-stu-id="079bb-147">That image is available from Docker Hub at this URL:</span></span>

<https://hub.docker.com/\_/redis/>

<span data-ttu-id="079bb-148">Você pode executar diretamente um contêiner do Docker Redis executando o seguinte comando da CLI do Docker em seu prompt de comando:</span><span class="sxs-lookup"><span data-stu-id="079bb-148">You can directly run a Docker Redis container by executing the following Docker CLI command in your command prompt:</span></span>

```
  docker run --name some-redis -d redis
```

<span data-ttu-id="079bb-149">A imagem do Redis inclui expose:6379 (a porta usada pelo Redis), de modo que a vinculação de contêiner padrão o tornará automaticamente disponível aos contêineres vinculados.</span><span class="sxs-lookup"><span data-stu-id="079bb-149">The Redis image includes expose:6379 (the port used by Redis), so standard container linking will make it automatically available to the linked containers.</span></span>

<span data-ttu-id="079bb-150">Em eShopOnContainers, o microsserviço basket.api usa um Cache Redis em execução como um contêiner.</span><span class="sxs-lookup"><span data-stu-id="079bb-150">In eShopOnContainers, the basket.api microservice uses a Redis cache running as a container.</span></span> <span data-ttu-id="079bb-151">O contêiner basket.data é definido como parte do arquivo docker-compose.yml multicontêiner, conforme mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="079bb-151">That basket.data container is defined as part of the multi-container docker-compose.yml file, as shown in the following example:</span></span>

```yml
#docker-compose.yml file
#...
  basket.data:
    image: redis
    expose:
      - "6379"
```

<span data-ttu-id="079bb-152">Esse código no docker-compose.yml define um contêiner denominado basket.data com base na imagem do redis e publicando a porta 6379 internamente, o que significa que ele poderá ser acessado somente de outros contêineres em execução dentro do host do Docker.</span><span class="sxs-lookup"><span data-stu-id="079bb-152">This code in the docker-compose.yml defines a container named basket.data based on the redis image and publishing the port 6379 internally, meaning that it will be accessible only from other containers running within the Docker host.</span></span>

<span data-ttu-id="079bb-153">Por fim, no arquivo docker-compose.override.yml, o microsserviço basket.api para o exemplo eShopOnContainers define a cadeia de conexão a usar para o contêiner Redis:</span><span class="sxs-lookup"><span data-stu-id="079bb-153">Finally, in the docker-compose.override.yml file, the basket.api microservice for the eShopOnContainers sample defines the connection string to use for that Redis container:</span></span>

```yml
  basket.api:
    environment:
      # Other data ...
      - ConnectionString=basket.data
      - EventBusConnection=rabbitmq
```

<span data-ttu-id="079bb-154">Como mencionado anteriormente, o nome do microsserviço "basket.data" é resolvido pelo DNS da rede interna do docker.</span><span class="sxs-lookup"><span data-stu-id="079bb-154">As mentioned before, the name of the microservice "basket.data" is resolved by docker's internal network DNS.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="079bb-155">[Anterior](multi-container-applications-docker-compose.md)
>[Próximo](integration-event-based-microservice-communications.md)</span><span class="sxs-lookup"><span data-stu-id="079bb-155">[Previous](multi-container-applications-docker-compose.md)
[Next](integration-event-based-microservice-communications.md)</span></span>
