---
title: "Como implementar uma operação de serviço assíncrona"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 4e5d2ea5-d8f8-4712-bd18-ea3c5461702c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cd208cf361b78da7f755bbe77070d440fe07b4ac
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-implement-an-asynchronous-service-operation"></a><span data-ttu-id="628a5-102">Como implementar uma operação de serviço assíncrona</span><span class="sxs-lookup"><span data-stu-id="628a5-102">How to: Implement an Asynchronous Service Operation</span></span>
<span data-ttu-id="628a5-103">Em [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] aplicativos, uma operação de serviço podem ser implementados assíncrona ou síncrona sem ditando ao cliente como chamá-lo.</span><span class="sxs-lookup"><span data-stu-id="628a5-103">In [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] applications, a service operation can be implemented asynchronously or synchronously without dictating to the client how to call it.</span></span> <span data-ttu-id="628a5-104">Por exemplo, operações de serviço assíncrona podem chamar sincronamente e operações de serviço síncronas podem ser chamadas de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="628a5-104">For example, asynchronous service operations can be calling synchronously, and synchronous service operations can be called asynchronously.</span></span> <span data-ttu-id="628a5-105">Para obter um exemplo que mostra como chamar uma operação assíncrona em um aplicativo cliente, consulte [como: chamar operações de serviço assíncrona](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="628a5-105">For an example that shows how to call an operation asynchronously in a client application, see [How to: Call Service Operations Asynchronously](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="628a5-106">operações síncronas e assíncronas, consulte [criar contratos de serviço](../../../docs/framework/wcf/designing-service-contracts.md) e [síncrona e operações assíncronas](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span><span class="sxs-lookup"><span data-stu-id="628a5-106"> synchronous and asynchronous operations, see [Designing Service Contracts](../../../docs/framework/wcf/designing-service-contracts.md) and [Synchronous and Asynchronous Operations](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span></span> <span data-ttu-id="628a5-107">Este tópico descreve a estrutura básica de uma operação de serviço assíncrona, o código não está completo.</span><span class="sxs-lookup"><span data-stu-id="628a5-107">This topic describes the basic structure of an asynchronous service operation, the code is not complete.</span></span> <span data-ttu-id="628a5-108">Para um exemplo completo de cliente e serviço consulte [assíncrona](http://msdn.microsoft.com/en-us/833db946-f511-4f64-a26f-2759a11217c7).</span><span class="sxs-lookup"><span data-stu-id="628a5-108">For a complete example of both the service and client sides see [Asynchronous](http://msdn.microsoft.com/en-us/833db946-f511-4f64-a26f-2759a11217c7).</span></span>  
  
### <a name="implement-a-service-operation-asynchronously"></a><span data-ttu-id="628a5-109">Implementar uma operação de serviço de forma assíncrona</span><span class="sxs-lookup"><span data-stu-id="628a5-109">Implement a service operation asynchronously</span></span>  
  
1.  <span data-ttu-id="628a5-110">No seu contrato de serviço, declare um par de método assíncrono, de acordo com as diretrizes de design assíncronos .NET.</span><span class="sxs-lookup"><span data-stu-id="628a5-110">In your service contract, declare an asynchronous method pair according to the .NET asynchronous design guidelines.</span></span> <span data-ttu-id="628a5-111">O `Begin` método utiliza um parâmetro, um objeto de retorno de chamada e um objeto de estado e retorna um <xref:System.IAsyncResult?displayProperty=nameWithType> uma correspondência e `End` método que utiliza um <xref:System.IAsyncResult?displayProperty=nameWithType> e retorna o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="628a5-111">The `Begin` method takes a parameter, a callback object, and a state object, and returns a <xref:System.IAsyncResult?displayProperty=nameWithType> and a matching `End` method that takes a <xref:System.IAsyncResult?displayProperty=nameWithType> and returns the return value.</span></span> <span data-ttu-id="628a5-112">Para obter mais informações sobre as chamadas assíncronas, consulte [padrões de Design de programação assíncrona](http://go.microsoft.com/fwlink/?LinkId=248221).</span><span class="sxs-lookup"><span data-stu-id="628a5-112">For more information about asynchronous calls, see [Asynchronous Programming Design Patterns](http://go.microsoft.com/fwlink/?LinkId=248221).</span></span>  
  
2.  <span data-ttu-id="628a5-113">Marca o `Begin` método do par de método assíncrono com o <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> de atributo e definir o <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="628a5-113">Mark the `Begin` method of the asynchronous method pair with the <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> attribute and set the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="628a5-114">Por exemplo, o código a seguir executa as etapas 1 e 2.</span><span class="sxs-lookup"><span data-stu-id="628a5-114">For example, the following code performs steps 1 and 2.</span></span>  
  
     [!code-csharp[C_SyncAsyncClient#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#6)]
     [!code-vb[C_SyncAsyncClient#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#6)]  
  
3.  <span data-ttu-id="628a5-115">Implementar o `Begin/End` par de métodos em sua classe de serviço de acordo com as diretrizes de design assíncronos.</span><span class="sxs-lookup"><span data-stu-id="628a5-115">Implement the `Begin/End` method pair in your service class according to the asynchronous design guidelines.</span></span> <span data-ttu-id="628a5-116">Por exemplo, o exemplo de código a seguir mostra uma implementação na qual uma cadeia de caracteres é gravada no console em ambos o `Begin` e `End` partes da operação de serviço assíncrona e o valor de retorno a `End` operação retornado ao cliente.</span><span class="sxs-lookup"><span data-stu-id="628a5-116">For example, the following code example shows an implementation in which a string is written to the console in both the `Begin` and `End` portions of the asynchronous service operation, and the return value of the `End` operation is returned to the client.</span></span> <span data-ttu-id="628a5-117">Para o exemplo de código completo, consulte a seção de exemplo.</span><span class="sxs-lookup"><span data-stu-id="628a5-117">For the complete code example, see the Example section.</span></span>  
  
     [!code-csharp[C_SyncAsyncClient#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#3)]
     [!code-vb[C_SyncAsyncClient#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="628a5-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="628a5-118">Example</span></span>  
 <span data-ttu-id="628a5-119">Os exemplos de código a seguir mostram:</span><span class="sxs-lookup"><span data-stu-id="628a5-119">The following code examples show:</span></span>  
  
1.  <span data-ttu-id="628a5-120">Uma interface de contrato de serviço com:</span><span class="sxs-lookup"><span data-stu-id="628a5-120">A service contract interface with:</span></span>  
  
    1.  <span data-ttu-id="628a5-121">Um síncrono `SampleMethod` operação.</span><span class="sxs-lookup"><span data-stu-id="628a5-121">A synchronous `SampleMethod` operation.</span></span>  
  
    2.  <span data-ttu-id="628a5-122">Assíncrona `BeginSampleMethod` operação.</span><span class="sxs-lookup"><span data-stu-id="628a5-122">An asynchronous `BeginSampleMethod` operation.</span></span>  
  
    3.  <span data-ttu-id="628a5-123">Assíncrona `BeginServiceAsyncMethod` / `EndServiceAsyncMethod` par de operação.</span><span class="sxs-lookup"><span data-stu-id="628a5-123">An asynchronous `BeginServiceAsyncMethod`/`EndServiceAsyncMethod` operation pair.</span></span>  
  
2.  <span data-ttu-id="628a5-124">Uma implementação de serviço usando um <xref:System.IAsyncResult?displayProperty=nameWithType> objeto.</span><span class="sxs-lookup"><span data-stu-id="628a5-124">A service implementation using a <xref:System.IAsyncResult?displayProperty=nameWithType> object.</span></span>  
  
 [!code-csharp[C_SyncAsyncClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#1)]
 [!code-vb[C_SyncAsyncClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="628a5-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="628a5-125">See Also</span></span>  
 <span data-ttu-id="628a5-126">[Designing Service Contracts](../../../docs/framework/wcf/designing-service-contracts.md) (Criando contratos de serviço)</span><span class="sxs-lookup"><span data-stu-id="628a5-126">[Designing Service Contracts](../../../docs/framework/wcf/designing-service-contracts.md)</span></span>  
 [<span data-ttu-id="628a5-127">Operações síncronas e assíncronas</span><span class="sxs-lookup"><span data-stu-id="628a5-127">Synchronous and Asynchronous Operations</span></span>](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)
