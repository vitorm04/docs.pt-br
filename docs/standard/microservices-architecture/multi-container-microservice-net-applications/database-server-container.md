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
# <a name="using-a-database-server-running-as-a-container"></a>Usando um servidor de banco de dados em execução como um contêiner

Você pode ter seus bancos de dados (SQL Server, PostgreSQL, MySQL, etc.) em servidores autônomo regular, em clusters locais ou em serviços de PaaS na nuvem como banco de dados de SQL do Azure. No entanto, para ambientes de desenvolvimento e teste, ter seus bancos de dados em execução como contêineres é simplesmente em execução e conveniente, porque você não tem nenhuma dependência externa, a compor docker comando inicia o aplicativo inteiro. Ter esses bancos de dados como contêineres também é excelente para testes de integração, porque o banco de dados é iniciado no contêiner e sempre é preenchido com dados de exemplo, para que testes possam ser mais previsíveis.

### <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a>SQL Server em execução como um contêiner com um banco de dados relacionados de microsserviço

EShopOnContainers, há um contêiner denominado sql.data definido no [docker compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) arquivos que executa o SQL Server para Linux com todos os SQL Server bancos de dados necessários para o microservices. (Você também pode ter um contêiner do SQL Server para cada banco de dados, mas que exigem mais memória atribuída ao Docker). O ponto importante microservices é que cada microsserviço possui seus dados relacionados, portanto, seu banco de dados SQL relacionado nesse caso. Mas os bancos de dados podem estar em qualquer lugar.

Docker de contêiner no aplicativo de amostra está configurado com o código a seguir YAML no arquivo compose.yml docker, que é executado quando você executa o SQL Server-compor backup. Observe que o código YAML consolidou informações de configuração de arquivo genérico de compose.yml de docker e o arquivo de docker compose.override.yml. (Normalmente separe as configurações de ambiente com as informações de base ou estáticas relacionada à imagem do SQL Server.)

```yml
sql.data:
  image: microsoft/mssql-server-linux
  environment:
    - SA_PASSWORD=your@password
    - ACCEPT_EULA=Y
  ports:
    - "5434:1433"
```

O seguinte comando docker run pode executar esse contêiner:

```
  docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD= your@password' -p 1433:1433 -d microsoft/mssql-server-linux
```

No entanto, se você estiver implantando um aplicativo de multi-contêiner como eShopOnContainers, é mais conveniente usar o docker-compor o comando para que ele implanta todos os contêineres necessários para o aplicativo.

Quando você inicia esse contêiner do SQL Server pela primeira vez, o contêiner inicia o SQL Server com a senha que você fornecer. Depois que o SQL Server está em execução como um contêiner, você pode atualizar o banco de dados conectando através de qualquer conexão de SQL regular, como SQL Server Management Studio, o Visual Studio ou o C\# código.

O aplicativo eShopOnContainers inicializa cada banco de dados com dados de exemplo microsserviço propagá-lo com dados na inicialização, conforme explicado na seção a seguir.

Com o SQL Server em execução como um contêiner não é útil apenas para uma demonstração em que talvez você não tenha acesso a uma instância do SQL Server. Como mencionado, também é ideal para ambientes de desenvolvimento e teste para que você pode executar testes de integração a partir de uma imagem do SQL Server limpar facilmente e dados conhecidos, propagando novos dados de exemplo.

#### <a name="additional-resources"></a>Recursos adicionais

-   **Executar a imagem do Docker do SQL Server no Linux, Mac ou Windows**
    [*https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker*](https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker)

-   **Conectar e consultar o SQL Server no Linux com sqlcmd**
    [*https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd*](https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd)

### <a name="seeding-with-test-data-on-web-application-startup"></a>A propagação com dados de teste na inicialização do aplicativo Web

Para adicionar dados ao banco de dados quando o aplicativo é iniciado, você pode adicionar código como o seguinte ao configurar método na classe de inicialização do projeto de API da Web:

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

