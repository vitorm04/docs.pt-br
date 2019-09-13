---
title: Serviços de duplex
ms.date: 05/09/2018
dev_langs:
- csharp
- vb
ms.assetid: 396b875a-d203-4ebe-a3a1-6a330d962e95
ms.openlocfilehash: f9e563cb87ee376e33442cdf718f70202d300f40
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895176"
---
# <a name="duplex-services"></a><span data-ttu-id="2b855-102">Serviços de duplex</span><span class="sxs-lookup"><span data-stu-id="2b855-102">Duplex Services</span></span>

<span data-ttu-id="2b855-103">Um contrato de serviço duplex é um padrão de troca de mensagens no qual ambos os pontos de extremidade podem enviar mensagens para o outro de forma independente.</span><span class="sxs-lookup"><span data-stu-id="2b855-103">A duplex service contract is a message exchange pattern in which both endpoints can send messages to the other independently.</span></span> <span data-ttu-id="2b855-104">Um serviço duplex, portanto, pode enviar mensagens de volta ao ponto de extremidade do cliente, fornecendo comportamento semelhante a evento.</span><span class="sxs-lookup"><span data-stu-id="2b855-104">A duplex service, therefore, can send messages back to the client endpoint, providing event-like behavior.</span></span> <span data-ttu-id="2b855-105">A comunicação duplex ocorre quando um cliente se conecta a um serviço e fornece o serviço com um canal no qual o serviço pode enviar mensagens de volta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="2b855-105">Duplex communication occurs when a client connects to a service and provides the service with a channel on which the service can send messages back to the client.</span></span> <span data-ttu-id="2b855-106">Observe que o comportamento do tipo evento dos serviços duplex só funciona em uma sessão.</span><span class="sxs-lookup"><span data-stu-id="2b855-106">Note that the event-like behavior of duplex services only works within a session.</span></span>

<span data-ttu-id="2b855-107">Para criar um contrato duplex, crie um par de interfaces.</span><span class="sxs-lookup"><span data-stu-id="2b855-107">To create a duplex contract you create a pair of interfaces.</span></span> <span data-ttu-id="2b855-108">A primeira é a interface de contrato de serviço que descreve as operações que um cliente pode invocar.</span><span class="sxs-lookup"><span data-stu-id="2b855-108">The first is the service contract interface that describes the operations that a client can invoke.</span></span> <span data-ttu-id="2b855-109">Esse contrato de serviço deve especificar um contrato de retorno <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> de *chamada* na propriedade.</span><span class="sxs-lookup"><span data-stu-id="2b855-109">That service contract must specify a *callback contract* in the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="2b855-110">O contrato de retorno de chamada é a interface que define as operações que o serviço pode chamar no ponto de extremidade do cliente.</span><span class="sxs-lookup"><span data-stu-id="2b855-110">The callback contract is the interface that defines the operations that the service can call on the client endpoint.</span></span> <span data-ttu-id="2b855-111">Um contrato duplex não requer uma sessão, embora as associações duplex fornecidas pelo sistema façam uso delas.</span><span class="sxs-lookup"><span data-stu-id="2b855-111">A duplex contract does not require a session, although the system-provided duplex bindings make use of them.</span></span>

<span data-ttu-id="2b855-112">Veja a seguir um exemplo de um contrato duplex.</span><span class="sxs-lookup"><span data-stu-id="2b855-112">The following is an example of a duplex contract.</span></span>

