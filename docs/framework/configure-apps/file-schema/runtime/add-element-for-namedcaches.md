---
title: Elemento <add> para <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: 076d940e0c15cf48013480fef68b8fac42cf76e9
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252886"
---
# <a name="add-element-for-namedcaches"></a>\<Adicionar > elemento para \<namedCaches >
Adiciona uma `namedCache` entrada `namedCaches` à coleção para um cache de memória.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<sistema. Runtime. Caching >** ](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> memoryCache**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> namedCaches**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Adicionar >**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<namedCaches>  
    <add name="Default" />  
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
|`CacheMemoryLimitMegabytes`|Um valor inteiro que especifica o tamanho máximo permitido (em megabytes) para o qual uma instância <xref:System.Runtime.Caching.MemoryCache> de um pode crescer. O valor padrão é 0, o que significa que <xref:System.Runtime.Caching.MemoryCache> a heurística de dimensionamento automático da classe é usada por padrão.|  
|`Name`|O nome do cache.|  
|`PhysicalMemoryLimitPercentage`|Um valor inteiro entre 0 e 100 que especifica a porcentagem máxima de memória do computador fisicamente instalada que pode ser consumida pelo cache. O valor padrão é 0, o que significa que <xref:System.Runtime.Caching.MemoryCache> a heurística de dimensionamento automático da classe é usada por padrão.|  
|`PollingInterval`|Um valor que indica o intervalo de tempo após o qual a implementação de cache compara a carga de memória atual com os limites de memória absolutos e baseados em percentual que são definidos para a instância de cache. Esse valor é inserido no formato "HH: MM: SS".|  
  
### <a name="child-elements"></a>Elementos filho  
 `None`  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|Contém uma coleção de definições de configuração para as <xref:System.Runtime.Caching.MemoryCache> instâncias nomeadas.|  
  
## <a name="remarks"></a>Comentários  
 O `add` elemento adiciona uma entrada `namedCaches` à coleção para um cache de memória. Você pode usar o elemento [Clear](clear-element-for-namedcaches.md) antes de usar o `add` elemento para ter certeza de que não há outros caches nomeados na coleção. Esse elemento pode ser usado no arquivo Machine. config e no arquivo Web. config.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como definir configurações para a entrada `namedCache` padrão para a `namedCaches` coleção de um cache de memória.  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="Default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também

- [\<Elemento de > namedCaches (configurações de cache)](namedcaches-element-cache-settings.md)
