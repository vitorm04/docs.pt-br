---
title: '&lt;namedCaches&gt; elemento (configurações de Cache)'
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: fac50aedbb11eba40482fab71c912f587d85f855
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltnamedcachesgt-element-cache-settings"></a>&lt;namedCaches&gt; elemento (configurações de Cache)
Especifica uma coleção de definições de configuração para nomeado <xref:System.Runtime.Caching.MemoryCache> instâncias. O <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> propriedade faz referência a coleção de definições de configuração de um ou mais `namedCaches` elementos do arquivo de configuração.  
  
 \<configuration>  
\< System.Runtime.Caching >  
\<memoryCache>  
\<namedCaches >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<namedCaches>  
  <add name="default"/>   
</namedCaches>  
```  
  
## <a name="type"></a>Tipo  
 `None`  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|Um valor inteiro que especifica o tamanho máximo permitido, em megabytes, que uma instância de um <xref:System.Runtime.Caching.MemoryCache> pode atingir. O valor padrão é 0, o que significa que a heurística de dimensionamento automático do <xref:System.Runtime.Caching.MemoryCache> classe são usadas por padrão.|  
|`name`|O nome do cache.|  
|`physicalMemoryLimitPercentage`|Um valor inteiro entre 0 e 100 que especifica a porcentagem máxima de memória instalada fisicamente do computador que pode ser consumida pelo cache. O valor padrão é 0, o que significa que a heurística de dimensionamento automático do <xref:System.Runtime.Caching.MemoryCache> classe são usadas por padrão.|  
|`pollingInterval`|Um valor que indica o intervalo de tempo após o qual a implementação de cache compara a carga de memória atual em relação as limites de memória absoluto e baseadas em porcentagens que são definidas para a instância de cache. Esse valor é inserido no formato "Hh".|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/runtime/add-element-for-namedcaches.md)|Adiciona um cache nomeado à coleção de `namedCaches` para um cache de memória.|  
|[\<clear>](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)|Limpa a coleção `namedCaches` de um cache de memória.|  
|[\<remove>](../../../../../docs/framework/configure-apps/file-schema/runtime/remove-element-for-namedcaches.md)|Remove uma entrada de cache nomeado da coleção de `namedCaches` para um cache de memória.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<memoryCache>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|Define um elemento usado para configurar um cache baseado na classe <xref:System.Runtime.Caching.MemoryCache>.|  
  
## <a name="remarks"></a>Comentários  
 A seção de configuração do cache de memória do arquivo Web. config pode conter `add`, `remove`, e `clear` atributos para o `namedCaches` coleção. Cada `namedCaches` entrada é identificada exclusivamente pelo `name` atributo.  
  
 Você pode recuperar instâncias de entradas de cache de memória consultando as informações nos arquivos de configuração do aplicativo. Por padrão, a instância de cache padrão tem uma entrada no arquivo de configuração. A instância de cache padrão é a instância que é retornada de <xref:System.Runtime.Caching.MemoryCache.Default%2A> propriedade.  
  
 Se você definir o atributo de nome "padrão", o elemento usa a instância padrão do cache de memória.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como definir o nome do cache para o nome de entrada de cache padrão definindo o `name` atributo como "padrão".  
  
 O `cacheMemoryLimitMegabytes` atributo e o `physicalMemoryPercentage` atributo são definidos como zero. Definir esses atributos como zero significa que a heurística de dimensionamento automático do <xref:System.Runtime.Caching.MemoryCache> classe são usados. A implementação de cache compara a carga de memória atual em relação as limites de memória absoluto e baseadas em porcentagens cada dois minutos.  
  
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
 [\<memoryCache > elemento (configurações de Cache)](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)
