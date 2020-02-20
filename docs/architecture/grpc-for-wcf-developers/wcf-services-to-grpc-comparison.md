---
title: Comparando o WCF com o gRPC-gRPC para desenvolvedores do WCF
description: Uma comparação das estruturas do WCF e do gRPC para a criação de aplicativos distribuídos.
ms.date: 09/02/2019
ms.openlocfilehash: 4f54db76c9512b770b4dd993496d95437dd89753
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503332"
---
# <a name="comparing-wcf-to-grpc"></a>Comparando o WCF com o gRPC

O capítulo anterior forneceu uma boa visão sobre Protobuf e como o gRPC lida com mensagens. Antes de você trabalhar com uma conversão detalhada de Windows Communication Foundation (WCF) para gRPC, é importante saber como os recursos disponíveis no WCF são manipulados no gRPC e quais soluções alternativas você pode usar quando não há nenhum equivalente gRPC. Em particular, este capítulo abordará os seguintes assuntos:

- Operações e métodos
- Associações e transportes
- Tipos de RPC
- Metadados
- Tratamento de erros
- Protocolos WS-\*

## <a name="grpc-example"></a>exemplo de gRPC

Quando você cria um novo projeto ASP.NET Core 3,0 gRPC no Visual Studio 2019 ou na linha de comando, o equivalente de gRPC de "Olá, Mundo" é gerado para você. Ele consiste em um arquivo de `greeter.proto` que define o serviço e suas mensagens, e um arquivo de `GreeterService.cs` com uma implementação do serviço.

```protobuf
syntax = "proto3";

option csharp_namespace = "HelloGrpc";

package Greet;

// The greeting service definition.
service Greeter {
  // Sends a greeting
  rpc SayHello (HelloRequest) returns (HelloReply);
}

// The request message that contains the user's name.
message HelloRequest {
  string name = 1;
}

// The response message that contains the greetings.
message HelloReply {
  string message = 1;
}
```

```csharp
using System.Threading.Tasks;
using Grpc.Core;
using Microsoft.Extensions.Logging;

namespace HelloGrpc
{
    public class GreeterService : Greeter.GreeterBase
    {
        private readonly ILogger<GreeterService> _logger;
        public GreeterService(ILogger<GreeterService> logger)
        {
            _logger = logger;
        }

        public override Task<HelloReply> SayHello(HelloRequest request, ServerCallContext context)
        {
            return Task.FromResult(new HelloReply
            {
                Message = "Hello " + request.Name
            });
        }
    }
}
```

Este capítulo fará referência a este código de exemplo ao explicar diferentes conceitos e recursos do gRPC.

>[!div class="step-by-step"]
>[Anterior](protobuf-maps.md)
>[Próximo](wcf-endpoints-grpc-methods.md)
