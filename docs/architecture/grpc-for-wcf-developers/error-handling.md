---
title: Manipulação de erros - gRPC para desenvolvedores WCF
description: Tópicos relativos ao manuseio de erros no gRPC. Inclui uma tabela dos códigos de status mais usados.
ms.date: 09/02/2019
ms.openlocfilehash: 64a2355a8bd608c074f9bc420312b23aba0c1fb2
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988941"
---
# <a name="error-handling"></a><span data-ttu-id="27163-104">Tratamento de erros</span><span class="sxs-lookup"><span data-stu-id="27163-104">Error handling</span></span>

<span data-ttu-id="27163-105">O Windows Communication Foundation <xref:System.ServiceModel.FaultException%601> (WCF) usa e [o FaultContract](xref:System.ServiceModel.FaultContractAttribute) para fornecer informações detalhadas sobre erros, incluindo o suporte ao padrão SOAP Fault.</span><span class="sxs-lookup"><span data-stu-id="27163-105">Windows Communication Foundation (WCF) uses <xref:System.ServiceModel.FaultException%601> and [FaultContract](xref:System.ServiceModel.FaultContractAttribute) to provide detailed error information, including supporting the SOAP Fault standard.</span></span>

<span data-ttu-id="27163-106">Infelizmente, a versão atual do gRPC não possui a sofisticação encontrada com o WCF, e só tem um tratamento limitado de erros incorporados com base em códigos de status simples e metadados.</span><span class="sxs-lookup"><span data-stu-id="27163-106">Unfortunately, the current version of gRPC lacks the sophistication found with WCF, and only has limited built-in error handling based on simple status codes and metadata.</span></span> <span data-ttu-id="27163-107">A tabela a seguir é um guia rápido para os códigos de status mais usados:</span><span class="sxs-lookup"><span data-stu-id="27163-107">The following table is a quick guide to the most commonly used status codes:</span></span>

| <span data-ttu-id="27163-108">Código de status</span><span class="sxs-lookup"><span data-stu-id="27163-108">Status code</span></span> | <span data-ttu-id="27163-109">Problema</span><span class="sxs-lookup"><span data-stu-id="27163-109">Problem</span></span> |
| ----------- | ------- |
| `GRPC_STATUS_UNIMPLEMENTED` | <span data-ttu-id="27163-110">O método não foi escrito.</span><span class="sxs-lookup"><span data-stu-id="27163-110">Method hasn't been written.</span></span> |
| `GRPC_STATUS_UNAVAILABLE` | <span data-ttu-id="27163-111">Problema com todo o serviço.</span><span class="sxs-lookup"><span data-stu-id="27163-111">Problem with the whole service.</span></span> |
| `GRPC_STATUS_UNKNOWN` | <span data-ttu-id="27163-112">Resposta inválida.</span><span class="sxs-lookup"><span data-stu-id="27163-112">Invalid response.</span></span> |
| `GRPC_STATUS_INTERNAL` | <span data-ttu-id="27163-113">Problema com codificação/decodificação.</span><span class="sxs-lookup"><span data-stu-id="27163-113">Problem with encoding/decoding.</span></span> |
| `GRPC_STATUS_UNAUTHENTICATED` | <span data-ttu-id="27163-114">Falha na autenticação.</span><span class="sxs-lookup"><span data-stu-id="27163-114">Authentication failed.</span></span> |
| `GRPC_STATUS_PERMISSION_DENIED` | <span data-ttu-id="27163-115">Falha na autorização.</span><span class="sxs-lookup"><span data-stu-id="27163-115">Authorization failed.</span></span> |
| `GRPC_STATUS_CANCELLED` | <span data-ttu-id="27163-116">A chamada foi cancelada, geralmente pelo interlocutor.</span><span class="sxs-lookup"><span data-stu-id="27163-116">Call was canceled, usually by the caller.</span></span> |

## <a name="raise-errors-in-aspnet-core-grpc"></a><span data-ttu-id="27163-117">Aumentar os erros no núcleo ASP.NET gRPC</span><span class="sxs-lookup"><span data-stu-id="27163-117">Raise errors in ASP.NET Core gRPC</span></span>

