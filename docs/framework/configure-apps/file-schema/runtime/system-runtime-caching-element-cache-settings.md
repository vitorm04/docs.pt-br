---
title: '&lt;System.Runtime.Caching&gt; elemento (configurações de Cache)'
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 659a168f6c0bcb459bcfbdb247a9959c61c9c996
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltsystemruntimecachinggt-element-cache-settings"></a>&lt;System.Runtime.Caching&gt; elemento (configurações de Cache)
Fornece configuração para a padrão de memória <xref:System.Runtime.Caching.ObjectCache> implementação por meio de `memoryCache` entrada no arquivo de configuração.  
  
 \<configuration>  
\<system.runtime.caching>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 `None`  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<memoryCache>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|Define um elemento usado para configurar um cache baseado na classe <xref:System.Runtime.Caching.MemoryCache>.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<configuration>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Especifica o elemento raiz em todos os arquivos de configuração que é usado pelo common language runtime e [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] aplicativos.|  
  
## <a name="remarks"></a>Comentários  
 As classes nesse namespace fornecem uma maneira de usar recursos de cache como aqueles no ASP.NET, mas sem uma dependência no `System.Web` assembly. Para obter mais informações, consulte [cache em aplicativos do .NET Framework](../../../../../docs/framework/performance/caching-in-net-framework-applications.md).  
  
> [!NOTE]
>  A saída de cache de funcionalidade e tipos no <xref:System.Runtime.Caching> namespace são novos no [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como configurar um cache que se baseia o <xref:System.Runtime.Caching.MemoryCache> classe. O exemplo mostra como configurar uma instância de `namedCaches` entrada de cache de memória. O nome do cache é definido para o nome de entrada de cache padrão definindo o `name` atributo como "padrão".  
  
 O `cacheMemoryLimitMegabytes` atributo e o `physicalMemoryPercentage` atributo são definidos como zero. Definir esses atributos como zero significa que o <xref:System.Runtime.Caching.MemoryCache> dimensionando heurística é usadas por padrão. A implementação de cache deve comparar a carga de memória atual em relação as limites de memória absoluto e baseadas em porcentagens cada dois minutos.  
  
```xml  
<configuration>  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 [\<memoryCache > elemento (configurações de Cache)](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)
