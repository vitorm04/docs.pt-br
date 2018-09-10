---
title: Criando um microsserviço de CRUD simples controlado por dados
description: Arquitetura de microsserviços .NET para aplicativos .NET em contêineres | Criando um microsserviço de CRUD simples controlado por dados
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 28955b2309b3efb321e40e19db821052b8ce42ab
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43512110"
---
# <a name="creating-a-simple-data-driven-crud-microservice"></a>Criando um microsserviço de CRUD simples controlado por dados

Esta seção descreve como criar um microsserviço simples que execute operações de CRUD (criar, ler, atualizar e excluir) em uma fonte de dados.

## <a name="designing-a-simple-crud-microservice"></a>Criando um microsserviço de CRUD simples

Do ponto de vista do design, esse tipo de microsserviço em contêineres é muito simples. Talvez o problema a ser resolvido seja simples ou talvez a implementação seja apenas uma prova de conceito.

![](./media/image4.png)

**Figura 8-4**. Design interno para microsserviços de CRUD simples

Um exemplo desse tipo de serviço de unidade de dados é o microsserviço de catálogo do aplicativo de exemplo eShopOnContainers. Esse tipo de serviço implementa todas as suas funcionalidades em um único projeto da API Web ASP.NET Core que inclui classes para seu modelo de dados, sua lógica de negócios e seu código de acesso a dados. Ele também armazena os dados relacionados em um banco de dados em execução no SQL Server (como outro contêiner para fins de Desenvolvimento/Teste), mas também poderia ser em qualquer host regular do SQL Server, conforme é mostrado na Figura 8-5.

![](./media/image5.png)

**Figura 8-5**. Design de microsserviço controlado por dados/CRUD simples

