---
title: Use um servidor de banco de dados em execução como um contêiner
description: Entenda a importância de usar um servidor de banco de dados funcionando como um contêiner apenas para o desenvolvimento. Nunca para produção.
ms.date: 01/30/2020
ms.openlocfilehash: 0cbc933003aac10970814378c27e88b5cb0ddbe5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77628521"
---
# <a name="use-a-database-server-running-as-a-container"></a>Use um servidor de banco de dados em execução como um contêiner

Você pode ter seus bancos de dados (SQL Server, PostgreSQL, MySQL etc.) em servidores autônomo regulares, em clusters locais ou em serviços de PaaS na nuvem como o BD SQL do Azure. No entanto, para ambientes de desenvolvimento e teste, ter seus bancos de dados funcionando como `docker-compose up` contêineres é conveniente, porque você não tem nenhuma dependência externa e simplesmente executar o comando inicia todo o aplicativo. Ter esses bancos de dados como contêineres também é excelente para testes de integração, porque o banco de dados é iniciado no contêiner e sempre é preenchido com os dados de exemplo, assim, os testes podem ser mais previsíveis.

## <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a>SQL Server em execução como um contêiner com um banco de dados relacionado a microsserviço

No eShopOnContainers, há um `sqldata`contêiner chamado , como definido no arquivo [docker-compose.yml,](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) que executa um SQL Server para linux com os bancos de dados SQL para todos os microserviços que precisam de um.

Um ponto-chave nos microsserviços é que cada microserviço possui seus dados relacionados, por isso deve ter seu próprio banco de dados. No entanto, os bancos de dados podem estar em qualquer lugar. Neste caso, todos eles estão no mesmo contêiner para manter os requisitos de memória Docker o mais baixo possível. Tenha em mente que esta é uma solução boa o suficiente para o desenvolvimento e, talvez, para testes, mas não para a produção.

O contêiner do SQL Server no aplicativo de exemplo é configurado com o seguinte código YAML no arquivo docker-compose.yml, que é executado quando você executa o `docker-compose up`. Observe que o código YAML consolidou informações de configuração do arquivo genérico docker-compose.yml e o arquivo docker-compose.override.yml. (Normalmente, separe as configurações de ambiente com as informações de base ou estáticas relacionada à imagem do SQL Server.)

```yml
  sqldata:
    image: mcr.microsoft.com/mssql/server:2017-latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"
```

De maneira semelhante, em vez de usar `docker-compose`, o seguinte comando `docker run` pode ser executado naquele contêiner:

```powershell
docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Pass@word' -p 5433:1433 -d mcr.microsoft.com/mssql/server:2017-latest
```

No entanto, se você estiver implantando um aplicativo multicontêiner, como eShopOnContainers, será mais conveniente usar o comando `docker-compose up` para que ele implante todos os contêineres necessários para o aplicativo.

Quando você inicia esse contêiner do SQL Server pela primeira vez, o contêiner inicializa o SQL Server com a senha que você fornece. Depois que o SQL Server está em execução como um contêiner, você pode atualizar o banco de dados conectando por meio de qualquer conexão de SQL normal, como SQL Server Management Studio, Visual Studio ou código C\#.

O aplicativo eShopOnContainers inicializa cada banco de dados de microsserviço usando dados de exemplo propagando-os com os dados na inicialização, conforme explica a seção a seguir.

Ter o SQL Server em execução como um contêiner não é apenas útil para uma demonstração em que você talvez não tenha acesso a uma instância do SQL Server. Como mencionado, também é ótimo para ambientes de desenvolvimento e teste para que você possa executar facilmente testes de integração começando com uma imagem limpa do SQL Server e dados conhecidos propagando novos dados de exemplo.

### <a name="additional-resources"></a>Recursos adicionais

- **Execute a imagem sql server docker no Linux, Mac ou Windows** \
  <https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker>

- **Conectar e consultar o SQL Server no Linux com sqlcmd** \
  <https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd>

## <a name="seeding-with-test-data-on-web-application-startup"></a>Propagação com os dados de teste na inicialização do aplicativo Web

Para adicionar dados ao banco de dados quando o aplicativo for `Main` iniciado, `Program` você pode adicionar código como o seguinte ao método na classe do projeto de API da Web:

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

