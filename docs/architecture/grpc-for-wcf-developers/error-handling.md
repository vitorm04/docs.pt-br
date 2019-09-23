---
title: Tratamento de erro-gRPC para desenvolvedores do WCF
description: A SER ESCRITO
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 3535a00aad49f532eb5f5f778116454a12bfd639
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184452"
---
# <a name="error-handling"></a>Tratamento de erros

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

O WCF `FaultException<T>` usa `FaultContract` e para fornecer informações detalhadas de erro, incluindo suporte ao padrão de falha de SOAP.

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

## <a name="raising-errors-in-aspnet-core-grpc"></a>Gerando erros no ASP.NET Core gRPC

Um serviço gRPC do ASP.NET Core pode enviar uma resposta de erro lançando um `RpcException`, que pode ser capturado pelo cliente como se estivesse no mesmo processo. O `RpcException` deve incluir um código de status e uma descrição e pode, opcionalmente, incluir metadados e uma mensagem de exceção mais longa. Os metadados podem ser usados para enviar dados de suporte, de forma `FaultContract` semelhante a como os objetos podem transportar dados adicionais para erros do WCF.

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

## <a name="catching-errors-in-grpc-clients"></a>Capturando erros em clientes gRPC

Assim como os clientes WCF podem <xref:System.ServiceModel.FaultException%601> capturar erros, um cliente gRPC pode capturar `RpcException` um para lidar com erros. Como `RpcException` não é um tipo genérico, você não pode capturar tipos de erro diferentes em blocos diferentes, mas C#você pode usar o recurso de filtros `catch` de *exceção* para declarar blocos separados para códigos de status diferentes, conforme mostrado a seguir exemplo

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
> Ao fornecer metadados adicionais para erros, certifique-se de documentar as chaves e os valores relevantes na documentação da API ou em comentários em `.proto` seu arquivo.

## <a name="grpc-richer-error-model"></a>Modelo de erro gRPC mais rico

Olhando adiante, o Google desenvolveu um [modelo de erro mais rico](https://cloud.google.com/apis/design/errors#error_model) que é mais parecido com o [FaultContract](xref:System.ServiceModel.FaultContractAttribute)do WCF, mas C# ainda não tem suporte. Atualmente, ele está disponível apenas para go, Java, Python e C++, mas o suporte C# para é esperado no próximo ano.

>[!div class="step-by-step"]
>[Anterior](metadata.md)
>[Próximo](ws-protocols.md)
