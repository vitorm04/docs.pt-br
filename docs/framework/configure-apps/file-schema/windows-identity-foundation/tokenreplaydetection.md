---
title: '&lt;tokenReplayDetection&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 88622d4d30d40702425da8bbdbdaf2c4a6878f47
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="lttokenreplaydetectiongt"></a>&lt;tokenReplayDetection&gt;
Habilita a detecção de reprodução de token e especifica a hora de expiração de tokens.  
  
 \<System. IdentityModel >  
\<identityConfiguration >  
\<tokenReplayDetection >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a>Tipo  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|Habilitado|Um valor que especifica se a detecção de reprodução de token é habilitada; detecção de repetição "true" para habilitar o token.|  
|expirationPeriod|Um <xref:System.TimeSpan> que especifica a quantidade máxima de tempo antes que um item é considerado expirado e removido do cache.  Para obter mais informações sobre como especificar <xref:System.TimeSpan> valores, consulte [Timespan valores](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Especifica as configurações de identidade de nível de serviço.|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Fornece manipuladores de token de configuração para uma coleção de segurança.|  
  
## <a name="remarks"></a>Comentários  
 Um `<tokenReplayDetection>` elemento pode ser especificado no nível de serviço sob a `<identityConfiguration>` elemento ou em nível de coleção de manipulador de token de segurança sob o `<securityTokenHandlerConfiguration>` elemento. As configurações em uma coleção de manipulador de token substituem aquelas especificadas no serviço.  
  
 O tipo de cache de reprodução de token é especificado pelo [ \<tokenReplayCache >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) elemento.
