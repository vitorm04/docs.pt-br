---
title: DiscoveryClient e DynamicEndpoint
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7cd418f0-0eab-48d1-a493-7eb907867ec3
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 49e64fb9a8a2b6bd90c2f9ed062afecafc8cfecd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="discoveryclient-and-dynamicendpoint"></a><span data-ttu-id="76515-102">DiscoveryClient e DynamicEndpoint</span><span class="sxs-lookup"><span data-stu-id="76515-102">DiscoveryClient and DynamicEndpoint</span></span>
<span data-ttu-id="76515-103"><xref:System.ServiceModel.Discovery.DiscoveryClient>e <xref:System.ServiceModel.Discovery.DynamicEndpoint> são duas classes usadas no lado do cliente para procurar serviços.</span><span class="sxs-lookup"><span data-stu-id="76515-103"><xref:System.ServiceModel.Discovery.DiscoveryClient> and <xref:System.ServiceModel.Discovery.DynamicEndpoint> are two classes used on the client side to search for services.</span></span> <span data-ttu-id="76515-104"><xref:System.ServiceModel.Discovery.DiscoveryClient>Fornece uma lista de serviços que correspondam a um determinado conjunto de critérios e permite que você se conecte aos serviços.</span><span class="sxs-lookup"><span data-stu-id="76515-104"><xref:System.ServiceModel.Discovery.DiscoveryClient> provides you with a list of services that match a specific set of criteria and allows you to connect to the services.</span></span> <span data-ttu-id="76515-105"><xref:System.ServiceModel.Discovery.DynamicEndpoint>executa a mesma operação e Além disso, conecta-se automaticamente para um dos serviços que foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="76515-105"><xref:System.ServiceModel.Discovery.DynamicEndpoint> performs the same operation and in addition, automatically connects to one of the services that was found.</span></span> <span data-ttu-id="76515-106">Qualquer ponto de extremidade pode ser transformado em um <xref:System.ServiceModel.Discovery.DynamicEndpoint>, os critérios de pesquisa também podem ser adicionados na configuração, portanto, <xref:System.ServiceModel.Discovery.DynamicEndpoint> é útil quando você precisa de descoberta em sua solução, mas não deseja modificar a lógica do cliente – você só precisa modificar os pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="76515-106">Any endpoint can be made into a <xref:System.ServiceModel.Discovery.DynamicEndpoint>, the search criteria can also be added in configuration, thus <xref:System.ServiceModel.Discovery.DynamicEndpoint> is useful when you need discovery in your solution but do not want to modify the client logic – you only need to modify the endpoints.</span></span> <span data-ttu-id="76515-107"><xref:System.ServiceModel.Discovery.DiscoveryClient>Por outro lado, pode ser usado para obter um controle mais preciso sobre a operação de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="76515-107"><xref:System.ServiceModel.Discovery.DiscoveryClient> on the other hand can be used to gain finer control over your search operation.</span></span> <span data-ttu-id="76515-108">Os usos e benefícios de cada são elaborados abaixo.</span><span class="sxs-lookup"><span data-stu-id="76515-108">The uses and benefits of each are elaborated below.</span></span>  
  
