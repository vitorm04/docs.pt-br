---
title: '&lt;endpointExtensions&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33396e0a-1fae-4616-b822-923584eebfd1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 47aad13591e3a35433cafea3e49fff7fa6e7b7c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltendpointextensionsgt"></a>&lt;endpointExtensions&gt;
Esta seção registra um novo ponto de extremidade padrão na seção de extensões em um computador ou arquivo de configuração do aplicativo. Você pode adicionar um ponto de extremidade padrão para esta coleção usando o `add` palavra-chave e a configuração de `type` atributo do elemento para o tipo de ponto de extremidade, bem como a `name` de atributo para o nome do ponto de extremidade padrão.  
  
 O exemplo a seguir usa o `add` elemento, bem como o `name` atributo para adicionar um ponto de extremidade padrão para o `<endpointExtensions>` seção do arquivo de configuração.  
  
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
        <standardEndpoint  
                  name="udpConfig"  
                  multicastAddress="soap.udp://239.255.255.250:3703"  
                  ... />  
      </udpDiscoveryEndpoint>  
    </standardEndpoints>  
  </system.serviceModel>  
```
