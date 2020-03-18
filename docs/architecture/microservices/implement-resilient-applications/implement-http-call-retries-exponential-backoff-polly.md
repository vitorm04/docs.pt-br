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
# <a name="implement-http-call-retries-with-exponential-backoff-with-ihttpclientfactory-and-polly-policies"></a>Implementar tentativas de chamada HTTP com backoff exponencial com políticas IHttpClientFactory e Polly

A abordagem recomendada para repetições com retirada exponencial é aproveitar as bibliotecas do .NET mais avançadas como a [biblioteca Polly](https://github.com/App-vNext/Polly) de software livre.

A Polly é uma biblioteca .NET que fornece resiliência e recursos de tratamento de falhas temporárias. Você pode implementar essas funcionalidades por meio da aplicação de políticas da Polly como repetição, disjuntor, isolamento do bulkhead, tempo limite e fallback. O Polly tem como alvo o .NET Framework 4.x e o .NET Standard 1.0, 1.1 e 2.0 (que suporta o .NET Core).

As etapas a seguir mostram como você `IHttpClientFactory`pode usar as repetições http com polly integrada, o que é explicado na seção anterior.

**Referenciar os pacotes ASP.NET Core 3.1**

`IHttpClientFactory`está disponível desde .NET Core 2.1 no entanto recomendamos que você use os pacotes mais recentes ASP.NET Core 3.1 do NuGet em seu projeto. Você normalmente também precisa fazer `Microsoft.Extensions.Http.Polly`referência ao pacote de extensão .

**Configure um cliente com a política de Repetição da Polly, em Inicialização**

Conforme mostrado nas seções anteriores, você precisa definir uma configuração cliente do HttpClient nomeada ou tipada no método padrão Startup.ConfigureServices(...), mas agora, adicione o código incremental especificando a política para as repetições de HTTP com retirada exponencial, como é mostrado abaixo:

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

O método **AddPolicyHandler()** é aquele que adiciona políticas aos objetos `HttpClient` que você usará. Neste caso, está adicionando uma política da Polly para Http Retries com recuo exponencial.

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

## <a name="add-a-jitter-strategy-to-the-retry-policy"></a>Adicionar uma estratégia de tremulação à política de repetição

Uma política de Repetição regular pode afetar o sistema em casos de alta simultaneidade e escalabilidade e sob alta contenção. Para superar os picos de novas tentativas semelhantes provenientes de muitos clientes em caso de interrupções parciais, uma boa solução alternativa é adicionar uma estratégia de variação à política/ao algoritmo de novas tentativas. Isso pode melhorar o desempenho geral do sistema de ponta a ponta, adicionando aleatoriedade à retirada exponencial. Isso espalha os picos quando surgem problemas. O princípio é ilustrado pelo seguinte exemplo:

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

Polly fornece algoritmos de jitter prontos para a produção através do site do projeto.

## <a name="additional-resources"></a>Recursos adicionais

- **Padrão de repetição**  
  [https://docs.microsoft.com/azure/architecture/patterns/retry](/azure/architecture/patterns/retry)

- **Polly e IHttpClientFactory**  
  <https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory>

- **Polly (biblioteca de tratamento de falhas transitórias e resiliência do .NET)**  
  <https://github.com/App-vNext/Polly>

- **Polly: Tente com jitter**  
  <https://github.com/App-vNext/Polly/wiki/Retry-with-jitter>

- **Marc Brooker. Jitter: Tornando as coisas melhores com a leatoriedade**  
  <https://brooker.co.za/blog/2015/03/21/backoff.html>

>[!div class="step-by-step"]
>[Próximo](use-httpclientfactory-to-implement-resilient-http-requests.md)
>[anterior](implement-circuit-breaker-pattern.md)
