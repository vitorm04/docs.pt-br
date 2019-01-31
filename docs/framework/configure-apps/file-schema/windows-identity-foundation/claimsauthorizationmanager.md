---
title: <claimsAuthorizationManager>
ms.date: 03/30/2017
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
author: BrucePerlerMS
ms.openlocfilehash: 59d47eda97e97629408ece12a1d1dfbe804feb3e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55268087"
---
# <a name="claimsauthorizationmanager"></a>\<claimsAuthorizationManager>
Registra um Gerenciador de autorização de declarações para as declarações de entrada.  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<claimsAuthorizationManager>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthorizationManager type = xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthorizationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|tipo|Um tipo personalizado que deriva de <xref:System.Security.Claims.ClaimsAuthorizationManager> classe. Para obter mais informações sobre como especificar o `type` atributo, consulte [referências de tipo personalizado](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).|  
  
### <a name="child-elements"></a>Elementos filho  
 Se não houver nenhuma `type` atributo, ou se o `type` as referências ao atributo de <xref:System.Security.Claims.ClaimsAuthenticationManager> classe, o `<claimsAuthorizationManager>` elemento não tem elementos filho; no entanto, as classes derivadas de <xref:System.Security.Claims.ClaimsAuthorizationManager> pode definir os elementos de configuração filho.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Especifica as configurações de identidade de nível de serviço.|  
  
## <a name="remarks"></a>Comentários  
 O comportamento padrão fornecido por meio de <xref:System.Security.Claims.ClaimsAuthorizationManager> classe sempre autoriza as declarações de entrada. Se nenhum `type` atributo for especificado ou se o `type` atributo especifica a <xref:System.Security.Claims.ClaimsAuthorizationManager> classe, o `<claimsAuthorizationManager>` elemento não tem elementos filho. Você pode especificar o `type` atributo para registrar um tipo derivado do <xref:System.Security.Claims.ClaimsAuthorizationManager> classe para implementar comportamento personalizado. Classes derivadas podem dar suporte a configuração por meio de elementos filho do `<claimsAuthorizationManager>` elemento, substituindo o <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> método para lidar com esses elementos. O esquema definido para os elementos filho é até o designer da classe.  
  
> [!IMPORTANT]
>  Ao usar o <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> ou o <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> classe para fornecer controle de acesso baseado em declarações em seu código, a configuração de identidade que é referenciado pelo `<federationConfiguration>` elemento configura o Gerenciador de autorização de declarações e a política que é usada para fazer decisões de autorização. Isso é verdadeiro, mesmo em cenários que não são cenários passivos na Web, por exemplo, aplicativos do Windows Communication Foundation (WCF) ou um aplicativo que não é baseado na Web. Se o aplicativo não for um aplicativo da Web passivo, o `<claimsAuthorizationManager>` elemento (e seus elementos de política filho, se presente) da configuração de identidade referenciada são as únicas configurações aplicadas. Todas as outras configurações são ignoradas. Para obter mais informações, consulte o [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) elemento.  
  
 Esse elemento define o <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> propriedade.  
  
## <a name="example"></a>Exemplo  
 O XML a seguir mostra a configuração para a autorização de declarações Gerenciador que implementa a política composta de pares de ação de recurso de cada um deles especifica combinações booleanas as declarações que um solicitante deve ter para executar a ação no recurso. O código que implementa o Gerenciador de autorização de declarações capaz de usar essa política pode ser encontrado na `ClaimsBasedAuthorization` exemplo.  
  
```xml  
<system.identityModel>  
    <identityConfiguration>  
      <claimsAuthorizationManager type="ClaimsAuthorizationLibrary.MyClaimsAuthorizationManager, ClaimsAuthorizationLibrary">  
        <policy resource="http://localhost:28491/Developers.aspx" action="GET">  
          <or>  
            <claim claimType="http://schemas.microsoft.com/ws/2008/06/identity/claims/role" claimValue="developer" />  
            <claim claimType="http://schemas.xmlsoap.org/claims/Group" claimValue="Administrator" />  
          </or>  
        </policy>  
        <policy resource="http://localhost:28491/Administrators.aspx" action="GET">  
          <and>  
            <claim claimType="http://schemas.xmlsoap.org/claims/Group" claimValue="Administrator" />  
            <claim claimType="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/country" claimValue="USA" />  
          </and>  
        </policy>  
        <policy resource="http://localhost:28491/Default.aspx" action="GET">  
        </policy>  
        <policy resource="http://localhost:28491/" action="GET">  
        </policy>  
        <policy resource="http://localhost:28491/Claims.aspx" action="GET">  
        </policy>  
      </claimsAuthorizationManager>  
    <identityConfiguration>  
<system.identityModel>  
```
