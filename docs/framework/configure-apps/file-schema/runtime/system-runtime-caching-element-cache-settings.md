---
title: '&lt;System.Runtime.Caching&gt; (configurações de Cache)'
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c9932d1328f010158535b096e4ead599c7b3f47
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50202127"
---
# <a name="ltsystemruntimecachinggt-element-cache-settings"></a>&lt;System.Runtime.Caching&gt; (configurações de Cache)
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
|[\<configuration>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Especifica o elemento raiz em cada arquivo de configuração que é usado pelo common language runtime e [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] aplicativos.|  
  
## <a name="remarks"></a>Comentários  
 As classes nesse namespace fornecem uma maneira de usar recursos de armazenamento em cache, como aqueles no ASP.NET, mas sem uma dependência no `System.Web` assembly. Para obter mais informações, consulte [cache em aplicativos do .NET Framework](../../../../../docs/framework/performance/caching-in-net-framework-applications.md).  
  
> [!NOTE]
>  A saída de cache de funcionalidade e tipos na <xref:System.Runtime.Caching> namespace são novos no [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como configurar um cache que se baseia o <xref:System.Runtime.Caching.MemoryCache> classe. O exemplo mostra como configurar uma instância da `namedCaches` entrada para o cache de memória. O nome do cache é definido para o nome de entrada de cache padrão definindo a `name` atributo como "default".  
  
 O `cacheMemoryLimitMegabytes` atributo e o `physicalMemoryPercentage` atributo são definidos como zero. Definir esses atributos como zero significa que o <xref:System.Runtime.Caching.MemoryCache> heurística de dimensionamento automático é usada por padrão. A implementação de cache deve comparar a carga de memória atual em relação as limites de memória absoluto e baseado em percentual cada dois minutos.  
  
```xml  
<configuration>  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryLimitPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 [\<memoryCache > (configurações de Cache)](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)
