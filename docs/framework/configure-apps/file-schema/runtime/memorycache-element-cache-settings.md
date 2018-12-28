---
title: '&lt;memoryCache&gt; (configurações de Cache)'
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
author: mcleblanc
ms.author: markl
ms.openlocfilehash: ed815f66e0c542cf20b0a8127f75d10219aea92b
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611601"
---
# <a name="ltmemorycachegt-element-cache-settings"></a>&lt;memoryCache&gt; (configurações de Cache)
Define um elemento usado para configurar um cache baseado na classe <xref:System.Runtime.Caching.MemoryCache>. O <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> classe define um [memoryCache](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md) elemento que você pode usar para configurar o cache. Várias instâncias do <xref:System.Runtime.Caching.MemoryCache> classe pode ser usada em um único aplicativo. Cada `memoryCache` elemento no arquivo de configuração pode conter configurações para uma nomeada <xref:System.Runtime.Caching.MemoryCache> instância.  
  
 \<configuration>  
\<system.runtime.caching>  
\<memoryCache>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<memoryCache>   
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>   
</memoryCache>  
```  
  
## <a name="type"></a>Tipo  
 <xref:System.Runtime.Caching.MemoryCache> classe.  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|O tamanho máximo de memória, em megabytes, que uma instância de um <xref:System.Runtime.Caching.MemoryCache> objeto pode atingir. O valor padrão é 0, o que significa que o <xref:System.Runtime.Caching.MemoryCache> heurística de autosize da classe é usada por padrão.|  
|`Name`|O nome da configuração do cache.|  
|`PhysicalMemoryLimitPercentage`|A porcentagem de memória física que pode ser usada pelo cache. O valor padrão é 0, o que significa que o <xref:System.Runtime.Caching.MemoryCache> heurística de autosize da classe é usada por padrão.|  
|`PollingInterval`|Um valor que indica o intervalo de tempo após o qual a implementação de cache compara a carga de memória atual com os limites de memória absoluto e baseado em percentual que são definidas para a instância do cache. O valor é inserido no formato "Hh".|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<namedCaches>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|Contém um conjunto de definições de configuração para a instância `namedCache`.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<system.runtime.caching>](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)|Contém tipos que permitem implementar o cache de saída em aplicativos que integram o [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].|  
  
## <a name="remarks"></a>Comentários  
 O <xref:System.Runtime.Caching.MemoryCache> classe é uma implementação concreta do resumo <xref:System.Runtime.Caching.ObjectCache> classe. Instâncias do <xref:System.Runtime.Caching.MemoryCache> classe pode ser fornecido com informações de configuração de arquivos de configuração do aplicativo. O [memoryCache](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md) seção de configuração contém um `namedCaches` coleção de configuração.  
  
 Quando um objeto de cache baseadas em memória é inicializado, ele primeiro tenta encontrar um `namedCaches` entrada que corresponde ao nome no parâmetro que é passado para o construtor de cache de memória. Se um `namedCaches` entrada for encontrada, a sondagem e informações de gerenciamento de memória são recuperados do arquivo de configuração.  
  
 O processo de inicialização, em seguida, determina se todas as entradas de configuração foram substituídas usando a coleção opcional de pares nome/valor das informações de configuração no construtor. Se você passar qualquer um dos seguintes valores na coleção de par nome/valor, esses valores substituem as informações obtidas do arquivo de configuração:  
  
-   <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
-   <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
-   <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como definir o nome da <xref:System.Runtime.Caching.MemoryCache> objeto para o nome do objeto de cache padrão definindo a `name` atributo como "default".  
  
 O `cacheMemoryLimitMegabytes` atributo e o `physicalMemoryLimitPercentage` atributo são definidos como zero. Definir esses atributos como zero significa que o <xref:System.Runtime.Caching.MemoryCache> heurística de dimensionamento automático é usada por padrão. A implementação de cache deve comparar a carga de memória atual em relação as limites de memória absoluto e baseado em percentual cada dois minutos.  
  
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
- <xref:System.Runtime.Caching.MemoryCache>  
- [\<System.Runtime.Caching > (configurações de Cache)](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)  
- [\<namedCaches > (configurações de Cache)](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
