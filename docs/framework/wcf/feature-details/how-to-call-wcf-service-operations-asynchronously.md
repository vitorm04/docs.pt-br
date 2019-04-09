---
title: 'Como: Chamar operações de serviço WCF de forma assíncrona'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
ms.openlocfilehash: 9a7bd1d67d9730c75e3f3f3b1eeb59f5d2d3c49a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59204829"
---
# <a name="how-to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="5a62e-102">Como: Chamar operações de serviço WCF de forma assíncrona</span><span class="sxs-lookup"><span data-stu-id="5a62e-102">How to: Call WCF Service Operations Asynchronously</span></span>
<span data-ttu-id="5a62e-103">Este tópico aborda como um cliente pode acessar uma operação de serviço assincronamente.</span><span class="sxs-lookup"><span data-stu-id="5a62e-103">This topic covers how a client can access a service operation asynchronously.</span></span> <span data-ttu-id="5a62e-104">Implementa o serviço neste tópico o `ICalculator` interface.</span><span class="sxs-lookup"><span data-stu-id="5a62e-104">The service in this topic implements the `ICalculator` interface.</span></span> <span data-ttu-id="5a62e-105">O cliente pode chamar as operações nesta interface de forma assíncrona usando o modelo de chamada assíncrono controlada por evento.</span><span class="sxs-lookup"><span data-stu-id="5a62e-105">The client can call the operations on this interface asynchronously by using the event-driven asynchronous calling model.</span></span> <span data-ttu-id="5a62e-106">(Para obter mais informações sobre o modelo de chamada assíncrono baseado em evento, consulte [programação Multithreaded com o padrão assíncrono baseado em evento](https://go.microsoft.com/fwlink/?LinkId=248184)).</span><span class="sxs-lookup"><span data-stu-id="5a62e-106">(For more information about the event-based asynchronous calling model, see [Multithreaded Programming with the Event-based Asynchronous Pattern](https://go.microsoft.com/fwlink/?LinkId=248184)).</span></span> <span data-ttu-id="5a62e-107">Para obter um exemplo que mostra como implementar uma operação de forma assíncrona em um serviço, consulte [como: Implementar uma operação de serviço assíncrona](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span><span class="sxs-lookup"><span data-stu-id="5a62e-107">For an example that shows how to implement an operation asynchronously in a service, see [How to: Implement an Asynchronous Service Operation](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span></span> <span data-ttu-id="5a62e-108">Para obter mais informações sobre operações síncronas e assíncronas, consulte [síncrona e operações assíncronas](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span><span class="sxs-lookup"><span data-stu-id="5a62e-108">For more information about synchronous and asynchronous operations, see [Synchronous and Asynchronous Operations](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a62e-109">O modelo de chamada assíncrona controlada por evento não é suportado ao usar um <xref:System.ServiceModel.ChannelFactory%601>.</span><span class="sxs-lookup"><span data-stu-id="5a62e-109">The event-driven asynchronous calling model is not supported when using a <xref:System.ServiceModel.ChannelFactory%601>.</span></span> <span data-ttu-id="5a62e-110">Para obter informações sobre como fazer chamadas assíncronas usando o <xref:System.ServiceModel.ChannelFactory%601>, consulte [como: Chamar operações assíncronas usando uma fábrica de canais](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span><span class="sxs-lookup"><span data-stu-id="5a62e-110">For information about making asynchronous calls using the <xref:System.ServiceModel.ChannelFactory%601>, see [How to: Call Operations Asynchronously Using a Channel Factory](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="5a62e-111">Procedimento</span><span class="sxs-lookup"><span data-stu-id="5a62e-111">Procedure</span></span>  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="5a62e-112">Para chamar operações de serviço WCF de forma assíncrona</span><span class="sxs-lookup"><span data-stu-id="5a62e-112">To call WCF service operations asynchronously</span></span>  
  
1.  <span data-ttu-id="5a62e-113">Execute o [ferramenta Utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ferramenta com ambos os `/async` e o `/tcv:Version35` comando opções juntas, conforme mostrado no comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="5a62e-113">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool with both the `/async` and the `/tcv:Version35` command options together as shown in the following command.</span></span>  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     <span data-ttu-id="5a62e-114">Isso gera, além de operações síncronas e padrão com base em delegado assíncronas, uma classe de cliente do WCF que contém:</span><span class="sxs-lookup"><span data-stu-id="5a62e-114">This generates, in addition to the synchronous and standard delegate-based asynchronous operations, a WCF client class that contains:</span></span>  
  
    -   <span data-ttu-id="5a62e-115">Dois <`operationName` > `Async` operações para uso com a abordagem de chamada assíncrono baseado em evento.</span><span class="sxs-lookup"><span data-stu-id="5a62e-115">Two <`operationName`>`Async` operations for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="5a62e-116">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="5a62e-116">For example:</span></span>  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    -   <span data-ttu-id="5a62e-117">Eventos da operação foi concluída no formato <`operationName` > `Completed` para uso com a abordagem de chamada assíncrono baseado em evento.</span><span class="sxs-lookup"><span data-stu-id="5a62e-117">Operation completed events of the form <`operationName`>`Completed` for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="5a62e-118">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="5a62e-118">For example:</span></span>  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    -   <xref:System.EventArgs?displayProperty=nameWithType> <span data-ttu-id="5a62e-119">tipos de cada operação (no formato <`operationName`>`CompletedEventArgs`) para uso com a abordagem de chamada assíncrono baseado em evento.</span><span class="sxs-lookup"><span data-stu-id="5a62e-119">types for each operation (of the form <`operationName`>`CompletedEventArgs`) for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="5a62e-120">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="5a62e-120">For example:</span></span>  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2.  <span data-ttu-id="5a62e-121">No aplicativo de chamada, crie um método de retorno de chamada a ser chamado quando a operação assíncrona for concluída, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="5a62e-121">In the calling application, create a callback method to be called when the asynchronous operation is complete, as shown in the following sample code.</span></span>  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3.  <span data-ttu-id="5a62e-122">Antes de chamar a operação, use um novo genérico <xref:System.EventHandler%601?displayProperty=nameWithType> do tipo <`operationName` > `EventArgs` para adicionar o método do manipulador (criado na etapa anterior) para o <`operationName` > `Completed` eventos.</span><span class="sxs-lookup"><span data-stu-id="5a62e-122">Prior to calling the operation, use a new generic <xref:System.EventHandler%601?displayProperty=nameWithType> of type <`operationName`>`EventArgs` to add the handler method (created in the preceding step) to the <`operationName`>`Completed` event.</span></span> <span data-ttu-id="5a62e-123">Em seguida, chame o <`operationName` > `Async` método.</span><span class="sxs-lookup"><span data-stu-id="5a62e-123">Then call the <`operationName`>`Async` method.</span></span> <span data-ttu-id="5a62e-124">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="5a62e-124">For example:</span></span>  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="5a62e-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a62e-125">Example</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a62e-126">As diretrizes de design do modelo assíncrono baseado em eventos declaram que, se mais de um valor for retornado, um valor será retornado como a propriedade `Result` e os outros serão retornados como propriedades no objeto <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="5a62e-126">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="5a62e-127">Um resultado disso é que, se um cliente importar metadados usando as opções de comando assíncrono baseado em evento e a operação retornar mais de um valor, o padrão <xref:System.EventArgs> objeto retorna um valor como o `Result` são de propriedade e restante Propriedades do <xref:System.EventArgs> objeto. Se você quiser receber o objeto de mensagem como a `Result` propriedade e têm os valores retornados como propriedades nesse objeto, use o `/messageContract` opção de comando.</span><span class="sxs-lookup"><span data-stu-id="5a62e-127">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the `/messageContract` command option.</span></span> <span data-ttu-id="5a62e-128">Isso gera uma assinatura que retorna a mensagem de resposta como a propriedade `Result` no objeto <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="5a62e-128">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="5a62e-129">Todos os valores de retorno internos são propriedades do objeto da mensagem de resposta.</span><span class="sxs-lookup"><span data-stu-id="5a62e-129">All internal return values are then properties of the response message object.</span></span>  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="5a62e-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5a62e-130">See also</span></span>

- [<span data-ttu-id="5a62e-131">Como: implementar uma operação de serviço assíncrona</span><span class="sxs-lookup"><span data-stu-id="5a62e-131">How to: Implement an Asynchronous Service Operation</span></span>](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)
