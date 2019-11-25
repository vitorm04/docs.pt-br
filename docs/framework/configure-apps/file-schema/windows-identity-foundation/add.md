---
title: <add>
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
ms.openlocfilehash: 83ba51cbbd5100bf7412f9914a270cac88f7faa1
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973811"
---
# <a name="add"></a>\<add>
Adiciona o manipulador de token de segurança especificado à coleção de manipulador de token.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<adicionar >**  
  
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
|tipo|O nome do tipo CLR do manipulador de token a ser adicionado. Para obter mais informações sobre como especificar o atributo `type`, consulte [referências de tipo personalizado](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement >](samlsecuritytokenrequirement.md)|Fornece a configuração para a classe <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, a classe <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> ou uma classe derivada de qualquer uma dessas classes.|  
|[\<sessionTokenRequirement >](sessiontokenrequirement.md)|Fornece a configuração para a classe de <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> ou classes derivadas.|  
|[\<userNameSecurityTokenHandlerRequirement >](usernamesecuritytokenhandlerrequirement.md)|Fornece a configuração para a classe de <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> ou classes derivadas.|  
|[\<x509SecurityTokenHandlerRequirement >](x509securitytokenhandlerrequirement.md)|Fornece a configuração opcional para a classe <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> ou classes derivadas.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<securityTokenHandlers >](securitytokenhandlers.md)|Especifica uma coleção de manipuladores de token de segurança que são registrados com o ponto de extremidade.|  
  
## <a name="remarks"></a>Comentários  
 O elemento `<add>` pode pegar um único elemento filho que especifica a configuração para o manipulador de token. Isso depende de se a classe de manipulador referenciada por meio do atributo `type` do elemento `<add>` fornece suporte para esse recurso. Classes de manipulador de token que fornecem esse recurso devem expor um construtor que usa um objeto <xref:System.Xml.XmlElement>.  

```csharp  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 Várias classes internas de manipulador de token de segurança fornecem essa funcionalidade. Essas classes são <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>e <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.  
  
> [!IMPORTANT]
> A coleção de manipuladores de token só pode conter um único manipulador de qualquer tipo específico. Isso significa, por exemplo, que, se você quiser adicionar um manipulador derivado da classe <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> à coleção, primeiro deverá remover o <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, que está presente por padrão, da coleção. Você pode usar o elemento [\<remover >](remove.md) para remover um único manipulador da coleção ou usar o elemento [\<Clear >](clear.md) para remover todos os manipuladores da coleção.  
  
 As configurações especificadas em um manipulador substituem as configurações equivalentes especificadas na coleção do manipulador de tokens no elemento [\<securityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md) e aquelas especificadas no nível de serviço no elemento [\<> identityConfiguration](identityconfiguration.md) .  
  
## <a name="example"></a>Exemplo  
 O XML a seguir mostra o uso dos elementos `<add>` e `<remove>` para substituir o manipulador de token de sessão padrão por um manipulador de token de sessão personalizado. O XML é obtido do exemplo de `ClaimsAwareWebFarm`.  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
