---
title: '&lt;securityTokenHandlerConfiguration&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: ac7284fa418c1540582c40bd744e913ba31aa881
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecuritytokenhandlerconfigurationgt"></a>&lt;securityTokenHandlerConfiguration&gt;
Fornece configuração para a coleção de manipuladores de token.  
  
 \<System. IdentityModel >  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<securityTokenHandlerConfiguration >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration saveBootstrapContext=xs:boolean  
          maximumClockSkew=TimeSpan>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|saveBootstrapContext|Especifica se os tokens de inicialização devem ser incluídos no token de sessão. O valor também pode ser definido em uma coleção de manipulador de token, definindo o `saveBootstrapContext` atributo no [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elemento. Um valor definido na coleção de manipulador de token substitui o valor definido no serviço.|  
|maximumClockSkew|Um <xref:System.TimeSpan> que especifica a distorção máxima permitida do relógio. Controla a distorção máxima permitida do relógio ao executar operações de detecção de hora, como validar o tempo de expiração de uma sessão de logon. O padrão é 5 minutos, "00: 05:00". Para obter mais informações sobre como especificar <xref:System.TimeSpan> valores, consulte [Timespan valores](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md). O máximo do relógio também pode ser definido no nível de serviço, definindo o `maximumClockSkew` atributo no [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elemento. Um valor definido na coleção de manipulador de token substitui o valor definido no serviço.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<audienceUris >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)|Especifica o conjunto de URIs que são aceitáveis identificadores da terceira parte confiável. Opcional.|  
|[\<armazena em cache >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|Registra os caches usados para detecção de reprodução de token e tokens de sessão. Pode ser especificado no nível de serviço ou em uma coleção de manipulador de token de segurança. Opcional.|  
|[\<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|Controla as configurações que manipuladores de token usam para validar certificados. Pode ser especificado no nível de serviço ou em uma coleção de manipulador de token de segurança. Essas configurações são substituídas se um manipulador específico é configurado com seu próprio validados. Opcional.|  
|[\<issuerNameRegistry >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|Configura o registro de nome de emissor que é usado por manipuladores na coleção de manipulador de token. Opcional.|  
|[\<issuerTokenResolver >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)|Registra o resolvedor de token do emissor que é usado por manipuladores na coleção de manipulador de token. O resolvedor de token do emissor é usado para resolver o token de assinatura em tokens de entrada e de mensagens. Opcional.|  
|[\<serviceTokenResolver >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)|Registra o resolvedor de token de serviço que é usado por manipuladores na coleção de manipulador de token. O resolvedor de token de serviço é usado para resolver o token de criptografia em tokens de entrada e de mensagens. Opcional.|  
|[\<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|Habilita a detecção de reprodução de token e especifica a hora de expiração de tokens. Pode ser especificado no nível de serviço ou em uma coleção de manipulador de token de segurança. Opcional.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<securityTokenHandlers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|Especifica uma coleção de manipuladores de token de segurança que são registrados com o ponto de extremidade.|  
  
## <a name="remarks"></a>Comentários  
 Esta seção fornece valores de propriedade para um <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> objeto. As configurações definidas nesta seção substituem aquelas configuradas no serviço. Algumas dessas configurações, por sua vez, podem ser substituídas pelas configurações que são especificadas quando um manipulador é adicionado à coleção de manipulador de token de segurança.  
  
## <a name="example"></a>Exemplo  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>   
      <securityTokenHandlerConfiguration>  
  
        <audienceUris>  
          <clear/>  
          <add value="http://www.example.com/myapp/" />  
        </audienceUris>  
  
        <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel">  
          <trustedIssuers>  
            <add thumbprint="97249e1a … 4c9158de" name="contoso.com" />  
          </trustedIssuers>  
        </issuerNameRegistry>  
  
        <issuerTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
        <serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```
