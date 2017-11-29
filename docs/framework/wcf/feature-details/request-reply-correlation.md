---
title: "Correlação resposta/solicitação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf4379bf-2d08-43f3-9584-dfa30ffcb1f6
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 16140f71875357e3a07ac4a5a9134d4ae04e0f43
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="request-reply-correlation"></a>Correlação resposta/solicitação
Correlação de solicitação-resposta é usada com um <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> par para implementar uma operação bidirecional em um serviço de fluxo de trabalho e com um <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> par que invoca uma operação bidirecional em outra Web serviço. Ao invocar uma operação bidirecional em uma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service, o serviço pode ser uma imperativa tradicional baseada em código [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] serviço ou pode ser um serviço de fluxo de trabalho. Para usar uma associação bidirecional forem usada, como de correlação de solicitação-resposta <xref:System.ServiceModel.BasicHttpBinding>. Se chamar ou implementar uma operação bidirecional, as etapas de inicialização de correlação são semelhantes e são abordadas nesta seção.  
  
## <a name="using-correlation-in-a-two-way-operation-with-receivesendreply"></a>Uso de correlação em uma operação bidirecional com SendReply/receber  
 Um <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> par é usado para implementar uma operação bidirecional em um serviço de fluxo de trabalho. O tempo de execução usa correlação de solicitação-resposta para garantir que a resposta será enviada para o chamador correto. Quando um fluxo de trabalho é hospedado usando <xref:System.ServiceModel.Activities.WorkflowServiceHost>, que é o caso para serviços de fluxo de trabalho e, em seguida, a inicialização de correlação padrão é suficiente. Nesse cenário, um <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> par é usado por um fluxo de trabalho, e nenhuma configuração de correlação específica é necessária.  
  
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
  
### <a name="explicitly-initializing-request-reply-correlation"></a>Inicializando explicitamente a correlação de solicitação-resposta  
 Se outras operações bidirecionais em paralelo, em seguida, correlação deve ser configurada explicitamente. Isso pode ser feito especificando uma <xref:System.ServiceModel.Activities.CorrelationHandle> e <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>, ou colocando o <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> dentro de um <xref:System.ServiceModel.Activities.CorrelationScope>. Neste exemplo, a correlação de solicitação-resposta está configurada em um <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> par.  
  
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
  
 Em vez de configurar explicitamente a correlação, um <xref:System.ServiceModel.Activities.CorrelationScope> atividade pode ser usada. <xref:System.ServiceModel.Activities.CorrelationScope>Fornece um implícita <xref:System.ServiceModel.Activities.CorrelationHandle> para as atividades de mensagens que ele contém. Neste exemplo, um <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> par está contido em um <xref:System.ServiceModel.Activities.CorrelationScope>. Nenhuma configuração de correlação explícita é necessária.  
  
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
  
 Se correlações adicionais são necessárias, elas podem ser configuradas usando o <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> propriedade das respectivas atividades mensagens usando desejado `CorrelationInitializer` tipos.  
  
## <a name="using-correlation-in-a-two-way-operation-with-sendreceivereply"></a>Uso de correlação em uma operação bidirecional com envio/ReceiveReply  
 Enquanto o <xref:System.ServiceModel.Activities.Receive> atividade somente pode ser usada em um serviço de fluxo de trabalho hospedado por <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> par pode ser usado em qualquer fluxo de trabalho deve invocar um método em um serviço Web. Se o fluxo de trabalho é hospedado usando <xref:System.ServiceModel.Activities.WorkflowServiceHost> , em seguida, aplica-se a correlação padrão descrita na seção anterior, mas se não, em seguida, correlação deve ser configurada explicitamente usando o desejado <xref:System.ServiceModel.Activities.CorrelationInitializer> e <xref:System.ServiceModel.Activities.CorrelationHandle>, ou usando o implícita controlar o gerenciamento do <xref:System.ServiceModel.Activities.CorrelationScope>.  
  
 Ao usar **adicionar referência de serviço** em um serviço com operações de duas vias, as atividades são geradas que quebra uma <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> emparelhar atividade internamente com a correlação de solicitação/resposta explicitamente especificado.
