---
title: Use o IHttpClientFactory para implementar solicitações HTTP resilientes
description: Saiba como usar o IHttpClientFactory, disponível desde o .NET Core 2,1, para `HttpClient` criar instâncias, facilitando seu uso em seus aplicativos.
ms.date: 03/03/2020
ms.openlocfilehash: ade26208a931faa456c8e267def2caef7a3f32de
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507293"
---
# <a name="use-ihttpclientfactory-to-implement-resilient-http-requests"></a>Use o IHttpClientFactory para implementar solicitações HTTP resilientes

<xref:System.Net.Http.IHttpClientFactory>é um contrato implementado pelo `DefaultHttpClientFactory`, uma fábrica conceituada, disponível desde o .net Core 2,1, para <xref:System.Net.Http.HttpClient> a criação de instâncias a serem usadas em seus aplicativos.

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a>Problemas com a classe HttpClient original disponível no .NET Core

A classe original e conhecida <xref:System.Net.Http.HttpClient> pode ser facilmente usada, mas, em alguns casos, ela não está sendo usada corretamente por muitos desenvolvedores.

Embora essa `IDisposable`classe implemente, a declaração e a criação de `using` uma instância dele dentro de uma instrução `HttpClient` não é preferida porque, quando o objeto é Descartado, o soquete subjacente não é lançado imediatamente, o que pode levar a um problema de _esgotamento de soquete_ . Para obter mais informações sobre esse problema, consulte a postagem de blog [que você está usando HttpClient errado e está desestabilizando o software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/).

Portanto, `HttpClient` deve ser instanciado uma única vez e reutilizado durante a vida útil de um aplicativo. A criação de uma instância de uma classe `HttpClient` para cada solicitação esgotará o número de soquetes disponíveis em condições de carga pesada. Esse problema resultará em erros de `SocketException`. Abordagens possíveis para resolver o problema baseiam-se na criação do objeto `HttpClient` como singleton ou estático, conforme é explicado neste [artigo da Microsoft sobre o uso do HttpClient](../../../csharp/tutorials/console-webapiclient.md). Isso pode ser uma boa solução para aplicativos de console de curta duração ou semelhantes que são executadas algumas vezes por dia.

