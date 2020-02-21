---
title: Tratamento de erro-gRPC para desenvolvedores do WCF
description: Tópicos referentes ao tratamento de erros no gRPC. Inclui uma tabela dos códigos de status mais comumente usados.
ms.date: 09/02/2019
ms.openlocfilehash: c380c651f854adc97e8b2ead36d30c3b83662aac
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542787"
---
# <a name="error-handling"></a><span data-ttu-id="0955e-104">Tratamento de erros</span><span class="sxs-lookup"><span data-stu-id="0955e-104">Error handling</span></span>

<span data-ttu-id="0955e-105">Windows Communication Foundation (WCF) usa <xref:System.ServiceModel.FaultException%601> e [FaultContract](xref:System.ServiceModel.FaultContractAttribute) para fornecer informações de erro detalhadas, incluindo suporte ao padrão de falha SOAP.</span><span class="sxs-lookup"><span data-stu-id="0955e-105">Windows Communication Foundation (WCF) uses <xref:System.ServiceModel.FaultException%601> and [FaultContract](xref:System.ServiceModel.FaultContractAttribute) to provide detailed error information, including supporting the SOAP Fault standard.</span></span>

<span data-ttu-id="0955e-106">Infelizmente, a versão atual do gRPC não tem a sofisticação encontrada com o WCF e só tem tratamento de erro interno limitado com base em códigos de status e metadados simples.</span><span class="sxs-lookup"><span data-stu-id="0955e-106">Unfortunately, the current version of gRPC lacks the sophistication found with WCF, and only has limited built-in error handling based on simple status codes and metadata.</span></span> <span data-ttu-id="0955e-107">A tabela a seguir é um guia rápido para os códigos de status mais usados:</span><span class="sxs-lookup"><span data-stu-id="0955e-107">The following table is a quick guide to the most commonly used status codes:</span></span>

| <span data-ttu-id="0955e-108">Código de status</span><span class="sxs-lookup"><span data-stu-id="0955e-108">Status code</span></span> | <span data-ttu-id="0955e-109">Problema</span><span class="sxs-lookup"><span data-stu-id="0955e-109">Problem</span></span> |
| ----------- | ------- |
| `GRPC_STATUS_UNIMPLEMENTED` | <span data-ttu-id="0955e-110">O método não foi gravado.</span><span class="sxs-lookup"><span data-stu-id="0955e-110">Method hasn’t been written.</span></span> |
| `GRPC_STATUS_UNAVAILABLE` | <span data-ttu-id="0955e-111">Problema com o serviço inteiro.</span><span class="sxs-lookup"><span data-stu-id="0955e-111">Problem with the whole service.</span></span> |
| `GRPC_STATUS_UNKNOWN` | <span data-ttu-id="0955e-112">Resposta inválida.</span><span class="sxs-lookup"><span data-stu-id="0955e-112">Invalid response.</span></span> |
| `GRPC_STATUS_INTERNAL` | <span data-ttu-id="0955e-113">Problema com codificação/decodificação.</span><span class="sxs-lookup"><span data-stu-id="0955e-113">Problem with encoding/decoding.</span></span> |
| `GRPC_STATUS_UNAUTHENTICATED` | <span data-ttu-id="0955e-114">Falha na autenticação.</span><span class="sxs-lookup"><span data-stu-id="0955e-114">Authentication failed.</span></span> |
| `GRPC_STATUS_PERMISSION_DENIED` | <span data-ttu-id="0955e-115">Falha na autorização.</span><span class="sxs-lookup"><span data-stu-id="0955e-115">Authorization failed.</span></span> |
| `GRPC_STATUS_CANCELLED` | <span data-ttu-id="0955e-116">A chamada foi cancelada, geralmente pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="0955e-116">Call was canceled, usually by the caller.</span></span> |

## <a name="raise-errors-in-aspnet-core-grpc"></a><span data-ttu-id="0955e-117">Gerar erros no ASP.NET Core gRPC</span><span class="sxs-lookup"><span data-stu-id="0955e-117">Raise errors in ASP.NET Core gRPC</span></span>

