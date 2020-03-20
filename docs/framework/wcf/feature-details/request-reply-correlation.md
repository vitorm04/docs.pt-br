---
title: Correlação resposta/solicitação
ms.date: 03/30/2017
ms.assetid: cf4379bf-2d08-43f3-9584-dfa30ffcb1f6
ms.openlocfilehash: 34a41a149e740faf0f3816bba2c9bd9b47d4996e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184551"
---
# <a name="request-reply-correlation"></a><span data-ttu-id="9d1aa-102">Correlação resposta/solicitação</span><span class="sxs-lookup"><span data-stu-id="9d1aa-102">Request-Reply Correlation</span></span>
<span data-ttu-id="9d1aa-103">A correlação solicitação-resposta <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> é usada com um par para implementar uma <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> operação bidirecional em um serviço de fluxo de trabalho e com um par que invoca uma operação bidirecional em outro serviço web.</span><span class="sxs-lookup"><span data-stu-id="9d1aa-103">Request-reply correlation is used with a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair to implement a two-way operation in a workflow service and with a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair that invokes a two-way operation in another Web service.</span></span> <span data-ttu-id="9d1aa-104">Ao invocar uma operação bidirecional em um serviço WCF, o serviço pode ser um serviço tradicional baseado em código baseado em código windows communication Foundation (WCF) ou pode ser um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="9d1aa-104">When invoking a two-way operation in a WCF service, the service can be either a traditional imperative code-based Windows Communication Foundation (WCF) service or it can be a workflow service.</span></span> <span data-ttu-id="9d1aa-105">Para usar a correlação solicitação-resposta, deve ser <xref:System.ServiceModel.BasicHttpBinding>utilizada uma vinculação bidirecional, como .</span><span class="sxs-lookup"><span data-stu-id="9d1aa-105">To use request-reply correlation a two-way binding must be used, such as <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="9d1aa-106">Seja invocando ou implementando uma operação bidirecional, as etapas de inicialização da correlação são semelhantes e são cobertas nesta seção.</span><span class="sxs-lookup"><span data-stu-id="9d1aa-106">Whether invoking or implementing a two-way operation, the correlation initialization steps are similar and are covered in this section.</span></span>  
  
## <a name="using-correlation-in-a-two-way-operation-with-receivesendreply"></a><span data-ttu-id="9d1aa-107">Usando correlação em uma operação bidirecional com receber/enviar resposta</span><span class="sxs-lookup"><span data-stu-id="9d1aa-107">Using Correlation in a Two-Way Operation with Receive/SendReply</span></span>  
 <span data-ttu-id="9d1aa-108"><xref:System.ServiceModel.Activities.Receive> / Um <xref:System.ServiceModel.Activities.SendReply> par é usado para implementar uma operação bidirecional em um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="9d1aa-108">A <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is used to implement a two-way operation in a workflow service.</span></span> <span data-ttu-id="9d1aa-109">O tempo de execução usa correlação solicitação-resposta para garantir que a resposta seja enviada ao chamador correto.</span><span class="sxs-lookup"><span data-stu-id="9d1aa-109">The runtime uses request-reply correlation to ensure that the reply is dispatched to the correct caller.</span></span> <span data-ttu-id="9d1aa-110">Quando um fluxo de <xref:System.ServiceModel.Activities.WorkflowServiceHost>trabalho é hospedado usando , que é o caso dos serviços de fluxo de trabalho, então a inicialização da correlação padrão é suficiente.</span><span class="sxs-lookup"><span data-stu-id="9d1aa-110">When a workflow is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>, which is the case for workflow services, then the default correlation initialization is sufficient.</span></span> <span data-ttu-id="9d1aa-111">Neste cenário, <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> um par é usado por um fluxo de trabalho, e nenhuma configuração de correlação específica é necessária.</span><span class="sxs-lookup"><span data-stu-id="9d1aa-111">In this scenario, a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is used by a workflow, and no specific correlation configuration is required.</span></span>  
  
```csharp  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder"  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
// Construct a workflow using StartOrder and ReplyToStartOrder.  
```  
  
### <a name="explicitly-initializing-request-reply-correlation"></a><span data-ttu-id="9d1aa-112">Inicializando explicitamente a correlação solicitação-resposta</span><span class="sxs-lookup"><span data-stu-id="9d1aa-112">Explicitly Initializing Request-Reply Correlation</span></span>  
 <span data-ttu-id="9d1aa-113">Se outras operações bidirecionais estiverem em paralelo, então a correlação deve ser explicitamente configurada.</span><span class="sxs-lookup"><span data-stu-id="9d1aa-113">If other two-way operations are in parallel, then correlation should be explicitly configured.</span></span> <span data-ttu-id="9d1aa-114">Isso pode ser feito <xref:System.ServiceModel.Activities.CorrelationHandle> especificando <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>a e <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> , <xref:System.ServiceModel.Activities.CorrelationScope>ou colocando o interior de um .</span><span class="sxs-lookup"><span data-stu-id="9d1aa-114">This can be done by specifying a <xref:System.ServiceModel.Activities.CorrelationHandle> and <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>, or by placing the <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> inside of a <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span> <span data-ttu-id="9d1aa-115">Neste exemplo, a correlação solicitação-resposta <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> é configurada em um par.</span><span class="sxs-lookup"><span data-stu-id="9d1aa-115">In this example, request-reply correlation is configured on a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair.</span></span>  
  
