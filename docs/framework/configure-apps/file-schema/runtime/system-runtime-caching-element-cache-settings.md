---
title: Elemento <system.runtime.caching> (Configurações de cache)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
ms.openlocfilehash: df4887c8801dcf8af06b3826673a03cbc7dbc9b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153848"
---
# <a name="systemruntimecaching-element-cache-settings"></a>\<system.runtime.cacheching> Element (Configurações de cache)

Fornece configuração para a <xref:System.Runtime.Caching.ObjectCache> implementação `memoryCache` in-memory padrão através da entrada no arquivo de configuração.  
  
[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.runtime.cache>**  
  
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
|[\<memória>de cache](memorycache-element-cache-settings.md)|Define um elemento usado para configurar um cache baseado na classe <xref:System.Runtime.Caching.MemoryCache>.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<>de configuração](../configuration-element.md)|Especifica o elemento raiz em cada arquivo de configuração que é usado pelos aplicativos common language runtime e .NET Framework.|  
  
## <a name="remarks"></a>Comentários

As aulas neste namespace fornecem uma maneira de usar instalações de cache `System.Web` como as de ASP.NET, mas sem dependência da montagem. Para obter mais informações, consulte [Cache em .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md).  
  
> [!NOTE]
> A funcionalidade de cache de <xref:System.Runtime.Caching> saída e os tipos no namespace são novos no .NET Framework 4.  
  
## <a name="example"></a>Exemplo

O exemplo a seguir mostra como configurar um <xref:System.Runtime.Caching.MemoryCache> cache baseado na classe. O exemplo mostra como configurar uma `namedCaches` instância da entrada para cache de memória. O nome do cache é definido como nome `name` de entrada de cache padrão definindo o atributo como "Padrão".  
  
O `cacheMemoryLimitMegabytes` atributo `physicalMemoryPercentage` e o atributo são definidos como zero. Definir esses atributos como <xref:System.Runtime.Caching.MemoryCache> zero significa que a heurística autosizante é usada por padrão. A implementação do cache deve comparar a carga de memória atual com os limites de memória absolutos e baseados em porcentagem a cada dois minutos.  
  
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

- [\<memóriaElemento> cache (configurações de cache)](memorycache-element-cache-settings.md)
