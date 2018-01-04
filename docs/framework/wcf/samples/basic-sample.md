---
title: "Exemplo básico"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1910bc1-3d0a-4fa6-b12a-4ed6fe759620
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0f0d5c25e2b2d3dac042ef93e5a174b25ce17314
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="basic-sample"></a><span data-ttu-id="8e9d7-102">Exemplo básico</span><span class="sxs-lookup"><span data-stu-id="8e9d7-102">Basic Sample</span></span>
<span data-ttu-id="8e9d7-103">Este exemplo mostra como criar um serviço detectável e como procurar e chamar um serviço detectável.</span><span class="sxs-lookup"><span data-stu-id="8e9d7-103">This sample shows how to make a service discoverable and how to search for and call a discoverable service.</span></span> <span data-ttu-id="8e9d7-104">Este exemplo é composto de dois projetos: serviço e cliente.</span><span class="sxs-lookup"><span data-stu-id="8e9d7-104">This sample is composed of two projects: service and client.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8e9d7-105">Este exemplo implementa descoberta no código.</span><span class="sxs-lookup"><span data-stu-id="8e9d7-105">This sample implements discovery in code.</span></span>  <span data-ttu-id="8e9d7-106">Para obter um exemplo que implementa a descoberta de configuração, consulte [configuração](../../../../docs/framework/wcf/samples/configuration-sample.md).</span><span class="sxs-lookup"><span data-stu-id="8e9d7-106">For a sample that implements discovery in configuration, see [Configuration](../../../../docs/framework/wcf/samples/configuration-sample.md).</span></span>  
  
## <a name="service"></a><span data-ttu-id="8e9d7-107">Serviço</span><span class="sxs-lookup"><span data-stu-id="8e9d7-107">Service</span></span>  
 <span data-ttu-id="8e9d7-108">Isso é uma implementação de serviço de cálculo simples.</span><span class="sxs-lookup"><span data-stu-id="8e9d7-108">This is a simple calculator service implementation.</span></span> <span data-ttu-id="8e9d7-109">A descoberta relacionadas código pode ser encontrado em `Main` onde um <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> é adicionada para o host de serviço e um <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> é adicionado, como mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="8e9d7-109">The discovery related code can be found in `Main` where a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> is added to the service host and a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is added as shown in the following code.</span></span>  
  
```  
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))  
{  
    serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new   
      WSHttpBinding(), String.Empty);  
  
    // Make the service discoverable over UDP multicast  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());                  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
  
    serviceHost.Open();  
    // ...  
}  
```  
  
## <a name="client"></a><span data-ttu-id="8e9d7-110">Cliente</span><span class="sxs-lookup"><span data-stu-id="8e9d7-110">Client</span></span>  
 <span data-ttu-id="8e9d7-111">O cliente usa um <xref:System.ServiceModel.Discovery.DynamicEndpoint> para localizar o serviço.</span><span class="sxs-lookup"><span data-stu-id="8e9d7-111">The client uses a <xref:System.ServiceModel.Discovery.DynamicEndpoint> to locate the service.</span></span> <span data-ttu-id="8e9d7-112">O <xref:System.ServiceModel.Discovery.DynamicEndpoint>, um ponto de extremidade padrão resolve o ponto de extremidade do serviço quando o cliente é aberto.</span><span class="sxs-lookup"><span data-stu-id="8e9d7-112">The <xref:System.ServiceModel.Discovery.DynamicEndpoint>, a standard endpoint, resolves the endpoint of the service when the client is opened.</span></span> <span data-ttu-id="8e9d7-113">Nesse caso, o <xref:System.ServiceModel.Discovery.DynamicEndpoint> procura o serviço com base no contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="8e9d7-113">In this case, the <xref:System.ServiceModel.Discovery.DynamicEndpoint> looks for the service based on the service contract.</span></span> <span data-ttu-id="8e9d7-114">O <xref:System.ServiceModel.Discovery.DynamicEndpoint> realiza a pesquisa em um <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> por padrão.</span><span class="sxs-lookup"><span data-stu-id="8e9d7-114">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> conducts the search over a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> by default.</span></span> <span data-ttu-id="8e9d7-115">Depois que ele localiza um ponto de extremidade de serviço, o cliente se conecta ao serviço sobre a associação especificada.</span><span class="sxs-lookup"><span data-stu-id="8e9d7-115">Once it locates a service endpoint, the client connects to that service over the specified binding.</span></span>  
  
