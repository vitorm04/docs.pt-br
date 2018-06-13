---
title: '&lt;filterTable&gt;'
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: 7bdc76ba7a8e2927b93fa0207f48cc569279482f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747405"
---
# <a name="ltfiltertablegt"></a>&lt;filterTable&gt;
Representa uma tabela de roteamento que contém uma lista de filtros para avaliar mensagens e o ponto de extremidade do cliente para rotear mensagens para se o filtro é avaliado como true.  
  
 \<system.serviceModel>  
\<roteamento >  
\<routingTables >  
\<Tabela >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
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
|[\<Filtros >](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|Mapeamentos entre os filtros de roteamento e os pontos de extremidade de destino para enviar mensagens para quando o filtro corresponde.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<roteamento >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Uma seção de configuração que contém tabelas de roteamento.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>    
