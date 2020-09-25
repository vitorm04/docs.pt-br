---
title: <endpointExtensions>
ms.date: 03/30/2017
ms.assetid: 33396e0a-1fae-4616-b822-923584eebfd1
ms.openlocfilehash: d0587ae942d1b0c7eb72bee830ca3ced76e4270c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190027"
---
# \<endpointExtensions>

<span data-ttu-id="d356e-101">Esta seção registra um novo ponto de extremidade padrão na seção extensões em um computador ou arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d356e-101">This section registers a new standard endpoint in the extensions section in a machine or application configuration file.</span></span> <span data-ttu-id="d356e-102">Você pode adicionar um ponto de extremidade padrão a essa coleção usando a `add` palavra-chave e definindo o `type` atributo do elemento como o tipo de ponto de extremidade, bem como o `name` atributo para o nome do ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="d356e-102">You can add a standard endpoint to this collection by using the `add` keyword, and setting the `type` attribute of the element to the endpoint type, as well as the `name` attribute to the name of the standard endpoint.</span></span>  
  
 <span data-ttu-id="d356e-103">O exemplo a seguir usa o `add` elemento, bem como o `name` atributo para adicionar um ponto de extremidade padrão à `<endpointExtensions>` seção do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="d356e-103">The following example uses the `add` element, as well as the `name` attribute to add a standard endpoint to the `<endpointExtensions>` section of the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="d356e-104">Depois que o ponto de extremidade padrão tiver sido registrado, você poderá usá-lo conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="d356e-104">After the standard endpoint has been registered, you can use it as shown in the following example.</span></span> <span data-ttu-id="d356e-105">No [\<endpoint>](endpoint-element.md) elemento, o `kind` atributo especifica o tipo de ponto de extremidade padrão que foi registrado na `<endpointExtensions>` seção.</span><span class="sxs-lookup"><span data-stu-id="d356e-105">In the [\<endpoint>](endpoint-element.md) element, the `kind` attribute specifies the standard endpoint type that has been registered in the `<endpointExtensions>` section.</span></span> <span data-ttu-id="d356e-106">O `endpointConfiguration` atributo será idêntico ao `name` atributo do elemento de configuração do ponto de extremidade padrão na `<standardEndpoints>` seção.</span><span class="sxs-lookup"><span data-stu-id="d356e-106">The `endpointConfiguration` attribute will be identical to the `name` attribute of the configuration element of the standard endpoint in the `<standardEndpoints>` section.</span></span>  
  
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
