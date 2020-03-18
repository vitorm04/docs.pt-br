---
title: Implementar repetições de chamadas HTTP com retirada exponencial com a Polly
description: Aprenda a lidar com falhas HTTP com Polly e IHttpClientFactory.
ms.date: 03/03/2020
ms.openlocfilehash: 49396dd545a05699278254474c77acf1483e0e0c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846790"
---
# <a name="implement-http-call-retries-with-exponential-backoff-with-ihttpclientfactory-and-polly-policies"></a><span data-ttu-id="534ac-103">Implementar tentativas de chamada HTTP com backoff exponencial com políticas IHttpClientFactory e Polly</span><span class="sxs-lookup"><span data-stu-id="534ac-103">Implement HTTP call retries with exponential backoff with IHttpClientFactory and Polly policies</span></span>

<span data-ttu-id="534ac-104">A abordagem recomendada para repetições com retirada exponencial é aproveitar as bibliotecas do .NET mais avançadas como a [biblioteca Polly](https://github.com/App-vNext/Polly) de software livre.</span><span class="sxs-lookup"><span data-stu-id="534ac-104">The recommended approach for retries with exponential backoff is to take advantage of more advanced .NET libraries like the open-source [Polly library](https://github.com/App-vNext/Polly).</span></span>

<span data-ttu-id="534ac-105">A Polly é uma biblioteca .NET que fornece resiliência e recursos de tratamento de falhas temporárias.</span><span class="sxs-lookup"><span data-stu-id="534ac-105">Polly is a .NET library that provides resilience and transient-fault handling capabilities.</span></span> <span data-ttu-id="534ac-106">Você pode implementar essas funcionalidades por meio da aplicação de políticas da Polly como repetição, disjuntor, isolamento do bulkhead, tempo limite e fallback.</span><span class="sxs-lookup"><span data-stu-id="534ac-106">You can implement those capabilities by applying Polly policies such as Retry, Circuit Breaker, Bulkhead Isolation, Timeout, and Fallback.</span></span> <span data-ttu-id="534ac-107">O Polly tem como alvo o .NET Framework 4.x e o .NET Standard 1.0, 1.1 e 2.0 (que suporta o .NET Core).</span><span class="sxs-lookup"><span data-stu-id="534ac-107">Polly targets .NET Framework 4.x and .NET Standard 1.0, 1.1, and 2.0 (which supports .NET Core).</span></span>

<span data-ttu-id="534ac-108">As etapas a seguir mostram como você `IHttpClientFactory`pode usar as repetições http com polly integrada, o que é explicado na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="534ac-108">The following steps show how you can use Http retries with Polly integrated into `IHttpClientFactory`, which is explained in the previous section.</span></span>

<span data-ttu-id="534ac-109">**Referenciar os pacotes ASP.NET Core 3.1**</span><span class="sxs-lookup"><span data-stu-id="534ac-109">**Reference the ASP.NET Core 3.1 packages**</span></span>

<span data-ttu-id="534ac-110">`IHttpClientFactory`está disponível desde .NET Core 2.1 no entanto recomendamos que você use os pacotes mais recentes ASP.NET Core 3.1 do NuGet em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="534ac-110">`IHttpClientFactory` is available since .NET Core 2.1 however we recommend you to use the latest ASP.NET Core 3.1 packages from NuGet in your project.</span></span> <span data-ttu-id="534ac-111">Você normalmente também precisa fazer `Microsoft.Extensions.Http.Polly`referência ao pacote de extensão .</span><span class="sxs-lookup"><span data-stu-id="534ac-111">You typically also need to reference the extension package `Microsoft.Extensions.Http.Polly`.</span></span>

<span data-ttu-id="534ac-112">**Configure um cliente com a política de Repetição da Polly, em Inicialização**</span><span class="sxs-lookup"><span data-stu-id="534ac-112">**Configure a client with Polly's Retry policy, in Startup**</span></span>

<span data-ttu-id="534ac-113">Conforme mostrado nas seções anteriores, você precisa definir uma configuração cliente do HttpClient nomeada ou tipada no método padrão Startup.ConfigureServices(...), mas agora, adicione o código incremental especificando a política para as repetições de HTTP com retirada exponencial, como é mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="534ac-113">As shown in previous sections, you need to define a named or typed client HttpClient configuration in your standard Startup.ConfigureServices(...) method, but now, you add incremental code specifying the policy for the Http retries with exponential backoff, as below:</span></span>

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

<span data-ttu-id="534ac-114">O método **AddPolicyHandler()** é aquele que adiciona políticas aos objetos `HttpClient` que você usará.</span><span class="sxs-lookup"><span data-stu-id="534ac-114">The **AddPolicyHandler()** method is what adds policies to the `HttpClient` objects you'll use.</span></span> <span data-ttu-id="534ac-115">Neste caso, está adicionando uma política da Polly para Http Retries com recuo exponencial.</span><span class="sxs-lookup"><span data-stu-id="534ac-115">In this case, it's adding a Polly's policy for Http Retries with exponential backoff.</span></span>

<span data-ttu-id="534ac-116">Para obter uma abordagem mais modular, a política de repetição de HTTP pode ser definida em um método separado no arquivo `Startup.cs`, como mostra o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="534ac-116">To have a more modular approach, the Http Retry Policy can be defined in a separate method within the `Startup.cs` file, as shown in the following code:</span></span>

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2,
                                                                    retryAttempt)));
}
```

<span data-ttu-id="534ac-117">Com a Polly, você pode definir uma política de repetição com o número de repetições, a configuração de retirada exponencial e as ações a serem executadas quando houver uma exceção de HTTP, como registrar o erro em log.</span><span class="sxs-lookup"><span data-stu-id="534ac-117">With Polly, you can define a Retry policy with the number of retries, the exponential backoff configuration, and the actions to take when there's an HTTP exception, such as logging the error.</span></span> <span data-ttu-id="534ac-118">Nesse caso, a política é configurada para tentar seis vezes com uma repetição exponencial, começando em dois segundos.</span><span class="sxs-lookup"><span data-stu-id="534ac-118">In this case, the policy is configured to try six times with an exponential retry, starting at two seconds.</span></span>

## <a name="add-a-jitter-strategy-to-the-retry-policy"></a><span data-ttu-id="534ac-119">Adicionar uma estratégia de tremulação à política de repetição</span><span class="sxs-lookup"><span data-stu-id="534ac-119">Add a jitter strategy to the retry policy</span></span>

<span data-ttu-id="534ac-120">Uma política de Repetição regular pode afetar o sistema em casos de alta simultaneidade e escalabilidade e sob alta contenção.</span><span class="sxs-lookup"><span data-stu-id="534ac-120">A regular Retry policy can impact your system in cases of high concurrency and scalability and under high contention.</span></span> <span data-ttu-id="534ac-121">Para superar os picos de novas tentativas semelhantes provenientes de muitos clientes em caso de interrupções parciais, uma boa solução alternativa é adicionar uma estratégia de variação à política/ao algoritmo de novas tentativas.</span><span class="sxs-lookup"><span data-stu-id="534ac-121">To overcome peaks of similar retries coming from many clients in case of partial outages, a good workaround is to add a jitter strategy to the retry algorithm/policy.</span></span> <span data-ttu-id="534ac-122">Isso pode melhorar o desempenho geral do sistema de ponta a ponta, adicionando aleatoriedade à retirada exponencial.</span><span class="sxs-lookup"><span data-stu-id="534ac-122">This can improve the overall performance of the end-to-end system by adding randomness to the exponential backoff.</span></span> <span data-ttu-id="534ac-123">Isso espalha os picos quando surgem problemas.</span><span class="sxs-lookup"><span data-stu-id="534ac-123">This spreads out the spikes when issues arise.</span></span> <span data-ttu-id="534ac-124">O princípio é ilustrado pelo seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="534ac-124">The principle is illustrated by the following example:</span></span>

```csharp
Random jitterer = new Random();
var retryWithJitterPolicy = HttpPolicyExtensions
    .HandleTransientHttpError()
    .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
    .WaitAndRetryAsync(6,    // exponential back-off plus some jitter
        retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))  
                      + TimeSpan.FromMilliseconds(jitterer.Next(0, 100))
    );
