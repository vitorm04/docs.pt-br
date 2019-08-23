---
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: f9d7e3a4957d2a8f30724f0bfc04e58a57fc5f7d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919265"
---
# <a name="discoveryclient"></a>\<discoveryClient>
Um elemento de configuração para criar uma associação personalizada que permite que um aplicativo cliente pesquise automaticamente um serviço detectável e encontre seu endereço em tempo de execução.  
  
\<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<> de associação  
\<discoveryClient>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<discoveryClient discoveryEndpoint="String">
  <findCriteria duration="TimeSpan"
                maxResults="Integer"
                scopeMatchBy="Uri">
    <contractTypeNames>
      <add name="String"
           namespace="String" />
    </contractTypeNames>
    <extensions />
    <scopes>
      <add scope="URI"/>
    </scopes>
  </findCriteria>
</discoveryClient>
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
|[\<binding>](../../../misc/binding.md)|Define todos os recursos de associação da associação personalizada.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
