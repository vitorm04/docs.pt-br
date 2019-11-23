---
title: Elemento <requestCaching> (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requestCaching
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching
helpviewer_keywords:
- requestCaching element
- <requestCaching> element
ms.assetid: 9962a2fe-cbda-41a6-9377-571811eaea84
ms.openlocfilehash: f0979d2e0caeb0b22b90572aef0ad53235020f1d
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697835"
---
# <a name="requestcaching-element-network-settings"></a>\<Elemento requestCaching> (configurações de rede)
Controla o mecanismo de cache para solicitações de rede.  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp; **\<requestCaching >**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<requestCaching  
  isPrivateCache ="true|false"  
  disableAllCaching="true|false"  
  defaultPolicyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
  unspecifiedMaximumAge= "d.hh.mm.ss">  
    <defaultHttpCachePolicy>...</defaultHttpCachePolicy>  
    <defaultFtpCachePolicy>...</defaultFtpCachePolicy>  
</requestCaching>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem os atributos, bem como os elementos filhos e pais.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`isPrivateCache`|Especifica se o cache fornece isolamento entre as informações de diferentes usuários. O valor padrão é `true`. Esse valor deve ser `false` para aplicativos de camada intermediária.|  
|`disableAllCaching`|Especifica que o Caching está desabilitado para todas as respostas da Web e não pode ser substituído programaticamente.|  
|`defaultPolicyLevel`|Um dos valores na enumeração <xref:System.Net.Cache.RequestCacheLevel>. O valor padrão é `BypassCache`.|  
|`unspecifiedMaximumAge`|Especifica o tempo padrão após o qual o conteúdo é marcado como expirado.|  
  
## <a name="policylevel-attribute"></a>Atributo policyLevel  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`Default`|Retorna o recurso armazenado em cache se o recurso for atualizado, se o tamanho do conteúdo for preciso e os atributos de expiração, modificação e comprimento do conteúdo estiverem presentes.|  
|`BypassCache`|Retorna o recurso do servidor.|  
|`CacheOnly`|Retorna o recurso armazenado em cache se o tamanho do conteúdo estiver presente e corresponder ao tamanho da entrada.|  
|`CacheIfAvailable`|Retornará o recurso armazenado em cache se o comprimento do conteúdo for fornecido e corresponder ao tamanho da entrada; caso contrário, o recurso é baixado do servidor e retornado para o chamador.|  
|`Revalidate`|Retorna o recurso armazenado em cache se o carimbo de data/hora do recurso armazenado em cache for o mesmo que o carimbo de data/hora do recurso no servidor; caso contrário, o recurso será baixado do servidor, armazenado no cache, e retornado ao chamador.|  
|`Reload`|Baixa o recurso do servidor, armazena-o no cache e retorna o recurso para o chamador.|  
|`NoCacheNoStore`|Se um recurso armazenado em cache existir, ele será excluído. O recurso é baixado do servidor e retornado para o chamador.|  
|`Revalidate`|Atende a uma solicitação usando a cópia armazenada em cache do recurso se o carimbo de data/hora for o mesmo que o carimbo de data/hora do recurso no servidor; caso contrário, o recurso será baixado do servidor, apresentado ao chamador e armazenado no cache,|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[defaultHttpCachePolicy](defaulthttpcachepolicy-element-network-settings.md)|Elemento opcional.<br /><br /> Descreve se o cache HTTP está ativo e descreve a política de cache padrão.|  
|[\<elemento de > defaultFtpCachePolicy (configurações de rede)](defaultftpcachepolicy-element-network-settings.md)|Elemento opcional.<br /><br /> Descreve se o cache FTP está ativo e descreve a política de cache padrão.|  
  
### <a name="parent-elements"></a>Elementos Pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[system.net](system-net-element-network-settings.md)|Contém configurações que especificam como o .NET Framework se conecta à rede.|  
  
## <a name="example"></a>{1&gt;Exemplo&lt;1}  
 O exemplo a seguir mostra como desabilitar todo o cache.  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Net.Cache?displayProperty=nameWithType>
- [Esquema de configurações de rede](index.md)
