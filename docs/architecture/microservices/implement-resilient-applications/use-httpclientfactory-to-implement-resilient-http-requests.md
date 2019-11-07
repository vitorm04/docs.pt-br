---
title: Usar HttpClientFactory implementar solicitações HTTP resilientes
description: Saiba como usar o HttpClientFactory, disponível desde o .NET Core 2.1, para a criação de instâncias de `HttpClient`, facilitando o uso em seus aplicativos.
ms.date: 08/08/2019
ms.openlocfilehash: 9eff4a01361b3dc6f7471bc012c945d048b9a276
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73737750"
---
# <a name="use-httpclientfactory-to-implement-resilient-http-requests"></a><span data-ttu-id="acd37-103">Usar HttpClientFactory implementar solicitações HTTP resilientes</span><span class="sxs-lookup"><span data-stu-id="acd37-103">Use HttpClientFactory to implement resilient HTTP requests</span></span>

<span data-ttu-id="acd37-104">`HttpClientFactory` é um alocador "teimoso", disponível desde o .NET Core 2.1, para a criação de instâncias do <xref:System.Net.Http.HttpClient> a serem usadas nos aplicativos.</span><span class="sxs-lookup"><span data-stu-id="acd37-104">`HttpClientFactory` is an opinionated factory, available since .NET Core 2.1, for creating <xref:System.Net.Http.HttpClient> instances to be used in your applications.</span></span>

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a><span data-ttu-id="acd37-105">Problemas com a classe HttpClient original disponível no .NET Core</span><span class="sxs-lookup"><span data-stu-id="acd37-105">Issues with the original HttpClient class available in .NET Core</span></span>

<span data-ttu-id="acd37-106">A classe de <xref:System.Net.Http.HttpClient> original e conhecida pode ser facilmente usada, mas em alguns casos, ela não está sendo usada corretamente por muitos desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="acd37-106">The original and well-known <xref:System.Net.Http.HttpClient> class can be easily used, but in some cases, it isn't being properly used by many developers.</span></span>

