---
title: Correlação resposta/solicitação
ms.date: 03/30/2017
ms.assetid: cf4379bf-2d08-43f3-9584-dfa30ffcb1f6
ms.openlocfilehash: c38854ad42ad4dddce5171482f3ddcfe5bd16b61
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991127"
---
# <a name="request-reply-correlation"></a><span data-ttu-id="f35eb-102">Correlação resposta/solicitação</span><span class="sxs-lookup"><span data-stu-id="f35eb-102">Request-Reply Correlation</span></span>
<span data-ttu-id="f35eb-103">Correlação de solicitação-resposta é usada com um <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> par para implementar uma operação bidirecional em um serviço de fluxo de trabalho e com um <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> par que chama uma operação bidirecional em outra Web serviço.</span><span class="sxs-lookup"><span data-stu-id="f35eb-103">Request-reply correlation is used with a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair to implement a two-way operation in a workflow service and with a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair that invokes a two-way operation in another Web service.</span></span> <span data-ttu-id="f35eb-104">Ao invocar uma operação bidirecional em um serviço WCF, o serviço pode ser qualquer um tradicional serviço Windows Communication Foundation (WCF) código imperativo, ou ele pode ser um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="f35eb-104">When invoking a two-way operation in a WCF service, the service can be either a traditional imperative code-based Windows Communication Foundation (WCF) service or it can be a workflow service.</span></span> <span data-ttu-id="f35eb-105">Para usar uma associação bidirecional forem usada, como de correlação de solicitação-resposta <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="f35eb-105">To use request-reply correlation a two-way binding must be used, such as <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="f35eb-106">Se invocar ou implementar uma operação bidirecional, as etapas de inicialização de correlação são semelhantes e são abordadas nesta seção.</span><span class="sxs-lookup"><span data-stu-id="f35eb-106">Whether invoking or implementing a two-way operation, the correlation initialization steps are similar and are covered in this section.</span></span>  
  
## <a name="using-correlation-in-a-two-way-operation-with-receivesendreply"></a><span data-ttu-id="f35eb-107">Uso de correlação em uma operação bidirecional com receber/SendReply</span><span class="sxs-lookup"><span data-stu-id="f35eb-107">Using Correlation in a Two-Way Operation with Receive/SendReply</span></span>  
 <span data-ttu-id="f35eb-108">Um <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> par é usado para implementar uma operação bidirecional em um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="f35eb-108">A <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is used to implement a two-way operation in a workflow service.</span></span> <span data-ttu-id="f35eb-109">O tempo de execução usa correlação de solicitação-resposta para garantir que a resposta é expedida para o chamador correto.</span><span class="sxs-lookup"><span data-stu-id="f35eb-109">The runtime uses request-reply correlation to ensure that the reply is dispatched to the correct caller.</span></span> <span data-ttu-id="f35eb-110">Quando um fluxo de trabalho é hospedado usando <xref:System.ServiceModel.Activities.WorkflowServiceHost>, que é o caso para serviços de fluxo de trabalho e, em seguida, a inicialização de correlação padrão é suficiente.</span><span class="sxs-lookup"><span data-stu-id="f35eb-110">When a workflow is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>, which is the case for workflow services, then the default correlation initialization is sufficient.</span></span> <span data-ttu-id="f35eb-111">Nesse cenário, uma <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> par é usado por um fluxo de trabalho, e nenhuma configuração de correlação específica é necessária.</span><span class="sxs-lookup"><span data-stu-id="f35eb-111">In this scenario, a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is used by a workflow, and no specific correlation configuration is required.</span></span>  
  
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
  
