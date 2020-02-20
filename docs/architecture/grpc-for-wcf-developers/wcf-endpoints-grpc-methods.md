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
# <a name="wcf-endpoints-and-grpc-methods"></a><span data-ttu-id="f914a-103">Pontos de extremidade do WCF e métodos gRPC</span><span class="sxs-lookup"><span data-stu-id="f914a-103">WCF endpoints and gRPC methods</span></span>

<span data-ttu-id="f914a-104">No Windows Communication Foundation (WCF), quando você estiver escrevendo o código do aplicativo, use um dos seguintes métodos:</span><span class="sxs-lookup"><span data-stu-id="f914a-104">In Windows Communication Foundation (WCF), when you're writing your application code, you use one of the following methods:</span></span>

- <span data-ttu-id="f914a-105">Você escreve o código do aplicativo em uma classe e decora métodos com o atributo [OperationContract](xref:System.ServiceModel.OperationContractAttribute) .</span><span class="sxs-lookup"><span data-stu-id="f914a-105">You write the application code in a class and decorate methods with the [OperationContract](xref:System.ServiceModel.OperationContractAttribute) attribute.</span></span>
- <span data-ttu-id="f914a-106">Você declara uma interface para o serviço e adiciona atributos [OperationContract](xref:System.ServiceModel.OperationContractAttribute) à interface.</span><span class="sxs-lookup"><span data-stu-id="f914a-106">You declare an interface for the service and add [OperationContract](xref:System.ServiceModel.OperationContractAttribute) attributes to the interface.</span></span>

<span data-ttu-id="f914a-107">Por exemplo, o equivalente do WCF do serviço de saudação `greet.proto` pode ser escrito da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="f914a-107">For example, the WCF equivalent of the `greet.proto` Greeter service might be written as follows:</span></span>

```csharp
[ServiceContract]
public interface IGreeterService
{
    [OperationContract]
    string SayHello(string name);
}
```

<span data-ttu-id="f914a-108">O capítulo 3 mostrou que as definições de mensagem Protobuf são usadas para gerar classes de dados.</span><span class="sxs-lookup"><span data-stu-id="f914a-108">Chapter 3 showed that Protobuf message definitions are used to generate data classes.</span></span> <span data-ttu-id="f914a-109">Declarações de serviço e método são usadas para gerar classes base que você herda de para implementar o serviço.</span><span class="sxs-lookup"><span data-stu-id="f914a-109">Service and method declarations are used to generate base classes that you inherit from to implement the service.</span></span> <span data-ttu-id="f914a-110">Você apenas declara os métodos a serem implementados no arquivo `.proto`, e o compilador gera uma classe base com métodos virtuais que você deve substituir.</span><span class="sxs-lookup"><span data-stu-id="f914a-110">You just declare the methods to be implemented in the `.proto` file, and the compiler generates a base class with virtual methods that you must override.</span></span>

## <a name="operationcontract-properties"></a><span data-ttu-id="f914a-111">Propriedades de OperationContract</span><span class="sxs-lookup"><span data-stu-id="f914a-111">OperationContract properties</span></span>

<span data-ttu-id="f914a-112">O atributo [OperationContract](xref:System.ServiceModel.OperationContractAttribute) tem propriedades para controlar ou refinar como ele funciona.</span><span class="sxs-lookup"><span data-stu-id="f914a-112">The [OperationContract](xref:System.ServiceModel.OperationContractAttribute) attribute has properties to control or refine how it works.</span></span> <span data-ttu-id="f914a-113">os métodos gRPC não oferecem esse tipo de controle.</span><span class="sxs-lookup"><span data-stu-id="f914a-113">gRPC methods don't offer this type of control.</span></span> <span data-ttu-id="f914a-114">A tabela a seguir lista as propriedades de `OperationContract` e descreve como a funcionalidade que elas especificam é (ou não) lida com o no gRPC:</span><span class="sxs-lookup"><span data-stu-id="f914a-114">The following table lists those `OperationContract` properties and describes how the functionality that they specify is (or isn't) dealt with in gRPC:</span></span>

