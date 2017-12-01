---
title: "Implementação de tentativas de chamada HTTP personalizadas com retirada exponencial"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Implementação de tentativas de chamada HTTP personalizadas com retirada exponencial"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 4449e5d7e0ca3c81aead26fac653de3ba2187a92
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-custom-http-call-retries-with-exponential-backoff"></a>Implementação de tentativas de chamada HTTP personalizadas com retirada exponencial

Para criar microservices resiliente, você precisa lidar com possíveis cenários de falha HTTP. Para essa finalidade, você pode criar sua própria implementação de novas tentativas com retirada exponencial.

Além de controlar a indisponibilidade do recurso temporal, a retirada exponencial também precisa levar em conta que o provedor de nuvem pode limitar a disponibilidade de recursos para evitar a sobrecarga de uso. Por exemplo, a criação de muitas solicitações de conexão rapidamente pode ser exibido como uma negação de serviço ([DoS](https://en.wikipedia.org/wiki/Denial-of-service_attack)) ataque pelo provedor de nuvem. Como resultado, você precisa fornecer um mecanismo para dimensionar as solicitações de conexão back quando um limite de capacidade foi encontrado.

Como uma exploração inicial, você pode implementar seu próprio código com uma classe de utilitário para retirada exponencial como em [RetryWithExponentialBackoff.cs](https://gist.github.com/CESARDELATORRE/6d7f647b29e55fdc219ee1fd2babb260), além de código semelhante ao seguinte (que também está disponível em um [repositório GitHub ](https://gist.github.com/CESARDELATORRE/d80c6423a1aebaffaf387469f5194f5b)).

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

Usando esse código em um cliente C\# aplicativo (outro microsserviço de cliente de API da Web, um aplicativo ASP.NET MVC ou até mesmo um C\# aplicativo Xamarin) é simples. A exemplo a seguir mostra como fazer isso, usando a classe HttpClient.

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

No entanto, esse código é adequado somente como uma prova de conceito. O próximo tópico explica como usar bibliotecas mais sofisticadas e testadas.


>[!div class="step-by-step"]
[Anterior] (implement-resilient-entity-framework-core-sql-connections.md) [Avançar] (implement-http-call-retries-exponential-backoff-polly.md)
