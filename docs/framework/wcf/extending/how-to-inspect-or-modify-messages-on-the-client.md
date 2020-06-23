---
title: Como inspecionar ou modificar mensagens no cliente
description: Saiba como inspecionar ou modificar as mensagens de entrada ou saída em um cliente ou serviço WCF implementando a interface apropriada.
ms.date: 03/30/2017
ms.assetid: b8256335-f1c2-419f-b862-9f220ccad84c
ms.openlocfilehash: 6f6a3d20d7f3a9fb79de5cd3e29096e270d0f188
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247501"
---
# <a name="how-to-inspect-or-modify-messages-on-the-client"></a><span data-ttu-id="25e1a-103">Como inspecionar ou modificar mensagens no cliente</span><span class="sxs-lookup"><span data-stu-id="25e1a-103">How to: Inspect or Modify Messages on the Client</span></span>
<span data-ttu-id="25e1a-104">Você pode inspecionar ou modificar as mensagens de entrada ou saída em um cliente WCF implementando uma <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> e inserindo-as no tempo de execução do cliente.</span><span class="sxs-lookup"><span data-stu-id="25e1a-104">You can inspect or modify the incoming or outgoing messages across a WCF client by implementing a <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> and inserting it into the client runtime.</span></span> <span data-ttu-id="25e1a-105">Para obter mais informações, consulte [estendendo clientes](extending-clients.md).</span><span class="sxs-lookup"><span data-stu-id="25e1a-105">For more information, see [Extending Clients](extending-clients.md).</span></span> <span data-ttu-id="25e1a-106">O recurso equivalente no serviço é o <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="25e1a-106">The equivalent feature on the service is the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>.</span></span> <span data-ttu-id="25e1a-107">Para obter um exemplo de código completo, consulte o exemplo de [inspetores de mensagem](../samples/message-inspectors.md) .</span><span class="sxs-lookup"><span data-stu-id="25e1a-107">For a complete code example see the [Message Inspectors](../samples/message-inspectors.md) sample.</span></span>  
  
### <a name="to-inspect-or-modify-messages"></a><span data-ttu-id="25e1a-108">Para inspecionar ou modificar mensagens</span><span class="sxs-lookup"><span data-stu-id="25e1a-108">To inspect or modify messages</span></span>  
  
1. <span data-ttu-id="25e1a-109">Implemente a interface <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="25e1a-109">Implement the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> interface.</span></span>  
  
2. <span data-ttu-id="25e1a-110">Implemente um <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> ou <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> dependendo do escopo no qual você deseja inserir o Inspetor de mensagem do cliente.</span><span class="sxs-lookup"><span data-stu-id="25e1a-110">Implement a <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> depending upon the scope at which you want to insert the client message inspector.</span></span> <span data-ttu-id="25e1a-111"><xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>permite alterar o comportamento no nível do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="25e1a-111"><xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> allows you to change behavior at the endpoint level.</span></span> <span data-ttu-id="25e1a-112"><xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>permite alterar o comportamento no nível do contrato.</span><span class="sxs-lookup"><span data-stu-id="25e1a-112"><xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> allows you to change behavior at the contract level.</span></span>  
  
3. <span data-ttu-id="25e1a-113">Insira o comportamento antes de chamar o <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> método ou <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> no <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="25e1a-113">Insert the behavior prior to calling the <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> or the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="25e1a-114">Para obter detalhes, consulte [Configurando e estendendo o tempo de execução com comportamentos](configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="25e1a-114">For details, see [Configuring and Extending the Runtime with Behaviors](configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="25e1a-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="25e1a-115">Example</span></span>  
 <span data-ttu-id="25e1a-116">Os exemplos de código a seguir mostram, em ordem:</span><span class="sxs-lookup"><span data-stu-id="25e1a-116">The following code examples show, in order:</span></span>  
  
- <span data-ttu-id="25e1a-117">Uma implementação de Inspetor de cliente.</span><span class="sxs-lookup"><span data-stu-id="25e1a-117">A client inspector implementation.</span></span>  
  
- <span data-ttu-id="25e1a-118">Um comportamento de ponto de extremidade que insere o Inspetor.</span><span class="sxs-lookup"><span data-stu-id="25e1a-118">An endpoint behavior that inserts the inspector.</span></span>  
  
- <span data-ttu-id="25e1a-119">Uma <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> classe derivada que permite adicionar o comportamento em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="25e1a-119">A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>- derived class that allows you to add the behavior in a configuration file.</span></span>  
  
- <span data-ttu-id="25e1a-120">Um arquivo de configuração que adiciona o comportamento do ponto de extremidade que insere o Inspetor de mensagem do cliente no tempo de execução do cliente.</span><span class="sxs-lookup"><span data-stu-id="25e1a-120">A configuration file that adds the endpoint behavior which inserts the client message inspector into the client runtime.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="25e1a-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="25e1a-121">See also</span></span>

- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>
- [<span data-ttu-id="25e1a-122">Configurando e estendendo o runtime com comportamentos</span><span class="sxs-lookup"><span data-stu-id="25e1a-122">Configuring and Extending the Runtime with Behaviors</span></span>](configuring-and-extending-the-runtime-with-behaviors.md)
