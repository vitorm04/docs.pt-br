---
title: Como implementar uma operação de serviço assíncrona
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e5d2ea5-d8f8-4712-bd18-ea3c5461702c
ms.openlocfilehash: fd7a1399dd575ad1a4b6c95e0e0510670eb13b51
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802300"
---
# <a name="how-to-implement-an-asynchronous-service-operation"></a><span data-ttu-id="a58d6-102">Como implementar uma operação de serviço assíncrona</span><span class="sxs-lookup"><span data-stu-id="a58d6-102">How to: Implement an Asynchronous Service Operation</span></span>
<span data-ttu-id="a58d6-103">Em aplicativos Windows Communication Foundation (WCF), uma operação de serviço pode ser implementada de forma assíncrona ou síncrona, sem ditar ao cliente como chamá-lo.</span><span class="sxs-lookup"><span data-stu-id="a58d6-103">In Windows Communication Foundation (WCF) applications, a service operation can be implemented asynchronously or synchronously without dictating to the client how to call it.</span></span> <span data-ttu-id="a58d6-104">Por exemplo, as operações de serviço assíncronas podem ser chamadas de forma síncrona e as operações de serviço síncronas podem ser chamadas assincronamente.</span><span class="sxs-lookup"><span data-stu-id="a58d6-104">For example, asynchronous service operations can be called synchronously, and synchronous service operations can be called asynchronously.</span></span> <span data-ttu-id="a58d6-105">Para obter um exemplo que mostra como chamar uma operação de forma assíncrona em um aplicativo cliente, consulte [como: chamar operações de serviço de forma assíncrona](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="a58d6-105">For an example that shows how to call an operation asynchronously in a client application, see [How to: Call Service Operations Asynchronously](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span> <span data-ttu-id="a58d6-106">Para obter mais informações sobre operações síncronas e assíncronas, consulte [Criando contratos de serviço](designing-service-contracts.md) e operações síncronas [e assíncronas](synchronous-and-asynchronous-operations.md).</span><span class="sxs-lookup"><span data-stu-id="a58d6-106">For more information about synchronous and asynchronous operations, see [Designing Service Contracts](designing-service-contracts.md) and [Synchronous and Asynchronous Operations](synchronous-and-asynchronous-operations.md).</span></span> <span data-ttu-id="a58d6-107">Este tópico descreve a estrutura básica de uma operação de serviço assíncrona, o código não está completo.</span><span class="sxs-lookup"><span data-stu-id="a58d6-107">This topic describes the basic structure of an asynchronous service operation, the code is not complete.</span></span> <span data-ttu-id="a58d6-108">Para obter um exemplo completo dos lados do serviço e do cliente, consulte [assíncrono](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms751505(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a58d6-108">For a complete example of both the service and client sides, see [Asynchronous](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms751505(v=vs.100)).</span></span>  
  
### <a name="implement-a-service-operation-asynchronously"></a><span data-ttu-id="a58d6-109">Implementar uma operação de serviço de forma assíncrona</span><span class="sxs-lookup"><span data-stu-id="a58d6-109">Implement a service operation asynchronously</span></span>  
  
1. <span data-ttu-id="a58d6-110">Em seu contrato de serviço, declare um par de métodos assíncronos de acordo com as diretrizes de design assíncrono do .NET.</span><span class="sxs-lookup"><span data-stu-id="a58d6-110">In your service contract, declare an asynchronous method pair according to the .NET asynchronous design guidelines.</span></span> <span data-ttu-id="a58d6-111">O método `Begin` usa um parâmetro, um objeto de retorno de chamada e um objeto de estado e retorna um <xref:System.IAsyncResult?displayProperty=nameWithType> e um método `End` correspondente que usa um <xref:System.IAsyncResult?displayProperty=nameWithType> e retorna o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="a58d6-111">The `Begin` method takes a parameter, a callback object, and a state object, and returns a <xref:System.IAsyncResult?displayProperty=nameWithType> and a matching `End` method that takes a <xref:System.IAsyncResult?displayProperty=nameWithType> and returns the return value.</span></span> <span data-ttu-id="a58d6-112">Para obter mais informações sobre chamadas assíncronas, consulte [padrões de design de programação assíncrona](../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span><span class="sxs-lookup"><span data-stu-id="a58d6-112">For more information about asynchronous calls, see [Asynchronous Programming Design Patterns](../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span></span>  
  
2. <span data-ttu-id="a58d6-113">Marque o método `Begin` do par método assíncrono com o atributo <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> e defina a propriedade <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> como `true`.</span><span class="sxs-lookup"><span data-stu-id="a58d6-113">Mark the `Begin` method of the asynchronous method pair with the <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> attribute and set the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="a58d6-114">Por exemplo, o código a seguir executa as etapas 1 e 2.</span><span class="sxs-lookup"><span data-stu-id="a58d6-114">For example, the following code performs steps 1 and 2.</span></span>  
  
     [!code-csharp[C_SyncAsyncClient#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#6)]
     [!code-vb[C_SyncAsyncClient#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#6)]  
  
3. <span data-ttu-id="a58d6-115">Implemente o par de método `Begin/End` em sua classe de serviço de acordo com as diretrizes de design assíncronas.</span><span class="sxs-lookup"><span data-stu-id="a58d6-115">Implement the `Begin/End` method pair in your service class according to the asynchronous design guidelines.</span></span> <span data-ttu-id="a58d6-116">Por exemplo, o exemplo de código a seguir mostra uma implementação na qual uma cadeia de caracteres é gravada no console do nas partes `Begin` e `End` da operação de serviço assíncrona e o valor de retorno da operação de `End` é retornado ao cliente.</span><span class="sxs-lookup"><span data-stu-id="a58d6-116">For example, the following code example shows an implementation in which a string is written to the console in both the `Begin` and `End` portions of the asynchronous service operation, and the return value of the `End` operation is returned to the client.</span></span> <span data-ttu-id="a58d6-117">Para obter o exemplo de código completo, consulte a seção de exemplo.</span><span class="sxs-lookup"><span data-stu-id="a58d6-117">For the complete code example, see the Example section.</span></span>  
  
     [!code-csharp[C_SyncAsyncClient#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#3)]
     [!code-vb[C_SyncAsyncClient#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="a58d6-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a58d6-118">Example</span></span>  
 <span data-ttu-id="a58d6-119">Os exemplos de código a seguir mostram:</span><span class="sxs-lookup"><span data-stu-id="a58d6-119">The following code examples show:</span></span>  
  
1. <span data-ttu-id="a58d6-120">Uma interface de contrato de serviço com:</span><span class="sxs-lookup"><span data-stu-id="a58d6-120">A service contract interface with:</span></span>  
  
    1. <span data-ttu-id="a58d6-121">Uma operação de `SampleMethod` síncrona.</span><span class="sxs-lookup"><span data-stu-id="a58d6-121">A synchronous `SampleMethod` operation.</span></span>  
  
    2. <span data-ttu-id="a58d6-122">Uma operação de `BeginSampleMethod` assíncrona.</span><span class="sxs-lookup"><span data-stu-id="a58d6-122">An asynchronous `BeginSampleMethod` operation.</span></span>  
  
    3. <span data-ttu-id="a58d6-123">Um par de operações `BeginServiceAsyncMethod`/`EndServiceAsyncMethod` assíncrona.</span><span class="sxs-lookup"><span data-stu-id="a58d6-123">An asynchronous `BeginServiceAsyncMethod`/`EndServiceAsyncMethod` operation pair.</span></span>  
  
2. <span data-ttu-id="a58d6-124">Uma implementação de serviço usando um objeto <xref:System.IAsyncResult?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a58d6-124">A service implementation using a <xref:System.IAsyncResult?displayProperty=nameWithType> object.</span></span>  
  
 [!code-csharp[C_SyncAsyncClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#1)]
 [!code-vb[C_SyncAsyncClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a58d6-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a58d6-125">See also</span></span>

- [<span data-ttu-id="a58d6-126">Criando contratos de serviço</span><span class="sxs-lookup"><span data-stu-id="a58d6-126">Designing Service Contracts</span></span>](designing-service-contracts.md)
- [<span data-ttu-id="a58d6-127">Operações síncronas e assíncronas</span><span class="sxs-lookup"><span data-stu-id="a58d6-127">Synchronous and Asynchronous Operations</span></span>](synchronous-and-asynchronous-operations.md)