[!code-csharp[c_DuplexServices#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#0)]
[!code-vb[c_DuplexServices#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#0)]

<span data-ttu-id="2b855-113">A `CalculatorService` classe implementa a interface `ICalculatorDuplex` primária.</span><span class="sxs-lookup"><span data-stu-id="2b855-113">The `CalculatorService` class implements the primary `ICalculatorDuplex` interface.</span></span> <span data-ttu-id="2b855-114">O serviço usa o <xref:System.ServiceModel.InstanceContextMode.PerSession> modo de instância para manter o resultado de cada sessão.</span><span class="sxs-lookup"><span data-stu-id="2b855-114">The service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the result for each session.</span></span> <span data-ttu-id="2b855-115">Uma propriedade privada chamada `Callback` acessa o canal de retorno de chamada para o cliente.</span><span class="sxs-lookup"><span data-stu-id="2b855-115">A private property named `Callback` accesses the callback channel to the client.</span></span> <span data-ttu-id="2b855-116">O serviço usa o retorno de chamada para enviar mensagens de volta para o cliente por meio da interface de retorno de chamada, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="2b855-116">The service uses the callback for sending messages back to the client through the callback interface, as shown in the following sample code.</span></span>

[!code-csharp[c_DuplexServices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#1)]
[!code-vb[c_DuplexServices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#1)]

<span data-ttu-id="2b855-117">O cliente deve fornecer uma classe que implemente a interface de retorno de chamada do contrato duplex, para receber mensagens do serviço.</span><span class="sxs-lookup"><span data-stu-id="2b855-117">The client must provide a class that implements the callback interface of the duplex contract, for receiving messages from the service.</span></span> <span data-ttu-id="2b855-118">O código de exemplo a seguir `CallbackHandler` mostra uma classe que `ICalculatorDuplexCallback` implementa a interface.</span><span class="sxs-lookup"><span data-stu-id="2b855-118">The following sample code shows a `CallbackHandler` class that implements the `ICalculatorDuplexCallback` interface.</span></span>

[!code-csharp[c_DuplexServices#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#2)]
[!code-vb[c_DuplexServices#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#2)]

<span data-ttu-id="2b855-119">O cliente WCF que é gerado para um contrato duplex requer que <xref:System.ServiceModel.InstanceContext> uma classe seja fornecida na construção.</span><span class="sxs-lookup"><span data-stu-id="2b855-119">The WCF client that is generated for a duplex contract requires a <xref:System.ServiceModel.InstanceContext> class to be provided upon construction.</span></span> <span data-ttu-id="2b855-120">Essa <xref:System.ServiceModel.InstanceContext> classe é usada como o site de um objeto que implementa a interface de retorno de chamada e manipula as mensagens que são enviadas de volta do serviço.</span><span class="sxs-lookup"><span data-stu-id="2b855-120">This <xref:System.ServiceModel.InstanceContext> class is used as the site for an object that implements the callback interface and handles messages that are sent back from the service.</span></span> <span data-ttu-id="2b855-121">Uma <xref:System.ServiceModel.InstanceContext> classe é construída com uma instância `CallbackHandler` da classe.</span><span class="sxs-lookup"><span data-stu-id="2b855-121">An <xref:System.ServiceModel.InstanceContext> class is constructed with an instance of the `CallbackHandler` class.</span></span> <span data-ttu-id="2b855-122">Esse objeto manipula as mensagens enviadas do serviço para o cliente na interface de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="2b855-122">This object handles messages sent from the service to the client on the callback interface.</span></span>

[!code-csharp[c_DuplexServices#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#3)]
[!code-vb[c_DuplexServices#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#3)]

<span data-ttu-id="2b855-123">A configuração do serviço deve ser configurada para fornecer uma associação que dê suporte à comunicação de sessão e à comunicação duplex.</span><span class="sxs-lookup"><span data-stu-id="2b855-123">The configuration for the service must be set up to provide a binding that supports both session communication and duplex communication.</span></span> <span data-ttu-id="2b855-124">O `wsDualHttpBinding` elemento dá suporte à comunicação de sessão e permite a comunicação duplex fornecendo conexões http duplas, uma para cada direção.</span><span class="sxs-lookup"><span data-stu-id="2b855-124">The `wsDualHttpBinding` element supports session communication and allows duplex communication by providing dual HTTP connections, one for each direction.</span></span>

<span data-ttu-id="2b855-125">No cliente, você deve configurar um endereço que o servidor pode usar para se conectar ao cliente, conforme mostrado na seguinte configuração de exemplo.</span><span class="sxs-lookup"><span data-stu-id="2b855-125">On the client, you must configure an address that the server can use to connect to the client, as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="2b855-126">Clientes não duplex que não se autenticam usando uma conversa segura normalmente lançam <xref:System.ServiceModel.Security.MessageSecurityException>um.</span><span class="sxs-lookup"><span data-stu-id="2b855-126">Non-duplex clients that fail to authenticate using a secure conversation typically throw a <xref:System.ServiceModel.Security.MessageSecurityException>.</span></span> <span data-ttu-id="2b855-127">No entanto, se um cliente duplex que usa uma conversa segura não for autenticado, o <xref:System.TimeoutException> cliente receberá um em vez disso.</span><span class="sxs-lookup"><span data-stu-id="2b855-127">However, if a duplex client that uses a secure conversation fails to authenticate, the client receives a <xref:System.TimeoutException> instead.</span></span>

<span data-ttu-id="2b855-128">Se você criar um cliente/serviço usando o `WSHttpBinding` elemento e não incluir o ponto de extremidade de retorno de chamada do cliente, você receberá o seguinte erro.</span><span class="sxs-lookup"><span data-stu-id="2b855-128">If you create a client/service using the `WSHttpBinding` element and you do not include the client callback endpoint, you will receive the following error.</span></span>

```console
HTTP could not register URL
htp://+:80/Temporary_Listen_Addresses/<guid> because TCP port 80 is being used by another application.
```

<span data-ttu-id="2b855-129">O código de exemplo a seguir mostra como especificar o endereço do ponto de extremidade do cliente programaticamente.</span><span class="sxs-lookup"><span data-stu-id="2b855-129">The following sample code shows how to specify the client endpoint address programmatically.</span></span>

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

<span data-ttu-id="2b855-130">O código de exemplo a seguir mostra como especificar o endereço do ponto de extremidade do cliente na configuração.</span><span class="sxs-lookup"><span data-stu-id="2b855-130">The following sample code shows how to specify the client endpoint address in configuration.</span></span>

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
> <span data-ttu-id="2b855-131">O modelo duplex não detecta automaticamente quando um serviço ou cliente fecha seu canal.</span><span class="sxs-lookup"><span data-stu-id="2b855-131">The duplex model doesn't automatically detect when a service or client closes its channel.</span></span> <span data-ttu-id="2b855-132">Portanto, se um cliente for encerrado inesperadamente, por padrão, o serviço não será notificado, ou se um serviço for encerrado inesperadamente, o cliente não será notificado.</span><span class="sxs-lookup"><span data-stu-id="2b855-132">So if a client unexpectedly terminates, by default the service will not be notified, or if a service unexpectedly terminates, the client will not be notified.</span></span> <span data-ttu-id="2b855-133">Se você usar um serviço que está desconectado, <xref:System.ServiceModel.CommunicationException> a exceção será gerada.</span><span class="sxs-lookup"><span data-stu-id="2b855-133">If you use a service that is disconnected, the <xref:System.ServiceModel.CommunicationException> exception is raised.</span></span> <span data-ttu-id="2b855-134">Os clientes e serviços podem implementar seu próprio protocolo para notificar uns aos outros se escolherem.</span><span class="sxs-lookup"><span data-stu-id="2b855-134">Clients and services can implement their own protocol to notify each other if they so choose.</span></span> <span data-ttu-id="2b855-135">Para obter mais informações sobre o tratamento de erros, consulte [controle de erros do WCF](../wcf-error-handling.md)</span><span class="sxs-lookup"><span data-stu-id="2b855-135">For more information on error handling, see [WCF Error Handling](../wcf-error-handling.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="2b855-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2b855-136">See also</span></span>

- [<span data-ttu-id="2b855-137">Duplex</span><span class="sxs-lookup"><span data-stu-id="2b855-137">Duplex</span></span>](../samples/duplex.md)
- [<span data-ttu-id="2b855-138">Especificando o comportamento em tempo de execução do cliente</span><span class="sxs-lookup"><span data-stu-id="2b855-138">Specifying Client Run-Time Behavior</span></span>](../specifying-client-run-time-behavior.md)
- [<span data-ttu-id="2b855-139">Como: Criar uma fábrica de canais e usá-la para criar e gerenciar canais</span><span class="sxs-lookup"><span data-stu-id="2b855-139">How to: Create a Channel Factory and Use it to Create and Manage Channels</span></span>](how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels.md)
