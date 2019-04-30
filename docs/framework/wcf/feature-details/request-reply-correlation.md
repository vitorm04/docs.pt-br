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
# <a name="request-reply-correlation"></a>Correlação resposta/solicitação
Correlação de solicitação-resposta é usada com um <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> par para implementar uma operação bidirecional em um serviço de fluxo de trabalho e com um <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> par que chama uma operação bidirecional em outra Web serviço. Ao invocar uma operação bidirecional em um serviço WCF, o serviço pode ser qualquer um tradicional serviço Windows Communication Foundation (WCF) código imperativo, ou ele pode ser um serviço de fluxo de trabalho. Para usar uma associação bidirecional forem usada, como de correlação de solicitação-resposta <xref:System.ServiceModel.BasicHttpBinding>. Se invocar ou implementar uma operação bidirecional, as etapas de inicialização de correlação são semelhantes e são abordadas nesta seção.  
  
## <a name="using-correlation-in-a-two-way-operation-with-receivesendreply"></a>Uso de correlação em uma operação bidirecional com receber/SendReply  
 Um <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> par é usado para implementar uma operação bidirecional em um serviço de fluxo de trabalho. O tempo de execução usa correlação de solicitação-resposta para garantir que a resposta é expedida para o chamador correto. Quando um fluxo de trabalho é hospedado usando <xref:System.ServiceModel.Activities.WorkflowServiceHost>, que é o caso para serviços de fluxo de trabalho e, em seguida, a inicialização de correlação padrão é suficiente. Nesse cenário, uma <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> par é usado por um fluxo de trabalho, e nenhuma configuração de correlação específica é necessária.  
  
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
  
### <a name="explicitly-initializing-request-reply-correlation"></a>Inicializar explicitamente a correlação de solicitação-resposta  
 Se outras operações bidirecionais estiverem em paralelo, em seguida, correlação deve ser configurada explicitamente. Isso pode ser feito especificando uma <xref:System.ServiceModel.Activities.CorrelationHandle> e <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>, ou colocando o <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> dentro de um <xref:System.ServiceModel.Activities.CorrelationScope>. Neste exemplo, a correlação de solicitação-resposta é configurada em um <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> par.  
  
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
  
 Em vez de definir explicitamente a correlação, um <xref:System.ServiceModel.Activities.CorrelationScope> atividade pode ser usada. <xref:System.ServiceModel.Activities.CorrelationScope> Fornece um implícita <xref:System.ServiceModel.Activities.CorrelationHandle> para as atividades de mensagem que ele contém. Neste exemplo, uma <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> par está contido dentro de um <xref:System.ServiceModel.Activities.CorrelationScope>. Nenhuma configuração de correlação explícita é necessária.  
  
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
  
 Se correlações adicionais são necessárias, elas podem ser configuradas usando o <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> propriedade das atividades de mensagem respectivas usando desejado `CorrelationInitializer` tipos.  
  
## <a name="using-correlation-in-a-two-way-operation-with-sendreceivereply"></a>Uso de correlação em uma operação bidirecional com Send/ReceiveReply  
 Enquanto o <xref:System.ServiceModel.Activities.Receive> atividade somente pode ser usada em um serviço de fluxo de trabalho hospedado pelo <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.ServiceModel.Activities.Send> e o <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> par pode ser usado em qualquer fluxo de trabalho deve invocar um método em um serviço Web. Se o fluxo de trabalho é hospedado usando <xref:System.ServiceModel.Activities.WorkflowServiceHost> e em seguida, aplica-se a correlação de padrão descrita na seção anterior, mas se não, em seguida, correlação deve ser configurada explicitamente usando o desejado <xref:System.ServiceModel.Activities.CorrelationInitializer> e <xref:System.ServiceModel.Activities.CorrelationHandle>, ou usando o implícita lidar com o gerenciamento do <xref:System.ServiceModel.Activities.CorrelationScope>.  
  
 Ao usar **adicionar referência de serviço** em um serviço com operações de duas vias, as atividades são geradas esse encapsulamento de uma <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> emparelhar atividade internamente com a correlação de solicitação/resposta explicitamente especificado.
