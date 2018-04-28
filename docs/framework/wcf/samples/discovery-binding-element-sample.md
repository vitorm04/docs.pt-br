---
title: Amostra do elemento de associação de descoberta
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af513015-85bf-417b-8729-1bdff77ff6d6
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 624209221dc8c2745afa6b4db20df6e47c7374f1
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="discovery-binding-element-sample"></a><span data-ttu-id="039f8-102">Amostra do elemento de associação de descoberta</span><span class="sxs-lookup"><span data-stu-id="039f8-102">Discovery Binding Element Sample</span></span>
<span data-ttu-id="039f8-103">Este exemplo demonstra como usar o elemento de associação de cliente de descoberta para descobrir um serviço.</span><span class="sxs-lookup"><span data-stu-id="039f8-103">This sample demonstrates how to use the discovery client binding element to discover a service.</span></span> <span data-ttu-id="039f8-104">Esse recurso permite aos desenvolvedores adicionar um canal de cliente de descoberta para sua pilha de canais de cliente existente, tornando o modelo de programação muito intuitiva.</span><span class="sxs-lookup"><span data-stu-id="039f8-104">This feature enables developers to add a discovery client channel to their existing client channel stack, making the programming model very intuitive.</span></span> <span data-ttu-id="039f8-105">Quando o canal associado é aberto, o endereço do serviço é resolvido usando a descoberta.</span><span class="sxs-lookup"><span data-stu-id="039f8-105">When the associated channel is opened, the address of the service is resolved using discovery.</span></span> <span data-ttu-id="039f8-106">Este exemplo consiste nas seguintes projetos:</span><span class="sxs-lookup"><span data-stu-id="039f8-106">This sample consists of the following projects:</span></span>  
  