<span data-ttu-id="0955e-118">Um serviço gRPC do ASP.NET Core pode enviar uma resposta de erro lançando um `RpcException`, que pode ser capturado pelo cliente como se estivesse no mesmo processo.</span><span class="sxs-lookup"><span data-stu-id="0955e-118">An ASP.NET Core gRPC service can send an error response by throwing an `RpcException`, which can be caught by the client as if it were in the same process.</span></span> <span data-ttu-id="0955e-119">O `RpcException` deve incluir um código de status e uma descrição e pode, opcionalmente, incluir metadados e uma mensagem de exceção mais longa.</span><span class="sxs-lookup"><span data-stu-id="0955e-119">The `RpcException` must include a status code and description, and can optionally include metadata and a longer exception message.</span></span> <span data-ttu-id="0955e-120">Os metadados podem ser usados para enviar dados de suporte, de forma semelhante a como `FaultContract` objetos podem transportar dados adicionais para erros do WCF.</span><span class="sxs-lookup"><span data-stu-id="0955e-120">The metadata can be used to send supporting data, similar to how `FaultContract` objects can carry additional data for WCF errors.</span></span>

```csharp
public async Task<GetPortfolioResponse> GetPortfolio(GetPortfolioRequest request, ServerCallContext context)
{
    var user = context.GetHttpContext().User;
    if (!ValidateUser(user))
    {
        var metadata = new Metadata
        {
            { "User", user.Identity.Name }
        };
        throw new RpcException(new Status(StatusCode.PermissionDenied, "Permission denied"), metadata);
    }
}
```

## <a name="catch-errors-in-grpc-clients"></a><span data-ttu-id="0955e-121">Capturar erros em clientes gRPC</span><span class="sxs-lookup"><span data-stu-id="0955e-121">Catch errors in gRPC clients</span></span>

<span data-ttu-id="0955e-122">Assim como os clientes WCF podem capturar erros de <xref:System.ServiceModel.FaultException%601>, um cliente gRPC pode capturar uma `RpcException` para lidar com erros.</span><span class="sxs-lookup"><span data-stu-id="0955e-122">Just like WCF clients can catch <xref:System.ServiceModel.FaultException%601> errors, a gRPC client can catch an `RpcException` to handle errors.</span></span> <span data-ttu-id="0955e-123">Como `RpcException` não é um tipo genérico, você não pode capturar tipos de erro diferentes em blocos diferentes.</span><span class="sxs-lookup"><span data-stu-id="0955e-123">Because `RpcException` isn't a generic type, you can't catch different error types in different blocks.</span></span> <span data-ttu-id="0955e-124">Mas você pode usar C#o recurso de *filtros de exceção* para declarar blocos de `catch` separados para códigos de status diferentes, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="0955e-124">But you can use C#'s *exception filters* feature to declare separate `catch` blocks for different status codes, as shown in the following example:</span></span>

```csharp
try
{
    var portfolio = await client.GetPortfolioAsync(new GetPortfolioRequest { Id = id });
}
catch (RpcException ex) when (ex.StatusCode == StatusCode.PermissionDenied)
{
    var userEntry = ex.Trailers.FirstOrDefault(e => e.Key == "User");
    Console.WriteLine($"User '{userEntry.Value}' does not have permission to view this portfolio.");
}
catch (RpcException)
{
    // Handle any other error type ...
}
```

> [!IMPORTANT]
> <span data-ttu-id="0955e-125">Ao fornecer metadados adicionais para erros, certifique-se de documentar as chaves e os valores relevantes na documentação da API ou em comentários no arquivo de `.proto`.</span><span class="sxs-lookup"><span data-stu-id="0955e-125">When you provide additional metadata for errors, be sure to document the relevant keys and values in your API documentation, or in comments in your `.proto` file.</span></span>

## <a name="grpc-richer-error-model"></a><span data-ttu-id="0955e-126">modelo de erro gRPC mais rico</span><span class="sxs-lookup"><span data-stu-id="0955e-126">gRPC richer error model</span></span>

<span data-ttu-id="0955e-127">O Google desenvolveu um [modelo de erro mais rico](https://cloud.google.com/apis/design/errors#error_model) que é mais parecido com o [FaultContract](xref:System.ServiceModel.FaultContractAttribute)do WCF, mas esse modelo C# ainda não tem suporte.</span><span class="sxs-lookup"><span data-stu-id="0955e-127">Google has developed a [richer error model](https://cloud.google.com/apis/design/errors#error_model) that's more like WCF's [FaultContract](xref:System.ServiceModel.FaultContractAttribute), but this model isn't supported in C# yet.</span></span> <span data-ttu-id="0955e-128">Atualmente, ele só está disponível para go, Java, Python e C++.</span><span class="sxs-lookup"><span data-stu-id="0955e-128">Currently, it's only available for Go, Java, Python, and C++.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="0955e-129">[Anterior](metadata.md)
>[Próximo](ws-protocols.md)</span><span class="sxs-lookup"><span data-stu-id="0955e-129">[Previous](metadata.md)
[Next](ws-protocols.md)</span></span>
