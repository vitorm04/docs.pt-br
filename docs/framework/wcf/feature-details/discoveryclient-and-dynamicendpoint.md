---
title: DiscoveryClient e DynamicEndpoint
ms.date: 03/30/2017
ms.assetid: 7cd418f0-0eab-48d1-a493-7eb907867ec3
ms.openlocfilehash: 455ccc7f09c13a33b4034099b16b116fd3a8dbdf
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895303"
---
# <a name="discoveryclient-and-dynamicendpoint"></a><span data-ttu-id="ec581-102">DiscoveryClient e DynamicEndpoint</span><span class="sxs-lookup"><span data-stu-id="ec581-102">DiscoveryClient and DynamicEndpoint</span></span>
<span data-ttu-id="ec581-103"><xref:System.ServiceModel.Discovery.DiscoveryClient>e <xref:System.ServiceModel.Discovery.DynamicEndpoint> são duas classes usadas no lado do cliente para procurar serviços.</span><span class="sxs-lookup"><span data-stu-id="ec581-103"><xref:System.ServiceModel.Discovery.DiscoveryClient> and <xref:System.ServiceModel.Discovery.DynamicEndpoint> are two classes used on the client side to search for services.</span></span> <span data-ttu-id="ec581-104"><xref:System.ServiceModel.Discovery.DiscoveryClient>fornece uma lista de serviços que correspondem a um conjunto específico de critérios e permite que você se conecte aos serviços.</span><span class="sxs-lookup"><span data-stu-id="ec581-104"><xref:System.ServiceModel.Discovery.DiscoveryClient> provides you with a list of services that match a specific set of criteria and allows you to connect to the services.</span></span> <span data-ttu-id="ec581-105"><xref:System.ServiceModel.Discovery.DynamicEndpoint>executa a mesma operação e, além disso, conecta-se automaticamente a um dos serviços que foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="ec581-105"><xref:System.ServiceModel.Discovery.DynamicEndpoint> performs the same operation and in addition, automatically connects to one of the services that was found.</span></span> <span data-ttu-id="ec581-106">Qualquer ponto de extremidade pode ser feito <xref:System.ServiceModel.Discovery.DynamicEndpoint>em um, os critérios de pesquisa também podem ser adicionados na <xref:System.ServiceModel.Discovery.DynamicEndpoint> configuração, portanto, é útil quando você precisa de descoberta em sua solução, mas não deseja modificar a lógica do cliente – você só precisa modificar os pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ec581-106">Any endpoint can be made into a <xref:System.ServiceModel.Discovery.DynamicEndpoint>, the search criteria can also be added in configuration, thus <xref:System.ServiceModel.Discovery.DynamicEndpoint> is useful when you need discovery in your solution but do not want to modify the client logic – you only need to modify the endpoints.</span></span> <span data-ttu-id="ec581-107"><xref:System.ServiceModel.Discovery.DiscoveryClient>por outro lado, pode ser usado para obter um controle mais preciso sobre a operação de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="ec581-107"><xref:System.ServiceModel.Discovery.DiscoveryClient> on the other hand can be used to gain finer control over your search operation.</span></span> <span data-ttu-id="ec581-108">Os usos e benefícios de cada um são elaborados abaixo.</span><span class="sxs-lookup"><span data-stu-id="ec581-108">The uses and benefits of each are elaborated below.</span></span>  
  