## <a name="discoveryclient"></a><span data-ttu-id="76515-109">DiscoveryClient</span><span class="sxs-lookup"><span data-stu-id="76515-109">DiscoveryClient</span></span>  
 <span data-ttu-id="76515-110">O <xref:System.ServiceModel.Discovery.DiscoveryClient> define métodos síncronos e assíncronos de localização, <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> e <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> eventos.</span><span class="sxs-lookup"><span data-stu-id="76515-110">The <xref:System.ServiceModel.Discovery.DiscoveryClient> defines synchronous and asynchronous Find methods, <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> and <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> events.</span></span>  <span data-ttu-id="76515-111">Ele também define os métodos Resolve síncronos e assíncronos e um <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> eventos.</span><span class="sxs-lookup"><span data-stu-id="76515-111">It also defines synchronous and asynchronous Resolve methods and a <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> event.</span></span> <span data-ttu-id="76515-112">Use o <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> ou <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> métodos para procurar serviços.</span><span class="sxs-lookup"><span data-stu-id="76515-112">Use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> or <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> methods to search for services.</span></span> <span data-ttu-id="76515-113">Ambos os métodos levar um <xref:System.ServiceModel.Discovery.FindCriteria> instância que permite que você especifique nomes de tipo de contrato, escopos, o número máximo de resultados solicitado e o escopo de regras de correspondência.</span><span class="sxs-lookup"><span data-stu-id="76515-113">Both of these methods take a <xref:System.ServiceModel.Discovery.FindCriteria> instance that allows you to specify contract type names, scopes, maximum number of results requested, and scope matching rules.</span></span> <span data-ttu-id="76515-114">O <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> e <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> eventos podem ser usados ao chamar o <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> método.</span><span class="sxs-lookup"><span data-stu-id="76515-114">The <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> and <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> events can be used when calling the <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> method.</span></span> <span data-ttu-id="76515-115"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged>é acionado sempre que o <xref:System.ServiceModel.Discovery.DiscoveryClient> recebe uma resposta de um serviço.</span><span class="sxs-lookup"><span data-stu-id="76515-115"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> is fired whenever the <xref:System.ServiceModel.Discovery.DiscoveryClient> receives a response from a service.</span></span> <span data-ttu-id="76515-116">Ele pode ser usado para exibir um barra de progresso demonstrando o progresso da operação de localização.</span><span class="sxs-lookup"><span data-stu-id="76515-116">It can be used to display a progress bar showing the progress of the find operation.</span></span> <span data-ttu-id="76515-117">Ele também pode ser usado para agir em localizar respostas que são recebidas.</span><span class="sxs-lookup"><span data-stu-id="76515-117">It can also be used to act on find responses as they are received.</span></span> <span data-ttu-id="76515-118">O <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> evento é acionado quando a operação de localização é concluída.</span><span class="sxs-lookup"><span data-stu-id="76515-118">The <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> event is fired when the find operation completes.</span></span> <span data-ttu-id="76515-119">Isso pode ocorrer porque o número máximo de respostas foi recebido ou se o <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> expirou.</span><span class="sxs-lookup"><span data-stu-id="76515-119">This may happen because the maximum number of responses has been received or if the <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> has elapsed.</span></span> <span data-ttu-id="76515-120">Ao concluir a operação de localizar os resultados são retornados em um <xref:System.ServiceModel.Discovery.FindResponse> instância.</span><span class="sxs-lookup"><span data-stu-id="76515-120">When the find operation completes the results are returned in a <xref:System.ServiceModel.Discovery.FindResponse> instance.</span></span> <span data-ttu-id="76515-121">O <xref:System.ServiceModel.Discovery.FindResponse> contém uma coleção de <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> que contém endereços, nomes de tipo de contrato, extensões, URIs de escuta e escopos dos serviços correspondentes.</span><span class="sxs-lookup"><span data-stu-id="76515-121">The <xref:System.ServiceModel.Discovery.FindResponse> contains a collection of <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> which contains the addresses, contract type names, extensions, listen URIs, and scopes of the matching services.</span></span> <span data-ttu-id="76515-122">Você pode usar essas informações para conectar e chamar um dos serviços de correspondência.</span><span class="sxs-lookup"><span data-stu-id="76515-122">You can then use this information to connect to and call one of the matching services.</span></span> <span data-ttu-id="76515-123">O exemplo a seguir mostra como chamar o método System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) e usar os metadados retornados para chamar o serviço encontrado.</span><span class="sxs-lookup"><span data-stu-id="76515-123">The following example shows how to call the System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) method and use the returned metadata to call the found service.</span></span> <span data-ttu-id="76515-124">Uma vantagem de usar <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> é que você pode armazenar em cache a lista de pontos de extremidade encontradas e usá-los mais tarde.</span><span class="sxs-lookup"><span data-stu-id="76515-124">A benefit of using <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> is that you can cache the list of endpoints you’ve found and use them at a later time.</span></span> <span data-ttu-id="76515-125">Com esse cache, você pode criar lógica personalizada para lidar com várias condições de falha.</span><span class="sxs-lookup"><span data-stu-id="76515-125">With this cache, you can build custom logic to handle various failure conditions.</span></span>  
  
