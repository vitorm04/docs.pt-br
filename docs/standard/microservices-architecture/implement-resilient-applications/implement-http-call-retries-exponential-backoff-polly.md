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
# <a name="implementing-http-call-retries-with-exponential-backoff-with-polly"></a>A implementação de novas tentativas de chamada HTTP com retirada exponencial com Polly

É a abordagem recomendada para repetições com retirada exponencial tirar proveito das bibliotecas mais avançados do .NET como código-fonte aberto [Polly](https://github.com/App-vNext/Polly) biblioteca.

Polly é uma biblioteca .NET que fornece recursos de tratamento de falhas transitórias e resiliência. Você pode implementar esses recursos facilmente Aplicando políticas de Polly como repetição, disjuntor, isolamento Bulkhead, tempo limite e de Fallback. Polly tem como alvo o .NET 4. x e padrão do .NET versão 1.0 (que dá suporte ao .NET Core).

A política de repetição em Polly é a abordagem usada em eShopOnContainers durante a implementação de novas tentativas HTTP. Você pode implementar uma interface para que você pode injetar funcionalidade HttpClient padrão ou uma versão resiliente HttpClient usando Polly, dependendo de qual configuração de política de repetição que deseja usar.

O exemplo a seguir mostra a interface implementada no eShopOnContainers.

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

Se você não deseja usar um mecanismo flexível, como quando você estiver desenvolvendo ou abordagens mais simples de teste, você pode usar a implementação padrão. O código a seguir mostra as solicitações de permissão de implementação padrão do HttpClient com tokens de autenticação como um caso opcional.

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

A implementação interessante é codificar classe outro, de forma semelhante, mas usando Polly para implementar os mecanismos resilientes que você deseja usar, no exemplo a seguir, novas tentativas com retirada exponencial.

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

Com Polly, você deve definir uma política de repetição com o número de repetições, a configuração de retirada exponencial e as ações a serem tomadas quando há uma exceção de HTTP, como registrar em log o erro. Nesse caso, a política é configurada para que ele tentará o número de vezes especificado ao registrar os tipos no contêiner IoC. Por causa da configuração de retirada exponencial, sempre que o código detecta uma exceção de HttpRequest, tentar novamente a solicitação Http após aguardar um período de tempo que aumenta exponencialmente, dependendo de como a política foi configurada.

O método importante é HttpInvoker, que faz com que as solicitações HTTP em toda esta classe de utilitário. Que método é executado internamente a solicitação HTTP com \_policyWrapper.ExecuteAsync, que leva em conta a política de repetição.

EShopOnContainers você especifica políticas Polly ao registrar os tipos no contêiner IoC, como no código a seguir do [aplicativo da web MVC no startup.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Web/WebMVC/Startup.cs) classe.

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

Observe que os objetos IHttpClient são instanciados como singleton em vez de como transitório para que as conexões TCP são usadas com eficiência pelo serviço e [um problema com soquetes](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) não ocorrerá.

Mas o ponto importante sobre resiliência que você aplique a política Polly WaitAndRetryAsync em ResilientHttpClientFactory no método CreateResilientHttpClient, conforme mostrado no código a seguir:

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
[Anterior] (implement-custom-http-call-retries-exponential-backoff.md) [Avançar] (implementar-circuito-separador-pattern.md)
