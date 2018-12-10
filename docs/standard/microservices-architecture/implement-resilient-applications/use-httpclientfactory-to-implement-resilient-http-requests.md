---
title: Usar HttpClientFactory implementar solicitações HTTP resilientes
description: HttpClientFactory é um alocador "teimoso", disponível desde o .NET Core 2.1, para a criação de instâncias do `HttpClient` a serem usadas nos aplicativos.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 07/03/2018
ms.openlocfilehash: 07ea85509b86eadd2c85dfe59ace674e2faae9a3
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53145105"
---
# <a name="use-httpclientfactory-to-implement-resilient-http-requests"></a><span data-ttu-id="87807-103">Usar HttpClientFactory implementar solicitações HTTP resilientes</span><span class="sxs-lookup"><span data-stu-id="87807-103">Use HttpClientFactory to implement resilient HTTP requests</span></span>

<span data-ttu-id="87807-104">`HttpClientFactory` é um alocador "teimoso", disponível desde o .NET Core 2.1, para a criação de instâncias do `HttpClient` a serem usadas nos aplicativos.</span><span class="sxs-lookup"><span data-stu-id="87807-104">`HttpClientFactory` is an opinionated factory, available since .NET Core 2.1, for creating `HttpClient` instances to be used in your applications.</span></span> 

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a><span data-ttu-id="87807-105">Problemas com a classe HttpClient original disponível no .NET Core</span><span class="sxs-lookup"><span data-stu-id="87807-105">Issues with the original HttpClient class available in .NET Core</span></span>

