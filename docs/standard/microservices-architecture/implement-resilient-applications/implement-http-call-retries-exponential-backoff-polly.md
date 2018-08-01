---
title: Implementar repetições de chamadas HTTP com retirada exponencial com a Polly
description: Saiba como lidar com falhas de HTTP com a Polly e o HttpClientFactory
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/10/2018
ms.openlocfilehash: c16f4c0f2ef09f346c8b46ff8089883cedcf0c7e
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874891"
---
# <a name="implement-http-call-retries-with-exponential-backoff-with-httpclientfactory-and-polly-policies"></a>Implementar repetições de chamadas HTTP com retirada exponencial com o HttpClientFactory e políticas da Polly

A abordagem recomendada para repetições com retirada exponencial é aproveitar as bibliotecas do .NET mais avançadas como a [biblioteca Polly](https://github.com/App-vNext/Polly) de software livre.

A Polly é uma biblioteca .NET que fornece resiliência e recursos de tratamento de falhas temporárias. Você pode implementar essas funcionalidades por meio da aplicação de políticas da Polly como repetição, disjuntor, isolamento do bulkhead, tempo limite e fallback. A Polly é direcionada ao .NET 4.x e ao .NET Standard Library 1.0 (compatível com o .NET Core).

No entanto, pode ser muito complexo usar a biblioteca Polly com seu próprio código personalizado com o HttpClient. Na versão original do eShopOnContainers, havia um [bloco de construção ResilientHttpClient](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/Resilience/Resilience.Http/ResilientHttpClient.cs) com base na Polly. Mas, com o lançamento do HttpClientFactory, a comunicação HTTP resiliente ficou muito mais simples de ser implementada, portanto, o bloco de construção foi preterido do eShopOnContainers. 

As etapas a seguir mostram como você pode usar repetições de HTTP com a Polly integrada ao HttpClientFactory, que foi explicado na seção anterior.

**Referenciar os pacotes do ASP.NET Core 2.1**

Seu projeto precisa estar usando os pacotes NuGet do ASP.NET Core 2.1. Normalmente, o metapacote `AspNetCore` e o pacote de extensão `Microsoft.Extensions.Http.Polly` são necessários.

**Configurar um cliente com a política de repetição da Polly, na inicialização**

Conforme mostrado nas seções anteriores, você precisa definir uma configuração cliente do HttpClient nomeada ou tipada no método padrão Startup.ConfigureServices(...), mas agora, adicione o código incremental especificando a política para as repetições de HTTP com retirada exponencial, como é mostrado abaixo:

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

O método **AddPolicyHandler()** é o que adiciona políticas aos objetos `HttpClient` que você usará. Nesse caso, ele está adicionando a política da Polly para repetições de HTTP com retirada exponencial.

Para obter uma abordagem mais modular, a política de repetição de HTTP pode ser definida em um método separado dentro do método ConfigureServices(), como o código a seguir.

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

Com a Polly, é possível definir uma política de repetição com o número de repetições, a configuração de retirada exponencial e as ações a serem executadas quando há uma exceção de HTTP, como registrar o erro em log. Nesse caso, a política é configurada para tentar seis vezes com uma repetição exponencial, começando em dois segundos. 

Portanto, ela tentará seis vezes e os segundos entre cada repetição serão exponenciais, começando em dois segundos.

### <a name="adding-a-jitter-strategy-to-the-retry-policy"></a>Adicionando uma estratégia de tremulação à política de repetição

Uma política de Repetição regular pode afetar o sistema em casos de alta simultaneidade e escalabilidade e sob alta contenção. Para superar os picos de novas tentativas semelhantes provenientes de muitos clientes em caso de interrupções parciais, uma boa solução alternativa é adicionar uma estratégia de variação à política/ao algoritmo de novas tentativas. Isso pode melhorar o desempenho geral do sistema de ponta a ponta, adicionando aleatoriedade à retirada exponencial. Isso espalha os picos quando surgem problemas. Quando você usa uma política da Polly simples, o código para implementar a variação pode ser semelhante ao seguinte exemplo:

```csharp
Random jitterer = new Random(); 
Policy
  .Handle<HttpResponseException>() // etc
  .WaitAndRetry(5,    // exponential back-off plus some jitter
      retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))  
                    + TimeSpan.FromMilliseconds(jitterer.Next(0, 100)) 
  );
```

## <a name="additional-resources"></a>Recursos adicionais

-   **Padrão de repetição**
    [*https://docs.microsoft.com/azure/architecture/patterns/retry*](https://docs.microsoft.com/azure/architecture/patterns/retry)

-   **Polly e HttpClientFactory**
    [*https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory*](https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory)

-   **Polly (biblioteca de tratamento de falhas transitórias e resiliência do .NET)**

    [*https://github.com/App-vNext/Polly*](https://github.com/App-vNext/Polly)

-   **Marc Brooker. Jitter: Making Things Better With Randomness** (Variação: melhorando as coisas com aleatoriedade)

    [*https://brooker.co.za/blog/2015/03/21/backoff.html*](https://brooker.co.za/blog/2015/03/21/backoff.html)



>[!div class="step-by-step"]
[Anterior](explore-custom-http-call-retries-exponential-backoff.md)
[Próximo](implement-circuit-breaker-pattern.md)
