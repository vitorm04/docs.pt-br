---
title: <filterTable>
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: ba65d3858cdbdf6b49c50e60f4e3cc9624fef136
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254399"
---
# <a name="filtertable"></a>\<filterTable>
Representa uma tabela de roteamento que contém uma lista de filtros para avaliar mensagens e o ponto de extremidade do cliente para rotear mensagens para se o filtro é avaliada como true.  
  
 \<system.serviceModel>  
\<routing>  
\<routingTables>  
\<table>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<routing>
  <filterTables>
    <filterTable name="String">
      <entries>
        <add backupList="String"
             endpointName="String"
             filterName="String"
             priority="Integer" />
      </entries>
    </filterTable>
  </filterTables>
</routing>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|name|Uma cadeia de caracteres que contém o nome exclusivo deste elemento de configuração.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<filters>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|Mapeamentos entre os filtros de roteamento e os pontos de extremidade para enviar mensagens para quando o filtro corresponde ao destino.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<routing>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Uma seção de configuração que contém tabelas de roteamento.|  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