-   <span data-ttu-id="039f8-107">**CalculatorService**: um detectável [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço.</span><span class="sxs-lookup"><span data-stu-id="039f8-107">**CalculatorService**: A discoverable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
-   <span data-ttu-id="039f8-108">**CalculatorClient**: um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativo cliente que usa o canal cliente discovery para pesquisar e chamar o CalculatorService.</span><span class="sxs-lookup"><span data-stu-id="039f8-108">**CalculatorClient**: A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application that uses the discovery client channel to search for and call the CalculatorService.</span></span>  
  
-   <span data-ttu-id="039f8-109">**DynamicCalculatorClient**: um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativo cliente que usa um ponto de extremidade dinâmico para pesquisar e chamar o CalculatorService.</span><span class="sxs-lookup"><span data-stu-id="039f8-109">**DynamicCalculatorClient**: A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application that uses a dynamic endpoint to search for and call the CalculatorService.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="039f8-110">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="039f8-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="039f8-111">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="039f8-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="039f8-112">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="039f8-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="039f8-113">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="039f8-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryBindingElement`  
  
## <a name="calculatorservice"></a><span data-ttu-id="039f8-114">CalculatorService</span><span class="sxs-lookup"><span data-stu-id="039f8-114">CalculatorService</span></span>  
 <span data-ttu-id="039f8-115">Este projeto contém um serviço de cálculo simples que implementa o `ICalculatorService` contrato.</span><span class="sxs-lookup"><span data-stu-id="039f8-115">This project contains a simple calculator service that implements the `ICalculatorService` contract.</span></span>  
  
 <span data-ttu-id="039f8-116">O seguinte arquivo App. config é usado para adicionar um `<serviceDiscovery>` comportamento os comportamentos de serviço, bem como o ponto de extremidade de descoberta.</span><span class="sxs-lookup"><span data-stu-id="039f8-116">The following App.config file is used to add a `<serviceDiscovery>` behavior in the service behaviors as well as the discovery endpoint.</span></span>  
  
```xml  
<system.serviceModel>  
    <services>  
      <service behaviorConfiguration="CalculatorBehavior" name="Microsoft.Samples.Discovery.CalculatorService">  
        <endpoint name="udpDiscoveryEpt" kind="udpDiscoveryEndpoint" />  
      </service>  
    </services>  
    <behaviors>  
      <!--Enable discovery through configuration.-->  
      <serviceBehaviors>  
        <behavior name="CalculatorBehavior">  
          <serviceDiscovery>  
          </serviceDiscovery>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="039f8-117">Isso torna o serviço e seus pontos de extremidade podem ser descobertos.</span><span class="sxs-lookup"><span data-stu-id="039f8-117">This makes the service and its endpoints discoverable.</span></span> <span data-ttu-id="039f8-118">O CalculatorService é um serviço auto-hospedado que adiciona um ponto de extremidade usando a associação de NetTcpBinding.</span><span class="sxs-lookup"><span data-stu-id="039f8-118">The CalculatorService is a self-hosted service that adds one endpoint using the NetTcpBinding binding.</span></span> <span data-ttu-id="039f8-119">Ele também adiciona uma `EndpointDiscoveryBehavior` ao ponto de extremidade e especifica um escopo, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="039f8-119">It also adds an `EndpointDiscoveryBehavior` to the endpoint and specifies a scope as shown in the following code.</span></span>  
  
```  
// Add a NET.TCP endpoint and add a scope to that endpoint.  
ServiceEndpoint netTcpEndpoint = serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new NetTcpBinding(), netTcpAddress);  
EndpointDiscoveryBehavior netTctEndpointBehavior = new EndpointDiscoveryBehavior();  
netTctEndpointBehavior.Scopes.Add(new Uri("ldap:///ou=engineering,o=exampleorg,c=us"));  
netTcpEndpoint.Behaviors.Add(netTctEndpointBehavior);  
serviceHost.Open();  
```  
  
## <a name="calculatorclient"></a><span data-ttu-id="039f8-120">CalculatorClient</span><span class="sxs-lookup"><span data-stu-id="039f8-120">CalculatorClient</span></span>  
 <span data-ttu-id="039f8-121">Este projeto contém uma implementação de cliente que envia mensagens para o CalculatorService.</span><span class="sxs-lookup"><span data-stu-id="039f8-121">This project contains a client implementation that sends messages to the CalculatorService.</span></span> <span data-ttu-id="039f8-122">Esse programa usa a `CreateCustomBindingWithDiscoveryElement()` método para criar uma associação personalizada que usa o canal cliente Discovery.</span><span class="sxs-lookup"><span data-stu-id="039f8-122">This program uses the `CreateCustomBindingWithDiscoveryElement()` method to create a custom binding that uses the Discovery Client Channel.</span></span>  
  
```  
static CustomBinding CreateCustomBindingWithDiscoveryElement()  
 {  
      DiscoveryClientBindingElement discoveryBindingElement = new DiscoveryClientBindingElement();  
  
            // Provide the search criteria and the endpoint over which the probe is sent  
            discoveryBindingElement.FindCriteria = new FindCriteria(typeof(ICalculatorService));  
            discoveryBindingElement.DiscoveryEndpointProvider = new UdpDiscoveryEndpointProvider();  
  
            CustomBinding customBinding = new CustomBinding(new NetTcpBinding());  
            // Insert DiscoveryClientBindingElement at the top of the BindingElement stack.  
            // An exception is thrown if this binding element is not at the top  
            customBinding.Elements.Insert(0, discoveryBindingElement);  
  
            return customBinding; }  
```  
  
 <span data-ttu-id="039f8-123">Após o <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> é instanciada, o desenvolvedor Especifica os critérios para usar ao pesquisar para um serviço.</span><span class="sxs-lookup"><span data-stu-id="039f8-123">After the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> is instantiated, the developer specifies the criteria to use when searching for a service.</span></span> <span data-ttu-id="039f8-124">Nesse caso, o critério de localização de descoberta é o `ICalculatorService` tipo.</span><span class="sxs-lookup"><span data-stu-id="039f8-124">In this case, the discovery find criterion is the `ICalculatorService` type.</span></span> <span data-ttu-id="039f8-125">Além disso, o desenvolvedor Especifica um <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> que retorna um <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> que especifica onde procurar os serviços.</span><span class="sxs-lookup"><span data-stu-id="039f8-125">Additionally, the developer specifies a <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> which returns a <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> that specifies where to look for the services.</span></span> <span data-ttu-id="039f8-126">O <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> retorna um novo <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instância.</span><span class="sxs-lookup"><span data-stu-id="039f8-126">The <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> returns a new <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instance.</span></span> <span data-ttu-id="039f8-127">Para obter mais informações, consulte [usando uma associação personalizada com o canal cliente Discovery](../../../../docs/framework/wcf/feature-details/using-a-custom-binding-with-the-discovery-client-channel.md).</span><span class="sxs-lookup"><span data-stu-id="039f8-127">For more information, see [Using a Custom Binding with the Discovery Client Channel](../../../../docs/framework/wcf/feature-details/using-a-custom-binding-with-the-discovery-client-channel.md).</span></span>  
  
```  
// Extend DiscoveryEndpointProvider class to change the default DiscoveryEndpoint  
    // to the DiscoveryClientBindingElement. The Discovery ClientChannel   
    // uses this endpoint to send Probe message.  
    public class UdpDiscoveryEndpointProvider : DiscoveryEndpointProvider  
    {  
        public override DiscoveryEndpoint GetDiscoveryEndpoint()  
        {  
            return new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscoveryApril2005);  
        }  
    }  
```  
  
 <span data-ttu-id="039f8-128">Nesse caso, o cliente usa o protocolo UDP multicast mecanismo definido pelo protocolo de descoberta para procurar serviços na sub-rede local.</span><span class="sxs-lookup"><span data-stu-id="039f8-128">In this case, the client uses the UDP multicast mechanism defined by the Discovery protocol to search for services on the local subnet.</span></span> <span data-ttu-id="039f8-129">O restante do método cria uma associação personalizada e insere o elemento de associação de descoberta na parte superior da pilha.</span><span class="sxs-lookup"><span data-stu-id="039f8-129">The remainder of the method creates a custom binding and inserts the Discovery binding element at the top of the stack.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="039f8-130">O <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> devem ser colocados na parte superior da pilha de associação.</span><span class="sxs-lookup"><span data-stu-id="039f8-130">The <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> must be placed on the top of the binding stack.</span></span> <span data-ttu-id="039f8-131">Qualquer <xref:System.ServiceModel.Channels.BindingElement> na parte superior do <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> deve certificar-se de que a fábrica de canais ou o canal cria não usa o `EndpointAddress` ou `Via` propriedades, porque o endereço real é encontrado apenas no canal cliente Discovery.</span><span class="sxs-lookup"><span data-stu-id="039f8-131">Any <xref:System.ServiceModel.Channels.BindingElement> on top of <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> must make sure that the channel factory or channel it creates does not use the `EndpointAddress` or `Via` properties, because the actual address is found only at the Discovery client channel.</span></span>  
  
 <span data-ttu-id="039f8-132">Em seguida, o `CalculatorClient` pode ser instanciado, passando essa associação personalizada, bem como um endereço de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="039f8-132">Next, the `CalculatorClient` can be instantiated by passing in this custom binding as well as an endpoint address.</span></span>  
  
```  
CalculatorServiceClient client = new CalculatorServiceClient(CreateCustomBindingWithDiscoveryElement(), DiscoveryClientBindingElement.DiscoveryEndpointAddress);  
```  
  
 <span data-ttu-id="039f8-133">Ao usar o canal cliente Discovery, o endereço de constante de ponto de extremidade especificado anteriormente é passado.</span><span class="sxs-lookup"><span data-stu-id="039f8-133">When using the Discovery Client Channel, the constant endpoint address specified previously is passed in.</span></span> <span data-ttu-id="039f8-134">Agora em tempo de execução, o canal cliente Discovery localiza o serviço especificado pelos critérios de localização e se conectará a ele.</span><span class="sxs-lookup"><span data-stu-id="039f8-134">Now at runtime, the Discovery Client Channel finds the service specified by the find criteria and connects to it.</span></span> <span data-ttu-id="039f8-135">Para o serviço e o cliente para estabelecer uma conexão, eles também devem ter a mesma pilha de associação subjacente.</span><span class="sxs-lookup"><span data-stu-id="039f8-135">For the service and the client to establish a connection, they must also have the same underlying binding stack.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="039f8-136">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="039f8-136">To use this sample</span></span>  
  
1.  <span data-ttu-id="039f8-137">Abra a solução em [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="039f8-137">Open the solution in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="039f8-138">Compile a solução.</span><span class="sxs-lookup"><span data-stu-id="039f8-138">Build the solution.</span></span>  
  
3.  <span data-ttu-id="039f8-139">Execute o aplicativo de serviço e cada cliente de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="039f8-139">Run the service application and each of the client applications.</span></span>  
  
4.  <span data-ttu-id="039f8-140">Observe que o cliente foi capaz de encontrar o serviço sem saber o endereço.</span><span class="sxs-lookup"><span data-stu-id="039f8-140">Observe that the client was able to find the service without knowing its address.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="039f8-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="039f8-141">See Also</span></span>
