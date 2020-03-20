---
title: Como inspecionar ou modificar mensagens no cliente
ms.date: 03/30/2017
ms.assetid: b8256335-f1c2-419f-b862-9f220ccad84c
ms.openlocfilehash: db1a99d2ed1f765e39815e6b6c70d6ada1db1d15
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185532"
---
# <a name="how-to-inspect-or-modify-messages-on-the-client"></a>Como inspecionar ou modificar mensagens no cliente
Você pode inspecionar ou modificar as mensagens recebidas ou de <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> saída em um cliente WCF implementando-a e inserindo-as no tempo de execução do cliente. Para obter mais informações, consulte [Extending Clients](extending-clients.md). A característica equivalente no <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>serviço é o . Para obter um exemplo de código completo, consulte a amostra [De inspetores de mensagens.](../samples/message-inspectors.md)  
  
### <a name="to-inspect-or-modify-messages"></a>Para inspecionar ou modificar mensagens  
  
1. Implemente a interface <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.  
  
2. Implemente <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> um ou dependendo do escopo no qual você deseja inserir o inspetor de mensagens do cliente. <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>permite que você mude o comportamento no nível final. <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>permite que você mude de comportamento no nível do contrato.  
  
3. Insira o comportamento <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> antes <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> de <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>chamar o método ou o método no . Para obter detalhes, [consulte Configuração e Prolongamento do tempo de execução com comportamentos](configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="example"></a>Exemplo  
 Os exemplos de código a seguir mostram, em ordem:  
  
- Uma implementação de inspetor de clientes.  
  
- Um comportamento final que insere o inspetor.  
  
- A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>- classe derivada que permite adicionar o comportamento em um arquivo de configuração.  
  
- Um arquivo de configuração que adiciona o comportamento de ponto final que insere o inspetor de mensagens do cliente no tempo de execução do cliente.  
  
```csharp  
// Client message inspector  
public class SimpleMessageInspector : IClientMessageInspector  
{  
    public void AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
    {  
        // Implement this method to inspect/modify messages after a message  
        // is received but prior to passing it back to the client
        Console.WriteLine("AfterReceiveReply called");  
    }  
  
    public object BeforeSendRequest(ref System.ServiceModel.Channels.Message request, IClientChannel channel)  
    {  
        // Implement this method to inspect/modify messages before they
        // are sent to the service  
        Console.WriteLine("BeforeSendRequest called");  
        return null;  
    }  
}  
```  
  
```csharp  
// Endpoint behavior  
public class SimpleEndpointBehavior : IEndpointBehavior  
{  
    public void AddBindingParameters(ServiceEndpoint endpoint, System.ServiceModel.Channels.BindingParameterCollection bindingParameters)  
    {  
         // No implementation necessary  
    }  
  
    public void ApplyClientBehavior(ServiceEndpoint endpoint, ClientRuntime clientRuntime)  
    {  
        clientRuntime.MessageInspectors.Add(new SimpleMessageInspector());  
    }  
  
    public void ApplyDispatchBehavior(ServiceEndpoint endpoint, EndpointDispatcher endpointDispatcher)  
    {  
         // No implementation necessary  
    }  
  
    public void Validate(ServiceEndpoint endpoint)  
    {  
         // No implementation necessary  
    }  
}  
```  
  
```csharp  
// Configuration element
public class SimpleBehaviorExtensionElement : BehaviorExtensionElement  
{  
    public override Type BehaviorType  
    {  
        get { return typeof(SimpleEndpointBehavior); }  
    }  
  
    protected override object CreateBehavior()  
    {  
         // Create the  endpoint behavior that will insert the message  
         // inspector into the client runtime  
        return new SimpleEndpointBehavior();  
    }  
}  
```  
  
```xml
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
    <system.serviceModel>  
        <client>  
            <endpoint address="http://localhost:8080/SimpleService/"
                      binding="wsHttpBinding"
                      behaviorConfiguration="clientInspectorsAdded"
                      contract="ServiceReference1.IService1"  
                      name="WSHttpBinding_IService1"/>  
        </client>  
  
      <behaviors>  
        <endpointBehaviors>  
          <behavior name="clientInspectorsAdded">  
            <simpleBehaviorExtension />  
          </behavior>  
        </endpointBehaviors>  
      </behaviors>  
      <extensions>  
        <behaviorExtensions>  
          <add  
            name="simpleBehaviorExtension"  
            type="SimpleServiceLib.SimpleBehaviorExtensionElement, Host, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
        </behaviorExtensions>  
      </extensions>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Confira também

- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>
- [Configurando e estendendo o runtime com comportamentos](configuring-and-extending-the-runtime-with-behaviors.md)
