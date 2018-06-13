---
title: '&lt;audienceUris&gt;'
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 7415cb3f1792d2de566161ae6c348ef591b4a0c3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755988"
---
# <a name="ltaudienceurisgt"></a>&lt;audienceUris&gt;
Especifica o conjunto de URIs que são aceitáveis identificadores da terceira parte confiável (RP). Tokens não serão aceitas, a menos que eles têm o escopo para uma das URIs de audiência permitidas.  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<securityTokenHandlerConfiguration >  
\<audienceUris >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <audienceUris mode=xs:string>  
          <add value=xs:string />  
          <clear />  
          <remove value=xs:string />  
        </audienceUris>  
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
|modo|Um <xref:System.IdentityModel.Selectors.AudienceUriMode> valor que especifica se a restrição de público-alvo deve ser aplicada a um token de entrada. Os valores possíveis são "Sempre", "Nunca" e "BearerKeyOnly". O padrão é "Sempre". Opcional.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`<add value=xs:string>`|Adiciona o URI especificado pelo `value` atributo à coleção audienceUris. O atributo `value` é necessário. O URI diferencia maiusculas de minúsculas.|  
|`<clear>`|Limpa a coleção de audienceUris. Todos os identificadores são removidos da coleção.|  
|`<remove value=xs:string>`|Remove o URI especificado pelo `value` atributo da coleção audienceUris. O atributo `value` é necessário. O URI diferencia maiusculas de minúsculas.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Fornece manipuladores de token de configuração para uma coleção de segurança.|  
  
## <a name="remarks"></a>Comentários  
 Por padrão, a coleção está vazia. Use `<add>`, `<clear>`, e `<remove>` elementos para modificar a coleção. <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> e <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objetos usam os valores no conjunto de URI público para configurar quaisquer permitido público restrições URI <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objetos.  
  
 O `<audienceUris>` elemento é representado pela <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> classe. Um URI individual adicionado à coleção é representado pela <xref:System.IdentityModel.Configuration.AudienceUriElement> classe.  
  
> [!NOTE]
>  O uso do `<audienceUris>` como um elemento filho do [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elemento foi substituído, mas ainda há suporte para compatibilidade com versões anteriores. Configurações de `<securityTokenHandlerConfiguration>` elemento substituem aquelas no `<identityConfiguration>` elemento.  
  
## <a name="example"></a>Exemplo  
 O XML a seguir mostra como configurar o URIs de público aceitáveis para um aplicativo. Este exemplo configura um URI único. Tokens de escopo para esse URI serão aceito, todos os outros serão rejeitados.  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
