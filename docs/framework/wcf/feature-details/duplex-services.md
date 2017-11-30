---
title: "Serviços de duplex"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 396b875a-d203-4ebe-a3a1-6a330d962e95
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5b5e0e2b1b2aa6292d53f1688ef124d9add42b5a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="duplex-services"></a><span data-ttu-id="d8206-102">Serviços de duplex</span><span class="sxs-lookup"><span data-stu-id="d8206-102">Duplex Services</span></span>
<span data-ttu-id="d8206-103">Um contrato de serviço duplex é um padrão de troca de mensagem no qual os pontos de extremidade podem enviar mensagens para o outro independentemente.</span><span class="sxs-lookup"><span data-stu-id="d8206-103">A duplex service contract is a message exchange pattern in which both endpoints can send messages to the other independently.</span></span> <span data-ttu-id="d8206-104">Um serviço duplex, portanto, pode enviar mensagens para o ponto de extremidade do cliente, fornecendo o comportamento do tipo de evento.</span><span class="sxs-lookup"><span data-stu-id="d8206-104">A duplex service, therefore, can send messages back to the client endpoint, providing event-like behavior.</span></span> <span data-ttu-id="d8206-105">Comunicação duplex ocorre quando um cliente se conecta a um serviço e fornece o serviço com um canal em que o serviço pode enviar mensagens de volta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="d8206-105">Duplex communication occurs when a client connects to a service and provides the service with a channel on which the service can send messages back to the client.</span></span> <span data-ttu-id="d8206-106">Observe que o comportamento do tipo de evento de serviços duplex só funciona em uma sessão.</span><span class="sxs-lookup"><span data-stu-id="d8206-106">Note that the event-like behavior of duplex services only works within a session.</span></span>  
  
 <span data-ttu-id="d8206-107">Para criar um contrato duplex você criar um par de interfaces.</span><span class="sxs-lookup"><span data-stu-id="d8206-107">To create a duplex contract you create a pair of interfaces.</span></span> <span data-ttu-id="d8206-108">A primeira é a interface de contrato de serviço que descreve as operações que um cliente pode invocar.</span><span class="sxs-lookup"><span data-stu-id="d8206-108">The first is the service contract interface that describes the operations that a client can invoke.</span></span> <span data-ttu-id="d8206-109">Esse contrato de serviço deve especificar um *contrato de retorno de chamada* no <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="d8206-109">That service contract must specify a *callback contract* in the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="d8206-110">O contrato de retorno de chamada é a interface que define as operações que o serviço pode chamar o ponto de extremidade do cliente.</span><span class="sxs-lookup"><span data-stu-id="d8206-110">The callback contract is the interface that defines the operations that the service can call on the client endpoint.</span></span> <span data-ttu-id="d8206-111">Um contrato duplex não requer uma sessão, embora as associações de duplex fornecido pelo sistema fazer utilizá-las.</span><span class="sxs-lookup"><span data-stu-id="d8206-111">A duplex contract does not require a session, although the system-provided duplex bindings make use of them.</span></span>  
  
 <span data-ttu-id="d8206-112">Este é um exemplo de um contrato duplex.</span><span class="sxs-lookup"><span data-stu-id="d8206-112">The following is an example of a duplex contract.</span></span>  
  
 [!code-csharp[c_DuplexServices#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#0)]
 [!code-vb[c_DuplexServices#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#0)]  
  
 <span data-ttu-id="d8206-113">O `CalculatorService` classe implementa primário `ICalculatorDuplex` interface.</span><span class="sxs-lookup"><span data-stu-id="d8206-113">The `CalculatorService` class implements the primary `ICalculatorDuplex` interface.</span></span> <span data-ttu-id="d8206-114">O serviço usa o <xref:System.ServiceModel.InstanceContextMode.PerSession> modo de instância para manter o resultado para cada sessão.</span><span class="sxs-lookup"><span data-stu-id="d8206-114">The service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the result for each session.</span></span> <span data-ttu-id="d8206-115">Uma propriedade privada denominada `Callback` acessa o canal de retorno de chamada para o cliente.</span><span class="sxs-lookup"><span data-stu-id="d8206-115">A private property named `Callback` accesses the callback channel to the client.</span></span> <span data-ttu-id="d8206-116">O serviço usa o retorno de chamada para enviar mensagens ao cliente por meio da interface de retorno de chamada, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="d8206-116">The service uses the callback for sending messages back to the client through the callback interface, as shown in the following sample code.</span></span>  
  
 [!code-csharp[c_DuplexServices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#1)]
 [!code-vb[c_DuplexServices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#1)]  
  
 <span data-ttu-id="d8206-117">O cliente deve fornecer uma classe que implementa a interface de retorno de chamada do contrato duplex, para receber mensagens do serviço.</span><span class="sxs-lookup"><span data-stu-id="d8206-117">The client must provide a class that implements the callback interface of the duplex contract, for receiving messages from the service.</span></span> <span data-ttu-id="d8206-118">O exemplo a seguir mostra código um `CallbackHandler` classe que implementa o `ICalculatorDuplexCallback` interface.</span><span class="sxs-lookup"><span data-stu-id="d8206-118">The following sample code shows a `CallbackHandler` class that implements the `ICalculatorDuplexCallback` interface.</span></span>  
  
 [!code-csharp[c_DuplexServices#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#2)]
 [!code-vb[c_DuplexServices#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#2)]  
  
 <span data-ttu-id="d8206-119">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente que é gerado para um contrato duplex requer um <xref:System.ServiceModel.InstanceContext> classe será fornecido após a construção.</span><span class="sxs-lookup"><span data-stu-id="d8206-119">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client that is generated for a duplex contract requires a <xref:System.ServiceModel.InstanceContext> class to be provided upon construction.</span></span> <span data-ttu-id="d8206-120">Isso <xref:System.ServiceModel.InstanceContext> classe é usada como o site para um objeto que implementa a interface de retorno de chamada e manipula mensagens que são enviadas de volta do serviço.</span><span class="sxs-lookup"><span data-stu-id="d8206-120">This <xref:System.ServiceModel.InstanceContext> class is used as the site for an object that implements the callback interface and handles messages that are sent back from the service.</span></span> <span data-ttu-id="d8206-121">Um <xref:System.ServiceModel.InstanceContext> classe é construída com uma instância do `CallbackHandler` classe.</span><span class="sxs-lookup"><span data-stu-id="d8206-121">An <xref:System.ServiceModel.InstanceContext> class is constructed with an instance of the `CallbackHandler` class.</span></span> <span data-ttu-id="d8206-122">Esse objeto manipula mensagens enviadas do serviço para o cliente na interface de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="d8206-122">This object handles messages sent from the service to the client on the callback interface.</span></span>  
  
 [!code-csharp[c_DuplexServices#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#3)]
 [!code-vb[c_DuplexServices#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#3)]  
  
 <span data-ttu-id="d8206-123">A configuração para o serviço deve configurar para fornecer uma associação que dá suporte à comunicação de sessão e comunicação duplex.</span><span class="sxs-lookup"><span data-stu-id="d8206-123">The configuration for the service must be set up to provide a binding that supports both session communication and duplex communication.</span></span> <span data-ttu-id="d8206-124">O `wsDualHttpBinding` elemento dá suporte à comunicação de sessão e permite a comunicação duplex, fornecendo duas conexões HTTP, uma para cada direção.</span><span class="sxs-lookup"><span data-stu-id="d8206-124">The `wsDualHttpBinding` element supports session communication and allows duplex communication by providing dual HTTP connections, one for each direction.</span></span>  
  
 <span data-ttu-id="d8206-125">No cliente, você deve configurar um endereço que o servidor pode usar para se conectar ao cliente, conforme mostrado no exemplo de configuração.</span><span class="sxs-lookup"><span data-stu-id="d8206-125">On the client, you must configure an address that the server can use to connect to the client, as shown in the following sample configuration.</span></span>  
  
  
  
> [!NOTE]
>  <span data-ttu-id="d8206-126">Clientes não-duplex que falham ao autenticar usando uma conversa segura normalmente geram um <xref:System.ServiceModel.Security.MessageSecurityException>.</span><span class="sxs-lookup"><span data-stu-id="d8206-126">Non-duplex clients that fail to authenticate using a secure conversation typically throw a <xref:System.ServiceModel.Security.MessageSecurityException>.</span></span> <span data-ttu-id="d8206-127">No entanto, se um cliente duplex que usa uma conversa segura não for autenticado, o cliente recebe um <xref:System.TimeoutException> em vez disso.</span><span class="sxs-lookup"><span data-stu-id="d8206-127">However, if a duplex client that uses a secure conversation fails to authenticate, the client receives a <xref:System.TimeoutException> instead.</span></span>  
  
 <span data-ttu-id="d8206-128">Se você criar um serviço do cliente usando o `WSHttpBinding` elemento e você não incluir o ponto de extremidade de retorno de chamada do cliente, você receberá o erro a seguir.</span><span class="sxs-lookup"><span data-stu-id="d8206-128">If you create a client/service using the `WSHttpBinding` element and you do not include the client callback endpoint, you will receive the following error.</span></span>  
  
```  
HTTP could not register URL  
htp://+:80/Temporary_Listen_Addresses/<guid> because TCP port 80 is being used by another application.  
```  
  
 <span data-ttu-id="d8206-129">O código de exemplo a seguir mostra como especificar o cliente do endereço de ponto de extremidade no código.</span><span class="sxs-lookup"><span data-stu-id="d8206-129">The following sample code shows how to specify the client endpoint address in code.</span></span>  
  
```  
WSDualHttpBinding binding = new WSDualHttpBinding();  
EndpointAddress endptadr = new EndpointAddress("http://localhost:12000/DuplexTestUsingCode/Server");  
binding.ClientBaseAddress = new Uri("http://localhost:8000/DuplexTestUsingCode/Client/");  
```  
  
 <span data-ttu-id="d8206-130">O código de exemplo a seguir mostra como especificar o cliente do endereço de ponto de extremidade na configuração.</span><span class="sxs-lookup"><span data-stu-id="d8206-130">The following sample code shows how to specify the client endpoint address in configuration.</span></span>  
  
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
>  <span data-ttu-id="d8206-131">O modelo duplex não detecta automaticamente quando um serviço ou cliente fecha o canal.</span><span class="sxs-lookup"><span data-stu-id="d8206-131">The duplex model does not automatically detect when a service or client closes its channel.</span></span> <span data-ttu-id="d8206-132">Então se um cliente termina inesperadamente, por padrão o serviço não será notificado, ou se um cliente termina inesperadamente, o serviço não será notificado.</span><span class="sxs-lookup"><span data-stu-id="d8206-132">So if a client unexpectedly terminates, by default the service will not be notified, or if a client unexpectedly terminates, the service will not be notified.</span></span> <span data-ttu-id="d8206-133">Os clientes e serviços podem implementar seu próprio protocolo para notificar uns aos outros, se desejarem assim.</span><span class="sxs-lookup"><span data-stu-id="d8206-133">Clients and services can implement their own protocol to notify each other if they so choose.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8206-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d8206-134">See Also</span></span>  
 [<span data-ttu-id="d8206-135">Duplex</span><span class="sxs-lookup"><span data-stu-id="d8206-135">Duplex</span></span>](../../../../docs/framework/wcf/samples/duplex.md)  
 <span data-ttu-id="d8206-136">[Specifying Client Run-Time Behavior](../../../../docs/framework/wcf/specifying-client-run-time-behavior.md) (Especificando o comportamento em tempo de execução do cliente)</span><span class="sxs-lookup"><span data-stu-id="d8206-136">[Specifying Client Run-Time Behavior](../../../../docs/framework/wcf/specifying-client-run-time-behavior.md)</span></span>  
 [<span data-ttu-id="d8206-137">Como: criar uma fábrica de canais e usá-lo para criar e gerenciar canais</span><span class="sxs-lookup"><span data-stu-id="d8206-137">How to: Create a Channel Factory and Use it to Create and Manage Channels</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels.md)
