---
title: Processamento de mensagem com problema
ms.date: 03/30/2017
ms.assetid: 33fc62a5-5d59-461c-a37a-0e1b51ac763d
ms.openlocfilehash: 7930f26cf5957158a16d65085267cf1bab2e4504
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598717"
---
# <a name="out-of-order-message-processing"></a><span data-ttu-id="d0d3d-102">Processamento de mensagem com problema</span><span class="sxs-lookup"><span data-stu-id="d0d3d-102">Out-of-Order Message Processing</span></span>
<span data-ttu-id="d0d3d-103">Os serviços de fluxo de trabalho podem depender de mensagens sendo enviadas em uma ordem específica.</span><span class="sxs-lookup"><span data-stu-id="d0d3d-103">Workflow services may depend on messages being sent in a specific order.</span></span> <span data-ttu-id="d0d3d-104">Um serviço de fluxo de trabalho contém uma ou mais <xref:System.ServiceModel.Activities.Receive> atividades e cada <xref:System.ServiceModel.Activities.Receive> atividade está esperando uma mensagem específica.</span><span class="sxs-lookup"><span data-stu-id="d0d3d-104">A workflow service contains one or more <xref:System.ServiceModel.Activities.Receive> activities and each <xref:System.ServiceModel.Activities.Receive> activity is expecting a specific message.</span></span> <span data-ttu-id="d0d3d-105">Sem garantias de entrega de transporte específicas, as mensagens enviadas pelos clientes podem ser atrasadas e, portanto, entregues em uma ordem o serviço de fluxo de trabalho pode não esperar.</span><span class="sxs-lookup"><span data-stu-id="d0d3d-105">Without particular transport delivery guarantees, messages sent by clients may be delayed and therefore delivered in an order the workflow service may not expect.</span></span> <span data-ttu-id="d0d3d-106">A implementação de um serviço de fluxo de trabalho que não requer mensagens enviadas em uma ordem específica normalmente é feita usando uma atividade paralela.</span><span class="sxs-lookup"><span data-stu-id="d0d3d-106">Implementing a workflow service that does not require messages be sent in a specific order is normally done using a Parallel activity.</span></span> <span data-ttu-id="d0d3d-107">Para um protocolo de aplicativo mais complicado, o fluxo de trabalho se tornaria muito complexo muito rapidamente.</span><span class="sxs-lookup"><span data-stu-id="d0d3d-107">For a more complicated application protocol, the workflow would become very complex very quickly.</span></span>  <span data-ttu-id="d0d3d-108">O recurso de processamento de mensagens fora de ordem no Windows Communication Foundation (WCF) permite que você crie um fluxo de trabalho sem toda a complexidade de atividades paralelas aninhadas.</span><span class="sxs-lookup"><span data-stu-id="d0d3d-108">The out-of-order message processing feature in Windows Communication Foundation (WCF) allows you to create such a workflow without all of the complexity of nested Parallel activities.</span></span> <span data-ttu-id="d0d3d-109">O processamento de mensagens fora de ordem tem suporte apenas em canais que dão suporte como <xref:System.ServiceModel.Channels.ReceiveContext> associações MSMQ do WCF.</span><span class="sxs-lookup"><span data-stu-id="d0d3d-109">Out-of-order message processing is only supported on channels that support <xref:System.ServiceModel.Channels.ReceiveContext> such as the WCF MSMQ bindings.</span></span>  
  
## <a name="enabling-out-of-order-message-processing"></a><span data-ttu-id="d0d3d-110">Habilitando o processamento de mensagens fora de ordem</span><span class="sxs-lookup"><span data-stu-id="d0d3d-110">Enabling Out-Of-Order Message Processing</span></span>  
 <span data-ttu-id="d0d3d-111">O processamento de mensagens fora de ordem é habilitado pela definição da <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> propriedade como `true` no WorkflowService.</span><span class="sxs-lookup"><span data-stu-id="d0d3d-111">Out-of-order message processing is enabled by setting the <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> property to `true` on the WorkflowService.</span></span> <span data-ttu-id="d0d3d-112">O exemplo a seguir mostra como definir a <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> propriedade no código.</span><span class="sxs-lookup"><span data-stu-id="d0d3d-112">The following example shows how to set the <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> property in code.</span></span>  
  
```csharp  
// Code: Opt-in to Buffered Receive processing...  
WorkflowService service = new WorkflowService  
{  
    Name="MyService",  
    Body = workflow,  
    AllowBufferedReceive = true  
};  
```  
  
 <span data-ttu-id="d0d3d-113">Você também pode aplicar o `AllowBufferedReceive` atributo a um serviço de fluxo de trabalho em XAML, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="d0d3d-113">You can also apply the `AllowBufferedReceive` attribute to a workflow service in XAML as shown in the following example.</span></span>  
  
```xaml  
// Xaml: Opt-in to Buffered Receive processing...  
<WorkflowService AllowBufferedReceive="True">  
   <!--the actual children activities -->  
</Sequence>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d0d3d-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0d3d-114">See also</span></span>

- <xref:System.ServiceModel.Channels.ReceiveContext>
- [<span data-ttu-id="d0d3d-115">Serviços de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="d0d3d-115">Workflow Services</span></span>](workflow-services.md)
- [<span data-ttu-id="d0d3d-116">Sessões confiáveis e filas</span><span class="sxs-lookup"><span data-stu-id="d0d3d-116">Queues and Reliable Sessions</span></span>](queues-and-reliable-sessions.md)
