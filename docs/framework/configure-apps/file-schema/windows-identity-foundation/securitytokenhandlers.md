---
title: '&lt;securityTokenHandlers&gt;'
ms.date: 03/30/2017
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
author: BrucePerlerMS
ms.openlocfilehash: e63f02add81495e474b59b6c5cc090bd69add3d2
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47082975"
---
# <a name="ltsecuritytokenhandlersgt"></a>&lt;securityTokenHandlers&gt;
Especifica uma coleção de manipuladores de token de segurança que são registrados com o ponto de extremidade.  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|name|Especifica o nome de uma coleção de manipulador de token. Os únicos valores reconhecidos pela estrutura são "ActAs" e "OnBehalfOf". Se as coleções de manipuladores de token são especificadas com qualquer um desses nomes, a coleção será usada ao processamento ActAs ou OnBehalfOf tokens, respectivamente.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|Adiciona um manipulador de token de segurança para a coleção de manipulador de token.|  
|[\<clear>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md)|Limpa todos os manipuladores de token de segurança da coleção de manipulador de token.|  
|[\<remove>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md)|Remove um manipulador de token de segurança da coleção de manipulador de token.|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Fornece configuração para a coleção de manipuladores de token.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Especifica as configurações de identidade de nível de serviço.|  
  
## <a name="remarks"></a>Comentários  
 Você pode especificar uma ou mais coleções nomeadas de manipuladores de token de segurança em uma configuração de serviço. Você pode especificar um nome para uma coleção usando o `name` atributo. Os únicos nomes que as alças da estrutura são "ActAs" e "OnBehalfOf". Se existirem manipuladores nessas coleções, eles são usados por um serviço de token de segurança (STS) em vez dos manipuladores padrão durante o processamento `ActAs` e `OnBehalfOf` tokens.  
  
 Por padrão, a coleção é preenchida com os seguintes tipos de manipulador: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, e <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>. Você pode modificar a coleção usando o `<add>`, `<remove>`, e `<clear>` elementos. Você deve garantir que apenas um único manipulador de qualquer tipo específico existe na coleção. Por exemplo, se você derivar de um manipulador de <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe, ou seu manipulador ou o <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> podem ser configurados em uma única coleção, mas não ambos.  
  
 Use o `<securityTokenHandlerConfiguration>` elemento para especificar as definições de configuração para os manipuladores na coleção. As configurações especificadas por meio desse elemento substituem aquelas especificadas no serviço por meio de [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elemento. Alguns manipuladores (incluindo vários tipos de manipulador interno de) podem dar suporte a configuração adicional por meio de um elemento filho do `<add>` elemento. As configurações especificadas em um manipulador substituem configurações equivalentes especificadas na coleção ou o serviço.
