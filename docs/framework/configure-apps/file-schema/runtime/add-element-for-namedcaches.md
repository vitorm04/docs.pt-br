---
title: '&lt;Adicionar&gt; elemento para &lt;namedCaches&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d65dfd9a1560f2657f48b327277b64ab77014b47
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-element-for-ltnamedcachesgt"></a>&lt;Adicionar&gt; elemento para &lt;namedCaches&gt;
Adiciona um `namedCache` entrada para o `namedCaches` coleção para um cache de memória.  
  
 \<system.runtime.caching>  
\<memoryCache>  
\<namedCaches >  
\<add>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<namedCaches>  
    <add name="default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a>Tipo  
 `None`  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|-|-|  
|`CacheMemoryLimitMegabytes`|Um valor inteiro que especifica o tamanho máximo (em megabytes) que uma instância de um <xref:System.Runtime.Caching.MemoryCache> pode atingir. O valor padrão é 0, o que significa que o <xref:System.Runtime.Caching.MemoryCache> heurística de dimensionamento automático da classe é usadas por padrão.|  
|`Name`|O nome do cache.|  
|`PhysicalMemoryLimitPercentage`|Um valor inteiro entre 0 e 100 que especifica a porcentagem máxima de memória instalada fisicamente do computador que pode ser consumida pelo cache. O valor padrão é 0, o que significa que o <xref:System.Runtime.Caching.MemoryCache> heurística de dimensionamento automático da classe é usadas por padrão.|  
|`PollingInterval`|Um valor que indica o intervalo de tempo após o qual a implementação de cache compara a carga de memória atual em relação as limites de memória absoluto e baseadas em porcentagens que são definidas para a instância de cache. Esse valor é inserido no formato "Hh".|  
  
### <a name="child-elements"></a>Elementos filho  
 `None`  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<namedCaches>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|Contém uma coleção de definições de configuração para nomeado <xref:System.Runtime.Caching.MemoryCache> instâncias.|  
  
## <a name="remarks"></a>Comentários  
 O `add` elemento adiciona uma entrada para o `namedCaches` coleção para um cache de memória. Você pode usar o [limpar](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md) elemento antes de usar o `add` elemento certificar-se de que não haja nenhum outro denominado caches na coleção. Esse elemento pode ser usado no arquivo Machine. config e no arquivo Web. config.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como definir as configurações para o padrão `namedCache` entrada para o `namedCaches` coleção para um cache de memória.  
  
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
 [\<namedCaches > elemento (configurações de Cache)](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
