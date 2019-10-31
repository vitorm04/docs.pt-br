---
title: Elemento <system.runtime.caching> (Configurações de cache)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
ms.openlocfilehash: 70573f92f1799a54116bc91f7a39d157a7ae5b36
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115512"
---
# <a name="systemruntimecaching-element-cache-settings"></a>\<o elemento System. Runtime. Caching > (configurações de cache)

Fornece a configuração para a implementação de <xref:System.Runtime.Caching.ObjectCache> na memória padrão por meio da entrada de `memoryCache` no arquivo de configuração.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp; **\<System. Runtime. caching >**  
  
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
|[\<memoryCache>](memorycache-element-cache-settings.md)|Define um elemento usado para configurar um cache baseado na classe <xref:System.Runtime.Caching.MemoryCache>.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|Especifica o elemento raiz em cada arquivo de configuração que é usado pelo Common Language Runtime e .NET Framework aplicativos.|  
  
## <a name="remarks"></a>Comentários

As classes nesse namespace fornecem uma maneira de usar recursos de caching como aqueles em ASP.NET, mas sem uma dependência no assembly `System.Web`. Para obter mais informações, consulte [Caching in .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md).  
  
> [!NOTE]
> A funcionalidade e os tipos de cache de saída no namespace <xref:System.Runtime.Caching> são novos no .NET Framework 4.  
  
## <a name="example"></a>Exemplo

O exemplo a seguir mostra como configurar um cache baseado na classe <xref:System.Runtime.Caching.MemoryCache>. O exemplo mostra como configurar uma instância da entrada de `namedCaches` para o cache de memória. O nome do cache é definido como o nome da entrada de cache padrão, definindo o atributo `name` como "padrão".  
  
O atributo `cacheMemoryLimitMegabytes` e o atributo `physicalMemoryPercentage` são definidos como zero. Definir esses atributos como zero significa que a heurística de dimensionamento automático de <xref:System.Runtime.Caching.MemoryCache> é usada por padrão. A implementação de cache deve comparar a carga de memória atual com os limites de memória absolutos e baseados em porcentagem a cada dois minutos.  
  
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
  
## <a name="see-also"></a>Consulte também

- [\<elemento de > memoryCache (configurações de cache)](memorycache-element-cache-settings.md)
