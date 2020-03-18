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
# <a name="use-ihttpclientfactory-to-implement-resilient-http-requests"></a><span data-ttu-id="f0b33-103">Use ihttpClientFactory para implementar solicitações HTTP resilientes</span><span class="sxs-lookup"><span data-stu-id="f0b33-103">Use IHttpClientFactory to implement resilient HTTP requests</span></span>

<span data-ttu-id="f0b33-104"><xref:System.Net.Http.IHttpClientFactory>é um contrato `DefaultHttpClientFactory`implementado por , uma fábrica opinativa, disponível <xref:System.Net.Http.HttpClient> desde .NET Core 2.1, para criar instâncias a serem usadas em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="f0b33-104"><xref:System.Net.Http.IHttpClientFactory> is a contract implemented by `DefaultHttpClientFactory`, an opinionated factory, available since .NET Core 2.1, for creating <xref:System.Net.Http.HttpClient> instances to be used in your applications.</span></span>

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a><span data-ttu-id="f0b33-105">Problemas com a classe HttpClient original disponível no .NET Core</span><span class="sxs-lookup"><span data-stu-id="f0b33-105">Issues with the original HttpClient class available in .NET Core</span></span>

<span data-ttu-id="f0b33-106">A classe original <xref:System.Net.Http.HttpClient> e bem conhecida pode ser facilmente usada, mas em alguns casos, não está sendo usada corretamente por muitos desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="f0b33-106">The original and well-known <xref:System.Net.Http.HttpClient> class can be easily used, but in some cases, it isn't being properly used by many developers.</span></span>

<span data-ttu-id="f0b33-107">Embora esta classe `IDisposable`implemente , declarando-o `using` e instanciando-o dentro de uma declaração não é preferível porque quando o `HttpClient` objeto é eliminado, o soquete subjacente não é imediatamente liberado, o que pode levar a um problema de _exaustão do soquete._</span><span class="sxs-lookup"><span data-stu-id="f0b33-107">While this class implements `IDisposable`, declaring and instantiating it within a `using` statement is not preferred because when the `HttpClient` object gets disposed of, the underlying socket is not immediately released, which can lead to a _socket exhaustion_ problem.</span></span> <span data-ttu-id="f0b33-108">Para obter mais informações sobre este problema, consulte o post do blog [Você está usando httpClient errado e está desestabilizando seu software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/).</span><span class="sxs-lookup"><span data-stu-id="f0b33-108">For more information about this issue, see the blog post [You're using HttpClient wrong and it's destabilizing your software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/).</span></span>

<span data-ttu-id="f0b33-109">Portanto, `HttpClient` deve ser instanciado uma única vez e reutilizado durante a vida útil de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f0b33-109">Therefore, `HttpClient` is intended to be instantiated once and reused throughout the life of an application.</span></span> <span data-ttu-id="f0b33-110">A criação de uma instância de uma classe `HttpClient` para cada solicitação esgotará o número de soquetes disponíveis em condições de carga pesada.</span><span class="sxs-lookup"><span data-stu-id="f0b33-110">Instantiating an `HttpClient` class for every request will exhaust the number of sockets available under heavy loads.</span></span> <span data-ttu-id="f0b33-111">Esse problema resultará em erros de `SocketException`.</span><span class="sxs-lookup"><span data-stu-id="f0b33-111">That issue will result in `SocketException` errors.</span></span> <span data-ttu-id="f0b33-112">Abordagens possíveis para resolver o problema baseiam-se na criação do objeto `HttpClient` como singleton ou estático, conforme é explicado neste [artigo da Microsoft sobre o uso do HttpClient](../../../csharp/tutorials/console-webapiclient.md).</span><span class="sxs-lookup"><span data-stu-id="f0b33-112">Possible approaches to solve that problem are based on the creation of the `HttpClient` object as singleton or static, as explained in this [Microsoft article on HttpClient usage](../../../csharp/tutorials/console-webapiclient.md).</span></span> <span data-ttu-id="f0b33-113">Esta pode ser uma boa solução para aplicativos de console de curta duração ou similares que são executados algumas vezes por dia.</span><span class="sxs-lookup"><span data-stu-id="f0b33-113">This can be a good solution for short-lived console apps or similar that are run a few times a day.</span></span>

