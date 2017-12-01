---
title: "Criar um microsserviço CRUD simple controlada por dados"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Criar um microsserviço CRUD simple controlada por dados"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: b814d344f2c78e7cf57f9e2896cf1d6b52db38d9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="creating-a-simple-data-driven-crud-microservice"></a>Criar um microsserviço CRUD simple controlada por dados

Esta seção descreve como criar um simples microsserviço executa criar, ler, atualização e operações de exclusão (CRUD) em uma fonte de dados.

## <a name="designing-a-simple-crud-microservice"></a>Criar um microsserviço CRUD simple

Do ponto de vista do design, esse tipo de microsserviço em contêineres é muito simple. Talvez o problema a resolver é simple ou talvez a implementação é apenas uma prova de conceito.

![](./media/image4.png)

**Figura 8-4**. Design interno microservices CRUD simples

Um exemplo desse tipo de serviço simples de unidade de dados é o microsserviço de catálogo do aplicativo de exemplo eShopOnContainers. Esse tipo de serviço implementa todos os seus recursos em um único projeto de API da Web do ASP.NET Core que inclui classes para seu modelo de dados, sua lógica de negócios e seu código de acesso a dados. Ele também armazena seus dados relacionados em um banco de dados em execução no SQL Server (como outro contêiner para fins de desenvolvimento/teste), mas também pode ser qualquer host regular do SQL Server, conforme mostrado na Figura 8-5.

![](./media/image5.png)

**Figura 8-5**. Design de microsserviço simples de dados controlada por/CRUD

Quando você estiver desenvolvendo esse tipo de serviço, você só precisa [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) e uma API de acesso a dados ou ORM como [Entity Framework Core](https://docs.microsoft.com/ef/core/index). Você também pode gerar [Swagger](http://swagger.io/) automaticamente por meio de metadados [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) para fornecer uma descrição do que o seu serviço oferece, conforme explicado na próxima seção.

Observe que a execução de um servidor de banco de dados como o SQL Server em um contêiner do Docker é ótimo para ambientes de desenvolvimento, porque você pode ter todas as suas dependências até e em execução sem a necessidade de provisionar um banco de dados na nuvem ou local. Isso é muito conveniente quando executando a integração de testes. No entanto, para ambientes de produção, executar um servidor de banco de dados em um contêiner não é recomendável, porque você normalmente não tem alta disponibilidade com essa abordagem. Para um ambiente de produção no Azure, é recomendável que você use o banco de dados de SQL Azure ou qualquer outra tecnologia de banco de dados que pode fornecer alta disponibilidade e alto desempenho. Por exemplo, para uma abordagem NoSQL, você pode escolher documentos.

Por fim, editando os arquivos de metadados do Dockerfile e compose.yml docker, você pode configurar como a imagem desse contêiner será criada – qual imagem de base-la será usar, além de configurações, como nomes internos e externos e portas TCP de design. 

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a>Implementando um microsserviço CRUD simple com o ASP.NET Core

Para implementar um microsserviço CRUD simple usando o .NET Core e o Visual Studio, você inicia criando um projeto de API da Web do ASP.NET Core simples (em execução no .NET Core para que ele pode ser executado em um host Linux Docker), como 8-6 mostrado na figura.

  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------
  ![](./media/image6.png)   ![](./media/image7.png)
  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------

**Figura 8-6**. Criando um projeto de API da Web do ASP.NET Core no Visual Studio

Depois de criar o projeto, você pode implementar os controladores MVC como você faria em qualquer outro projeto de API da Web, usando a API do Entity Framework ou outros API. No projeto eShopOnContainers.Catalog.API, você pode ver que as dependências principais para que microsserviço são apenas ASP.NET Core em si, Entity Framework e Swashbuckle, conforme mostrado na Figura 8-7.

![](./media/image8.PNG)

**Figura 8-7**. Dependências em um microsserviço CRUD Web API simple

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a>Implementando serviços de API da Web de CRUD com o Entity Framework Core

Núcleo do Entity Framework (EF) é leve e extensível, e tecnologia de acesso de versão de plataforma cruzada dos dados do Entity Framework populares. Núcleo do EF é mapeador relacional de objeto (ORM) que permite que os desenvolvedores de .NET trabalhar com um banco de dados usando objetos do .NET Framework.

O catálogo microsserviço usa EF e o provedor do SQL Server porque seu banco de dados está em execução em um contêiner com o SQL Server para a imagem do Docker do Linux. No entanto, o banco de dados pode ser implantado em qualquer servidor SQL, como o local do Windows ou o banco de dados do Azure SQL. A única coisa que você precisa alterar é a cadeia de caracteres de conexão em microsserviço a API Web do ASP.NET.

#### <a name="add-entity-framework-core-to-your-dependencies"></a>Adicionar o Entity Framework Core para as suas dependências

Você pode instalar o pacote NuGet para o provedor de banco de dados que você deseja usar, no caso do SQL Server, de dentro do IDE do Visual Studio ou com o console do NuGet. Use o seguinte comando:

```
  Install-Package Microsoft.EntityFrameworkCore.SqlServer
```

#### <a name="the-data-model"></a>O modelo de dados

Com o núcleo do EF, acesso a dados é executado usando um modelo. Um modelo é composto de classes de entidade e um contexto derivado que representa uma sessão com o banco de dados, permitindo que você consultar e salvar dados. Você pode gerar um modelo de banco de dados existente, manualmente um modelo para coincidir com seu banco de dados de código ou usar migrações EF para criar um banco de dados do seu modelo (e evolui-lo como o modelo é alterado ao longo do tempo). Para o catálogo microsserviço estamos usando a última abordagem. Você pode ver um exemplo da classe da entidade CatalogItem no exemplo de código a seguir, que é um simples objeto Plain Old CLR ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) classe da entidade.