## <a name="discoveryclient"></a><span data-ttu-id="ec581-109">DiscoveryClient</span><span class="sxs-lookup"><span data-stu-id="ec581-109">DiscoveryClient</span></span>  
 <span data-ttu-id="ec581-110">O <xref:System.ServiceModel.Discovery.DiscoveryClient> define métodos <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> e<xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> eventos de localização síncrona e assíncrona.</span><span class="sxs-lookup"><span data-stu-id="ec581-110">The <xref:System.ServiceModel.Discovery.DiscoveryClient> defines synchronous and asynchronous Find methods, <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> and <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> events.</span></span>  <span data-ttu-id="ec581-111">Ele também define métodos de resolução síncrono e assíncrono e <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> um evento.</span><span class="sxs-lookup"><span data-stu-id="ec581-111">It also defines synchronous and asynchronous Resolve methods and a <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> event.</span></span> <span data-ttu-id="ec581-112">Use os <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> métodos <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> ou para procurar serviços.</span><span class="sxs-lookup"><span data-stu-id="ec581-112">Use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> or <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> methods to search for services.</span></span> <span data-ttu-id="ec581-113">Ambos os métodos usam uma <xref:System.ServiceModel.Discovery.FindCriteria> instância que permite especificar nomes de tipo de contrato, escopos, número máximo de resultados solicitados e regras de correspondência de escopo.</span><span class="sxs-lookup"><span data-stu-id="ec581-113">Both of these methods take a <xref:System.ServiceModel.Discovery.FindCriteria> instance that allows you to specify contract type names, scopes, maximum number of results requested, and scope matching rules.</span></span> <span data-ttu-id="ec581-114">Os <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> eventos <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> e podem ser usados ao chamar o <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> método.</span><span class="sxs-lookup"><span data-stu-id="ec581-114">The <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> and <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> events can be used when calling the <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> method.</span></span> <span data-ttu-id="ec581-115"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged>é acionado sempre <xref:System.ServiceModel.Discovery.DiscoveryClient> que o recebe uma resposta de um serviço.</span><span class="sxs-lookup"><span data-stu-id="ec581-115"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> is fired whenever the <xref:System.ServiceModel.Discovery.DiscoveryClient> receives a response from a service.</span></span> <span data-ttu-id="ec581-116">Ele pode ser usado para exibir uma barra de progresso que mostra o progresso da operação de localização.</span><span class="sxs-lookup"><span data-stu-id="ec581-116">It can be used to display a progress bar showing the progress of the find operation.</span></span> <span data-ttu-id="ec581-117">Ele também pode ser usado para agir em busca de respostas à medida que elas são recebidas.</span><span class="sxs-lookup"><span data-stu-id="ec581-117">It can also be used to act on find responses as they are received.</span></span> <span data-ttu-id="ec581-118">O <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> evento é acionado quando a operação Localizar é concluída.</span><span class="sxs-lookup"><span data-stu-id="ec581-118">The <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> event is fired when the find operation completes.</span></span> <span data-ttu-id="ec581-119">Isso pode acontecer porque o número máximo de respostas foi recebido ou se o <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> foi decorrido.</span><span class="sxs-lookup"><span data-stu-id="ec581-119">This may happen because the maximum number of responses has been received or if the <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> has elapsed.</span></span> <span data-ttu-id="ec581-120">Quando a operação Localizar é concluída, os resultados são retornados em <xref:System.ServiceModel.Discovery.FindResponse> uma instância.</span><span class="sxs-lookup"><span data-stu-id="ec581-120">When the find operation completes the results are returned in a <xref:System.ServiceModel.Discovery.FindResponse> instance.</span></span> <span data-ttu-id="ec581-121">O <xref:System.ServiceModel.Discovery.FindResponse> contém uma coleção de <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> que contém os endereços, os nomes de tipo de contrato, as extensões, os URIs de escuta e os escopos dos serviços correspondentes.</span><span class="sxs-lookup"><span data-stu-id="ec581-121">The <xref:System.ServiceModel.Discovery.FindResponse> contains a collection of <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> which contains the addresses, contract type names, extensions, listen URIs, and scopes of the matching services.</span></span> <span data-ttu-id="ec581-122">Você pode usar essas informações para se conectar e chamar um dos serviços correspondentes.</span><span class="sxs-lookup"><span data-stu-id="ec581-122">You can then use this information to connect to and call one of the matching services.</span></span> <span data-ttu-id="ec581-123">O exemplo a seguir mostra como chamar o método System. ServiceModel. Discovery. DiscoveryClient. Localize (System. ServiceModel. Discovery. FindCriteria) e usar os metadados retornados para chamar o serviço encontrado.</span><span class="sxs-lookup"><span data-stu-id="ec581-123">The following example shows how to call the System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) method and use the returned metadata to call the found service.</span></span> <span data-ttu-id="ec581-124">Um benefício do uso <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> do é que você pode armazenar em cache a lista de pontos de extremidade que você encontrou e usá-los em um momento posterior.</span><span class="sxs-lookup"><span data-stu-id="ec581-124">A benefit of using <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> is that you can cache the list of endpoints you’ve found and use them at a later time.</span></span> <span data-ttu-id="ec581-125">Com esse cache, você pode criar uma lógica personalizada para lidar com várias condições de falha.</span><span class="sxs-lookup"><span data-stu-id="ec581-125">With this cache, you can build custom logic to handle various failure conditions.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="ec581-126">O exemplo a seguir mostra como executar uma operação Localizar de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="ec581-126">The following example shows how to perform a find operation asynchronously.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="ec581-127">Use os <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> métodos <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> e para localizar um serviço com base em seu endereço de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ec581-127">Use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> and <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> methods to locate a service based on its endpoint address.</span></span> <span data-ttu-id="ec581-128">Isso é útil quando o endereço do ponto de extremidade não é endereçável de rede.</span><span class="sxs-lookup"><span data-stu-id="ec581-128">This is useful when the endpoint address is not network addressable.</span></span> <span data-ttu-id="ec581-129">Os métodos de resolução tomam uma instância <xref:System.ServiceModel.Discovery.ResolveCriteria> do que permite especificar o endereço do ponto de extremidade do serviço que você está resolvendo, a duração máxima da operação de resolução e um conjunto de extensões.</span><span class="sxs-lookup"><span data-stu-id="ec581-129">The Resolve methods take an instance of <xref:System.ServiceModel.Discovery.ResolveCriteria> which allows you to specify the endpoint address of the service you are resolving, the maximum duration of the resolve operation, and a set of extensions.</span></span> <span data-ttu-id="ec581-130">O exemplo a seguir mostra como usar o <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> método para resolver um serviço.</span><span class="sxs-lookup"><span data-stu-id="ec581-130">The following example shows how to use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> method to resolve a service.</span></span>  
  