Outro problema que os desenvolvedores executam é ao usar uma instância compartilhada `HttpClient` do em processos de longa execução. Em uma situação em que o HttpClient é instanciado como um singleton ou um objeto estático, ele não lida com as alterações de DNS, conforme descrito neste [problema](https://github.com/dotnet/runtime/issues/18348) do repositório do GitHub de dotnet/tempo de execução.

No entanto, o problema não `HttpClient` é realmente com o por si, mas com o [construtor padrão para HttpClient](https://docs.microsoft.com/dotnet/api/system.net.http.httpclient.-ctor?view=netcore-3.1#System_Net_Http_HttpClient__ctor), porque ele cria uma <xref:System.Net.Http.HttpMessageHandler>nova instância concreta do, que é aquela que tem os problemas de *esgotamento de soquetes* e alterações de DNS mencionados acima.

Para resolver os problemas mencionados acima e tornar `HttpClient` as instâncias gerenciáveis, o .net Core 2,1 introduziu a <xref:System.Net.Http.IHttpClientFactory> interface que pode ser usada para configurar `HttpClient` e criar instâncias em um aplicativo por meio de injeção de dependência (di). Ele também fornece extensões para que o middleware baseado em Polly Aproveite a delegação de manipuladores no HttpClient.

O [Polly](http://www.thepollyproject.org/) é uma biblioteca de tratamento de falhas transitórias que ajuda os desenvolvedores a adicionar resiliência aos seus aplicativos, usando algumas políticas predefinidas de forma fluente e thread-safe.

## <a name="benefits-of-using-ihttpclientfactory"></a>Benefícios do uso do IHttpClientFactory

A implementação atual do <xref:System.Net.Http.IHttpClientFactory>, que também implementa <xref:System.Net.Http.IHttpMessageHandlerFactory>, oferece os seguintes benefícios:

- Fornece um local central para nomear e configurar `HttpClient` objetos lógicos. Por exemplo, você pode configurar um cliente (agente de serviço) pré-configurado para acessar um microsserviço específico.
- Codificar o conceito de middleware de saída por meio da delegação de manipuladores `HttpClient` no e implementação do middleware baseado em Polly para tirar proveito das políticas de Polly para resiliência.
- O `HttpClient` já tem o conceito de delegar manipuladores que podem ser vinculados uns aos outros para solicitações HTTP de saída. Você pode registrar clientes HTTP na fábrica e usar um manipulador Polly para usar políticas de Polly para repetir, CircuitBreakers e assim por diante.
- Gerencie o tempo <xref:System.Net.Http.HttpMessageHandler> de vida de para evitar problemas/problemas mencionados que podem ocorrer `HttpClient` ao gerenciar os tempos de vida por conta própria.

> [!TIP]
> As `HttpClient` instâncias injetadas por di podem ser descartadas de forma segura, porque o `HttpMessageHandler` associado é gerenciado pela fábrica. Na verdade, as `HttpClient` instâncias injetadas têm o *escopo* de uma perspectiva de di.

> [!NOTE]
> A implementação de `IHttpClientFactory` (`DefaultHttpClientFactory`) está rigidamente ligada à implementação de di no pacote `Microsoft.Extensions.DependencyInjection` NuGet. Para obter mais informações sobre como usar outros contêineres de DI, consulte esta [discussão do GitHub](https://github.com/dotnet/extensions/issues/1345).

## <a name="multiple-ways-to-use-ihttpclientfactory"></a>Várias maneiras de usar o IHttpClientFactory

Há várias maneiras de usar o `IHttpClientFactory` no aplicativo:

- Uso básico
- Usar clientes nomeados
- Usar clientes tipados
- Usar clientes gerados

Para fins de brevidade, essas diretrizes mostram a maneira mais estruturada de usar `IHttpClientFactory`, que é usar clientes digitados (padrão de agente de serviço). No entanto, todas as opções estão documentadas e estão listadas neste [artigo abordando `IHttpClientFactory` o uso](/aspnet/core/fundamentals/http-requests#consumption-patterns).

## <a name="how-to-use-typed-clients-with-ihttpclientfactory"></a>Como usar clientes digitados com IHttpClientFactory

Portanto, o que é um "cliente tipado"? É apenas um `HttpClient` que é pré-configurado para um uso específico. Essa configuração pode incluir valores específicos, como o servidor base, cabeçalhos HTTP ou tempos limite.

O diagrama a seguir mostra como os clientes tipados são usados com o `IHttpClientFactory`:

![Diagrama mostrando como os clientes digitados são usados com IHttpClientFactory.](./media/use-httpclientfactory-to-implement-resilient-http-requests/client-application-code.png)

**Figura 8-4**. Usando `IHttpClientFactory` com classes de cliente tipadas.

Na imagem acima, a `ClientService` (usada por um controlador ou código de cliente) usa um `HttpClient` criado pelo registrado. `IHttpClientFactory` Essa fábrica atribui um `HttpMessageHandler` de um pool ao. `HttpClient` O `HttpClient` pode ser configurado com as políticas do Polly ao registrar o `IHttpClientFactory` no contêiner di com o método <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*>de extensão.

Para configurar a estrutura acima, adicione <xref:System.Net.Http.IHttpClientFactory> em seu aplicativo instalando o `Microsoft.Extensions.Http` pacote NuGet que inclui o <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*> método de extensão <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>para. Esse método de extensão registra a `DefaultHttpClientFactory` classe interna a ser usada como um singleton para a `IHttpClientFactory`interface. Ele define uma configuração transitória para o <xref:Microsoft.Extensions.Http.HttpMessageHandlerBuilder>. Esse manipulador de mensagens (objeto <xref:System.Net.Http.HttpMessageHandler>), obtido de um pool, é usado pelo `HttpClient` retornado do alocador.

No próximo código, veja como `AddHttpClient()` pode ser usado para registrar clientes tipados (agentes de serviço) que precisam usar `HttpClient`.

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services)
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

O registro dos serviços do cliente, conforme mostrado no código anterior, faz `DefaultClientFactory` com que o `HttpClient` crie um padrão para cada serviço.

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

Os objetos `HttpMessageHandler` no pool têm um tempo de vida que é o período de tempo em que uma instância `HttpMessageHandler` no pool pode ser reutilizada. O valor padrão é dois minutos, mas pode ser substituído por cliente tipado. Para substituí-lo, chame `SetHandlerLifetime()` no <xref:Microsoft.Extensions.DependencyInjection.IHttpClientBuilder> que é retornado ao criar o cliente, como mostra o código a seguir:

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client
services.AddHttpClient<ICatalogService, CatalogService>()
    .SetHandlerLifetime(TimeSpan.FromMinutes(5));
```

Cada cliente tipado pode ter seu próprio valor de tempo de vida do manipulador configurado. Defina o tempo de vida como `InfiniteTimeSpan` para desabilitar a expiração do manipulador.

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a>Implementar suas classes de cliente tipado que usam o HttpClient injetado e configurado

Como uma etapa anterior, você precisa ter suas classes de cliente digitadas definidas, como as classes no código de exemplo, como ' BasketService ', ' CatalogService ', ' OrderingService ', etc. – um cliente tipado é uma classe que aceita `HttpClient` um objeto (injetado através de seu construtor) e o usa para chamar algum serviço http remoto. Por exemplo:

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

O cliente digitado`CatalogService` (no exemplo) é ativado por di (injeção de dependência), o que significa que ele pode aceitar qualquer serviço registrado em seu construtor, `HttpClient`além de.

Um cliente tipado é, efetivamente, um objeto transitório, o que significa que uma instância é criada sempre que necessário e recebe uma nova instância de `HttpClient` sempre que é construída. No entanto `HttpMessageHandler` , os objetos no pool são os objetos que são reutilizados `HttpClient` por várias instâncias.

### <a name="use-your-typed-client-classes"></a>Usar suas classes de cliente tipado

Por fim, depois de implementar as classes tipadas e tê-las registradas `AddHttpClient()`e configuradas com o, você poderá usá-las sempre que puder ter os serviços injetados por di. Por exemplo, em um código de página do Razor ou no controlador de um aplicativo Web MVC, como no código a seguir de eShopOnContainers:

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

Até esse ponto, o código mostrado está apenas executando solicitações HTTP regulares, mas a ' mágica ' vem nas seções a seguir, em que, apenas adicionando políticas e delegando manipuladores a seus clientes tipados registrados, todas as solicitações HTTP a serem feitas `HttpClient` por se comportarão levando em conta políticas resilientes, como repetições com retirada exponencial, separadores de circuito ou qualquer outro manipulador de delegação personalizado para implementar recursos de segurança adicionais, como usar tokens de autenticação ou qualquer outro recurso personalizado.

## <a name="additional-resources"></a>Recursos adicionais

- **Usando HttpClientFactory no .NET Core**  
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests](/aspnet/core/fundamentals/http-requests)

- **HttpClientFactory o `dotnet/extensions` código-fonte no repositório github**  
  <https://github.com/dotnet/extensions/tree/master/src/HttpClientFactory>

- **Polly (biblioteca de tratamento de falhas transitórias e resiliência do .NET)**  
  <http://www.thepollyproject.org/>
  
- **Usando IHttpClientFactory sem injeção de dependência (problema do GitHub)**  
  <https://github.com/dotnet/extensions/issues/1345>

>[!div class="step-by-step"]
>[Anterior](implement-resilient-entity-framework-core-sql-connections.md)
>[próximo](implement-http-call-retries-exponential-backoff-polly.md)
