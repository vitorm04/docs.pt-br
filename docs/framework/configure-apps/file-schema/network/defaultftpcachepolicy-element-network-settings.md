---
title: Elemento <defaultFtpCachePolicy> (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy
helpviewer_keywords:
- <defaultFtpCachePolicy> element
- defaultFtpCachePolicy element
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
ms.openlocfilehash: 9261a430642cb4d5ac4507835bd0fd3561bd8c02
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088436"
---
# <a name="defaultftpcachepolicy-element-network-settings"></a>\<elemento de > defaultFtpCachePolicy (configurações de rede)
Descreve se o cache FTP está ativo e descreve a política de cache padrão.  

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<requestCaching >** ](requestcaching-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<defaultFtpCachePolicy >**

## <a name="syntax"></a>Sintaxe  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`policyLevel`|Especifica a política de cache de FTP. O valor padrão é `Default`.|  
  
## <a name="policylevel-attribute"></a>Atributo policyLevel  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`Default`|Retorna o recurso armazenado em cache se o recurso for atualizado, se o tamanho do conteúdo for preciso e os atributos de expiração, modificação e comprimento do conteúdo estiverem presentes.|  
|`BypassCache`|Retorna o recurso do servidor.|  
|`CacheOnly`|Retorna o recurso armazenado em cache se o tamanho do conteúdo estiver presente e corresponder ao tamanho da entrada.|  
|`CacheIfAvailable`|Retornará o recurso armazenado em cache se o comprimento do conteúdo for fornecido e corresponder ao tamanho da entrada; caso contrário, o recurso é baixado do servidor e retornado para o chamador.|  
|`Revalidate`|Retorna o recurso armazenado em cache se o carimbo de data/hora do recurso armazenado em cache for o mesmo que o carimbo de data/hora do recurso no servidor; caso contrário, o recurso será baixado do servidor, armazenado no cache e retornado ao chamador.|  
|`Reload`|Baixa o recurso do servidor, armazena-o no cache e retorna o recurso para o chamador.|  
|`NoCacheNoStore`|Se um recurso armazenado em cache existir, ele será excluído. O recurso é baixado do servidor e retornado para o chamador.|  
|`Revalidate`|Atende a uma solicitação usando a cópia do recurso armazenada em cache se o carimbo de data/hora for igual ao do recurso no servidor; caso contrário, o recurso será baixado do servidor, apresentado ao chamador e armazenado no cache.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[requestCaching](requestcaching-element-network-settings.md)|Controla o mecanismo de cache para solicitações de rede.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como especificar uma política de cache de FTP de `NoCacheNoStore`.  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultFtpCachePolicy  
        policyLevel="NoCacheNoStore">  
      </defaultFtpCachePolicy>  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [Esquema de configurações de rede](index.md)
