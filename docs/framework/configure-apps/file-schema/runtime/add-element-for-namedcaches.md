---
title: Elemento <add> para <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: c1345022b79df371ad9c89a39a0a8b625e26608c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154499"
---
# <a name="add-element-for-namedcaches"></a>\<adicionar> \<Element para> chamados Caches
Adiciona `namedCache` uma entrada `namedCaches` à coleção para um cache de memória.  
  
[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.cache>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memória>de cache**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<chamadoCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<adicionar>**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<namedCaches>  
    <add name="Default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a>Type  
 `None`  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|-|-|  
|`CacheMemoryLimitMegabytes`|Um valor inteiro que especifica o tamanho máximo permitido (em megabytes) que uma instância de um <xref:System.Runtime.Caching.MemoryCache> pode crescer. O valor padrão é 0, <xref:System.Runtime.Caching.MemoryCache> o que significa que a heurística autosizante da classe é usada por padrão.|  
|`Name`|O nome do cache.|  
|`PhysicalMemoryLimitPercentage`|Um valor inteiro entre 0 e 100 que especifica a porcentagem máxima de memória do computador fisicamente instalada que pode ser consumida pelo cache. O valor padrão é 0, <xref:System.Runtime.Caching.MemoryCache> o que significa que a heurística autosizante da classe é usada por padrão.|  
|`PollingInterval`|Um valor que indica o intervalo de tempo após o qual a implementação do cache compara a carga de memória atual com os limites de memória absolutos e baseados em porcentagem definidos para a instância do cache. Esse valor é inserido no formato "HH:MM:SS".|  
  
### <a name="child-elements"></a>Elementos filho  
 `None`  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<chamadoCaches>](namedcaches-element-cache-settings.md)|Contém uma coleção de configurações <xref:System.Runtime.Caching.MemoryCache> para as instâncias nomeadas.|  
  
## <a name="remarks"></a>Comentários  
 O `add` elemento adiciona uma `namedCaches` entrada à coleção para um cache de memória. Você pode [clear](clear-element-for-namedcaches.md) usar o elemento `add` claro antes de usar o elemento para ter certeza de que não há outros caches nomeados na coleção. Este elemento pode ser usado no arquivo machine.config e no arquivo Web.config.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como `namedCache` definir as `namedCaches` configurações para a entrada padrão na coleção para um cache de memória.  
  
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
  
## <a name="see-also"></a>Confira também

- [\<chamadoCaches> Element (Configurações de cache)](namedcaches-element-cache-settings.md)
