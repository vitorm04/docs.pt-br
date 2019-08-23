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
# <a name="endpointextensions"></a>\<endpointExtensions>
Esta seção registra um novo ponto de extremidade padrão na seção extensões em um computador ou arquivo de configuração de aplicativo. Você pode adicionar um ponto de extremidade padrão a essa coleção usando `add` a palavra-chave e `type` definindo o atributo do elemento como o tipo de ponto de extremidade, `name` bem como o atributo para o nome do ponto de extremidade padrão.  
  
 O exemplo a seguir usa `add` o elemento, bem como o `name` atributo para adicionar `<endpointExtensions>` um ponto de extremidade padrão à seção do arquivo de configuração.  
  
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
  
 Depois que o ponto de extremidade padrão tiver sido registrado, você poderá usá-lo conforme mostrado no exemplo a seguir. No elemento `kind` `<endpointExtensions>` Endpoint >, o atributo especifica o tipo de ponto de extremidade padrão que foi registrado na seção. [ \<](endpoint-element.md) O `endpointConfiguration` atributo será idêntico `name` ao atributo do elemento de configuração do ponto de extremidade padrão na `<standardEndpoints>` seção.  
  
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
