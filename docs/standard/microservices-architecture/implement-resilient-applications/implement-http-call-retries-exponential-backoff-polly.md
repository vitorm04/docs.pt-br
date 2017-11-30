---
title: "A implementação de novas tentativas de chamada HTTP com retirada exponencial com Polly"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | A implementação de novas tentativas de chamada HTTP com retirada exponencial com Polly"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 1ed48142546403ea710f4c132e038521232c20ed
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-http-call-retries-with-exponential-backoff-with-polly"></a><span data-ttu-id="3cb2d-104">A implementação de novas tentativas de chamada HTTP com retirada exponencial com Polly</span><span class="sxs-lookup"><span data-stu-id="3cb2d-104">Implementing HTTP call retries with exponential backoff with Polly</span></span>

<span data-ttu-id="3cb2d-105">É a abordagem recomendada para repetições com retirada exponencial tirar proveito das bibliotecas mais avançados do .NET como código-fonte aberto [Polly](https://github.com/App-vNext/Polly) biblioteca.</span><span class="sxs-lookup"><span data-stu-id="3cb2d-105">The recommended approach for retries with exponential backoff is to take advantage of more advanced .NET libraries like the open source [Polly](https://github.com/App-vNext/Polly) library.</span></span>

<span data-ttu-id="3cb2d-106">Polly é uma biblioteca .NET que fornece recursos de tratamento de falhas transitórias e resiliência.</span><span class="sxs-lookup"><span data-stu-id="3cb2d-106">Polly is a .NET library that provides resilience and transient-fault handling capabilities.</span></span> <span data-ttu-id="3cb2d-107">Você pode implementar esses recursos facilmente Aplicando políticas de Polly como repetição, disjuntor, isolamento Bulkhead, tempo limite e de Fallback.</span><span class="sxs-lookup"><span data-stu-id="3cb2d-107">You can implement those capabilities easily by applying Polly policies such as Retry, Circuit Breaker, Bulkhead Isolation, Timeout, and Fallback.</span></span> <span data-ttu-id="3cb2d-108">Polly tem como alvo o .NET 4. x e padrão do .NET versão 1.0 (que dá suporte ao .NET Core).</span><span class="sxs-lookup"><span data-stu-id="3cb2d-108">Polly targets .NET 4.x and the .NET Standard version 1.0 (which supports .NET Core).</span></span>

<span data-ttu-id="3cb2d-109">A política de repetição em Polly é a abordagem usada em eShopOnContainers durante a implementação de novas tentativas HTTP.</span><span class="sxs-lookup"><span data-stu-id="3cb2d-109">The Retry policy in Polly is the approach used in eShopOnContainers when implementing HTTP retries.</span></span> <span data-ttu-id="3cb2d-110">Você pode implementar uma interface para que você pode injetar funcionalidade HttpClient padrão ou uma versão resiliente HttpClient usando Polly, dependendo de qual configuração de política de repetição que deseja usar.</span><span class="sxs-lookup"><span data-stu-id="3cb2d-110">You can implement an interface so you can inject either standard HttpClient functionality or a resilient version of HttpClient using Polly, depending on what retry policy configuration you want to use.</span></span>

<span data-ttu-id="3cb2d-111">O exemplo a seguir mostra a interface implementada no eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="3cb2d-111">The following example shows the interface implemented in eShopOnContainers.</span></span>

```csharp
public interface IHttpClient
{
    Task<string> GetStringAsync(string uri, string authorizationToken = null,
        string authorizationMethod = "Bearer");
        Task<HttpResponseMessage> PostAsync<T>(string uri, T item,
        string authorizationToken = null, string requestId = null,
        string authorizationMethod = "Bearer");

    Task<HttpResponseMessage> DeleteAsync(string uri,
        string authorizationToken = null, string requestId = null,
        string authorizationMethod = "Bearer");

    // Other methods ...
}
```

<span data-ttu-id="3cb2d-112">Se você não deseja usar um mecanismo flexível, como quando você estiver desenvolvendo ou abordagens mais simples de teste, você pode usar a implementação padrão.</span><span class="sxs-lookup"><span data-stu-id="3cb2d-112">You can use the standard implementation if you do not want to use a resilient mechanism, as when you are developing or testing simpler approaches.</span></span> <span data-ttu-id="3cb2d-113">O código a seguir mostra as solicitações de permissão de implementação padrão do HttpClient com tokens de autenticação como um caso opcional.</span><span class="sxs-lookup"><span data-stu-id="3cb2d-113">The following code shows the standard HttpClient implementation allowing requests with authentication tokens as an optional case.</span></span>

```csharp
public class StandardHttpClient : IHttpClient
{
    private HttpClient _client;
    private ILogger<StandardHttpClient> _logger;

    public StandardHttpClient(ILogger<StandardHttpClient> logger)
    {
        _client = new HttpClient();
        _logger = logger;
    }

    public async Task<string> GetStringAsync(string uri,
        string authorizationToken = null,
        string authorizationMethod = "Bearer")
    {
        var requestMessage = new HttpRequestMessage(HttpMethod.Get, uri);
        if (authorizationToken != null)
        {
            requestMessage.Headers.Authorization =
                new AuthenticationHeaderValue(authorizationMethod, authorizationToken);
        }
        var response = await _client.SendAsync(requestMessage);
        return await response.Content.ReadAsStringAsync();
    }

    public async Task<HttpResponseMessage> PostAsync<T>(string uri, T item,
        string authorizationToken = null, string requestId = null,
        string authorizationMethod = "Bearer")
    {
        // Rest of the code and other Http methods ...
```

<span data-ttu-id="3cb2d-114">A implementação interessante é codificar classe outro, de forma semelhante, mas usando Polly para implementar os mecanismos resilientes que você deseja usar, no exemplo a seguir, novas tentativas com retirada exponencial.</span><span class="sxs-lookup"><span data-stu-id="3cb2d-114">The interesting implementation is to code another, similar class, but using Polly to implement the resilient mechanisms you want to use—in the following example, retries with exponential backoff.</span></span>

```csharp
public class ResilientHttpClient : IHttpClient
{
    private HttpClient _client;
    private PolicyWrap _policyWrapper;
    private ILogger<ResilientHttpClient> _logger;

    public ResilientHttpClient(Policy[] policies,
        ILogger<ResilientHttpClient> logger)
    {
        _client = new HttpClient();
        _logger = logger;
        // Add Policies to be applied
        _policyWrapper = Policy.WrapAsync(policies);
    }

    private Task<T> HttpInvoker<T>(Func<Task<T>> action)
    {
        // Executes the action applying all
        // the policies defined in the wrapper
        return _policyWrapper.ExecuteAsync(() => action());
    }

    public Task<string> GetStringAsync(string uri,
        string authorizationToken = null,
        string authorizationMethod = "Bearer")
    {
        return HttpInvoker(async () =>
        {
            var requestMessage = new HttpRequestMessage(HttpMethod.Get, uri);
            // The Token's related code eliminated for clarity in code snippet
            var response = await _client.SendAsync(requestMessage);
            return await response.Content.ReadAsStringAsync();
        });
    }
    // Other Http methods executed through HttpInvoker so it applies Polly policies
    // ...
}
```

<span data-ttu-id="3cb2d-115">Com Polly, você deve definir uma política de repetição com o número de repetições, a configuração de retirada exponencial e as ações a serem tomadas quando há uma exceção de HTTP, como registrar em log o erro.</span><span class="sxs-lookup"><span data-stu-id="3cb2d-115">With Polly, you define a Retry policy with the number of retries, the exponential backoff configuration, and the actions to take when there is an HTTP exception, such as logging the error.</span></span> <span data-ttu-id="3cb2d-116">Nesse caso, a política é configurada para que ele tentará o número de vezes especificado ao registrar os tipos no contêiner IoC.</span><span class="sxs-lookup"><span data-stu-id="3cb2d-116">In this case, the policy is configured so it will try the number of times specified when registering the types in the IoC container.</span></span> <span data-ttu-id="3cb2d-117">Por causa da configuração de retirada exponencial, sempre que o código detecta uma exceção de HttpRequest, tentar novamente a solicitação Http após aguardar um período de tempo que aumenta exponencialmente, dependendo de como a política foi configurada.</span><span class="sxs-lookup"><span data-stu-id="3cb2d-117">Because of the exponential backoff configuration, whenever the code detects an HttpRequest exception, it retries the Http request after waiting an amount of time that increases exponentially depending on how the policy was configured.</span></span>

<span data-ttu-id="3cb2d-118">O método importante é HttpInvoker, que faz com que as solicitações HTTP em toda esta classe de utilitário.</span><span class="sxs-lookup"><span data-stu-id="3cb2d-118">The important method is HttpInvoker, which is what makes HTTP requests throughout this utility class.</span></span> <span data-ttu-id="3cb2d-119">Que método é executado internamente a solicitação HTTP com \_policyWrapper.ExecuteAsync, que leva em conta a política de repetição.</span><span class="sxs-lookup"><span data-stu-id="3cb2d-119">That method internally executes the HTTP request with \_policyWrapper.ExecuteAsync, which takes into account the retry policy.</span></span>

<span data-ttu-id="3cb2d-120">EShopOnContainers você especifica políticas Polly ao registrar os tipos no contêiner IoC, como no código a seguir do [aplicativo da web MVC no startup.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Web/WebMVC/Startup.cs) classe.</span><span class="sxs-lookup"><span data-stu-id="3cb2d-120">In eShopOnContainers you specify Polly policies when registering the types at the IoC container, as in the following code from the [MVC web app at the startup.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Web/WebMVC/Startup.cs) class.</span></span>

```csharp
// Startup.cs class
if (Configuration.GetValue<string>("UseResilientHttp") == bool.TrueString)
{
    services.AddTransient<IResilientHttpClientFactory,
        ResilientHttpClientFactory>();
    services.AddSingleton<IHttpClient,
        ResilientHttpClient>(sp =>
            sp.GetService<IResilientHttpClientFactory>().
            CreateResilientHttpClient());
}
else
{
    services.AddSingleton<IHttpClient, StandardHttpClient>();
}
```

<span data-ttu-id="3cb2d-121">Observe que os objetos IHttpClient são instanciados como singleton em vez de como transitório para que as conexões TCP são usadas com eficiência pelo serviço e [um problema com soquetes](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) não ocorrerá.</span><span class="sxs-lookup"><span data-stu-id="3cb2d-121">Note that the IHttpClient objects are instantiated as singleton instead of as transient so that TCP connections are used efficiently by the service and [an issue with sockets](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) will not occur.</span></span>

<span data-ttu-id="3cb2d-122">Mas o ponto importante sobre resiliência que você aplique a política Polly WaitAndRetryAsync em ResilientHttpClientFactory no método CreateResilientHttpClient, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="3cb2d-122">But the important point about resiliency is that you apply the Polly WaitAndRetryAsync policy within ResilientHttpClientFactory in the CreateResilientHttpClient method, as shown in the following code:</span></span>

```csharp
public ResilientHttpClient CreateResilientHttpClient()
    => new ResilientHttpClient(CreatePolicies(), _logger);

// Other code
private Policy[] CreatePolicies()
    => new Policy[]
    {
        Policy.Handle<HttpRequestException>()
            .WaitAndRetryAsync(
        // number of retries
        6,
        // exponential backoff
        retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)),
        // on retry
        (exception, timeSpan, retryCount, context) =>
        {
            var msg = $"Retry {retryCount} implemented with Pollys RetryPolicy " +
            $"of {context.PolicyKey} " +
            $"at {context.ExecutionKey}, " +
            $"due to: {exception}.";
            _logger.LogWarning(msg);
            _logger.LogDebug(msg);
        }),
    }
```


>[!div class="step-by-step"]
<span data-ttu-id="3cb2d-123">[Anterior] (implement-custom-http-call-retries-exponential-backoff.md) [Avançar] (implementar-circuito-separador-pattern.md)</span><span class="sxs-lookup"><span data-stu-id="3cb2d-123">[Previous] (implement-custom-http-call-retries-exponential-backoff.md) [Next] (implement-circuit-breaker-pattern.md)</span></span>