```csharp
public class CatalogItem
{
    public int Id { get; set; }
    public string Name { get; set; }
    public string Description { get; set; }
    public decimal Price { get; set; }
    public string PictureUri { get; set; }
    public int CatalogTypeId { get; set; }
    public CatalogType CatalogType { get; set; }
    public int CatalogBrandId { get; set; }
    public CatalogBrand CatalogBrand { get; set; }
    public CatalogItem() { }
}
```

Você também precisa de um DbContext que representa uma sessão com o banco de dados. Para o catálogo microsserviço, a classe de CatalogContext deriva da classe DbContext base, conforme mostrado no exemplo a seguir:

```csharp
public class CatalogContext : DbContext
{
    public CatalogContext(DbContextOptions<CatalogContext> options) : base(options)
    {
    }

    public DbSet<CatalogItem> CatalogItems { get; set; }
    public DbSet<CatalogBrand> CatalogBrands { get; set; }
    public DbSet<CatalogType> CatalogTypes { get; set; }

    // Additional code ...

}
```

Você pode ter um código adicional na implementação do DbContext. Por exemplo, o aplicativo de exemplo, temos um método OnModelCreating na classe CatalogContext que preenche automaticamente os dados de exemplo na primeira vez que tentar acessar o banco de dados. Esse método é útil para dados de demonstração. Você também pode usar o método OnModelCreating para personalizar os mapeamentos de entidades de objeto/banco de dados com muitos outros [pontos de extensibilidade do EF](https://blogs.msdn.microsoft.com/dotnet/2016/09/29/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).

Você pode ver mais detalhes sobre OnModelCreating no [Implementando a camada de persistência de infraestrutura com o Entity Framework Core](#implementing_infrastructure_persistence) seção mais adiante neste manual.

##### <a name="querying-data-from-web-api-controllers"></a>Consultar dados de controladores de API da Web

Instâncias de suas classes de entidade normalmente são recuperadas do banco de dados usando linguagem integrado LINQ (consulta), conforme mostrado no exemplo a seguir:

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    private readonly CatalogContext _catalogContext;
    private readonly CatalogSettings _settings;
    private readonly ICatalogIntegrationEventService _catalogIntegrationEventService;

    public CatalogController(CatalogContext context,
        IOptionsSnapshot<CatalogSettings> settings,
        ICatalogIntegrationEventService catalogIntegrationEventService)
    {
        _catalogContext = context ?? throw new ArgumentNullException(nameof(context));
        _catalogIntegrationEventService = catalogIntegrationEventService ??
           throw new ArgumentNullException(nameof(catalogIntegrationEventService));
        _settings = settings.Value;
        ((DbContext)context).ChangeTracker.QueryTrackingBehavior = QueryTrackingBehavior.NoTracking;
    }

    // GET api/v1/[controller]/items[?pageSize=3&pageIndex=10]
    [HttpGet]
    [Route("[action]")]
    public async Task<IActionResult> Items([FromQuery]int pageSize = 10,
    [FromQuery]int pageIndex = 0)
    {
        var totalItems = await _catalogContext.CatalogItems
            .LongCountAsync();
        var itemsOnPage = await _catalogContext.CatalogItems
            .OrderBy(c => c.Name)
            .Skip(pageSize * pageIndex)
            .Take(pageSize)
            .ToListAsync();
        itemsOnPage = ChangeUriPlaceholder(itemsOnPage);
        var model = new PaginatedItemsViewModel<CatalogItem>(
            pageIndex, pageSize, totalItems, itemsOnPage);
        return Ok(model);
    } 

    //...
}
```

##### <a name="saving-data"></a>Salvando dados

Dados são criados, excluídos e modificados no banco de dados usando as instâncias de suas classes de entidade. Você pode adicionar código como o exemplo a seguir embutido (dados fictícios, neste caso) para os controladores de API da Web.

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
   Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a>Injeção de dependência em controladores de API da Web do ASP.NET Core

No núcleo do ASP.NET, você pode usar injeção de dependência (DI) fora da caixa. Você não precisa configurar um contêiner de inversão de controle (IoC) de terceiros, embora você pode conectar seu contêiner IoC preferencial da infraestrutura do ASP.NET Core se você quiser. Nesse caso, isso significa que você pode injetar diretamente o EF DBContext necessária ou repositórios adicionais por meio do construtor do controlador. No exemplo acima da classe CatalogController, estamos injetando um objeto do tipo CatalogContext além de outros objetos por meio do construtor CatalogController.

Uma configuração importante para configurar o projeto de API da Web é o registro de classe DbContext no contêiner de IoC do serviço. Você normalmente faz isso na classe de inicialização ao chamar os serviços. Método AddDbContext dentro do método ConfigureServices, conforme mostrado no exemplo a seguir:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddDbContext<CatalogContext>(options =>
    {
        options.UseSqlServer(Configuration["ConnectionString"],
        sqlServerOptionsAction: sqlOptions =>
        {
           sqlOptions.
               MigrationsAssembly(
               typeof(Startup).
               GetTypeInfo().
               Assembly.
               GetName().Name);

           //Configuring Connection Resiliency:
           sqlOptions.
               EnableRetryOnFailure(maxRetryCount: 5,
               maxRetryDelay: TimeSpan.FromSeconds(30),
               errorNumbersToAdd: null);

       });

       // Changing default behavior when client evaluation occurs to throw.
       // Default in EFCore would be to log warning when client evaluation is done.
       options.ConfigureWarnings(warnings => warnings.Throw(
           RelationalEventId.QueryClientEvaluationWarning));
   });

  //...

}
```

### <a name="additional-resources"></a>Recursos adicionais

-   **Consultando dados**
    [*https://docs.microsoft.com/ef/core/querying/index*](https://docs.microsoft.com/ef/core/querying/index)

-   **Salvando dados**
    [*https://docs.microsoft.com/ef/core/saving/index*](https://docs.microsoft.com/ef/core/saving/index)

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a>As variáveis banco de dados de cadeia de caracteres e o ambiente de conexão usadas por contêineres do Docker

Você pode usar as configurações do ASP.NET Core e adicionar uma propriedade ConnectionString para o arquivo settings.json, conforme mostrado no exemplo a seguir:

```csharp
{
    "ConnectionString": "Server=tcp:127.0.0.1,5433;Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word",
    "ExternalCatalogBaseUrl": "http://localhost:5101",
    "Logging": {
        "IncludeScopes": false,
        "LogLevel": {
            "Default": "Debug",
            "System": "Information",
            "Microsoft": "Information"
        }
    }
}
```

O arquivo de settings.json pode ter valores padrão para a propriedade ConnectionString ou para qualquer outra propriedade. No entanto, essas propriedades serão substituídas pelos valores de variáveis de ambiente que você especificar no arquivo compose.override.yml docker.

Dos seus arquivos de docker compose.yml ou compose.override.yml docker, é possível inicializar as variáveis de ambiente para que Docker configurará-los como variáveis de ambiente do sistema operacional, conforme mostrado no seguinte arquivo docker compose.override.yml (a conexão cadeia de caracteres e outras linhas quebrar neste exemplo, mas ele não seria quebrar em seu próprio arquivo).

```yml
# docker-compose.override.yml

#
catalog.api:
  environment:
    - ConnectionString=Server=sql.data;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word
    - ExternalCatalogBaseUrl=http://10.0.75.1:5101
    #- ExternalCatalogBaseUrl=http://dockerhoststaging.westus.cloudapp.azure.com:5101
  
  ports:
    - "5101:5101"
```

Os arquivos de docker compose.yml no nível da solução apenas não são mais flexíveis do que os arquivos de configuração no nível do projeto ou microsserviço, mas também mais segura. Considere a possibilidade de que as imagens do Docker que você cria por microsserviço não contêm o docker-compose.yml arquivos, somente os arquivos binários e arquivos de configuração para cada microsserviço, incluindo o Dockerfile. Mas o arquivo compose.yml docker não está implantado juntamente com seu aplicativo. ele é usado somente no momento da implantação. Portanto, é mais seguro do que colocar esses valores nos arquivos de configuração .NET regulares que são implantados com o código de colocar valores de variáveis de ambiente nesses arquivos de docker compose.yml (mesmo sem criptografar os valores).

Por fim, você pode obter esse valor no seu código usando a configuração\["ConnectionString"\], conforme mostrado no método ConfigureServices em um exemplo de código anterior.

No entanto, para ambientes de produção, você talvez queira maneiras adicionais de explorer sobre como armazenar segredos, como as cadeias de caracteres de conexão. Geralmente que serão gerenciados pelo seu orchestrator escolhido, como você pode fazer com [Docker Swarm gerenciamento de segredos](https://docs.docker.com/engine/swarm/secrets/).

### <a name="implementing-versioning-in-aspnet-web-apis"></a>Implementar o controle de versão em APIs da Web de ASP.NET

Como alterarem os requisitos de negócios, novas coleções de recursos podem ser adicionadas, poderão alterar as relações entre os recursos e a estrutura dos dados de recursos pode ser corrigida. Uma API da Web para lidar com novos requisitos de atualização é um processo relativamente simples, mas você deve considerar os efeitos que tenham essas alterações em aplicativos cliente consumo da API da Web. Embora o desenvolvedor Projetando e implementando uma API da Web tem controle total sobre essa API, o desenvolvedor não tem o mesmo nível de controle sobre os aplicativos cliente que podem ser criados por terceiros organizações operacional remotamente.

Controle de versão permite uma API da Web indicar os recursos e os recursos que ele expõe. Um aplicativo cliente pode enviar solicitações para uma versão específica de um recurso ou recurso. Há várias abordagens para implementar o controle de versão:

-   Controle de versão do URI

-   Controle de versão de cadeia de caracteres de consulta

-   Controle de versão de cabeçalho

Cadeia de caracteres de consulta e controle de versão do URI são mais simples de implementar. Controle de versão do cabeçalho é uma boa abordagem. No entanto, controle de versão de cabeçalho não como explícita e simples como controle de versão do URI. Como o controle de versão de URL é a mais simples e mais explícito, o aplicativo de exemplo eShopOnContainers usa controle de versão do URI.

Com controle de versão URI, como o aplicativo de exemplo eShopOnContainers, cada vez que você modifique a API da Web ou alterar o esquema de recursos, você adicionar um número de versão para o URI para cada recurso. URIs existentes devem continuar a operar como antes, retornando os recursos que estão de acordo com o esquema que corresponde à versão solicitada.

Conforme mostrado no exemplo de código a seguir, a versão pode ser definida usando o atributo da rota na API da Web, que torna a versão explícita no URI (v1 neste caso).

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

Esse mecanismo de controle de versão é simple e depende do servidor de roteamento de solicitação para o ponto de extremidade apropriado. No entanto, para uma versão mais sofisticada e o melhor método ao usar o REST, você deve usar hipermídia e implementar [HATEOAS (como o mecanismo de estado do aplicativo de hipertexto)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#using-the-hateoas-approach-to-enable-navigation-to-related-resources).

### <a name="additional-resources"></a>Recursos adicionais

-   **Scott Hanselman. Controle de versão do núcleo da API da Web RESTful ASP.NET facilitado**
    [*http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx*](http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx)

-   **Controle de versão de uma API da web RESTful**

    [*https://docs.microsoft.com/Azure/Architecture/Best-Practices/API-design#Versioning-a-RESTful-Web-API*](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)

-   **Roy Fielding. Controle de versão, hipermídia e REST**
    [*https://www.infoq.com/articles/roy-fielding-on-versioning*](https://www.infoq.com/articles/roy-fielding-on-versioning)

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a>Geração de metadados do Swagger descrição de sua API Web do ASP.NET Core 

[Swagger](http://swagger.io/) é uma estrutura de código aberto usados com o apoio de um grande ecossistema de ferramentas que ajuda você a design, compilação, documento e consumir suas APIs RESTful. Ele está se tornando o padrão para o domínio de metadados de descrição de APIs. Você deve incluir os metadados do Swagger descrição com qualquer tipo de microsserviço, controlada por dados microservices ou mais avançados microservices controlado por domínio (conforme explicado na seção a seguir).

A essência do Swagger é a especificação de Swagger, que metadados de descrição de API em um arquivo JSON ou YAML. A especificação cria o contrato RESTful para sua API, detalhando a todos os seus recursos e operações em ambos os humanos e machine readable formato para fácil desenvolvimento, descoberta e integração.

A especificação é a base da especificação OpenAPI (OAS) e é desenvolvida em uma comunidade transparente, colaboração e abrir para padronizar a maneira RESTful interfaces são definidas.

A especificação define a estrutura de como um serviço pode ser descoberto e como seus recursos entendido. Para obter mais informações, inclusive um editor de web e exemplos de especificações de Swagger de empresas como Spotify, Uber, atraso e Microsoft, consulte o site de Swagger (<http://swagger.io>).

### <a name="why-use-swagger"></a>Por que usar Swagger?

As principais razões para gerar os metadados do Swagger para suas APIs são os seguintes.

**Capacidade para outros produtos consumir e integrar suas APIs automaticamente**. Dezenas de produtos e [ferramentas comercial](http://swagger.io/commercial-tools/) e muitos [estruturas e bibliotecas](http://swagger.io/open-source-integrations/) Swagger de suporte. A Microsoft tem alto nível produtos e ferramentas que podem consumir automaticamente o APIs Swagger, como o seguinte:

-   [AutoRest](https://github.com/Azure/AutoRest). Você pode gerar automaticamente as classes de cliente .NET para chamar Swagger. Este

-   ferramenta pode ser usada da CLI e ele também se integra com o Visual Studio fácil de usar por meio da GUI.

-   [Microsoft Flow](https://flow.microsoft.com/en-us/). Você pode automaticamente [usar e integrar sua API](https://flow.microsoft.com/en-us/blog/integrating-custom-api/) em um fluxo de trabalho do Microsoft Flow alto nível, sem nenhum programação habilidades necessárias.

-   [Microsoft PowerApps](https://powerapps.microsoft.com/en-us/). Automaticamente, você pode usar a API de [aplicativos móveis PowerApps](https://powerapps.microsoft.com/en-us/blog/register-and-use-custom-apis-in-powerapps/) criados com [PowerApps Studio](https://powerapps.microsoft.com/en-us/guided-learning/learning-powerapps-parts/), com nenhuma programação habilidades necessárias.

-   [Aplicativos do serviço de aplicativo do Azure lógica](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps). Você pode automaticamente [usar e integrar sua API em um aplicativo de lógica do serviço de aplicativo do Azure](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), com nenhuma programação habilidades necessárias.

**Capacidade de gerar automaticamente a documentação da API**. Quando você criar APIs RESTful em larga escala, como aplicativos baseados em microsserviço complexos, você precisa lidar com vários pontos de extremidade com modelos de dados diferentes usados nas cargas de solicitação e resposta. Ter a documentação adequada e ter um Gerenciador de API sólido, como você pode obter com Swagger, são a chave para o sucesso da sua API e adoção pelos desenvolvedores.

Metadados do swagger são o que os aplicativos lógicos do Azure, PowerApps e Microsoft Flow usam para entender como usar APIs e conectá-los.

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a>Como automatizar a geração de metadados Swagger de API com o pacote Swashbuckle NuGet

Geração de metadados Swagger manualmente (em um arquivo JSON ou YAML) pode ser entediante trabalho. No entanto, você pode automatizar a descoberta de API de serviços de API da Web ASP.NET usando o [pacote Swashbuckle NuGet](http://aka.ms/swashbuckledotnetcore) gerar dinamicamente os metadados do Swagger API.

Swashbuckle gera automaticamente os metadados do Swagger para seus projetos ASP.NET Web API. Ele dá suporte a projetos de API da Web do ASP.NET Core e o ASP.NET Web API tradicional e qualquer outro tipo, como aplicativo de API, aplicativo de celular do Azure, Azure Service Fabric microservices com base no ASP.NET. Ele também dá suporte a API da Web simples do implantado em contêineres, como para o aplicativo de referência.

Swashbuckle combina o Gerenciador de API e Swagger ou [swagger ui](https://github.com/swagger-api/swagger-ui) para fornecer a experiência de descoberta avançada e a documentação para seus consumidores de API. Além de seu mecanismo de gerador de metadados Swagger, Swashbuckle também contém uma versão incorporada do swagger-interface do usuário, que automaticamente servirá backup uma vez Swashbuckle será instalado.

Isso significa que você pode complementar a sua API com uma interface de usuário para ajudar os desenvolvedores a usar a API de descoberta adequada. Ele requer uma quantidade muito pequena de código e manutenção porque ela é gerada automaticamente, permitindo que você se concentre na sua API. O resultado para o Gerenciador de API é como a Figura 8-8.

![](./media/image9.png)

**Figura 8-8**. Gerenciador de API Swashbuckle com base nos metadados do Swagger — eShopOnContainers microsserviço do catálogo

O Gerenciador de API não é o mais importante aqui. Quando você tem uma API da Web que pode descrever-se nos metadados do Swagger, sua API pode ser usada diretamente do Swagger com ferramentas, incluindo geradores de código de classe de proxy de cliente que podem direcionar várias plataformas. Por exemplo, conforme mencionado, [AutoRest](https://github.com/Azure/AutoRest) gera automaticamente as classes de cliente .NET. Mas, como ferramentas adicionais [swagger codegen](https://github.com/swagger-api/swagger-codegen) também estão disponíveis, que permite a geração de código do cliente de API de bibliotecas, stubs de servidor e documentação automaticamente.

No momento, Swashbuckle consiste em dois pacotes do NuGet: Swashbuckle.SwaggerGen e Swashbuckle.SwaggerUi. O primeiro fornece funcionalidade para gerar um ou mais documentos de Swagger diretamente de sua implementação de API e expô-los como pontos de extremidade JSON. O último fornece uma versão incorporada da ferramenta de interface do usuário swagger que pode ser atendida por seu aplicativo e os documentos de Swagger gerados para descrever sua API da plataforma. No entanto, as versões mais recentes de Swashbuckle encapsulam esses recursos com o metapackage Swashbuckle.AspNetCore.

Observe que, para projetos Web API do .NET Core, você precisa usar [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore/1.0.0) versão 1.0.0 ou posterior.

Depois de instalar esses pacotes do NuGet em seu projeto de API da Web, você precisa configurar Swagger na classe de inicialização, como no código a seguir:

```csharp
public class Startup
{
    public IConfigurationRoot Configuration { get; }
    // Other startup code...

    public void ConfigureServices(IServiceCollection services)
    {
        // Other ConfigureServices() code...
        services.AddSwaggerGen();
        services.ConfigureSwaggerGen(options =>
        {
            options.DescribeAllEnumsAsStrings();
            options.SingleApiVersion(new Swashbuckle.Swagger.Model.Info()
            {
                Title = "eShopOnContainers - Catalog HTTP API",
                Version = "v1",
                Description = "The Catalog Microservice HTTP API",
                TermsOfService = "eShopOnContainers terms of service"
            });
        });
        // Other ConfigureServices() code...
    }

    public void Configure(IApplicationBuilder app,
        IHostingEnvironment env,
        ILoggerFactory loggerFactory)
    {
        // Other Configure() code...
        // ...
        app.UseSwagger()
            .UseSwaggerUi();
    }
}
```

Depois que isso for feito, você pode iniciar o aplicativo e procurar seguintes Swagger JSON e interface de usuário pontos de extremidade usando URLs como estes:

```json
  http://<your-root-url>/swagger/v1/swagger.json
  
  http://<your-root-url>/swagger/ui
```

Anteriormente, você viu a interface do usuário gerado criado pelo Swashbuckle para uma URL como http://&lt;sua url raiz &gt; /swagger/interface do usuário. Figura 8 e 9 você também pode ver como você pode testar qualquer método de API.

![](./media/image10.png)

**Figura 8 e 9**. Swashbuckle UI testar o método de API de itens do catálogo

Figura 8-10 mostra os metadados do Swagger JSON gerado a partir de microsserviço eShopOnContainers (que é o que usam as ferramentas abaixo) quando você solicitar &lt;sua url raiz&gt;/swagger/v1/swagger.json usando [carteiro](https://www.getpostman.com/).

![](./media/image11.png)

**Figura 8-10**. Metadados do swagger JSON

É simple. E como ela é gerada automaticamente, os metadados do Swagger aumentará quando você adicionar mais funcionalidade a sua API.

### <a name="additional-resources"></a>Recursos adicionais

-   **Páginas da Web ASP.NET API ajuda usando Swagger**
    [*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger*](https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger)


>[!div class="step-by-step"]
[Anterior] (microsserviço-aplicativo-design.md) [Avançar] (multi-container-aplicativos-docker-compose.md)
