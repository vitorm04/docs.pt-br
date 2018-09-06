---
title: FindCriteria e descoberta achada
ms.date: 03/30/2017
ms.assetid: 99016fa4-1778-495b-b4cc-0e22fbec42c6
ms.openlocfilehash: b2f679879bd3a32e770aa934f715dd70b4a2b5f8
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43855992"
---
# <a name="discovery-find-and-findcriteria"></a>FindCriteria e descoberta achada
Uma operação de localização de descoberta é iniciada por um cliente para descobrir um ou mais serviços e é uma das principais ações na descoberta. Executar um localizar envia uma mensagem de teste do WS-Discovery pela rede. Serviços que correspondem aos critérios especificados responder com mensagens WS-Discovery ProbeMatch. Para obter mais informações sobre as mensagens de descoberta, consulte o [especificação WS-Discovery](https://go.microsoft.com/fwlink/?LinkID=122347).  
  
## <a name="discoveryclient"></a>DiscoveryClient  
 O <xref:System.ServiceModel.Discovery.DiscoveryClient> classe fornece o mecanismo para executar operações de localização e facilita a execução de operações do cliente de descoberta fácil. Ele contém um <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> método, que executa uma busca de síncrona (bloqueio), e um <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> método, que inicia uma localização assíncrona sem bloqueio. Ambos os métodos usam um <xref:System.ServiceModel.Discovery.FindCriteria> parâmetro e fornecem resultados para o usuário por meio de um <xref:System.ServiceModel.Discovery.FindResponse> objeto.  
  
## <a name="findcriteria"></a>FindCriteria  
 <xref:System.ServiceModel.Discovery.FindCriteria> tem várias propriedades, que podem ser agrupadas em critérios de pesquisa, que especificam quais serviços você está procurando, e encontrar os critérios de término (quanto tempo a pesquisa deve durar). Um <xref:System.ServiceModel.Discovery.FindCriteria> pode conter vários critérios de pesquisa. Por padrão, o serviço deve corresponder a todos os componentes caso contrário, ele não considera próprio um serviço correspondente. Se você quiser localizar os serviços que correspondam somente alguns dos critérios, você pode implementar lógica de localização personalizada no serviço ou você pode usar várias consultas.  
  
 Critérios de pesquisa incluem:  
  
-   <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement> -Opcional. O nome do contrato do serviço que está sendo pesquisada e os critérios normalmente usados ao pesquisar por um serviço. Se mais de um nome de contrato for especificado, somente pontos de extremidade correspondentes a todos os contratos de resposta. Observe que no WCF um ponto de extremidade pode apenas suporta um contrato.  
  
-   <xref:System.ServiceModel.Discovery.Configuration.ScopeElement> -Opcional. Os escopos são URIs absolutos que são usados para categorizar os pontos de extremidade de serviço individuais. Talvez você queira usar isso em cenários onde vários pontos de extremidade expõem o mesmo contrato e desejar uma maneira para pesquisar um subconjunto de pontos de extremidade. Se mais de um escopo for especificado, somente pontos de extremidade correspondentes a todos os escopos de resposta.  
  
-   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchBy%2A> -Especifica o algoritmo correspondente a ser usado ao casar os escopos na mensagem do Probe com isso do ponto de extremidade. Há cinco regras de correspondência de escopo com suporte:  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByExact?displayProperty=nameWithType> diferencia maiusculas de minúsculas básico comparação cadeia de caracteres.  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix?displayProperty=nameWithType> correspondências por segmentos separados por "/". Uma pesquisa por http://contoso/building1 corresponde a um serviço com escopo http://contoso/building/floor1. Observe que não corresponde ao http://contoso/building100 porque os dois últimos segmentos não coincidem.  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByLdap?displayProperty=nameWithType> faz a correspondência escopos por segmentos usando uma URL LDAP.  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByUuid?displayProperty=nameWithType> corresponde a exatamente usando uma cadeia de caracteres UUID de escopos.  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByNone?displayProperty=nameWithType> corresponde a somente os serviços que não especificam um escopo.  
  
     Se uma regra de correspondência de escopo não for especificada, <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix> é usado.  
  
 Critérios de encerramento incluem:  
  
1.  <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> -O tempo máximo de espera por respostas de serviços na rede. A duração padrão é 20 segundos.  
  
2.  <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> -O número máximo de respostas a esperar. Se <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> respostas são recebidas antes de <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> tiver decorrido, o término da operação de localizar.  
  
## <a name="findresponse"></a>FindResponse  
 <xref:System.ServiceModel.Discovery.FindResponse> tem um <xref:System.ServiceModel.Discovery.FindResponse.Endpoints%2A> propriedade de coleção que contém as respostas enviadas por correspondência de serviços na rede. Se nenhum serviço respondida, a coleção está vazia. Se um ou mais serviços respondeu, cada resposta é armazenada em um <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> objeto, que contém o endereço, contrato e algumas informações adicionais sobre o serviço.  
  
 O exemplo a seguir mostra como executar uma operação de localização no código.  
  
```  
// Create DiscoveryClient  
DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
// Create FindCriteria  
FindCriteria findCriteria = new FindCriteria(typeof(IPrinterService));  
findCriteria.Scopes.Add(new Uri("http://www.contoso.com/building1/floor1"));  
findCriteria.Duration = TimeSpan.FromSeconds(10);   
  
// Find ICalculatorService endpoints              
FindResponse findResponse = discoveryClient.Find(findCriteria);  
  
Console.WriteLine("Found {0} ICalculatorService endpoint(s).", findResponse.Endpoints.Count)  
```  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de descoberta do WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [Usando o canal de cliente de descoberta](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)  
 [Descoberta com escopos](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)  
 [Descoberta assíncrona](../../../../docs/framework/wcf/samples/asynchronous-find-sample.md)  
 [Básico](../../../../docs/framework/wcf/samples/basic-sample.md)
