---
title: '&lt;contractTypeNames&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ec5efc6-87f8-4160-9be0-dcd2e01df3df
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 95be974404fdd845ee3a24bb194e9ba5e890147d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcontracttypenamesgt"></a>&lt;contractTypeNames&gt;
Uma seção de configuração que especifica uma lista de nomes de tipo de contrato, que são os nomes de contrato de serviços que está sendo pesquisados, e os critérios usados normalmente durante a pesquisa de um serviço. Se mais de um nome de contrato for especificado, somente pontos de extremidade correspondente a todos os contratos responderá. Observe que em [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)], um ponto de extremidade só pode oferecer suporte a um contrato.  
  
 \<sistema. ServiceModel >  
\<standardEndpoints >  
  
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
              <add name="String" namespace="String" />
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
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|Um nome de tipo de contrato é uma propriedade que faz referência ao conjunto de critérios usados normalmente durante a pesquisa de um serviço.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<findCriteria >](../../../../../docs/framework/configure-apps/file-schema/wcf/findcriteria.md)|Um elemento de configuração que fornece um conjunto de critérios usados por um aplicativo cliente para pesquisar para um serviço de descoberta. Critérios podem ser agrupados em critérios de pesquisa (especificando quais serviços você está procurando) e localizar os critérios de encerramento (quanto tempo a pesquisa deve durar).|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>  
 <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElementCollection>
