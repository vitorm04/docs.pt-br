---
title: Explorar repetições de chamadas HTTP personalizadas com retirada exponencial
description: Saiba como você pode implementar do zero, as repetições de chamadas HTTP com retirada exponencial para lidar com possíveis cenários de falha de HTTP.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/08/2018
ms.openlocfilehash: b7aaad9199bb275f45fd088a6207d707e8e5751c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53145092"
---
# <a name="explore-custom-http-call-retries-with-exponential-backoff"></a>Explorar repetições de chamadas HTTP personalizadas com retirada exponencial

Para criar microsserviços resilientes, você precisa lidar com possíveis cenários de falha de HTTP. Uma maneira de lidar com essas falhas, embora não seja recomendada, é criar sua própria implementação de repetições com retirada exponencial.

**Observação importante:** esta seção mostra como você poderia criar seu próprio código personalizado para implementar repetições de chamadas HTTP. No entanto, não é recomendado fazer isso sozinho, mas sim usar mecanismos mais avançados e confiáveis, embora mais simples de usar, como o `HttpClientFactory` com a Polly, disponível desde o .NET Core 2.1. As abordagens recomendadas são explicadas nas próximas seções. 

Como uma exploração inicial, você poderia implementar seu próprio código com uma classe de utilitário para retirada exponencial como em [RetryWithExponentialBackoff.cs](https://gist.github.com/CESARDELATORRE/6d7f647b29e55fdc219ee1fd2babb260), além do código como o seguinte (que também está disponível em um [repositório do GitHub](https://gist.github.com/CESARDELATORRE/d80c6423a1aebaffaf387469f5194f5b)).

```csharp
public sealed class RetryWithExponentialBackoff
{
    private readonly int maxRetries, delayMilliseconds, maxDelayMilliseconds;

    public RetryWithExponentialBackoff(int maxRetries = 50,
        int delayMilliseconds = 200,
        int maxDelayMilliseconds = 2000)
    {
        this.maxRetries = maxRetries;
        this.delayMilliseconds = delayMilliseconds;
        this.maxDelayMilliseconds = maxDelayMilliseconds;
    }

    public async Task RunAsync(Func<Task> func)
    {
        ExponentialBackoff backoff = new ExponentialBackoff(this.maxRetries,
            this.delayMilliseconds,
            this.maxDelayMilliseconds);
        retry:
        try
        {
            await func();
        }
        catch (Exception ex) when (ex is TimeoutException ||
            ex is System.Net.Http.HttpRequestException)
        {
            Debug.WriteLine("Exception raised is: " +
                ex.GetType().ToString() +
                " –Message: " + ex.Message +
                " -- Inner Message: " +
                ex.InnerException.Message);
            await backoff.Delay();
            goto retry;
        }
    }
}

public struct ExponentialBackoff
{
    private readonly int m_maxRetries, m_delayMilliseconds, m_maxDelayMilliseconds;
    private int m_retries, m_pow;

    public ExponentialBackoff(int maxRetries, int delayMilliseconds,
        int maxDelayMilliseconds)
    {
        m_maxRetries = maxRetries;
        m_delayMilliseconds = delayMilliseconds;
        m_maxDelayMilliseconds = maxDelayMilliseconds;
        m_retries = 0;
        m_pow = 1;
    }

    public Task Delay()
    {
        if (m_retries == m_maxRetries)
        {
            throw new TimeoutException("Max retry attempts exceeded.");
        }
        ++m_retries;
        if (m_retries < 31)
        {
            m_pow = m_pow << 1; // m_pow = Pow(2, m_retries - 1)
        }
        int delay = Math.Min(m_delayMilliseconds * (m_pow - 1) / 2,
            m_maxDelayMilliseconds);
        return Task.Delay(delay);
    }
}
```

Usar esse código em um aplicativo C\# cliente (outro microsserviço de cliente da API Web, um aplicativo MVC ASP.NET ou até mesmo um aplicativo Xamarin C\#) é simples. O exemplo a seguir mostra como fazer isso, usando a classe HttpClient.

```csharp
public async Task<Catalog> GetCatalogItems(int page,int take, int? brand, int? type)
{
    _apiClient = new HttpClient();
    var itemsQs = $"items?pageIndex={page}&pageSize={take}";
    var filterQs = "";
    var catalogUrl = $"{_remoteServiceBaseUrl}items{filterQs}?pageIndex={page}&pageSize={take}";
    var dataString = "";
    //
    // Using HttpClient with Retry and Exponential Backoff
    //
    var retry = new RetryWithExponentialBackoff();
    await retry.RunAsync(async () =>
    {
        // work with HttpClient call
        dataString = await _apiClient.GetStringAsync(catalogUrl);
    });
    return JsonConvert.DeserializeObject<Catalog>(dataString);
}
```

Lembre-se de que esse código é adequado apenas para prova de conceito. As próximas seções explicam como usar abordagens mais sofisticadas, embora mais simples, usando o HttpClientFactory.
O HttpClientFactory está disponível desde o .NET Core 2.1, com bibliotecas de resiliência comprovadas, como a Polly. 

>[!div class="step-by-step"]
>[Anterior](implement-resilient-entity-framework-core-sql-connections.md)
>[Próximo](use-httpclientfactory-to-implement-resilient-http-requests.md)