---
title: DiscoveryClient e DynamicEndpoint
ms.date: 03/30/2017
ms.assetid: 7cd418f0-0eab-48d1-a493-7eb907867ec3
ms.openlocfilehash: ff8cc071b13123a8d04162a2c52a8c3fb486d6db
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47205402"
---
# <a name="discoveryclient-and-dynamicendpoint"></a>DiscoveryClient e DynamicEndpoint
<xref:System.ServiceModel.Discovery.DiscoveryClient> e <xref:System.ServiceModel.Discovery.DynamicEndpoint> são duas classes usadas no lado do cliente para pesquisar serviços. <xref:System.ServiceModel.Discovery.DiscoveryClient> Fornece uma lista de serviços que correspondem a um determinado conjunto de critérios e permite que você se conecte aos serviços. <xref:System.ServiceModel.Discovery.DynamicEndpoint> executa a mesma operação e Além disso, se conecta automaticamente a um dos serviços que foi encontrado. Qualquer ponto de extremidade pode ser feito em um <xref:System.ServiceModel.Discovery.DynamicEndpoint>, os critérios de pesquisa também podem ser adicionados na configuração, portanto <xref:System.ServiceModel.Discovery.DynamicEndpoint> é útil quando você precisa descoberta em sua solução, mas não desejar modificar a lógica do cliente – você só precisa modificar os pontos de extremidade. <xref:System.ServiceModel.Discovery.DiscoveryClient> Por outro lado, pode ser usado para obter um melhor controle sobre a operação de pesquisa. Os usos e benefícios de cada são elaborados abaixo.  
  
## <a name="discoveryclient"></a>DiscoveryClient  
 O <xref:System.ServiceModel.Discovery.DiscoveryClient> define os métodos Find síncronos e assíncronos, <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> e <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> eventos.  Ele também define os métodos de resolução síncronos e assíncronos e um <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> eventos. Use o <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> ou <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> métodos para pesquisar serviços. Ambos os métodos levar um <xref:System.ServiceModel.Discovery.FindCriteria> instância que permite que você especifique nomes de tipo de contrato, escopos, o número máximo de resultados solicitado e escopo de regras de correspondência. O <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> e <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> eventos podem ser usados ao chamar o <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> método. <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> é acionado sempre que o <xref:System.ServiceModel.Discovery.DiscoveryClient> recebe uma resposta de um serviço. Ele pode ser usado para exibir um barra de progresso da mostrando o progresso da operação de localização. Ele também pode ser usado para agir em respostas de localização conforme elas são recebidas. O <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> evento é acionado quando a operação de localização é concluída. Isso pode acontecer porque o número máximo de respostas foi recebido ou se o <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> tiver decorrido. Quando a operação de localização é concluída os resultados são retornados em um <xref:System.ServiceModel.Discovery.FindResponse> instância. O <xref:System.ServiceModel.Discovery.FindResponse> contém uma coleção de <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> que contém os endereços, nomes de tipo de contrato, extensões, URIs de escuta e os escopos dos serviços correspondentes. Em seguida, você pode usar essas informações para conectar e chame um dos serviços correspondentes. O exemplo a seguir mostra como chamar o método System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) e usar os metadados retornados para chamar o serviço encontrado. Uma vantagem de usar <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> é que você pode armazenar em cache a lista de pontos de extremidade descobri e usá-los em um momento posterior. Com este cache, você pode criar lógica personalizada para manipular várias condições de falha.  
  
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
  
 O exemplo a seguir mostra como executar uma operação de localização de forma assíncrona.  
  
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
  
 Use o <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> e <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> métodos para localizar um serviço baseado em seu endereço de ponto de extremidade. Isso é útil quando o endereço do ponto de extremidade não é rede endereçável. Os métodos de resolução usam uma instância de <xref:System.ServiceModel.Discovery.ResolveCriteria> que permite que você especifique o endereço do ponto de extremidade do serviço de resolução, a duração máxima da operação de resolução e um conjunto de extensões. O exemplo a seguir mostra como usar o <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> método para resolver um serviço.  
  
```  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
ResolveCriteria criteria = new ResolveCriteria(endpointAddress);  
ResolveResponse response = dc.Resolve(criteria);  
EndpointAddress newEp = response.EndpointDiscoveryMetadata.Address;  
```  
  
## <a name="dynamicendpoint"></a>DynamicEndpoint  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint> é um ponto de extremidade padrão (para obter mais informações, consulte [pontos de extremidade padrão](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)) que executa a descoberta e seleciona automaticamente um serviço correspondente. Basta criar uma <xref:System.ServiceModel.Discovery.DynamicEndpoint> passando o contrato para pesquisa e a associação usar e passar o <xref:System.ServiceModel.Discovery.DynamicEndpoint> instância para o cliente do WCF. O exemplo a seguir mostra como criar e usar um <xref:System.ServiceModel.Discovery.DynamicEndpoint> para chamar o serviço da Calculadora. A descoberta é executada sempre que o cliente é aberto. Qualquer ponto de extremidade definido na configuração também pode ser transformado em um <xref:System.ServiceModel.Discovery.DynamicEndpoint> adicionando o `kind ="dynamicEndpoint"` atributo ao elemento de configuração de ponto de extremidade.  
  
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
  
## <a name="see-also"></a>Consulte também  
 [Descoberta com escopos](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)  
 [Básico](../../../../docs/framework/wcf/samples/basic-sample.md)
