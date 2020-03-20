---
title: DiscoveryClient e DynamicEndpoint
ms.date: 03/30/2017
ms.assetid: 7cd418f0-0eab-48d1-a493-7eb907867ec3
ms.openlocfilehash: c6d87a04a6787725ad7c4546650485af932882b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185190"
---
# <a name="discoveryclient-and-dynamicendpoint"></a><span data-ttu-id="3ba42-102">DiscoveryClient e DynamicEndpoint</span><span class="sxs-lookup"><span data-stu-id="3ba42-102">DiscoveryClient and DynamicEndpoint</span></span>
<span data-ttu-id="3ba42-103"><xref:System.ServiceModel.Discovery.DiscoveryClient>e <xref:System.ServiceModel.Discovery.DynamicEndpoint> são duas classes usadas no lado do cliente para procurar serviços.</span><span class="sxs-lookup"><span data-stu-id="3ba42-103"><xref:System.ServiceModel.Discovery.DiscoveryClient> and <xref:System.ServiceModel.Discovery.DynamicEndpoint> are two classes used on the client side to search for services.</span></span> <span data-ttu-id="3ba42-104"><xref:System.ServiceModel.Discovery.DiscoveryClient>fornece uma lista de serviços que correspondem a um conjunto específico de critérios e permite que você se conecte aos serviços.</span><span class="sxs-lookup"><span data-stu-id="3ba42-104"><xref:System.ServiceModel.Discovery.DiscoveryClient> provides you with a list of services that match a specific set of criteria and allows you to connect to the services.</span></span> <span data-ttu-id="3ba42-105"><xref:System.ServiceModel.Discovery.DynamicEndpoint>realiza a mesma operação e, além disso, conecta-se automaticamente a um dos serviços encontrados.</span><span class="sxs-lookup"><span data-stu-id="3ba42-105"><xref:System.ServiceModel.Discovery.DynamicEndpoint> performs the same operation and in addition, automatically connects to one of the services that was found.</span></span> <span data-ttu-id="3ba42-106">Qualquer ponto final pode <xref:System.ServiceModel.Discovery.DynamicEndpoint>ser feito em um , os <xref:System.ServiceModel.Discovery.DynamicEndpoint> critérios de pesquisa também podem ser adicionados na configuração, assim, é útil quando você precisa de descoberta em sua solução, mas não quer modificar a lógica do cliente – você só precisa modificar os pontos finais.</span><span class="sxs-lookup"><span data-stu-id="3ba42-106">Any endpoint can be made into a <xref:System.ServiceModel.Discovery.DynamicEndpoint>, the search criteria can also be added in configuration, thus <xref:System.ServiceModel.Discovery.DynamicEndpoint> is useful when you need discovery in your solution but do not want to modify the client logic – you only need to modify the endpoints.</span></span> <span data-ttu-id="3ba42-107"><xref:System.ServiceModel.Discovery.DiscoveryClient>por outro lado, pode ser usado para obter um controle mais fino sobre sua operação de busca.</span><span class="sxs-lookup"><span data-stu-id="3ba42-107"><xref:System.ServiceModel.Discovery.DiscoveryClient> on the other hand can be used to gain finer control over your search operation.</span></span> <span data-ttu-id="3ba42-108">Os usos e benefícios de cada um são elaborados abaixo.</span><span class="sxs-lookup"><span data-stu-id="3ba42-108">The uses and benefits of each are elaborated below.</span></span>  
  
