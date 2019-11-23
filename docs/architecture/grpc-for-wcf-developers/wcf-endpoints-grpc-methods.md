---
title: Pontos de extremidade do WCF e métodos de gRPC – gRPC para desenvolvedores do WCF
description: Comparação de pontos de extremidade do WCF declarados com os atributos ServiceContract e OperationContract, e os métodos gRPC declarados em Protobuf
ms.date: 09/02/2019
ms.openlocfilehash: 763862a363afc6aab72335050cf4822754816c7a
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966924"
---
# <a name="wcf-endpoints-and-grpc-methods"></a><span data-ttu-id="0b975-103">Pontos de extremidade do WCF e métodos gRPC</span><span class="sxs-lookup"><span data-stu-id="0b975-103">WCF endpoints and gRPC methods</span></span>

<span data-ttu-id="0b975-104">No WCF, quando você estiver escrevendo o código do aplicativo, use um dos seguintes métodos:</span><span class="sxs-lookup"><span data-stu-id="0b975-104">In WCF, when you're writing your application code, you use one of the following methods:</span></span>

- <span data-ttu-id="0b975-105">Você escreve o código do aplicativo em uma classe e decora métodos com o atributo [OperationContract](xref:System.ServiceModel.OperationContractAttribute) .</span><span class="sxs-lookup"><span data-stu-id="0b975-105">You write the application code in a class and decorate methods with the [OperationContract](xref:System.ServiceModel.OperationContractAttribute) attribute.</span></span>
- <span data-ttu-id="0b975-106">Você declara uma interface para o serviço e adiciona atributos [OperationContract](xref:System.ServiceModel.OperationContractAttribute) à interface.</span><span class="sxs-lookup"><span data-stu-id="0b975-106">You declare an interface for the service and add [OperationContract](xref:System.ServiceModel.OperationContractAttribute) attributes to the interface.</span></span>

<span data-ttu-id="0b975-107">Por exemplo, o equivalente do WCF do serviço de saudação `greet.proto` pode ser escrito da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="0b975-107">For example, the WCF equivalent of the `greet.proto` Greeter service might be written as follows:</span></span>

```csharp
[ServiceContract]
public interface IGreeterService
{
    [OperationContract]
    string SayHello(string name);
}
```

<span data-ttu-id="0b975-108">O capítulo 3 mostrou que as definições de mensagem Protobuf são usadas para gerar classes de dados.</span><span class="sxs-lookup"><span data-stu-id="0b975-108">Chapter 3 showed that Protobuf message definitions are used to generate data classes.</span></span> <span data-ttu-id="0b975-109">Declarações de serviço e método são usadas para gerar classes base que você herda de para implementar o serviço.</span><span class="sxs-lookup"><span data-stu-id="0b975-109">Service and method declarations are used to generate base classes that you inherit from to implement the service.</span></span> <span data-ttu-id="0b975-110">Você apenas declara os métodos a serem implementados no arquivo `.proto`, e o compilador gera uma classe base com métodos virtuais que você deve substituir.</span><span class="sxs-lookup"><span data-stu-id="0b975-110">You just declare the methods to be implemented in the `.proto` file, and the compiler generates a base class with virtual methods you must override.</span></span>

## <a name="operationcontract-properties"></a><span data-ttu-id="0b975-111">Propriedades de OperationContract</span><span class="sxs-lookup"><span data-stu-id="0b975-111">OperationContract properties</span></span>

<span data-ttu-id="0b975-112">O atributo [OperationContract](xref:System.ServiceModel.OperationContractAttribute) tem propriedades para controlar ou refinar como ele funciona.</span><span class="sxs-lookup"><span data-stu-id="0b975-112">The [OperationContract](xref:System.ServiceModel.OperationContractAttribute) attribute has properties to control or refine how it works.</span></span> <span data-ttu-id="0b975-113">os métodos gRPC não oferecem esse tipo de controle.</span><span class="sxs-lookup"><span data-stu-id="0b975-113">gRPC methods don’t offer this type of control.</span></span> <span data-ttu-id="0b975-114">A tabela a seguir define as propriedades `OperationContract` e como a funcionalidade que elas especificam é (ou não) lida com o no gRPC:</span><span class="sxs-lookup"><span data-stu-id="0b975-114">The following table sets out those `OperationContract` properties and how the functionality they specify is (or isn’t) dealt with in gRPC:</span></span>