```csharp  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
ResolveCriteria criteria = new ResolveCriteria(endpointAddress);  
ResolveResponse response = dc.Resolve(criteria);  
EndpointAddress newEp = response.EndpointDiscoveryMetadata.Address;  
```  
  
## <a name="dynamicendpoint"></a><span data-ttu-id="ec581-131">DynamicEndpoint</span><span class="sxs-lookup"><span data-stu-id="ec581-131">DynamicEndpoint</span></span>  
 <span data-ttu-id="ec581-132"><xref:System.ServiceModel.Discovery.DynamicEndpoint>é um ponto de extremidade padrão (para obter mais informações, consulte [pontos de extremidades padrão](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)) que executa a descoberta e seleciona automaticamente um serviço correspondente.</span><span class="sxs-lookup"><span data-stu-id="ec581-132"><xref:System.ServiceModel.Discovery.DynamicEndpoint> is a standard endpoint (For more information, see [Standard Endpoints](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)) which performs discovery and automatically selects a matching service.</span></span> <span data-ttu-id="ec581-133">Basta criar uma <xref:System.ServiceModel.Discovery.DynamicEndpoint> passagem no contrato para pesquisar e a associação a ser usada e passar a <xref:System.ServiceModel.Discovery.DynamicEndpoint> instância para o cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="ec581-133">Just create a <xref:System.ServiceModel.Discovery.DynamicEndpoint> passing in the contract to search for and the binding to use and pass the <xref:System.ServiceModel.Discovery.DynamicEndpoint> instance to the WCF client.</span></span> <span data-ttu-id="ec581-134">O exemplo a seguir mostra como criar e usar um <xref:System.ServiceModel.Discovery.DynamicEndpoint> para chamar o serviço de calculadora.</span><span class="sxs-lookup"><span data-stu-id="ec581-134">The following example shows how to create and use a <xref:System.ServiceModel.Discovery.DynamicEndpoint> to call the calculator service.</span></span> <span data-ttu-id="ec581-135">A descoberta é executada toda vez que o cliente é aberto.</span><span class="sxs-lookup"><span data-stu-id="ec581-135">The discovery is performed every time the client is opened.</span></span> <span data-ttu-id="ec581-136">Qualquer ponto de extremidade definido na configuração também pode ser convertido <xref:System.ServiceModel.Discovery.DynamicEndpoint> em um adicionando `kind ="dynamicEndpoint"` o atributo ao elemento de configuração do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ec581-136">Any endpoint defined in configuration can also be turned into a <xref:System.ServiceModel.Discovery.DynamicEndpoint> by adding the `kind ="dynamicEndpoint"` attribute to the endpoint configuration element.</span></span>  
  
```csharp  
DynamicEndpoint dynamicEndpoint = new DynamicEndpoint(ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());  
CalculatorServiceClient client = new CalculatorServiceClient(dynamicEndpoint);  
  
Console.WriteLine("Invoking CalculatorService");  
Console.WriteLine();  
  
double value1 = 100.00D;  
double value2 = 15.99D;  
  
double result = client.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```  
  
## <a name="see-also"></a><span data-ttu-id="ec581-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ec581-137">See also</span></span>

- [<span data-ttu-id="ec581-138">Descoberta com escopos</span><span class="sxs-lookup"><span data-stu-id="ec581-138">Discovery with Scopes</span></span>](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)
- [<span data-ttu-id="ec581-139">Básico</span><span class="sxs-lookup"><span data-stu-id="ec581-139">Basic</span></span>](../../../../docs/framework/wcf/samples/basic-sample.md)
