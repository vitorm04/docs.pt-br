---
title: Utilizando uma associação personalizada com o canal cliente Discovery
ms.date: 03/30/2017
ms.assetid: 36f95e75-04f7-44f3-a995-a0d623624d7f
ms.openlocfilehash: 4ef85b4c52c1f27b333413e2b6178452142d313f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498352"
---
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a><span data-ttu-id="dc04b-102">Utilizando uma associação personalizada com o canal cliente Discovery</span><span class="sxs-lookup"><span data-stu-id="dc04b-102">Using a Custom Binding with the Discovery Client Channel</span></span>
<span data-ttu-id="dc04b-103">Ao usar uma associação personalizada com o <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, você deve definir um <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> que cria <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instâncias.</span><span class="sxs-lookup"><span data-stu-id="dc04b-103">When using a custom binding with the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, you must define a <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> that creates <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances.</span></span>  
  
## <a name="creating-a-discoveryendpointprovider"></a><span data-ttu-id="dc04b-104">Criando um DiscoveryEndpointProvider</span><span class="sxs-lookup"><span data-stu-id="dc04b-104">Creating a DiscoveryEndpointProvider</span></span>  
 <span data-ttu-id="dc04b-105">O <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> é responsável pela criação <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instâncias sob demanda.</span><span class="sxs-lookup"><span data-stu-id="dc04b-105">The <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> is responsible for creating <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances on demand.</span></span> <span data-ttu-id="dc04b-106">Para definir um provedor de descoberta de ponto de extremidade, derive uma classe de <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> e substituir o <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> método e retorna um novo ponto de extremidade de descoberta.</span><span class="sxs-lookup"><span data-stu-id="dc04b-106">To define a discovery endpoint provider, derive a class from <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> and override the <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> method and return a new discovery endpoint.</span></span> <span data-ttu-id="dc04b-107">O exemplo a seguir mostra como criar um provedor de descoberta de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="dc04b-107">The following example shows how to create a discovery endpoint provider.</span></span>  
  
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
  
 <span data-ttu-id="dc04b-108">Depois de definir o provedor de ponto de extremidade de descoberta pode criar uma associação personalizada e adicionar o <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, que referencia o provedor de descoberta de ponto de extremidade, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="dc04b-108">Once you have defined the discovery endpoint provider you can create a custom binding and add the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, which references the discovery endpoint provider as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="dc04b-109">Para obter mais informações sobre como usar o canal cliente discovery, consulte [usando o canal cliente Discovery](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md).</span><span class="sxs-lookup"><span data-stu-id="dc04b-109">For more information about using the discovery client channel, see [Using the Discovery Client Channel](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md).</span></span> <span data-ttu-id="dc04b-110">Para obter um exemplo de código completo, consulte [amostra do elemento de associação de descoberta](../../../../docs/framework/wcf/samples/discovery-binding-element-sample.md)</span><span class="sxs-lookup"><span data-stu-id="dc04b-110">For a complete code example, see [Discovery Binding Element Sample](../../../../docs/framework/wcf/samples/discovery-binding-element-sample.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc04b-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dc04b-111">See Also</span></span>  
 [<span data-ttu-id="dc04b-112">Visão geral de descoberta do WCF</span><span class="sxs-lookup"><span data-stu-id="dc04b-112">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [<span data-ttu-id="dc04b-113">Usando o canal de cliente de descoberta</span><span class="sxs-lookup"><span data-stu-id="dc04b-113">Using the Discovery Client Channel</span></span>](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)  
 [<span data-ttu-id="dc04b-114">Exemplo de elemento de associação de descoberta</span><span class="sxs-lookup"><span data-stu-id="dc04b-114">Discovery Binding Element Sample</span></span>](../../../../docs/framework/wcf/samples/discovery-binding-element-sample.md)