| <span data-ttu-id="0b975-115">Propriedade `OperationContract`</span><span class="sxs-lookup"><span data-stu-id="0b975-115">`OperationContract` property</span></span> | <span data-ttu-id="0b975-116">gRPC</span><span class="sxs-lookup"><span data-stu-id="0b975-116">gRPC</span></span>                                             |
| ---------------------------- | ------------------------------------------------ |
| <xref:System.ServiceModel.OperationContractAttribute.Action>             | <span data-ttu-id="0b975-117">URI que identifica a operação.</span><span class="sxs-lookup"><span data-stu-id="0b975-117">URI identifying the operation.</span></span> <span data-ttu-id="0b975-118">gRPC usa o nome do `package`, `service` e `rpc` do arquivo `.proto`.</span><span class="sxs-lookup"><span data-stu-id="0b975-118">gRPC uses the name of the `package`, `service` and `rpc` from the `.proto` file.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern>       | <span data-ttu-id="0b975-119">Todos os métodos de serviço gRPC retornam objetos `Task`.</span><span class="sxs-lookup"><span data-stu-id="0b975-119">All gRPC service methods return `Task` objects.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.IsInitiating>       | <span data-ttu-id="0b975-120">Consulte a observação abaixo.</span><span class="sxs-lookup"><span data-stu-id="0b975-120">See note below.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.IsOneWay>           | <span data-ttu-id="0b975-121">Os métodos gRPC unidirecionais retornam resultados `Empty` ou usam o streaming de cliente.</span><span class="sxs-lookup"><span data-stu-id="0b975-121">One-way gRPC methods return `Empty` results or use client streaming.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.IsTerminating>      | <span data-ttu-id="0b975-122">Consulte a observação abaixo.</span><span class="sxs-lookup"><span data-stu-id="0b975-122">See note below.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.Name>               | <span data-ttu-id="0b975-123">Relacionado ao SOAP, não há significado em gRPC.</span><span class="sxs-lookup"><span data-stu-id="0b975-123">SOAP-related, no meaning in gRPC.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel>    | <span data-ttu-id="0b975-124">Sem criptografia de mensagem; criptografia de rede tratada na camada de transporte (TLS sobre HTTP/2).</span><span class="sxs-lookup"><span data-stu-id="0b975-124">No message encryption; network encryption handled at the transport layer (TLS over HTTP/2).</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.ReplyAction>        | <span data-ttu-id="0b975-125">Relacionado ao SOAP, não há significado em gRPC.</span><span class="sxs-lookup"><span data-stu-id="0b975-125">SOAP-related, no meaning in gRPC.</span></span> |

<span data-ttu-id="0b975-126">A propriedade `IsInitiating` permite que você indique que um método em um [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) não pode ser o primeiro método chamado como parte de uma sessão.</span><span class="sxs-lookup"><span data-stu-id="0b975-126">The `IsInitiating` property lets you indicate that a method within a [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) can't be the first method called as part of a session.</span></span> <span data-ttu-id="0b975-127">A propriedade `IsTerminating` faz com que o servidor feche a sessão depois que uma operação é chamada (ou o cliente, se usado em um cliente de retorno de chamada).</span><span class="sxs-lookup"><span data-stu-id="0b975-127">The `IsTerminating` property causes the server to close the session after an operation is called (or the client, if used on a callback client).</span></span> <span data-ttu-id="0b975-128">No gRPC, os fluxos são criados por métodos únicos e fechados explicitamente.</span><span class="sxs-lookup"><span data-stu-id="0b975-128">In gRPC, streams are created by single methods and closed explicitly.</span></span> <span data-ttu-id="0b975-129">Consulte [streaming do gRPC](rpc-types.md#grpc-streaming).</span><span class="sxs-lookup"><span data-stu-id="0b975-129">See [gRPC streaming](rpc-types.md#grpc-streaming).</span></span>

<span data-ttu-id="0b975-130">Para obter mais informações sobre segurança e criptografia do gRPC, consulte o [capítulo 6](security.md).</span><span class="sxs-lookup"><span data-stu-id="0b975-130">For more information on gRPC security and encryption, see [chapter 6](security.md).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="0b975-131">[Anterior](wcf-services-to-grpc-comparison.md)
>[Próximo](wcf-bindings.md)</span><span class="sxs-lookup"><span data-stu-id="0b975-131">[Previous](wcf-services-to-grpc-comparison.md)
[Next](wcf-bindings.md)</span></span>
