---
title: Correlação duplex durável
ms.date: 03/30/2017
ms.assetid: 8eb0e49a-6d3b-4f7e-a054-0d4febee2ffb
ms.openlocfilehash: f2f5fe557f1f8754758d0dd9b4042cacc62cc61f
ms.sourcegitcommit: daa8788af67ac2d1cecd24f9f3409babb2f978c9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47862879"
---
# <a name="durable-duplex-correlation"></a>Correlação duplex durável
Correlação duplex durável, também conhecido como correlação de retorno de chamada, é útil quando um serviço de fluxo de trabalho tem um requisito para enviar um retorno de chamada ao chamador inicial. Ao contrário de duplex do WCF, o retorno de chamada pode ocorrer a qualquer momento no futuro e não está vinculado ao mesmo canal ou o tempo de vida do canal; o único requisito é que o chamador tem um ponto de extremidade ativo escuta para a mensagem de retorno de chamada. Isso permite que dois serviços de fluxo de trabalho para se comunicar em uma conversa de longa execução. Este tópico fornece uma visão geral de correlação duplex durável.  
  
## <a name="using-durable-duplex-correlation"></a>Usando correlação Duplex durável  
 Para usar a correlação duplex durável, os dois serviços devem usar uma associação habilitada para contexto que dá suporte a operações de duas vias, tais como <xref:System.ServiceModel.NetTcpContextBinding> ou <xref:System.ServiceModel.WSHttpContextBinding>. Os registros de serviço chamada um <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> com a associação desejada no cliente <xref:System.ServiceModel.Endpoint>. O serviço de recebimento recebe esses dados em que a chamada inicial e, em seguida, usa-lo por conta própria <xref:System.ServiceModel.Endpoint> no <xref:System.ServiceModel.Activities.Send> atividade que faz a chamada para o serviço de chamada. Neste exemplo, dois serviços se comunicam entre si. O primeiro serviço invoca um método no serviço de segundo e, em seguida, aguarda uma resposta. O segundo serviço sabe o nome do método de retorno de chamada, mas o ponto de extremidade do serviço que implementa este método não é conhecido em tempo de design.  
  
> [!NOTE]
> Frente e verso durável só pode ser usado quando o <xref:System.ServiceModel.Channels.AddressingVersion> do ponto de extremidade é configurado com <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A>. Se não, então um <xref:System.InvalidOperationException> exceção é lançada com a seguinte mensagem: "a mensagem contém um cabeçalho de contexto do retorno de chamada com uma referência de ponto de extremidade para [AddressingVersion](http://schemas.xmlsoap.org/ws/2004/08/addressing). Contexto do retorno de chamada pode ser transmitido apenas quando o AddressingVersion é configurado com 'WSAddressing10'.
  
 No exemplo a seguir, um serviço de fluxo de trabalho é hospedado que cria um retorno de chamada <xref:System.ServiceModel.Endpoint> usando <xref:System.ServiceModel.WSHttpContextBinding>.  
  
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
  
 O fluxo de trabalho que implementa esse serviço de fluxo de trabalho inicializa a correlação de retorno de chamada com o seu <xref:System.ServiceModel.Activities.Send> atividade e faz referência a esse ponto de extremidade do retorno de chamada a <xref:System.ServiceModel.Activities.Receive> atividade que se correlaciona com a <xref:System.ServiceModel.Activities.Send>. O exemplo a seguir representa o fluxo de trabalho que é retornado o `GetWF1` método.  
  
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
  
 O segundo serviço de fluxo de trabalho é hospedado usando uma associação fornecida pelo sistema, com base em contexto.  
  
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
  
 O fluxo de trabalho que implementa esse serviço de fluxo de trabalho começa com um <xref:System.ServiceModel.Activities.Receive> atividade. Isso receber atividade inicializa a correlação de retorno de chamada para esse serviço, atrasa por um período de tempo para simular trabalho de longa execução e, em seguida, chama de volta para o primeiro serviço usando o contexto de retorno de chamada que foi passado na primeira chamada para o serviço. O exemplo a seguir representa o fluxo de trabalho que é retornado de uma chamada para `GetWF2`. Observe que o <xref:System.ServiceModel.Activities.Send> atividade tem um endereço de espaço reservado de `http://www.contoso.com`; o endereço real usado em tempo de execução é o endereço de retorno de chamada fornecido.  
  
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
  
 Quando o `StartOrder` método é invocado no primeiro fluxo de trabalho, a seguinte saída é exibida, que mostra o fluxo de execução por meio de dois fluxos de trabalho.  
  
```Output  
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
  
 Neste exemplo, ambos os fluxos de trabalho de gerenciar explicitamente correlação usando um <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>. Porque não havia apenas uma única correlação nesses fluxos de trabalho de exemplo, o padrão <xref:System.ServiceModel.Activities.CorrelationHandle> gerenciamento seria suficiente.
