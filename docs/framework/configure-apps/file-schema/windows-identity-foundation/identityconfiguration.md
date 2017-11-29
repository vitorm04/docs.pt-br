---
title: '&lt;identityConfiguration&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1db76253-07da-447b-9e7a-3705c7228cf4
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: b1cca286fc967631c60aa02a1318fe24120e05b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltidentityconfigurationgt"></a>&lt;identityConfiguration&gt;
Especifica as configurações de identidade de nível de serviço.  
  
 \<System. IdentityModel >  
\<identityConfiguration >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration  
      name=xs:string  
      saveBootstrapContext=xs:boolean>  
      maximumClockSkew=TimeSpan >  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|name|O nome da seção de configuração de identidade. Você pode usar esse nome para fazer referência a uma seção de configuração específico. Se nenhum `name` atributo for especificado, a seção define a configuração padrão. A configuração padrão é sempre usada para cenários de federação passiva. Para obter mais informações, consulte o [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) elemento.|  
|saveBootstrapContext|Especifica se os tokens de inicialização devem ser incluídos no token de sessão. O valor também pode ser definido em uma coleção de manipulador de token, definindo o `saveBootstrapContext` atributo no [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) elemento. Um valor definido na coleção de manipulador de token substitui o valor definido no serviço.|  
|maximumClockSkew|Um <xref:System.TimeSpan> que especifica a distorção máxima permitida do relógio. Controla a distorção máxima permitida do relógio ao executar operações de detecção de hora, como validar o tempo de expiração de uma sessão de logon. O padrão é 5 minutos, "00: 05:00". Para obter mais informações sobre como especificar <xref:System.TimeSpan> valores, consulte [Timespan valores](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md). O máximo do relógio também pode ser definido em uma coleção de manipulador de token, definindo o `maximumClockSkew` atributo no [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) elemento. Um valor definido na coleção de manipulador de token substitui o valor definido no serviço.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<armazena em cache >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|Registra os caches usados para detecção de reprodução de token e tokens de sessão. Pode ser especificado no nível de serviço ou em uma coleção de manipulador de token de segurança. Opcional.|  
|[\<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|Controla as configurações que manipuladores de token usam para validar certificados. Pode ser especificado no nível de serviço ou em uma coleção de manipulador de token de segurança. Opcional.|  
|[\<claimsAuthenticationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthenticationmanager.md)|Registra um Gerenciador de autenticação de declarações para as declarações de entrada. Opcional.|  
|[\<o claimsAuthorizationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md)|Registra um Gerenciador de autorização de declarações para as declarações de entrada. Opcional.|  
|[\<claimTypeRequired >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|Especifica o conjunto de declarações necessárias para tokens de segurança de entrada. Opcional.|  
|[\<securityTokenHandlers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|Especifica uma coleção de manipuladores de token de segurança. Zero ou mais coleções de manipuladores de token de segurança podem ser especificadas. Opcional.|  
|[\<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|Habilita a detecção de reprodução de token e especifica a hora de expiração de tokens. Pode ser especificado no nível de serviço ou em uma coleção de manipulador de token de segurança. Opcional.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<System. IdentityModel >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md)|Fornece configuração para habilitar opções do Windows Identity Foundation (WIF) em aplicativos.|  
  
## <a name="remarks"></a>Comentários  
 Identidade várias configurações podem ser definidas, cada um com um nome exclusivo. O comportamento é o seguinte:  
  
1.  Se nenhum `<identityConfiguration>` elemento for especificado. Uma configuração de identidade padrão é criada em tempo de execução e preenchida com valores padrão.  
  
2.  Se um único `<identityConfiguration>` elemento for especificado. É a configuração padrão de identidade. Não importa se ele é nomeado ou sem nome.  
  
3.  Se vários `<identityConfiguration>` elementos são especificados. O elemento sem nome Especifica a configuração de identidade padrão. É recomendável que quando você especificar vários `<identityConfiguration>` elementos, um deles deve ser sem nome.  
  
> [!WARNING]
>  Se você especificar vários `<identityConfiguration>` elementos, um deles deve ser sem nome. O elemento sem nome será a configuração de identidade padrão.  
  
 Algumas das configurações especificadas no `<identityConfiguration>` elemento pode ser substituído por configurações em uma coleção de manipulador de token de segurança ou configurações de manipuladores de token de segurança individuais.  
  
> [!IMPORTANT]
>  Ao usar o <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> ou <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> classe para fornecer controle de acesso baseado em declarações em seu código, a configuração de identidade que é referenciado pelo `<federationConfiguration>` elemento configura o Gerenciador de autorização de declarações e a política que é usada para fazer decisões de autorização. Isso é verdadeiro mesmo em cenários que não são cenários de Web passivos, por exemplo, aplicativos do Windows Communication Foundation (WCF) ou um aplicativo que não é baseado na Web. Se o aplicativo não é um aplicativo da Web passivo, o [ \<claimsAuthorizationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md) elemento (e seus elementos de diretiva filho, se presente) da configuração de identidade referenciada são as únicas configurações aplicadas. Todas as outras configurações são ignoradas. Para obter mais informações, consulte o [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) elemento.  
  
 O `<identityConfiguration>` elemento é representado pela <xref:System.IdentityModel.Configuration.IdentityConfigurationElement> classe. Uma seção de configuração de identidade é representada pela <xref:System.IdentityModel.Configuration.IdentityConfiguration> classe.  
  
> [!IMPORTANT]
>  Especificando os seguintes elementos como elementos filho de `<identityConfiguration>` elemento foi preterido, embora ainda haja suporte para o comportamento para compatibilidade com versões anteriores. Esses elementos em vez disso, devem ser especificados o [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) elemento.  
>   
>  -   [\<audienceUris >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)  
> -   [\<issuerNameRegistry >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)  
> -   [\<issuerTokenResolver >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)  
> -   [\<serviceTokenResolver >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria uma configuração de identidade chamada "alternateConfiguration". A configuração de identidade Especifica as configurações padrão.  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="alternateConfiguration"/>  
</system.identityModel>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IdentityModel.Configuration.IdentityConfiguration>  
 <xref:System.IdentityModel.Configuration.IdentityConfigurationElement>
