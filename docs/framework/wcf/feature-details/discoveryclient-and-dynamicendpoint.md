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
# <a name="discoveryclient-and-dynamicendpoint"></a>DiscoveryClient e DynamicEndpoint
<xref:System.ServiceModel.Discovery.DiscoveryClient>e <xref:System.ServiceModel.Discovery.DynamicEndpoint> são duas classes usadas no lado do cliente para procurar serviços. <xref:System.ServiceModel.Discovery.DiscoveryClient>fornece uma lista de serviços que correspondem a um conjunto específico de critérios e permite que você se conecte aos serviços. <xref:System.ServiceModel.Discovery.DynamicEndpoint>realiza a mesma operação e, além disso, conecta-se automaticamente a um dos serviços encontrados. Qualquer ponto final pode <xref:System.ServiceModel.Discovery.DynamicEndpoint>ser feito em um , os <xref:System.ServiceModel.Discovery.DynamicEndpoint> critérios de pesquisa também podem ser adicionados na configuração, assim, é útil quando você precisa de descoberta em sua solução, mas não quer modificar a lógica do cliente – você só precisa modificar os pontos finais. <xref:System.ServiceModel.Discovery.DiscoveryClient>por outro lado, pode ser usado para obter um controle mais fino sobre sua operação de busca. Os usos e benefícios de cada um são elaborados abaixo.  
  
## <a name="discoveryclient"></a>Discoveryclient  
 O <xref:System.ServiceModel.Discovery.DiscoveryClient> define métodos <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> e <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> eventos síncronos e assíncronos.  Também define métodos de Resolução síncronos e <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> assíncronos e um evento. Use <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> os <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> métodos para procurar serviços. Ambos os métodos <xref:System.ServiceModel.Discovery.FindCriteria> tomam uma instância que permite especificar nomes de tipos de contrato, escopos, número máximo de resultados solicitados e regras de correspondência de escopo. Os <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> eventos podem ser usados ao chamar o <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> método. <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged>é demitido <xref:System.ServiceModel.Discovery.DiscoveryClient> sempre que recebe uma resposta de um serviço. Ele pode ser usado para exibir uma barra de progresso mostrando o progresso da operação de achado. Ele também pode ser usado para agir em encontrar respostas à medida que são recebidas. O <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> evento é acionado quando a operação de achado é concluída. Isso pode acontecer porque o número máximo de <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> respostas foi recebido ou se o decorrido. Quando a operação find é concluída, <xref:System.ServiceModel.Discovery.FindResponse> os resultados são devolvidos em uma instância. O <xref:System.ServiceModel.Discovery.FindResponse> contém uma <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> coleção da qual contém endereços, nomes de tipos de contrato, extensões, URIs de escuta e escopos dos serviços correspondentes. Em seguida, você pode usar essas informações para se conectar e ligar para um dos serviços correspondentes. O exemplo a seguir mostra como chamar o método System.ServiceModel.Discovery.DiscoveryClient.Find (System.ServiceModel.Discovery.FindCriteria) e usar os metadados retornados para chamar o serviço encontrado. Um benefício <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> de usar é que você pode armazenar a lista de pontos finais que você encontrou e usá-los posteriormente. Com este cache, você pode construir uma lógica personalizada para lidar com várias condições de falha.  
  
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
  
 O exemplo a seguir mostra como executar uma operação de encontrar de forma assíncrona.  
  
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
  
 Use <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> os <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> métodos e métodos para localizar um serviço com base em seu endereço de ponto final. Isso é útil quando o endereço do ponto final não é endereçado à rede. Os métodos Resolver tomam <xref:System.ServiceModel.Discovery.ResolveCriteria> uma instância da qual permite especificar o endereço de ponto final do serviço que você está resolvendo, a duração máxima da operação de resolução e um conjunto de extensões. O exemplo a seguir <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> mostra como usar o método para resolver um serviço.  
  
```csharp  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
ResolveCriteria criteria = new ResolveCriteria(endpointAddress);  
ResolveResponse response = dc.Resolve(criteria);  
EndpointAddress newEp = response.EndpointDiscoveryMetadata.Address;  
```  
  
## <a name="dynamicendpoint"></a>Dynamicendpoint  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>é um ponto final padrão (Para obter mais informações, consulte [Standard Endpoints](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)) que executa a detecção e seleciona automaticamente um serviço de correspondência. Basta criar <xref:System.ServiceModel.Discovery.DynamicEndpoint> um passe no contrato para pesquisar e <xref:System.ServiceModel.Discovery.DynamicEndpoint> a vinculação para usar e passar a instância para o cliente WCF. O exemplo a seguir mostra <xref:System.ServiceModel.Discovery.DynamicEndpoint> como criar e usar um para chamar o serviço de calculadora. A descoberta é realizada toda vez que o cliente é aberto. Qualquer ponto final definido na configuração <xref:System.ServiceModel.Discovery.DynamicEndpoint> também `kind ="dynamicEndpoint"` pode ser transformado em um adicionando o atributo ao elemento de configuração do ponto final.  
  
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
  
## <a name="see-also"></a>Confira também

- [Descoberta com escopos](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)
- [Basic](../../../../docs/framework/wcf/samples/basic-sample.md)
