---
title: Serviços de duplex
description: Saiba como criar um contrato de serviço duplex no WCF, que permite que os dois pontos de extremidade enviem mensagens entre si por meio de um canal criado pelo cliente.
ms.date: 05/09/2018
dev_langs:
- csharp
- vb
ms.assetid: 396b875a-d203-4ebe-a3a1-6a330d962e95
ms.openlocfilehash: a43bb63a0ccf1a34b79dce755c19f7ed4cb6c16c
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247345"
---
# <a name="duplex-services"></a><span data-ttu-id="3688b-103">Serviços de duplex</span><span class="sxs-lookup"><span data-stu-id="3688b-103">Duplex Services</span></span>

<span data-ttu-id="3688b-104">Um contrato de serviço duplex é um padrão de troca de mensagens no qual ambos os pontos de extremidade podem enviar mensagens para o outro de forma independente.</span><span class="sxs-lookup"><span data-stu-id="3688b-104">A duplex service contract is a message exchange pattern in which both endpoints can send messages to the other independently.</span></span> <span data-ttu-id="3688b-105">Um serviço duplex, portanto, pode enviar mensagens de volta ao ponto de extremidade do cliente, fornecendo comportamento semelhante a evento.</span><span class="sxs-lookup"><span data-stu-id="3688b-105">A duplex service, therefore, can send messages back to the client endpoint, providing event-like behavior.</span></span> <span data-ttu-id="3688b-106">A comunicação duplex ocorre quando um cliente se conecta a um serviço e fornece o serviço com um canal no qual o serviço pode enviar mensagens de volta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="3688b-106">Duplex communication occurs when a client connects to a service and provides the service with a channel on which the service can send messages back to the client.</span></span> <span data-ttu-id="3688b-107">Observe que o comportamento do tipo evento dos serviços duplex só funciona em uma sessão.</span><span class="sxs-lookup"><span data-stu-id="3688b-107">Note that the event-like behavior of duplex services only works within a session.</span></span>

<span data-ttu-id="3688b-108">Para criar um contrato duplex, crie um par de interfaces.</span><span class="sxs-lookup"><span data-stu-id="3688b-108">To create a duplex contract you create a pair of interfaces.</span></span> <span data-ttu-id="3688b-109">A primeira é a interface de contrato de serviço que descreve as operações que um cliente pode invocar.</span><span class="sxs-lookup"><span data-stu-id="3688b-109">The first is the service contract interface that describes the operations that a client can invoke.</span></span> <span data-ttu-id="3688b-110">Esse contrato de serviço deve especificar um *contrato de retorno de chamada* na <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="3688b-110">That service contract must specify a *callback contract* in the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="3688b-111">O contrato de retorno de chamada é a interface que define as operações que o serviço pode chamar no ponto de extremidade do cliente.</span><span class="sxs-lookup"><span data-stu-id="3688b-111">The callback contract is the interface that defines the operations that the service can call on the client endpoint.</span></span> <span data-ttu-id="3688b-112">Um contrato duplex não requer uma sessão, embora as associações duplex fornecidas pelo sistema façam uso delas.</span><span class="sxs-lookup"><span data-stu-id="3688b-112">A duplex contract does not require a session, although the system-provided duplex bindings make use of them.</span></span>

<span data-ttu-id="3688b-113">Veja a seguir um exemplo de um contrato duplex.</span><span class="sxs-lookup"><span data-stu-id="3688b-113">The following is an example of a duplex contract.</span></span>

