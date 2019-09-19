---
title: Usando um servidor de banco de dados em execução como contêiner
description: Arquitetura de Microsserviços .NET para aplicativos .NET em contêineres | Usando um servidor de banco de dados em execução como um contêiner? Apenas para desenvolvimento! Entenda o porquê.
ms.date: 10/02/2018
ms.openlocfilehash: 3e655e26be2d6132577b0494db39d9c2e8b9aacd
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039847"
---
# <a name="using-a-database-server-running-as-a-container"></a>Usando um servidor de banco de dados em execução como contêiner

Você pode ter seus bancos de dados (SQL Server, PostgreSQL, MySQL etc.) em servidores autônomo regulares, em clusters locais ou em serviços de PaaS na nuvem como o BD SQL do Azure. No entanto, para ambientes de desenvolvimento e teste, ter os bancos de dados em execução como contêineres é conveniente, porque você não precisa de nenhuma dependência externa e basta executar o comando `docker-compose up` para iniciar todo o aplicativo. Ter esses bancos de dados como contêineres também é excelente para testes de integração, porque o banco de dados é iniciado no contêiner e sempre é preenchido com os dados de exemplo, assim, os testes podem ser mais previsíveis.

### <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a>SQL Server em execução como um contêiner com um banco de dados relacionado a microsserviço

Em eShopOnContainers, há um contêiner denominado sql.data definido no arquivo [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) que executa o SQL Server para Linux com todos os bancos de dados SQL Server necessários para os microsserviços. (Você também pode ter um contêiner SQL Server para cada banco de dados, mas isso exigiria mais memória atribuída ao Docker.) O ponto importante em microsserviços é que cada microsserviço tem seus dados relacionados, portanto, seu Banco de Dados SQL relacionado neste caso. Porém, os bancos de dados podem estar em qualquer lugar.

O contêiner do SQL Server no aplicativo de exemplo é configurado com o seguinte código YAML no arquivo docker-compose.yml, que é executado quando você executa o `docker-compose up`. Observe que o código YAML consolidou informações de configuração do arquivo genérico docker-compose.yml e o arquivo docker-compose.override.yml. (Normalmente, separe as configurações de ambiente com as informações de base ou estáticas relacionada à imagem do SQL Server.)

```yml
  sql.data:
    image: microsoft/mssql-server-linux:2017-latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"
```

De maneira semelhante, em vez de usar `docker-compose`, o seguinte comando `docker run` pode ser executado naquele contêiner:

```console
  docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Pass@word' -p 5433:1433 -d microsoft/mssql-server-linux:2017-latest
```

No entanto, se você estiver implantando um aplicativo multicontêiner, como eShopOnContainers, será mais conveniente usar o comando `docker-compose up` para que ele implante todos os contêineres necessários para o aplicativo.

Quando você inicia esse contêiner do SQL Server pela primeira vez, o contêiner inicializa o SQL Server com a senha que você fornece. Depois que o SQL Server está em execução como um contêiner, você pode atualizar o banco de dados conectando por meio de qualquer conexão de SQL normal, como SQL Server Management Studio, Visual Studio ou código C\#.

O aplicativo eShopOnContainers inicializa cada banco de dados de microsserviço usando dados de exemplo propagando-os com os dados na inicialização, conforme explica a seção a seguir.

Ter o SQL Server em execução como um contêiner não é apenas útil para uma demonstração em que você talvez não tenha acesso a uma instância do SQL Server. Como mencionado, também é ótimo para ambientes de desenvolvimento e teste para que você possa executar facilmente testes de integração começando com uma imagem limpa do SQL Server e dados conhecidos propagando novos dados de exemplo.

#### <a name="additional-resources"></a>Recursos adicionais

- **Executar a imagem do Docker do SQL Server no Linux, no Mac ou no Windows** \
    [https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker](/sql/linux/sql-server-linux-setup-docker)

- **Conectar e consultar o SQL Server em Linux com sqlcmd** \
    [https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd](/sql/linux/sql-server-linux-connect-and-query-sqlcmd)

### <a name="seeding-with-test-data-on-web-application-startup"></a>Propagação com os dados de teste na inicialização do aplicativo Web

Para adicionar dados ao banco de dados quando o aplicativo é iniciado, você pode adicionar código como o seguinte ao método Configurar na classe Inicialização do projeto da API da Web:

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

### <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a>Banco de dados InMemory do EF Core versus SQL Server em execução como um contêiner

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

### <a name="using-a-redis-cache-service-running-in-a-container"></a>Usando um Serviço de Cache Redis em execução em um contêiner

Você pode executar o Redis em um contêiner, especialmente para desenvolvimento e teste e para cenários de prova de conceito. Este cenário é conveniente, porque você pode ter todas as suas dependências em execução em contêineres, não apenas para os computadores de desenvolvimento locais, mas para seus ambientes de teste em seus pipelines CI/CD.

No entanto, quando você executa o Redis em produção, é melhor procurar uma solução de alta disponibilidade, como o Redis Microsoft Azure, que é executado como uma PaaS (plataforma como serviço). No seu código, basta alterar suas cadeias de caracteres de conexão.

O Redis fornece uma imagem do Docker com Redis. Essa imagem está disponível no Hub do Docker nesta URL:

<https://hub.docker.com/\_/redis/>

Você pode executar diretamente um contêiner do Docker Redis executando o seguinte comando da CLI do Docker em seu prompt de comando:

```console
  docker run --name some-redis -d redis
```

A imagem do Redis inclui expose:6379 (a porta usada pelo Redis), de modo que a vinculação de contêiner padrão o tornará automaticamente disponível aos contêineres vinculados.

Em eShopOnContainers, o microsserviço basket.api usa um Cache Redis em execução como um contêiner. O contêiner basket.data é definido como parte do arquivo docker-compose.yml multicontêiner, conforme mostra o exemplo a seguir:

```yml
#docker-compose.yml file
#...
  basket.data:
    image: redis
    expose:
      - "6379"
```

Esse código no docker-compose.yml define um contêiner denominado basket.data com base na imagem do redis e publicando a porta 6379 internamente, o que significa que ele poderá ser acessado somente de outros contêineres em execução dentro do host do Docker.

Por fim, no arquivo docker-compose.override.yml, o microsserviço basket.api para o exemplo eShopOnContainers define a cadeia de conexão a usar para o contêiner Redis:

```yml
  basket.api:
    environment:
      # Other data ...
      - ConnectionString=basket.data
      - EventBusConnection=rabbitmq
```

Como mencionado anteriormente, o nome do microsserviço "basket.data" é resolvido pelo DNS da rede interna do docker.

>[!div class="step-by-step"]
>[Anterior](multi-container-applications-docker-compose.md)
>[Próximo](integration-event-based-microservice-communications.md)
