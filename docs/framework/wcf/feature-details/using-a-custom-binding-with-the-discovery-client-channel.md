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
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a><span data-ttu-id="7a0dd-102">Utilizando uma associação personalizada com o canal cliente Discovery</span><span class="sxs-lookup"><span data-stu-id="7a0dd-102">Using a Custom Binding with the Discovery Client Channel</span></span>
<span data-ttu-id="7a0dd-103">Ao usar uma vinculação personalizada com o <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, você deve definir um <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> que cria <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instâncias.</span><span class="sxs-lookup"><span data-stu-id="7a0dd-103">When using a custom binding with the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, you must define a <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> that creates <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances.</span></span>  
  
## <a name="creating-a-discoveryendpointprovider"></a><span data-ttu-id="7a0dd-104">Criando um Provedor discoveryendpoint</span><span class="sxs-lookup"><span data-stu-id="7a0dd-104">Creating a DiscoveryEndpointProvider</span></span>  
 <span data-ttu-id="7a0dd-105">O <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> é responsável <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> por criar instâncias demanda.</span><span class="sxs-lookup"><span data-stu-id="7a0dd-105">The <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> is responsible for creating <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances on demand.</span></span> <span data-ttu-id="7a0dd-106">Para definir um provedor de ponto <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> final de <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> descoberta, obtenha uma classe e anule o método e retorne um novo ponto final de descoberta.</span><span class="sxs-lookup"><span data-stu-id="7a0dd-106">To define a discovery endpoint provider, derive a class from <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> and override the <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> method and return a new discovery endpoint.</span></span> <span data-ttu-id="7a0dd-107">O exemplo a seguir mostra como criar um provedor de ponto final de descoberta.</span><span class="sxs-lookup"><span data-stu-id="7a0dd-107">The following example shows how to create a discovery endpoint provider.</span></span>  
  
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
  
 <span data-ttu-id="7a0dd-108">Depois de definir o provedor de ponto final de <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>descoberta, você pode criar uma vinculação personalizada e adicionar o , que faz referência ao provedor de ponto final de detecção como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="7a0dd-108">Once you have defined the discovery endpoint provider you can create a custom binding and add the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, which references the discovery endpoint provider as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="7a0dd-109">Para obter mais informações sobre como usar o canal cliente de descoberta, consulte [Usando o Discovery Client Channel](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md).</span><span class="sxs-lookup"><span data-stu-id="7a0dd-109">For more information about using the discovery client channel, see [Using the Discovery Client Channel](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7a0dd-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="7a0dd-110">See also</span></span>

- [<span data-ttu-id="7a0dd-111">Visão geral de descoberta do WCF</span><span class="sxs-lookup"><span data-stu-id="7a0dd-111">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [<span data-ttu-id="7a0dd-112">Usando o canal cliente Discovery</span><span class="sxs-lookup"><span data-stu-id="7a0dd-112">Using the Discovery Client Channel</span></span>](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)