<span data-ttu-id="87807-106">A classe [HttpClient](https://docs.microsoft.com/dotnet/api/system.net.http.httpclient?view=netstandard-2.0) original e conhecida pode ser usada com facilidade, mas em alguns casos, ela não está sendo usada corretamente por muitos desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="87807-106">The original and well-known [HttpClient](https://docs.microsoft.com/dotnet/api/system.net.http.httpclient?view=netstandard-2.0) class can be easily used, but in some cases, it is not being properly used by many developers.</span></span> 

<span data-ttu-id="87807-107">Como um primeiro problema, embora essa classe seja descartável, usá-la com a instrução `using` não é a melhor opção porque, mesmo quando você descarta o objeto `HttpClient`, o soquete subjacente não é liberado imediatamente e pode causar um problema sério chamado 'esgotamento de soquetes'.</span><span class="sxs-lookup"><span data-stu-id="87807-107">As a first issue, while this class is disposable, using it with the `using` statement is not the best choice because even when you dispose `HttpClient` object, the underlying socket is not immediately released and can cause a serious issue named ‘sockets exhaustion’.</span></span> <span data-ttu-id="87807-108">Para obter mais informações sobre esse problema, confira a postagem no blog [You're using HttpClient wrong and it is destabilizing your software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) (Você está usando o HttpClient de forma errada e ele está desestabilizando o software).</span><span class="sxs-lookup"><span data-stu-id="87807-108">For more information about this issue, see [You're using HttpClient wrong and it is destabilizing your software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) blog post.</span></span>

<span data-ttu-id="87807-109">Portanto, `HttpClient` deve ser instanciado uma única vez e reutilizado durante a vida útil de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="87807-109">Therefore, `HttpClient` is intended to be instantiated once and reused throughout the life of an application.</span></span> <span data-ttu-id="87807-110">A criação de uma instância de uma classe `HttpClient` para cada solicitação esgotará o número de soquetes disponíveis em condições de carga pesada.</span><span class="sxs-lookup"><span data-stu-id="87807-110">Instantiating an `HttpClient` class for every request will exhaust the number of sockets available under heavy loads.</span></span> <span data-ttu-id="87807-111">Esse problema resultará em erros de `SocketException`.</span><span class="sxs-lookup"><span data-stu-id="87807-111">That issue will result in `SocketException` errors.</span></span> <span data-ttu-id="87807-112">Abordagens possíveis para resolver o problema baseiam-se na criação do objeto `HttpClient` como singleton ou estático, conforme é explicado neste [artigo da Microsoft sobre o uso do HttpClient](https://docs.microsoft.com/dotnet/csharp/tutorials/console-webapiclient).</span><span class="sxs-lookup"><span data-stu-id="87807-112">Possible approaches to solve that problem are based on the creation of the `HttpClient` object as singleton or static, as explained in this [Microsoft article on HttpClient usage](https://docs.microsoft.com/dotnet/csharp/tutorials/console-webapiclient).</span></span> 

<span data-ttu-id="87807-113">Mas há um segundo problema com o `HttpClient` que pode ocorrer quando ele é usado como um objeto singleton ou estático.</span><span class="sxs-lookup"><span data-stu-id="87807-113">But there’s a second issue with `HttpClient` that you can have when you use it as singleton or static object.</span></span> <span data-ttu-id="87807-114">Nesse caso, um `HttpClient` singleton ou estático não respeita as alterações de DNS, conforme é explicado neste [problema no repositório do GitHub do .NET Core](https://github.com/dotnet/corefx/issues/11224).</span><span class="sxs-lookup"><span data-stu-id="87807-114">In this case, a singleton or static `HttpClient` doesn't respect DNS changes, as explained in this [issue at the .NET Core GitHub repo](https://github.com/dotnet/corefx/issues/11224).</span></span> 

<span data-ttu-id="87807-115">Para resolver esses problemas mencionados e simplificar o gerenciamento das instâncias do `HttpClient` com mais facilidade, o .NET Core 2.1 oferece um novo `HttpClientFactory` que também pode ser usado para implementar chamadas HTTP resilientes, integrando a Polly a ele.</span><span class="sxs-lookup"><span data-stu-id="87807-115">To address those mentioned issues and make the management of `HttpClient` instances easier, .NET Core 2.1 offers a new `HttpClientFactory` that can also be used to implement resilient HTTP calls by integrating Polly with it.</span></span>   

## <a name="what-is-httpclientfactory"></a><span data-ttu-id="87807-116">O que é o HttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="87807-116">What is HttpClientFactory</span></span>

<span data-ttu-id="87807-117">O `HttpClientFactory` foi projetado para:</span><span class="sxs-lookup"><span data-stu-id="87807-117">`HttpClientFactory` is designed to:</span></span>

- <span data-ttu-id="87807-118">Fornecer um local central para nomear e configurar HttpClients lógicos.</span><span class="sxs-lookup"><span data-stu-id="87807-118">Provide a central location for naming and configuring logical HttpClients.</span></span> <span data-ttu-id="87807-119">Por exemplo, você pode configurar um cliente (agente de serviço) pré-configurado para acessar um microsserviço específico.</span><span class="sxs-lookup"><span data-stu-id="87807-119">For example, you may configure a client (Service Agent) that is pre-configured to access a specific microservice.</span></span>
- <span data-ttu-id="87807-120">Codificar o conceito de middleware de saída por meio da delegação de manipuladores no `HttpClient` e da implementação de middleware baseado em Polly para aproveitar as políticas da Polly e garantir a resiliência.</span><span class="sxs-lookup"><span data-stu-id="87807-120">Codify the concept of outgoing middleware via delegating handlers in `HttpClient` and implementing Polly-based middleware to take advantage of Polly’s policies for resiliency.</span></span>
- <span data-ttu-id="87807-121">O `HttpClient` já tem o conceito de delegar manipuladores que podem ser vinculados uns aos outros para solicitações HTTP de saída.</span><span class="sxs-lookup"><span data-stu-id="87807-121">`HttpClient` already has the concept of delegating handlers that could be linked together for outgoing HTTP requests.</span></span> <span data-ttu-id="87807-122">Você registra os clientes HTTP no alocador e usa um manipulador da Polly que permite que as políticas da Polly sejam usadas para repetição, CircuitBreakers, etc.</span><span class="sxs-lookup"><span data-stu-id="87807-122">You register http clients into the factory plus you can use a Polly handler that allows Polly policies to be used for Retry, CircuitBreakers, etc.</span></span>
- <span data-ttu-id="87807-123">Gerenciar o tempo de vida de HttpClientMessageHandlers para evitar os problemas mencionado que podem ocorrer ao gerenciar o tempo de vida do `HttpClient` por conta própria.</span><span class="sxs-lookup"><span data-stu-id="87807-123">Manage the lifetime of HttpClientMessageHandlers to avoid the mentioned problems/issues that can occur when managing `HttpClient` lifetimes yourself.</span></span> 

## <a name="multiple-ways-to-use-httpclientfactory"></a><span data-ttu-id="87807-124">Várias maneiras de usar o HttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="87807-124">Multiple ways to use HttpClientFactory</span></span>

<span data-ttu-id="87807-125">Há várias maneiras de usar o `HttpClientFactory` no aplicativo:</span><span class="sxs-lookup"><span data-stu-id="87807-125">There are several ways that you can use `HttpClientFactory` in your application:</span></span>

- <span data-ttu-id="87807-126">Usar o `HttpClientFactory` diretamente</span><span class="sxs-lookup"><span data-stu-id="87807-126">Use `HttpClientFactory` Directly</span></span>
- <span data-ttu-id="87807-127">Usar clientes nomeados</span><span class="sxs-lookup"><span data-stu-id="87807-127">Use Named Clients</span></span>
- <span data-ttu-id="87807-128">Usar clientes tipados</span><span class="sxs-lookup"><span data-stu-id="87807-128">Use Typed Clients</span></span>
- <span data-ttu-id="87807-129">Usar clientes gerados</span><span class="sxs-lookup"><span data-stu-id="87807-129">Use Generated Clients</span></span>

<span data-ttu-id="87807-130">Para ser mais breve, estas diretrizes mostram apenas a maneira mais estruturada de usar o `HttpClientFactory`, que é usar clientes tipados (o padrão do agente de serviço), mas todas as outras opções estão documentadas e listadas neste [artigo que aborda o uso de HttpClientFactory](https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?#consumption-patterns) no momento.</span><span class="sxs-lookup"><span data-stu-id="87807-130">For the sake of brevity, this guidance shows the most structured way to use `HttpClientFactory` that is to use Typed Clients (Service Agent pattern), but all options are documented and are currently listed in this [article covering HttpClientFactory usage](https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?#consumption-patterns).</span></span>  

## <a name="how-to-use-typed-clients-with-httpclientfactory"></a><span data-ttu-id="87807-131">Como usar clientes tipados com HttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="87807-131">How to use Typed Clients with HttpClientFactory</span></span>

<span data-ttu-id="87807-132">O diagrama a seguir mostra como os clientes tipados são usados com o HttpClientFactory.</span><span class="sxs-lookup"><span data-stu-id="87807-132">The following diagram shows how Typed Clients are used with HttpClientFactory.</span></span>

![Diagrama com um controlador MVC usando um ClientService injetado, que, internamente, está usando um HttpClient configurado pelo HttpClientFactory e por políticas da Polly](./media/image3.5.png)

<span data-ttu-id="87807-134">**Figura 10-4**.</span><span class="sxs-lookup"><span data-stu-id="87807-134">**Figure 10-4**.</span></span> <span data-ttu-id="87807-135">Usando `HttpClientFactory` com classes de cliente tipado.</span><span class="sxs-lookup"><span data-stu-id="87807-135">Using `HttpClientFactory`with Typed Client classes.</span></span>

<span data-ttu-id="87807-136">Primeiro, configure `HttpClientFactory` em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="87807-136">First, setup `HttpClientFactory` in your application.</span></span> <span data-ttu-id="87807-137">Adicione uma referência ao pacote `Microsoft.Extensions.Http` que inclua o método de extensão `AddHttpClient()` em `IServiceCollection`.</span><span class="sxs-lookup"><span data-stu-id="87807-137">Add a reference to the `Microsoft.Extensions.Http` package which includes the `AddHttpClient()` extension method for `IServiceCollection`.</span></span> <span data-ttu-id="87807-138">Esse método de extensão registra o `DefaultHttpClientFactory` a ser usado como um singleton da interface `IHttpClientFactory`.</span><span class="sxs-lookup"><span data-stu-id="87807-138">This extension method registers the `DefaultHttpClientFactory` to be used as a singleton for the interface `IHttpClientFactory`.</span></span> <span data-ttu-id="87807-139">Ele define uma configuração transitória para o `HttpMessageHandlerBuilder`.</span><span class="sxs-lookup"><span data-stu-id="87807-139">It defines a transient configuration for the `HttpMessageHandlerBuilder`.</span></span> <span data-ttu-id="87807-140">Esse manipulador de mensagens (objeto `HttpMessageHandler`), obtido de um pool, é usado pelo `HttpClient` retornado do alocador.</span><span class="sxs-lookup"><span data-stu-id="87807-140">This message handler (`HttpMessageHandler` object), taken from a pool, is used by the `HttpClient` returned from the factory.</span></span>

<span data-ttu-id="87807-141">No próximo código, veja como `AddHttpClient()` pode ser usado para registrar clientes tipados (agentes de serviço) que precisam usar `HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="87807-141">In the next code, you can see how `AddHttpClient()` can be used to register Typed Clients (Service Agents) that need to use `HttpClient`.</span></span>

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services) 
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

<span data-ttu-id="87807-142">Basta adicionar suas classes de cliente tipado com AddHttpClient(), para que sempre que você usar o objeto `HttpClient` que será injetado na classe por seu construtor, esse objeto `HttpClient` use todas as configurações e políticas fornecidas.</span><span class="sxs-lookup"><span data-stu-id="87807-142">Just by adding your typed client classes with AddHttpClient(), whenever you use the `HttpClient` object that will be injected to your class through its constructor, that `HttpClient` object will be using all the configuration and policies provided.</span></span> <span data-ttu-id="87807-143">Nas próximas seções, você verá essas políticas, como repetições ou disjuntores da Polly.</span><span class="sxs-lookup"><span data-stu-id="87807-143">In the next sections, you will see those policies like Polly’s retries or circuit-breakers.</span></span>

### <a name="httpclient-lifetimes"></a><span data-ttu-id="87807-144">Tempos de vida de HttpClient</span><span class="sxs-lookup"><span data-stu-id="87807-144">HttpClient lifetimes</span></span>

<span data-ttu-id="87807-145">Sempre que você receber um objeto `HttpClient` do IHttpClientFactory, uma nova instância de um `HttpClient` será retornada.</span><span class="sxs-lookup"><span data-stu-id="87807-145">Each time you get an `HttpClient` object from IHttpClientFactory, a new instance of an `HttpClient` is returned.</span></span> <span data-ttu-id="87807-146">Haverá um HttpMessageHandler\*\* para cada cliente nomeado tipado.</span><span class="sxs-lookup"><span data-stu-id="87807-146">There will be an HttpMessageHandler\*\* per named of typed client.</span></span> <span data-ttu-id="87807-147">O `IHttpClientFactory` fará o pool das instâncias de HttpMessageHandler criadas pelo alocador para reduzir o consumo de recursos.</span><span class="sxs-lookup"><span data-stu-id="87807-147">`IHttpClientFactory` will pool the HttpMessageHandler instances created by the factory to reduce resource consumption.</span></span> <span data-ttu-id="87807-148">Uma instância de HttpMessageHandler poderá ser reutilizada do pool quando uma nova instância de `HttpClient` for criada e seu tempo de vida ainda não tiver expirado.</span><span class="sxs-lookup"><span data-stu-id="87807-148">An HttpMessageHandler instance may be reused from the pool when creating a new `HttpClient` instance if its lifetime hasn't expired.</span></span>

<span data-ttu-id="87807-149">O pooling de manipuladores é interessante porque cada manipulador normalmente gerencia suas próprias conexões de HTTP subjacentes. Criar mais manipuladores do que o necessário pode resultar em atrasos de conexão.</span><span class="sxs-lookup"><span data-stu-id="87807-149">Pooling of handlers is desirable as each handler typically manages its own underlying HTTP connections; creating more handlers than necessary can result in connection delays.</span></span> <span data-ttu-id="87807-150">Alguns manipuladores também mantêm as conexões abertas indefinidamente, o que pode impedir que o manipulador reaja a alterações de DNS.</span><span class="sxs-lookup"><span data-stu-id="87807-150">Some handlers also keep connections open indefinitely, which can prevent the handler from reacting to DNS changes.</span></span>

<span data-ttu-id="87807-151">Os objetos HttpMessageHandler no pool têm um tempo de vida que corresponde ao período de tempo em que a instância de HttpMessageHandler no pool pode ser reutilizada.</span><span class="sxs-lookup"><span data-stu-id="87807-151">The HttpMessageHandler objects in the pool have a lifetime that is the length of time that an HttpMessageHandler instance in the pool can be reused.</span></span> <span data-ttu-id="87807-152">O valor padrão é de dois minutos, mas pode ser substituído para cada cliente nomeado ou tipado.</span><span class="sxs-lookup"><span data-stu-id="87807-152">The default value is two minutes, but it can be overridden per named or typed client basis.</span></span> <span data-ttu-id="87807-153">Para substituí-lo, chame SetHandlerLifetime() no IHttpClientBuilder que é retornado quando o cliente é criado, conforme é mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="87807-153">To override it, call SetHandlerLifetime() on the IHttpClientBuilder that is returned when creating the client, as shown in the following code.</span></span>

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client 
services.AddHttpClient<ICatalogService, CatalogService>()
                 .SetHandlerLifetime(TimeSpan.FromMinutes(5));  
```

<span data-ttu-id="87807-154">Cada cliente tipado ou nomeado pode ter seu próprio valor de tempo de vida do manipulador configurado.</span><span class="sxs-lookup"><span data-stu-id="87807-154">Each typed client or named client can have its own configured handler lifetime value.</span></span> <span data-ttu-id="87807-155">Defina o tempo de vida para InfiniteTimeSpan para desabilitar a expiração do manipulador.</span><span class="sxs-lookup"><span data-stu-id="87807-155">Set the lifetime to InfiniteTimeSpan to disable handler expiry.</span></span>

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a><span data-ttu-id="87807-156">Implementar suas classes de cliente tipado que usam o HttpClient injetado e configurado</span><span class="sxs-lookup"><span data-stu-id="87807-156">Implement your Typed Client classes that use the injected and configured HttpClient</span></span>

<span data-ttu-id="87807-157">Como uma etapa anterior, você precisa ter definido suas classes de cliente tipado, como as classes no código de exemplo: 'BasketService', 'CatalogService', 'OrderingService', etc. Um cliente tipado é uma classe que aceita um objeto `HttpClient` (injetado por seu construtor) e o usa para chamar algum serviço HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="87807-157">As a previous step, you need to have your Typed Client classes defined, such as the classes in the sample code, like ‘BasketService’, ‘CatalogService’, ‘OrderingService’, etc. – A typed client is a class that accepts an `HttpClient` object (injected through its constructor) and uses it to call some remote HTTP service.</span></span> <span data-ttu-id="87807-158">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="87807-158">For example:</span></span>

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

<span data-ttu-id="87807-159">O cliente tipado (CatalogService, no exemplo) é ativado pela DI (injeção de dependência), o que significa que ele pode aceitar qualquer serviço registrado em seu construtor, além do HttpClient.</span><span class="sxs-lookup"><span data-stu-id="87807-159">The typed client (CatalogService in the example) is activated by DI (Dependency Injection), meaning that it can accept any registered service in its constructor, in addition to HttpClient.</span></span>

<span data-ttu-id="87807-160">Um cliente tipado é, efetivamente, um objeto transitório, o que significa que uma nova instância é criada sempre que necessário e recebe uma nova instância de `HttpClient` sempre que é construída.</span><span class="sxs-lookup"><span data-stu-id="87807-160">A typed client is, effectively, a transient object, meaning that a new instance is created each time one is needed and it will receive a new `HttpClient` instance each time it is constructed.</span></span> <span data-ttu-id="87807-161">No entanto, os objetos HttpMessageHandler no pool são os objetos que são reutilizados por várias solicitações HTTP.</span><span class="sxs-lookup"><span data-stu-id="87807-161">However, the HttpMessageHandler objects in the pool are the objects that are reused by multiple Http requests.</span></span>

### <a name="use-your-typed-client-classes"></a><span data-ttu-id="87807-162">Usar suas classes de cliente tipado</span><span class="sxs-lookup"><span data-stu-id="87807-162">Use your Typed Client classes</span></span>

<span data-ttu-id="87807-163">Por fim, depois que suas classes tipadas são implementadas e registradas no AddHttpClient(), você pode usá-las em qualquer lugar em os serviços possam ser injetados pela DI, por exemplo, em qualquer código de Razor Page ou em qualquer controlador de um aplicativo Web MVC, como no código a seguir do eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="87807-163">Finally, once you have your type classes implemented and have them registered with AddHttpClient(), you can use it anywhere you can have services injected by DI, for example in any Razor page code or any controller of an MVC web app, like in the following code from eShopOnContainers.</span></span>

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

<span data-ttu-id="87807-164">Até este ponto, o código mostrado está apenas executando solicitações HTTP regulares, mas a 'mágica' vem nas seções a seguir, em que, basta adicionar políticas e delegar manipuladores para os clientes tipados registrados, para que todas as solicitações HTTP realizadas por `HttpClient` se comportem considerando políticas resilientes, como repetições com retirada exponencial, disjuntores ou qualquer outro manipulador delegado personalizado para implementar recursos de segurança adicionais, como o uso de tokens de autenticação ou qualquer outro recurso personalizado.</span><span class="sxs-lookup"><span data-stu-id="87807-164">Until this point, the code shown is just performing regular Http requests, but the ‘magic’ comes in the following sections where, just by adding policies and delegating handlers to your registered typed clients, all the Http requests to be done by `HttpClient` will behave taking into account resilient policies such as retries with exponential backoff, circuit breakers, or any other custom delegating handler to implement additional security features, like using auth tokens, or any other custom feature.</span></span> 


## <a name="additional-resources"></a><span data-ttu-id="87807-165">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="87807-165">Additional resources</span></span>

-   <span data-ttu-id="87807-166">**Usando HttpClientFactory no .NET Core 2.1**
    [*https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1*](https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1)</span><span class="sxs-lookup"><span data-stu-id="87807-166">**Using HttpClientFactory in .NET Core 2.1**
[*https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1*](https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1)</span></span>


-   <span data-ttu-id="87807-167">**Repositório do GitHub do HttpClientFactory**</span><span class="sxs-lookup"><span data-stu-id="87807-167">**HttpClientFactory GitHub repo**</span></span>

    [*https://github.com/aspnet/HttpClientFactory*](https://github.com/aspnet/HttpClientFactory)

>[!div class="step-by-step"]
><span data-ttu-id="87807-168">[Anterior](explore-custom-http-call-retries-exponential-backoff.md)
>[Próximo](implement-http-call-retries-exponential-backoff-polly.md)</span><span class="sxs-lookup"><span data-stu-id="87807-168">[Previous](explore-custom-http-call-retries-exponential-backoff.md)
[Next](implement-http-call-retries-exponential-backoff-polly.md)</span></span>