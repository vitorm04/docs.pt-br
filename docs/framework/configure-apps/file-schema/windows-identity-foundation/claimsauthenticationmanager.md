---
title: '&lt;claimsAuthenticationManager&gt;'
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: 0ec7e44363f87e54eae97b70352f520fe87540be
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47074947"
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
|tipo|Especifica um tipo personalizado que deriva de <xref:System.Security.Claims.ClaimsAuthenticationManager> classe. Para obter mais informações sobre como especificar o `type` atributo, consulte [referências de tipo personalizado].|  
  
### <a name="child-elements"></a>Elementos filho  
 Se não houver nenhuma `type` atributo, ou se o `type` as referências ao atributo de <xref:System.Security.Claims.ClaimsAuthenticationManager> classe, o `<claimsAuthenticationManager>` elemento não tem elementos filho; no entanto, as classes derivadas de <xref:System.Security.Claims.ClaimsAuthenticationManager> pode definir os elementos de configuração filho.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Especifica as configurações de identidade de nível de serviço.|  
  
## <a name="remarks"></a>Comentários  
 O comportamento padrão fornecido por meio de <xref:System.Security.Claims.ClaimsAuthenticationManager> classe retorna as declarações de entrada. Se nenhum `type` atributo for especificado ou se o `type` atributo especifica a <xref:System.Security.Claims.ClaimsAuthenticationManager> classe, o `<claimsAuthenticationManager>` elemento não tem elementos filho. Você pode especificar o `type` atributo para registrar um tipo derivado do <xref:System.Security.Claims.ClaimsAuthenticationManager> classe para implementar comportamento personalizado. Classes derivadas podem dar suporte a configuração por meio de elementos filho do `<claimsAuthenticationManager>` elemento, substituindo o <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> método para lidar com esses elementos. O esquema definido para os elementos filho é até o designer da classe.  
  
 O `<claimsAuthenticationManager>` conjuntos de elemento de <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> propriedade.  
  
## <a name="example"></a>Exemplo  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</microsoft.identityModel>  
```