| <span data-ttu-id="f914a-115">Propriedade `OperationContract`</span><span class="sxs-lookup"><span data-stu-id="f914a-115">`OperationContract` property</span></span> | <span data-ttu-id="f914a-116">gRPC</span><span class="sxs-lookup"><span data-stu-id="f914a-116">gRPC</span></span>                                             |
| ---------------------------- | ------------------------------------------------ |
| <xref:System.ServiceModel.OperationContractAttribute.Action>             | <span data-ttu-id="f914a-117">Um URI identifica a operação.</span><span class="sxs-lookup"><span data-stu-id="f914a-117">A URI identifies the operation.</span></span> <span data-ttu-id="f914a-118">gRPC usa o nome de `package`, `service`e `rpc` do arquivo `.proto`.</span><span class="sxs-lookup"><span data-stu-id="f914a-118">gRPC uses the name of `package`, `service`, and `rpc` from the `.proto` file.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern>       | <span data-ttu-id="f914a-119">Todos os métodos de serviço gRPC retornam objetos `Task`.</span><span class="sxs-lookup"><span data-stu-id="f914a-119">All gRPC service methods return `Task` objects.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.IsInitiating>       | <span data-ttu-id="f914a-120">Consulte o parágrafo após esta tabela.</span><span class="sxs-lookup"><span data-stu-id="f914a-120">See the paragraph after this table.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.IsOneWay>           | <span data-ttu-id="f914a-121">Os métodos gRPC unidirecionais retornam resultados `Empty` ou usam o streaming de cliente.</span><span class="sxs-lookup"><span data-stu-id="f914a-121">One-way gRPC methods return `Empty` results or use client streaming.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.IsTerminating>      | <span data-ttu-id="f914a-122">Consulte o parágrafo após esta tabela.</span><span class="sxs-lookup"><span data-stu-id="f914a-122">See the paragraph after this table.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.Name>               | <span data-ttu-id="f914a-123">Essa propriedade é relacionada a SOAP e não tem significado em gRPC.</span><span class="sxs-lookup"><span data-stu-id="f914a-123">This property is SOAP related and has no meaning in gRPC.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel>    | <span data-ttu-id="f914a-124">Não há criptografia de mensagem.</span><span class="sxs-lookup"><span data-stu-id="f914a-124">There's no message encryption.</span></span> <span data-ttu-id="f914a-125">A criptografia de rede é tratada na camada de transporte (TLS sobre HTTP/2).</span><span class="sxs-lookup"><span data-stu-id="f914a-125">Network encryption is handled at the transport layer (TLS over HTTP/2).</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.ReplyAction>        | <span data-ttu-id="f914a-126">Essa propriedade é relacionada a SOAP e não tem significado em gRPC.</span><span class="sxs-lookup"><span data-stu-id="f914a-126">This property is SOAP related and has no meaning in gRPC.</span></span> |

<span data-ttu-id="f914a-127">A propriedade `IsInitiating` permite que você indique que um método no [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) não pode ser o primeiro método chamado como parte de uma sessão.</span><span class="sxs-lookup"><span data-stu-id="f914a-127">The `IsInitiating` property lets you indicate that a method within [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) can't be the first method called as part of a session.</span></span> <span data-ttu-id="f914a-128">A propriedade `IsTerminating` faz com que o servidor feche a sessão depois que uma operação for chamada (ou o cliente, se a propriedade for usada em um cliente de retorno de chamada).</span><span class="sxs-lookup"><span data-stu-id="f914a-128">The `IsTerminating` property causes the server to close the session after an operation is called (or the client, if the property is used on a callback client).</span></span> <span data-ttu-id="f914a-129">No gRPC, os fluxos são criados por métodos únicos e fechados explicitamente.</span><span class="sxs-lookup"><span data-stu-id="f914a-129">In gRPC, streams are created by single methods and closed explicitly.</span></span> <span data-ttu-id="f914a-130">Consulte [streaming do gRPC](rpc-types.md#grpc-streaming).</span><span class="sxs-lookup"><span data-stu-id="f914a-130">See [gRPC streaming](rpc-types.md#grpc-streaming).</span></span>

<span data-ttu-id="f914a-131">Para obter mais informações sobre segurança e criptografia do gRPC, consulte o [capítulo 6](security.md).</span><span class="sxs-lookup"><span data-stu-id="f914a-131">For more information on gRPC security and encryption, see [chapter 6](security.md).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f914a-132">[Anterior](wcf-services-to-grpc-comparison.md)
>[Próximo](wcf-bindings.md)</span><span class="sxs-lookup"><span data-stu-id="f914a-132">[Previous](wcf-services-to-grpc-comparison.md)
[Next](wcf-bindings.md)</span></span>