```

<span data-ttu-id="534ac-125">Polly fornece algoritmos de jitter prontos para a produção através do site do projeto.</span><span class="sxs-lookup"><span data-stu-id="534ac-125">Polly provides production-ready jitter algorithms via the project website.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="534ac-126">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="534ac-126">Additional resources</span></span>

- <span data-ttu-id="534ac-127">**Padrão de repetição**</span><span class="sxs-lookup"><span data-stu-id="534ac-127">**Retry pattern**</span></span>  
  [https://docs.microsoft.com/azure/architecture/patterns/retry](/azure/architecture/patterns/retry)

- <span data-ttu-id="534ac-128">**Polly e IHttpClientFactory**</span><span class="sxs-lookup"><span data-stu-id="534ac-128">**Polly and IHttpClientFactory**</span></span>  
  <https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory>

- <span data-ttu-id="534ac-129">**Polly (biblioteca de tratamento de falhas transitórias e resiliência do .NET)**</span><span class="sxs-lookup"><span data-stu-id="534ac-129">**Polly (.NET resilience and transient-fault-handling library)**</span></span>  
  <https://github.com/App-vNext/Polly>

- <span data-ttu-id="534ac-130">**Polly: Tente com jitter**</span><span class="sxs-lookup"><span data-stu-id="534ac-130">**Polly: Retry with Jitter**</span></span>  
  <https://github.com/App-vNext/Polly/wiki/Retry-with-jitter>

- <span data-ttu-id="534ac-131">**Marc Brooker. Jitter: Tornando as coisas melhores com a leatoriedade**</span><span class="sxs-lookup"><span data-stu-id="534ac-131">**Marc Brooker. Jitter: Making Things Better With Randomness**</span></span>  
  <https://brooker.co.za/blog/2015/03/21/backoff.html>

>[!div class="step-by-step"]
><span data-ttu-id="534ac-132">[Próximo](use-httpclientfactory-to-implement-resilient-http-requests.md)
>[anterior](implement-circuit-breaker-pattern.md)</span><span class="sxs-lookup"><span data-stu-id="534ac-132">[Previous](use-httpclientfactory-to-implement-resilient-http-requests.md)
[Next](implement-circuit-breaker-pattern.md)</span></span>
