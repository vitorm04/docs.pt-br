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
# <a name="error-handling"></a>Tratamento de erros

Windows Communication Foundation (WCF) usa <xref:System.ServiceModel.FaultException%601> e [FaultContract](xref:System.ServiceModel.FaultContractAttribute) para fornecer informações de erro detalhadas, incluindo suporte ao padrão de falha SOAP.

Infelizmente, a versão atual do gRPC não tem a sofisticação encontrada com o WCF e só tem tratamento de erro interno limitado com base em códigos de status e metadados simples. A tabela a seguir é um guia rápido para os códigos de status mais usados:

| Código de status | Problema |
| ----------- | ------- |
| `GRPC_STATUS_UNIMPLEMENTED` | O método não foi gravado. |
| `GRPC_STATUS_UNAVAILABLE` | Problema com o serviço inteiro. |
| `GRPC_STATUS_UNKNOWN` | Resposta inválida. |
| `GRPC_STATUS_INTERNAL` | Problema com codificação/decodificação. |
| `GRPC_STATUS_UNAUTHENTICATED` | Falha na autenticação. |
| `GRPC_STATUS_PERMISSION_DENIED` | Falha na autorização. |
| `GRPC_STATUS_CANCELLED` | A chamada foi cancelada, geralmente pelo chamador. |

## <a name="raise-errors-in-aspnet-core-grpc"></a>Gerar erros no ASP.NET Core gRPC

Um serviço gRPC do ASP.NET Core pode enviar uma resposta de erro lançando um `RpcException`, que pode ser capturado pelo cliente como se estivesse no mesmo processo. O `RpcException` deve incluir um código de status e uma descrição e pode, opcionalmente, incluir metadados e uma mensagem de exceção mais longa. Os metadados podem ser usados para enviar dados de suporte, de forma semelhante a como `FaultContract` objetos podem transportar dados adicionais para erros do WCF.

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

## <a name="catch-errors-in-grpc-clients"></a>Capturar erros em clientes gRPC

Assim como os clientes WCF podem capturar erros de <xref:System.ServiceModel.FaultException%601>, um cliente gRPC pode capturar uma `RpcException` para lidar com erros. Como `RpcException` não é um tipo genérico, você não pode capturar tipos de erro diferentes em blocos diferentes. Mas você pode usar C#o recurso de *filtros de exceção* para declarar blocos de `catch` separados para códigos de status diferentes, conforme mostrado no exemplo a seguir:

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
> Ao fornecer metadados adicionais para erros, certifique-se de documentar as chaves e os valores relevantes na documentação da API ou em comentários no arquivo de `.proto`.

## <a name="grpc-richer-error-model"></a>modelo de erro gRPC mais rico

O Google desenvolveu um [modelo de erro mais rico](https://cloud.google.com/apis/design/errors#error_model) que é mais parecido com o [FaultContract](xref:System.ServiceModel.FaultContractAttribute)do WCF, mas esse modelo C# ainda não tem suporte. Atualmente, ele só está disponível para go, Java, Python e C++.

>[!div class="step-by-step"]
>[Anterior](metadata.md)
>[Próximo](ws-protocols.md)
