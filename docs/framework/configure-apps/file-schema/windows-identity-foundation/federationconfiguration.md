---
title: <federationConfiguration>
ms.date: 03/30/2017
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
author: BrucePerlerMS
ms.openlocfilehash: bcd8e00b770517e3faff011b4acee08ebdc5a0df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152730"
---
# <a name="federationconfiguration"></a>\<federationConfiguration>
Configura o <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) <xref:System.IdentityModel.Services.SessionAuthenticationModule> e o (SAM) ao usar a autenticação federada através do protocolo WS-Federation. Configura o <xref:System.Security.Claims.ClaimsAuthorizationManager> quando <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> usa <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> a ou a classe para fornecer controle de acesso baseado em sinistros.  
  
[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<federaçãoconfiguração>**  
  
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
|name|O nome deste elemento de configuração da federação. Este atributo fornece principalmente um ponto de extensibilidade para protocolos futuros. Opcional.|  
|identityConfigurationName|O nome da seção de configuração de identidade especificado em uma [ \<identidadeConfiguração>](identityconfiguration.md) elemento a ser usado. Se esse atributo não for especificado, a seção de configuração de identidade padrão será usada. Opcional.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<>de cookiesHandler](cookiehandler.md)|Configura o manipulador de cookies usado pelo SAM. Opcional.|  
|[\<>de>de certificados de serviço](servicecertificate.md)|Configura o certificado usado para criptografar e descriptografar tokens. Opcional.|  
|[\<>da WSFederation](wsfederation.md)|Configura o Módulo de Autenticação WS-Federação (WSFAM). Opcional.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<system.identityModel.services>](system-identitymodel-services.md)|Seção de configuração para autenticação usando o protocolo WS-Federation.|  
  
## <a name="remarks"></a>Comentários  
 O \<elemento federationConfiguration> fornece configurações em dois cenários diferentes:  
  
- Ao usar o WS-Federation em uma aplicação web passiva, <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> o elemento contém configurações que configuram o (WSFAM) e o <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM). Ele também faz referência à configuração de identidade a ser usada para configurar manipuladores e certificados de token de segurança e componentes como o gerenciador de autorização de sinistros e o gerenciador de autenticação de sinistros.  
  
- Ao usar <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> a <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> ou a classe para fornecer controle de acesso baseado em sinistros em seu código, o elemento faz referência à configuração de identidade que configura o gerenciador e a política de autorização de sinistros que é usada para tomar decisões de autorização. Isso é verdade, mesmo em cenários que não são cenários passivos da Web; por exemplo, aplicativos do Windows Communication Foundation (WCF) ou um aplicativo que não seja baseado na Web. Se o aplicativo não for um aplicativo da Web passivo, o `<federationConfiguration>` [ \<claimsAuthorizationManager>](claimsauthorizationmanager.md) elemento (e seus elementos de política filho, se presente) da configuração de identidade referenciada pelo elemento são as únicas configurações aplicadas. Todos os outros são ignorados.  
  
 Independentemente do cenário, o tempo de execução carrega a configuração padrão da federação. O comportamento é definido da seguinte forma:  
  
1. Se não `<federationConfiguration>` houver nenhum elemento presente, o tempo de execução cria uma configuração de federação e a preenche com valores padrão. Essa configuração de federação padrão fará referência à configuração de identidade padrão.  
  
2. Se um `<federationConfiguration>` único elemento estiver presente, é a configuração padrão da federação, independentemente de ser nomeado ou não. Se `identityConfiguration` seu atributo for especificado, a configuração de identidade nomeada será referenciada; caso contrário, a configuração de identidade padrão é referenciada.  
  
3. Se um `<federationConfiguration>` elemento não nomeado estiver presente, é a configuração padrão da federação. Se `identityConfiguration` seu atributo for especificado, a configuração de identidade nomeada será referenciada; caso contrário, a configuração de identidade padrão é referenciada.  
  
4. Se vários `<federationConfiguration>` elementos nomeados `<federationConfiguration>` estiverem presentes e nenhum elemento não nomeado estiver presente, uma exceção será lançada.  
  
 Normalmente, apenas `<federationConfiguration>` uma única seção é definida. Esta seção é a configuração padrão da federação. Você pode especificar vários `<federationConfiguration>` elementos com nome exclusivo; no entanto, neste caso, se você quiser carregar uma configuração de federação diferente da não nomeada, você deve fornecer um manipulador para o. <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated>evento e <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> definir a propriedade <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> dentro do manipulador para `<federationConfiguration>` um objeto inicializado com valores do elemento apropriado no arquivo de configuração.  
  
 O `<federationConfiguration>` elemento é <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> representado pela classe. O objeto de configuração <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> em si é representado pela classe. Uma <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> única instância é <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> definida na propriedade e fornece configuração federada para o aplicativo.  
  
## <a name="example"></a>Exemplo  
 O XML a `<federationConfiguration>` seguir mostra um elemento que especifica as configurações para o WSFAM e especifica que o manipulador de cookies padrão (uma instância da <xref:System.IdentityModel.Services.ChunkedCookieHandler> classe) será usado pelo SAM.  
  
> [!WARNING]
> Neste exemplo, nem o manipulador de cookies nem o WSFAM são obrigados a usar HTTPS. Isso porque `requireHttps` o atributo `<wsFederation>` no `requireSsl` elemento `<cookieHandlerElement>` e `false`o atributo no são . Essas configurações não são recomendadas para a maioria dos ambientes de produção, pois podem apresentar um risco à segurança.  
  
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
  
## <a name="see-also"></a>Confira também

- <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>
- <xref:System.IdentityModel.Services.SessionAuthenticationModule>
- <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>
- [\<>de configuração de identidade](identityconfiguration.md)
