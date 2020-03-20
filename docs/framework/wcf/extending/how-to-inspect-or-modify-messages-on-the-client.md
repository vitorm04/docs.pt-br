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
# <a name="how-to-inspect-or-modify-messages-on-the-client"></a><span data-ttu-id="6e99d-102">Como inspecionar ou modificar mensagens no cliente</span><span class="sxs-lookup"><span data-stu-id="6e99d-102">How to: Inspect or Modify Messages on the Client</span></span>
<span data-ttu-id="6e99d-103">Você pode inspecionar ou modificar as mensagens recebidas ou de <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> saída em um cliente WCF implementando-a e inserindo-as no tempo de execução do cliente.</span><span class="sxs-lookup"><span data-stu-id="6e99d-103">You can inspect or modify the incoming or outgoing messages across a WCF client by implementing a <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> and inserting it into the client runtime.</span></span> <span data-ttu-id="6e99d-104">Para obter mais informações, consulte [Extending Clients](extending-clients.md).</span><span class="sxs-lookup"><span data-stu-id="6e99d-104">For more information, see [Extending Clients](extending-clients.md).</span></span> <span data-ttu-id="6e99d-105">A característica equivalente no <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>serviço é o .</span><span class="sxs-lookup"><span data-stu-id="6e99d-105">The equivalent feature on the service is the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6e99d-106">Para obter um exemplo de código completo, consulte a amostra [De inspetores de mensagens.](../samples/message-inspectors.md)</span><span class="sxs-lookup"><span data-stu-id="6e99d-106">For a complete code example see the [Message Inspectors](../samples/message-inspectors.md) sample.</span></span>  
  
### <a name="to-inspect-or-modify-messages"></a><span data-ttu-id="6e99d-107">Para inspecionar ou modificar mensagens</span><span class="sxs-lookup"><span data-stu-id="6e99d-107">To inspect or modify messages</span></span>  
  
1. <span data-ttu-id="6e99d-108">Implemente a interface <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6e99d-108">Implement the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> interface.</span></span>  
  
2. <span data-ttu-id="6e99d-109">Implemente <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> um ou dependendo do escopo no qual você deseja inserir o inspetor de mensagens do cliente.</span><span class="sxs-lookup"><span data-stu-id="6e99d-109">Implement a <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> depending upon the scope at which you want to insert the client message inspector.</span></span> <span data-ttu-id="6e99d-110"><xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>permite que você mude o comportamento no nível final.</span><span class="sxs-lookup"><span data-stu-id="6e99d-110"><xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> allows you to change behavior at the endpoint level.</span></span> <span data-ttu-id="6e99d-111"><xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>permite que você mude de comportamento no nível do contrato.</span><span class="sxs-lookup"><span data-stu-id="6e99d-111"><xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> allows you to change behavior at the contract level.</span></span>  
  
3. <span data-ttu-id="6e99d-112">Insira o comportamento <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> antes <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> de <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>chamar o método ou o método no .</span><span class="sxs-lookup"><span data-stu-id="6e99d-112">Insert the behavior prior to calling the <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> or the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6e99d-113">Para obter detalhes, [consulte Configuração e Prolongamento do tempo de execução com comportamentos](configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="6e99d-113">For details, see [Configuring and Extending the Runtime with Behaviors](configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e99d-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6e99d-114">Example</span></span>  
 <span data-ttu-id="6e99d-115">Os exemplos de código a seguir mostram, em ordem:</span><span class="sxs-lookup"><span data-stu-id="6e99d-115">The following code examples show, in order:</span></span>  
  
- <span data-ttu-id="6e99d-116">Uma implementação de inspetor de clientes.</span><span class="sxs-lookup"><span data-stu-id="6e99d-116">A client inspector implementation.</span></span>  
  
- <span data-ttu-id="6e99d-117">Um comportamento final que insere o inspetor.</span><span class="sxs-lookup"><span data-stu-id="6e99d-117">An endpoint behavior that inserts the inspector.</span></span>  
  
- <span data-ttu-id="6e99d-118">A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>- classe derivada que permite adicionar o comportamento em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="6e99d-118">A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>- derived class that allows you to add the behavior in a configuration file.</span></span>  
  
- <span data-ttu-id="6e99d-119">Um arquivo de configuração que adiciona o comportamento de ponto final que insere o inspetor de mensagens do cliente no tempo de execução do cliente.</span><span class="sxs-lookup"><span data-stu-id="6e99d-119">A configuration file that adds the endpoint behavior which inserts the client message inspector into the client runtime.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6e99d-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="6e99d-120">See also</span></span>

- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>
- [<span data-ttu-id="6e99d-121">Configurando e estendendo o runtime com comportamentos</span><span class="sxs-lookup"><span data-stu-id="6e99d-121">Configuring and Extending the Runtime with Behaviors</span></span>](configuring-and-extending-the-runtime-with-behaviors.md)
