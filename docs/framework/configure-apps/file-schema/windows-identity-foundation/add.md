---
title: <add>
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
ms.openlocfilehash: 34643d10ef1ed2e87152e5013634e62859e0594e
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/06/2019
ms.locfileid: "55759477"
---
# <a name="add"></a>\<add>
Adiciona o manipulador de token de segurança especificado à coleção de manipulador de token.  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<add>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type=xs:string>  
        <optionalConfigurationElement>  
        </optionalConfigurationElement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|tipo|O nome do tipo CLR do manipulador de token a ser adicionado. Para obter mais informações sobre como especificar o `type` atributo, consulte [referências de tipo personalizado](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|Fornece configuração para o <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> classe, o <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe ou uma classe derivada de qualquer uma dessas classes.|  
|[\<sessionTokenRequirement>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessiontokenrequirement.md)|Fornece configuração para o <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> classe ou classes derivadas.|  
|[\<userNameSecurityTokenHandlerRequirement>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/usernamesecuritytokenhandlerrequirement.md)|Fornece configuração para o <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> classe ou classes derivadas.|  
|[\<x509SecurityTokenHandlerRequirement>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/x509securitytokenhandlerrequirement.md)|Fornece configuração opcional para o <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> classe ou classes derivadas.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|Especifica uma coleção de manipuladores de token de segurança que são registrados com o ponto de extremidade.|  
  
## <a name="remarks"></a>Comentários  
 O `<add>` elemento pode levar a um único elemento filho que especifica a configuração para o manipulador de token. Isso depende se a classe de manipulador referenciado por meio de `type` atributo do `<add>` elemento oferece suporte para esse recurso. Classes de manipulador de token que fornecem esse recurso devem expor um construtor que aceita um <xref:System.Xml.XmlElement> objeto.  
  
```  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 Várias das classes de manipulador de token de segurança internas fornecem essa funcionalidade. Essas classes são <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, e <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.  
  
> [!IMPORTANT]
>  A coleção de manipulador de token só pode conter um único manipulador de qualquer tipo. Isso significa, por exemplo, que se você deseja adicionar um manipulador que é derivado do <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe à coleção, você deve primeiro remover o <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, que está presente por padrão, da coleção. Você pode usar o [ \<remover >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md) elemento para remover um único manipulador de coleção ou use o [ \<limpar >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md) elemento a ser removido de todos os manipuladores da coleção.  
  
 As configurações especificadas em um manipulador de substituem configurações equivalentes especificadas na coleção de manipulador de token sob o [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) elemento e às especificadas no nível de serviço em o [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elemento.  
  
## <a name="example"></a>Exemplo  
 O XML a seguir mostra o uso do `<add>` e `<remove>` elementos para substituir o manipulador de token de sessão padrão por um manipulador de token de sessão personalizadas. O XML é obtido a `ClaimsAwareWebFarm` exemplo.  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