<span data-ttu-id="acd37-107">Como um primeiro problema, embora essa classe seja descartável, usá-la com a instrução `using` não é a melhor opção porque, mesmo quando você descarta o objeto `HttpClient`, o soquete subjacente não é liberado imediatamente e pode causar um problema sério chamado 'esgotamento de soquetes'.</span><span class="sxs-lookup"><span data-stu-id="acd37-107">As a first issue, while this class is disposable, using it with the `using` statement is not the best choice because even when you dispose `HttpClient` object, the underlying socket is not immediately released and can cause a serious issue named ‘sockets exhaustion’.</span></span> <span data-ttu-id="acd37-108">Para obter mais informações sobre esse problema, confira a postagem no blog [You're using HttpClient wrong and it is destabilizing your software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) (Você está usando o HttpClient incorretamente e ele está desestabilizando o software).</span><span class="sxs-lookup"><span data-stu-id="acd37-108">For more information about this issue, see [You're using HttpClient wrong and it's destabilizing your software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) blog post.</span></span>

<span data-ttu-id="acd37-109">Portanto, `HttpClient` deve ser instanciado uma única vez e reutilizado durante a vida útil de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="acd37-109">Therefore, `HttpClient` is intended to be instantiated once and reused throughout the life of an application.</span></span> <span data-ttu-id="acd37-110">A criação de uma instância de uma classe `HttpClient` para cada solicitação esgotará o número de soquetes disponíveis em condições de carga pesada.</span><span class="sxs-lookup"><span data-stu-id="acd37-110">Instantiating an `HttpClient` class for every request will exhaust the number of sockets available under heavy loads.</span></span> <span data-ttu-id="acd37-111">Esse problema resultará em erros de `SocketException`.</span><span class="sxs-lookup"><span data-stu-id="acd37-111">That issue will result in `SocketException` errors.</span></span> <span data-ttu-id="acd37-112">Abordagens possíveis para resolver o problema baseiam-se na criação do objeto `HttpClient` como singleton ou estático, conforme é explicado neste [artigo da Microsoft sobre o uso do HttpClient](../../../csharp/tutorials/console-webapiclient.md).</span><span class="sxs-lookup"><span data-stu-id="acd37-112">Possible approaches to solve that problem are based on the creation of the `HttpClient` object as singleton or static, as explained in this [Microsoft article on HttpClient usage](../../../csharp/tutorials/console-webapiclient.md).</span></span>

<span data-ttu-id="acd37-113">Mas há um segundo problema com o `HttpClient` que pode ocorrer quando ele é usado como um objeto singleton ou estático.</span><span class="sxs-lookup"><span data-stu-id="acd37-113">But there’s a second issue with `HttpClient` that you can have when you use it as singleton or static object.</span></span> <span data-ttu-id="acd37-114">Nesse caso, um singleton ou `HttpClient` estático não respeitam as alterações de DNS, conforme explicado neste [problema](https://github.com/dotnet/corefx/issues/11224) no repositório do GitHub dotnet/corefx.</span><span class="sxs-lookup"><span data-stu-id="acd37-114">In this case, a singleton or static `HttpClient` doesn't respect DNS changes, as explained in this [issue](https://github.com/dotnet/corefx/issues/11224) at the dotnet/corefx GitHub repository.</span></span>

<span data-ttu-id="acd37-115">Para resolver esses problemas mencionados e facilitar o gerenciamento das instâncias do `HttpClient`, o .NET Core 2.1 introduziu um novo `HttpClientFactory` que também pode ser usado para implementar chamadas HTTP resilientes pela integração do Polly a ele.</span><span class="sxs-lookup"><span data-stu-id="acd37-115">To address those mentioned issues and make the management of `HttpClient` instances easier, .NET Core 2.1 introduced a new `HttpClientFactory` that can also be used to implement resilient HTTP calls by integrating Polly with it.</span></span>

<span data-ttu-id="acd37-116">[Polly](http://www.thepollyproject.org/) é uma biblioteca de tratamento de falhas transitórias que ajuda os desenvolvedores a adicionar resiliência aos seus aplicativos, usando algumas políticas predefinidas de forma fluente e thread-safe.</span><span class="sxs-lookup"><span data-stu-id="acd37-116">[Polly](http://www.thepollyproject.org/) is transient-fault-handling library that helps developers add resiliency to their applications, by using some pre-defined policies in a fluent and thread-safe manner.</span></span>

## <a name="what-is-httpclientfactory"></a><span data-ttu-id="acd37-117">O que é o HttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="acd37-117">What is HttpClientFactory</span></span>

<span data-ttu-id="acd37-118">O `HttpClientFactory` foi projetado para:</span><span class="sxs-lookup"><span data-stu-id="acd37-118">`HttpClientFactory` is designed to:</span></span>

- <span data-ttu-id="acd37-119">Forneça um local central para nomear e configurar objetos de `HttpClient` lógicos.</span><span class="sxs-lookup"><span data-stu-id="acd37-119">Provide a central location for naming and configuring logical `HttpClient` objects.</span></span> <span data-ttu-id="acd37-120">Por exemplo, você pode configurar um cliente (agente de serviço) pré-configurado para acessar um microsserviço específico.</span><span class="sxs-lookup"><span data-stu-id="acd37-120">For example, you may configure a client (Service Agent) that's pre-configured to access a specific microservice.</span></span>
- <span data-ttu-id="acd37-121">Codificar o conceito de middleware de saída por meio da delegação de manipuladores no `HttpClient` e da implementação de middleware baseado em Polly para aproveitar as políticas da Polly e garantir a resiliência.</span><span class="sxs-lookup"><span data-stu-id="acd37-121">Codify the concept of outgoing middleware via delegating handlers in `HttpClient` and implementing Polly-based middleware to take advantage of Polly’s policies for resiliency.</span></span>
- <span data-ttu-id="acd37-122">O `HttpClient` já tem o conceito de delegar manipuladores que podem ser vinculados uns aos outros para solicitações HTTP de saída.</span><span class="sxs-lookup"><span data-stu-id="acd37-122">`HttpClient` already has the concept of delegating handlers that could be linked together for outgoing HTTP requests.</span></span> <span data-ttu-id="acd37-123">Você registra clientes HTTP na fábrica e pode usar um manipulador Polly para usar políticas Polly para repetição, CircuitBreakers e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="acd37-123">You register HTTP clients into the factory and you can use a Polly handler to use Polly policies for Retry, CircuitBreakers, and so on.</span></span>
- <span data-ttu-id="acd37-124">Gerencie o tempo de vida de `HttpClientMessageHandlers` para evitar problemas/problemas mencionados que podem ocorrer ao gerenciar `HttpClient` os tempos de vida.</span><span class="sxs-lookup"><span data-stu-id="acd37-124">Manage the lifetime of `HttpClientMessageHandlers` to avoid the mentioned problems/issues that can occur when managing `HttpClient` lifetimes yourself.</span></span>

> [!NOTE]
> <span data-ttu-id="acd37-125">`HttpClientFactory` está rigidamente ligado à implementação de injeção de dependência (DI) no pacote NuGet `Microsoft.Extensions.DependencyInjection`.</span><span class="sxs-lookup"><span data-stu-id="acd37-125">`HttpClientFactory` is tightly tied to the dependency injection (DI) implementation in the `Microsoft.Extensions.DependencyInjection` NuGet package.</span></span> <span data-ttu-id="acd37-126">Para obter mais informações sobre como usar outros contêineres de injeção de dependência, consulte esta [discussão do GitHub](https://github.com/aspnet/Extensions/issues/1345).</span><span class="sxs-lookup"><span data-stu-id="acd37-126">For more information about using other dependency injection containers, see this [GitHub discussion](https://github.com/aspnet/Extensions/issues/1345).</span></span>

## <a name="multiple-ways-to-use-httpclientfactory"></a><span data-ttu-id="acd37-127">Várias maneiras de usar o HttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="acd37-127">Multiple ways to use HttpClientFactory</span></span>

<span data-ttu-id="acd37-128">Há várias maneiras de usar o `HttpClientFactory` no aplicativo:</span><span class="sxs-lookup"><span data-stu-id="acd37-128">There are several ways that you can use `HttpClientFactory` in your application:</span></span>

- <span data-ttu-id="acd37-129">Usar o `HttpClientFactory` diretamente</span><span class="sxs-lookup"><span data-stu-id="acd37-129">Use `HttpClientFactory` Directly</span></span>
- <span data-ttu-id="acd37-130">Usar clientes nomeados</span><span class="sxs-lookup"><span data-stu-id="acd37-130">Use Named Clients</span></span>
- <span data-ttu-id="acd37-131">Usar clientes tipados</span><span class="sxs-lookup"><span data-stu-id="acd37-131">Use Typed Clients</span></span>
- <span data-ttu-id="acd37-132">Usar clientes gerados</span><span class="sxs-lookup"><span data-stu-id="acd37-132">Use Generated Clients</span></span>

<span data-ttu-id="acd37-133">Para fins de brevidade, essas diretrizes mostram a maneira mais estruturada de usar `HttpClientFactory`, que é usar clientes digitados (padrão de agente de serviço).</span><span class="sxs-lookup"><span data-stu-id="acd37-133">For the sake of brevity, this guidance shows the most structured way to use `HttpClientFactory`, which is to use Typed Clients (Service Agent pattern).</span></span> <span data-ttu-id="acd37-134">No entanto, todas as opções estão documentadas e atualmente estão listadas neste [artigo cobrindo o uso do HttpClientFactory](/aspnet/core/fundamentals/http-requests#consumption-patterns).</span><span class="sxs-lookup"><span data-stu-id="acd37-134">However, all options are documented and are currently listed in this [article covering HttpClientFactory usage](/aspnet/core/fundamentals/http-requests#consumption-patterns).</span></span>

## <a name="how-to-use-typed-clients-with-httpclientfactory"></a><span data-ttu-id="acd37-135">Como usar clientes tipados com HttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="acd37-135">How to use Typed Clients with HttpClientFactory</span></span>

<span data-ttu-id="acd37-136">Portanto, o que é um "cliente tipado"?</span><span class="sxs-lookup"><span data-stu-id="acd37-136">So, what's a "Typed Client"?</span></span> <span data-ttu-id="acd37-137">É apenas um `HttpClient` que é configurado na injeção pelo `DefaultHttpClientFactory`.</span><span class="sxs-lookup"><span data-stu-id="acd37-137">It's just an `HttpClient` that's configured upon injection by the `DefaultHttpClientFactory`.</span></span>

<span data-ttu-id="acd37-138">O diagrama a seguir mostra como os clientes tipados são usados com o `HttpClientFactory`:</span><span class="sxs-lookup"><span data-stu-id="acd37-138">The following diagram shows how Typed Clients are used with `HttpClientFactory`:</span></span>

![Diagrama mostrando como os clientes digitados são usados com HttpClientFactory.](./media/use-httpclientfactory-to-implement-resilient-http-requests/client-application-code.png)

<span data-ttu-id="acd37-140">**Figura 8-4**.</span><span class="sxs-lookup"><span data-stu-id="acd37-140">**Figure 8-4**.</span></span> <span data-ttu-id="acd37-141">Use o HttpClientFactory com classes de cliente tipado.</span><span class="sxs-lookup"><span data-stu-id="acd37-141">Using HttpClientFactory with Typed Client classes.</span></span>

<span data-ttu-id="acd37-142">Na imagem acima, um ClientService (usado por um controlador ou código de cliente) usa um `HttpClient` criado pelo `IHttpClientFactory`registrado.</span><span class="sxs-lookup"><span data-stu-id="acd37-142">In the above image, a ClientService (used by a controller or client code) uses an `HttpClient` created by the registered `IHttpClientFactory`.</span></span> <span data-ttu-id="acd37-143">Essa fábrica atribui o `HttpClient` um `HttpMessageHandler` de um pool que ele gerencia.</span><span class="sxs-lookup"><span data-stu-id="acd37-143">This factory assigns the `HttpClient` an `HttpMessageHandler` from a pool it manages.</span></span> <span data-ttu-id="acd37-144">O `HttpClient` pode ser configurado com as políticas do Polly ao registrar o `IHttpClientFactory` no contêiner DI com o método de extensão `AddHttpClient`.</span><span class="sxs-lookup"><span data-stu-id="acd37-144">The `HttpClient` can be configured with Polly's policies when registering the `IHttpClientFactory` in the DI container with the extension method `AddHttpClient`.</span></span>

<span data-ttu-id="acd37-145">Para configurar a estrutura acima, adicione `HttpClientFactory` em seu aplicativo instalando o pacote NuGet `Microsoft.Extensions.Http` que inclui o método de extensão `AddHttpClient()` para `IServiceCollection`.</span><span class="sxs-lookup"><span data-stu-id="acd37-145">To configure the above structure, add `HttpClientFactory` in your application by installing the `Microsoft.Extensions.Http` NuGet package that includes the `AddHttpClient()` extension method for `IServiceCollection`.</span></span> <span data-ttu-id="acd37-146">Esse método de extensão registra o `DefaultHttpClientFactory` a ser usado como um singleton da interface `IHttpClientFactory`.</span><span class="sxs-lookup"><span data-stu-id="acd37-146">This extension method registers the `DefaultHttpClientFactory` to be used as a singleton for the interface `IHttpClientFactory`.</span></span> <span data-ttu-id="acd37-147">Ele define uma configuração transitória para o `HttpMessageHandlerBuilder`.</span><span class="sxs-lookup"><span data-stu-id="acd37-147">It defines a transient configuration for the `HttpMessageHandlerBuilder`.</span></span> <span data-ttu-id="acd37-148">Esse manipulador de mensagens (objeto `HttpMessageHandler`), obtido de um pool, é usado pelo `HttpClient` retornado do alocador.</span><span class="sxs-lookup"><span data-stu-id="acd37-148">This message handler (`HttpMessageHandler` object), taken from a pool, is used by the `HttpClient` returned from the factory.</span></span>

<span data-ttu-id="acd37-149">No próximo código, veja como `AddHttpClient()` pode ser usado para registrar clientes tipados (agentes de serviço) que precisam usar `HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="acd37-149">In the next code, you can see how `AddHttpClient()` can be used to register Typed Clients (Service Agents) that need to use `HttpClient`.</span></span>

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services)
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

<span data-ttu-id="acd37-150">O registro dos serviços do cliente, conforme mostrado no código anterior, torna o `DefaultClientFactory` criar um `HttpClient` padrão para cada serviço.</span><span class="sxs-lookup"><span data-stu-id="acd37-150">Registering the client services as shown in the previous code, makes the `DefaultClientFactory` create a standard `HttpClient` for each service.</span></span>

<span data-ttu-id="acd37-151">Você também pode adicionar a configuração específica da instância no registro para, por exemplo, configurar o endereço base e adicionar algumas políticas de resiliência, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="acd37-151">You could also add instance-specific configuration in the registration to, for example, configure the base address, and add some resiliency policies, as shown in the following code:</span></span>

```csharp
services.AddHttpClient<ICatalogService, CatalogService>(client =>
{
    client.BaseAddress = new Uri(Configuration["BaseUrl"]);
})
    .AddPolicyHandler(GetRetryPolicy())
    .AddPolicyHandler(GetCircuitBreakerPolicy());
```

<span data-ttu-id="acd37-152">Apenas para o exemplo, você pode ver uma das políticas acima no próximo código:</span><span class="sxs-lookup"><span data-stu-id="acd37-152">Just for the example sake, you can see one of the above policies in the next code:</span></span>

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)));
}
```

<span data-ttu-id="acd37-153">Você pode encontrar mais detalhes sobre como usar o Polly no [próximo artigo](implement-http-call-retries-exponential-backoff-polly.md).</span><span class="sxs-lookup"><span data-stu-id="acd37-153">You can find more details about using Polly in the [Next article](implement-http-call-retries-exponential-backoff-polly.md).</span></span>

### <a name="httpclient-lifetimes"></a><span data-ttu-id="acd37-154">Tempos de vida de HttpClient</span><span class="sxs-lookup"><span data-stu-id="acd37-154">HttpClient lifetimes</span></span>

<span data-ttu-id="acd37-155">Sempre que você receber um objeto `HttpClient` do `IHttpClientFactory`, uma nova instância será retornada.</span><span class="sxs-lookup"><span data-stu-id="acd37-155">Each time you get an `HttpClient` object from the `IHttpClientFactory`, a new instance is returned.</span></span> <span data-ttu-id="acd37-156">Mas cada `HttpClient` usa um `HttpMessageHandler` que foi colocado em pool e reutilizado pelo `IHttpClientFactory` para reduzir o consumo de recursos, desde que o tempo de vida do `HttpMessageHandler` não tenha expirado.</span><span class="sxs-lookup"><span data-stu-id="acd37-156">But each `HttpClient` uses an `HttpMessageHandler` that's pooled and reused by the `IHttpClientFactory` to reduce resource consumption, as long as the `HttpMessageHandler`'s lifetime hasn't expired.</span></span>

<span data-ttu-id="acd37-157">O pooling de manipuladores é interessante porque cada manipulador normalmente gerencia suas próprias conexões de HTTP subjacentes. Criar mais manipuladores do que o necessário pode resultar em atrasos de conexão.</span><span class="sxs-lookup"><span data-stu-id="acd37-157">Pooling of handlers is desirable as each handler typically manages its own underlying HTTP connections; creating more handlers than necessary can result in connection delays.</span></span> <span data-ttu-id="acd37-158">Alguns manipuladores também mantêm as conexões abertas indefinidamente, o que pode impedir que o manipulador reaja a alterações de DNS.</span><span class="sxs-lookup"><span data-stu-id="acd37-158">Some handlers also keep connections open indefinitely, which can prevent the handler from reacting to DNS changes.</span></span>

<span data-ttu-id="acd37-159">Os objetos `HttpMessageHandler` no pool têm um tempo de vida que é o período de tempo em que uma instância `HttpMessageHandler` no pool pode ser reutilizada.</span><span class="sxs-lookup"><span data-stu-id="acd37-159">The `HttpMessageHandler` objects in the pool have a lifetime that's the length of time that an `HttpMessageHandler` instance in the pool can be reused.</span></span> <span data-ttu-id="acd37-160">O valor padrão é dois minutos, mas pode ser substituído por cliente tipado.</span><span class="sxs-lookup"><span data-stu-id="acd37-160">The default value is two minutes, but it can be overridden per Typed Client.</span></span> <span data-ttu-id="acd37-161">Para substituí-lo, chame `SetHandlerLifetime()` no `IHttpClientBuilder` que é retornado ao criar o cliente, como mostra o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="acd37-161">To override it, call `SetHandlerLifetime()` on the `IHttpClientBuilder` that's returned when creating the client, as shown in the following code:</span></span>

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client
services.AddHttpClient<ICatalogService, CatalogService>()
    .SetHandlerLifetime(TimeSpan.FromMinutes(5));
```

<span data-ttu-id="acd37-162">Cada cliente tipado pode ter seu próprio valor de tempo de vida do manipulador configurado.</span><span class="sxs-lookup"><span data-stu-id="acd37-162">Each Typed Client can have its own configured handler lifetime value.</span></span> <span data-ttu-id="acd37-163">Defina o tempo de vida como `InfiniteTimeSpan` para desabilitar a expiração do manipulador.</span><span class="sxs-lookup"><span data-stu-id="acd37-163">Set the lifetime to `InfiniteTimeSpan` to disable handler expiry.</span></span>

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a><span data-ttu-id="acd37-164">Implementar suas classes de cliente tipado que usam o HttpClient injetado e configurado</span><span class="sxs-lookup"><span data-stu-id="acd37-164">Implement your Typed Client classes that use the injected and configured HttpClient</span></span>

<span data-ttu-id="acd37-165">Como uma etapa anterior, você precisa ter definido suas classes de cliente tipado, como as classes no código de exemplo: 'BasketService', 'CatalogService', 'OrderingService', etc. Um cliente tipado é uma classe que aceita um objeto `HttpClient` (injetado por seu construtor) e o usa para chamar algum serviço HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="acd37-165">As a previous step, you need to have your Typed Client classes defined, such as the classes in the sample code, like ‘BasketService’, ‘CatalogService’, ‘OrderingService’, etc. – A Typed Client is a class that accepts an `HttpClient` object (injected through its constructor) and uses it to call some remote HTTP service.</span></span> <span data-ttu-id="acd37-166">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="acd37-166">For example:</span></span>

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

<span data-ttu-id="acd37-167">O cliente tipado (CatalogService, no exemplo) é ativado pela DI (injeção de dependência), o que significa que ele pode aceitar qualquer serviço registrado em seu construtor, além do HttpClient.</span><span class="sxs-lookup"><span data-stu-id="acd37-167">The Typed Client (CatalogService in the example) is activated by DI (Dependency Injection), meaning that it can accept any registered service in its constructor, in addition to HttpClient.</span></span>

<span data-ttu-id="acd37-168">Um cliente tipado é, efetivamente, um objeto transitório, o que significa que uma instância é criada sempre que necessário e recebe uma nova instância de `HttpClient` sempre que é construída.</span><span class="sxs-lookup"><span data-stu-id="acd37-168">A Typed Client is, effectively, a transient object, meaning that a new instance is created each time one is needed and it will receive a new `HttpClient` instance each time it's constructed.</span></span> <span data-ttu-id="acd37-169">No entanto, os objetos HttpMessageHandler no pool são os objetos que são reutilizados por várias solicitações HTTP.</span><span class="sxs-lookup"><span data-stu-id="acd37-169">However, the HttpMessageHandler objects in the pool are the objects that are reused by multiple Http requests.</span></span>

### <a name="use-your-typed-client-classes"></a><span data-ttu-id="acd37-170">Usar suas classes de cliente tipado</span><span class="sxs-lookup"><span data-stu-id="acd37-170">Use your Typed Client classes</span></span>

<span data-ttu-id="acd37-171">Por fim, depois de implementar as classes tipadas e tê-las registradas com `AddHttpClient()`, você poderá usá-las sempre que puder ter os serviços injetados por DI.</span><span class="sxs-lookup"><span data-stu-id="acd37-171">Finally, once you have your typed classes implemented and have them registered with `AddHttpClient()`, you can use them wherever you can have services injected by DI.</span></span> <span data-ttu-id="acd37-172">Por exemplo, em um código de página do Razor ou no controlador de um aplicativo Web MVC, como no código a seguir de eShopOnContainers:</span><span class="sxs-lookup"><span data-stu-id="acd37-172">For example, in a Razor page code or controller of an MVC web app, like in the following code from eShopOnContainers:</span></span>

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

<span data-ttu-id="acd37-173">Até este ponto, o código mostrado está apenas executando solicitações HTTP regulares, mas a 'mágica' vem nas seções a seguir, em que, basta adicionar políticas e delegar manipuladores aos clientes tipados registrados, para que todas as solicitações HTTP realizadas por `HttpClient` se comportem considerando políticas resilientes, como repetições com retirada exponencial, disjuntores ou qualquer outro manipulador delegado personalizado para implementar recursos de segurança adicionais, como o uso de tokens de autenticação ou qualquer outro recurso personalizado.</span><span class="sxs-lookup"><span data-stu-id="acd37-173">Up to this point, the code shown is just performing regular Http requests, but the ‘magic’ comes in the following sections where, just by adding policies and delegating handlers to your registered Typed Clients, all the HTTP requests to be done by `HttpClient` will behave taking into account resilient policies such as retries with exponential backoff, circuit breakers, or any other custom delegating handler to implement additional security features, like using auth tokens, or any other custom feature.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="acd37-174">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="acd37-174">Additional resources</span></span>

- <span data-ttu-id="acd37-175">**Usando o HttpClientFactory no .NET Core**</span><span class="sxs-lookup"><span data-stu-id="acd37-175">**Using HttpClientFactory in .NET Core**</span></span>  
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests](/aspnet/core/fundamentals/http-requests)

- <span data-ttu-id="acd37-176">**HttpClientFactory o código-fonte no repositório GitHub `aspnet/Extensions`**</span><span class="sxs-lookup"><span data-stu-id="acd37-176">**HttpClientFactory source code in the `aspnet/Extensions` GitHub repository**</span></span>  
  <https://github.com/aspnet/Extensions/tree/master/src/HttpClientFactory>

- <span data-ttu-id="acd37-177">**Polly (biblioteca de tratamento de falhas transitórias e resiliência do .NET)**</span><span class="sxs-lookup"><span data-stu-id="acd37-177">**Polly (.NET resilience and transient-fault-handling library)**</span></span>  
  <http://www.thepollyproject.org/>
  
- <span data-ttu-id="acd37-178">**Usando HttpClientFactory sem injeção de dependência (problema do GitHub)**</span><span class="sxs-lookup"><span data-stu-id="acd37-178">**Using HttpClientFactory without dependency injection (GitHub issue)**</span></span>  
  <https://github.com/aspnet/Extensions/issues/1345>

>[!div class="step-by-step"]
><span data-ttu-id="acd37-179">[Anterior](explore-custom-http-call-retries-exponential-backoff.md)
>[Próximo](implement-http-call-retries-exponential-backoff-polly.md)</span><span class="sxs-lookup"><span data-stu-id="acd37-179">[Previous](explore-custom-http-call-retries-exponential-backoff.md)
[Next](implement-http-call-retries-exponential-backoff-polly.md)</span></span>
