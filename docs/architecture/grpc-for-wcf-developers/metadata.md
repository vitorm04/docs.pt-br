---
title: Metadata-gRPC para desenvolvedores do WCF
description: Como os metadados são usados no gRPC para passar o contexto adicional entre clientes e servidores
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 1a2131fa3ee3112eaa3c3e7f7c97017fea6b1004
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184326"
---
# <a name="metadata"></a>Metadados

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

"Metadados" refere-se a dados adicionais que podem ser úteis durante o processamento de solicitações e respostas, mas que não fazem parte dos dados reais do aplicativo. Os metadados podem incluir tokens de autenticação, identificadores de solicitação e marcas para fins de monitoramento ou informações sobre os dados, como o número de registros em um DataSet.

É possível adicionar cabeçalhos de chave/valor genéricos a mensagens do WCF usando uma <xref:System.ServiceModel.OperationContextScope> e a <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders?displayProperty=nameWithType> Propriedade e tratá-los usando <xref:System.ServiceModel.Channels.MessageProperties>.

chamadas e respostas gRPC também podem incluir metadados semelhantes aos cabeçalhos HTTP. Eles são praticamente invisíveis para se gRPC e são passados para serem processados pelo seu código de aplicativo ou middleware. Os metadados são representados como pares de chave/valor em que a chave é uma cadeia de caracteres e o valor é uma cadeia de caracteres ou dados binários. Você não precisa especificar metadados no `.proto` arquivo.

Os metadados são tratados usando `Metadata` a classe do pacote NuGet [Grpc. Core](https://www.nuget.org/packages/Grpc.Core/) . Essa classe pode ser usada com a sintaxe do inicializador de coleção.

O exemplo a seguir mostra como adicionar metadados a uma chamada de um C# cliente:

```csharp
var metadata = new Metadata
{
    { "Requester", _clientName }
};

var request = new GetPortfolioRequest
{
    Id = portfolioId
};

var response = await client.GetPortfolioAsync(request, metadata);
```

os `ServerCallContext` serviços gRPCs podem acessar metadados da propriedade `RequestHeaders` do argumento:

```csharp
public async Task<GetPortfolioResponse> GetPortfolio(GetPortfolioRequest request, ServerCallContext context)
{
    var requesterHeader = context.RequestHeaders.FirstOrDefault(e => e.Key == "Requester");
    if (requesterHeader != null)
    {
        _logger.LogInformation($"Request from {requesterHeader.Value}");
    }
    // ...
}
```

Os serviços podem enviar metadados para clientes usando `ResponseTrailers` a propriedade `ServerCallContext`de:

```csharp
public async Task<GetPortfolioResponse> GetPortfolio(GetPortfolioRequest request, ServerCallContext context)
{
    // ...
    context.ResponseTrailers.Add("Responder", _serverName);
    // ...
}
```

>[!div class="step-by-step"]
>[Anterior](rpc-types.md)
>[Próximo](error-handling.md)