## <a name="discoveryclient"></a><span data-ttu-id="3ba42-109">Discoveryclient</span><span class="sxs-lookup"><span data-stu-id="3ba42-109">DiscoveryClient</span></span>  
 <span data-ttu-id="3ba42-110">O <xref:System.ServiceModel.Discovery.DiscoveryClient> define métodos <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> e <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> eventos síncronos e assíncronos.</span><span class="sxs-lookup"><span data-stu-id="3ba42-110">The <xref:System.ServiceModel.Discovery.DiscoveryClient> defines synchronous and asynchronous Find methods, <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> and <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> events.</span></span>  <span data-ttu-id="3ba42-111">Também define métodos de Resolução síncronos e <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> assíncronos e um evento.</span><span class="sxs-lookup"><span data-stu-id="3ba42-111">It also defines synchronous and asynchronous Resolve methods and a <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> event.</span></span> <span data-ttu-id="3ba42-112">Use <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> os <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> métodos para procurar serviços.</span><span class="sxs-lookup"><span data-stu-id="3ba42-112">Use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> or <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> methods to search for services.</span></span> <span data-ttu-id="3ba42-113">Ambos os métodos <xref:System.ServiceModel.Discovery.FindCriteria> tomam uma instância que permite especificar nomes de tipos de contrato, escopos, número máximo de resultados solicitados e regras de correspondência de escopo.</span><span class="sxs-lookup"><span data-stu-id="3ba42-113">Both of these methods take a <xref:System.ServiceModel.Discovery.FindCriteria> instance that allows you to specify contract type names, scopes, maximum number of results requested, and scope matching rules.</span></span> <span data-ttu-id="3ba42-114">Os <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> eventos podem ser usados ao chamar o <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> método.</span><span class="sxs-lookup"><span data-stu-id="3ba42-114">The <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> and <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> events can be used when calling the <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> method.</span></span> <span data-ttu-id="3ba42-115"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged>é demitido <xref:System.ServiceModel.Discovery.DiscoveryClient> sempre que recebe uma resposta de um serviço.</span><span class="sxs-lookup"><span data-stu-id="3ba42-115"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> is fired whenever the <xref:System.ServiceModel.Discovery.DiscoveryClient> receives a response from a service.</span></span> <span data-ttu-id="3ba42-116">Ele pode ser usado para exibir uma barra de progresso mostrando o progresso da operação de achado.</span><span class="sxs-lookup"><span data-stu-id="3ba42-116">It can be used to display a progress bar showing the progress of the find operation.</span></span> <span data-ttu-id="3ba42-117">Ele também pode ser usado para agir em encontrar respostas à medida que são recebidas.</span><span class="sxs-lookup"><span data-stu-id="3ba42-117">It can also be used to act on find responses as they are received.</span></span> <span data-ttu-id="3ba42-118">O <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> evento é acionado quando a operação de achado é concluída.</span><span class="sxs-lookup"><span data-stu-id="3ba42-118">The <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> event is fired when the find operation completes.</span></span> <span data-ttu-id="3ba42-119">Isso pode acontecer porque o número máximo de <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> respostas foi recebido ou se o decorrido.</span><span class="sxs-lookup"><span data-stu-id="3ba42-119">This may happen because the maximum number of responses has been received or if the <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> has elapsed.</span></span> <span data-ttu-id="3ba42-120">Quando a operação find é concluída, <xref:System.ServiceModel.Discovery.FindResponse> os resultados são devolvidos em uma instância.</span><span class="sxs-lookup"><span data-stu-id="3ba42-120">When the find operation completes the results are returned in a <xref:System.ServiceModel.Discovery.FindResponse> instance.</span></span> <span data-ttu-id="3ba42-121">O <xref:System.ServiceModel.Discovery.FindResponse> contém uma <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> coleção da qual contém endereços, nomes de tipos de contrato, extensões, URIs de escuta e escopos dos serviços correspondentes.</span><span class="sxs-lookup"><span data-stu-id="3ba42-121">The <xref:System.ServiceModel.Discovery.FindResponse> contains a collection of <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> which contains the addresses, contract type names, extensions, listen URIs, and scopes of the matching services.</span></span> <span data-ttu-id="3ba42-122">Em seguida, você pode usar essas informações para se conectar e ligar para um dos serviços correspondentes.</span><span class="sxs-lookup"><span data-stu-id="3ba42-122">You can then use this information to connect to and call one of the matching services.</span></span> <span data-ttu-id="3ba42-123">O exemplo a seguir mostra como chamar o método System.ServiceModel.Discovery.DiscoveryClient.Find (System.ServiceModel.Discovery.FindCriteria) e usar os metadados retornados para chamar o serviço encontrado.</span><span class="sxs-lookup"><span data-stu-id="3ba42-123">The following example shows how to call the System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) method and use the returned metadata to call the found service.</span></span> <span data-ttu-id="3ba42-124">Um benefício <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> de usar é que você pode armazenar a lista de pontos finais que você encontrou e usá-los posteriormente.</span><span class="sxs-lookup"><span data-stu-id="3ba42-124">A benefit of using <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> is that you can cache the list of endpoints you’ve found and use them at a later time.</span></span> <span data-ttu-id="3ba42-125">Com este cache, você pode construir uma lógica personalizada para lidar com várias condições de falha.</span><span class="sxs-lookup"><span data-stu-id="3ba42-125">With this cache, you can build custom logic to handle various failure conditions.</span></span>  
  
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
  
 <span data-ttu-id="3ba42-126">O exemplo a seguir mostra como executar uma operação de encontrar de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="3ba42-126">The following example shows how to perform a find operation asynchronously.</span></span>  
  
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
  
 <span data-ttu-id="3ba42-127">Use <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> os <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> métodos e métodos para localizar um serviço com base em seu endereço de ponto final.</span><span class="sxs-lookup"><span data-stu-id="3ba42-127">Use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> and <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> methods to locate a service based on its endpoint address.</span></span> <span data-ttu-id="3ba42-128">Isso é útil quando o endereço do ponto final não é endereçado à rede.</span><span class="sxs-lookup"><span data-stu-id="3ba42-128">This is useful when the endpoint address is not network addressable.</span></span> <span data-ttu-id="3ba42-129">Os métodos Resolver tomam <xref:System.ServiceModel.Discovery.ResolveCriteria> uma instância da qual permite especificar o endereço de ponto final do serviço que você está resolvendo, a duração máxima da operação de resolução e um conjunto de extensões.</span><span class="sxs-lookup"><span data-stu-id="3ba42-129">The Resolve methods take an instance of <xref:System.ServiceModel.Discovery.ResolveCriteria> which allows you to specify the endpoint address of the service you are resolving, the maximum duration of the resolve operation, and a set of extensions.</span></span> <span data-ttu-id="3ba42-130">O exemplo a seguir <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> mostra como usar o método para resolver um serviço.</span><span class="sxs-lookup"><span data-stu-id="3ba42-130">The following example shows how to use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> method to resolve a service.</span></span>  
  