```csharp  
Variable<CorrelationHandle> RRHandle = new Variable<CorrelationHandle>();  
  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder",  
    CorrelationInitializers =  
    {  
        new RequestReplyCorrelationInitializer  
        {  
            CorrelationHandle = RRHandle  
        }  
    }  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
// Construct a workflow using StartOrder and ReplyToStartOrder.  
```  
  
 <span data-ttu-id="9d1aa-116">Em vez de configurar explicitamente <xref:System.ServiceModel.Activities.CorrelationScope> a correlação, uma atividade pode ser usada.</span><span class="sxs-lookup"><span data-stu-id="9d1aa-116">Instead of explicitly configuring the correlation, a <xref:System.ServiceModel.Activities.CorrelationScope> activity can be used.</span></span> <span data-ttu-id="9d1aa-117"><xref:System.ServiceModel.Activities.CorrelationScope>fornece uma <xref:System.ServiceModel.Activities.CorrelationHandle> implícita para as atividades de mensagens que ele contém.</span><span class="sxs-lookup"><span data-stu-id="9d1aa-117"><xref:System.ServiceModel.Activities.CorrelationScope> provides an implicit <xref:System.ServiceModel.Activities.CorrelationHandle> to the messaging activities that it contains.</span></span> <span data-ttu-id="9d1aa-118">Neste exemplo, <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> um par está <xref:System.ServiceModel.Activities.CorrelationScope>contido dentro de um .</span><span class="sxs-lookup"><span data-stu-id="9d1aa-118">In this example, a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is contained inside a <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span> <span data-ttu-id="9d1aa-119">Nenhuma configuração de correlação explícita é necessária.</span><span class="sxs-lookup"><span data-stu-id="9d1aa-119">No explicit correlation configuration is required.</span></span>  
  
```csharp  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder"  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
CorrelationScope s = new CorrelationScope  
{  
    Body = new Sequence  
    {  
        Activities =
        {  
            StartOrder,  
            // Activities that create the reply.  
            ReplyToStartOrder  
        }  
    }  
};  
  
// Construct a workflow using the CorrelationScope.  
```  
  
 <span data-ttu-id="9d1aa-120">Se forem necessárias correlações adicionais, <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> elas podem ser configuradas `CorrelationInitializer` usando a propriedade das respectivas atividades de mensagens usando os tipos desejados.</span><span class="sxs-lookup"><span data-stu-id="9d1aa-120">If additional correlations are required then they can be configured using the <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> property of the respective messaging activities using the desired `CorrelationInitializer` types.</span></span>  
  
## <a name="using-correlation-in-a-two-way-operation-with-sendreceivereply"></a><span data-ttu-id="9d1aa-121">Usando correlação em uma operação bidirecional com enviar/receberresposta</span><span class="sxs-lookup"><span data-stu-id="9d1aa-121">Using Correlation in a Two-Way Operation with Send/ReceiveReply</span></span>  
 <span data-ttu-id="9d1aa-122">Embora <xref:System.ServiceModel.Activities.Receive> a atividade só possa ser usada em <xref:System.ServiceModel.Activities.WorkflowServiceHost> <xref:System.ServiceModel.Activities.Send> um <xref:System.ServiceModel.Activities.Send> / serviço de fluxo de trabalho hospedado por , e o <xref:System.ServiceModel.Activities.ReceiveReply> par pode ser usado em qualquer fluxo de trabalho que deve invocar um método em um serviço web.</span><span class="sxs-lookup"><span data-stu-id="9d1aa-122">While the <xref:System.ServiceModel.Activities.Receive> activity can only be used in a workflow service hosted by <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.ServiceModel.Activities.Send> and the <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair can be used in any workflow that must invoke a method on a Web service.</span></span> <span data-ttu-id="9d1aa-123">Se o fluxo de <xref:System.ServiceModel.Activities.WorkflowServiceHost> trabalho estiver hospedado usando a correlação padrão descrita na seção anterior se aplica, <xref:System.ServiceModel.Activities.CorrelationInitializer> mas <xref:System.ServiceModel.Activities.CorrelationHandle>se não, então a <xref:System.ServiceModel.Activities.CorrelationScope>correlação deve ser configurada explicitamente usando o desejado e , ou usando o gerenciamento implícito da alça do .</span><span class="sxs-lookup"><span data-stu-id="9d1aa-123">If the workflow is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost> then the default correlation described in the previous section applies, but if not, then correlation must be configured either explicitly using the desired <xref:System.ServiceModel.Activities.CorrelationInitializer> and <xref:System.ServiceModel.Activities.CorrelationHandle>, or by using the implicit handle management of the <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span>  
  
 <span data-ttu-id="9d1aa-124">Ao usar **adicionar referência de serviço** em um serviço com <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> operações bidirecionais, são geradas atividades que envolvem uma atividade de par internamente com a correlação Solicitação/Resposta explicitamente especificada.</span><span class="sxs-lookup"><span data-stu-id="9d1aa-124">When using **Add Service Reference** on a service with two-way operations, activities are generated that wrap a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair activity internally with the Request/Reply correlation explicitly specified.</span></span>
