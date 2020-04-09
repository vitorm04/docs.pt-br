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
# <a name="error-handling"></a>Tratamento de erros

O Windows Communication Foundation <xref:System.ServiceModel.FaultException%601> (WCF) usa e [o FaultContract](xref:System.ServiceModel.FaultContractAttribute) para fornecer informações detalhadas sobre erros, incluindo o suporte ao padrão SOAP Fault.

Infelizmente, a versão atual do gRPC não possui a sofisticação encontrada com o WCF, e só tem um tratamento limitado de erros incorporados com base em códigos de status simples e metadados. A tabela a seguir é um guia rápido para os códigos de status mais usados:

| Código de status | Problema |
| ----------- | ------- |
| `GRPC_STATUS_UNIMPLEMENTED` | O método não foi escrito. |
| `GRPC_STATUS_UNAVAILABLE` | Problema com todo o serviço. |
| `GRPC_STATUS_UNKNOWN` | Resposta inválida. |
| `GRPC_STATUS_INTERNAL` | Problema com codificação/decodificação. |
| `GRPC_STATUS_UNAUTHENTICATED` | Falha na autenticação. |
| `GRPC_STATUS_PERMISSION_DENIED` | Falha na autorização. |
| `GRPC_STATUS_CANCELLED` | A chamada foi cancelada, geralmente pelo interlocutor. |

## <a name="raise-errors-in-aspnet-core-grpc"></a>Aumentar os erros no núcleo ASP.NET gRPC

Uma ASP.NET serviço core gRPC pode enviar `RpcException`uma resposta de erro lançando um , que pode ser pego pelo cliente como se estivesse no mesmo processo. O `RpcException` deve incluir um código de status e uma descrição, e pode incluir, opcionalmente, metadados e uma mensagem de exceção mais longa. Os metadados podem ser usados para `FaultContract` enviar dados de suporte, semelhante si com a forma como os objetos podem transportar dados adicionais para erros de WCF.

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

## <a name="catch-errors-in-grpc-clients"></a>Erros de captura em clientes gRPC

Assim como os clientes WCF podem pegar <xref:System.ServiceModel.FaultException%601> erros, um cliente gRPC pode pegar um `RpcException` para lidar com erros. Como `RpcException` não é um tipo genérico, você não pode pegar diferentes tipos de erro em blocos diferentes. Mas você pode usar o recurso de filtros de exceção do C#para declarar *blocos separados* `catch` para diferentes códigos de status, como mostrado no exemplo a seguir:

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
> Quando você fornecer metadados adicionais para erros, certifique-se de documentar as chaves `.proto` e valores relevantes em sua documentação de API ou em comentários em seu arquivo.

## <a name="grpc-richer-error-model"></a>modelo de erro gRPC mais rico

O Google desenvolveu um [modelo de erro mais rico](https://cloud.google.com/apis/design/errors#error_model) que é mais parecido com o [FaultContract](xref:System.ServiceModel.FaultContractAttribute)do WCF, mas este modelo ainda não é suportado em C#. Atualmente, ele só está disponível para Go, Java, Python e C++.

>[!div class="step-by-step"]
>[Próximo](metadata.md)
>[anterior](ws-protocols.md)
