---
title: Correlação duplex durável
ms.date: 03/30/2017
ms.assetid: 8eb0e49a-6d3b-4f7e-a054-0d4febee2ffb
ms.openlocfilehash: bb73cef5190a0b146e713ef1adae24219dc2eed8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185169"
---
# <a name="durable-duplex-correlation"></a>Correlação duplex durável
A correlação duplex durável, também conhecida como correlação de retorno de chamada, é útil quando um serviço de fluxo de trabalho tem o requisito de enviar um retorno de chamada para o chamador inicial. Ao contrário do duplex WCF, o retorno de chamada pode acontecer a qualquer momento no futuro e não está vinculado ao mesmo canal ou à vida útil do canal; o único requisito é que o chamador tenha um ponto final ativo ouvindo a mensagem de retorno de chamada. Isso permite que dois serviços de fluxo de trabalho se comuniquem em uma conversa de longa duração. Este tópico fornece uma visão geral da correlação duplex durável.  
  
## <a name="using-durable-duplex-correlation"></a>Usando correlação duplex durável  
 Para usar correlação duplex durável, os dois serviços devem usar uma vinculação habilitada para contexto que suporte operações bidirecionais, como <xref:System.ServiceModel.NetTcpContextBinding> ou <xref:System.ServiceModel.WSHttpContextBinding>. O serviço de <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> chamada registra um com <xref:System.ServiceModel.Endpoint>a vinculação desejada em seu cliente. O serviço de recebimento recebe esses dados na chamada <xref:System.ServiceModel.Endpoint> inicial <xref:System.ServiceModel.Activities.Send> e depois os utiliza por conta própria na atividade que faz a chamada de volta para o serviço de chamada. Neste exemplo, dois serviços se comunicam entre si. O primeiro serviço invoca um método no segundo serviço e, em seguida, aguarda uma resposta. O segundo serviço sabe o nome do método de retorno de chamada, mas o ponto final do serviço que implementa esse método não é conhecido no momento do projeto.  
  
> [!NOTE]
> O duplex durável só <xref:System.ServiceModel.Channels.AddressingVersion> pode ser usado quando <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A>o ponto final estiver configurado com . Se não for, <xref:System.InvalidOperationException> então uma exceção é lançada com a seguinte mensagem: "A mensagem contém um cabeçalho de contexto de retorno de chamada com uma referência de ponto final para [AddressingVersion](http://schemas.xmlsoap.org/ws/2004/08/addressing). O contexto de retorno de chamada só pode ser transmitido quando o AddressingVersion é configurado com 'WSAddressing10'.
  
 No exemplo a seguir, um serviço de fluxo <xref:System.ServiceModel.Endpoint> de <xref:System.ServiceModel.WSHttpContextBinding>trabalho é hospedado que cria um retorno de chamada usando .  
  
```csharp  
// Host WF Service 1.  
string baseAddress1 = "http://localhost:8080/Service1";  
WorkflowServiceHost host1 = new WorkflowServiceHost(GetWF1(), new Uri(baseAddress1));  
  
// Add the callback endpoint.  
WSHttpContextBinding Binding1 = new WSHttpContextBinding();  
host1.AddServiceEndpoint("ICallbackItemsReady", Binding1, "ItemsReady");  
  
// Add the service endpoint.  
host1.AddServiceEndpoint("IService1", Binding1, baseAddress1);  
  
// Open the first workflow service.  
host1.Open();  
Console.WriteLine("Service1 waiting at: {0}", baseAddress1);  
```  
  
 O fluxo de trabalho que implementa esse serviço de <xref:System.ServiceModel.Activities.Send> fluxo de trabalho inicializa a correlação de retorno de chamada com sua atividade e faz referência a <xref:System.ServiceModel.Activities.Receive> esse ponto final de retorno da atividade que se correlaciona com o <xref:System.ServiceModel.Activities.Send>. O exemplo a seguir representa o fluxo `GetWF1` de trabalho que é retornado do método.  
  
