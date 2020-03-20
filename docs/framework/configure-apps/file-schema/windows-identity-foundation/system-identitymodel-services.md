---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: 57757aaec39bc5c552e7ba12c9779cb3a92a9025
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152498"
---
# <a name="systemidentitymodelservices"></a>\<system.identityModel.services>
Seção de configuração para autenticação usando o protocolo WS-Federation.  
  
[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.identityModel.services>**  
  
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
 Nenhum  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<federaçãoconfiguração>](federationconfiguration.md)|Contém as configurações que <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> configuram os módulos <xref:System.IdentityModel.Services.SessionAuthenticationModule> HTTP (WSFAM) e (SAM).|  
  
### <a name="parent-elements"></a>Elementos pai  
 Nenhum  
  
## <a name="remarks"></a>Comentários  
 Adicione `<system.identityModel.services>` uma seção ao arquivo de configuração do aplicativo para fornecer configurações para o SAM e o WSFAM.  
  
> [!IMPORTANT]
> Ao usar <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> a <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> classe ou a classe para fornecer controle de<xref:System.Security.Claims.ClaimsAuthorizationManager>acesso baseado em sinistros em seu código, `<identityConfiguration>` o gerenciador de autorização de sinistros ( ) e a política que é usada para tomar decisões de autorização são configurados através de um elemento que é implicitamente ou explicitamente referenciado a partir de um `<federationConfiguration>` elemento nesta seção. Para obter mais informações, consulte as **Observações** o elemento [ \<>de configuração da federação.](federationconfiguration.md)  
  
 A `<system.identityModel.services>` seção é <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> representada pela classe. A coleção `<federationConfiguration>` de elementos infantis configurados <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> na seção é representada pela classe.  
  
## <a name="example"></a>Exemplo  
 O XML a seguir `<system.identityModel.services>` mostra como adicionar uma seção a um arquivo de configuração. Você deve primeiro adicionar declarações `<system.identityModel.services>` de `<system.identityModel>` seção para a seção e as seções. (Quando você `<system.identityModel.services>` adiciona uma seção, você `<system.identityModel>` também deve adicionar `<identityConfiguration>` uma declaração para a seção para garantir que uma seção padrão possa ser criada pelo tempo de execução, se necessário.) Depois que as declarações de seção foram adicionadas, você `<system.identityModel.services>` pode configurar configurações de autenticação federada o elemento.  
  
```xml  
<configuration>  
  <configSections>  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
  </configSections>  
  
  <!-- Additional elements (not shown) -->  
  
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
  
</configuration>  
```
