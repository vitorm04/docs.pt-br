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
# <a name="metadata"></a><span data-ttu-id="5f8a2-103">Metadados</span><span class="sxs-lookup"><span data-stu-id="5f8a2-103">Metadata</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="5f8a2-104">"Metadados" refere-se a dados adicionais que podem ser úteis durante o processamento de solicitações e respostas, mas que não fazem parte dos dados reais do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5f8a2-104">"Metadata" refers to additional data that may be useful while processing requests and responses but is not part of the actual application data.</span></span> <span data-ttu-id="5f8a2-105">Os metadados podem incluir tokens de autenticação, identificadores de solicitação e marcas para fins de monitoramento ou informações sobre os dados, como o número de registros em um DataSet.</span><span class="sxs-lookup"><span data-stu-id="5f8a2-105">Metadata might include authentication tokens, request identifiers and tags for monitoring purposes, or information about the data like the number of records in a dataset.</span></span>

<span data-ttu-id="5f8a2-106">É possível adicionar cabeçalhos de chave/valor genéricos a mensagens do WCF usando uma <xref:System.ServiceModel.OperationContextScope> e a <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders?displayProperty=nameWithType> Propriedade e tratá-los usando <xref:System.ServiceModel.Channels.MessageProperties>.</span><span class="sxs-lookup"><span data-stu-id="5f8a2-106">It's possible to add generic key/value headers to WCF messages using an <xref:System.ServiceModel.OperationContextScope> and the <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders?displayProperty=nameWithType> property, and handle them using <xref:System.ServiceModel.Channels.MessageProperties>.</span></span>

<span data-ttu-id="5f8a2-107">chamadas e respostas gRPC também podem incluir metadados semelhantes aos cabeçalhos HTTP.</span><span class="sxs-lookup"><span data-stu-id="5f8a2-107">gRPC calls and responses can also include metadata similar to HTTP headers.</span></span> <span data-ttu-id="5f8a2-108">Eles são praticamente invisíveis para se gRPC e são passados para serem processados pelo seu código de aplicativo ou middleware.</span><span class="sxs-lookup"><span data-stu-id="5f8a2-108">These are mostly invisible to gRPC itself and are passed through to be processed by your application code or middleware.</span></span> <span data-ttu-id="5f8a2-109">Os metadados são representados como pares de chave/valor em que a chave é uma cadeia de caracteres e o valor é uma cadeia de caracteres ou dados binários.</span><span class="sxs-lookup"><span data-stu-id="5f8a2-109">Metadata is represented as key/value pairs where the key is a string and the value is either a string or binary data.</span></span> <span data-ttu-id="5f8a2-110">Você não precisa especificar metadados no `.proto` arquivo.</span><span class="sxs-lookup"><span data-stu-id="5f8a2-110">You don’t need to specify metadata in the `.proto` file.</span></span>

<span data-ttu-id="5f8a2-111">Os metadados são tratados usando `Metadata` a classe do pacote NuGet [Grpc. Core](https://www.nuget.org/packages/Grpc.Core/) .</span><span class="sxs-lookup"><span data-stu-id="5f8a2-111">Metadata is handled using the `Metadata` class from the [Grpc.Core](https://www.nuget.org/packages/Grpc.Core/) NuGet package.</span></span> <span data-ttu-id="5f8a2-112">Essa classe pode ser usada com a sintaxe do inicializador de coleção.</span><span class="sxs-lookup"><span data-stu-id="5f8a2-112">This class can be used with collection initializer syntax.</span></span>

<span data-ttu-id="5f8a2-113">O exemplo a seguir mostra como adicionar metadados a uma chamada de um C# cliente:</span><span class="sxs-lookup"><span data-stu-id="5f8a2-113">The following example shows how to add metadata to a call from a C# client:</span></span>

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

<span data-ttu-id="5f8a2-114">os `ServerCallContext` serviços gRPCs podem acessar metadados da propriedade `RequestHeaders` do argumento:</span><span class="sxs-lookup"><span data-stu-id="5f8a2-114">gRPC services can access metadata from the `ServerCallContext` argument's `RequestHeaders` property:</span></span>

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

<span data-ttu-id="5f8a2-115">Os serviços podem enviar metadados para clientes usando `ResponseTrailers` a propriedade `ServerCallContext`de:</span><span class="sxs-lookup"><span data-stu-id="5f8a2-115">Services can send metadata to clients using the `ResponseTrailers` property of `ServerCallContext`:</span></span>

```csharp
public async Task<GetPortfolioResponse> GetPortfolio(GetPortfolioRequest request, ServerCallContext context)
{
    // ...
    context.ResponseTrailers.Add("Responder", _serverName);
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="5f8a2-116">[Anterior](rpc-types.md)
>[Próximo](error-handling.md)</span><span class="sxs-lookup"><span data-stu-id="5f8a2-116">[Previous](rpc-types.md)
[Next](error-handling.md)</span></span>
