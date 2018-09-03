---
title: Correlação de intercâmbio de contexto
ms.date: 03/30/2017
ms.assetid: 1e2852be-3601-45ae-b507-ccc465d45c60
ms.openlocfilehash: d9de111fa08b4a398bba52bc903ea1fec8c7f298
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43483691"
---
# <a name="context-exchange-correlation"></a>Correlação de intercâmbio de contexto
Correlação de contexto se baseia o mecanismo de troca de contexto descrito o [especificação de protocolo de troca de contexto do .NET](https://go.microsoft.com/fwlink/?LinkId=166059). Correlação de contexto usa um cabeçalho de contexto conhecido ou um cookie para relacionar mensagens para a instância correta. Para usar a correlação de contexto, uma com base no contexto de associação, como <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, ou <xref:System.ServiceModel.NetTcpContextBinding> deve ser usado no ponto de extremidade fornecido para o <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Este tópico explica como usar a correlação de contexto com atividades de mensagem em um serviço de fluxo de trabalho.  
  
## <a name="using-context-correlation"></a>Usando o contexto de correlação  
 Correlação de contexto é usada quando um cliente deve fazer chamadas repetidas em um serviço de fluxo de trabalho e o serviço está hospedado usando uma das ligações de contexto. Esse tipo de correlação é inicializado por uma <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> par no serviço de fluxo de trabalho. O contexto é enviado de volta para o cliente juntamente com a resposta e, em seguida, o cliente o anexa nesse contexto em chamadas subsequentes para o serviço.  
  
### <a name="configuring-context-correlation-in-a-workflow-service"></a>Configurar correlação de contexto em um serviço de fluxo de trabalho  
 Correlação de contexto é inicializada usando um <xref:System.ServiceModel.Activities.ContextCorrelationInitializer> que está associado com o <xref:System.ServiceModel.Activities.SendReply> atividade responde à mensagem de entrada inicial. No exemplo a seguir, o <xref:System.ServiceModel.Activities.SendReply> está configurado para inicializar uma correlação de contexto.  
  
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
>  Neste exemplo, há realmente dois tipos de correlação que está sendo usada: correlação de contexto e correlação de solicitação-resposta. A correlação de contexto é usada para que as chamadas de clientes são roteadas para a instância correta. A correlação de solicitação-resposta é usada pelas <xref:System.ServiceModel.Activities.Receive> e o <xref:System.ServiceModel.Activities.SendReply> atividades juntos para implementar a operação bidirecional é modelado por essas atividades. Neste exemplo, somente a correlação de contexto for configurada explicitamente e o <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> par está usando a correlação de solicitação-resposta padrão fornecida pelo implícito <xref:System.ServiceModel.Activities.CorrelationHandle> gerenciamento de <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Ao usar o **ReceiveAndSendReply** modelo de atividade no designer, correlação de solicitação-resposta de fluxo de trabalho está configurado explicitamente. Para obter mais informações sobre a correlação de solicitação-resposta e gerenciamento de identificador de correlação implícita, consulte [solicitação-resposta](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md) e [visão geral de correlação](../../../../docs/framework/wcf/feature-details/correlation-overview.md). Para obter mais informações sobre o **ReceiveAndSendReply** modelo de atividade, consulte [ReceiveAndSendReply](/visualstudio/workflow-designer/receiveandsendreply-template-designer).  
  
 Subsequentes <xref:System.ServiceModel.Activities.Receive> atividades no serviço de fluxo de trabalho podem fazer referência a <xref:System.ServiceModel.Activities.CorrelationHandle> que foi inicializado pelo <xref:System.ServiceModel.Activities.SendReply> no exemplo anterior.  
  
```csharp  
Receive AddItem = new Receive  
{  
    ServiceContractName = "IOrderService",  
    OperationName = "AddItem",  
    CorrelatesWith = OrderHandle  
};  
```  
  
 O ponto de extremidade está configurado, em seguida, o <xref:System.ServiceModel.Activities.WorkflowServiceHost> para usar uma com base no contexto de associação, como <xref:System.ServiceModel.BasicHttpContextBinding>.  
  
```xml  
<endpoint  
  contract="IOrderContract"  
  binding = "basicHttpContextBinding"  
  address="http://localhost:8080/OrderService" />  
```  
  
### <a name="configuring-context-correlation-in-a-workflow-client"></a>Configurar correlação de contexto em um cliente de fluxo de trabalho  
 Quando o cliente é outro fluxo de trabalho, correlação de contexto deve ser configurada no cliente também. O fluxo de trabalho do cliente, o <xref:System.ServiceModel.Activities.ReceiveReply> do <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> par que faz a chamada inicial para o serviço de fluxo de trabalho deve ser configurado com um <xref:System.ServiceModel.Activities.ContextCorrelationInitializer>.  
  
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
  
 Depois que a correlação é inicializada, as próximas <xref:System.ServiceModel.Activities.Send> atividades podem usar o <xref:System.ServiceModel.Activities.CorrelationHandle> para invocar métodos na mesma instância do serviço.  
  
```csharp  
Send request2 = new Send  
{  
    CorrelatesWith = cchandle,  
    // Remaining activity configuration omitted.  
};  
```  
  
 Observe que nesses exemplos, a correlação de contexto tenha sido explicitamente configurada. Se o fluxo de trabalho cliente também não está hospedado em um <xref:System.ServiceModel.Activities.WorkflowServiceHost>, e em seguida, correlação deve ser configurada explicitamente, a menos que as atividades estão contidas em um <xref:System.ServiceModel.Activities.CorrelationScope> atividade. Para obter mais informações sobre a correlação de contexto, consulte o [NetContextExchangeCorrelation](https://msdn.microsoft.com/library/93c74a1a-b9e2-46c6-95c0-c9b0e9472caf) exemplo.  
  
 Se o cliente que está fazendo chamadas para o serviço de fluxo de trabalho não é um fluxo de trabalho, em seguida, ele poderá fazer chamadas repetidas desde que ela explicitamente passa de volta o contexto que é retornado da primeira chamada para o serviço de fluxo de trabalho. Proxies gerados pela adição de uma referência de serviço no [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] armazenar e passar esse contexto por padrão.
