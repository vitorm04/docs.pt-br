---
title: <scopes>
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: 57e9e19025db5e1fa588f073fdf30de09837a25d
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399925"
---
# <a name="scopes"></a>\<escopos >
Contém uma coleção de elementos de configuração que especificam URIs de escopo personalizado que podem ser usados para filtrar pontos de extremidade de serviço durante a consulta.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> endpointBehaviors**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> endpointDiscovery**](endpointdiscovery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<escopos >**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enable="Boolean">
        <scopes>
          <add scope="URI" />
        </scopes>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|[\<add>](add-of-scopes.md)|Adiciona as informações de escopo para o ponto de extremidade que pode ser usado em critérios de correspondência para localizar serviços.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<endpointDiscovery>](endpointdiscovery.md)|Especifica as várias configurações de descoberta para um ponto de extremidade, como sua descoberta, escopos e quaisquer extensões personalizadas para seus metadados.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
