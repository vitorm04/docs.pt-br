---
title: <defaultFtpCachePolicy> (Configurações de rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy
helpviewer_keywords:
- <defaultFtpCachePolicy> element
- defaultFtpCachePolicy element
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
ms.openlocfilehash: 36d174beea58ff96674bd873bfbcb8be89591669
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132529"
---
# <a name="defaultftpcachepolicy-element-network-settings"></a>\<defaultFtpCachePolicy > (configurações de rede)
Descreve se o cache de FTP está ativo e descreve a política de cache padrão.  
  
 \<configuration>  
\<system.net>  
\<requestCaching>  
\<defaultFtpCachePolicy>  
  
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
|`policyLevel`|Especifica o política de cache de FTP. O valor padrão é `Default`.|  
  
## <a name="policylevel-attribute"></a>policyLevel atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`Default`|Retorna o recurso armazenado em cache se o recurso estiver atualizado, o comprimento do conteúdo é preciso e a expiração, modificação e atributos de comprimento de conteúdo estão presentes.|  
|`BypassCache`|Retorna o recursos do servidor.|  
|`CacheOnly`|Retorna o recurso armazenado em cache se o comprimento do conteúdo está presente e corresponde ao tamanho de entrada.|  
|`CacheIfAvailable`|Retorna o recurso armazenado em cache se o comprimento do conteúdo é fornecido e corresponde o tamanho da entrada. Caso contrário, o recurso é baixado do servidor e é retornado ao chamador.|  
|`Revalidate`|Retorna o recurso armazenado em cache se o carimbo de hora do recurso em cache é o mesmo que o carimbo de hora do recurso no servidor. Caso contrário, o recurso é baixado do servidor, armazenado no cache e retornado ao chamador.|  
|`Reload`|Baixa o recurso do servidor, armazena em cache e retorna o recurso para o chamador.|  
|`NoCacheNoStore`|Se existir um recurso armazenado em cache, ele será excluído. O recurso é baixado do servidor e é retornado ao chamador.|  
|`Revalidate`|Atende a uma solicitação usando a cópia do recurso armazenada em cache se o carimbo de data/hora for igual ao do recurso no servidor; caso contrário, o recurso será baixado do servidor, apresentado ao chamador e armazenado no cache.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[requestCaching](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|Controla o mecanismo de cache para solicitações de rede.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como especificar um política de cache de FTP `NoCacheNoStore`.  
  
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
- [Esquema de configurações de rede](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
