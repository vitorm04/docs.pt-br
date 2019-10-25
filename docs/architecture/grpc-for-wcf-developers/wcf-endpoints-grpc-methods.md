---
title: Pontos de extremidade do WCF e métodos de gRPC – gRPC para desenvolvedores do WCF
description: Comparação de pontos de extremidade do WCF declarados com os atributos ServiceContract e OperationContract, e os métodos gRPC declarados em Protobuf
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 1cb7fedf1fbb632438134375306801f356d7b921
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846062"
---
# <a name="wcf-endpoints-and-grpc-methods"></a>Pontos de extremidade do WCF e métodos gRPC

No WCF, quando você estiver escrevendo o código do aplicativo, use um dos seguintes métodos:

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

O atributo [OperationContract](xref:System.ServiceModel.OperationContractAttribute) tem propriedades para controlar ou refinar como ele funciona. os métodos gRPC não oferecem esse tipo de controle. A tabela a seguir define as propriedades `OperationContract` e como a funcionalidade que elas especificam é (ou não) lida com o no gRPC:

| Propriedade `OperationContract` | gRPC                                             |
| ---------------------------- | ------------------------------------------------ |
| <xref:System.ServiceModel.OperationContractAttribute.Action>             | URI que identifica a operação. gRPC usa o nome do `package`, `service` e `rpc` do arquivo `.proto`. |
| <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern>       | Todos os métodos de serviço gRPC retornam objetos `Task`. |
| <xref:System.ServiceModel.OperationContractAttribute.IsInitiating>       | Consulte a observação abaixo. |
| <xref:System.ServiceModel.OperationContractAttribute.IsOneWay>           | Os métodos gRPC unidirecionais retornam resultados `Empty` ou usam o streaming de cliente. |
| <xref:System.ServiceModel.OperationContractAttribute.IsTerminating>      | Consulte a observação abaixo. |
| <xref:System.ServiceModel.OperationContractAttribute.Name>               | Relacionado ao SOAP, não há significado em gRPC. |
| <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel>    | Sem criptografia de mensagem; criptografia de rede tratada na camada de transporte (TLS sobre HTTP/2). |
| <xref:System.ServiceModel.OperationContractAttribute.ReplyAction>        | Relacionado ao SOAP, não há significado em gRPC. |

A propriedade `IsInitiating` permite que você indique que um método em um [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) não pode ser o primeiro método chamado como parte de uma sessão. A propriedade `IsTerminating` faz com que o servidor feche a sessão depois que uma operação é chamada (ou o cliente, se usado em um cliente de retorno de chamada). No gRPC, os fluxos são criados por métodos únicos e fechados explicitamente. Consulte [streaming do gRPC](rpc-types.md#grpc-streaming).

Para obter mais informações sobre segurança e criptografia do gRPC, consulte o [capítulo 6](security.md).

>[!div class="step-by-step"]
>[Anterior](wcf-services-to-grpc-comparison.md)
>[Próximo](wcf-bindings.md)
