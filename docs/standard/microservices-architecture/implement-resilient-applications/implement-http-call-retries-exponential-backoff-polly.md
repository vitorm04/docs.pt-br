---
title: Implementar repetições de chamadas HTTP com retirada exponencial com a Polly
description: Saiba como tratar falhas de HTTP com a Polly e o HttpClientFactory.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: d031ca9b7c46f02cd9e22ae91fb20f281ebb47a2
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59612050"
---
# <a name="implement-http-call-retries-with-exponential-backoff-with-httpclientfactory-and-polly-policies"></a>Implementar repetições de chamadas HTTP com retirada exponencial com o HttpClientFactory e políticas da Polly

A abordagem recomendada para repetições com retirada exponencial é aproveitar as bibliotecas do .NET mais avançadas como a [biblioteca Polly](https://github.com/App-vNext/Polly) de software livre.

A Polly é uma biblioteca .NET que fornece resiliência e recursos de tratamento de falhas temporárias. Você pode implementar essas funcionalidades por meio da aplicação de políticas da Polly como repetição, disjuntor, isolamento do bulkhead, tempo limite e fallback. A Polly é direcionada ao .NET 4.x e ao .NET Standard Library 1.0 (compatível com o .NET Core).

No entanto, pode ser muito complexo usar a biblioteca Polly com seu próprio código personalizado com o HttpClient. Na versão original do eShopOnContainers, havia um [bloco de construção ResilientHttpClient](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/Resilience/Resilience.Http/ResilientHttpClient.cs) com base na Polly. Mas, com o lançamento do HttpClientFactory, a comunicação HTTP resiliente ficou muito mais simples de ser implementada, portanto, o bloco de construção foi preterido do eShopOnContainers. 

As etapas a seguir mostram como você pode usar repetições de HTTP com a Polly integrada ao HttpClientFactory, que foi explicado na seção anterior.

**Referenciar os pacotes do ASP.NET Core 2.2**

O `HttpClientFactory` está disponível no .NET Core 2.1 em diante. No entanto, é recomendável que você use os últimos pacotes do ASP.NET Core 2.2 do NuGet em seu projeto. Normalmente, o metapacote `AspNetCore` e o pacote de extensão `Microsoft.Extensions.Http.Polly` são necessários.

**Configurar um cliente com a política de repetição da Polly, na inicialização**

Conforme mostrado nas seções anteriores, você precisa definir uma configuração cliente do HttpClient nomeada ou tipada no método padrão Startup.ConfigureServices(...), mas agora, adicione o código incremental especificando a política para as repetições de HTTP com retirada exponencial, como é mostrado abaixo:

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

O método **AddPolicyHandler()** é aquele que adiciona políticas aos objetos `HttpClient` que você usará. Nesse caso, ele está adicionando a política da Polly para repetições de HTTP com retirada exponencial.

Para obter uma abordagem mais modular, a política de repetição de HTTP pode ser definida em um método separado no arquivo `Startup.cs`, como mostra o código a seguir:

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

Com a Polly, você pode definir uma política de repetição com o número de repetições, a configuração de retirada exponencial e as ações a serem executadas quando houver uma exceção de HTTP, como registrar o erro em log. Nesse caso, a política é configurada para tentar seis vezes com uma repetição exponencial, começando em dois segundos. 

Portanto, ela tentará seis vezes e os segundos entre cada repetição serão exponenciais, começando em dois segundos.

## <a name="add-a-jitter-strategy-to-the-retry-policy"></a>Adicionar uma estratégia de tremulação à política de repetição

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

- **Padrão de repetição**\
  [https://docs.microsoft.com/azure/architecture/patterns/retry](/azure/architecture/patterns/retry)

- **Polly e HttpClientFactory**\
  <https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory>

- **Polly (biblioteca de tratamento de falhas transitórias e resiliência do .NET)**\
  <https://github.com/App-vNext/Polly>

- **Marc Brooker. Jitter: Making Things Better With Randomness**\ (Tremulação: melhorando as coisas com aleatoriedade)
  <https://brooker.co.za/blog/2015/03/21/backoff.html>

>[!div class="step-by-step"]
>[Anterior](explore-custom-http-call-retries-exponential-backoff.md)
>[Próximo](implement-circuit-breaker-pattern.md)
