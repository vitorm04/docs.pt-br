---
title: Implementar repetições de chamadas HTTP com retirada exponencial com a Polly
description: Saiba como tratar falhas de HTTP com a Polly e o HttpClientFactory.
ms.date: 01/07/2019
ms.openlocfilehash: 551cd1230c565b30c81090c984747e726680b9ed
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73089966"
---
# <a name="implement-http-call-retries-with-exponential-backoff-with-httpclientfactory-and-polly-policies"></a><span data-ttu-id="62813-103">Implementar repetições de chamadas HTTP com retirada exponencial com o HttpClientFactory e políticas da Polly</span><span class="sxs-lookup"><span data-stu-id="62813-103">Implement HTTP call retries with exponential backoff with HttpClientFactory and Polly policies</span></span>

<span data-ttu-id="62813-104">A abordagem recomendada para repetições com retirada exponencial é aproveitar as bibliotecas do .NET mais avançadas como a [biblioteca Polly](https://github.com/App-vNext/Polly) de software livre.</span><span class="sxs-lookup"><span data-stu-id="62813-104">The recommended approach for retries with exponential backoff is to take advantage of more advanced .NET libraries like the open-source [Polly library](https://github.com/App-vNext/Polly).</span></span>

<span data-ttu-id="62813-105">A Polly é uma biblioteca .NET que fornece resiliência e recursos de tratamento de falhas temporárias.</span><span class="sxs-lookup"><span data-stu-id="62813-105">Polly is a .NET library that provides resilience and transient-fault handling capabilities.</span></span> <span data-ttu-id="62813-106">Você pode implementar essas funcionalidades por meio da aplicação de políticas da Polly como repetição, disjuntor, isolamento do bulkhead, tempo limite e fallback.</span><span class="sxs-lookup"><span data-stu-id="62813-106">You can implement those capabilities by applying Polly policies such as Retry, Circuit Breaker, Bulkhead Isolation, Timeout, and Fallback.</span></span> <span data-ttu-id="62813-107">Polly targets .NET Framework 4. x e .NET Standard 1,0, 1,1 e 2,0 (que dá suporte ao .NET Core).</span><span class="sxs-lookup"><span data-stu-id="62813-107">Polly targets .NET Framework 4.x and .NET Standard 1.0, 1.1, and 2.0 (which supports .NET Core).</span></span>

<span data-ttu-id="62813-108">No entanto, escrever seu próprio código personalizado para usar a biblioteca do Polly com HttpClient pode ser significativamente complexo.</span><span class="sxs-lookup"><span data-stu-id="62813-108">However, writing your own custom code to use Polly’s library with HttpClient can be significantly complex.</span></span> <span data-ttu-id="62813-109">Na versão original do eShopOnContainers, havia um [bloco de construção ResilientHttpClient](https://github.com/dotnet-architecture/eShopOnContainers/commit/0c317d56f3c8937f6823cf1b45f5683397274815#diff-e6532e623eb606a0f8568663403e3a10) com base na Polly.</span><span class="sxs-lookup"><span data-stu-id="62813-109">In the original version of eShopOnContainers, there was a [ResilientHttpClient building-block](https://github.com/dotnet-architecture/eShopOnContainers/commit/0c317d56f3c8937f6823cf1b45f5683397274815#diff-e6532e623eb606a0f8568663403e3a10) based on Polly.</span></span> <span data-ttu-id="62813-110">Mas, com o lançamento do [HttpClientFactory](use-httpclientfactory-to-implement-resilient-http-requests.md), a implementação da comunicação http resiliente com o Polly tornou-se muito mais simples, de modo que o bloco de construção foi preterido do eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="62813-110">But with the release of [HttpClientFactory](use-httpclientfactory-to-implement-resilient-http-requests.md), implementing resilient HTTP communication with Polly has become much simpler, so that building-block was deprecated from eShopOnContainers.</span></span>

<span data-ttu-id="62813-111">As etapas a seguir mostram como você pode usar repetições de HTTP com a Polly integrada ao HttpClientFactory, que foi explicado na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="62813-111">The following steps show how you can use Http retries with Polly integrated into HttpClientFactory, which is explained in the previous section.</span></span>

<span data-ttu-id="62813-112">**Referenciar os pacotes do ASP.NET Core 2.2**</span><span class="sxs-lookup"><span data-stu-id="62813-112">**Reference the ASP.NET Core 2.2 packages**</span></span>

<span data-ttu-id="62813-113">O `HttpClientFactory` está disponível no .NET Core 2.1 em diante. No entanto, é recomendável que você use os últimos pacotes do ASP.NET Core 2.2 do NuGet em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="62813-113">`HttpClientFactory` is available since .NET Core 2.1 however we recommend you to use the latest ASP.NET Core 2.2 packages from NuGet in your project.</span></span> <span data-ttu-id="62813-114">Normalmente, o metapacote `AspNetCore` e o pacote de extensão `Microsoft.Extensions.Http.Polly` são necessários.</span><span class="sxs-lookup"><span data-stu-id="62813-114">You typically need the `AspNetCore` metapackage, and the extension package `Microsoft.Extensions.Http.Polly`.</span></span>

<span data-ttu-id="62813-115">**Configurar um cliente com a política de repetição da Polly, na inicialização**</span><span class="sxs-lookup"><span data-stu-id="62813-115">**Configure a client with Polly’s Retry policy, in Startup**</span></span>

<span data-ttu-id="62813-116">Conforme mostrado nas seções anteriores, você precisa definir uma configuração cliente do HttpClient nomeada ou tipada no método padrão Startup.ConfigureServices(...), mas agora, adicione o código incremental especificando a política para as repetições de HTTP com retirada exponencial, como é mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="62813-116">As shown in previous sections, you need to define a named or typed client HttpClient configuration in your standard Startup.ConfigureServices(...) method, but now, you add incremental code specifying the policy for the Http retries with exponential backoff, as below:</span></span>

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

<span data-ttu-id="62813-117">O método **AddPolicyHandler()** é aquele que adiciona políticas aos objetos `HttpClient` que você usará.</span><span class="sxs-lookup"><span data-stu-id="62813-117">The **AddPolicyHandler()** method is what adds policies to the `HttpClient` objects you'll use.</span></span> <span data-ttu-id="62813-118">Nesse caso, ele está adicionando a política da Polly para repetições de HTTP com retirada exponencial.</span><span class="sxs-lookup"><span data-stu-id="62813-118">In this case, it's adding a Polly’s policy for Http Retries with exponential backoff.</span></span>

<span data-ttu-id="62813-119">Para obter uma abordagem mais modular, a política de repetição de HTTP pode ser definida em um método separado no arquivo `Startup.cs`, como mostra o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="62813-119">To have a more modular approach, the Http Retry Policy can be defined in a separate method within the `Startup.cs` file, as shown in the following code:</span></span>

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

<span data-ttu-id="62813-120">Com a Polly, você pode definir uma política de repetição com o número de repetições, a configuração de retirada exponencial e as ações a serem executadas quando houver uma exceção de HTTP, como registrar o erro em log.</span><span class="sxs-lookup"><span data-stu-id="62813-120">With Polly, you can define a Retry policy with the number of retries, the exponential backoff configuration, and the actions to take when there's an HTTP exception, such as logging the error.</span></span> <span data-ttu-id="62813-121">Nesse caso, a política é configurada para tentar seis vezes com uma repetição exponencial, começando em dois segundos.</span><span class="sxs-lookup"><span data-stu-id="62813-121">In this case, the policy is configured to try six times with an exponential retry, starting at two seconds.</span></span>

## <a name="add-a-jitter-strategy-to-the-retry-policy"></a><span data-ttu-id="62813-122">Adicionar uma estratégia de tremulação à política de repetição</span><span class="sxs-lookup"><span data-stu-id="62813-122">Add a jitter strategy to the retry policy</span></span>

<span data-ttu-id="62813-123">Uma política de Repetição regular pode afetar o sistema em casos de alta simultaneidade e escalabilidade e sob alta contenção.</span><span class="sxs-lookup"><span data-stu-id="62813-123">A regular Retry policy can impact your system in cases of high concurrency and scalability and under high contention.</span></span> <span data-ttu-id="62813-124">Para superar os picos de novas tentativas semelhantes provenientes de muitos clientes em caso de interrupções parciais, uma boa solução alternativa é adicionar uma estratégia de variação à política/ao algoritmo de novas tentativas.</span><span class="sxs-lookup"><span data-stu-id="62813-124">To overcome peaks of similar retries coming from many clients in case of partial outages, a good workaround is to add a jitter strategy to the retry algorithm/policy.</span></span> <span data-ttu-id="62813-125">Isso pode melhorar o desempenho geral do sistema de ponta a ponta, adicionando aleatoriedade à retirada exponencial.</span><span class="sxs-lookup"><span data-stu-id="62813-125">This can improve the overall performance of the end-to-end system by adding randomness to the exponential backoff.</span></span> <span data-ttu-id="62813-126">Isso espalha os picos quando surgem problemas.</span><span class="sxs-lookup"><span data-stu-id="62813-126">This spreads out the spikes when issues arise.</span></span> <span data-ttu-id="62813-127">O princípio é ilustrado pelo exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="62813-127">The principle is illustrated by the following example:</span></span>

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

<span data-ttu-id="62813-128">O Polly fornece algoritmos de tremulação prontos para produção por meio do site do projeto.</span><span class="sxs-lookup"><span data-stu-id="62813-128">Polly provides production-ready jitter algorithms via the project website.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="62813-129">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="62813-129">Additional resources</span></span>

- <span data-ttu-id="62813-130">**Padrão de repetição**</span><span class="sxs-lookup"><span data-stu-id="62813-130">**Retry pattern**</span></span>  
  [https://docs.microsoft.com/azure/architecture/patterns/retry](/azure/architecture/patterns/retry)

- <span data-ttu-id="62813-131">**Polly e HttpClientFactory**</span><span class="sxs-lookup"><span data-stu-id="62813-131">**Polly and HttpClientFactory**</span></span>  
  <https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory>

- <span data-ttu-id="62813-132">**Polly (biblioteca de tratamento de falhas transitórias e resiliência do .NET)**</span><span class="sxs-lookup"><span data-stu-id="62813-132">**Polly (.NET resilience and transient-fault-handling library)**</span></span>  
  <https://github.com/App-vNext/Polly>

- <span data-ttu-id="62813-133">**Polly: repetir com tremulação**</span><span class="sxs-lookup"><span data-stu-id="62813-133">**Polly: Retry with Jitter**</span></span>  
  <https://github.com/App-vNext/Polly/wiki/Retry-with-jitter>

- <span data-ttu-id="62813-134">**Marc Brooker. Tremulação: tornando as coisas melhores com aleatoriedade**</span><span class="sxs-lookup"><span data-stu-id="62813-134">**Marc Brooker. Jitter: Making Things Better With Randomness**</span></span>  
  <https://brooker.co.za/blog/2015/03/21/backoff.html>

>[!div class="step-by-step"]
><span data-ttu-id="62813-135">[Anterior](explore-custom-http-call-retries-exponential-backoff.md)
>[Próximo](implement-circuit-breaker-pattern.md)</span><span class="sxs-lookup"><span data-stu-id="62813-135">[Previous](explore-custom-http-call-retries-exponential-backoff.md)
[Next](implement-circuit-breaker-pattern.md)</span></span>
