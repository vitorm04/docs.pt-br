---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: a54fc2cea84bb9d08a9725d846fe38efd7b5475a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152743"
---
# <a name="claimsauthenticationmanager"></a>\<> de autenticação de autenticação
Registra um gerente de autenticação de sinistros para as reclamações recebidas.  
  
[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de configuração de identidade**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthenticationManager>**  
  
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
|type|Especifica um tipo personalizado que <xref:System.Security.Claims.ClaimsAuthenticationManager> deriva da classe. Para obter mais informações `type` sobre como especificar o atributo, consulte [Referências de tipo personalizado].|  
  
### <a name="child-elements"></a>Elementos filho  
 Se não `type` houver atributo, `type` ou se <xref:System.Security.Claims.ClaimsAuthenticationManager> o `<claimsAuthenticationManager>` atributo fizer referência à classe, o elemento não leva elementos da criança; no entanto, <xref:System.Security.Claims.ClaimsAuthenticationManager> classes derivadas podem definir elementos de configuração filho.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<>de configuração de identidade](identityconfiguration.md)|Especifica as configurações de identidade em nível de serviço.|  
  
## <a name="remarks"></a>Comentários  
 O comportamento padrão fornecido <xref:System.Security.Claims.ClaimsAuthenticationManager> através da classe ecoa as reivindicações recebidas. Se `type` nenhum atributo for `type` especificado ou <xref:System.Security.Claims.ClaimsAuthenticationManager> se `<claimsAuthenticationManager>` o atributo especificar a classe, o elemento não levará elementos da criança. Você pode `type` especificar o atributo para <xref:System.Security.Claims.ClaimsAuthenticationManager> registrar um tipo derivado da classe para implementar comportamento personalizado. Classes derivadas podem suportar a `<claimsAuthenticationManager>` configuração através <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> de elementos infantis do elemento, substituindo o método para lidar com esses elementos. O esquema definido para os elementos infantis cabe ao designer da classe.  
  
 O `<claimsAuthenticationManager>` elemento <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> define a propriedade.  
  
## <a name="example"></a>Exemplo  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>
    </identityConfiguration>  
</system.identityModel>  
```
