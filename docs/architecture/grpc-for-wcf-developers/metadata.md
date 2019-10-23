---
title: Metadata-gRPC para desenvolvedores do WCF
description: Como os metadados são usados no gRPC para passar o contexto adicional entre clientes e servidores
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 71ac60cd4c389277675dd452430735fb698fd342
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72770486"
---
# <a name="metadata"></a><span data-ttu-id="a5b35-103">Metadados</span><span class="sxs-lookup"><span data-stu-id="a5b35-103">Metadata</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="a5b35-104">"Metadados" refere-se a dados adicionais que podem ser úteis durante o processamento de solicitações e respostas, mas que não fazem parte dos dados reais do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a5b35-104">"Metadata" refers to additional data that may be useful while processing requests and responses but is not part of the actual application data.</span></span> <span data-ttu-id="a5b35-105">Os metadados podem incluir tokens de autenticação, identificadores de solicitação e marcas para fins de monitoramento ou informações sobre os dados, como o número de registros em um DataSet.</span><span class="sxs-lookup"><span data-stu-id="a5b35-105">Metadata might include authentication tokens, request identifiers and tags for monitoring purposes, or information about the data like the number of records in a dataset.</span></span>

<span data-ttu-id="a5b35-106">É possível adicionar cabeçalhos de chave/valor genéricos a mensagens WCF usando um <xref:System.ServiceModel.OperationContextScope> e a propriedade <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders?displayProperty=nameWithType> e tratá-los usando <xref:System.ServiceModel.Channels.MessageProperties>.</span><span class="sxs-lookup"><span data-stu-id="a5b35-106">It's possible to add generic key/value headers to WCF messages using an <xref:System.ServiceModel.OperationContextScope> and the <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders?displayProperty=nameWithType> property, and handle them using <xref:System.ServiceModel.Channels.MessageProperties>.</span></span>

<span data-ttu-id="a5b35-107">chamadas e respostas gRPC também podem incluir metadados semelhantes aos cabeçalhos HTTP.</span><span class="sxs-lookup"><span data-stu-id="a5b35-107">gRPC calls and responses can also include metadata similar to HTTP headers.</span></span> <span data-ttu-id="a5b35-108">Eles são praticamente invisíveis para se gRPC e são passados para serem processados pelo seu código de aplicativo ou middleware.</span><span class="sxs-lookup"><span data-stu-id="a5b35-108">These are mostly invisible to gRPC itself and are passed through to be processed by your application code or middleware.</span></span> <span data-ttu-id="a5b35-109">Os metadados são representados como pares de chave/valor em que a chave é uma cadeia de caracteres e o valor é uma cadeia de caracteres ou dados binários.</span><span class="sxs-lookup"><span data-stu-id="a5b35-109">Metadata is represented as key/value pairs where the key is a string and the value is either a string or binary data.</span></span> <span data-ttu-id="a5b35-110">Você não precisa especificar metadados no arquivo de `.proto`.</span><span class="sxs-lookup"><span data-stu-id="a5b35-110">You don’t need to specify metadata in the `.proto` file.</span></span>

<span data-ttu-id="a5b35-111">Os metadados são tratados usando a classe `Metadata` do pacote NuGet [Grpc. Core. API](https://www.nuget.org/packages/Grpc.Core.Api/) .</span><span class="sxs-lookup"><span data-stu-id="a5b35-111">Metadata is handled using the `Metadata` class from the [Grpc.Core.Api](https://www.nuget.org/packages/Grpc.Core.Api/) NuGet package.</span></span> <span data-ttu-id="a5b35-112">Essa classe pode ser usada com a sintaxe do inicializador de coleção.</span><span class="sxs-lookup"><span data-stu-id="a5b35-112">This class can be used with collection initializer syntax.</span></span>

<span data-ttu-id="a5b35-113">O exemplo a seguir mostra como adicionar metadados a uma chamada de um C# cliente:</span><span class="sxs-lookup"><span data-stu-id="a5b35-113">The following example shows how to add metadata to a call from a C# client:</span></span>

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

<span data-ttu-id="a5b35-114">os serviços gRPCs podem acessar metadados da propriedade `RequestHeaders` do argumento de `ServerCallContext`:</span><span class="sxs-lookup"><span data-stu-id="a5b35-114">gRPC services can access metadata from the `ServerCallContext` argument's `RequestHeaders` property:</span></span>

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

<span data-ttu-id="a5b35-115">Os serviços podem enviar metadados para clientes usando a propriedade `ResponseTrailers` de `ServerCallContext`:</span><span class="sxs-lookup"><span data-stu-id="a5b35-115">Services can send metadata to clients using the `ResponseTrailers` property of `ServerCallContext`:</span></span>

```csharp
public async Task<GetPortfolioResponse> GetPortfolio(GetPortfolioRequest request, ServerCallContext context)
{
    // ...
    context.ResponseTrailers.Add("Responder", _serverName);
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="a5b35-116">[Anterior](rpc-types.md)
>[Próximo](error-handling.md)</span><span class="sxs-lookup"><span data-stu-id="a5b35-116">[Previous](rpc-types.md)
[Next](error-handling.md)</span></span>
