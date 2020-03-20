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
# <a name="request-reply-correlation"></a>Correlação resposta/solicitação
A correlação solicitação-resposta <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> é usada com um par para implementar uma <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> operação bidirecional em um serviço de fluxo de trabalho e com um par que invoca uma operação bidirecional em outro serviço web. Ao invocar uma operação bidirecional em um serviço WCF, o serviço pode ser um serviço tradicional baseado em código baseado em código windows communication Foundation (WCF) ou pode ser um serviço de fluxo de trabalho. Para usar a correlação solicitação-resposta, deve ser <xref:System.ServiceModel.BasicHttpBinding>utilizada uma vinculação bidirecional, como . Seja invocando ou implementando uma operação bidirecional, as etapas de inicialização da correlação são semelhantes e são cobertas nesta seção.  
  
## <a name="using-correlation-in-a-two-way-operation-with-receivesendreply"></a>Usando correlação em uma operação bidirecional com receber/enviar resposta  
 <xref:System.ServiceModel.Activities.Receive> / Um <xref:System.ServiceModel.Activities.SendReply> par é usado para implementar uma operação bidirecional em um serviço de fluxo de trabalho. O tempo de execução usa correlação solicitação-resposta para garantir que a resposta seja enviada ao chamador correto. Quando um fluxo de <xref:System.ServiceModel.Activities.WorkflowServiceHost>trabalho é hospedado usando , que é o caso dos serviços de fluxo de trabalho, então a inicialização da correlação padrão é suficiente. Neste cenário, <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> um par é usado por um fluxo de trabalho, e nenhuma configuração de correlação específica é necessária.  
  
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
  
### <a name="explicitly-initializing-request-reply-correlation"></a>Inicializando explicitamente a correlação solicitação-resposta  
 Se outras operações bidirecionais estiverem em paralelo, então a correlação deve ser explicitamente configurada. Isso pode ser feito <xref:System.ServiceModel.Activities.CorrelationHandle> especificando <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>a e <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> , <xref:System.ServiceModel.Activities.CorrelationScope>ou colocando o interior de um . Neste exemplo, a correlação solicitação-resposta <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> é configurada em um par.  
  
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
  
 Em vez de configurar explicitamente <xref:System.ServiceModel.Activities.CorrelationScope> a correlação, uma atividade pode ser usada. <xref:System.ServiceModel.Activities.CorrelationScope>fornece uma <xref:System.ServiceModel.Activities.CorrelationHandle> implícita para as atividades de mensagens que ele contém. Neste exemplo, <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> um par está <xref:System.ServiceModel.Activities.CorrelationScope>contido dentro de um . Nenhuma configuração de correlação explícita é necessária.  
  
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
  
 Se forem necessárias correlações adicionais, <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> elas podem ser configuradas `CorrelationInitializer` usando a propriedade das respectivas atividades de mensagens usando os tipos desejados.  
  
## <a name="using-correlation-in-a-two-way-operation-with-sendreceivereply"></a>Usando correlação em uma operação bidirecional com enviar/receberresposta  
 Embora <xref:System.ServiceModel.Activities.Receive> a atividade só possa ser usada em <xref:System.ServiceModel.Activities.WorkflowServiceHost> <xref:System.ServiceModel.Activities.Send> um <xref:System.ServiceModel.Activities.Send> / serviço de fluxo de trabalho hospedado por , e o <xref:System.ServiceModel.Activities.ReceiveReply> par pode ser usado em qualquer fluxo de trabalho que deve invocar um método em um serviço web. Se o fluxo de <xref:System.ServiceModel.Activities.WorkflowServiceHost> trabalho estiver hospedado usando a correlação padrão descrita na seção anterior se aplica, <xref:System.ServiceModel.Activities.CorrelationInitializer> mas <xref:System.ServiceModel.Activities.CorrelationHandle>se não, então a <xref:System.ServiceModel.Activities.CorrelationScope>correlação deve ser configurada explicitamente usando o desejado e , ou usando o gerenciamento implícito da alça do .  
  
 Ao usar **adicionar referência de serviço** em um serviço com <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> operações bidirecionais, são geradas atividades que envolvem uma atividade de par internamente com a correlação Solicitação/Resposta explicitamente especificada.