<span data-ttu-id="f0b33-114">Outro problema que os desenvolvedores se deparam é ao usar uma instância compartilhada de processos de `HttpClient` longo prazo.</span><span class="sxs-lookup"><span data-stu-id="f0b33-114">Another issue that developers run into is when using a shared instance of `HttpClient` in long running processes.</span></span> <span data-ttu-id="f0b33-115">Em uma situação em que o HttpClient é instanciado como um singleton ou um objeto estático, ele não consegue lidar com as alterações de DNS como descrito nesta [edição](https://github.com/dotnet/corefx/issues/11224) do repositório dotnet/corefx GitHub.</span><span class="sxs-lookup"><span data-stu-id="f0b33-115">In a situation where the HttpClient is instantiated as a singleton or a static object, it fails to handle the DNS changes as described in this [issue](https://github.com/dotnet/corefx/issues/11224) of the dotnet/corefx GitHub repository.</span></span>

<span data-ttu-id="f0b33-116">No entanto, o problema `HttpClient` não é realmente com per se, mas com o <xref:System.Net.Http.HttpMessageHandler>construtor padrão para [HttpClient](https://docs.microsoft.com/dotnet/api/system.net.http.httpclient.-ctor?view=netcore-3.1#System_Net_Http_HttpClient__ctor), porque cria uma nova instância concreta de , que é a que tem *soquetes exaustos* e dns altera problemas mencionados acima.</span><span class="sxs-lookup"><span data-stu-id="f0b33-116">However, the issue isn't really with `HttpClient` per se, but with the [default constructor for HttpClient](https://docs.microsoft.com/dotnet/api/system.net.http.httpclient.-ctor?view=netcore-3.1#System_Net_Http_HttpClient__ctor), because it creates a new concrete instance of <xref:System.Net.Http.HttpMessageHandler>, which is the one that has *sockets exhaustion* and DNS changes issues mentioned above.</span></span>

<span data-ttu-id="f0b33-117">Para resolver os problemas mencionados acima e tornar `HttpClient` as instâncias <xref:System.Net.Http.IHttpClientFactory> gerenciáveis, o .NET `HttpClient` Core 2.1 introduziu a interface que pode ser usada para configurar e criar instâncias em um aplicativo através da Injeção de Dependência (DI).</span><span class="sxs-lookup"><span data-stu-id="f0b33-117">To address the issues mentioned above and to make `HttpClient` instances manageable, .NET Core 2.1 introduced the <xref:System.Net.Http.IHttpClientFactory> interface which can be used to configure and create `HttpClient` instances in an app through Dependency Injection (DI).</span></span> <span data-ttu-id="f0b33-118">Ele também fornece extensões para middleware baseado em Polly para tirar proveito da delegar manipuladores em HttpClient.</span><span class="sxs-lookup"><span data-stu-id="f0b33-118">It also provides extensions for Polly-based middleware to take advantage of delegating handlers in HttpClient.</span></span>

<span data-ttu-id="f0b33-119">[O Polly](http://www.thepollyproject.org/) é uma biblioteca de manipulação de falhas transitórias que ajuda os desenvolvedores a adicionar resiliência aos seus aplicativos, usando algumas políticas pré-definidas de forma fluente e segura de segmentos.</span><span class="sxs-lookup"><span data-stu-id="f0b33-119">[Polly](http://www.thepollyproject.org/) is a transient-fault-handling library that helps developers add resiliency to their applications, by using some pre-defined policies in a fluent and thread-safe manner.</span></span>

## <a name="benefits-of-using-ihttpclientfactory"></a><span data-ttu-id="f0b33-120">Benefícios de usar ihttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="f0b33-120">Benefits of using IHttpClientFactory</span></span>

<span data-ttu-id="f0b33-121">A implementação <xref:System.Net.Http.IHttpClientFactory>atual de <xref:System.Net.Http.IHttpMessageHandlerFactory>, que também implementa , oferece os seguintes benefícios:</span><span class="sxs-lookup"><span data-stu-id="f0b33-121">The current implementation of <xref:System.Net.Http.IHttpClientFactory>, that also implements <xref:System.Net.Http.IHttpMessageHandlerFactory>, offers the following benefits:</span></span>

- <span data-ttu-id="f0b33-122">Fornece um local central para `HttpClient` nomear e configurar objetos lógicos.</span><span class="sxs-lookup"><span data-stu-id="f0b33-122">Provides a central location for naming and configuring logical `HttpClient` objects.</span></span> <span data-ttu-id="f0b33-123">Por exemplo, você pode configurar um cliente (agente de serviço) pré-configurado para acessar um microsserviço específico.</span><span class="sxs-lookup"><span data-stu-id="f0b33-123">For example, you may configure a client (Service Agent) that's pre-configured to access a specific microservice.</span></span>
- <span data-ttu-id="f0b33-124">Codififique o conceito de middleware de saída `HttpClient` através de delegar manipuladores e implementar middleware baseado em Polly para tirar proveito das políticas de resiliência da Polly.</span><span class="sxs-lookup"><span data-stu-id="f0b33-124">Codify the concept of outgoing middleware via delegating handlers in `HttpClient` and implementing Polly-based middleware to take advantage of Polly's policies for resiliency.</span></span>
- <span data-ttu-id="f0b33-125">O `HttpClient` já tem o conceito de delegar manipuladores que podem ser vinculados uns aos outros para solicitações HTTP de saída.</span><span class="sxs-lookup"><span data-stu-id="f0b33-125">`HttpClient` already has the concept of delegating handlers that could be linked together for outgoing HTTP requests.</span></span> <span data-ttu-id="f0b33-126">Você pode registrar clientes HTTP na fábrica e pode usar um manipulador Polly para usar as políticas polly para Retry, CircuitBreakers e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="f0b33-126">You can register HTTP clients into the factory and you can use a Polly handler to use Polly policies for Retry, CircuitBreakers, and so on.</span></span>
- <span data-ttu-id="f0b33-127">Gerencie a <xref:System.Net.Http.HttpMessageHandler> vida útil para evitar os problemas/problemas mencionados que podem ocorrer ao gerenciar `HttpClient` vidas sozinho.</span><span class="sxs-lookup"><span data-stu-id="f0b33-127">Manage the lifetime of <xref:System.Net.Http.HttpMessageHandler> to avoid the mentioned problems/issues that can occur when managing `HttpClient` lifetimes yourself.</span></span>

> [!TIP]
> <span data-ttu-id="f0b33-128">As `HttpClient` instâncias injetadas por DI, podem ser descartadas com segurança, pois as associadas `HttpMessageHandler` são gerenciadas pela fábrica.</span><span class="sxs-lookup"><span data-stu-id="f0b33-128">The `HttpClient` instances injected by DI, can be disposed of safely, because the associated `HttpMessageHandler` is managed by the factory.</span></span> <span data-ttu-id="f0b33-129">Na verdade, as instâncias injetadas `HttpClient` são escopo *de* uma perspectiva DI.</span><span class="sxs-lookup"><span data-stu-id="f0b33-129">As a matter of fact, injected `HttpClient` instances are *Scoped* from a DI perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="f0b33-130">A implementação de `IHttpClientFactory` (`DefaultHttpClientFactory`) está fortemente `Microsoft.Extensions.DependencyInjection` ligada à implementação di no pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="f0b33-130">The implementation of `IHttpClientFactory` (`DefaultHttpClientFactory`) is tightly tied to the DI implementation in the `Microsoft.Extensions.DependencyInjection` NuGet package.</span></span> <span data-ttu-id="f0b33-131">Para obter mais informações sobre o uso de outros contêineres DI, consulte esta [discussão do GitHub](https://github.com/dotnet/extensions/issues/1345).</span><span class="sxs-lookup"><span data-stu-id="f0b33-131">For more information about using other DI containers, see this [GitHub discussion](https://github.com/dotnet/extensions/issues/1345).</span></span>

## <a name="multiple-ways-to-use-ihttpclientfactory"></a><span data-ttu-id="f0b33-132">Várias maneiras de usar ihttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="f0b33-132">Multiple ways to use IHttpClientFactory</span></span>

<span data-ttu-id="f0b33-133">Há várias maneiras de usar o `IHttpClientFactory` no aplicativo:</span><span class="sxs-lookup"><span data-stu-id="f0b33-133">There are several ways that you can use `IHttpClientFactory` in your application:</span></span>

- <span data-ttu-id="f0b33-134">Uso básico</span><span class="sxs-lookup"><span data-stu-id="f0b33-134">Basic usage</span></span>
- <span data-ttu-id="f0b33-135">Usar clientes nomeados</span><span class="sxs-lookup"><span data-stu-id="f0b33-135">Use Named Clients</span></span>
- <span data-ttu-id="f0b33-136">Usar clientes tipados</span><span class="sxs-lookup"><span data-stu-id="f0b33-136">Use Typed Clients</span></span>
- <span data-ttu-id="f0b33-137">Usar clientes gerados</span><span class="sxs-lookup"><span data-stu-id="f0b33-137">Use Generated Clients</span></span>

<span data-ttu-id="f0b33-138">Por uma questão de brevidade, essa orientação `IHttpClientFactory`mostra a maneira mais estruturada de usar, que é usar clientes digitados (padrão de Agente de Serviço).</span><span class="sxs-lookup"><span data-stu-id="f0b33-138">For the sake of brevity, this guidance shows the most structured way to use `IHttpClientFactory`, which is to use Typed Clients (Service Agent pattern).</span></span> <span data-ttu-id="f0b33-139">No entanto, todas as opções estão documentadas e estão atualmente listadas neste [artigo cobrindo o `IHttpClientFactory` uso](/aspnet/core/fundamentals/http-requests#consumption-patterns).</span><span class="sxs-lookup"><span data-stu-id="f0b33-139">However, all options are documented and are currently listed in this [article covering the `IHttpClientFactory` usage](/aspnet/core/fundamentals/http-requests#consumption-patterns).</span></span>

## <a name="how-to-use-typed-clients-with-ihttpclientfactory"></a><span data-ttu-id="f0b33-140">Como usar clientes digitados com IHttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="f0b33-140">How to use Typed Clients with IHttpClientFactory</span></span>

<span data-ttu-id="f0b33-141">Portanto, o que é um "cliente tipado"?</span><span class="sxs-lookup"><span data-stu-id="f0b33-141">So, what's a "Typed Client"?</span></span> <span data-ttu-id="f0b33-142">É apenas um `HttpClient` que está pré-configurado para algum uso específico.</span><span class="sxs-lookup"><span data-stu-id="f0b33-142">It's just an `HttpClient` that's pre-configured for some specific use.</span></span> <span data-ttu-id="f0b33-143">Essa configuração pode incluir valores específicos, como o servidor base, cabeçalhos HTTP ou intervalos de tempo.</span><span class="sxs-lookup"><span data-stu-id="f0b33-143">This configuration can include specific values such as the base server, HTTP headers or time outs.</span></span>

<span data-ttu-id="f0b33-144">O diagrama a seguir mostra como os clientes tipados são usados com o `IHttpClientFactory`:</span><span class="sxs-lookup"><span data-stu-id="f0b33-144">The following diagram shows how Typed Clients are used with `IHttpClientFactory`:</span></span>

![Diagrama mostrando como os clientes digitados são usados com IHttpClientFactory.](./media/use-httpclientfactory-to-implement-resilient-http-requests/client-application-code.png)

<span data-ttu-id="f0b33-146">**Figura 8-4**.</span><span class="sxs-lookup"><span data-stu-id="f0b33-146">**Figure 8-4**.</span></span> <span data-ttu-id="f0b33-147">Usando `IHttpClientFactory` com classes de cliente digitado.</span><span class="sxs-lookup"><span data-stu-id="f0b33-147">Using `IHttpClientFactory` with Typed Client classes.</span></span>

<span data-ttu-id="f0b33-148">Na imagem acima, `ClientService` a (usada por um controlador `HttpClient` ou código cliente) usa um criado pelo registrado `IHttpClientFactory`.</span><span class="sxs-lookup"><span data-stu-id="f0b33-148">In the above image, a `ClientService` (used by a controller or client code) uses an `HttpClient` created by the registered `IHttpClientFactory`.</span></span> <span data-ttu-id="f0b33-149">Esta fábrica atribui `HttpMessageHandler` um de `HttpClient`uma piscina para o .</span><span class="sxs-lookup"><span data-stu-id="f0b33-149">This factory assigns an `HttpMessageHandler` from a pool to the `HttpClient`.</span></span> <span data-ttu-id="f0b33-150">O `HttpClient` pode ser configurado com as políticas `IHttpClientFactory` de Polly ao registrar <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*>o recipiente DI no recipiente DI com o método de extensão .</span><span class="sxs-lookup"><span data-stu-id="f0b33-150">The `HttpClient` can be configured with Polly's policies when registering the `IHttpClientFactory` in the DI container with the extension method <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*>.</span></span>

<span data-ttu-id="f0b33-151">Para configurar a estrutura <xref:System.Net.Http.IHttpClientFactory> acima, adicione seu `Microsoft.Extensions.Http` aplicativo instalando o <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*> pacote NuGet que inclui o método de extensão para <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>.</span><span class="sxs-lookup"><span data-stu-id="f0b33-151">To configure the above structure, add <xref:System.Net.Http.IHttpClientFactory> in your application by installing the `Microsoft.Extensions.Http` NuGet package that includes the <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*> extension method for <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>.</span></span> <span data-ttu-id="f0b33-152">Este método de extensão registra a classe interna `DefaultHttpClientFactory` `IHttpClientFactory`a ser usada como singleton para a interface .</span><span class="sxs-lookup"><span data-stu-id="f0b33-152">This extension method registers the internal `DefaultHttpClientFactory` class to be used as a singleton for the interface `IHttpClientFactory`.</span></span> <span data-ttu-id="f0b33-153">Ele define uma configuração transitória para o <xref:Microsoft.Extensions.Http.HttpMessageHandlerBuilder>.</span><span class="sxs-lookup"><span data-stu-id="f0b33-153">It defines a transient configuration for the <xref:Microsoft.Extensions.Http.HttpMessageHandlerBuilder>.</span></span> <span data-ttu-id="f0b33-154">Esse manipulador de mensagens (objeto <xref:System.Net.Http.HttpMessageHandler>), obtido de um pool, é usado pelo `HttpClient` retornado do alocador.</span><span class="sxs-lookup"><span data-stu-id="f0b33-154">This message handler (<xref:System.Net.Http.HttpMessageHandler> object), taken from a pool, is used by the `HttpClient` returned from the factory.</span></span>

<span data-ttu-id="f0b33-155">No próximo código, veja como `AddHttpClient()` pode ser usado para registrar clientes tipados (agentes de serviço) que precisam usar `HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="f0b33-155">In the next code, you can see how `AddHttpClient()` can be used to register Typed Clients (Service Agents) that need to use `HttpClient`.</span></span>

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services)
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

<span data-ttu-id="f0b33-156">Registrar os serviços do cliente como mostrado `DefaultClientFactory` no `HttpClient` código anterior, torna a criação um padrão para cada serviço.</span><span class="sxs-lookup"><span data-stu-id="f0b33-156">Registering the client services as shown in the previous code, makes the `DefaultClientFactory` create a standard `HttpClient` for each service.</span></span>

<span data-ttu-id="f0b33-157">Você também pode adicionar configuração específica de instância no registro para, por exemplo, configurar o endereço base e adicionar algumas políticas de resiliência, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="f0b33-157">You could also add instance-specific configuration in the registration to, for example, configure the base address, and add some resiliency policies, as shown in the following code:</span></span>

```csharp
services.AddHttpClient<ICatalogService, CatalogService>(client =>
{
    client.BaseAddress = new Uri(Configuration["BaseUrl"]);
})
    .AddPolicyHandler(GetRetryPolicy())
    .AddPolicyHandler(GetCircuitBreakerPolicy());
```

<span data-ttu-id="f0b33-158">Apenas por exemplo, você pode ver uma das políticas acima no próximo código:</span><span class="sxs-lookup"><span data-stu-id="f0b33-158">Just for the example sake, you can see one of the above policies in the next code:</span></span>

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)));
}
```

<span data-ttu-id="f0b33-159">Você pode encontrar mais detalhes sobre o uso de Polly no [artigo Next](implement-http-call-retries-exponential-backoff-polly.md).</span><span class="sxs-lookup"><span data-stu-id="f0b33-159">You can find more details about using Polly in the [Next article](implement-http-call-retries-exponential-backoff-polly.md).</span></span>

### <a name="httpclient-lifetimes"></a><span data-ttu-id="f0b33-160">Tempos de vida de HttpClient</span><span class="sxs-lookup"><span data-stu-id="f0b33-160">HttpClient lifetimes</span></span>

<span data-ttu-id="f0b33-161">Sempre que você receber um objeto `HttpClient` do `IHttpClientFactory`, uma nova instância será retornada.</span><span class="sxs-lookup"><span data-stu-id="f0b33-161">Each time you get an `HttpClient` object from the `IHttpClientFactory`, a new instance is returned.</span></span> <span data-ttu-id="f0b33-162">Mas cada `HttpClient` usa um `HttpMessageHandler` que foi colocado em pool e reutilizado pelo `IHttpClientFactory` para reduzir o consumo de recursos, desde que o tempo de vida do `HttpMessageHandler` não tenha expirado.</span><span class="sxs-lookup"><span data-stu-id="f0b33-162">But each `HttpClient` uses an `HttpMessageHandler` that's pooled and reused by the `IHttpClientFactory` to reduce resource consumption, as long as the `HttpMessageHandler`'s lifetime hasn't expired.</span></span>

<span data-ttu-id="f0b33-163">O pooling de manipuladores é interessante porque cada manipulador normalmente gerencia suas próprias conexões de HTTP subjacentes. Criar mais manipuladores do que o necessário pode resultar em atrasos de conexão.</span><span class="sxs-lookup"><span data-stu-id="f0b33-163">Pooling of handlers is desirable as each handler typically manages its own underlying HTTP connections; creating more handlers than necessary can result in connection delays.</span></span> <span data-ttu-id="f0b33-164">Alguns manipuladores também mantêm as conexões abertas indefinidamente, o que pode impedir que o manipulador reaja a alterações de DNS.</span><span class="sxs-lookup"><span data-stu-id="f0b33-164">Some handlers also keep connections open indefinitely, which can prevent the handler from reacting to DNS changes.</span></span>

<span data-ttu-id="f0b33-165">Os objetos `HttpMessageHandler` no pool têm um tempo de vida que é o período de tempo em que uma instância `HttpMessageHandler` no pool pode ser reutilizada.</span><span class="sxs-lookup"><span data-stu-id="f0b33-165">The `HttpMessageHandler` objects in the pool have a lifetime that's the length of time that an `HttpMessageHandler` instance in the pool can be reused.</span></span> <span data-ttu-id="f0b33-166">O valor padrão é dois minutos, mas pode ser substituído por cliente tipado.</span><span class="sxs-lookup"><span data-stu-id="f0b33-166">The default value is two minutes, but it can be overridden per Typed Client.</span></span> <span data-ttu-id="f0b33-167">Para substituí-lo, chame `SetHandlerLifetime()` no <xref:Microsoft.Extensions.DependencyInjection.IHttpClientBuilder> que é retornado ao criar o cliente, como mostra o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="f0b33-167">To override it, call `SetHandlerLifetime()` on the <xref:Microsoft.Extensions.DependencyInjection.IHttpClientBuilder> that's returned when creating the client, as shown in the following code:</span></span>

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client
services.AddHttpClient<ICatalogService, CatalogService>()
    .SetHandlerLifetime(TimeSpan.FromMinutes(5));
```

<span data-ttu-id="f0b33-168">Cada cliente tipado pode ter seu próprio valor de tempo de vida do manipulador configurado.</span><span class="sxs-lookup"><span data-stu-id="f0b33-168">Each Typed Client can have its own configured handler lifetime value.</span></span> <span data-ttu-id="f0b33-169">Defina o tempo de vida como `InfiniteTimeSpan` para desabilitar a expiração do manipulador.</span><span class="sxs-lookup"><span data-stu-id="f0b33-169">Set the lifetime to `InfiniteTimeSpan` to disable handler expiry.</span></span>

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a><span data-ttu-id="f0b33-170">Implementar suas classes de cliente tipado que usam o HttpClient injetado e configurado</span><span class="sxs-lookup"><span data-stu-id="f0b33-170">Implement your Typed Client classes that use the injected and configured HttpClient</span></span>

<span data-ttu-id="f0b33-171">Como etapa anterior, você precisa ter suas classes de Cliente Digitado definidas, como as classes no código de exemplo, como 'BasketService', 'CatalogService', 'OrderingService', etc. – Um Cliente Digitado é uma classe que aceita um `HttpClient` objeto (injetado através de seu construtor) e o usa para chamar algum serviço HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="f0b33-171">As a previous step, you need to have your Typed Client classes defined, such as the classes in the sample code, like 'BasketService', 'CatalogService', 'OrderingService', etc. – A Typed Client is a class that accepts an `HttpClient` object (injected through its constructor) and uses it to call some remote HTTP service.</span></span> <span data-ttu-id="f0b33-172">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="f0b33-172">For example:</span></span>

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

<span data-ttu-id="f0b33-173">O Cliente Digitado (`CatalogService` no exemplo) é ativado por DI (Dependency Injection), o que significa `HttpClient`que ele pode aceitar qualquer serviço registrado em sua construtora, além de .</span><span class="sxs-lookup"><span data-stu-id="f0b33-173">The Typed Client (`CatalogService` in the example) is activated by DI (Dependency Injection), meaning that it can accept any registered service in its constructor, in addition to `HttpClient`.</span></span>

<span data-ttu-id="f0b33-174">Um cliente tipado é, efetivamente, um objeto transitório, o que significa que uma instância é criada sempre que necessário e recebe uma nova instância de `HttpClient` sempre que é construída.</span><span class="sxs-lookup"><span data-stu-id="f0b33-174">A Typed Client is, effectively, a transient object, meaning that a new instance is created each time one is needed and it will receive a new `HttpClient` instance each time it's constructed.</span></span> <span data-ttu-id="f0b33-175">No entanto, os `HttpMessageHandler` objetos na piscina são `HttpClient` os objetos que são reutilizados por várias instâncias.</span><span class="sxs-lookup"><span data-stu-id="f0b33-175">However, the `HttpMessageHandler` objects in the pool are the objects that are reused by multiple `HttpClient` instances.</span></span>

### <a name="use-your-typed-client-classes"></a><span data-ttu-id="f0b33-176">Usar suas classes de cliente tipado</span><span class="sxs-lookup"><span data-stu-id="f0b33-176">Use your Typed Client classes</span></span>

<span data-ttu-id="f0b33-177">Finalmente, uma vez que você tenha suas classes digitadas implementadas e tê-las registradas e configuradas com `AddHttpClient()`, você pode usá-las onde você pode ter serviços injetados por DI.</span><span class="sxs-lookup"><span data-stu-id="f0b33-177">Finally, once you have your typed classes implemented and have them registered and configured with `AddHttpClient()`, you can use them wherever you can have services injected by DI.</span></span> <span data-ttu-id="f0b33-178">Por exemplo, em um código de página razor ou controlador de um aplicativo web MVC, como no seguinte código do eShopOnContainers:</span><span class="sxs-lookup"><span data-stu-id="f0b33-178">For example, in a Razor page code or controller of an MVC web app, like in the following code from eShopOnContainers:</span></span>

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

<span data-ttu-id="f0b33-179">Até este ponto, o código mostrado está apenas executando solicitações http regulares, mas a 'mágica' vem nas seguintes seções onde, apenas adicionando políticas `HttpClient` e delegando manipuladores aos seus Clientes Digitados registrados, todas as solicitações HTTP a serem feitas se comportarão levando em conta políticas resilientes, como tentativas com backoff exponencial, disjuntores ou qualquer outro manipulador personalizado para implementar recursos de segurança adicionais, como usar tokens auth ou qualquer outro recurso personalizado.</span><span class="sxs-lookup"><span data-stu-id="f0b33-179">Up to this point, the code shown is just performing regular Http requests, but the 'magic' comes in the following sections where, just by adding policies and delegating handlers to your registered Typed Clients, all the HTTP requests to be done by `HttpClient` will behave taking into account resilient policies such as retries with exponential backoff, circuit breakers, or any other custom delegating handler to implement additional security features, like using auth tokens, or any other custom feature.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="f0b33-180">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="f0b33-180">Additional resources</span></span>

- <span data-ttu-id="f0b33-181">**Usando HttpClientFactory no .NET Core**</span><span class="sxs-lookup"><span data-stu-id="f0b33-181">**Using HttpClientFactory in .NET Core**</span></span>  
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests](/aspnet/core/fundamentals/http-requests)

- <span data-ttu-id="f0b33-182">**Código-fonte httpClientFactory `dotnet/extensions` no repositório GitHub**</span><span class="sxs-lookup"><span data-stu-id="f0b33-182">**HttpClientFactory source code in the `dotnet/extensions` GitHub repository**</span></span>  
  <https://github.com/dotnet/extensions/tree/master/src/HttpClientFactory>

- <span data-ttu-id="f0b33-183">**Polly (biblioteca de tratamento de falhas transitórias e resiliência do .NET)**</span><span class="sxs-lookup"><span data-stu-id="f0b33-183">**Polly (.NET resilience and transient-fault-handling library)**</span></span>  
  <http://www.thepollyproject.org/>
  
- <span data-ttu-id="f0b33-184">**Usando iHttpClientFactory sem injeção de dependência (problema do GitHub)**</span><span class="sxs-lookup"><span data-stu-id="f0b33-184">**Using IHttpClientFactory without dependency injection (GitHub issue)**</span></span>  
  <https://github.com/dotnet/extensions/issues/1345>

>[!div class="step-by-step"]
><span data-ttu-id="f0b33-185">[Próximo](implement-resilient-entity-framework-core-sql-connections.md)
>[anterior](implement-http-call-retries-exponential-backoff-polly.md)</span><span class="sxs-lookup"><span data-stu-id="f0b33-185">[Previous](implement-resilient-entity-framework-core-sql-connections.md)
[Next](implement-http-call-retries-exponential-backoff-polly.md)</span></span>
