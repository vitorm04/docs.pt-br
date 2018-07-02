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
# <a name="implementing-http-call-retries-with-exponential-backoff-with-polly"></a>Implementando novas tentativas de chamadas HTTP com retirada exponencial com a Polly

A abordagem recomendada para novas tentativas com retirada exponencial é aproveitar as bibliotecas .NET mais avançadas como a biblioteca [Polly](https://github.com/App-vNext/Polly) de software livre.

A Polly é uma biblioteca .NET que fornece resiliência e recursos de tratamento de falhas temporárias. É possível implementar esses recursos facilmente aplicando políticas da Polly como Nova tentativa, Disjuntor, Isolamento bulkhead, Tempo limite e Fallback. A Polly direciona o .NET 4. x e o .NET Standard versão 1.0 (compatível com o .NET Core).

A política de repetição na Polly é a abordagem usada em eShopOnContainers ao implementar novas tentativas HTTP. É possível implementar uma interface para poder injetar funcionalidade HttpClient padrão ou uma versão resiliente de HttpClient que usa a Polly, dependendo de qual configuração de política de repetição você deseja usar.

O exemplo a seguir mostra a interface implementada em eShopOnContainers.

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

Será possível usar a implementação padrão se você não desejar usar um mecanismo resiliente, como quando você está desenvolvendo ou testando abordagens mais simples. O código a seguir mostra a implementação HttpClient padrão que permite solicitações com tokens de autenticação como um caso opcional.

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

A implementação interessante é codificar outra classe semelhante, mas usando a Polly para implementar os mecanismos resilientes que você deseja usar — no exemplo a seguir, novas tentativas com retirada exponencial.

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

Com a Polly, você define uma política de repetição com o número de novas tentativas, a configuração de retirada exponencial e as ações a serem executadas quando há uma exceção de HTTP, como registrar em log o erro. Nesse caso, a política é configurada, portanto, ela tentará o número de vezes especificado ao registrar os tipos no contêiner IoC. Por causa da configuração de retirada exponencial, sempre que o código detecta uma exceção HttpRequest, ele tenta novamente a solicitação Http após aguardar um período de tempo que aumenta exponencialmente dependendo de como a política foi configurada.

O método importante é HttpInvoker, que é o que cria solicitações HTTP em toda esta classe de utilitário. Esse método executa internamente a solicitação HTTP com \_policyWrapper.ExecuteAsync, que leva em consideração a política de repetição.

No eShopOnContainers, você especifica políticas Polly ao registrar os tipos no contêiner IoC, como no código a seguir da classe [aplicativo Web MVC no startup.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Web/WebMVC/Startup.cs).

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

Observe que uma instância dos objetos IHttpClient é criada como singleton, em vez de como temporária para que as conexões TCP sejam usadas com eficiência pelo serviço e [um problema com soquetes](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) não ocorrerá.

Mas o ponto importante sobre a resiliência é que você aplique a política WaitAndRetryAsync da Polly dentro de ResilientHttpClientFactory no método CreateResilientHttpClient, conforme mostrado no código a seguir:

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
[Anterior](implement-custom-http-call-retries-exponential-backoff.md)
[Próximo](implement-circuit-breaker-pattern.md)