```csharp  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
ResolveCriteria criteria = new ResolveCriteria(endpointAddress);  
ResolveResponse response = dc.Resolve(criteria);  
EndpointAddress newEp = response.EndpointDiscoveryMetadata.Address;  
```  
  
## <a name="dynamicendpoint"></a><span data-ttu-id="3ba42-131">Dynamicendpoint</span><span class="sxs-lookup"><span data-stu-id="3ba42-131">DynamicEndpoint</span></span>  
 <span data-ttu-id="3ba42-132"><xref:System.ServiceModel.Discovery.DynamicEndpoint>é um ponto final padrão (Para obter mais informações, consulte [Standard Endpoints](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)) que executa a detecção e seleciona automaticamente um serviço de correspondência.</span><span class="sxs-lookup"><span data-stu-id="3ba42-132"><xref:System.ServiceModel.Discovery.DynamicEndpoint> is a standard endpoint (For more information, see [Standard Endpoints](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)) which performs discovery and automatically selects a matching service.</span></span> <span data-ttu-id="3ba42-133">Basta criar <xref:System.ServiceModel.Discovery.DynamicEndpoint> um passe no contrato para pesquisar e <xref:System.ServiceModel.Discovery.DynamicEndpoint> a vinculação para usar e passar a instância para o cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="3ba42-133">Just create a <xref:System.ServiceModel.Discovery.DynamicEndpoint> passing in the contract to search for and the binding to use and pass the <xref:System.ServiceModel.Discovery.DynamicEndpoint> instance to the WCF client.</span></span> <span data-ttu-id="3ba42-134">O exemplo a seguir mostra <xref:System.ServiceModel.Discovery.DynamicEndpoint> como criar e usar um para chamar o serviço de calculadora.</span><span class="sxs-lookup"><span data-stu-id="3ba42-134">The following example shows how to create and use a <xref:System.ServiceModel.Discovery.DynamicEndpoint> to call the calculator service.</span></span> <span data-ttu-id="3ba42-135">A descoberta é realizada toda vez que o cliente é aberto.</span><span class="sxs-lookup"><span data-stu-id="3ba42-135">The discovery is performed every time the client is opened.</span></span> <span data-ttu-id="3ba42-136">Qualquer ponto final definido na configuração <xref:System.ServiceModel.Discovery.DynamicEndpoint> também `kind ="dynamicEndpoint"` pode ser transformado em um adicionando o atributo ao elemento de configuração do ponto final.</span><span class="sxs-lookup"><span data-stu-id="3ba42-136">Any endpoint defined in configuration can also be turned into a <xref:System.ServiceModel.Discovery.DynamicEndpoint> by adding the `kind ="dynamicEndpoint"` attribute to the endpoint configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3ba42-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="3ba42-137">See also</span></span>

- [<span data-ttu-id="3ba42-138">Descoberta com escopos</span><span class="sxs-lookup"><span data-stu-id="3ba42-138">Discovery with Scopes</span></span>](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)
- [<span data-ttu-id="3ba42-139">Basic</span><span class="sxs-lookup"><span data-stu-id="3ba42-139">Basic</span></span>](../../../../docs/framework/wcf/samples/basic-sample.md)
