---
title: Implementando novas tentativas de chamadas HTTP com retirada exponencial com a Polly
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Implementando novas tentativas de chamadas HTTP com retirada exponencial com a Polly
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: cce1392bb381859e7cad89c9f2518113241ae724
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106925"
---
# <a name="implementing-http-call-retries-with-exponential-backoff-with-polly"></a><span data-ttu-id="8fe84-103">Implementando novas tentativas de chamadas HTTP com retirada exponencial com a Polly</span><span class="sxs-lookup"><span data-stu-id="8fe84-103">Implementing HTTP call retries with exponential backoff with Polly</span></span>

<span data-ttu-id="8fe84-104">A abordagem recomendada para novas tentativas com retirada exponencial é aproveitar as bibliotecas .NET mais avançadas como a biblioteca [Polly](https://github.com/App-vNext/Polly) de software livre.</span><span class="sxs-lookup"><span data-stu-id="8fe84-104">The recommended approach for retries with exponential backoff is to take advantage of more advanced .NET libraries like the open source [Polly](https://github.com/App-vNext/Polly) library.</span></span>

<span data-ttu-id="8fe84-105">A Polly é uma biblioteca .NET que fornece resiliência e recursos de tratamento de falhas temporárias.</span><span class="sxs-lookup"><span data-stu-id="8fe84-105">Polly is a .NET library that provides resilience and transient-fault handling capabilities.</span></span> <span data-ttu-id="8fe84-106">É possível implementar esses recursos facilmente aplicando políticas da Polly como Nova tentativa, Disjuntor, Isolamento bulkhead, Tempo limite e Fallback.</span><span class="sxs-lookup"><span data-stu-id="8fe84-106">You can implement those capabilities easily by applying Polly policies such as Retry, Circuit Breaker, Bulkhead Isolation, Timeout, and Fallback.</span></span> <span data-ttu-id="8fe84-107">A Polly direciona o .NET 4. x e o .NET Standard versão 1.0 (compatível com o .NET Core).</span><span class="sxs-lookup"><span data-stu-id="8fe84-107">Polly targets .NET 4.x and the .NET Standard version 1.0 (which supports .NET Core).</span></span>

<span data-ttu-id="8fe84-108">A política de repetição na Polly é a abordagem usada em eShopOnContainers ao implementar novas tentativas HTTP.</span><span class="sxs-lookup"><span data-stu-id="8fe84-108">The Retry policy in Polly is the approach used in eShopOnContainers when implementing HTTP retries.</span></span> <span data-ttu-id="8fe84-109">É possível implementar uma interface para poder injetar funcionalidade HttpClient padrão ou uma versão resiliente de HttpClient que usa a Polly, dependendo de qual configuração de política de repetição você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="8fe84-109">You can implement an interface so you can inject either standard HttpClient functionality or a resilient version of HttpClient using Polly, depending on what retry policy configuration you want to use.</span></span>

<span data-ttu-id="8fe84-110">O exemplo a seguir mostra a interface implementada em eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="8fe84-110">The following example shows the interface implemented in eShopOnContainers.</span></span>

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

<span data-ttu-id="8fe84-111">Será possível usar a implementação padrão se você não desejar usar um mecanismo resiliente, como quando você está desenvolvendo ou testando abordagens mais simples.</span><span class="sxs-lookup"><span data-stu-id="8fe84-111">You can use the standard implementation if you do not want to use a resilient mechanism, as when you are developing or testing simpler approaches.</span></span> <span data-ttu-id="8fe84-112">O código a seguir mostra a implementação HttpClient padrão que permite solicitações com tokens de autenticação como um caso opcional.</span><span class="sxs-lookup"><span data-stu-id="8fe84-112">The following code shows the standard HttpClient implementation allowing requests with authentication tokens as an optional case.</span></span>

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

<span data-ttu-id="8fe84-113">A implementação interessante é codificar outra classe semelhante, mas usando a Polly para implementar os mecanismos resilientes que você deseja usar — no exemplo a seguir, novas tentativas com retirada exponencial.</span><span class="sxs-lookup"><span data-stu-id="8fe84-113">The interesting implementation is to code another, similar class, but using Polly to implement the resilient mechanisms you want to use—in the following example, retries with exponential backoff.</span></span>

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

<span data-ttu-id="8fe84-114">Com a Polly, você define uma política de repetição com o número de novas tentativas, a configuração de retirada exponencial e as ações a serem executadas quando há uma exceção de HTTP, como registrar em log o erro.</span><span class="sxs-lookup"><span data-stu-id="8fe84-114">With Polly, you define a Retry policy with the number of retries, the exponential backoff configuration, and the actions to take when there is an HTTP exception, such as logging the error.</span></span> <span data-ttu-id="8fe84-115">Nesse caso, a política é configurada, portanto, ela tentará o número de vezes especificado ao registrar os tipos no contêiner IoC.</span><span class="sxs-lookup"><span data-stu-id="8fe84-115">In this case, the policy is configured so it will try the number of times specified when registering the types in the IoC container.</span></span> <span data-ttu-id="8fe84-116">Por causa da configuração de retirada exponencial, sempre que o código detecta uma exceção HttpRequest, ele tenta novamente a solicitação Http após aguardar um período de tempo que aumenta exponencialmente dependendo de como a política foi configurada.</span><span class="sxs-lookup"><span data-stu-id="8fe84-116">Because of the exponential backoff configuration, whenever the code detects an HttpRequest exception, it retries the Http request after waiting an amount of time that increases exponentially depending on how the policy was configured.</span></span>

<span data-ttu-id="8fe84-117">O método importante é HttpInvoker, que é o que cria solicitações HTTP em toda esta classe de utilitário.</span><span class="sxs-lookup"><span data-stu-id="8fe84-117">The important method is HttpInvoker, which is what makes HTTP requests throughout this utility class.</span></span> <span data-ttu-id="8fe84-118">Esse método executa internamente a solicitação HTTP com \_policyWrapper.ExecuteAsync, que leva em consideração a política de repetição.</span><span class="sxs-lookup"><span data-stu-id="8fe84-118">That method internally executes the HTTP request with \_policyWrapper.ExecuteAsync, which takes into account the retry policy.</span></span>

<span data-ttu-id="8fe84-119">No eShopOnContainers, você especifica políticas Polly ao registrar os tipos no contêiner IoC, como no código a seguir da classe [aplicativo Web MVC no startup.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Web/WebMVC/Startup.cs).</span><span class="sxs-lookup"><span data-stu-id="8fe84-119">In eShopOnContainers you specify Polly policies when registering the types at the IoC container, as in the following code from the [MVC web app at the startup.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Web/WebMVC/Startup.cs) class.</span></span>

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

<span data-ttu-id="8fe84-120">Observe que uma instância dos objetos IHttpClient é criada como singleton, em vez de como temporária para que as conexões TCP sejam usadas com eficiência pelo serviço e [um problema com soquetes](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) não ocorrerá.</span><span class="sxs-lookup"><span data-stu-id="8fe84-120">Note that the IHttpClient objects are instantiated as singleton instead of as transient so that TCP connections are used efficiently by the service and [an issue with sockets](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) will not occur.</span></span>

<span data-ttu-id="8fe84-121">Mas o ponto importante sobre a resiliência é que você aplique a política WaitAndRetryAsync da Polly dentro de ResilientHttpClientFactory no método CreateResilientHttpClient, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="8fe84-121">But the important point about resiliency is that you apply the Polly WaitAndRetryAsync policy within ResilientHttpClientFactory in the CreateResilientHttpClient method, as shown in the following code:</span></span>

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
<span data-ttu-id="8fe84-122">[Anterior](implement-custom-http-call-retries-exponential-backoff.md)
[Próximo](implement-circuit-breaker-pattern.md)</span><span class="sxs-lookup"><span data-stu-id="8fe84-122">[Previous](implement-custom-http-call-retries-exponential-backoff.md)
[Next](implement-circuit-breaker-pattern.md)</span></span>