Há uma ressalva importante ao aplicar migrações e semear um banco de dados durante a inicialização do contêiner. Uma vez que o servidor de banco de dados pode não estar disponível por qualquer motivo, você deve lidar com repetições enquanto espera que o servidor esteja disponível. Esta lógica de repetição `MigrateDbContext()` é tratada pelo método de extensão, conforme mostrado no código a seguir:

```cs
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

O código a seguir na classe CatalogContextSeed personalizada preenche os dados.

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

Quando você executa testes de integração, é útil ter uma maneira de gerar dados consistentes com seus testes de integração. Poder criar tudo do zero, incluindo uma instância do SQL Server em execução em um contêiner, é ótimo para ambientes de teste.

## <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a>Banco de dados InMemory do EF Core versus SQL Server em execução como um contêiner

Outra boa opção para executar testes é usar o provedor de banco de dados do Entity Framework InMemory. Você pode especificar essa configuração no método ConfigureServices da classe de Inicialização em seu projeto de API da Web:

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

No entanto, há um problema importante. O banco de dados na memória não é compatível com muitas restrições específicas de um determinado banco de dados. Por exemplo, você pode adicionar um índice exclusivo em uma coluna em seu modelo EF Core e escrever um teste com relação ao seu banco de dados na memória para verificar se ele não permite que você adicione um valor duplicado. Porém, quando você estiver usando o banco de dados na memória, não poderá manipular índices exclusivos em uma coluna. Portanto, o banco de dados em memória não se comporta exatamente como um banco de dados real do SQL Server: ele não emula restrições específicas do banco de dados.

Mesmo assim, um banco de dados na memória é útil para testes e protótipos. Porém, se você quiser criar testes de integração precisos que levem em conta o comportamento de uma implementação do banco de dados específica, você precisará usar um banco de dados real como o SQL Server. Para essa finalidade, executar o SQL Server em um contêiner é uma ótima escolha e mais preciso do que o provedor de banco de dados do EF Core InMemory.

## <a name="using-a-redis-cache-service-running-in-a-container"></a>Usando um Serviço de Cache Redis em execução em um contêiner

Você pode executar o Redis em um contêiner, especialmente para desenvolvimento e teste e para cenários de prova de conceito. Este cenário é conveniente, porque você pode ter todas as suas dependências em execução em contêineres, não apenas para os computadores de desenvolvimento locais, mas para seus ambientes de teste em seus pipelines CI/CD.

No entanto, quando você executa o Redis em produção, é melhor procurar uma solução de alta disponibilidade, como o Redis Microsoft Azure, que é executado como uma PaaS (plataforma como serviço). No seu código, basta alterar suas cadeias de caracteres de conexão.

O Redis fornece uma imagem do Docker com Redis. Essa imagem está disponível no Hub do Docker nesta URL:

<https://hub.docker.com/_/redis/>

Você pode executar diretamente um contêiner do Docker Redis executando o seguinte comando da CLI do Docker em seu prompt de comando:

```console
docker run --name some-redis -d redis
```

A imagem do Redis inclui expose:6379 (a porta usada pelo Redis), de modo que a vinculação de contêiner padrão o tornará automaticamente disponível aos contêineres vinculados.

No eShopOnContainers, `basket-api` o microserviço usa um cache Redis em execução como um contêiner. Esse `basketdata` contêiner é definido como parte do arquivo *docker-compose.yml* de vários contêineres, conforme mostrado no exemplo a seguir:

```yml
#docker-compose.yml file
#...
  basketdata:
    image: redis
    expose:
      - "6379"
```

Este código no docker-compose.yml define `basketdata` um contêiner nomeado com base na imagem redis e publicando a porta 6379 internamente. Isso significa que ele só estará acessível a partir de outros contêineres executados dentro do host Docker.

Finalmente, no arquivo *docker-compose.override.yml,* o `basket-api` microserviço para a amostra eShopOnContainers define a string de conexão a ser usada para o contêiner Redis:

```yml
  basket-api:
    environment:
      # Other data ...
      - ConnectionString=basketdata
      - EventBusConnection=rabbitmq
```

Como mencionado anteriormente, o `basketdata` nome do microserviço é resolvido pelo DNS da rede interna do Docker.

>[!div class="step-by-step"]
>[Próximo](multi-container-applications-docker-compose.md)
>[anterior](integration-event-based-microservice-communications.md)
