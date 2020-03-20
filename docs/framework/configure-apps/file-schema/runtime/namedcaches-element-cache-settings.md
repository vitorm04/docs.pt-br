---
title: Elemento <namedCaches> (Configurações de cache)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: e0640ca18d386141f3c03135019eb4fe959b5bf8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153952"
---
# <a name="namedcaches-element-cache-settings"></a>\<chamadoCaches> Element (Configurações de cache)
Especifica uma coleção de configurações <xref:System.Runtime.Caching.MemoryCache> para as instâncias nomeadas. A <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> propriedade faz referência à coleção de `namedCaches` configurações de um ou mais elementos do arquivo de configuração.  
  
[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.cache>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memória>de cache**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<chamadoCaches>**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<namedCaches>  
  <add name="default"/>
</namedCaches>  
```  
  
## <a name="type"></a>Type  
 `None`  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|Um valor inteiro que especifica o tamanho máximo permitido, em megabytes, que uma instância de um <xref:System.Runtime.Caching.MemoryCache> pode crescer. O valor padrão é 0, o que significa que <xref:System.Runtime.Caching.MemoryCache> a heurística autosizante da classe é usada por padrão.|  
|`name`|O nome do cache.|  
|`physicalMemoryLimitPercentage`|Um valor inteiro entre 0 e 100 que especifica a porcentagem máxima de memória do computador fisicamente instalada que pode ser consumida pelo cache. O valor padrão é 0, o que significa que <xref:System.Runtime.Caching.MemoryCache> a heurística autosizante da classe é usada por padrão.|  
|`pollingInterval`|Um valor que indica o intervalo de tempo após o qual a implementação do cache compara a carga de memória atual com os limites de memória absolutos e baseados em porcentagem definidos para a instância do cache. Esse valor é inserido no formato "HH:MM:SS".|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<adicionar>](add-element-for-namedcaches.md)|Adiciona um cache nomeado à coleção de `namedCaches` para um cache de memória.|  
|[\<claro>](clear-element-for-namedcaches.md)|Limpa a coleção `namedCaches` de um cache de memória.|  
|[\<remover>](remove-element-for-namedcaches.md)|Remove uma entrada de cache nomeado da coleção de `namedCaches` para um cache de memória.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<>de configuração](../configuration-element.md)|Especifica o elemento raiz em cada arquivo de configuração que é usado pelos aplicativos common language runtime e .NET Framework.|  
|[\<memória>de cache](memorycache-element-cache-settings.md)|Define um elemento usado para configurar um cache baseado na classe <xref:System.Runtime.Caching.MemoryCache>.|  
|[\<system.runtime.cache>](system-runtime-caching-element-cache-settings.md)|Contém tipos que permitem implementar o cache de saída em aplicativos incorporados ao Quadro .NET.|  
  
## <a name="remarks"></a>Comentários  
 A seção de configuração de cache `add`de `remove`memória `clear` do arquivo `namedCaches` Web.config pode conter , e atributos para a coleção. Cada `namedCaches` entrada é identificada `name` exclusivamente pelo atributo.  
  
 Você pode recuperar instâncias de entradas de cache de memória fazendo referência às informações nos arquivos de configuração do aplicativo. Por padrão, apenas a instância de cache padrão tem uma entrada no arquivo de configuração. A instância de cache padrão é a <xref:System.Runtime.Caching.MemoryCache.Default%2A> instância que é devolvida da propriedade.  
  
 Se você definir o atributo nome como "padrão", o elemento usará a instância de cache de memória padrão.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como definir o nome do cache `name` para o nome de entrada de cache padrão, definindo o atributo como "padrão".  
  
 O `cacheMemoryLimitMegabytes` atributo `physicalMemoryPercentage` e o atributo são definidos como zero. Definir esses atributos como zero significa que a <xref:System.Runtime.Caching.MemoryCache> heurística autosizante da classe é usada. A implementação do cache compara a carga de memória atual com os limites de memória absolutos e baseados em porcentagem a cada dois minutos.  
  
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
  
## <a name="see-also"></a>Confira também

- [\<memóriaElemento> cache (configurações de cache)](memorycache-element-cache-settings.md)
