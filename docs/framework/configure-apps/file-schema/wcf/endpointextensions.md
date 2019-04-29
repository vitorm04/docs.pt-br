---
title: <endpointExtensions>
ms.date: 03/30/2017
ms.assetid: 33396e0a-1fae-4616-b822-923584eebfd1
ms.openlocfilehash: 12ac8d9a7b0ed584fb1308e56d197a03b1c53e51
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61700872"
---
# <a name="endpointextensions"></a><span data-ttu-id="8027c-101">\<endpointExtensions></span><span class="sxs-lookup"><span data-stu-id="8027c-101">\<endpointExtensions></span></span>
<span data-ttu-id="8027c-102">Esta seção registra um novo ponto de extremidade padrão na seção de extensões em um computador ou arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8027c-102">This section registers a new standard endpoint in the extensions section in a machine or application configuration file.</span></span> <span data-ttu-id="8027c-103">Você pode adicionar um ponto de extremidade padrão para esta coleção usando o `add` palavra-chave e a configuração o `type` atributo do elemento para o tipo de ponto de extremidade, bem como o `name` de atributo para o nome do ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="8027c-103">You can add a standard endpoint to this collection by using the `add` keyword, and setting the `type` attribute of the element to the endpoint type, as well as the `name` attribute to the name of the standard endpoint.</span></span>  
  
 <span data-ttu-id="8027c-104">O exemplo a seguir usa o `add` elemento, bem como o `name` atributo a ser adicionado a um ponto de extremidade padrão para o `<endpointExtensions>` seção do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="8027c-104">The following example uses the `add` element, as well as the `name` attribute to add a standard endpoint to the `<endpointExtensions>` section of the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="8027c-105">Depois que o ponto de extremidade padrão tiver sido registrado, você pode usá-lo conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="8027c-105">After the standard endpoint has been registered, you can use it as shown in the following example.</span></span> <span data-ttu-id="8027c-106">No [ \<ponto de extremidade >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) elemento, o `kind` atributo especifica o tipo de ponto de extremidade padrão que foi registrado no `<endpointExtensions>` seção.</span><span class="sxs-lookup"><span data-stu-id="8027c-106">In the [\<endpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element, the `kind` attribute specifies the standard endpoint type that has been registered in the `<endpointExtensions>` section.</span></span> <span data-ttu-id="8027c-107">O `endpointConfiguration` atributo será idêntico de `name` atributo do elemento de configuração do ponto de extremidade padrão no `<standardEndpoints>` seção.</span><span class="sxs-lookup"><span data-stu-id="8027c-107">The `endpointConfiguration` attribute will be identical to the `name` attribute of the configuration element of the standard endpoint in the `<standardEndpoints>` section.</span></span>  
  
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
