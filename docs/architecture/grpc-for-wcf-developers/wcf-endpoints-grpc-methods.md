---
title: Pontos de extremidade do WCF e métodos de gRPC – gRPC para desenvolvedores do WCF
description: Comparação de pontos de extremidade do WCF declarados com os atributos ServiceContract e OperationContract, e os métodos gRPC declarados em Protobuf
ms.date: 09/02/2019
ms.openlocfilehash: 1bc6ecbc73bfc0a58393e4c28672b897ed6f2f15
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503427"
---
# <a name="wcf-endpoints-and-grpc-methods"></a>Pontos de extremidade do WCF e métodos gRPC

No Windows Communication Foundation (WCF), quando você estiver escrevendo o código do aplicativo, use um dos seguintes métodos:

- Você escreve o código do aplicativo em uma classe e decora métodos com o atributo [OperationContract](xref:System.ServiceModel.OperationContractAttribute) .
- Você declara uma interface para o serviço e adiciona atributos [OperationContract](xref:System.ServiceModel.OperationContractAttribute) à interface.

Por exemplo, o equivalente do WCF do serviço de saudação `greet.proto` pode ser escrito da seguinte maneira:

```csharp
[ServiceContract]
public interface IGreeterService
{
    [OperationContract]
    string SayHello(string name);
}
```

O capítulo 3 mostrou que as definições de mensagem Protobuf são usadas para gerar classes de dados. Declarações de serviço e método são usadas para gerar classes base que você herda de para implementar o serviço. Você apenas declara os métodos a serem implementados no arquivo `.proto`, e o compilador gera uma classe base com métodos virtuais que você deve substituir.

## <a name="operationcontract-properties"></a>Propriedades de OperationContract

O atributo [OperationContract](xref:System.ServiceModel.OperationContractAttribute) tem propriedades para controlar ou refinar como ele funciona. os métodos gRPC não oferecem esse tipo de controle. A tabela a seguir lista as propriedades de `OperationContract` e descreve como a funcionalidade que elas especificam é (ou não) lida com o no gRPC:

| Propriedade `OperationContract` | gRPC                                             |
| ---------------------------- | ------------------------------------------------ |
| <xref:System.ServiceModel.OperationContractAttribute.Action>             | Um URI identifica a operação. gRPC usa o nome de `package`, `service`e `rpc` do arquivo `.proto`. |
| <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern>       | Todos os métodos de serviço gRPC retornam objetos `Task`. |
| <xref:System.ServiceModel.OperationContractAttribute.IsInitiating>       | Consulte o parágrafo após esta tabela. |
| <xref:System.ServiceModel.OperationContractAttribute.IsOneWay>           | Os métodos gRPC unidirecionais retornam resultados `Empty` ou usam o streaming de cliente. |
| <xref:System.ServiceModel.OperationContractAttribute.IsTerminating>      | Consulte o parágrafo após esta tabela. |
| <xref:System.ServiceModel.OperationContractAttribute.Name>               | Essa propriedade é relacionada a SOAP e não tem significado em gRPC. |
| <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel>    | Não há criptografia de mensagem. A criptografia de rede é tratada na camada de transporte (TLS sobre HTTP/2). |
| <xref:System.ServiceModel.OperationContractAttribute.ReplyAction>        | Essa propriedade é relacionada a SOAP e não tem significado em gRPC. |

A propriedade `IsInitiating` permite que você indique que um método no [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) não pode ser o primeiro método chamado como parte de uma sessão. A propriedade `IsTerminating` faz com que o servidor feche a sessão depois que uma operação for chamada (ou o cliente, se a propriedade for usada em um cliente de retorno de chamada). No gRPC, os fluxos são criados por métodos únicos e fechados explicitamente. Consulte [streaming do gRPC](rpc-types.md#grpc-streaming).

Para obter mais informações sobre segurança e criptografia do gRPC, consulte o [capítulo 6](security.md).

>[!div class="step-by-step"]
>[Anterior](wcf-services-to-grpc-comparison.md)
>[Próximo](wcf-bindings.md)
