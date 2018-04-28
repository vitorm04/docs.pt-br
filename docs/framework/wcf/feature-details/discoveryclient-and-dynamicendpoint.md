---
title: DiscoveryClient e DynamicEndpoint
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7cd418f0-0eab-48d1-a493-7eb907867ec3
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c652e58b20a6fe836e647ed07c6a84328ee4631e
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="discoveryclient-and-dynamicendpoint"></a>DiscoveryClient e DynamicEndpoint
<xref:System.ServiceModel.Discovery.DiscoveryClient> e <xref:System.ServiceModel.Discovery.DynamicEndpoint> são duas classes usadas no lado do cliente para procurar serviços. <xref:System.ServiceModel.Discovery.DiscoveryClient> Fornece uma lista de serviços que correspondam a um determinado conjunto de critérios e permite que você se conecte aos serviços. <xref:System.ServiceModel.Discovery.DynamicEndpoint> executa a mesma operação e Além disso, conecta-se automaticamente para um dos serviços que foi encontrado. Qualquer ponto de extremidade pode ser transformado em um <xref:System.ServiceModel.Discovery.DynamicEndpoint>, os critérios de pesquisa também podem ser adicionados na configuração, portanto, <xref:System.ServiceModel.Discovery.DynamicEndpoint> é útil quando você precisa de descoberta em sua solução, mas não deseja modificar a lógica do cliente – você só precisa modificar os pontos de extremidade. <xref:System.ServiceModel.Discovery.DiscoveryClient> Por outro lado, pode ser usado para obter um controle mais preciso sobre a operação de pesquisa. Os usos e benefícios de cada são elaborados abaixo.  
  
## <a name="discoveryclient"></a>DiscoveryClient  
 O <xref:System.ServiceModel.Discovery.DiscoveryClient> define métodos síncronos e assíncronos de localização, <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> e <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> eventos.  Ele também define os métodos Resolve síncronos e assíncronos e um <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> eventos. Use o <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> ou <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> métodos para procurar serviços. Ambos os métodos levar um <xref:System.ServiceModel.Discovery.FindCriteria> instância que permite que você especifique nomes de tipo de contrato, escopos, o número máximo de resultados solicitado e o escopo de regras de correspondência. O <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> e <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> eventos podem ser usados ao chamar o <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> método. <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> é acionado sempre que o <xref:System.ServiceModel.Discovery.DiscoveryClient> recebe uma resposta de um serviço. Ele pode ser usado para exibir um barra de progresso demonstrando o progresso da operação de localização. Ele também pode ser usado para agir em localizar respostas que são recebidas. O <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> evento é acionado quando a operação de localização é concluída. Isso pode ocorrer porque o número máximo de respostas foi recebido ou se o <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> expirou. Ao concluir a operação de localizar os resultados são retornados em um <xref:System.ServiceModel.Discovery.FindResponse> instância. O <xref:System.ServiceModel.Discovery.FindResponse> contém uma coleção de <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> que contém endereços, nomes de tipo de contrato, extensões, URIs de escuta e escopos dos serviços correspondentes. Você pode usar essas informações para conectar e chamar um dos serviços de correspondência. O exemplo a seguir mostra como chamar o método System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) e usar os metadados retornados para chamar o serviço encontrado. Uma vantagem de usar <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> é que você pode armazenar em cache a lista de pontos de extremidade encontradas e usá-los mais tarde. Com esse cache, você pode criar lógica personalizada para lidar com várias condições de falha.  
  
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
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] tornando assíncrona localizar chamadas, consulte [localizar assíncrona](../../../../docs/framework/wcf/samples/asynchronous-find-sample.md).  
  
 Use o <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> e <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> métodos para localizar um serviço baseiam em seu endereço de ponto de extremidade. Isso é útil quando o endereço do ponto de extremidade não é rede endereçável. Os métodos de resolução levar a uma instância de <xref:System.ServiceModel.Discovery.ResolveCriteria> que permite que você especifique o endereço de ponto de extremidade do serviço que você está resolvendo, a duração máxima da operação de resolução e um conjunto de extensões. O exemplo a seguir mostra como usar o <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> método para resolver um serviço.  
  
```  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
ResolveCriteria criteria = new ResolveCriteria(endpointAddress);  
ResolveResponse response = dc.Resolve(criteria);  
EndpointAddress newEp = response.EndpointDiscoveryMetadata.Address;  
```  
  
## <a name="dynamicendpoint"></a>DynamicEndpoint  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint> é um ponto de extremidade padrão (para obter mais informações, consulte [pontos de extremidade padrão](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)) que executa a descoberta e seleciona automaticamente um serviço correspondente. Crie um <xref:System.ServiceModel.Discovery.DynamicEndpoint> passando o contrato para pesquisa e a associação usar e passar o <xref:System.ServiceModel.Discovery.DynamicEndpoint> instância para o cliente do WCF. O exemplo a seguir mostra como criar e usar um <xref:System.ServiceModel.Discovery.DynamicEndpoint> para chamar o serviço da Calculadora. A descoberta é executada sempre que o cliente é aberto. Qualquer ponto de extremidade definido na configuração também pode ser transformado em um <xref:System.ServiceModel.Discovery.DynamicEndpoint> adicionando o `kind ="dynamicEndpoint"` de atributo para o elemento de configuração de ponto de extremidade.  
  
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
 [Descoberta assíncrona](../../../../docs/framework/wcf/samples/asynchronous-find-sample.md)  
 [Básico](../../../../docs/framework/wcf/samples/basic-sample.md)
