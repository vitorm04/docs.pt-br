---
title: <endpointExtensions>
ms.date: 03/30/2017
ms.assetid: 33396e0a-1fae-4616-b822-923584eebfd1
ms.openlocfilehash: 746f98b54285f95bb63e15136508909327c0d140
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55264603"
---
# <a name="endpointextensions"></a>\<endpointExtensions>
Esta seção registra um novo ponto de extremidade padrão na seção de extensões em um computador ou arquivo de configuração do aplicativo. Você pode adicionar um ponto de extremidade padrão para esta coleção usando o `add` palavra-chave e a configuração o `type` atributo do elemento para o tipo de ponto de extremidade, bem como o `name` de atributo para o nome do ponto de extremidade padrão.  
  
 O exemplo a seguir usa o `add` elemento, bem como o `name` atributo a ser adicionado a um ponto de extremidade padrão para o `<endpointExtensions>` seção do arquivo de configuração.  
  
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
  
 Depois que o ponto de extremidade padrão tiver sido registrado, você pode usá-lo conforme mostrado no exemplo a seguir. No [ \<ponto de extremidade >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) elemento, o `kind` atributo especifica o tipo de ponto de extremidade padrão que foi registrado no `<endpointExtensions>` seção. O `endpointConfiguration` atributo será idêntico de `name` atributo do elemento de configuração do ponto de extremidade padrão no `<standardEndpoints>` seção.  
  
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
  
