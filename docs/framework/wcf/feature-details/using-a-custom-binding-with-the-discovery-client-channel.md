---
title: Utilizando uma associação personalizada com o canal cliente Discovery
ms.date: 03/30/2017
ms.assetid: 36f95e75-04f7-44f3-a995-a0d623624d7f
ms.openlocfilehash: 5f3f5fe24d1f19ce503b793d9aad870d882c7971
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184283"
---
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a>Utilizando uma associação personalizada com o canal cliente Discovery
Ao usar uma vinculação personalizada com o <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, você deve definir um <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> que cria <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instâncias.  
  
## <a name="creating-a-discoveryendpointprovider"></a>Criando um Provedor discoveryendpoint  
 O <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> é responsável <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> por criar instâncias demanda. Para definir um provedor de ponto <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> final de <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> descoberta, obtenha uma classe e anule o método e retorne um novo ponto final de descoberta. O exemplo a seguir mostra como criar um provedor de ponto final de descoberta.  
  
```csharp
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
  
 Depois de definir o provedor de ponto final de <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>descoberta, você pode criar uma vinculação personalizada e adicionar o , que faz referência ao provedor de ponto final de detecção como mostrado no exemplo a seguir.  
  
```csharp
DiscoveryClientBindingElement discoveryBindingElement = new DiscoveryClientBindingElement();  
  
// Provide the search criteria and the endpoint over which the probe is sent.  
discoveryBindingElement.FindCriteria = new FindCriteria(typeof(ICalculatorService));  
discoveryBindingElement.DiscoveryEndpointProvider = new UdpDiscoveryEndpointProvider();  
  
CustomBinding customBinding = new CustomBinding(new NetTcpBinding());  
// Insert DiscoveryClientBindingElement at the top of the BindingElement stack.  
// An exception is thrown if this binding element is not at the top.  
customBinding.Elements.Insert(0, discoveryBindingElement);  
```  
  
 Para obter mais informações sobre como usar o canal cliente de descoberta, consulte [Usando o Discovery Client Channel](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md).
  
## <a name="see-also"></a>Confira também

- [Visão geral de descoberta do WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [Usando o canal cliente Discovery](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)
