---
title: Comparando o WCF com o gRPC-gRPC para desenvolvedores do WCF
description: Uma comparação das estruturas do WCF e do gRPC para a criação de aplicativos distribuídos.
ms.date: 09/02/2019
ms.openlocfilehash: 312492dcce4bdef61feff0bf924c6df287b9c676
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966961"
---
# <a name="comparing-wcf-to-grpc"></a>Comparando o WCF com o gRPC

O capítulo anterior deve ter dado a você uma boa visão do Protobuf e como o gRPC lida com as mensagens. Antes de trabalhar em uma conversão detalhada do WCF para o gRPC, é importante observar como a variedade de recursos disponíveis atualmente no WCF é tratada em gRPC e quais soluções alternativas você pode usar quando não parece haver um equivalente gRPC. Em particular, este capítulo abordará os seguintes assuntos:

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

// The request message containing the user's name.
message HelloRequest {
  string name = 1;
}

// The response message containing the greetings.
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

Este capítulo fará referência a este código de exemplo ao explicar vários conceitos e recursos do gRPC.

>[!div class="step-by-step"]
>[Anterior](protobuf-maps.md)
>[Próximo](wcf-endpoints-grpc-methods.md)