[!code-csharp[c_DuplexServices#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#0)]
[!code-vb[c_DuplexServices#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#0)]

<span data-ttu-id="3688b-114">A `CalculatorService` classe implementa a `ICalculatorDuplex` interface primária.</span><span class="sxs-lookup"><span data-stu-id="3688b-114">The `CalculatorService` class implements the primary `ICalculatorDuplex` interface.</span></span> <span data-ttu-id="3688b-115">O serviço usa o <xref:System.ServiceModel.InstanceContextMode.PerSession> modo de instância para manter o resultado de cada sessão.</span><span class="sxs-lookup"><span data-stu-id="3688b-115">The service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the result for each session.</span></span> <span data-ttu-id="3688b-116">Uma propriedade privada chamada `Callback` acessa o canal de retorno de chamada para o cliente.</span><span class="sxs-lookup"><span data-stu-id="3688b-116">A private property named `Callback` accesses the callback channel to the client.</span></span> <span data-ttu-id="3688b-117">O serviço usa o retorno de chamada para enviar mensagens de volta para o cliente por meio da interface de retorno de chamada, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="3688b-117">The service uses the callback for sending messages back to the client through the callback interface, as shown in the following sample code.</span></span>

[!code-csharp[c_DuplexServices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#1)]
[!code-vb[c_DuplexServices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#1)]

<span data-ttu-id="3688b-118">O cliente deve fornecer uma classe que implemente a interface de retorno de chamada do contrato duplex, para receber mensagens do serviço.</span><span class="sxs-lookup"><span data-stu-id="3688b-118">The client must provide a class that implements the callback interface of the duplex contract, for receiving messages from the service.</span></span> <span data-ttu-id="3688b-119">O código de exemplo a seguir mostra uma `CallbackHandler` classe que implementa a `ICalculatorDuplexCallback` interface.</span><span class="sxs-lookup"><span data-stu-id="3688b-119">The following sample code shows a `CallbackHandler` class that implements the `ICalculatorDuplexCallback` interface.</span></span>

[!code-csharp[c_DuplexServices#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#2)]
[!code-vb[c_DuplexServices#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#2)]

<span data-ttu-id="3688b-120">O cliente WCF que é gerado para um contrato duplex requer <xref:System.ServiceModel.InstanceContext> que uma classe seja fornecida na construção.</span><span class="sxs-lookup"><span data-stu-id="3688b-120">The WCF client that is generated for a duplex contract requires a <xref:System.ServiceModel.InstanceContext> class to be provided upon construction.</span></span> <span data-ttu-id="3688b-121">Essa <xref:System.ServiceModel.InstanceContext> classe é usada como o site de um objeto que implementa a interface de retorno de chamada e manipula as mensagens que são enviadas de volta do serviço.</span><span class="sxs-lookup"><span data-stu-id="3688b-121">This <xref:System.ServiceModel.InstanceContext> class is used as the site for an object that implements the callback interface and handles messages that are sent back from the service.</span></span> <span data-ttu-id="3688b-122">Uma <xref:System.ServiceModel.InstanceContext> classe é construída com uma instância da `CallbackHandler` classe.</span><span class="sxs-lookup"><span data-stu-id="3688b-122">An <xref:System.ServiceModel.InstanceContext> class is constructed with an instance of the `CallbackHandler` class.</span></span> <span data-ttu-id="3688b-123">Esse objeto manipula as mensagens enviadas do serviço para o cliente na interface de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="3688b-123">This object handles messages sent from the service to the client on the callback interface.</span></span>

[!code-csharp[c_DuplexServices#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#3)]
[!code-vb[c_DuplexServices#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#3)]

<span data-ttu-id="3688b-124">A configuração do serviço deve ser configurada para fornecer uma associação que dê suporte à comunicação de sessão e à comunicação duplex.</span><span class="sxs-lookup"><span data-stu-id="3688b-124">The configuration for the service must be set up to provide a binding that supports both session communication and duplex communication.</span></span> <span data-ttu-id="3688b-125">O `wsDualHttpBinding` elemento dá suporte à comunicação de sessão e permite a comunicação duplex fornecendo conexões http duplas, uma para cada direção.</span><span class="sxs-lookup"><span data-stu-id="3688b-125">The `wsDualHttpBinding` element supports session communication and allows duplex communication by providing dual HTTP connections, one for each direction.</span></span>

<span data-ttu-id="3688b-126">No cliente, você deve configurar um endereço que o servidor pode usar para se conectar ao cliente, conforme mostrado na seguinte configuração de exemplo.</span><span class="sxs-lookup"><span data-stu-id="3688b-126">On the client, you must configure an address that the server can use to connect to the client, as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="3688b-127">Clientes não duplex que não se autenticam usando uma conversa segura normalmente lançam um <xref:System.ServiceModel.Security.MessageSecurityException> .</span><span class="sxs-lookup"><span data-stu-id="3688b-127">Non-duplex clients that fail to authenticate using a secure conversation typically throw a <xref:System.ServiceModel.Security.MessageSecurityException>.</span></span> <span data-ttu-id="3688b-128">No entanto, se um cliente duplex que usa uma conversa segura não for autenticado, o cliente receberá um <xref:System.TimeoutException> em vez disso.</span><span class="sxs-lookup"><span data-stu-id="3688b-128">However, if a duplex client that uses a secure conversation fails to authenticate, the client receives a <xref:System.TimeoutException> instead.</span></span>

<span data-ttu-id="3688b-129">Se você criar um cliente/serviço usando o `WSHttpBinding` elemento e não incluir o ponto de extremidade de retorno de chamada do cliente, você receberá o seguinte erro.</span><span class="sxs-lookup"><span data-stu-id="3688b-129">If you create a client/service using the `WSHttpBinding` element and you do not include the client callback endpoint, you will receive the following error.</span></span>

```console
HTTP could not register URL
htp://+:80/Temporary_Listen_Addresses/<guid> because TCP port 80 is being used by another application.
```

<span data-ttu-id="3688b-130">O código de exemplo a seguir mostra como especificar o endereço do ponto de extremidade do cliente programaticamente.</span><span class="sxs-lookup"><span data-stu-id="3688b-130">The following sample code shows how to specify the client endpoint address programmatically.</span></span>

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

<span data-ttu-id="3688b-131">O código de exemplo a seguir mostra como especificar o endereço do ponto de extremidade do cliente na configuração.</span><span class="sxs-lookup"><span data-stu-id="3688b-131">The following sample code shows how to specify the client endpoint address in configuration.</span></span>

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
> <span data-ttu-id="3688b-132">O modelo duplex não detecta automaticamente quando um serviço ou cliente fecha seu canal.</span><span class="sxs-lookup"><span data-stu-id="3688b-132">The duplex model doesn't automatically detect when a service or client closes its channel.</span></span> <span data-ttu-id="3688b-133">Portanto, se um cliente for encerrado inesperadamente, por padrão, o serviço não será notificado, ou se um serviço for encerrado inesperadamente, o cliente não será notificado.</span><span class="sxs-lookup"><span data-stu-id="3688b-133">So if a client unexpectedly terminates, by default the service will not be notified, or if a service unexpectedly terminates, the client will not be notified.</span></span> <span data-ttu-id="3688b-134">Se você usar um serviço que está desconectado, a <xref:System.ServiceModel.CommunicationException> exceção será gerada.</span><span class="sxs-lookup"><span data-stu-id="3688b-134">If you use a service that is disconnected, the <xref:System.ServiceModel.CommunicationException> exception is raised.</span></span> <span data-ttu-id="3688b-135">Os clientes e serviços podem implementar seu próprio protocolo para notificar uns aos outros se escolherem.</span><span class="sxs-lookup"><span data-stu-id="3688b-135">Clients and services can implement their own protocol to notify each other if they so choose.</span></span> <span data-ttu-id="3688b-136">Para obter mais informações sobre o tratamento de erros, consulte [controle de erros do WCF](../wcf-error-handling.md).</span><span class="sxs-lookup"><span data-stu-id="3688b-136">For more information on error handling, see [WCF Error Handling](../wcf-error-handling.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3688b-137">Veja também</span><span class="sxs-lookup"><span data-stu-id="3688b-137">See also</span></span>

- [<span data-ttu-id="3688b-138">Duplex</span><span class="sxs-lookup"><span data-stu-id="3688b-138">Duplex</span></span>](../samples/duplex.md)
- [<span data-ttu-id="3688b-139">Especificando o comportamento em tempo de execução do cliente</span><span class="sxs-lookup"><span data-stu-id="3688b-139">Specifying Client Run-Time Behavior</span></span>](../specifying-client-run-time-behavior.md)
- [<span data-ttu-id="3688b-140">Como criar uma fábrica de canais e utilizá-la para criar e gerenciar canais</span><span class="sxs-lookup"><span data-stu-id="3688b-140">How to: Create a Channel Factory and Use it to Create and Manage Channels</span></span>](how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels.md)
