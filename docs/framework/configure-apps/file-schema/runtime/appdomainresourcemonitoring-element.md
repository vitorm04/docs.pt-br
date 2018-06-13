---
title: '&lt;appDomainResourceMonitoring&gt; elemento'
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 11e892d8ab9001d3670c801b43ba444aa24b2e41
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743570"
---
# <a name="ltappdomainresourcemonitoringgt-element"></a>&lt;appDomainResourceMonitoring&gt; elemento
Instrui o tempo de execução a coletar estatísticas sobre todos os domínios de aplicativos no processo durante toda a vida do processo.  
  
 \<configuration>  
\<runtime>  
\<appDomainResourceMonitoring >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<appDomainResourceMonitoring    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`enabled`|Atributo obrigatório.<br /><br /> Especifica se o tempo de execução de coleta estatísticas de monitoramento de recursos do domínio de aplicativo.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`true`|Estatísticas para monitoramento de recursos do domínio de aplicativo são coletadas.|  
|`false`|Estatísticas para monitoramento de recursos do domínio de aplicativo não são coletadas.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 Monitoramento de recursos do domínio de aplicativo está disponível por meio da classe de domínio de aplicativo gerenciado, a hospedagem [ICLRAppDomainResourceMonitor](../../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface e o rastreamento de eventos para Windows (ETW). Quando o monitoramento é habilitado, as estatísticas são coletadas para todos os domínios de aplicativo no processo durante a vida útil do processo.  
  
 Para habilitar o monitoramento do código gerenciado, use o <xref:System.AppDomain.MonitoringIsEnabled%2A> propriedade.  
  
 Este elemento de configuração está disponível apenas no [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] e posterior.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como habilitar o monitoramento de recursos do domínio de aplicativo.  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
 [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)
