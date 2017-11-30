---
title: '&lt;securityTokenHandlers&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 3151ec3511bca598e5aaabc72b821bdd3aed0b7b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltsecuritytokenhandlersgt"></a>&lt;securityTokenHandlers&gt;
Especifica uma coleção de manipuladores de token de segurança que são registrados com o ponto de extremidade.  
  
 \<System. IdentityModel >  
\<identityConfiguration >  
\<securityTokenHandlers >  
  
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
|name|Especifica o nome de uma coleção de manipulador de token. Os únicos valores reconhecidos pela estrutura são "ActAs" e "OnBehalfOf". Se o manipulador de token coleções é especificadas com qualquer um desses nomes, a coleção será usada ao processamento ActAs ou OnBehalfOf tokens respectivamente.|  
  
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
 Você pode especificar uma ou mais coleções de manipuladores de token de segurança nomeadas em uma configuração de serviço. Você pode especificar um nome para uma coleção usando o `name` atributo. Apenas os nomes que lida com a estrutura são "ActAs" e "OnBehalfOf". Se existirem manipuladores nessas coleções, são usadas por um serviço de token de segurança (STS) em vez do manipulador padrão durante o processamento `ActAs` e `OnBehalfOf` tokens.  
  
 Por padrão, a coleção é preenchida com os seguintes tipos de manipulador: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, e <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>. Você pode modificar a coleção usando o `<add>`, `<remove>`, e `<clear>` elementos. Certifique-se de que apenas um único manipulador de qualquer tipo específico existe na coleção. Por exemplo, se você derivar um manipulador do <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe, ou o manipulador ou <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> pode ser configurado em uma única coleção, mas não ambos.  
  
 Use o `<securityTokenHandlerConfiguration>` elemento para especificar configurações para os manipuladores na coleção. As configurações especificadas por meio desse elemento substituem aquelas especificadas no serviço por meio de [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elemento. Alguns manipuladores (incluindo vários tipos de manipulador internos) podem dar suporte a configuração adicional por meio de um elemento filho do `<add>` elemento. As configurações especificadas em um manipulador de substituem configurações equivalentes especificadas na coleção ou o serviço.
