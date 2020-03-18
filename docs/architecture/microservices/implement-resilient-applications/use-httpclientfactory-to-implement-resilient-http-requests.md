---
title: Use ihttpClientFactory para implementar solicitações HTTP resilientes
description: Aprenda a usar o IHttpClientFactory, disponível desde o `HttpClient` .NET Core 2.1, para criar instâncias, facilitando o uso em seus aplicativos.
ms.date: 03/03/2020
ms.openlocfilehash: 088fb6c7e10ad656247ee4065da5c13d383b2cf7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847213"
---
# <a name="use-ihttpclientfactory-to-implement-resilient-http-requests"></a>Use ihttpClientFactory para implementar solicitações HTTP resilientes

<xref:System.Net.Http.IHttpClientFactory>é um contrato `DefaultHttpClientFactory`implementado por , uma fábrica opinativa, disponível <xref:System.Net.Http.HttpClient> desde .NET Core 2.1, para criar instâncias a serem usadas em seus aplicativos.

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a>Problemas com a classe HttpClient original disponível no .NET Core

A classe original <xref:System.Net.Http.HttpClient> e bem conhecida pode ser facilmente usada, mas em alguns casos, não está sendo usada corretamente por muitos desenvolvedores.

Embora esta classe `IDisposable`implemente , declarando-o `using` e instanciando-o dentro de uma declaração não é preferível porque quando o `HttpClient` objeto é eliminado, o soquete subjacente não é imediatamente liberado, o que pode levar a um problema de _exaustão do soquete._ Para obter mais informações sobre este problema, consulte o post do blog [Você está usando httpClient errado e está desestabilizando seu software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/).

Portanto, `HttpClient` deve ser instanciado uma única vez e reutilizado durante a vida útil de um aplicativo. A criação de uma instância de uma classe `HttpClient` para cada solicitação esgotará o número de soquetes disponíveis em condições de carga pesada. Esse problema resultará em erros de `SocketException`. Abordagens possíveis para resolver o problema baseiam-se na criação do objeto `HttpClient` como singleton ou estático, conforme é explicado neste [artigo da Microsoft sobre o uso do HttpClient](../../../csharp/tutorials/console-webapiclient.md). Esta pode ser uma boa solução para aplicativos de console de curta duração ou similares que são executados algumas vezes por dia.

