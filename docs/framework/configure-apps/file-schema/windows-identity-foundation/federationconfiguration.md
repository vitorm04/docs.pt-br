---
title: '&lt;federationConfiguration&gt;'
ms.date: 03/30/2017
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 44014d620dcd03e055eb58b50a1428b8e1b41186
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltfederationconfigurationgt"></a>&lt;federationConfiguration&gt;
Configura o <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) e o <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) ao usar federated autenticação por meio do protocolo WS-Federation. Configura o <xref:System.Security.Claims.ClaimsAuthorizationManager> ao usar o <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> ou <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> classe para fornecer controle de acesso baseado em declarações.  
  
 \<System >  
\<federationConfiguration >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|name|O nome deste elemento de configuração de Federação. Esse atributo principalmente fornece um ponto de extensibilidade para protocolos futuras. Opcional.|  
|identityConfigurationName|O nome da seção de configuração de identidade como especificado em uma [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elemento a ser usado. Se esse atributo não for especificado, a seção de configuração de identidade padrão será usada. Opcional.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<cookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|Configura o manipulador de cookie usado pelo SAM. Opcional.|  
|[\<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|Configura o certificado usado para criptografar e descriptografar tokens. Opcional.|  
|[\<wsFederation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation.md)|Configura o módulo de autenticação de WS-Federation (WSFAM). Opcional.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<system.identityModel.services>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)|Seção de configuração para a autenticação usando o protocolo WS-Federation.|  
  
## <a name="remarks"></a>Comentários  
 O \<federationConfiguration > elemento fornece configurações em dois cenários diferentes:  
  
-   Ao usar o WS-Federation em um aplicativo da Web passivo, o elemento contém configurações que configura o <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) e o <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM). Ele também faz referência a configuração de identidade a ser usado para configurar os componentes, como o Gerenciador de autorização de declarações e o Gerenciador de autenticação de declarações, certificados e manipuladores de token de segurança.  
  
-   Ao usar o <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> ou <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> da classe para fornecer controle de acesso baseado em declarações em seu código, o elemento faz referência a configuração de identidade que configura o Gerenciador de autorização de declarações e a política que é usada para fazer a autorização decisões. Isso é verdadeiro mesmo em cenários que não são cenários de Web passivos; Por exemplo, aplicativos do Windows Communication Foundation (WCF) ou um aplicativo que não é baseado na Web. Se o aplicativo não é um aplicativo da Web passivo, o [ \<claimsAuthorizationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md) elemento (e seus elementos de diretiva filho, se presente) da configuração de identidade referenciada pelo `<federationConfiguration>` elemento as únicas configurações são aplicadas. Todos os outros são ignorados.  
  
 Independentemente do cenário, o tempo de execução carrega a configuração padrão de Federação. O comportamento é definido da seguinte maneira:  
  
1.  Se não houver nenhum `<federationConfiguration>` elemento presente, o tempo de execução cria uma configuração de Federação e o preenche com valores padrão. Essa configuração de Federação padrão fará referência a configuração de identidade padrão.  
  
2.  Se um único `<federationConfiguration>` estiver presente, é a configuração padrão de federação, independentemente de ele é nomeado ou sem nome. Se seu `identityConfiguration` atributo for especificado, a configuração de identidade nomeada é referenciada; caso contrário, a configuração padrão de identidade é referenciada.  
  
3.  Se um dispositivo sem nome `<federationConfiguration>` estiver presente, é a configuração padrão de Federação. Se seu `identityConfiguration` atributo for especificado, a configuração de identidade nomeada é referenciada; caso contrário, a configuração padrão de identidade é referenciada.  
  
4.  Se o nome de vários `<federationConfiguration>` elementos estão presentes e sem nome não `<federationConfiguration>` estiver presente, uma exceção será lançada.  
  
 Normalmente, um único `<federationConfiguration>` seção está definida. Esta seção é a configuração padrão de Federação. Você pode especificar vários exclusivamente nomeada `<federationConfiguration>` elementos; no entanto, nesse caso, se você quiser carregar uma configuração de Federação diferente sem nome, você deve fornecer um manipulador para o. <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated> eventos e defina o <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> propriedade dentro do manipulador para um <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> objeto inicializado com valores de apropriado `<federationConfiguration>` elemento no arquivo de configuração.  
  
 O `<federationConfiguration>` elemento é representado pela <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> classe. O objeto de configuração é representado pela <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> classe. Um único <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> instância é ativada a <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> propriedade e fornece configuração federado para o aplicativo.  
  
## <a name="example"></a>Exemplo  
 O XML a seguir mostra um `<federationConfiguration>` elemento que especifica configurações para o WSFAM e especifica que o manipulador de cookie padrão (uma instância do <xref:System.IdentityModel.Services.ChunkedCookieHandler> classe) ser usado pelo SAM.  
  
> [!WARNING]
>  Neste exemplo, o manipulador de cookie nem WSFAM devem usar HTTPS. Isso ocorre porque o `requireHttps` atributo no `<wsFederation>` elemento e o `requireSsl` atributo no `<cookieHandlerElement>` são `false`. Essas configurações não são recomendadas para a maioria dos ambientes de produção, pois eles podem representar um risco de segurança.  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <wsFederation passiveRedirectEnabled="true"   
      issuer="http://localhost:15839/wsFederationSTS/Issue"   
      realm="http://localhost:50969/" reply="http://localhost:50969/"   
      requireHttps="false"   
      signOutReply="http://localhost:50969/SignedOutPage.html"   
      signOutQueryString="Param1=value2&Param2=value2"   
      persistentCookiesOnPassiveRedirects="true" />  
    <cookieHandler requireSsl="false" />  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>  
 <xref:System.IdentityModel.Services.SessionAuthenticationModule>  
 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>  
 [\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)