```  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
FindCriteria criteria = new FindCriteria(typeof(ICalculatorService));  
FindResponse fr = dc.Find(criteria);  
  
if (fr.Endpoints.Count > 0)  
{  
   EndpointAddress ep = fr.Endpoints[0].Address;  
   CalculatorServiceClient client = new CalculatorServiceClient();  
  
    // Connect to the discovered service endpoint  
   client.Endpoint.Address = endpointAddress;  
   Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress);  
  
   double value1 = 100.00D;  
   double value2 = 15.99D;  
  
   // Call the Add service operation.  
   double result = client.Add(value1, value2);  
   Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
}  
else  
   Console.WriteLine("No matching endpoints found");  
```  
  
 <span data-ttu-id="76515-126">O exemplo a seguir mostra como executar uma operação de localização de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="76515-126">The following example shows how to perform a find operation asynchronously.</span></span>  
  
```  
static void FindServiceAsync()  
{  
   DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());   
   dc.FindCompleted += new EventHandler<FindCompletedEventArgs>( discoveryClient_FindCompleted);  
   dc.FindProgressChanged += new EventHandler<FindProgressChangedEventArgs>(discoveryClient_FindProgressChanged);  
   dc.FindAsync(new FindCriteria(typeof(ICalculatorService)));   
}   
static void discoveryClient_FindProgressChanged(object sender, FindProgressChangedEventArgs e)  
{  
   Console.WriteLine("Found service at: " + e.EndpointDiscoveryMetadata.Address  
}   
  
static void discoveryClient_FindCompleted(object sender, FindCompletedEventArgs e)  
{    
      if (e.Result.Endpoints.Count > 0)  
            {  
                EndpointAddress ep = e.Result.Endpoints[0].Address;  
                CalculatorServiceClient client = new CalculatorServiceClient();  
  
                // Connect to the discovered service endpoint  
                client.Endpoint.Address = ep;  
                Console.WriteLine("Invoking CalculatorService at {0}", ep);  
  
                double value1 = 100.00D;  
                double value2 = 15.99D;  
  
                double result = client.Add(value1, value2);  
                Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
            }  
            else  
                Console.WriteLine("No matching endpoints found");  
  
        }  
```  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="76515-127">tornando assíncrona localizar chamadas, consulte [localizar assíncrona](../../../../docs/framework/wcf/samples/asynchronous-find-sample.md).</span><span class="sxs-lookup"><span data-stu-id="76515-127"> making asynchronous find calls, see [Asynchronous Find](../../../../docs/framework/wcf/samples/asynchronous-find-sample.md).</span></span>  
  
 <span data-ttu-id="76515-128">Use o <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> e <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> métodos para localizar um serviço baseiam em seu endereço de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="76515-128">Use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> and <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> methods to locate a service based on its endpoint address.</span></span> <span data-ttu-id="76515-129">Isso é útil quando o endereço do ponto de extremidade não é rede endereçável.</span><span class="sxs-lookup"><span data-stu-id="76515-129">This is useful when the endpoint address is not network addressable.</span></span> <span data-ttu-id="76515-130">Os métodos de resolução levar a uma instância de <xref:System.ServiceModel.Discovery.ResolveCriteria> que permite que você especifique o endereço de ponto de extremidade do serviço que você está resolvendo, a duração máxima da operação de resolução e um conjunto de extensões.</span><span class="sxs-lookup"><span data-stu-id="76515-130">The Resolve methods take an instance of <xref:System.ServiceModel.Discovery.ResolveCriteria> which allows you to specify the endpoint address of the service you are resolving, the maximum duration of the resolve operation, and a set of extensions.</span></span> <span data-ttu-id="76515-131">O exemplo a seguir mostra como usar o <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> método para resolver um serviço.</span><span class="sxs-lookup"><span data-stu-id="76515-131">The following example shows how to use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> method to resolve a service.</span></span>  
  