Outro problema que os desenvolvedores se deparam é ao usar uma instância compartilhada de processos de `HttpClient` longo prazo. Em uma situação em que o HttpClient é instanciado como um singleton ou um objeto estático, ele não consegue lidar com as alterações de DNS como descrito nesta [edição](https://github.com/dotnet/corefx/issues/11224) do repositório dotnet/corefx GitHub.

No entanto, o problema `HttpClient` não é realmente com per se, mas com o <xref:System.Net.Http.HttpMessageHandler>construtor padrão para [HttpClient](https://docs.microsoft.com/dotnet/api/system.net.http.httpclient.-ctor?view=netcore-3.1#System_Net_Http_HttpClient__ctor), porque cria uma nova instância concreta de , que é a que tem *soquetes exaustos* e dns altera problemas mencionados acima.

Para resolver os problemas mencionados acima e tornar `HttpClient` as instâncias <xref:System.Net.Http.IHttpClientFactory> gerenciáveis, o .NET `HttpClient` Core 2.1 introduziu a interface que pode ser usada para configurar e criar instâncias em um aplicativo através da Injeção de Dependência (DI). Ele também fornece extensões para middleware baseado em Polly para tirar proveito da delegar manipuladores em HttpClient.

[O Polly](http://www.thepollyproject.org/) é uma biblioteca de manipulação de falhas transitórias que ajuda os desenvolvedores a adicionar resiliência aos seus aplicativos, usando algumas políticas pré-definidas de forma fluente e segura de segmentos.

## <a name="benefits-of-using-ihttpclientfactory"></a>Benefícios de usar ihttpClientFactory

A implementação <xref:System.Net.Http.IHttpClientFactory>atual de <xref:System.Net.Http.IHttpMessageHandlerFactory>, que também implementa , oferece os seguintes benefícios:

- Fornece um local central para `HttpClient` nomear e configurar objetos lógicos. Por exemplo, você pode configurar um cliente (agente de serviço) pré-configurado para acessar um microsserviço específico.
- Codififique o conceito de middleware de saída `HttpClient` através de delegar manipuladores e implementar middleware baseado em Polly para tirar proveito das políticas de resiliência da Polly.
- O `HttpClient` já tem o conceito de delegar manipuladores que podem ser vinculados uns aos outros para solicitações HTTP de saída. Você pode registrar clientes HTTP na fábrica e pode usar um manipulador Polly para usar as políticas polly para Retry, CircuitBreakers e assim por diante.
- Gerencie a <xref:System.Net.Http.HttpMessageHandler> vida útil para evitar os problemas/problemas mencionados que podem ocorrer ao gerenciar `HttpClient` vidas sozinho.

> [!TIP]
> As `HttpClient` instâncias injetadas por DI, podem ser descartadas com segurança, pois as associadas `HttpMessageHandler` são gerenciadas pela fábrica. Na verdade, as instâncias injetadas `HttpClient` são escopo *de* uma perspectiva DI.

> [!NOTE]
> A implementação de `IHttpClientFactory` (`DefaultHttpClientFactory`) está fortemente `Microsoft.Extensions.DependencyInjection` ligada à implementação di no pacote NuGet. Para obter mais informações sobre o uso de outros contêineres DI, consulte esta [discussão do GitHub](https://github.com/dotnet/extensions/issues/1345).

## <a name="multiple-ways-to-use-ihttpclientfactory"></a>Várias maneiras de usar ihttpClientFactory

Há várias maneiras de usar o `IHttpClientFactory` no aplicativo:

- Uso básico
- Usar clientes nomeados
- Usar clientes tipados
- Usar clientes gerados

Por uma questão de brevidade, essa orientação `IHttpClientFactory`mostra a maneira mais estruturada de usar, que é usar clientes digitados (padrão de Agente de Serviço). No entanto, todas as opções estão documentadas e estão atualmente listadas neste [artigo cobrindo o `IHttpClientFactory` uso](/aspnet/core/fundamentals/http-requests#consumption-patterns).

## <a name="how-to-use-typed-clients-with-ihttpclientfactory"></a>Como usar clientes digitados com IHttpClientFactory

Portanto, o que é um "cliente tipado"? É apenas um `HttpClient` que está pré-configurado para algum uso específico. Essa configuração pode incluir valores específicos, como o servidor base, cabeçalhos HTTP ou intervalos de tempo.

O diagrama a seguir mostra como os clientes tipados são usados com o `IHttpClientFactory`:

![Diagrama mostrando como os clientes digitados são usados com IHttpClientFactory.](./media/use-httpclientfactory-to-implement-resilient-http-requests/client-application-code.png)

**Figura 8-4**. Usando `IHttpClientFactory` com classes de cliente digitado.

Na imagem acima, `ClientService` a (usada por um controlador `HttpClient` ou código cliente) usa um criado pelo registrado `IHttpClientFactory`. Esta fábrica atribui `HttpMessageHandler` um de `HttpClient`uma piscina para o . O `HttpClient` pode ser configurado com as políticas `IHttpClientFactory` de Polly ao registrar <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*>o recipiente DI no recipiente DI com o método de extensão .

Para configurar a estrutura <xref:System.Net.Http.IHttpClientFactory> acima, adicione seu `Microsoft.Extensions.Http` aplicativo instalando o <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*> pacote NuGet que inclui o método de extensão para <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>. Este método de extensão registra a classe interna `DefaultHttpClientFactory` `IHttpClientFactory`a ser usada como singleton para a interface . Ele define uma configuração transitória para o <xref:Microsoft.Extensions.Http.HttpMessageHandlerBuilder>. Esse manipulador de mensagens (objeto <xref:System.Net.Http.HttpMessageHandler>), obtido de um pool, é usado pelo `HttpClient` retornado do alocador.

No próximo código, veja como `AddHttpClient()` pode ser usado para registrar clientes tipados (agentes de serviço) que precisam usar `HttpClient`.

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services)
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

Registrar os serviços do cliente como mostrado `DefaultClientFactory` no `HttpClient` código anterior, torna a criação um padrão para cada serviço.

Você também pode adicionar configuração específica de instância no registro para, por exemplo, configurar o endereço base e adicionar algumas políticas de resiliência, conforme mostrado no código a seguir:

```csharp
services.AddHttpClient<ICatalogService, CatalogService>(client =>
{
    client.BaseAddress = new Uri(Configuration["BaseUrl"]);
})
    .AddPolicyHandler(GetRetryPolicy())
    .AddPolicyHandler(GetCircuitBreakerPolicy());
```

Apenas por exemplo, você pode ver uma das políticas acima no próximo código:

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)));
}
```

Você pode encontrar mais detalhes sobre o uso de Polly no [artigo Next](implement-http-call-retries-exponential-backoff-polly.md).

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

Como etapa anterior, você precisa ter suas classes de Cliente Digitado definidas, como as classes no código de exemplo, como 'BasketService', 'CatalogService', 'OrderingService', etc. – Um Cliente Digitado é uma classe que aceita um `HttpClient` objeto (injetado através de seu construtor) e o usa para chamar algum serviço HTTP remoto. Por exemplo: 

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

O Cliente Digitado (`CatalogService` no exemplo) é ativado por DI (Dependency Injection), o que significa `HttpClient`que ele pode aceitar qualquer serviço registrado em sua construtora, além de .

Um cliente tipado é, efetivamente, um objeto transitório, o que significa que uma instância é criada sempre que necessário e recebe uma nova instância de `HttpClient` sempre que é construída. No entanto, os `HttpMessageHandler` objetos na piscina são `HttpClient` os objetos que são reutilizados por várias instâncias.

### <a name="use-your-typed-client-classes"></a>Usar suas classes de cliente tipado

Finalmente, uma vez que você tenha suas classes digitadas implementadas e tê-las registradas e configuradas com `AddHttpClient()`, você pode usá-las onde você pode ter serviços injetados por DI. Por exemplo, em um código de página razor ou controlador de um aplicativo web MVC, como no seguinte código do eShopOnContainers:

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

Até este ponto, o código mostrado está apenas executando solicitações http regulares, mas a 'mágica' vem nas seguintes seções onde, apenas adicionando políticas `HttpClient` e delegando manipuladores aos seus Clientes Digitados registrados, todas as solicitações HTTP a serem feitas se comportarão levando em conta políticas resilientes, como tentativas com backoff exponencial, disjuntores ou qualquer outro manipulador personalizado para implementar recursos de segurança adicionais, como usar tokens auth ou qualquer outro recurso personalizado.

## <a name="additional-resources"></a>Recursos adicionais

- **Usando HttpClientFactory no .NET Core**  
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests](/aspnet/core/fundamentals/http-requests)

- **Código-fonte httpClientFactory `dotnet/extensions` no repositório GitHub**  
  <https://github.com/dotnet/extensions/tree/master/src/HttpClientFactory>

- **Polly (biblioteca de tratamento de falhas transitórias e resiliência do .NET)**  
  <http://www.thepollyproject.org/>
  
- **Usando iHttpClientFactory sem injeção de dependência (problema do GitHub)**  
  <https://github.com/dotnet/extensions/issues/1345>

>[!div class="step-by-step"]
>[Próximo](implement-resilient-entity-framework-core-sql-connections.md)
>[anterior](implement-http-call-retries-exponential-backoff-polly.md)
