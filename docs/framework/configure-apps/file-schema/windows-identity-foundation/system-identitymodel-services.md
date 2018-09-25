---
title: '&lt;IdentityModel&gt;'
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: c7261d20ae2379ad33679cadecdef484f2afdecf
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47075207"
---
# <a name="ltsystemidentitymodelservicesgt"></a>&lt;IdentityModel&gt;
Seção de configuração para a autenticação usando o protocolo WS-Federation.  
  
 \<IdentityModel >  
  
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
|[\<federationConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|Contém as configurações que configuram os <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) e o <xref:System.IdentityModel.Services.SessionAuthenticationModule> módulos HTTP (SAM).|  
  
### <a name="parent-elements"></a>Elementos pai  
 Nenhum  
  
## <a name="remarks"></a>Comentários  
 Adicionar um `<system.identityModel.services>` seção ao arquivo de configuração do seu aplicativo para fornecer configurações para o SAM e o WSFAM.  
  
> [!IMPORTANT]
>  Ao usar o <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> ou o <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> classe para fornecer controle de acesso baseado em declarações em seu código, o Gerenciador de autorização de declarações (<xref:System.Security.Claims.ClaimsAuthorizationManager>) e a política que é usada para tomar decisões de autorização são configurados por meio de um `<identityConfiguration>` elemento que é implicitamente ou explicitamente referenciado em um `<federationConfiguration>` elemento nesta seção. Para obter mais informações, consulte o **Remarks** sob o [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) elemento.  
  
 O `<system.identityModel.services>` seção é representada pelo <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> classe. A coleção de filhos `<federationConfiguration>` configurados na seção de elementos é representado pelo <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> classe.  
  
## <a name="example"></a>Exemplo  
 O XML a seguir mostra como adicionar um `<system.identityModel.services>` seção ao arquivo de configuração. Você deve primeiro adicionar declarações de seção para ambos os `<system.identityModel.services>` seção e o `<system.identityModel>` seções. (Quando você adiciona uma `<system.identityModel.services>` seção, você também deve adicionar uma declaração para o `<system.identityModel>` seção para garantir que um padrão `<identityConfiguration>` seção pode ser criada pelo tempo de execução, se necessário.) Depois que as declarações de seção foram adicionadas, você pode definir configurações de autenticação federada sob o `<system.identityModel.services>` elemento.  
  
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
