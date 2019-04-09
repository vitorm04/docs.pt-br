---
title: Serviços de duplex
ms.date: 05/09/2018
dev_langs:
- csharp
- vb
ms.assetid: 396b875a-d203-4ebe-a3a1-6a330d962e95
ms.openlocfilehash: 3f8e13c6983b6c3a88bc1d9f559f7fac3d6342d9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110078"
---
# <a name="duplex-services"></a><span data-ttu-id="7dd98-102">Serviços de duplex</span><span class="sxs-lookup"><span data-stu-id="7dd98-102">Duplex Services</span></span>
<span data-ttu-id="7dd98-103">Um contrato de serviço duplex é um padrão de troca de mensagem no qual os pontos de extremidade podem enviar mensagens para outro independentemente.</span><span class="sxs-lookup"><span data-stu-id="7dd98-103">A duplex service contract is a message exchange pattern in which both endpoints can send messages to the other independently.</span></span> <span data-ttu-id="7dd98-104">Um serviço duplex, portanto, pode enviar mensagens de volta para o ponto de extremidade do cliente, fornecendo o comportamento do tipo de evento.</span><span class="sxs-lookup"><span data-stu-id="7dd98-104">A duplex service, therefore, can send messages back to the client endpoint, providing event-like behavior.</span></span> <span data-ttu-id="7dd98-105">Comunicação duplex ocorre quando um cliente se conecta a um serviço e fornece o serviço com um canal no qual o serviço pode enviar mensagens de volta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="7dd98-105">Duplex communication occurs when a client connects to a service and provides the service with a channel on which the service can send messages back to the client.</span></span> <span data-ttu-id="7dd98-106">Observe que o comportamento do tipo de evento dos serviços duplex só funciona dentro de uma sessão.</span><span class="sxs-lookup"><span data-stu-id="7dd98-106">Note that the event-like behavior of duplex services only works within a session.</span></span>  
  
 <span data-ttu-id="7dd98-107">Para criar um contrato duplex, você cria um par de interfaces.</span><span class="sxs-lookup"><span data-stu-id="7dd98-107">To create a duplex contract you create a pair of interfaces.</span></span> <span data-ttu-id="7dd98-108">A primeira é a interface de contrato de serviço que descreve as operações que um cliente pode invocar.</span><span class="sxs-lookup"><span data-stu-id="7dd98-108">The first is the service contract interface that describes the operations that a client can invoke.</span></span> <span data-ttu-id="7dd98-109">Esse contrato de serviço deve especificar uma *contrato de retorno de chamada* no <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="7dd98-109">That service contract must specify a *callback contract* in the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="7dd98-110">O contrato de retorno de chamada é a interface que define as operações que o serviço pode chamar o ponto de extremidade do cliente.</span><span class="sxs-lookup"><span data-stu-id="7dd98-110">The callback contract is the interface that defines the operations that the service can call on the client endpoint.</span></span> <span data-ttu-id="7dd98-111">Um contrato duplex não requer uma sessão, embora as associações fornecidas pelo sistema duplex tornar usá-los.</span><span class="sxs-lookup"><span data-stu-id="7dd98-111">A duplex contract does not require a session, although the system-provided duplex bindings make use of them.</span></span>  
  
 <span data-ttu-id="7dd98-112">O exemplo a seguir é um exemplo de um contrato duplex.</span><span class="sxs-lookup"><span data-stu-id="7dd98-112">The following is an example of a duplex contract.</span></span>  
  
 [!code-csharp[c_DuplexServices#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#0)]
 [!code-vb[c_DuplexServices#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#0)]  
  
 <span data-ttu-id="7dd98-113">O `CalculatorService` classe implementa o primário `ICalculatorDuplex` interface.</span><span class="sxs-lookup"><span data-stu-id="7dd98-113">The `CalculatorService` class implements the primary `ICalculatorDuplex` interface.</span></span> <span data-ttu-id="7dd98-114">O serviço usa o <xref:System.ServiceModel.InstanceContextMode.PerSession> modo de instância para manter o resultado para cada sessão.</span><span class="sxs-lookup"><span data-stu-id="7dd98-114">The service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the result for each session.</span></span> <span data-ttu-id="7dd98-115">Uma propriedade privada chamada `Callback` acessa o canal de retorno de chamada para o cliente.</span><span class="sxs-lookup"><span data-stu-id="7dd98-115">A private property named `Callback` accesses the callback channel to the client.</span></span> <span data-ttu-id="7dd98-116">O serviço usa o retorno de chamada para o envio de mensagens de volta ao cliente por meio da interface de retorno de chamada, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="7dd98-116">The service uses the callback for sending messages back to the client through the callback interface, as shown in the following sample code.</span></span>  
  
 [!code-csharp[c_DuplexServices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#1)]
 [!code-vb[c_DuplexServices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#1)]  
  
 <span data-ttu-id="7dd98-117">O cliente deve fornecer uma classe que implementa a interface de retorno de chamada do contrato duplex, para receber mensagens do serviço.</span><span class="sxs-lookup"><span data-stu-id="7dd98-117">The client must provide a class that implements the callback interface of the duplex contract, for receiving messages from the service.</span></span> <span data-ttu-id="7dd98-118">O exemplo a seguir mostra código uma `CallbackHandler` classe que implementa o `ICalculatorDuplexCallback` interface.</span><span class="sxs-lookup"><span data-stu-id="7dd98-118">The following sample code shows a `CallbackHandler` class that implements the `ICalculatorDuplexCallback` interface.</span></span>  
  
 [!code-csharp[c_DuplexServices#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#2)]
 [!code-vb[c_DuplexServices#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#2)]  
  
 <span data-ttu-id="7dd98-119">O cliente do WCF que é gerado para um contrato duplex requer um <xref:System.ServiceModel.InstanceContext> classe a ser fornecido no momento da construção.</span><span class="sxs-lookup"><span data-stu-id="7dd98-119">The WCF client that is generated for a duplex contract requires a <xref:System.ServiceModel.InstanceContext> class to be provided upon construction.</span></span> <span data-ttu-id="7dd98-120">Isso <xref:System.ServiceModel.InstanceContext> classe é usada como o site para um objeto que implementa a interface de retorno de chamada e manipula as mensagens enviadas a resposta do serviço.</span><span class="sxs-lookup"><span data-stu-id="7dd98-120">This <xref:System.ServiceModel.InstanceContext> class is used as the site for an object that implements the callback interface and handles messages that are sent back from the service.</span></span> <span data-ttu-id="7dd98-121">Uma <xref:System.ServiceModel.InstanceContext> classe for construída com uma instância da `CallbackHandler` classe.</span><span class="sxs-lookup"><span data-stu-id="7dd98-121">An <xref:System.ServiceModel.InstanceContext> class is constructed with an instance of the `CallbackHandler` class.</span></span> <span data-ttu-id="7dd98-122">Esse objeto manipula as mensagens enviadas do serviço ao cliente na interface de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="7dd98-122">This object handles messages sent from the service to the client on the callback interface.</span></span>  
  
 [!code-csharp[c_DuplexServices#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#3)]
 [!code-vb[c_DuplexServices#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#3)]  
  
 <span data-ttu-id="7dd98-123">A configuração para o serviço deve configurar para fornecer uma associação que dá suporte à comunicação de sessão e comunicação duplex.</span><span class="sxs-lookup"><span data-stu-id="7dd98-123">The configuration for the service must be set up to provide a binding that supports both session communication and duplex communication.</span></span> <span data-ttu-id="7dd98-124">O `wsDualHttpBinding` elemento dá suporte à comunicação de sessão e permite a comunicação duplex, fornecendo duas conexões de HTTP, um para cada direção.</span><span class="sxs-lookup"><span data-stu-id="7dd98-124">The `wsDualHttpBinding` element supports session communication and allows duplex communication by providing dual HTTP connections, one for each direction.</span></span>  
  
 <span data-ttu-id="7dd98-125">No cliente, você deve configurar um endereço que o servidor pode usar para se conectar ao cliente, conforme mostrado no seguinte exemplo de configuração.</span><span class="sxs-lookup"><span data-stu-id="7dd98-125">On the client, you must configure an address that the server can use to connect to the client, as shown in the following sample configuration.</span></span>  

> [!NOTE]
>  <span data-ttu-id="7dd98-126">Os clientes não-duplex que falham ao autenticar usando uma conversa segura normalmente geram um <xref:System.ServiceModel.Security.MessageSecurityException>.</span><span class="sxs-lookup"><span data-stu-id="7dd98-126">Non-duplex clients that fail to authenticate using a secure conversation typically throw a <xref:System.ServiceModel.Security.MessageSecurityException>.</span></span> <span data-ttu-id="7dd98-127">No entanto, se um cliente duplex que usa uma conversa segura não conseguir autenticar o cliente recebe um <xref:System.TimeoutException> em vez disso.</span><span class="sxs-lookup"><span data-stu-id="7dd98-127">However, if a duplex client that uses a secure conversation fails to authenticate, the client receives a <xref:System.TimeoutException> instead.</span></span>  
  
 <span data-ttu-id="7dd98-128">Se você criar um serviço do cliente usando o `WSHttpBinding` elemento e você não incluir o ponto de extremidade de retorno de chamada do cliente, você receberá o erro a seguir.</span><span class="sxs-lookup"><span data-stu-id="7dd98-128">If you create a client/service using the `WSHttpBinding` element and you do not include the client callback endpoint, you will receive the following error.</span></span>  
  
```  
HTTP could not register URL  
htp://+:80/Temporary_Listen_Addresses/<guid> because TCP port 80 is being used by another application.  
```  
  
 <span data-ttu-id="7dd98-129">O código de exemplo a seguir mostra como especificar o cliente do endereço do ponto de extremidade por meio de programação.</span><span class="sxs-lookup"><span data-stu-id="7dd98-129">The following sample code shows how to specify the client endpoint address programmatically.</span></span>
  
```csharp  
WSDualHttpBinding binding = new WSDualHttpBinding();  
EndpointAddress endptadr = new EndpointAddress("http://localhost:12000/DuplexTestUsingCode/Server");  
binding.ClientBaseAddress = new Uri("http://localhost:8000/DuplexTestUsingCode/Client/");  
```  
```vb
Dim binding As New WSDualHttpBinding()
Dim endptadr As New EndpointAddress("http://localhost:12000/DuplexTestUsingCode/Server")
binding.ClientBaseAddress = New Uri("http://localhost:8000/DuplexTestUsingCode/Client/")  
```

 <span data-ttu-id="7dd98-130">O código de exemplo a seguir mostra como especificar o cliente do endereço do ponto de extremidade na configuração.</span><span class="sxs-lookup"><span data-stu-id="7dd98-130">The following sample code shows how to specify the client endpoint address in configuration.</span></span>  
  
```xml  
<client>  
    <endpoint name ="ServerEndpoint"   
          address="http://localhost:12000/DuplexTestUsingConfig/Server"  
          bindingConfiguration="WSDualHttpBinding_IDuplexTest"   
            binding="wsDualHttpBinding"  
           contract="IDuplexTest" />  
</client>  
<bindings>  
    <wsDualHttpBinding>  
        <binding name="WSDualHttpBinding_IDuplexTest"    
          clientBaseAddress="http://localhost:8000/myClient/" >  
            <security mode="None"/>  
         </binding>  
    </wsDualHttpBinding>  
</bindings>  
```  
  
> [!WARNING]
>  <span data-ttu-id="7dd98-131">O modelo de duplex não detecta automaticamente quando um serviço ou cliente fecha seu canal.</span><span class="sxs-lookup"><span data-stu-id="7dd98-131">The duplex model does not automatically detect when a service or client closes its channel.</span></span> <span data-ttu-id="7dd98-132">Portanto, se um cliente termina inesperadamente, por padrão o serviço não será notificado, ou se um cliente termina inesperadamente, o serviço não será notificado.</span><span class="sxs-lookup"><span data-stu-id="7dd98-132">So if a client unexpectedly terminates, by default the service will not be notified, or if a client unexpectedly terminates, the service will not be notified.</span></span> <span data-ttu-id="7dd98-133">Os clientes e serviços podem implementar seu próprio protocolo para notificar uns aos outros, se desejarem.</span><span class="sxs-lookup"><span data-stu-id="7dd98-133">Clients and services can implement their own protocol to notify each other if they so choose.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dd98-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7dd98-134">See also</span></span>

- [<span data-ttu-id="7dd98-135">Duplex</span><span class="sxs-lookup"><span data-stu-id="7dd98-135">Duplex</span></span>](../../../../docs/framework/wcf/samples/duplex.md)
- [<span data-ttu-id="7dd98-136">Especificando a execução do cliente- Comportamento do tempo</span><span class="sxs-lookup"><span data-stu-id="7dd98-136">Specifying Client Run-Time Behavior</span></span>](../../../../docs/framework/wcf/specifying-client-run-time-behavior.md)
- [<span data-ttu-id="7dd98-137">Como: criar uma fábrica de canais e usá-la para criar e gerenciar canais</span><span class="sxs-lookup"><span data-stu-id="7dd98-137">How to: Create a Channel Factory and Use it to Create and Manage Channels</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels.md)
