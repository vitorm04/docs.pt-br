---
title: '&lt;adicionar&gt; &lt;escopos&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c720d99a5abee00eeb52f91586503e0a8a89027b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltaddgt-of-ltscopesgt"></a>&lt;adicionar&gt; &lt;escopos&gt;
Adiciona um Uri que pode ser usado para filtrar pontos de extremidade de serviço durante consulta de escopo personalizado.  
  
\<sistema. ServiceModel >  
\<comportamentos >  
\<endpointBehaviors >  
\<comportamento >  
\<endpointDiscovery >  
\<escopos >  
\<add>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enable="Boolean">
        <scopes>
          <add scope="URI"/>
        </scopes>
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
|escopo|Um URI que contém informações de escopo para o ponto de extremidade que pode ser usada em critérios de correspondência para localizar serviços.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<escopos >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|Contém uma coleção de elementos de configuração que especificam Uris que podem ser usados para filtrar pontos de extremidade de serviço durante consulta de escopo personalizado.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