```  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
ResolveCriteria criteria = new ResolveCriteria(endpointAddress);  
ResolveResponse response = dc.Resolve(criteria);  
EndpointAddress newEp = response.EndpointDiscoveryMetadata.Address;  
```  
  
## <a name="dynamicendpoint"></a><span data-ttu-id="76515-132">DynamicEndpoint</span><span class="sxs-lookup"><span data-stu-id="76515-132">DynamicEndpoint</span></span>  
 <span data-ttu-id="76515-133"><xref:System.ServiceModel.Discovery.DynamicEndpoint>é um ponto de extremidade padrão ([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [pontos de extremidade padrão](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)) que executa a descoberta e seleciona automaticamente um serviço correspondente.</span><span class="sxs-lookup"><span data-stu-id="76515-133"><xref:System.ServiceModel.Discovery.DynamicEndpoint> is a standard endpoint ([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Standard Endpoints](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)) which performs discovery and automatically selects a matching service.</span></span> <span data-ttu-id="76515-134">Crie um <xref:System.ServiceModel.Discovery.DynamicEndpoint> passando o contrato para pesquisa e a associação usar e passar o <xref:System.ServiceModel.Discovery.DynamicEndpoint> instância para o cliente do WCF.</span><span class="sxs-lookup"><span data-stu-id="76515-134">Just create a <xref:System.ServiceModel.Discovery.DynamicEndpoint> passing in the contract to search for and the binding to use and pass the <xref:System.ServiceModel.Discovery.DynamicEndpoint> instance to the WCF client.</span></span> <span data-ttu-id="76515-135">O exemplo a seguir mostra como criar e usar um <xref:System.ServiceModel.Discovery.DynamicEndpoint> para chamar o serviço da Calculadora.</span><span class="sxs-lookup"><span data-stu-id="76515-135">The following example shows how to create and use a <xref:System.ServiceModel.Discovery.DynamicEndpoint> to call the calculator service.</span></span> <span data-ttu-id="76515-136">A descoberta é executada sempre que o cliente é aberto.</span><span class="sxs-lookup"><span data-stu-id="76515-136">The discovery is performed every time the client is opened.</span></span> <span data-ttu-id="76515-137">Qualquer ponto de extremidade definido na configuração também pode ser transformado em um <xref:System.ServiceModel.Discovery.DynamicEndpoint> adicionando o `kind ="dynamicEndpoint"` de atributo para o elemento de configuração de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="76515-137">Any endpoint defined in configuration can also be turned into a <xref:System.ServiceModel.Discovery.DynamicEndpoint> by adding the `kind ="dynamicEndpoint"` attribute to the endpoint configuration element.</span></span>  
  
```  
DynamicEndpoint dynamicEndpoint = new DynamicEndpoint(ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());  
CalculatorServiceClient client = new CalculatorServiceClient(dynamicEndpoint);  
  
Console.WriteLine("Invoking CalculatorService");  
Console.WriteLine();  
  
double value1 = 100.00D;  
double value2 = 15.99D;  
  
double result = client.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```  
  
## <a name="see-also"></a><span data-ttu-id="76515-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="76515-138">See Also</span></span>  
 [<span data-ttu-id="76515-139">Descoberta com escopos</span><span class="sxs-lookup"><span data-stu-id="76515-139">Discovery with Scopes</span></span>](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)  
 [<span data-ttu-id="76515-140">Assíncrono encontrado</span><span class="sxs-lookup"><span data-stu-id="76515-140">Asynchronous Find</span></span>](../../../../docs/framework/wcf/samples/asynchronous-find-sample.md)  
 [<span data-ttu-id="76515-141">Básico</span><span class="sxs-lookup"><span data-stu-id="76515-141">Basic</span></span>](../../../../docs/framework/wcf/samples/basic-sample.md)
