---
title: '&lt;Entradas&gt;'
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: b9cc7f7736ffefaca68a0f197bd064a99c4dca9a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746703"
---
# <a name="ltentriesgt"></a>&lt;Entradas&gt;
Uma entrada de roteamento que contêm mapeamentos entre os filtros de roteamento e os pontos de extremidade de destino para enviar mensagens para quando o filtro corresponde.  
  
 \<system.serviceModel>  
\<roteamento >  
\<routingTables >  
\<Tabela >  
\<entradas >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<Filtros >](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|Mapeia um filtro para um ponto de extremidade do cliente que foi definido anteriormente. As mensagens que correspondem a este filtro serão enviadas para este destino.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<roteamento >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Uma seção de configuração que contém uma tabela de roteamento.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>    
