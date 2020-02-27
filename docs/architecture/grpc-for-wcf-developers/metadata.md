---
title: Metadata-gRPC para desenvolvedores do WCF
description: Como os metadados são usados no gRPC para passar o contexto adicional entre clientes e servidores.
ms.date: 09/02/2019
ms.openlocfilehash: 64fa94d1e63af480cbc7363631de161c5b8b8fb8
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628573"
---
# <a name="metadata"></a>Metadados

Os *metadados* referem-se a dados adicionais que podem ser úteis durante o processamento de solicitações e respostas, mas isso não faz parte dos dados reais do aplicativo. Os metadados podem incluir tokens de autenticação, identificadores de solicitação e marcas para fins de monitoramento, além de informações sobre os dados, como o número de registros em um DataSet.

É possível adicionar cabeçalhos de chave/valor genéricos a mensagens Windows Communication Foundation (WCF) usando um <xref:System.ServiceModel.OperationContextScope> e a propriedade <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders?displayProperty=nameWithType> e tratá-los usando <xref:System.ServiceModel.Channels.MessageProperties>.

chamadas e respostas gRPC também podem incluir metadados semelhantes aos cabeçalhos HTTP. Esses metadados são praticamente invisíveis para se gRPC e são passados para serem processados pelo seu código de aplicativo ou middleware. Os metadados são representados como pares de chave/valor, em que a chave é uma cadeia de caracteres e o valor é uma cadeia de caracteres ou dados binários. Você não precisa especificar metadados no arquivo de `.proto`.

Os metadados são tratados pela classe `Metadata` do pacote NuGet [Grpc. Core. API](https://www.nuget.org/packages/Grpc.Core.Api/) . Essa classe pode ser usada com a sintaxe do inicializador de coleção.

Este exemplo mostra como adicionar metadados a uma chamada de um C# cliente:

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

os serviços gRPCs podem acessar metadados da propriedade `RequestHeaders` do argumento de `ServerCallContext`:

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

Os serviços podem enviar metadados para clientes usando a propriedade `ResponseTrailers` de `ServerCallContext`:

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
