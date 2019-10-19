---
title: Usar HttpClientFactory implementar solicitações HTTP resilientes
description: Saiba como usar o HttpClientFactory, disponível desde o .NET Core 2.1, para a criação de instâncias de `HttpClient`, facilitando o uso em seus aplicativos.
ms.date: 08/08/2019
ms.openlocfilehash: 3f9b3b18cede07e4c5c56600634ae230c0e251bb
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72578909"
---
# <a name="use-httpclientfactory-to-implement-resilient-http-requests"></a>Usar HttpClientFactory implementar solicitações HTTP resilientes

`HttpClientFactory` é um alocador "teimoso", disponível desde o .NET Core 2.1, para a criação de instâncias do <xref:System.Net.Http.HttpClient> a serem usadas nos aplicativos.

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a>Problemas com a classe HttpClient original disponível no .NET Core

A classe de <xref:System.Net.Http.HttpClient> original e conhecida pode ser facilmente usada, mas em alguns casos, ela não está sendo usada corretamente por muitos desenvolvedores.

Como um primeiro problema, embora essa classe seja descartável, usá-la com a instrução `using` não é a melhor opção porque, mesmo quando você descarta o objeto `HttpClient`, o soquete subjacente não é liberado imediatamente e pode causar um problema sério chamado 'esgotamento de soquetes'. Para obter mais informações sobre esse problema, confira a postagem no blog [You're using HttpClient wrong and it is destabilizing your software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) (Você está usando o HttpClient incorretamente e ele está desestabilizando o software).

Portanto, `HttpClient` deve ser instanciado uma única vez e reutilizado durante a vida útil de um aplicativo. A criação de uma instância de uma classe `HttpClient` para cada solicitação esgotará o número de soquetes disponíveis em condições de carga pesada. Esse problema resultará em erros de `SocketException`. Abordagens possíveis para resolver o problema baseiam-se na criação do objeto `HttpClient` como singleton ou estático, conforme é explicado neste [artigo da Microsoft sobre o uso do HttpClient](../../../csharp/tutorials/console-webapiclient.md).

Mas há um segundo problema com o `HttpClient` que pode ocorrer quando ele é usado como um objeto singleton ou estático. Nesse caso, um singleton ou `HttpClient` estático não respeitam as alterações de DNS, conforme explicado neste [problema](https://github.com/dotnet/corefx/issues/11224) no repositório do GitHub dotnet/corefx. 

Para resolver esses problemas mencionados e facilitar o gerenciamento das instâncias do `HttpClient`, o .NET Core 2.1 introduziu um novo `HttpClientFactory` que também pode ser usado para implementar chamadas HTTP resilientes pela integração do Polly a ele.

[Polly](http://www.thepollyproject.org/) é uma biblioteca de tratamento de falhas transitórias que ajuda os desenvolvedores a adicionar resiliência aos seus aplicativos, usando algumas políticas predefinidas de forma fluente e thread-safe.

## <a name="what-is-httpclientfactory"></a>O que é o HttpClientFactory

O `HttpClientFactory` foi projetado para:

- Forneça um local central para nomear e configurar objetos de `HttpClient` lógicos. Por exemplo, você pode configurar um cliente (agente de serviço) pré-configurado para acessar um microsserviço específico.
- Codificar o conceito de middleware de saída por meio da delegação de manipuladores no `HttpClient` e da implementação de middleware baseado em Polly para aproveitar as políticas da Polly e garantir a resiliência.
- O `HttpClient` já tem o conceito de delegar manipuladores que podem ser vinculados uns aos outros para solicitações HTTP de saída. Você registra clientes HTTP na fábrica e pode usar um manipulador Polly para usar políticas Polly para repetição, CircuitBreakers e assim por diante.
- Gerencie o tempo de vida de `HttpClientMessageHandlers` para evitar problemas/problemas mencionados que podem ocorrer ao gerenciar `HttpClient` os tempos de vida.

## <a name="multiple-ways-to-use-httpclientfactory"></a>Várias maneiras de usar o HttpClientFactory

Há várias maneiras de usar o `HttpClientFactory` no aplicativo:

- Usar o `HttpClientFactory` diretamente
- Usar clientes nomeados
- Usar clientes tipados
- Usar clientes gerados

Para fins de brevidade, essas diretrizes mostram a maneira mais estruturada de usar `HttpClientFactory`, que é usar clientes digitados (padrão de agente de serviço). No entanto, todas as opções estão documentadas e atualmente estão listadas neste [artigo cobrindo o uso do HttpClientFactory](/aspnet/core/fundamentals/http-requests#consumption-patterns).

## <a name="how-to-use-typed-clients-with-httpclientfactory"></a>Como usar clientes tipados com HttpClientFactory

Portanto, o que é um "cliente tipado"? É apenas um `HttpClient` que é configurado na injeção pelo `DefaultHttpClientFactory`.

O diagrama a seguir mostra como os clientes tipados são usados com o `HttpClientFactory`:

![Um ClientService (usado por um código de controlador ou cliente) usa um HttpClient criado pelo IHttpClientFactory registrado. Esse alocador atribui um HttpMessageHandler ao HttpClient de um pool que ele gerencia. O HttpClient pode ser configurado com políticas da Polly ao registrar o IHttpClientFactory no contêiner de injeção de dependência com o método de extensão AddHttpClient.](./media/image3.5.png)

**Figura 8-4**. Use o HttpClientFactory com classes de cliente tipado.

Primeiro, a instalação `HttpClientFactory` em seu aplicativo instalando o pacote NuGet do `Microsoft.Extensions.Http` que inclui o método de extensão `AddHttpClient()` para `IServiceCollection`. Esse método de extensão registra o `DefaultHttpClientFactory` a ser usado como um singleton da interface `IHttpClientFactory`. Ele define uma configuração transitória para o `HttpMessageHandlerBuilder`. Esse manipulador de mensagens (objeto `HttpMessageHandler`), obtido de um pool, é usado pelo `HttpClient` retornado do alocador.

No próximo código, veja como `AddHttpClient()` pode ser usado para registrar clientes tipados (agentes de serviço) que precisam usar `HttpClient`.

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services) 
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

O registro dos serviços do cliente, conforme mostrado no código anterior, torna o `DefaultClientFactory` criar um `HttpClient` padrão para cada serviço.

Você também pode adicionar a configuração específica da instância no registro para, por exemplo, configurar o endereço base e adicionar algumas políticas de resiliência, conforme mostrado no código a seguir:

```csharp
services.AddHttpClient<ICatalogService, CatalogService>(client =>
{
    client.BaseAddress = new Uri(Configuration["BaseUrl"]);
})
    .AddPolicyHandler(GetRetryPolicy())
    .AddPolicyHandler(GetCircuitBreakerPolicy());
```

Apenas para o exemplo, você pode ver uma das políticas acima no próximo código:

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)));
}
```

Você pode encontrar mais detalhes sobre como usar o Polly no [próximo artigo](implement-http-call-retries-exponential-backoff-polly.md).

### <a name="httpclient-lifetimes"></a>Tempos de vida de HttpClient

Sempre que você receber um objeto `HttpClient` do `IHttpClientFactory`, uma nova instância será retornada. Mas cada `HttpClient` usa um `HttpMessageHandler` que foi colocado em pool e reutilizado pelo `IHttpClientFactory` para reduzir o consumo de recursos, desde que o tempo de vida do `HttpMessageHandler` não tenha expirado.

O pooling de manipuladores é interessante porque cada manipulador normalmente gerencia suas próprias conexões de HTTP subjacentes. Criar mais manipuladores do que o necessário pode resultar em atrasos de conexão. Alguns manipuladores também mantêm as conexões abertas indefinidamente, o que pode impedir que o manipulador reaja a alterações de DNS.

Os objetos `HttpMessageHandler` no pool têm um tempo de vida que é o período de tempo em que uma instância `HttpMessageHandler` no pool pode ser reutilizada. O valor padrão é dois minutos, mas pode ser substituído por cliente tipado. Para substituí-lo, chame `SetHandlerLifetime()` no `IHttpClientBuilder` que é retornado ao criar o cliente, como mostra o código a seguir:

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client 
services.AddHttpClient<ICatalogService, CatalogService>()
    .SetHandlerLifetime(TimeSpan.FromMinutes(5));
```

