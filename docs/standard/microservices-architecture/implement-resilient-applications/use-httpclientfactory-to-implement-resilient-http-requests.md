---
title: Usar HttpClientFactory implementar solicitações HTTP resilientes
description: HttpClientFactory é um alocador "teimoso", disponível desde o .NET Core 2.1, para a criação de instâncias do `HttpClient` a serem usadas nos aplicativos.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 07/03/2018
ms.openlocfilehash: 0ae4dadd6921a71217b50757ede19b8d54910185
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611029"
---
# <a name="use-httpclientfactory-to-implement-resilient-http-requests"></a>Usar HttpClientFactory implementar solicitações HTTP resilientes

`HttpClientFactory` é um alocador "teimoso", disponível desde o .NET Core 2.1, para a criação de instâncias do `HttpClient` a serem usadas nos aplicativos. 

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a>Problemas com a classe HttpClient original disponível no .NET Core

A classe [HttpClient](https://docs.microsoft.com/dotnet/api/system.net.http.httpclient?view=netstandard-2.0) original e conhecida pode ser usada com facilidade, mas em alguns casos, ela não está sendo usada corretamente por muitos desenvolvedores. 

Como um primeiro problema, embora essa classe seja descartável, usá-la com a instrução `using` não é a melhor opção porque, mesmo quando você descarta o objeto `HttpClient`, o soquete subjacente não é liberado imediatamente e pode causar um problema sério chamado 'esgotamento de soquetes'. Para obter mais informações sobre esse problema, confira a postagem no blog [You're using HttpClient wrong and it is destabilizing your software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) (Você está usando o HttpClient de forma errada e ele está desestabilizando o software).

Portanto, `HttpClient` deve ser instanciado uma única vez e reutilizado durante a vida útil de um aplicativo. A criação de uma instância de uma classe `HttpClient` para cada solicitação esgotará o número de soquetes disponíveis em condições de carga pesada. Esse problema resultará em erros de `SocketException`. Abordagens possíveis para resolver o problema baseiam-se na criação do objeto `HttpClient` como singleton ou estático, conforme é explicado neste [artigo da Microsoft sobre o uso do HttpClient](https://docs.microsoft.com/dotnet/csharp/tutorials/console-webapiclient). 

Mas há um segundo problema com o `HttpClient` que pode ocorrer quando ele é usado como um objeto singleton ou estático. Nesse caso, um `HttpClient` singleton ou estático não respeita as alterações de DNS, conforme é explicado neste [problema no repositório do GitHub do .NET Core](https://github.com/dotnet/corefx/issues/11224). 

Para resolver esses problemas mencionados e simplificar o gerenciamento das instâncias do `HttpClient` com mais facilidade, o .NET Core 2.1 oferece um novo `HttpClientFactory` que também pode ser usado para implementar chamadas HTTP resilientes, integrando a Polly a ele.   

## <a name="what-is-httpclientfactory"></a>O que é o HttpClientFactory

O `HttpClientFactory` foi projetado para:

- Fornecer um local central para nomear e configurar HttpClients lógicos. Por exemplo, você pode configurar um cliente (agente de serviço) pré-configurado para acessar um microsserviço específico.
- Codificar o conceito de middleware de saída por meio da delegação de manipuladores no `HttpClient` e da implementação de middleware baseado em Polly para aproveitar as políticas da Polly e garantir a resiliência.
- O `HttpClient` já tem o conceito de delegar manipuladores que podem ser vinculados uns aos outros para solicitações HTTP de saída. Você registra os clientes HTTP no alocador e usa um manipulador da Polly que permite que as políticas da Polly sejam usadas para repetição, CircuitBreakers, etc.
- Gerenciar o tempo de vida de HttpClientMessageHandlers para evitar os problemas mencionado que podem ocorrer ao gerenciar o tempo de vida do `HttpClient` por conta própria. 

## <a name="multiple-ways-to-use-httpclientfactory"></a>Várias maneiras de usar o HttpClientFactory

Há várias maneiras de usar o `HttpClientFactory` no aplicativo:

- Usar o `HttpClientFactory` diretamente
- Usar clientes nomeados
- Usar clientes tipados
- Usar clientes gerados

Para ser mais breve, estas diretrizes mostram apenas a maneira mais estruturada de usar o `HttpClientFactory`, que é usar clientes tipados (o padrão do agente de serviço), mas todas as outras opções estão documentadas e listadas neste [artigo que aborda o uso de HttpClientFactory](https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?#consumption-patterns) no momento.  

## <a name="how-to-use-typed-clients-with-httpclientfactory"></a>Como usar clientes tipados com HttpClientFactory

O diagrama a seguir mostra como os clientes tipados são usados com o HttpClientFactory.

![Diagrama com um controlador MVC usando um ClientService injetado, que, internamente, está usando um HttpClient configurado pelo HttpClientFactory e por políticas da Polly](./media/image3.5.png)

**Figura 10-4**. Usando `HttpClientFactory` com classes de cliente tipado.

Primeiro, configure `HttpClientFactory` em seu aplicativo. Adicione uma referência ao pacote `Microsoft.Extensions.Http` que inclua o método de extensão `AddHttpClient()` em `IServiceCollection`. Esse método de extensão registra o `DefaultHttpClientFactory` a ser usado como um singleton da interface `IHttpClientFactory`. Ele define uma configuração transitória para o `HttpMessageHandlerBuilder`. Esse manipulador de mensagens (objeto `HttpMessageHandler`), obtido de um pool, é usado pelo `HttpClient` retornado do alocador.

No próximo código, veja como `AddHttpClient()` pode ser usado para registrar clientes tipados (agentes de serviço) que precisam usar `HttpClient`.

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services) 
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

Basta adicionar suas classes de cliente tipado com AddHttpClient(), para que sempre que você usar o objeto `HttpClient` que será injetado na classe por seu construtor, esse objeto `HttpClient` use todas as configurações e políticas fornecidas. Nas próximas seções, você verá essas políticas, como repetições ou disjuntores da Polly.

### <a name="httpclient-lifetimes"></a>Tempos de vida de HttpClient

Sempre que você receber um objeto `HttpClient` do IHttpClientFactory, uma nova instância de um `HttpClient` será retornada. Haverá um **HttpMessageHandler** para cada cliente nomeado tipado. O `IHttpClientFactory` fará o pool das instâncias de HttpMessageHandler criadas pelo alocador para reduzir o consumo de recursos. Uma instância de HttpMessageHandler poderá ser reutilizada do pool quando uma nova instância de `HttpClient` for criada e seu tempo de vida ainda não tiver expirado.

O pooling de manipuladores é interessante porque cada manipulador normalmente gerencia suas próprias conexões de HTTP subjacentes. Criar mais manipuladores do que o necessário pode resultar em atrasos de conexão. Alguns manipuladores também mantêm as conexões abertas indefinidamente, o que pode impedir que o manipulador reaja a alterações de DNS.

Os objetos HttpMessageHandler no pool têm um tempo de vida que corresponde ao período de tempo em que a instância de HttpMessageHandler no pool pode ser reutilizada. O valor padrão é de dois minutos, mas pode ser substituído para cada cliente nomeado ou tipado. Para substituí-lo, chame SetHandlerLifetime() no IHttpClientBuilder que é retornado quando o cliente é criado, conforme é mostrado no código a seguir.

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client 
services.AddHttpClient<ICatalogService, CatalogService>()
                 .SetHandlerLifetime(TimeSpan.FromMinutes(5));  
```

Cada cliente tipado ou nomeado pode ter seu próprio valor de tempo de vida do manipulador configurado. Defina o tempo de vida para InfiniteTimeSpan para desabilitar a expiração do manipulador.

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a>Implementar suas classes de cliente tipado que usam o HttpClient injetado e configurado

Como uma etapa anterior, você precisa ter definido suas classes de cliente tipado, como as classes no código de exemplo: 'BasketService', 'CatalogService', 'OrderingService', etc. Um cliente tipado é uma classe que aceita um objeto `HttpClient` (injetado por seu construtor) e o usa para chamar algum serviço HTTP remoto. Por exemplo:

```csharp
public class CatalogService : ICatalogService
{
    private readonly HttpClient _httpClient;
    private readonly string _remoteServiceBaseUrl;

    public CatalogService(HttpClient httpClient)
    {
        _httpClient = httpClient;
    }

    public async Task<Catalog> GetCatalogItems(int page, int take, 
                                               int? brand, int? type)
    {
        var uri = API.Catalog.GetAllCatalogItems(_remoteServiceBaseUrl, 
                                                 page, take, brand, type);

        var responseString = await _httpClient.GetStringAsync(uri);

        var catalog = JsonConvert.DeserializeObject<Catalog>(responseString);
        return catalog;
    }
}
```

O cliente tipado (CatalogService, no exemplo) é ativado pela DI (injeção de dependência), o que significa que ele pode aceitar qualquer serviço registrado em seu construtor, além do HttpClient.

Um cliente tipado é, efetivamente, um objeto transitório, o que significa que uma nova instância é criada sempre que necessário e recebe uma nova instância de `HttpClient` sempre que é construída. No entanto, os objetos HttpMessageHandler no pool são os objetos que são reutilizados por várias solicitações HTTP.

### <a name="use-your-typed-client-classes"></a>Usar suas classes de cliente tipado

Por fim, depois que suas classes tipadas são implementadas e registradas no AddHttpClient(), você pode usá-las em qualquer lugar em os serviços possam ser injetados pela DI, por exemplo, em qualquer código de Razor Page ou em qualquer controlador de um aplicativo Web MVC, como no código a seguir do eShopOnContainers.

```csharp
namespace Microsoft.eShopOnContainers.WebMVC.Controllers
{
    public class CatalogController : Controller
    {
        private ICatalogService _catalogSvc;

        public CatalogController(ICatalogService catalogSvc) => 
                                                           _catalogSvc = catalogSvc;

        public async Task<IActionResult> Index(int? BrandFilterApplied, 
                                               int? TypesFilterApplied, 
                                               int? page, 
                                               [FromQuery]string errorMsg)
        {
            var itemsPage = 10;
            var catalog = await _catalogSvc.GetCatalogItems(page ?? 0, 
                                                            itemsPage, 
                                                            BrandFilterApplied, 
                                                            TypesFilterApplied);
            //… Additional code
        }

        }
}
```

Até este ponto, o código mostrado está apenas executando solicitações HTTP regulares, mas a 'mágica' vem nas seções a seguir, em que, basta adicionar políticas e delegar manipuladores para os clientes tipados registrados, para que todas as solicitações HTTP realizadas por `HttpClient` se comportem considerando políticas resilientes, como repetições com retirada exponencial, disjuntores ou qualquer outro manipulador delegado personalizado para implementar recursos de segurança adicionais, como o uso de tokens de autenticação ou qualquer outro recurso personalizado. 


## <a name="additional-resources"></a>Recursos adicionais

-   **Usando HttpClientFactory no .NET Core 2.1**
    [*https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1*](https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1)


-   **Repositório do GitHub do HttpClientFactory**

    [*https://github.com/aspnet/HttpClientFactory*](https://github.com/aspnet/HttpClientFactory)

>[!div class="step-by-step"]
>[Anterior](explore-custom-http-call-retries-exponential-backoff.md)
>[Próximo](implement-http-call-retries-exponential-backoff-polly.md)
