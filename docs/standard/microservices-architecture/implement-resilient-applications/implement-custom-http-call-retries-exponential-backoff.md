---
title: Implementando novas tentativas de chamadas HTTP personalizadas com retirada exponencial
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Implementando novas tentativas de chamadas HTTP personalizadas com retirada exponencial
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 77663f193b5f788ee07eba001306caed764ed253
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37104773"
---
# <a name="implementing-custom-http-call-retries-with-exponential-backoff"></a><span data-ttu-id="c636c-103">Implementando novas tentativas de chamadas HTTP personalizadas com retirada exponencial</span><span class="sxs-lookup"><span data-stu-id="c636c-103">Implementing custom HTTP call retries with exponential backoff</span></span>

<span data-ttu-id="c636c-104">Para criar microsserviços resilientes, é necessário manipular possíveis cenários de falha HTTP.</span><span class="sxs-lookup"><span data-stu-id="c636c-104">In order to create resilient microservices, you need to handle possible HTTP failure scenarios.</span></span> <span data-ttu-id="c636c-105">Para essa finalidade, é possível criar sua própria implementação de novas tentativas com retirada exponencial.</span><span class="sxs-lookup"><span data-stu-id="c636c-105">For that purpose, you could create your own implementation of retries with exponential backoff.</span></span>

<span data-ttu-id="c636c-106">Além de manipular a indisponibilidade de recursos temporais, a retirada exponencial também precisa levar em conta que o provedor de nuvem pode restringir a disponibilidade de recursos para evitar a sobrecarga de uso.</span><span class="sxs-lookup"><span data-stu-id="c636c-106">In addition to handling temporal resource unavailability, the exponential backoff also needs to take into account that the cloud provider might throttle availability of resources to prevent usage overload.</span></span> <span data-ttu-id="c636c-107">Por exemplo, a criação de muitas solicitações de conexão muito rapidamente pode ser exibida como um ataque [DoS](https://en.wikipedia.org/wiki/Denial-of-service_attack) (Negação de Serviço) pelo provedor de nuvem.</span><span class="sxs-lookup"><span data-stu-id="c636c-107">For example, creating too many connection requests very quickly might be viewed as a Denial of Service ([DoS](https://en.wikipedia.org/wiki/Denial-of-service_attack)) attack by the cloud provider.</span></span> <span data-ttu-id="c636c-108">Como resultado, será necessário fornecer um mecanismo para dimensionar as solicitações de conexão de retorno quando um limite de capacidade tiver sido encontrado.</span><span class="sxs-lookup"><span data-stu-id="c636c-108">As a result, you need to provide a mechanism to scale back connection requests when a capacity threshold has been encountered.</span></span>

<span data-ttu-id="c636c-109">Como uma exploração inicial, você poderia implementar seu próprio código com uma classe de utilitário para retirada exponencial como em [RetryWithExponentialBackoff.cs](https://gist.github.com/CESARDELATORRE/6d7f647b29e55fdc219ee1fd2babb260), além de código como o seguinte (que também está disponível em um [repositório GitHub](https://gist.github.com/CESARDELATORRE/d80c6423a1aebaffaf387469f5194f5b)).</span><span class="sxs-lookup"><span data-stu-id="c636c-109">As an initial exploration, you could implement your own code with a utility class for exponential backoff as in [RetryWithExponentialBackoff.cs](https://gist.github.com/CESARDELATORRE/6d7f647b29e55fdc219ee1fd2babb260), plus code like the following (which is also available on a [GitHub repo](https://gist.github.com/CESARDELATORRE/d80c6423a1aebaffaf387469f5194f5b)).</span></span>

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

<span data-ttu-id="c636c-110">Usar esse código em um aplicativo C\# cliente (outro microsserviço de cliente da API Web, um aplicativo MVC ASP.NET ou até mesmo um aplicativo Xamarin C\#) é simples.</span><span class="sxs-lookup"><span data-stu-id="c636c-110">Using this code in a client C\# application (another Web API client microservice, an ASP.NET MVC application, or even a C\# Xamarin application) is straightforward.</span></span> <span data-ttu-id="c636c-111">O exemplo a seguir mostra como fazer isso, usando a classe HttpClient.</span><span class="sxs-lookup"><span data-stu-id="c636c-111">The following example shows how, using the HttpClient class.</span></span>

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

<span data-ttu-id="c636c-112">No entanto, esse código é adequado apenas como uma prova de conceito.</span><span class="sxs-lookup"><span data-stu-id="c636c-112">However, this code is suitable only as a proof of concept.</span></span> <span data-ttu-id="c636c-113">O próximo tópico explica como usar bibliotecas mais sofisticadas e comprovadas.</span><span class="sxs-lookup"><span data-stu-id="c636c-113">The next topic explains how to use more sophisticated and proven libraries.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="c636c-114">[Anterior](implement-resilient-entity-framework-core-sql-connections.md)
[Próximo](implement-http-call-retries-exponential-backoff-polly.md)</span><span class="sxs-lookup"><span data-stu-id="c636c-114">[Previous](implement-resilient-entity-framework-core-sql-connections.md)
[Next](implement-http-call-retries-exponential-backoff-polly.md)</span></span>
