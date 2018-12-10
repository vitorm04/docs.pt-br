---
title: Implementar repetições de chamadas HTTP com retirada exponencial com a Polly
description: Saiba como lidar com falhas de HTTP com a Polly e o HttpClientFactory
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/10/2018
ms.openlocfilehash: 78de1440721e83459e455f5c31d10e52a1d3b1b6
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143981"
---
# <a name="implement-http-call-retries-with-exponential-backoff-with-httpclientfactory-and-polly-policies"></a><span data-ttu-id="ae266-103">Implementar repetições de chamadas HTTP com retirada exponencial com o HttpClientFactory e políticas da Polly</span><span class="sxs-lookup"><span data-stu-id="ae266-103">Implement HTTP call retries with exponential backoff with HttpClientFactory and Polly policies</span></span>

<span data-ttu-id="ae266-104">A abordagem recomendada para repetições com retirada exponencial é aproveitar as bibliotecas do .NET mais avançadas como a [biblioteca Polly](https://github.com/App-vNext/Polly) de software livre.</span><span class="sxs-lookup"><span data-stu-id="ae266-104">The recommended approach for retries with exponential backoff is to take advantage of more advanced .NET libraries like the open-source [Polly library](https://github.com/App-vNext/Polly).</span></span>

<span data-ttu-id="ae266-105">A Polly é uma biblioteca .NET que fornece resiliência e recursos de tratamento de falhas temporárias.</span><span class="sxs-lookup"><span data-stu-id="ae266-105">Polly is a .NET library that provides resilience and transient-fault handling capabilities.</span></span> <span data-ttu-id="ae266-106">Você pode implementar essas funcionalidades por meio da aplicação de políticas da Polly como repetição, disjuntor, isolamento do bulkhead, tempo limite e fallback.</span><span class="sxs-lookup"><span data-stu-id="ae266-106">You can implement those capabilities by applying Polly policies such as Retry, Circuit Breaker, Bulkhead Isolation, Timeout, and Fallback.</span></span> <span data-ttu-id="ae266-107">A Polly é direcionada ao .NET 4.x e ao .NET Standard Library 1.0 (compatível com o .NET Core).</span><span class="sxs-lookup"><span data-stu-id="ae266-107">Polly targets .NET 4.x and the .NET Standard Library 1.0 (which supports .NET Core).</span></span>

<span data-ttu-id="ae266-108">No entanto, pode ser muito complexo usar a biblioteca Polly com seu próprio código personalizado com o HttpClient.</span><span class="sxs-lookup"><span data-stu-id="ae266-108">However, using Polly’s library with your own custom code with HttpClient can be significantly complex.</span></span> <span data-ttu-id="ae266-109">Na versão original do eShopOnContainers, havia um [bloco de construção ResilientHttpClient](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/Resilience/Resilience.Http/ResilientHttpClient.cs) com base na Polly.</span><span class="sxs-lookup"><span data-stu-id="ae266-109">In the original version of eShopOnContainers, there was a [ResilientHttpClient building-block](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/Resilience/Resilience.Http/ResilientHttpClient.cs) based on Polly.</span></span> <span data-ttu-id="ae266-110">Mas, com o lançamento do HttpClientFactory, a comunicação HTTP resiliente ficou muito mais simples de ser implementada, portanto, o bloco de construção foi preterido do eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="ae266-110">But with the release of HttpClientFactory, resilient Http communication has become much simpler to implement, so that building-block was deprecated from eShopOnContainers.</span></span> 

<span data-ttu-id="ae266-111">As etapas a seguir mostram como você pode usar repetições de HTTP com a Polly integrada ao HttpClientFactory, que foi explicado na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="ae266-111">The following steps show how you can use Http retries with Polly integrated into HttpClientFactory, which is explained in the previous section.</span></span>

<span data-ttu-id="ae266-112">**Referenciar os pacotes do ASP.NET Core 2.1**</span><span class="sxs-lookup"><span data-stu-id="ae266-112">**Reference the ASP.NET Core 2.1 packages**</span></span>

<span data-ttu-id="ae266-113">Seu projeto precisa estar usando os pacotes NuGet do ASP.NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="ae266-113">Your project has to be using the ASP.NET Core 2.1 packages from NuGet.</span></span> <span data-ttu-id="ae266-114">Normalmente, o metapacote `AspNetCore` e o pacote de extensão `Microsoft.Extensions.Http.Polly` são necessários.</span><span class="sxs-lookup"><span data-stu-id="ae266-114">You typically need the `AspNetCore` metapackage, and the extension package `Microsoft.Extensions.Http.Polly`.</span></span>

<span data-ttu-id="ae266-115">**Configurar um cliente com a política de repetição da Polly, na inicialização**</span><span class="sxs-lookup"><span data-stu-id="ae266-115">**Configure a client with Polly’s Retry policy, in Startup**</span></span>

<span data-ttu-id="ae266-116">Conforme mostrado nas seções anteriores, você precisa definir uma configuração cliente do HttpClient nomeada ou tipada no método padrão Startup.ConfigureServices(...), mas agora, adicione o código incremental especificando a política para as repetições de HTTP com retirada exponencial, como é mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="ae266-116">As shown in previous sections, you need to define a named or typed client HttpClient configuration in your standard Startup.ConfigureServices(...) method, but now, you add incremental code specifying the policy for the Http retries with exponential backoff, as below:</span></span>

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

<span data-ttu-id="ae266-117">O método **AddPolicyHandler()** é o que adiciona políticas aos objetos `HttpClient` que você usará.</span><span class="sxs-lookup"><span data-stu-id="ae266-117">The **AddPolicyHandler()** method is what adds policies to the `HttpClient` objects you will use.</span></span> <span data-ttu-id="ae266-118">Nesse caso, ele está adicionando a política da Polly para repetições de HTTP com retirada exponencial.</span><span class="sxs-lookup"><span data-stu-id="ae266-118">In this case, it is adding a Polly’s policy for Http Retries with exponential backoff.</span></span>

<span data-ttu-id="ae266-119">Para obter uma abordagem mais modular, a política de repetição de HTTP pode ser definida em um método separado dentro do método ConfigureServices(), como o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="ae266-119">In order to have a more modular approach, the Http Retry Policy can be defined in a separate method within the ConfigureServices() method, as the following code.</span></span>

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

<span data-ttu-id="ae266-120">Com a Polly, é possível definir uma política de repetição com o número de repetições, a configuração de retirada exponencial e as ações a serem executadas quando há uma exceção de HTTP, como registrar o erro em log.</span><span class="sxs-lookup"><span data-stu-id="ae266-120">With Polly, you can define a Retry policy with the number of retries, the exponential backoff configuration, and the actions to take when there is an HTTP exception, such as logging the error.</span></span> <span data-ttu-id="ae266-121">Nesse caso, a política é configurada para tentar seis vezes com uma repetição exponencial, começando em dois segundos.</span><span class="sxs-lookup"><span data-stu-id="ae266-121">In this case, the policy is configured to try six times with an exponential retry, starting at two seconds.</span></span> 

<span data-ttu-id="ae266-122">Portanto, ela tentará seis vezes e os segundos entre cada repetição serão exponenciais, começando em dois segundos.</span><span class="sxs-lookup"><span data-stu-id="ae266-122">so it will try six times and the seconds between each retry will be exponential, starting on two seconds.</span></span>

### <a name="adding-a-jitter-strategy-to-the-retry-policy"></a><span data-ttu-id="ae266-123">Adicionando uma estratégia de tremulação à política de repetição</span><span class="sxs-lookup"><span data-stu-id="ae266-123">Adding a jitter strategy to the retry policy</span></span>

<span data-ttu-id="ae266-124">Uma política de Repetição regular pode afetar o sistema em casos de alta simultaneidade e escalabilidade e sob alta contenção.</span><span class="sxs-lookup"><span data-stu-id="ae266-124">A regular Retry policy can impact your system in cases of high concurrency and scalability and under high contention.</span></span> <span data-ttu-id="ae266-125">Para superar os picos de novas tentativas semelhantes provenientes de muitos clientes em caso de interrupções parciais, uma boa solução alternativa é adicionar uma estratégia de variação à política/ao algoritmo de novas tentativas.</span><span class="sxs-lookup"><span data-stu-id="ae266-125">To overcome peaks of similar retries coming from many clients in case of partial outages, a good workaround is to add a jitter strategy to the retry algorithm/policy.</span></span> <span data-ttu-id="ae266-126">Isso pode melhorar o desempenho geral do sistema de ponta a ponta, adicionando aleatoriedade à retirada exponencial.</span><span class="sxs-lookup"><span data-stu-id="ae266-126">This can improve the overall performance of the end-to-end system by adding randomness to the exponential backoff.</span></span> <span data-ttu-id="ae266-127">Isso espalha os picos quando surgem problemas.</span><span class="sxs-lookup"><span data-stu-id="ae266-127">This spreads out the spikes when issues arise.</span></span> <span data-ttu-id="ae266-128">Quando você usa uma política da Polly simples, o código para implementar a variação pode ser semelhante ao seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="ae266-128">When you use a plain Polly policy, code to implement jitter could look like the following example:</span></span>

```csharp
Random jitterer = new Random(); 
Policy
  .Handle<HttpResponseException>() // etc
  .WaitAndRetry(5,    // exponential back-off plus some jitter
      retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))  
                    + TimeSpan.FromMilliseconds(jitterer.Next(0, 100)) 
  );
```

## <a name="additional-resources"></a><span data-ttu-id="ae266-129">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="ae266-129">Additional resources</span></span>

-   <span data-ttu-id="ae266-130">**Padrão de repetição**
    [*https://docs.microsoft.com/azure/architecture/patterns/retry*](https://docs.microsoft.com/azure/architecture/patterns/retry)</span><span class="sxs-lookup"><span data-stu-id="ae266-130">**Retry pattern**
[*https://docs.microsoft.com/azure/architecture/patterns/retry*](https://docs.microsoft.com/azure/architecture/patterns/retry)</span></span>

-   <span data-ttu-id="ae266-131">**Polly e HttpClientFactory**
    [*https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory*](https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory)</span><span class="sxs-lookup"><span data-stu-id="ae266-131">**Polly and HttpClientFactory**
[*https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory*](https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory)</span></span>

-   <span data-ttu-id="ae266-132">**Polly (biblioteca de tratamento de falhas transitórias e resiliência do .NET)**</span><span class="sxs-lookup"><span data-stu-id="ae266-132">**Polly (.NET resilience and transient-fault-handling library)**</span></span>

    [*https://github.com/App-vNext/Polly*](https://github.com/App-vNext/Polly)

-   <span data-ttu-id="ae266-133">**Marc Brooker. Jitter: Making Things Better With Randomness** (Variação: melhorando as coisas com aleatoriedade)</span><span class="sxs-lookup"><span data-stu-id="ae266-133">**Marc Brooker. Jitter: Making Things Better With Randomness**</span></span>

    [*https://brooker.co.za/blog/2015/03/21/backoff.html*](https://brooker.co.za/blog/2015/03/21/backoff.html)

>[!div class="step-by-step"]
><span data-ttu-id="ae266-134">[Anterior](explore-custom-http-call-retries-exponential-backoff.md)
>[Próximo](implement-circuit-breaker-pattern.md)</span><span class="sxs-lookup"><span data-stu-id="ae266-134">[Previous](explore-custom-http-call-retries-exponential-backoff.md)
[Next](implement-circuit-breaker-pattern.md)</span></span>