O código a seguir na classe CatalogContextSeed personalizado preenche os dados.

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

Quando você executa testes de integração, é útil ter uma maneira de gerar dados consistentes com os testes de integração. Capacidade de criar tudo do zero, incluindo uma instância do SQL Server em execução em um contêiner, é ideal para ambientes de teste.

### <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a>Banco de dados do EF InMemory Core em comparação com o SQL Server em execução como um contêiner

Outra boa opção para a execução de testes é usar o provedor de banco de dados do Entity Framework InMemory. Você pode especificar que a configuração no método ConfigureServices da classe de inicialização em seu projeto de API da Web:

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

Há um problema importante, embora. O banco de dados na memória não oferece suporte a muitas restrições que são específicas para um determinado banco de dados. Por exemplo, você pode adicionar um índice exclusivo em uma coluna em seu modelo EF principal e um teste de gravação no banco de dados na memória para verificar se ele não permite que você adicionar um valor duplicado. Mas quando você estiver usando o banco de dados na memória, você não pode manipular índices exclusivos em uma coluna. Portanto, o banco de dados na memória não se comporta exatamente como um banco de dados real do SQL Server — não emula restrições específicas do banco de dados.

Mesmo assim, um banco de dados na memória é útil para teste e de protótipos. Mas se você quiser criar testes de integração precisas que levam em conta o comportamento de uma implementação do banco de dados específico, você precisa usar um banco de dados real como o SQL Server. Para essa finalidade, executando o SQL Server em um contêiner é um ótimo choice e mais preciso do que o provedor de banco de dados do EF Core InMemory.

### <a name="using-a-redis-cache-service-running-in-a-container"></a>Usando um serviço de cache Redis em execução em um contêiner

Você pode executar o Redis em um contêiner, especialmente para desenvolvimento e teste e para cenários de prova de conceito. Este cenário é conveniente, porque você pode ter todas as suas dependências em execução em contêineres — não apenas para as máquinas de desenvolvimento local, mas para seus ambientes de teste em seu pipelines CI/CD.

No entanto, quando você executa o Redis em produção, é melhor procurar uma solução de alta disponibilidade, como o Redis Microsoft Azure, que é executado como um PaaS (plataforma como serviço). No seu código, basta alterar suas cadeias de caracteres de conexão.

Redis fornece uma imagem do Docker com Redis. Essa imagem está disponível no Hub do Docker nesta URL:

<https://hub.docker.com/_/redis/>

Você pode executar diretamente um contêiner de Docker Redis, executando o seguinte comando CLI do Docker em seu prompt de comando:

```
  docker run --name some-redis -d redis
```

A imagem de Redis inclui expor: 6379 (a porta usada pelo Redis), então padrão vinculação de contêiner será disponibilizá-lo automaticamente para os contêineres vinculados.

EShopOnContainers, o microsserviço basket.api usa um cache Redis em execução como um contêiner. Esse contêiner basket.data é definido como parte do arquivo de multi-contêiner docker-compose.yml, conforme mostrado no exemplo a seguir:

```yml
#docker-compose.yml file
#...
  basket.data:
    image: redis
    expose:
      - "6379"
```

Esse código no docker-compose.yml define um contêiner denominado basket.data com base na imagem do redis e publicando a porta 6379 internamente, que significa que eles poderão ser acessados somente de outros contêineres em execução dentro do host do Docker.

Por fim, no arquivo compose.override.yml docker, o microsserviço basket.api para o exemplo eShopOnContainers define a cadeia de caracteres de conexão para usar para o contêiner Redis:

```yml
  basket.api:
    environment:
      # Other data ...
      - ConnectionString=basket.data
      - EventBusConnection=rabbitmq
```


>[!div class="step-by-step"]
[Anterior] (multi-container-aplicativos-docker-compose.md) [Avançar] (integração-evento-com base-microsserviço-communications.md)
