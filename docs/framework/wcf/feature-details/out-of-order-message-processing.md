---
title: Processamento de mensagem com problema
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33fc62a5-5d59-461c-a37a-0e1b51ac763d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 19ab5afbc1eb13a3126e94a040d51204fea131a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="out-of-order-message-processing"></a><span data-ttu-id="a7875-102">Processamento de mensagem com problema</span><span class="sxs-lookup"><span data-stu-id="a7875-102">Out-of-Order Message Processing</span></span>
<span data-ttu-id="a7875-103">Serviços de fluxo de trabalho podem depender de mensagens enviadas em uma ordem específica.</span><span class="sxs-lookup"><span data-stu-id="a7875-103">Workflow services may depend on messages being sent in a specific order.</span></span> <span data-ttu-id="a7875-104">Um serviço de fluxo de trabalho contém um ou mais <xref:System.ServiceModel.Activities.Receive> atividades e cada <xref:System.ServiceModel.Activities.Receive> atividade está esperando uma mensagem específica.</span><span class="sxs-lookup"><span data-stu-id="a7875-104">A workflow service contains one or more <xref:System.ServiceModel.Activities.Receive> activities and each <xref:System.ServiceModel.Activities.Receive> activity is expecting a specific message.</span></span> <span data-ttu-id="a7875-105">Sem garantias de entrega de transporte particular, as mensagens enviadas por clientes podem ser atrasadas e portanto entregues em uma ordem não pode esperar que o serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="a7875-105">Without particular transport delivery guarantees, messages sent by clients may be delayed and therefore delivered in an order the workflow service may not expect.</span></span> <span data-ttu-id="a7875-106">Implementar um serviço de fluxo de trabalho que não exige que as mensagens enviadas em uma determinada ordem normalmente é feita usando uma atividade paralela.</span><span class="sxs-lookup"><span data-stu-id="a7875-106">Implementing a workflow service that does not require messages be sent in a specific order is normally done using a Parallel activity.</span></span> <span data-ttu-id="a7875-107">Para um protocolo de aplicativo mais complicado, o fluxo de trabalho deve se tornar muito complexo muito rapidamente.</span><span class="sxs-lookup"><span data-stu-id="a7875-107">For a more complicated application protocol, the workflow would become very complex very quickly.</span></span>  <span data-ttu-id="a7875-108">O recurso de processamento de mensagens de fora de ordem no [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] permite que você crie um fluxo de trabalho sem toda a complexidade de atividades paralelas aninhadas.</span><span class="sxs-lookup"><span data-stu-id="a7875-108">The out-of-order message processing feature in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] allows you to create such a workflow without all of the complexity of nested Parallel activities.</span></span> <span data-ttu-id="a7875-109">Só há suporte para o processamento de mensagens de fora de ordem nos canais que oferecem suporte a <xref:System.ServiceModel.Channels.ReceiveContext> , como o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] associações do MSMQ.</span><span class="sxs-lookup"><span data-stu-id="a7875-109">Out-of-order message processing is only supported on channels that support <xref:System.ServiceModel.Channels.ReceiveContext> such as the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] MSMQ bindings.</span></span>  
  
## <a name="enabling-out-of-order-message-processing"></a><span data-ttu-id="a7875-110">Habilitando o processamento de mensagens de fora de ordem</span><span class="sxs-lookup"><span data-stu-id="a7875-110">Enabling Out-Of-Order Message Processing</span></span>  
 <span data-ttu-id="a7875-111">Processamento de mensagens de fora de ordem é habilitado definindo o <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> propriedade `true` no WorkflowService.</span><span class="sxs-lookup"><span data-stu-id="a7875-111">Out-of-order message processing is enabled by setting the <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> property to `true` on the WorkflowService.</span></span> <span data-ttu-id="a7875-112">O exemplo a seguir mostra como definir o <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> propriedade no código.</span><span class="sxs-lookup"><span data-stu-id="a7875-112">The following example shows how to set the <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> property in code.</span></span>  
  
```csharp  
// Code: Opt-in to Buffered Receive processing...  
WorkflowService service = new WorkflowService  
{  
    Name="MyService",  
    Body = workflow,  
    AllowBufferedReceive = true  
};  
```  
  
 <span data-ttu-id="a7875-113">Você também pode aplicar o `AllowBufferedReceive` atributo para um serviço de fluxo de trabalho em XAML, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="a7875-113">You can also apply the `AllowBufferedReceive` attribute to a workflow service in XAML as shown in the following example.</span></span>  
  
```xaml  
// Xaml: Opt-in to Buffered Receive processing...  
<WorkflowService AllowBufferedReceive="True">  
   <!—the actual children activities -->  
</Sequence>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a7875-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7875-114">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ReceiveContext>  
 [<span data-ttu-id="a7875-115">Serviços de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="a7875-115">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="a7875-116">Sessões confiáveis e filas</span><span class="sxs-lookup"><span data-stu-id="a7875-116">Queues and Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)