Quando estiver desenvolvendo esse tipo de serviço, você somente precisará do [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) e de uma API de acesso a dados ou de um ORM (mapeador relacional de objeto) como o [Entity Framework Core](https://docs.microsoft.com/ef/core/index). Você também pode gerar metadados do [Swagger](https://swagger.io/) automaticamente por meio do [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) para fornecer uma descrição do que o serviço oferece, conforme será explicado na próxima seção.

Observe que executar um servidor de banco de dados como o SQL Server em um contêiner do Docker é ótimo para ambientes de desenvolvimento, porque todas as dependências podem funcionar sem precisar provisionar um banco de dados na nuvem ou localmente. Isso é muito conveniente ao executar testes de integração. No entanto, para ambientes de produção, executar um servidor de banco de dados em um contêiner não é recomendável, porque, geralmente, essa abordagem não oferece alta disponibilidade. Para um ambiente de produção no Azure, é recomendável usar o BD SQL do Azure ou qualquer outra tecnologia de banco de dados que possa fornecer alta disponibilidade e alta escalabilidade. Por exemplo, para uma abordagem NoSQL, você pode escolher o DocumentDB.

Por fim, editando os arquivos de metadados Dockerfile e docker-compose.yml, você pode configurar como a imagem desse contêiner será criada, ou seja, qual imagem base ele usará, além das configurações de design, como nomes internos e externos e portas TCP. 

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a>Implementando um microsserviço de CRUD simples com o ASP.NET Core

Para implementar um microsserviço de CRUD simples usando o .NET Core e o Visual Studio, comece criando um projeto de API Web ASP.NET Core simples (em execução no .NET Core para que ele possa ser executado em um host Linux do Docker), como é mostrado na Figura 8-6.

  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------
  ![](./media/image6.png)   ![](./media/image7.png)
  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------

**Figura 8-6**. Criando um projeto de API Web ASP.NET Core no Visual Studio

Depois de criar o projeto, você poderá implementar os controladores de MVC como faria em qualquer outro projeto de API Web, usando a API do Entity Framework ou uma outra API. Em um novo projeto de API Web, você verá que a única dependência existente nesse microsserviço é em relação ao próprio ASP.NET Core. Internamente, na dependência `Microsoft.AspNetCore.All`, ela se refere ao Entity Framework e a muitos outros pacotes NuGet do .NET Core, como é mostrado na Figura 8-7.

![](./media/image8.PNG)

**Figura 8-7**. Dependências em um microsserviço de API Web de CRUD simples

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a>Implementando serviços da API Web de CRUD com o Entity Framework Core

O Entity Framework (EF) Core é uma versão de multiplaforma leve, extensível e de plataforma cruzada da popular tecnologia de acesso a dados do Entity Framework. O EF Core é um ORM (mapeador relacional de objeto) que permite que os desenvolvedores do .NET trabalhem com um banco de dados usando objetos .NET.

O microsserviço de catálogo usa o EF e o provedor do SQL Server porque seu banco de dados está em execução em um contêiner com o SQL Server para a imagem do Docker do Linux. No entanto, o banco de dados poderia ser implantado em qualquer SQL Server, como o Windows local ou o BD SQL do Azure. A única coisa que você precisaria alterar seria a cadeia de conexão no microsserviço do ASP.NET Web API.


#### <a name="the-data-model"></a>O modelo de dados

Com o EF Core, o acesso a dados é executado usando um modelo. Um modelo é composto por classes de entidade e um contexto derivado que representa uma sessão com o banco de dados, permitindo que você consulte e salve os dados. É possível gerar um modelo usando um banco de dados existente, codificar manualmente um modelo para corresponder ao seu banco de dados ou usar migrações do EF para criar um banco de dados usando o modelo (e evolui-lo conforme o modelo mudar com o tempo). Para o microsserviço de catálogo estamos usando a última abordagem. Veja um exemplo da classe de entidade CatalogItem no exemplo de código a seguir, que é uma classe de entidade [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object) (objeto CRL básico) simples.

```csharp
public class CatalogItem
{
    public int Id { get; set; }
    public string Name { get; set; }
    public string Description { get; set; }
    public decimal Price { get; set; }
    public string PictureFileName { get; set; }
    public string PictureUri { get; set; }
    public int CatalogTypeId { get; set; }
    public CatalogType CatalogType { get; set; }
    public int CatalogBrandId { get; set; }
    public CatalogBrand CatalogBrand { get; set; }
    public int AvailableStock { get; set; }
    public int RestockThreshold { get; set; }
    public int MaxStockThreshold { get; set; }

    public bool OnReorder { get; set; }
    public CatalogItem() { }

    // Additional code ...
}
```

Você também precisará de um DbContext que represente uma sessão com o banco de dados. Para o microsserviço de catálogo, a classe CatalogContext é derivada da classe base DbContext, conforme é mostrado no exemplo a seguir:

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

É possível ter implementações adicionais do `DbContext`. Por exemplo, no microsserviço Catalog.API de exemplo, há um segundo `DbContext` chamado `CatalogContextSeed` no qual ele populará automaticamente os dados de exemplo na primeira vez que tentar acessar o banco de dados. Esse método é útil para dados de demonstração e também para cenários de teste automatizados. Dentro do `DbContext`, use o método `OnModelCreating` para personalizar os mapeamentos de entidade de banco de dados/objeto com e outros [pontos de extensibilidade do EF](https://blogs.msdn.microsoft.com/dotnet/2016/09/29/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).

##### <a name="querying-data-from-web-api-controllers"></a>Consultando dados de controladores da API Web

As instâncias das classes de entidade normalmente são recuperadas do banco de dados usando LINQ (consulta integrada à linguagem), conforme é mostrado no exemplo a seguir:

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
        _catalogIntegrationEventService = catalogIntegrationEventService ?? throw new ArgumentNullException(nameof(catalogIntegrationEventService));

        _settings = settings.Value;
        ((DbContext)context).ChangeTracker.QueryTrackingBehavior = QueryTrackingBehavior.NoTracking;
    }

    // GET api/v1/[controller]/items[?pageSize=3&pageIndex=10]
    [HttpGet]
    [Route("[action]")]
    [ProducesResponseType(typeof(PaginatedItemsViewModel<CatalogItem>), (int)HttpStatusCode.OK)]
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

##### <a name="saving-data"></a>Salvar dados

Dados são criados, excluídos e modificados no banco de dados usando as instâncias de suas classes de entidade. Você poderia adicionar um código como o exemplo embutido em código a seguir (dados fictícios, neste caso) aos controladores da API Web.

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
                                     Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a>Injeção de dependência nos controladores da API Web e do ASP.NET Core

Na ASP.NET Core, você pode usar a DI (injeção de dependência) pronta para uso. Não é necessário configurar um contêiner de IoC (inversão de controle) de terceiros, embora seja possível conectar o contêiner de IoC de sua preferência à infraestrutura do ASP.NET Core, caso deseje. Nesse caso, isso significa que você pode injetar diretamente o DBContext do EF necessário ou repositórios adicionais por meio do construtor do controlador. No exemplo da classe `CatalogController` acima, estamos injetando um objeto do tipo `CatalogContext` além de outros objetos por meio do construtor `CatalogController()`.

Uma configuração importante a ser definida no projeto de API Web é o registro da classe DbContext no contêiner de IoC do serviço. Normalmente isso é feito na classe `Startup` chamando o método `services.AddDbContext<DbContext>()` dentro do método `ConfigureServices()`, conforme é mostrado no exemplo a seguir:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // Additional code...

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

-   **Consultando Dados**
    [*https://docs.microsoft.com/ef/core/querying/index*](https://docs.microsoft.com/ef/core/querying/index)

-   **Salvando Dados**
    [*https://docs.microsoft.com/ef/core/saving/index*](https://docs.microsoft.com/ef/core/saving/index)

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a>A cadeia de conexão e as variáveis de ambiente do BD usadas pelos contêineres do Docker

É possível usar as configurações do ASP.NET Core e adicionar uma propriedade ConnectionString no arquivo settings.json, conforme é mostrado no exemplo a seguir:

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

O arquivo settings.json pode ter valores padrão para a propriedade ConnectionString ou para qualquer outra propriedade. No entanto, essas propriedades serão substituídas pelos valores das variáveis de ambiente que você especificar no arquivo docker-compose.override.yml, ao usar o Docker.

Usando os arquivos docker-compose.yml ou docker-compose.override.yml, é possível inicializar essas variáveis de ambiente para que o Docker as configure como variáveis de ambiente do sistema operacional, como é mostrado no seguinte arquivo docker-compose.override.yml (a cadeia de conexão e as outras linhas estão quebradas automaticamente neste exemplo, mas elas não seriam quebradas automaticamente no seu arquivo de código real).

```yml
# docker-compose.override.yml

#
catalog.api:
  environment:
    - ConnectionString=Server=sql.data;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word
    # Additional environment variables for this service
  ports:
    - "5101:80"
```

Os arquivos docker-compose.yml no nível da solução não são apenas mais flexíveis do que os arquivos de configuração no nível do projeto ou do microsserviço, mas também mais seguros se você substitui as variáveis de ambiente declaradas nos arquivos docker-compose pelos valores definidos pelas ferramentas de implantação, como as tarefas de implantação do Docker do VSTS. 

Por fim, você pode obter esse valor do código usando Configuration\["ConnectionString"\], como foi mostrado no método ConfigureServices em um exemplo de código anterior.

No entanto, para ambientes de produção, é recomendável explorar outras maneiras de armazenar segredos como as cadeias de conexão. Geralmente isso será gerenciado pelo orquestrador escolhido, por exemplo, usando o [gerenciamento de segredos Docker Swarm](https://docs.docker.com/engine/swarm/secrets/).

### <a name="implementing-versioning-in-aspnet-web-apis"></a>Implementando o controle de versão em APIs Web ASP.NET

À medida que os requisitos de negócios mudam, novas coleções de recursos podem ser adicionadas, as relações entre os recursos podem mudar e a estrutura dos dados nos recursos pode ser corrigida. Atualizar uma API Web para lidar com novos requisitos é um processo relativamente simples, mas você precisa considerar os efeitos que essas alterações causarão nos aplicativos cliente que consomem a API Web. Embora o desenvolvedor que projeta e implementa uma API Web tenha o controle total sobre essa API, ele não tem o mesmo nível de controle sobre aplicativos cliente que possam ter sido criados por organizações terceiras operando remotamente.

O controle de versão permite que uma API Web indique as funcionalidades e os recursos que ela expõe. Assim, um aplicativo cliente pode enviar solicitações para uma versão específica de uma funcionalidade ou de um recurso. Há várias abordagens para implementar o controle de versão:

-   Controle de versão de URI

-   Controle de versão de cadeia de caracteres de consulta

-   Controle de versão de cabeçalho

O controle de versão de cadeia de caracteres de consulta e de URI são os mais simples de implementar. O controle de versão de cabeçalho é uma boa abordagem. No entanto, o controle de versão de cabeçalho não é tão explícito e simples como o controle de versão de URI. Como o controle de versão de URL é o mais simples e o mais explícito, o aplicativo de exemplo eShopOnContainers usa esse o controle de versão de URI.

Com o controle de versão de URI, como no aplicativo de exemplo eShopOnContainers, sempre que você modificar a API Web ou alterar o esquema de recursos, você adicionará um número de versão ao URI de cada recurso. Os URIs existentes devem continuar a operar como antes, retornando os recursos que estão em conformidade com o esquema que corresponde à versão solicitada.

Conforme será mostrado no exemplo de código a seguir, a versão pode ser definida usando o atributo de rota na API Web, o que torna a versão explícita no URI (v1 neste caso).

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

Esse mecanismo de controle de versão é simples e depende do roteamento que o servidor faz da solicitação para o ponto de extremidade apropriado. No entanto, para obter um controle de versão mais sofisticado, e o melhor método ao usar o REST, você deve usar hipermídia e implementar o [HATEOAS (Hypertext as the Engine of Application State)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#using-the-hateoas-approach-to-enable-navigation-to-related-resources).

### <a name="additional-resources"></a>Recursos adicionais

-   **Scott Hanselman. Facilitando o controle de versão da API Web RESTful do ASP.NET Core**
    [*https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx*](https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx)

-   **Controle de versão de uma API Web RESTful**
    [*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)

-   **Roy Fielding. Controle de versão, hipermídia e REST**
    [*https://www.infoq.com/articles/roy-fielding-on-versioning*](https://www.infoq.com/articles/roy-fielding-on-versioning)

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a>Gerando metadados de descrição do Swagger para a API Web ASP.NET Core 

O [Swagger](https://swagger.io/) é uma estrutura de software livre muito usada, apoiada por um grande ecossistema de ferramentas que ajuda a projetar, compilar, documentar e consumir APIs RESTful. Ele está se tornando o padrão no domínio de metadados de descrição de APIs. Você deve incluir os metadados de descrição do Swagger em qualquer tipo de microsserviço, seja ele um microsserviço controlado por dados ou um mais avançado orientado por domínio (conforme será explicado na seção a seguir).

A essência do Swagger é a especificação do Swagger, que são metadados de descrição de API em um arquivo JSON ou YAML. A especificação cria o contrato RESTful para a API, detalhando todos os recursos e as operações em dois formatos, legível por pessoas e legível por computadores, para facilitar o desenvolvimento, a descoberta e a integração.

A especificação é a base da OAS (especificação OpenAPI) e é desenvolvida em uma comunidade aberta, transparente e colaborativa para padronizar a maneira que as interfaces RESTful são definidas.

A especificação define a estrutura de como um serviço pode ser descoberto e como seus recursos são entendidos. Para obter mais informações, incluindo um editor na Web e exemplos de especificações do Swagger de empresas como Spotify, Uber, Slack e Microsoft, consulte o site do Swagger (<https://swagger.io/>).

### <a name="why-use-swagger"></a>Por que usar Swagger?

As principais razões para gerar metadados do Swagger para suas APIs são as seguintes.

**Capacidade para outros produtos consumirem e integrarem suas APIs automaticamente**. Dezenas de produtos e [ferramentas comerciais](https://swagger.io/commercial-tools/) e diversas [estruturas e bibliotecas](https://swagger.io/open-source-integrations/) são compatíveis com o Swagger. A Microsoft tem produtos e ferramentas de alto nível que podem consumir automaticamente as APIs baseadas no Swagger, como os seguintes:

-   [AutoRest](https://github.com/Azure/AutoRest). É possível gerar classes de cliente do .NET automaticamente para chamar o Swagger. Essa ferramenta pode ser usada na CLI e também se integra ao Visual Studio, facilitando o uso por meio da GUI.

-   [Microsoft Flow](https://flow.microsoft.com/en-us/). É possível [usar e integrar sua API](https://flow.microsoft.com/en-us/blog/integrating-custom-api/) automaticamente em um fluxo de trabalho do Microsoft Flow de alto nível, sem precisar de nenhuma habilidade de programação.

-   [Microsoft PowerApps](https://powerapps.microsoft.com/en-us/). É possível consumir a API Automaticamente de [aplicativos móveis PowerApps](https://powerapps.microsoft.com/en-us/blog/register-and-use-custom-apis-in-powerapps/) criados com o [PowerApps Studio](https://powerapps.microsoft.com/en-us/guided-learning/learning-powerapps-parts/), sem precisar de nenhuma habilidade de programação.

-   [Aplicativos Lógicos do Serviço de Aplicativo do Azure](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps). É possível [usar e integrar sua API a um Aplicativo Lógico do Serviço de Aplicativo do Azure](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api) automaticamente, sem precisar de nenhuma habilidade de programação.

**Capacidade de gerar a documentação da API automaticamente**. Ao criar APIs RESTful em grande escala, como aplicativos complexos baseados em microsserviços, você precisa lidar com vários pontos de extremidade com modelos de dados diferentes usados no conteúdo de solicitação e de resposta. Ter uma documentação adequada e um gerenciador de API sólido, como o Swagger oferece, é fundamental para o sucesso da API e da adoção pelos desenvolvedores.

Os metadados do Swagger são o que os Aplicativo Lógico do Azure, o PowerApps e o Microsoft Flow usam para entender como usar as APIs e conectar-se a elas.

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a>Como automatizar a geração de metadados do Swagger para a API com o pacote NuGet Swashbuckle

A geração manual de metadados do Swagger (em um arquivo JSON ou YAML) pode ser um trabalho entediante. No entanto, é possível automatizar a descoberta de serviços do ASP.NET Web API usando o [pacote NuGet Swashbuckle](https://aka.ms/swashbuckledotnetcore) para gerar dinamicamente os metadados do Swagger para a API.

O Swashbuckle gera automaticamente os metadados do Swagger para os projetos do ASP.NET Web API. Ele é compatível com projetos da API Web ASP.NET Core, do ASP.NET Web API tradicional e de outros tipos, como os microsserviços de Aplicativo de API do Azure, Aplicativo Móvel Azure, Azure Service Fabric com base no ASP.NET. Ele também é compatível com a API Web simples implantada em contêineres, como no aplicativo de referência.

O Swashbuckle combina o Gerenciador de API e o Swagger ou o [swagger-ui](https://github.com/swagger-api/swagger-ui) para fornecer uma experiência avançada de descoberta e de documentação aos consumidores da API. Além do mecanismo gerador de metadados do Swagger, o Swashbuckle também contém uma versão incorporada do swagger-ui, que ele oferecerá automaticamente quando for instalado.

Isso significa que você pode complementar a API com uma ótima interface do usuário de descoberta para ajudar os desenvolvedores a usarem a API. Isso exige uma quantidade muito pequena de código e manutenção porque ela é gerada automaticamente, permitindo que você se concentre na API. O resultado do Gerenciador de API é semelhante ao da Figura 8-8.

![](./media/image9.png)

**Figura 8-8**. Gerenciador de API do Swashbuckle baseado nos metadados do Swagger – microsserviço de catálogo do eShopOnContainers

O Gerenciador de API não é o mais importante aqui. Quando a API Web consegue se descrever nos metadados do Swagger, ela pode ser usada diretamente por meio das ferramentas baseadas no Swagger, incluindo geradores de código de classe de proxy de cliente que podem direcionar a várias plataformas. Por exemplo, conforme mencionado, o [AutoRest](https://github.com/Azure/AutoRest) gera as classes de cliente do .NET automaticamente. Mas ferramentas adicionais como [swagger-codegen](https://github.com/swagger-api/swagger-codegen) também estão disponíveis, permitindo automaticamente a geração de código das bibliotecas clientes da API, de stubs de servidor e da documentação.

Atualmente, o Swashbuckle consiste em vários pacotes NuGet internos no metapacote de alto nível [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore/) versão 1.0.0 ou posteriores para aplicativos ASP.NET Core.

Depois de instalar esses pacotes NuGet em seu projeto de API Web, você precisará configurar o Swagger na classe de inicialização, como no código a seguir:

```csharp
public class Startup
{
    public IConfigurationRoot Configuration { get; }
    // Other startup code...

    public void ConfigureServices(IServiceCollection services)
    {
        // Other ConfigureServices() code...

        // Add framework services.
        services.AddSwaggerGen(options =>
        {
            options.DescribeAllEnumsAsStrings();
            options.SwaggerDoc("v1", new Swashbuckle.AspNetCore.Swagger.Info
            {
                Title = "eShopOnContainers - Catalog HTTP API",
                Version = "v1",
                Description = "The Catalog Microservice HTTP API. This is a Data-Driven/CRUD microservice sample",
                TermsOfService = "Terms Of Service"
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
            .UseSwaggerUI(c =>
            {
                c.SwaggerEndpoint("/swagger/v1/swagger.json", "My API V1");
            });
    }
}
```

Depois que isso for feito, você poderá iniciar o aplicativo e procurar o JSON do Swagger e os pontos de extremidade da interface do usuário usando URLs como estas:

```json
  http://<your-root-url>/swagger/v1/swagger.json
  
  http://<your-root-url>/swagger/
```

Você já viu a interface do usuário gerada, criada pelo Swashbuckle para uma URL como http://&lt;your-root-url&gt;/swagger/ui. Na Figura 8-9, veja também como é possível testar qualquer método de API.

![](./media/image10.png)

**Figura 8-9**. Interface do usuário do Swashbuckle testando o método da API de itens/catálogo

A Figura 8-10 mostra os metadados JSON do Swagger gerados por meio do microsserviço eShopOnContainers (que é o que as ferramentas usam nos bastidores) quando você solicita &lt;sua-url-raiz&gt;/swagger/v1/swagger.json usando o [Postman](https://www.getpostman.com/).

![](./media/image11.png)

**Figura 8-10**. Metadados JSON do Swagger

É simples assim. E como são gerados automaticamente, os metadados do Swagger aumentarão à medida que você adicionar mais funcionalidades à API.

### <a name="additional-resources"></a>Recursos adicionais

-   **Páginas de Ajuda do ASP.NET Web API usando o Swagger**
    [*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger*](https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger)


>[!div class="step-by-step"]
[Anterior](microservice-application-design.md)
[Próximo](multi-container-applications-docker-compose.md)
