---
title: <discoveryClientSettings>
ms.date: 03/30/2017
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
ms.openlocfilehash: 2783796166d56be3d4983ab09a60d62491699fe3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925859"
---
# <a name="discoveryclientsettings"></a>\<discoveryClientSettings>
Contém as configurações necessárias para um aplicativo participar do processo de descoberta de serviço como um cliente.  
  
\<system.ServiceModel>  
\<standardEndpoints>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan"
                        maxResults="Integer"
                        scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String"
                   namespace="String" />
            <contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI"/>
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|discoveryEndpoint|Uma cadeia de caracteres que contém o nome do ponto de extremidade de descoberta que permite que um aplicativo cliente pesquise automaticamente um serviço detectável e encontre seu endereço em tempo de execução.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|Um elemento de configuração que fornece um conjunto de critérios usados por um aplicativo cliente para pesquisar um serviço de descoberta. Os critérios podem ser agrupados em critérios de pesquisa (especificando quais serviços você está procurando) e localizar os critérios de encerramento (por quanto tempo a pesquisa deve durar).|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|Define um ponto de extremidade padrão que contém informações para permitir que um aplicativo funcione como um programa cliente que pode encontrar o endereço do ponto de extremidade dinamicamente no tempo de execução.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>
