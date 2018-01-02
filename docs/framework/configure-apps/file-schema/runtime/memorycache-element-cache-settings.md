---
title: "&lt;memoryCache&gt; elemento (configurações de Cache)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 5862e696f084916f3359d185f42e84b2a2789a0e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltmemorycachegt-element-cache-settings"></a>&lt;memoryCache&gt; elemento (configurações de Cache)
Define um elemento usado para configurar um cache baseado na classe <xref:System.Runtime.Caching.MemoryCache>. O <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> classe define um [memoryCache](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md) elemento que você pode usar para configurar o cache. Várias instâncias de <xref:System.Runtime.Caching.MemoryCache> classe pode ser usada em um único aplicativo. Cada `memoryCache` elemento no arquivo de configuração pode conter configurações para um conjunto nomeado <xref:System.Runtime.Caching.MemoryCache> instância.  
  
 \<configuration>  
\<System.Runtime.Caching >  
\<memoryCache >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<memoryCache   
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>   
< memoryCache />  
```  
  
## <a name="type"></a>Tipo  
 <xref:System.Runtime.Caching.MemoryCache>classe.  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|O tamanho máximo de memória, em megabytes, que uma instância de um <xref:System.Runtime.Caching.MemoryCache> objeto pode atingir. O valor padrão é 0, o que significa que o <xref:System.Runtime.Caching.MemoryCache> heurística de autosize da classe é usadas por padrão.|  
|`Name`|O nome da configuração de cache.|  
|`PhysicalMemoryLimitPercentage`|A porcentagem de memória física que pode ser usada pelo cache. O valor padrão é 0, o que significa que o <xref:System.Runtime.Caching.MemoryCache> heurística de autosize da classe é usadas por padrão.|  
|`PollingInterval`|Um valor que indica o intervalo de tempo após o qual a implementação de cache compara a carga de memória atual em relação as limites de memória absoluto e baseadas em porcentagens que são definidas para a instância de cache. O valor é inserido no formato "Hh".|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<namedCaches>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|Contém um conjunto de definições de configuração para a instância `namedCache`.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<system.runtime.caching>](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)|Contém tipos que permitem implementar o cache de saída em aplicativos que são incorporados a [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].|  
  
## <a name="remarks"></a>Comentários  
 O <xref:System.Runtime.Caching.MemoryCache> classe é uma implementação concreta do resumo <xref:System.Runtime.Caching.ObjectCache> classe. Instâncias de <xref:System.Runtime.Caching.MemoryCache> classe pode ser fornecida com informações de configuração de arquivos de configuração do aplicativo. O [memoryCache](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md) seção de configuração contém um `namedCaches` coleção de configuração.  
  
 Quando um objeto de cache com base em memória é inicializado, ele primeiro tenta encontrar um `namedCaches` entrada que corresponde ao nome no parâmetro que é passado para o construtor de cache de memória. Se um `namedCaches` entrada for encontrada, a sondagem e informações de gerenciamento de memória são recuperados do arquivo de configuração.  
  
 O processo de inicialização, em seguida, determina se as entradas de configuração foram substituídas por meio da coleção opcional de pares de nome/valor das informações de configuração no construtor. Se você passar qualquer um dos seguintes valores no conjunto de pares de nome/valor, esses valores substituem as informações obtidas do arquivo de configuração:  
  
-   <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
-   <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
-   <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como definir o nome do <xref:System.Runtime.Caching.MemoryCache> objeto para o nome do objeto de cache padrão definindo o `name` atributo como "padrão".  
  
 O `cacheMemoryLimitMegabytes` atributo e o `physicalMemoryLimitPercentage` atributo são definidos como zero. Definir esses atributos como zero significa que o <xref:System.Runtime.Caching.MemoryCache> dimensionando heurística é usadas por padrão. A implementação de cache deve comparar a carga de memória atual em relação as limites de memória absoluto e baseadas em porcentagens cada dois minutos.  
  
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
 <xref:System.Runtime.Caching.MemoryCache>  
 [\<System.Runtime.Caching > elemento (configurações de Cache)](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)  
 [\<namedCaches > elemento (configurações de Cache)](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
