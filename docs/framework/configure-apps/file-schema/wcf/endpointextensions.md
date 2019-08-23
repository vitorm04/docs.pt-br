---
title: <endpointExtensions>
ms.date: 03/30/2017
ms.assetid: 33396e0a-1fae-4616-b822-923584eebfd1
ms.openlocfilehash: fe57cb84cfa70b1f6b92abf1dbac89ddad9d4dc8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925707"
---
# <a name="endpointextensions"></a><span data-ttu-id="6497f-101">\<endpointExtensions></span><span class="sxs-lookup"><span data-stu-id="6497f-101">\<endpointExtensions></span></span>
<span data-ttu-id="6497f-102">Esta seção registra um novo ponto de extremidade padrão na seção extensões em um computador ou arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6497f-102">This section registers a new standard endpoint in the extensions section in a machine or application configuration file.</span></span> <span data-ttu-id="6497f-103">Você pode adicionar um ponto de extremidade padrão a essa coleção usando `add` a palavra-chave e `type` definindo o atributo do elemento como o tipo de ponto de extremidade, `name` bem como o atributo para o nome do ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="6497f-103">You can add a standard endpoint to this collection by using the `add` keyword, and setting the `type` attribute of the element to the endpoint type, as well as the `name` attribute to the name of the standard endpoint.</span></span>  
  
 <span data-ttu-id="6497f-104">O exemplo a seguir usa `add` o elemento, bem como o `name` atributo para adicionar `<endpointExtensions>` um ponto de extremidade padrão à seção do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="6497f-104">The following example uses the `add` element, as well as the `name` attribute to add a standard endpoint to the `<endpointExtensions>` section of the configuration file.</span></span>  
  
```xml  
<system.serviceModel>
  <extensions>
    <endpointExtensions>
      <add name="udpDiscoveryEndpoint"
           type="System.Discovery.UdpEndpointCollectionElement, System.Discovery.dll, Version=1.0.0.0, Culture=neutral, PublicKeyToken=ffffffffffffffff"/>
    </endpointExtensions>
  </extensions>
</system.serviceModel>
```  
  
 <span data-ttu-id="6497f-105">Depois que o ponto de extremidade padrão tiver sido registrado, você poderá usá-lo conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="6497f-105">After the standard endpoint has been registered, you can use it as shown in the following example.</span></span> <span data-ttu-id="6497f-106">No elemento `kind` `<endpointExtensions>` Endpoint >, o atributo especifica o tipo de ponto de extremidade padrão que foi registrado na seção. [ \<](endpoint-element.md)</span><span class="sxs-lookup"><span data-stu-id="6497f-106">In the [\<endpoint>](endpoint-element.md) element, the `kind` attribute specifies the standard endpoint type that has been registered in the `<endpointExtensions>` section.</span></span> <span data-ttu-id="6497f-107">O `endpointConfiguration` atributo será idêntico `name` ao atributo do elemento de configuração do ponto de extremidade padrão na `<standardEndpoints>` seção.</span><span class="sxs-lookup"><span data-stu-id="6497f-107">The `endpointConfiguration` attribute will be identical to the `name` attribute of the configuration element of the standard endpoint in the `<standardEndpoints>` section.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service name="Service1">
      <endpoint kind="udpDiscoveryEndpoint"
                endpointConfiguration="udpConfig" />
    </service>
  </services>
  <standardEndpoints>
    <udpDiscoveryEndpoint>
      <standardEndpoint name="udpConfig"
                        multicastAddress="soap.udp://239.255.255.250:3703"
                        ... />
    </udpDiscoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
