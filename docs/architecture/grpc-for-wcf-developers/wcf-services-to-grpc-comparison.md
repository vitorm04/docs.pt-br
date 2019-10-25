---
title: Comparando o WCF com o gRPC-gRPC para desenvolvedores do WCF
description: Uma comparação das estruturas do WCF e do gRPC para a criação de aplicativos distribuídos.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 5ab1380d4ded52abff08c35c430adf2f3ed7c58b
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846063"
---
# <a name="comparing-wcf-to-grpc"></a><span data-ttu-id="047ab-103">Comparando o WCF com o gRPC</span><span class="sxs-lookup"><span data-stu-id="047ab-103">Comparing WCF to gRPC</span></span>

<span data-ttu-id="047ab-104">O capítulo anterior deve ter dado a você uma boa visão do Protobuf e como o gRPC lida com as mensagens.</span><span class="sxs-lookup"><span data-stu-id="047ab-104">The previous chapter should have given you a good look at Protobuf and how gRPC handles messages.</span></span> <span data-ttu-id="047ab-105">Antes de trabalhar em uma conversão detalhada do WCF para o gRPC, é importante observar como a variedade de recursos disponíveis atualmente no WCF é tratada em gRPC e quais soluções alternativas você pode usar quando não parece haver um equivalente gRPC.</span><span class="sxs-lookup"><span data-stu-id="047ab-105">Before working through a detailed conversion from WCF to gRPC, it's important to look at how the range of features currently available in WCF are handled in gRPC and what workarounds you can use when there doesn't appear to be a gRPC equivalent.</span></span> <span data-ttu-id="047ab-106">Em particular, este capítulo abordará os seguintes assuntos:</span><span class="sxs-lookup"><span data-stu-id="047ab-106">In particular, this chapter will cover the following subjects:</span></span>

- <span data-ttu-id="047ab-107">Operações e métodos</span><span class="sxs-lookup"><span data-stu-id="047ab-107">Operations and methods</span></span>
- <span data-ttu-id="047ab-108">Associações e transportes</span><span class="sxs-lookup"><span data-stu-id="047ab-108">Bindings and transports</span></span>
- <span data-ttu-id="047ab-109">Tipos de RPC</span><span class="sxs-lookup"><span data-stu-id="047ab-109">RPC types</span></span>
- <span data-ttu-id="047ab-110">Metadados</span><span class="sxs-lookup"><span data-stu-id="047ab-110">Metadata</span></span>
- <span data-ttu-id="047ab-111">Tratamento de erros</span><span class="sxs-lookup"><span data-stu-id="047ab-111">Error handling</span></span>
- <span data-ttu-id="047ab-112">Protocolos WS-\*</span><span class="sxs-lookup"><span data-stu-id="047ab-112">WS-\* protocols</span></span>

## <a name="grpc-example"></a><span data-ttu-id="047ab-113">exemplo de gRPC</span><span class="sxs-lookup"><span data-stu-id="047ab-113">gRPC example</span></span>

<span data-ttu-id="047ab-114">Quando você cria um novo projeto ASP.NET Core 3,0 gRPC no Visual Studio 2019 ou na linha de comando, o equivalente de gRPC de "Olá, Mundo" é gerado para você.</span><span class="sxs-lookup"><span data-stu-id="047ab-114">When you create a new ASP.NET Core 3.0 gRPC project from Visual Studio 2019 or the command line, the gRPC equivalent of "Hello World" is generated for you.</span></span> <span data-ttu-id="047ab-115">Ele consiste em um arquivo de `greeter.proto` que define o serviço e suas mensagens, e um arquivo de `GreeterService.cs` com uma implementação do serviço.</span><span class="sxs-lookup"><span data-stu-id="047ab-115">It consists of a `greeter.proto` file that defines the service and its messages, and a `GreeterService.cs` file with an implementation of the service.</span></span>

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

<span data-ttu-id="047ab-116">Este capítulo fará referência a este código de exemplo ao explicar vários conceitos e recursos do gRPC.</span><span class="sxs-lookup"><span data-stu-id="047ab-116">This chapter will refer to this example code when explaining various concepts and features of gRPC.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="047ab-117">[Anterior](protobuf-maps.md)
>[Próximo](wcf-endpoints-grpc-methods.md)</span><span class="sxs-lookup"><span data-stu-id="047ab-117">[Previous](protobuf-maps.md)
[Next](wcf-endpoints-grpc-methods.md)</span></span>
