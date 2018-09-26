---
title: Utilizando uma associação personalizada com o canal cliente Discovery
ms.date: 03/30/2017
ms.assetid: 36f95e75-04f7-44f3-a995-a0d623624d7f
ms.openlocfilehash: 7473262ec52adfd917b8ec5cd7ec1f4935a3646d
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47195219"
---
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a>Utilizando uma associação personalizada com o canal cliente Discovery
Ao usar uma associação personalizada com o <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, você deve definir um <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> que cria <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instâncias.  
  
## <a name="creating-a-discoveryendpointprovider"></a>Criando um DiscoveryEndpointProvider  
 O <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> é responsável por criar <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instâncias sob demanda. Para definir um provedor de descoberta do ponto de extremidade, derive uma classe de <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> e substitua o <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> método e retornar um novo ponto de extremidade de descoberta. O exemplo a seguir mostra como criar um provedor de descoberta do ponto de extremidade.  
  
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
  
 Depois de definir o provedor de descoberta de ponto de extremidade você pode criar uma ligação personalizada e adicionar o <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, que referencia o provedor de descoberta do ponto de extremidade, conforme mostrado no exemplo a seguir.  
  
```  
DiscoveryClientBindingElement discoveryBindingElement = new DiscoveryClientBindingElement();  
  
// Provide the search criteria and the endpoint over which the probe is sent.  
discoveryBindingElement.FindCriteria = new FindCriteria(typeof(ICalculatorService));  
discoveryBindingElement.DiscoveryEndpointProvider = new UdpDiscoveryEndpointProvider();  
  
CustomBinding customBinding = new CustomBinding(new NetTcpBinding());  
// Insert DiscoveryClientBindingElement at the top of the BindingElement stack.  
// An exception is thrown if this binding element is not at the top.  
customBinding.Elements.Insert(0, discoveryBindingElement);  
```  
  
 Para obter mais informações sobre como usar o canal cliente discovery, consulte [usando o canal cliente Discovery](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md). 
  
## <a name="see-also"></a>Consulte também  

- [Visão geral de descoberta do WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
- [Usando o canal de cliente de descoberta](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)  