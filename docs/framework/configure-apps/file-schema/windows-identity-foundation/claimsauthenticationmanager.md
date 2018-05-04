---
title: '&lt;claimsAuthenticationManager&gt;'
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 4d4a91e0ed1f437089e26e5902515f73a15d94a8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltclaimsauthenticationmanagergt"></a>&lt;claimsAuthenticationManager&gt;
Registra um Gerenciador de autenticação de declarações para as declarações de entrada.  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<claimsAuthenticationManager >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|tipo|Especifica um tipo personalizado que deriva de <xref:System.Security.Claims.ClaimsAuthenticationManager> classe. Para obter mais informações sobre como especificar o `type` de atributo, consulte [referências de tipo personalizado].|  
  
### <a name="child-elements"></a>Elementos filho  
 Se não houver nenhum `type` atributo, ou se o `type` as referências ao atributo o <xref:System.Security.Claims.ClaimsAuthenticationManager> classe, o `<claimsAuthenticationManager>` elemento não tem elementos filho; no entanto, as classes derivadas de <xref:System.Security.Claims.ClaimsAuthenticationManager> podem definir elementos de configuração filho.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Especifica as configurações de identidade de nível de serviço.|  
  
## <a name="remarks"></a>Comentários  
 O comportamento padrão fornecido por meio de <xref:System.Security.Claims.ClaimsAuthenticationManager> classe exibe as declarações de entrada. Se nenhum `type` atributo for especificado ou se o `type` atributo especifica o <xref:System.Security.Claims.ClaimsAuthenticationManager> classe, o `<claimsAuthenticationManager>` elemento não tem elementos filho. Você pode especificar o `type` atributo para registrar um tipo derivado de <xref:System.Security.Claims.ClaimsAuthenticationManager> classe para implementar o comportamento personalizado. Classes derivadas podem dar suporte a configuração por meio de elementos filho de `<claimsAuthenticationManager>` elemento, substituindo o <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> método para lidar com esses elementos. O esquema definido para os elementos filho é até o designer de classe.  
  
 O `<claimsAuthenticationManager>` elemento define o <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> propriedade.  
  
## <a name="example"></a>Exemplo  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</microsoft.identityModel>  
```
