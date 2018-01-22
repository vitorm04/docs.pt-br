---
title: "Como chamar operações assíncronas usando uma fábrica de canais"
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
ms.assetid: cc17dd47-b9ad-451c-a362-e36e0aac7ba0
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 216c0d529a15004ea9f7d6f087aeee4bf4f10e56
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-call-operations-asynchronously-using-a-channel-factory"></a><span data-ttu-id="5670d-102">Como chamar operações assíncronas usando uma fábrica de canais</span><span class="sxs-lookup"><span data-stu-id="5670d-102">How to: Call Operations Asynchronously Using a Channel Factory</span></span>
<span data-ttu-id="5670d-103">Este tópico aborda como um cliente pode acessar uma operação de serviço assíncrona usando um <xref:System.ServiceModel.ChannelFactory%601>-com base em aplicativos cliente.</span><span class="sxs-lookup"><span data-stu-id="5670d-103">This topic covers how a client can access a service operation asynchronously when using a <xref:System.ServiceModel.ChannelFactory%601>-based client application.</span></span> <span data-ttu-id="5670d-104">(Ao usar um <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> objeto invocar um serviço que você pode usar o modelo de chamada assíncrono controlada por evento.</span><span class="sxs-lookup"><span data-stu-id="5670d-104">(When using a <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> object to invoke a service you can use the event-driven asynchronous calling model.</span></span> <span data-ttu-id="5670d-105">Para obter mais informações, consulte [como: chamar operações de serviço assíncrona](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="5670d-105">For more information, see [How to: Call Service Operations Asynchronously](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span> <span data-ttu-id="5670d-106">Para obter mais informações sobre o modelo de chamada assíncrono baseado em evento, consulte [programação Multithreaded com o padrão assíncrono baseado em evento](../../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md).)</span><span class="sxs-lookup"><span data-stu-id="5670d-106">For more information about the event-based asynchronous calling model, see [Multithreaded Programming with the Event-based Asynchronous Pattern](../../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md).)</span></span>  
  
 <span data-ttu-id="5670d-107">O serviço neste tópico implementa o `ICalculator` interface.</span><span class="sxs-lookup"><span data-stu-id="5670d-107">The service in this topic implements the `ICalculator` interface.</span></span> <span data-ttu-id="5670d-108">O cliente pode chamar as operações nesta interface de forma assíncrona, o que significa que as operações como `Add` são divididas em dois métodos, `BeginAdd` e `EndAdd`, o primeiro deles inicia a chamada e o último recupera o resultado Quando a operação for concluída.</span><span class="sxs-lookup"><span data-stu-id="5670d-108">The client can call the operations on this interface asynchronously, which means that operations like `Add` are split into two methods, `BeginAdd` and `EndAdd`, the former of which initiates the call and the latter of which retrieves the result when the operation completes.</span></span> <span data-ttu-id="5670d-109">Para obter um exemplo mostrando como implementar uma operação assíncrona em um serviço, consulte [como: implementar uma operação assíncrona do serviço](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span><span class="sxs-lookup"><span data-stu-id="5670d-109">For an example showing how to implement an operation asynchronously in a service, see [How to: Implement an Asynchronous Service Operation](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span></span> <span data-ttu-id="5670d-110">Para obter detalhes sobre operações síncronas e assíncronas, consulte [síncrona e operações assíncronas](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span><span class="sxs-lookup"><span data-stu-id="5670d-110">For details about synchronous and asynchronous operations, see [Synchronous and Asynchronous Operations](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="5670d-111">Procedimento</span><span class="sxs-lookup"><span data-stu-id="5670d-111">Procedure</span></span>  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="5670d-112">Para chamar operações de serviço WCF de forma assíncrona</span><span class="sxs-lookup"><span data-stu-id="5670d-112">To call WCF service operations asynchronously</span></span>  
  
1.  <span data-ttu-id="5670d-113">Execute o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ferramenta com o `/async` opção conforme mostrado no comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="5670d-113">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool with the `/async` option as shown in the following command.</span></span>  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a  
    ```  
  
     <span data-ttu-id="5670d-114">Isso gera uma versão de cliente assíncrono do contrato de serviço para a operação.</span><span class="sxs-lookup"><span data-stu-id="5670d-114">This generates an asynchronous client version of the service contract for the operation.</span></span>  
  
2.  <span data-ttu-id="5670d-115">Crie uma função de retorno de chamada a ser chamado quando a operação assíncrona é concluída, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="5670d-115">Create a callback function to be called when the asynchronous operation is complete, as shown in the following sample code.</span></span>  
  
     [!code-csharp[C_How_To_CF_Async#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#2)]
     [!code-vb[C_How_To_CF_Async#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#2)]  
  
3.  <span data-ttu-id="5670d-116">Para acessar uma operação de serviço de forma assíncrona, criar o cliente e chamar o `Begin[Operation]` (por exemplo, `BeginAdd`) e especifique uma função de retorno de chamada, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="5670d-116">To access a service operation asynchronously, create the client and call the `Begin[Operation]` (for example, `BeginAdd`) and specify a callback function, as shown in the following sample code.</span></span>  
  
     [!code-csharp[C_How_To_CF_Async#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#3)]
     [!code-vb[C_How_To_CF_Async#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#3)]  
  
     <span data-ttu-id="5670d-117">Quando a função de retorno de chamada é executado, o cliente chama `End<operation>` (por exemplo, `EndAdd`) para recuperar o resultado.</span><span class="sxs-lookup"><span data-stu-id="5670d-117">When the callback function executes, the client calls `End<operation>` (for example, `EndAdd`) to retrieve the result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5670d-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5670d-118">Example</span></span>  
 <span data-ttu-id="5670d-119">O serviço que é usado com o código de cliente que é usado no procedimento anterior implementa o `ICalculator` interface conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="5670d-119">The service that is used with the client code that is used in the preceding procedure implements the `ICalculator` interface as shown in the following code.</span></span> <span data-ttu-id="5670d-120">No lado do serviço, o `Add` e `Subtract` operações do contrato são chamadas de forma síncrona pelo [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] tempo de execução, mesmo que as etapas anteriores do cliente são chamadas de maneira assíncrona no cliente.</span><span class="sxs-lookup"><span data-stu-id="5670d-120">On the service side, the `Add` and `Subtract` operations of the contract are invoked synchronously by the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] run time, even though the preceding client steps are invoked asynchronously on the client.</span></span> <span data-ttu-id="5670d-121">O `Multiply` e `Divide` operações são usadas para chamar o serviço de forma assíncrona no lado do serviço, mesmo se o cliente chama sincronicamente.</span><span class="sxs-lookup"><span data-stu-id="5670d-121">The `Multiply` and `Divide` operations are used to invoke the service asynchronously on the service side, even if the client invokes them synchronously.</span></span> <span data-ttu-id="5670d-122">Este exemplo define o <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="5670d-122">This example sets the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property to `true`.</span></span> <span data-ttu-id="5670d-123">Essa configuração de propriedade, em combinação com a implementação de [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] padrão assíncrono, indica o tempo de execução para invocar a operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="5670d-123">This property setting, in combination with the implementation of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] asynchronous pattern, tells the run time to invoke the operation asynchronously.</span></span>  
  
 [!code-csharp[C_How_To_CF_Async#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/service.cs#4)]
 [!code-vb[C_How_To_CF_Async#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/service.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="5670d-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5670d-124">See Also</span></span>  
 [<span data-ttu-id="5670d-125">Contrato de serviço: Exemplo de assíncrono</span><span class="sxs-lookup"><span data-stu-id="5670d-125">Service Contract: Asynchronous Sample</span></span>](http://msdn.microsoft.com/library/833db946-f511-4f64-a26f-2759a11217c7)