```csharp  
public static void Main()  
{  
   DynamicEndpoint dynamicEndpoint = new DynamicEndpoint( ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());  
   // ...  
}              
```  
  
 <span data-ttu-id="8e9d7-116">O cliente define um método chamado `InvokeCalculatorService` que usa o <xref:System.ServiceModel.Discovery.DiscoveryClient> classe para procurar serviços.</span><span class="sxs-lookup"><span data-stu-id="8e9d7-116">The client defines a method called `InvokeCalculatorService` that uses the <xref:System.ServiceModel.Discovery.DiscoveryClient> class to search for services.</span></span> <span data-ttu-id="8e9d7-117">O <xref:System.ServiceModel.Discovery.DynamicEndpoint> herda de <xref:System.ServiceModel.Description.ServiceEndpoint>, portanto, ele pode ser passado para o `InvokeCalculatorService` método.</span><span class="sxs-lookup"><span data-stu-id="8e9d7-117">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> inherits from <xref:System.ServiceModel.Description.ServiceEndpoint>, so it can be passed to the `InvokeCalculatorService` method.</span></span> <span data-ttu-id="8e9d7-118">O exemplo usa o <xref:System.ServiceModel.Discovery.DynamicEndpoint> para criar uma instância de `CalculatorServiceClient` e chama as várias operações do serviço de cálculo.</span><span class="sxs-lookup"><span data-stu-id="8e9d7-118">The example then uses the <xref:System.ServiceModel.Discovery.DynamicEndpoint> to create an instance of `CalculatorServiceClient` and calls the various operations of the calculator service.</span></span>  
  
```csharp  
static void InvokeCalculatorService(ServiceEndpoint serviceEndpoint)  
{  
   // Create a client  
   CalculatorServiceClient client = new CalculatorServiceClient(serviceEndpoint);  
  
   Console.WriteLine("Invoking CalculatorService");  
   Console.WriteLine();  
  
   double value1 = 100.00D;  
   double value2 = 15.99D;  
  
   // Call the Add service operation.  
   double result = client.Add(value1, value2);  
   Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
   // Call the Subtract service operation.  
   result = client.Subtract(value1, value2);  
   Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
   // Call the Multiply service operation.  
   result = client.Multiply(value1, value2);  
   Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
   // Call the Divide service operation.  
   result = client.Divide(value1, value2);  
   Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
   Console.WriteLine();  
  
   //Closing the client gracefully closes the connection and cleans up resources  
   client.Close();  
}  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="8e9d7-119">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="8e9d7-119">To use this sample</span></span>  
  
1.  <span data-ttu-id="8e9d7-120">Este exemplo usa pontos de extremidade HTTP e para executar este exemplo, as ACLs adequadas de URL deve ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="8e9d7-120">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="8e9d7-121">[Configurando HTTP e HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353).</span><span class="sxs-lookup"><span data-stu-id="8e9d7-121"> [Configuring HTTP and HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353).</span></span> <span data-ttu-id="8e9d7-122">Executando o seguinte comando em um privilégio elevado deve adicionar as ACLs corretas.</span><span class="sxs-lookup"><span data-stu-id="8e9d7-122">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="8e9d7-123">Convém substituir seu domínio e nome de usuário para os argumentos a seguir se o comando não funcionar como está.</span><span class="sxs-lookup"><span data-stu-id="8e9d7-123">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  <span data-ttu-id="8e9d7-124">Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra o Basic.sln e compilar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="8e9d7-124">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the Basic.sln and build the sample.</span></span>  
  
3.  <span data-ttu-id="8e9d7-125">Execute o aplicativo service.exe.</span><span class="sxs-lookup"><span data-stu-id="8e9d7-125">Run the service.exe application.</span></span>  
  
4.  <span data-ttu-id="8e9d7-126">Depois que o serviço foi iniciado, execute o client.exe.</span><span class="sxs-lookup"><span data-stu-id="8e9d7-126">After the service has started, run the client.exe.</span></span>  
  
5.  <span data-ttu-id="8e9d7-127">Observe que o cliente foi capaz de encontrar o serviço sem saber o endereço.</span><span class="sxs-lookup"><span data-stu-id="8e9d7-127">Observe that the client was able to find the service without knowing its address.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8e9d7-128">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="8e9d7-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8e9d7-129">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="8e9d7-129">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8e9d7-130">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="8e9d7-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8e9d7-131">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="8e9d7-131">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Basic`  
  
## <a name="see-also"></a><span data-ttu-id="8e9d7-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8e9d7-132">See Also</span></span>