Cada cliente tipado pode ter seu próprio valor de tempo de vida do manipulador configurado. Defina o tempo de vida como `InfiniteTimeSpan` para desabilitar a expiração do manipulador.

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

Um cliente tipado é, efetivamente, um objeto transitório, o que significa que uma instância é criada sempre que necessário e recebe uma nova instância de `HttpClient` sempre que é construída. No entanto, os objetos HttpMessageHandler no pool são os objetos que são reutilizados por várias solicitações HTTP.

### <a name="use-your-typed-client-classes"></a>Usar suas classes de cliente tipado

Por fim, depois de implementar as classes tipadas e tê-las registradas com `AddHttpClient()`, você poderá usá-las sempre que puder ter os serviços injetados por DI. Por exemplo, em um código de página do Razor ou no controlador de um aplicativo Web MVC, como no código a seguir de eShopOnContainers:

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

Até este ponto, o código mostrado está apenas executando solicitações HTTP regulares, mas a 'mágica' vem nas seções a seguir, em que, basta adicionar políticas e delegar manipuladores aos clientes tipados registrados, para que todas as solicitações HTTP realizadas por `HttpClient` se comportem considerando políticas resilientes, como repetições com retirada exponencial, disjuntores ou qualquer outro manipulador delegado personalizado para implementar recursos de segurança adicionais, como o uso de tokens de autenticação ou qualquer outro recurso personalizado.

## <a name="additional-resources"></a>Recursos adicionais

- **Usando HttpClientFactory no .NET Core** \
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests](/aspnet/core/fundamentals/http-requests)

- **Repositório HttpClientFactory do GitHub** \
  <https://github.com/aspnet/Extensions/tree/master/src/HttpClientFactory>

- **Polly (biblioteca de tratamento de falhas transitórias e resiliência do .NET)**  \
  <http://www.thepollyproject.org/>

>[!div class="step-by-step"]
>[Anterior](explore-custom-http-call-retries-exponential-backoff.md)
>[Próximo](implement-http-call-retries-exponential-backoff-polly.md)
