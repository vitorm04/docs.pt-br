---
title: '&lt;armazena em cache&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: b9dfa7b2f0952f3f9e224ad51fd4d9c0c263ce04
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcachesgt"></a>&lt;armazena em cache&gt;
Registra os caches usados para detecção de reprodução de token e tokens de sessão.  
  
 \<System. IdentityModel >  
\<identityConfiguration >  
\<armazena em cache >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 Nenhum  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<sessionSecurityTokenCache >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md)|Registra um cache de tokens de sessão com um serviço ou uma coleção de manipulador de token de segurança.|  
|[\<tokenReplayCache >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md)|Registra um cache de reprodução de token com um serviço ou uma coleção de manipulador de token de segurança.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Especifica as configurações de identidade de nível de serviço.|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Fornece manipuladores de token de configuração para uma coleção de segurança.|  
  
## <a name="remarks"></a>Comentários  
 Um `<caches>` elemento pode ser especificado no nível de serviço sob a `<identityConfiguration>` elemento ou em nível de coleção de manipulador de token de segurança sob o `<securityTokenHandlerConfiguration>` elemento. As configurações em uma coleção de manipulador de token substituem aquelas especificadas no serviço.  
  
 O `<caches>` elemento é representado pela <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> classe. Os caches configurados são representados pelo <xref:System.IdentityModel.Configuration.IdentityModelCaches> classe.  
  
## <a name="example"></a>Exemplo  
 O XML a seguir mostra a configuração de um cache personalizado para manter a sessão de tokens de segurança (<xref:System.IdentityModel.Tokens.SessionSecurityToken>). A configuração é obtida o `ClaimsAwareWebFarm` exemplo.  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
