---
title: '&lt;endpointDiscovery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7a997ddffa2267cdeb9e54bb98d4122db254104d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltendpointdiscoverygt"></a>&lt;endpointDiscovery&gt;
Especifica as várias configurações de descoberta para um ponto de extremidade, como sua capacidade de descoberta, escopos e quaisquer extensões personalizadas para seus metadados.  
  
\<sistema. ServiceModel >  
\<comportamentos >  
\<endpointBehaviors >  
\<comportamento >  
\<endpointDiscovery >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enabled="Boolean">
        <scopes>
          <add scope="URI"/>
        </scopes>
        <extensions />
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|Habilitado|Um valor booliano que especifica se a descoberta está habilitada neste ponto de extremidade. O padrão é `false`.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<escopos >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|Uma coleção de URIs de escopo para o ponto de extremidade. Uris de mais de um escopo pode ser associado um ponto de extremidade.|  
|[\<Extensões >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) [de \<endpointDiscovery >]|Uma coleção de elementos XML que permite que você especifique metadados personalizados a serem publicados para um ponto de extremidade.|  
|\<tipos >|Uma coleção de interfaces para pesquisar.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<comportamento >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Especifica um elemento de comportamento.|  
|||  
  
## <a name="remarks"></a>Comentários  
 Quando adicionado à configuração de comportamento do ponto de extremidade e com o `enabled` atributo definido como `true`, este elemento de configuração permite que a sua capacidade de descoberta. Além disso, você pode usar o [ \<escopos >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)elemento filho à especificação de escopo personalizado Uris que podem ser usados para filtrar pontos de extremidade de serviço durante a consulta, bem como o [ \<extensões >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) elemento filho para especificar metadados personalizados que devem ser publicados junto com os metadados detectável padrão (EPR, ContractTypeName, BindingName, escopo e ListenURI).  
  
 Este elemento de configuração é dependente de [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) elemento que fornece o controle de nível de serviço de descoberta. Isso significa que as configurações do elemento são ignoradas se [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) não está presente na configuração.  
  
## <a name="example"></a>Exemplo  
 O exemplo de configuração a seguir especifica os escopos de filtragem e metadados de extensão a ser publicado para um ponto de extremidade.  
  
```xml  
<services>  
  <service name="CalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
     <endpoint binding="basicHttpBinding"  
              address="calculator"  
              contract="ICalculatorService"  
              behaviorConfiguration="calculatorEndpointBehavior" />  
  </service>  
</services>  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceDiscovery />  
    </behavior>  
  </serviceBehaviors>  
  <endpointBehaviors>  
    <behavior name="calculatorEndpointBehavior">  
      <endpointDiscovery enabled="true">  
        <scopes>  
          <add scope="http://contoso/test1"/>  
          <add scope="http://contoso/test2"/>  
        </scopes>  
        <extensions>  
          <e:Publisher xmlns:e="http://example.org">  
            <e:Name>The Example Organization</e:Name>  
            <e:Address>One Example Way, ExampleTown, EX 12345</e:Address>  
            <e:Contact>support@example.org</e:Contact>  
          </e:Publisher>  
          <AnotherCustomMetadata>Custom Metadata</AnotherCustomMetadata>  
        </extensions>  
      </endpointDiscovery>  
    </behavior>  
  </endpointBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
