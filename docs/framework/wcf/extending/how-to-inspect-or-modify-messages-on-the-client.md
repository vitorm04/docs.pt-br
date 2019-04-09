---
title: 'Como: inspecionar ou modificar mensagens no cliente'
ms.date: 03/30/2017
ms.assetid: b8256335-f1c2-419f-b862-9f220ccad84c
ms.openlocfilehash: cc2a03806dbc9ff33c1b16da7a31d862001534aa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59167473"
---
# <a name="how-to-inspect-or-modify-messages-on-the-client"></a>Como: inspecionar ou modificar mensagens no cliente
Você pode inspecionar ou modificar as mensagens de entrada ou saídas em um cliente WCF implementando um <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> e inseri-lo no tempo de execução do cliente. Para obter mais informações, consulte [estendendo clientes](../../../../docs/framework/wcf/extending/extending-clients.md). O recurso equivalente no serviço é o <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>. Para obter um exemplo de código completo, consulte o [inspetores de mensagem](../../../../docs/framework/wcf/samples/message-inspectors.md) exemplo.  
  
### <a name="to-inspect-or-modify-messages"></a>Para inspecionar ou modificar as mensagens  
  
1.  Implementar a interface <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.  
  
2.  Implementar uma <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> ou <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> dependendo do escopo no qual você deseja inserir o Inspetor de mensagens do cliente. <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> permite que você altere o comportamento no nível do ponto de extremidade. <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> permite que você altere o comportamento no nível do contrato.  
  
3.  Inserir o comportamento antes de chamar o <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> ou o <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> método o <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>. Para obter detalhes, consulte [Configurando e estendendo o tempo de execução com comportamentos](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="example"></a>Exemplo  
 Os exemplos de código a seguir mostram, na ordem:  
  
-   Uma implementação de Inspetor de cliente.  
  
-   Um comportamento de ponto de extremidade que insere o Inspetor.  
  
-   Um <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>-derivado da classe que permite que você adicione o comportamento em um arquivo de configuração.  
  
-   Um arquivo de configuração que adiciona o comportamento de ponto de extremidade que insere o Inspetor de mensagens do cliente em tempo de execução do cliente.  
  
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
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>
- [Configurando e estendendo o tempo de execução com comportamentos](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
