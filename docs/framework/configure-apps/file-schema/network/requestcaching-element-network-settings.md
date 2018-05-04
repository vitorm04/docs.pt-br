---
title: '&lt;requestCaching&gt; elemento (configurações de rede)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requestCaching
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching
helpviewer_keywords:
- requestCaching element
- <requestCaching> element
ms.assetid: 9962a2fe-cbda-41a6-9377-571811eaea84
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 9c0c8d80182931f9ac14e687a337b7be55a5a9a5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltrequestcachinggt-element-network-settings"></a>&lt;requestCaching&gt; elemento (configurações de rede)
Controla o mecanismo de cache para solicitações de rede.  
  
 \<configuration>  
\<system.net>  
\<requestCaching >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
      <requestCaching>  
        isPrivateCache ="true|false"  
        disableAllCaching="true|false"  
        defaultPolicyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
        unspecifiedMaximumAge= "d.hh.mm.ss">  
          <defaultHttpCachePolicy> … </defaultHttpCachePolicy>  
          <defaultFtpCachePolicy> … </defaultFtpCachePolicy>  
      </requestCaching>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`isPrivateCache`|Especifica se o cache fornece isolamento entre as informações de usuários diferentes. O valor padrão é `true`. Esse valor deve ser `false` para aplicativos de camada intermediária.|  
|`disableAllCaching`|Especifica que o cache está desabilitado para todas as respostas de Web e não pode ser substituído por meio de programação.|  
|`defaultPolicyLevel`|Um dos valores na enumeração <xref:System.Net.Cache.RequestCacheLevel>. O valor padrão é `BypassCache`.|  
|`unspecifiedMaximumAge`|Especifica o tempo padrão depois que o conteúdo seja marcado como expirada.|  
  
## <a name="policylevel-attribute"></a>policyLevel atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`Default`|Retorna o recurso em cache se o recurso for atualizado, o comprimento do conteúdo é preciso e a expiração, modificação e atributos de comprimento de conteúdo estão presentes.|  
|`BypassCache`|Retorna o recurso do servidor.|  
|`CacheOnly`|Retorna o recurso em cache se o comprimento do conteúdo está presente e corresponde ao tamanho de entrada.|  
|`CacheIfAvailable`|Retorna o recurso em cache se o comprimento do conteúdo for fornecido e corresponda ao tamanho de entrada; Caso contrário, o recurso é baixado do servidor e é retornado ao chamador.|  
|`Revalidate`|Retorna o recurso em cache se o carimbo de hora do recurso em cache é o mesmo que o carimbo de hora do recurso no servidor. Caso contrário, o recurso é baixado do servidor, armazenado em cache e é retornado ao chamador.|  
|`Reload`|Baixe o recurso do servidor, armazena em cache e retorna o recurso para o chamador.|  
|`NoCacheNoStore`|Se existe um recurso de cache, ele será excluído. O recurso é baixado do servidor e é retornado ao chamador.|  
|`Revalidate`|Atenda a uma solicitação usando a cópia armazenada em cache do recurso se o carimbo de hora é o mesmo que o carimbo de hora do recurso no servidor. Caso contrário, o recurso é baixado do servidor, apresentado para o chamador e é armazenado no cache,|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[defaultHttpCachePolicy](../../../../../docs/framework/configure-apps/file-schema/network/defaulthttpcachepolicy-element-network-settings.md)|Elemento opcional.<br /><br /> Descreve se o cache de HTTP está ativo e descreve a política de cache padrão.|  
|[\<defaultFtpCachePolicy > elemento (configurações de rede)](../../../../../docs/framework/configure-apps/file-schema/network/defaultftpcachepolicy-element-network-settings.md)|Elemento opcional.<br /><br /> Descreve se o cache de FTP está ativo e descreve a política de cache padrão.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[System.NET](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|Contém configurações que especificam como o .NET Framework se conecta à rede.|  
  
## <a name="example"></a>Exemplo  
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
 <xref:System.Net.Cache?displayProperty=nameWithType>  
 [Esquema de configurações de rede](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