### <a name="explicitly-initializing-request-reply-correlation"></a><span data-ttu-id="f35eb-112">Inicializar explicitamente a correlação de solicitação-resposta</span><span class="sxs-lookup"><span data-stu-id="f35eb-112">Explicitly Initializing Request-Reply Correlation</span></span>  
 <span data-ttu-id="f35eb-113">Se outras operações bidirecionais estiverem em paralelo, em seguida, correlação deve ser configurada explicitamente.</span><span class="sxs-lookup"><span data-stu-id="f35eb-113">If other two-way operations are in parallel, then correlation should be explicitly configured.</span></span> <span data-ttu-id="f35eb-114">Isso pode ser feito especificando uma <xref:System.ServiceModel.Activities.CorrelationHandle> e <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>, ou colocando o <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> dentro de um <xref:System.ServiceModel.Activities.CorrelationScope>.</span><span class="sxs-lookup"><span data-stu-id="f35eb-114">This can be done by specifying a <xref:System.ServiceModel.Activities.CorrelationHandle> and <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>, or by placing the <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> inside of a <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span> <span data-ttu-id="f35eb-115">Neste exemplo, a correlação de solicitação-resposta é configurada em um <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> par.</span><span class="sxs-lookup"><span data-stu-id="f35eb-115">In this example, request-reply correlation is configured on a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair.</span></span>  
  
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
  
 <span data-ttu-id="f35eb-116">Em vez de definir explicitamente a correlação, um <xref:System.ServiceModel.Activities.CorrelationScope> atividade pode ser usada.</span><span class="sxs-lookup"><span data-stu-id="f35eb-116">Instead of explicitly configuring the correlation, a <xref:System.ServiceModel.Activities.CorrelationScope> activity can be used.</span></span> <span data-ttu-id="f35eb-117"><xref:System.ServiceModel.Activities.CorrelationScope> Fornece um implícita <xref:System.ServiceModel.Activities.CorrelationHandle> para as atividades de mensagem que ele contém.</span><span class="sxs-lookup"><span data-stu-id="f35eb-117"><xref:System.ServiceModel.Activities.CorrelationScope> provides an implicit <xref:System.ServiceModel.Activities.CorrelationHandle> to the messaging activities that it contains.</span></span> <span data-ttu-id="f35eb-118">Neste exemplo, uma <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> par está contido dentro de um <xref:System.ServiceModel.Activities.CorrelationScope>.</span><span class="sxs-lookup"><span data-stu-id="f35eb-118">In this example, a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is contained inside a <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span> <span data-ttu-id="f35eb-119">Nenhuma configuração de correlação explícita é necessária.</span><span class="sxs-lookup"><span data-stu-id="f35eb-119">No explicit correlation configuration is required.</span></span>  
  
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
  
 <span data-ttu-id="f35eb-120">Se correlações adicionais são necessárias, elas podem ser configuradas usando o <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> propriedade das atividades de mensagem respectivas usando desejado `CorrelationInitializer` tipos.</span><span class="sxs-lookup"><span data-stu-id="f35eb-120">If additional correlations are required then they can be configured using the <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> property of the respective messaging activities using the desired `CorrelationInitializer` types.</span></span>  
  
## <a name="using-correlation-in-a-two-way-operation-with-sendreceivereply"></a><span data-ttu-id="f35eb-121">Uso de correlação em uma operação bidirecional com Send/ReceiveReply</span><span class="sxs-lookup"><span data-stu-id="f35eb-121">Using Correlation in a Two-Way Operation with Send/ReceiveReply</span></span>  
 <span data-ttu-id="f35eb-122">Enquanto o <xref:System.ServiceModel.Activities.Receive> atividade somente pode ser usada em um serviço de fluxo de trabalho hospedado pelo <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.ServiceModel.Activities.Send> e o <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> par pode ser usado em qualquer fluxo de trabalho deve invocar um método em um serviço Web.</span><span class="sxs-lookup"><span data-stu-id="f35eb-122">While the <xref:System.ServiceModel.Activities.Receive> activity can only be used in a workflow service hosted by <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.ServiceModel.Activities.Send> and the <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair can be used in any workflow that must invoke a method on a Web service.</span></span> <span data-ttu-id="f35eb-123">Se o fluxo de trabalho é hospedado usando <xref:System.ServiceModel.Activities.WorkflowServiceHost> e em seguida, aplica-se a correlação de padrão descrita na seção anterior, mas se não, em seguida, correlação deve ser configurada explicitamente usando o desejado <xref:System.ServiceModel.Activities.CorrelationInitializer> e <xref:System.ServiceModel.Activities.CorrelationHandle>, ou usando o implícita lidar com o gerenciamento do <xref:System.ServiceModel.Activities.CorrelationScope>.</span><span class="sxs-lookup"><span data-stu-id="f35eb-123">If the workflow is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost> then the default correlation described in the previous section applies, but if not, then correlation must be configured either explicitly using the desired <xref:System.ServiceModel.Activities.CorrelationInitializer> and <xref:System.ServiceModel.Activities.CorrelationHandle>, or by using the implicit handle management of the <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span>  
  
 <span data-ttu-id="f35eb-124">Ao usar **adicionar referência de serviço** em um serviço com operações de duas vias, as atividades são geradas esse encapsulamento de uma <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> emparelhar atividade internamente com a correlação de solicitação/resposta explicitamente especificado.</span><span class="sxs-lookup"><span data-stu-id="f35eb-124">When using **Add Service Reference** on a service with two-way operations, activities are generated that wrap a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair activity internally with the Request/Reply correlation explicitly specified.</span></span>