```csharp  
Variable<CorrelationHandle> CallbackHandle = new Variable<CorrelationHandle>();  
  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = "IService1",  
    OperationName = "StartOrder"  
};  
  
Send GetItems = new Send  
{  
    CorrelationInitializers =
    {  
        new CallbackCorrelationInitializer  
        {  
            CorrelationHandle = CallbackHandle  
        }  
    },  
    ServiceContractName = "IService2",  
    OperationName = "StartItems",  
    Endpoint = new Endpoint  
    {  
        AddressUri = new Uri("http://localhost:8081/Service2"),  
        Binding = new WSHttpContextBinding  
        {  
            ClientCallbackAddress = new Uri("http://localhost:8080/Service1/ItemsReady")
        }  
    }  
};  
  
Receive ItemsReady = new Receive  
{  
    ServiceContractName = "ICallbackItemsReady",  
    OperationName = "ItemsReady",  
    CorrelatesWith = CallbackHandle,  
};  
  
Activity wf = new Sequence  
{  
    Variables =  
    {  
        CallbackHandle  
    },  
    Activities =  
    {  
        StartOrder,  
        new WriteLine  
        {  
            Text = "WF1 - Started"  
        },  
        GetItems,  
        new WriteLine  
        {  
            Text = "WF1 - Request Submitted"  
        },  
        ItemsReady,  
        new WriteLine  
        {  
            Text = "WF1 - Items Received"  
        }  
     }  
};  
```  
  
 O segundo serviço de fluxo de trabalho é hospedado usando uma vinculação baseada em contexto fornecida pelo sistema.  
  
```csharp  
// Host WF Service 2.  
string baseAddress2 = "http://localhost:8081/Service2";  
WorkflowServiceHost host2 = new WorkflowServiceHost(GetWF2(), new Uri(baseAddress2));  
  
// Add the service endpoint.  
WSHttpContextBinding Binding2 = new WSHttpContextBinding();  
host2.AddServiceEndpoint("IService2", Binding2, baseAddress2);  
  
// Open the second workflow service.  
host2.Open();  
Console.WriteLine("Service2 waiting at: {0}", baseAddress2);  
```  
  
 O fluxo de trabalho que implementa <xref:System.ServiceModel.Activities.Receive> esse serviço de fluxo de trabalho começa com uma atividade. Essa atividade de recebimento inicializa a correlação de retorno de chamada para este serviço, atrasa por um período de tempo para simular trabalhos de longa duração e, em seguida, liga de volta para o primeiro serviço usando o contexto de retorno de chamada que foi passado na primeira chamada para o serviço. O exemplo a seguir representa o fluxo de `GetWF2`trabalho que é retornado de uma chamada para . Observe que <xref:System.ServiceModel.Activities.Send> a atividade tem `http://www.contoso.com`um endereço de espaço reservado de; o endereço real usado em tempo de execução é o endereço de retorno de chamada fornecido.  
  
```csharp  
Variable<CorrelationHandle> ItemsCallbackHandle = new Variable<CorrelationHandle>();  
  
Receive StartItems = new Receive  
{  
    CorrelationInitializers =
    {  
        new CallbackCorrelationInitializer  
        {  
            CorrelationHandle = ItemsCallbackHandle  
        }  
    },  
    CanCreateInstance = true,  
    ServiceContractName = "IService2",  
    OperationName = "StartItems"  
};  
  
Send ItemsReady = new Send  
{  
    CorrelatesWith = ItemsCallbackHandle,  
    Endpoint = new Endpoint  
    {  
        // The callback address on the binding is used  
        // instead of this placeholder address.  
        AddressUri = new Uri("http://www.contoso.com"),  
  
        Binding = new WSHttpContextBinding()  
    },  
    OperationName = "ItemsReady",  
    ServiceContractName = "ICallbackItemsReady"  
};  
  
Activity wf = new Sequence  
{  
    Variables =  
    {  
        ItemsCallbackHandle  
    },  
    Activities =  
    {  
        StartItems,  
        new WriteLine  
        {  
            Text = "WF2 - Request Received"  
        },  
        new Delay  
        {  
            Duration = TimeSpan.FromMinutes(90)  
        },  
        new WriteLine  
        {  
            Text = "WF2 - Sending items"  
        },  
        ItemsReady,  
        new WriteLine  
        {  
            Text = "WF2 - Items sent"  
        }  
     }  
};  
```  
  
 Quando `StartOrder` o método é invocado no primeiro fluxo de trabalho, a seguinte saída é exibida, que mostra o fluxo de execução através dos dois fluxos de trabalho.  
  
```output  
Service1 waiting at: http://localhost:8080/Service1  
Service2 waiting at: http://localhost:8081/Service2  
Press enter to exit.
WF1 - Started  
WF2 - Request Received  
WF1 - Request Submitted  
WF2 - Sending items  
WF2 - Items sent  
WF1 - Items Received  
```  
  
 Neste exemplo, ambos os fluxos de <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>trabalho gerenciam explicitamente a correlação usando um . Como havia apenas uma única correlação nesses <xref:System.ServiceModel.Activities.CorrelationHandle> fluxos de trabalho amostrais, o gerenciamento padrão teria sido suficiente.
