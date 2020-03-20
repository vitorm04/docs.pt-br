---
title: Elemento <memoryCache> (Configurações de cache)
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
ms.openlocfilehash: 94c21e0408b7616bf0c8a24267b72bfa7cc3aaa0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153978"
---
# <a name="memorycache-element-cache-settings"></a>\<memóriaElemento> cache (configurações de cache)
Define um elemento usado para configurar um cache baseado na classe <xref:System.Runtime.Caching.MemoryCache>. A <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> classe define um elemento [memoryCache](memorycache-element-cache-settings.md) que você pode usar para configurar o cache. Várias instâncias da <xref:System.Runtime.Caching.MemoryCache> classe podem ser usadas em um único aplicativo. Cada `memoryCache` elemento no arquivo de configuração <xref:System.Runtime.Caching.MemoryCache> pode conter configurações para uma instância nomeada.  
  
[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.cache>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<memória>de cache**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<memoryCache>
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>
</memoryCache>  
```  
  
## <a name="type"></a>Type  
 <xref:System.Runtime.Caching.MemoryCache>Classe.  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|O tamanho máximo da memória, em megabytes, que uma instância de um <xref:System.Runtime.Caching.MemoryCache> objeto pode crescer. O valor padrão é 0, <xref:System.Runtime.Caching.MemoryCache> o que significa que a heurística de autotamanho da classe é usada por padrão.|  
|`Name`|O nome da configuração de cache.|  
|`PhysicalMemoryLimitPercentage`|A porcentagem de memória física que pode ser usada pelo cache. O valor padrão é 0, <xref:System.Runtime.Caching.MemoryCache> o que significa que a heurística de autotamanho da classe é usada por padrão.|  
|`PollingInterval`|Um valor que indica o intervalo de tempo após o qual a implementação do cache compara a carga de memória atual com os limites de memória absolutos e baseados em porcentagem definidos para a instância do cache. O valor é inserido no formato "HH:MM:SS".|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<chamadoCaches>](namedcaches-element-cache-settings.md)|Contém um conjunto de definições de configuração para a instância `namedCache`.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<>de configuração](../configuration-element.md)|Especifica o elemento raiz em cada arquivo de configuração que é usado pelos aplicativos common language runtime e .NET Framework.|  
|[\<system.runtime.cache>](system-runtime-caching-element-cache-settings.md)|Contém tipos que permitem implementar o cache de saída em aplicativos incorporados ao Quadro .NET.|  
  
## <a name="remarks"></a>Comentários  
 A <xref:System.Runtime.Caching.MemoryCache> aula é uma implementação concreta da classe abstrata. <xref:System.Runtime.Caching.ObjectCache> As instâncias da <xref:System.Runtime.Caching.MemoryCache> classe podem ser fornecidas com informações de configuração de arquivos de configuração de aplicativos. A seção de `namedCaches` configuração [memoryCache](memorycache-element-cache-settings.md) contém uma coleção de configurações.  
  
 Quando um objeto de cache baseado em memória é `namedCaches` inicializado, ele primeiro tenta encontrar uma entrada que corresponda ao nome no parâmetro que é passado para o construtor de cache de memória. Se `namedCaches` uma entrada for encontrada, as informações de pesquisa e gerenciamento de memória serão recuperadas do arquivo de configuração.  
  
 O processo de inicialização determina então se quaisquer entradas de configuração foram substituídas, usando a coleção opcional de pares de informações de configuração de nome/valor no construtor. Se você passar qualquer um dos seguintes valores na coleção de name/value pair, esses valores anulam as informações obtidas no arquivo de configuração:  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
- <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como <xref:System.Runtime.Caching.MemoryCache> definir o nome do objeto `name` para o nome do objeto de cache padrão definindo o atributo como "Padrão".  
  
 O `cacheMemoryLimitMegabytes` atributo `physicalMemoryLimitPercentage` e o atributo são definidos como zero. Definir esses atributos como <xref:System.Runtime.Caching.MemoryCache> zero significa que a heurística autosizante é usada por padrão. A implementação do cache deve comparar a carga de memória atual com os limites de memória absolutos e baseados em porcentagem a cada dois minutos.  
  
```xml  
<configuration>  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="Default"
               cacheMemoryLimitMegabytes="0"
               physicalMemoryLimitPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
</configuration>  
```  
  
## <a name="see-also"></a>Confira também

- <xref:System.Runtime.Caching.MemoryCache>
- [\<system.runtime.cacheching> Element (Configurações de cache)](system-runtime-caching-element-cache-settings.md)
- [\<chamadoCaches> Element (Configurações de cache)](namedcaches-element-cache-settings.md)