<span data-ttu-id="27163-118">Uma ASP.NET serviço core gRPC pode enviar `RpcException`uma resposta de erro lançando um , que pode ser pego pelo cliente como se estivesse no mesmo processo.</span><span class="sxs-lookup"><span data-stu-id="27163-118">An ASP.NET Core gRPC service can send an error response by throwing an `RpcException`, which can be caught by the client as if it were in the same process.</span></span> <span data-ttu-id="27163-119">O `RpcException` deve incluir um código de status e uma descrição, e pode incluir, opcionalmente, metadados e uma mensagem de exceção mais longa.</span><span class="sxs-lookup"><span data-stu-id="27163-119">The `RpcException` must include a status code and description, and can optionally include metadata and a longer exception message.</span></span> <span data-ttu-id="27163-120">Os metadados podem ser usados para `FaultContract` enviar dados de suporte, semelhante si com a forma como os objetos podem transportar dados adicionais para erros de WCF.</span><span class="sxs-lookup"><span data-stu-id="27163-120">The metadata can be used to send supporting data, similar to how `FaultContract` objects can carry additional data for WCF errors.</span></span>

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

## <a name="catch-errors-in-grpc-clients"></a><span data-ttu-id="27163-121">Erros de captura em clientes gRPC</span><span class="sxs-lookup"><span data-stu-id="27163-121">Catch errors in gRPC clients</span></span>

<span data-ttu-id="27163-122">Assim como os clientes WCF podem pegar <xref:System.ServiceModel.FaultException%601> erros, um cliente gRPC pode pegar um `RpcException` para lidar com erros.</span><span class="sxs-lookup"><span data-stu-id="27163-122">Just like WCF clients can catch <xref:System.ServiceModel.FaultException%601> errors, a gRPC client can catch an `RpcException` to handle errors.</span></span> <span data-ttu-id="27163-123">Como `RpcException` não é um tipo genérico, você não pode pegar diferentes tipos de erro em blocos diferentes.</span><span class="sxs-lookup"><span data-stu-id="27163-123">Because `RpcException` isn't a generic type, you can't catch different error types in different blocks.</span></span> <span data-ttu-id="27163-124">Mas você pode usar o recurso de filtros de exceção do C#para declarar *blocos separados* `catch` para diferentes códigos de status, como mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="27163-124">But you can use C#'s *exception filters* feature to declare separate `catch` blocks for different status codes, as shown in the following example:</span></span>

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
> <span data-ttu-id="27163-125">Quando você fornecer metadados adicionais para erros, certifique-se de documentar as chaves `.proto` e valores relevantes em sua documentação de API ou em comentários em seu arquivo.</span><span class="sxs-lookup"><span data-stu-id="27163-125">When you provide additional metadata for errors, be sure to document the relevant keys and values in your API documentation, or in comments in your `.proto` file.</span></span>

## <a name="grpc-richer-error-model"></a><span data-ttu-id="27163-126">modelo de erro gRPC mais rico</span><span class="sxs-lookup"><span data-stu-id="27163-126">gRPC richer error model</span></span>

<span data-ttu-id="27163-127">O Google desenvolveu um [modelo de erro mais rico](https://cloud.google.com/apis/design/errors#error_model) que é mais parecido com o [FaultContract](xref:System.ServiceModel.FaultContractAttribute)do WCF, mas este modelo ainda não é suportado em C#.</span><span class="sxs-lookup"><span data-stu-id="27163-127">Google has developed a [richer error model](https://cloud.google.com/apis/design/errors#error_model) that's more like WCF's [FaultContract](xref:System.ServiceModel.FaultContractAttribute), but this model isn't supported in C# yet.</span></span> <span data-ttu-id="27163-128">Atualmente, ele só está disponível para Go, Java, Python e C++.</span><span class="sxs-lookup"><span data-stu-id="27163-128">Currently, it's only available for Go, Java, Python, and C++.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="27163-129">[Próximo](metadata.md)
>[anterior](ws-protocols.md)</span><span class="sxs-lookup"><span data-stu-id="27163-129">[Previous](metadata.md)
[Next](ws-protocols.md)</span></span>
