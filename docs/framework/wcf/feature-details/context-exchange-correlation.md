---
title: Correlação de intercâmbio de contexto
ms.date: 03/30/2017
ms.assetid: 1e2852be-3601-45ae-b507-ccc465d45c60
ms.openlocfilehash: da5ab2c89e4e2011c38f5fca99aeb5c2c73801a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492317"
---
# <a name="context-exchange-correlation"></a><span data-ttu-id="1d13f-102">Correlação de intercâmbio de contexto</span><span class="sxs-lookup"><span data-stu-id="1d13f-102">Context Exchange Correlation</span></span>
<span data-ttu-id="1d13f-103">Correlação de contexto baseia-se o mecanismo de troca de contexto descrito no [especificação do protocolo de troca de contexto de .NET](http://go.microsoft.com/fwlink/?LinkId=166059).</span><span class="sxs-lookup"><span data-stu-id="1d13f-103">Context correlation is based on the context exchange mechanism described in the [.NET Context Exchange Protocol Specification](http://go.microsoft.com/fwlink/?LinkId=166059).</span></span> <span data-ttu-id="1d13f-104">Correlação de contexto usa um cabeçalho de contexto conhecido ou um cookie para relacionar as mensagens para a instância correta.</span><span class="sxs-lookup"><span data-stu-id="1d13f-104">Context correlation uses a well-known context header or cookie to relate messages to the correct instance.</span></span> <span data-ttu-id="1d13f-105">Para usar a correlação de contexto, uma com base em contexto de associação, como <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, ou <xref:System.ServiceModel.NetTcpContextBinding> deve ser usado no ponto de extremidade fornecido para o <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="1d13f-105">To use context correlation, a context-based binding such as <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, or <xref:System.ServiceModel.NetTcpContextBinding> must be used on the endpoint provided to the <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="1d13f-106">Este tópico explica como usar a correlação de contexto com atividades de mensagens em um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1d13f-106">This topic explains how to use context correlation with messaging activities in a workflow service.</span></span>  
  
## <a name="using-context-correlation"></a><span data-ttu-id="1d13f-107">Usando o contexto de correlação</span><span class="sxs-lookup"><span data-stu-id="1d13f-107">Using Context Correlation</span></span>  
 <span data-ttu-id="1d13f-108">Correlação de contexto é usada quando um cliente deve fazer chamadas repetidas em um serviço de fluxo de trabalho e o serviço é hospedado usando uma das ligações de contexto.</span><span class="sxs-lookup"><span data-stu-id="1d13f-108">Context correlation is used when a client must make repeated calls into a workflow service and the service is hosted using one of the context bindings.</span></span> <span data-ttu-id="1d13f-109">Esse tipo de correlação é inicializado por um <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> par no serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1d13f-109">This type of correlation is initialized by a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair in the workflow service.</span></span> <span data-ttu-id="1d13f-110">O contexto é enviado de volta ao cliente junto com a resposta e, em seguida, o cliente o anexa neste contexto em chamadas subsequentes para o serviço.</span><span class="sxs-lookup"><span data-stu-id="1d13f-110">The context is sent back to the client together with the reply, and then the client attaches this context on subsequent calls to the service.</span></span>  
  
### <a name="configuring-context-correlation-in-a-workflow-service"></a><span data-ttu-id="1d13f-111">Configurar correlação de contexto em um serviço de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="1d13f-111">Configuring Context Correlation in a Workflow Service</span></span>  
 <span data-ttu-id="1d13f-112">Correlação de contexto é inicializada usando um <xref:System.ServiceModel.Activities.ContextCorrelationInitializer> que está associado a <xref:System.ServiceModel.Activities.SendReply> atividade responde à mensagem de entrada inicial.</span><span class="sxs-lookup"><span data-stu-id="1d13f-112">Context correlation is initialized by using a <xref:System.ServiceModel.Activities.ContextCorrelationInitializer> that is associated with the <xref:System.ServiceModel.Activities.SendReply> activity that replies to the initial incoming message.</span></span> <span data-ttu-id="1d13f-113">No exemplo a seguir, o <xref:System.ServiceModel.Activities.SendReply> está configurado para inicializar uma correlação de contexto.</span><span class="sxs-lookup"><span data-stu-id="1d13f-113">In the following example, the <xref:System.ServiceModel.Activities.SendReply> is configured to initialize a context correlation.</span></span>  
  
```csharp  
Variable<string> Item = new Variable<string>();  
Variable<CorrelationHandle> OrderHandle = new Variable<CorrelationHandle>();  
  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = "IOrderService",  
    OperationName = "StartOrder"  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    CorrelationInitializers =  
    {  
        new ContextCorrelationInitializer  
        {  
            CorrelationHandle = OrderHandle  
        }  
    }  
};  
```  
  
> [!NOTE]
>  <span data-ttu-id="1d13f-114">Neste exemplo, há realmente dois tipos de correlação que está sendo usada: correlação de contexto e a correlação de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="1d13f-114">In this example, there are actually two types of correlation being used: context correlation and request-reply correlation.</span></span> <span data-ttu-id="1d13f-115">A correlação de contexto é usada para que as chamadas de clientes são roteadas para a instância correta.</span><span class="sxs-lookup"><span data-stu-id="1d13f-115">The context correlation is used so that calls from clients are routed to the correct instance.</span></span> <span data-ttu-id="1d13f-116">A correlação de solicitação-resposta é usada pelo <xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.SendReply> as atividades para implementar a operação bidirecional é modelado por essas atividades.</span><span class="sxs-lookup"><span data-stu-id="1d13f-116">The request-reply correlation is used by the <xref:System.ServiceModel.Activities.Receive> and the <xref:System.ServiceModel.Activities.SendReply> activities together to implement the two-way operation modeled by these activities.</span></span> <span data-ttu-id="1d13f-117">Neste exemplo, apenas a correlação de contexto é explicitamente configurada e o <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> par está usando a correlação de solicitação-resposta padrão que é fornecida pelo implícita <xref:System.ServiceModel.Activities.CorrelationHandle> gerenciamento de <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="1d13f-117">In this example, only the context correlation is explicitly configured, and the <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is using the default request-reply correlation that is provided by the implicit <xref:System.ServiceModel.Activities.CorrelationHandle> management of <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="1d13f-118">Ao usar o **ReceiveAndSendReply** configurado explicitamente do modelo de atividade na correlação de solicitação-resposta de designer de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1d13f-118">When using the **ReceiveAndSendReply** activity template in the workflow designer, request-reply correlation is explicitly configured.</span></span> <span data-ttu-id="1d13f-119">Para obter mais informações sobre a correlação de solicitação-resposta e gerenciamento de identificador de correlação implícita, consulte [solicitação-resposta](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md) e [visão geral de correlação](../../../../docs/framework/wcf/feature-details/correlation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1d13f-119">For more information about request-reply correlation and implicit correlation handle management, see [Request-Reply](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md) and [Correlation Overview](../../../../docs/framework/wcf/feature-details/correlation-overview.md).</span></span> <span data-ttu-id="1d13f-120">Para obter mais informações sobre o **ReceiveAndSendReply** modelo de atividade, consulte [ReceiveAndSendReply](/visualstudio/workflow-designer/receiveandsendreply-template-designer).</span><span class="sxs-lookup"><span data-stu-id="1d13f-120">For more information about the **ReceiveAndSendReply** activity template, see [ReceiveAndSendReply](/visualstudio/workflow-designer/receiveandsendreply-template-designer).</span></span>  
  
 <span data-ttu-id="1d13f-121">Subsequentes <xref:System.ServiceModel.Activities.Receive> atividades no serviço de fluxo de trabalho podem fazer referência a <xref:System.ServiceModel.Activities.CorrelationHandle> que foi inicializado pelo <xref:System.ServiceModel.Activities.SendReply> no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="1d13f-121">Subsequent <xref:System.ServiceModel.Activities.Receive> activities in the workflow service can reference the <xref:System.ServiceModel.Activities.CorrelationHandle> that was initialized by the <xref:System.ServiceModel.Activities.SendReply> in the previous example.</span></span>  
  
```csharp  
Receive AddItem = new Receive  
{  
    ServiceContractName = "IOrderService",  
    OperationName = "AddItem",  
    CorrelatesWith = OrderHandle  
};  
```  
  
 <span data-ttu-id="1d13f-122">O ponto de extremidade está configurado, em seguida, o <xref:System.ServiceModel.Activities.WorkflowServiceHost> para usar um contexto de acordo com associação, como <xref:System.ServiceModel.BasicHttpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="1d13f-122">The endpoint is then configured on the <xref:System.ServiceModel.Activities.WorkflowServiceHost> to use a context-based binding, such as <xref:System.ServiceModel.BasicHttpContextBinding>.</span></span>  
  
```xml  
<endpoint  
  contract="IOrderContract"  
  binding = "basicHttpContextBinding"  
  address="http://localhost:8080/OrderService" />  
```  
  
### <a name="configuring-context-correlation-in-a-workflow-client"></a><span data-ttu-id="1d13f-123">Configurar correlação de contexto em um cliente de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="1d13f-123">Configuring Context Correlation in a Workflow Client</span></span>  
 <span data-ttu-id="1d13f-124">Quando o cliente é outro fluxo de trabalho, correlação de contexto deve ser configurada no cliente também.</span><span class="sxs-lookup"><span data-stu-id="1d13f-124">When the client is another workflow, context correlation must be configured on the client as well.</span></span> <span data-ttu-id="1d13f-125">O fluxo de trabalho do cliente, o <xref:System.ServiceModel.Activities.ReceiveReply> do <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> par que faz a chamada inicial para o serviço de fluxo de trabalho deve ser configurado com um <xref:System.ServiceModel.Activities.ContextCorrelationInitializer>.</span><span class="sxs-lookup"><span data-stu-id="1d13f-125">On the client workflow, the <xref:System.ServiceModel.Activities.ReceiveReply> of the <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair that makes the initial call to the workflow service must be configured with a <xref:System.ServiceModel.Activities.ContextCorrelationInitializer>.</span></span>  
  
```csharp  
Variable<CorrelationHandle> cchandle = new Variable<CorrelationHandle>();  
Send request = new Send  
{  
    // Activity configuration omitted.  
};  
  
ReceiveReply reply = new ReceiveReply  
{  
    Request = request,  
    CorrelationInitializers =   
    {  
        new ContextCorrelationInitializer  
        {  
            CorrelationHandle = cchandle  
        }  
    }  
};  
```  
  
 <span data-ttu-id="1d13f-126">Depois que a correlação é inicializado, subsequentes <xref:System.ServiceModel.Activities.Send> atividades podem usar o <xref:System.ServiceModel.Activities.CorrelationHandle> para invocar os métodos na mesma instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="1d13f-126">After the correlation is initialized, subsequent <xref:System.ServiceModel.Activities.Send> activities can use the <xref:System.ServiceModel.Activities.CorrelationHandle> to invoke methods on the same service instance.</span></span>  
  
```csharp  
Send request2 = new Send  
{  
    CorrelatesWith = cchandle,  
    // Remaining activity configuration omitted.  
};  
```  
  
 <span data-ttu-id="1d13f-127">Observe que esses exemplos, a correlação de contexto foi configurada explicitamente.</span><span class="sxs-lookup"><span data-stu-id="1d13f-127">Note that in these examples, the context correlation has been explicitly configured.</span></span> <span data-ttu-id="1d13f-128">Se o fluxo de trabalho cliente também não está hospedado em um <xref:System.ServiceModel.Activities.WorkflowServiceHost>, e correlação deve ser configurada explicitamente, a menos que as atividades estão contidas em um <xref:System.ServiceModel.Activities.CorrelationScope> atividade.</span><span class="sxs-lookup"><span data-stu-id="1d13f-128">If the client workflow is not also hosted in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>, then correlation must be explicitly configured, unless the activities are contained within a <xref:System.ServiceModel.Activities.CorrelationScope> activity.</span></span> <span data-ttu-id="1d13f-129">Para obter mais informações sobre a correlação de contexto, consulte o [NetContextExchangeCorrelation](http://msdn.microsoft.com/library/93c74a1a-b9e2-46c6-95c0-c9b0e9472caf) exemplo.</span><span class="sxs-lookup"><span data-stu-id="1d13f-129">For more information about context correlation, see the [NetContextExchangeCorrelation](http://msdn.microsoft.com/library/93c74a1a-b9e2-46c6-95c0-c9b0e9472caf) sample.</span></span>  
  
 <span data-ttu-id="1d13f-130">Se o cliente que está fazendo chamadas para o serviço de fluxo de trabalho não é um fluxo de trabalho, em seguida, ele poderá fazer chamadas repetidas como transmiti-la explicitamente novamente o contexto que é retornado da primeira chamada para o serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1d13f-130">If the client that is making calls to the workflow service is not a workflow, then it can still make repeated calls as long as it explicitly passes back the context that is returned from the first call to the workflow service.</span></span> <span data-ttu-id="1d13f-131">Proxies gerados pela adição de uma referência de serviço no [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] armazenar e transmitir neste contexto, por padrão.</span><span class="sxs-lookup"><span data-stu-id="1d13f-131">Proxies generated by adding a service reference in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] store and pass this context by default.</span></span>
