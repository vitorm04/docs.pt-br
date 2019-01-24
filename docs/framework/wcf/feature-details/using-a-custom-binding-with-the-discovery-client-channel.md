---
title: Utilizando uma associação personalizada com o canal cliente Discovery
ms.date: 03/30/2017
ms.assetid: 36f95e75-04f7-44f3-a995-a0d623624d7f
ms.openlocfilehash: 6fe9370bb22ca424774fc8cb4566e0802bc06697
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54698336"
---
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a><span data-ttu-id="03db3-102">Utilizando uma associação personalizada com o canal cliente Discovery</span><span class="sxs-lookup"><span data-stu-id="03db3-102">Using a Custom Binding with the Discovery Client Channel</span></span>
<span data-ttu-id="03db3-103">Ao usar uma associação personalizada com o <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, você deve definir um <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> que cria <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instâncias.</span><span class="sxs-lookup"><span data-stu-id="03db3-103">When using a custom binding with the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, you must define a <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> that creates <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances.</span></span>  
  
## <a name="creating-a-discoveryendpointprovider"></a><span data-ttu-id="03db3-104">Criando um DiscoveryEndpointProvider</span><span class="sxs-lookup"><span data-stu-id="03db3-104">Creating a DiscoveryEndpointProvider</span></span>  
 <span data-ttu-id="03db3-105">O <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> é responsável por criar <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instâncias sob demanda.</span><span class="sxs-lookup"><span data-stu-id="03db3-105">The <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> is responsible for creating <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances on demand.</span></span> <span data-ttu-id="03db3-106">Para definir um provedor de descoberta do ponto de extremidade, derive uma classe de <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> e substitua o <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> método e retornar um novo ponto de extremidade de descoberta.</span><span class="sxs-lookup"><span data-stu-id="03db3-106">To define a discovery endpoint provider, derive a class from <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> and override the <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> method and return a new discovery endpoint.</span></span> <span data-ttu-id="03db3-107">O exemplo a seguir mostra como criar um provedor de descoberta do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="03db3-107">The following example shows how to create a discovery endpoint provider.</span></span>  
  
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
  
 <span data-ttu-id="03db3-108">Depois de definir o provedor de descoberta de ponto de extremidade você pode criar uma ligação personalizada e adicionar o <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, que referencia o provedor de descoberta do ponto de extremidade, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="03db3-108">Once you have defined the discovery endpoint provider you can create a custom binding and add the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, which references the discovery endpoint provider as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="03db3-109">Para obter mais informações sobre como usar o canal cliente discovery, consulte [usando o canal cliente Discovery](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md).</span><span class="sxs-lookup"><span data-stu-id="03db3-109">For more information about using the discovery client channel, see [Using the Discovery Client Channel](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md).</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="03db3-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="03db3-110">See also</span></span>

- [<span data-ttu-id="03db3-111">Visão geral de descoberta do WCF</span><span class="sxs-lookup"><span data-stu-id="03db3-111">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [<span data-ttu-id="03db3-112">Usando o canal de cliente de descoberta</span><span class="sxs-lookup"><span data-stu-id="03db3-112">Using the Discovery Client Channel</span></span>](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)
