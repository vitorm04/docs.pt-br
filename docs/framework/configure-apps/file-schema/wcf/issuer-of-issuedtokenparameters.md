---
title: '&lt;emissor&gt; de &lt;issuedTokenParameters&gt;'
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: 459f2f43d3ef9426fbce7e0a0dd067250eb2cc4b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltissuergt-of-ltissuedtokenparametersgt"></a>&lt;emissor&gt; de &lt;issuedTokenParameters&gt;
Especifica o Token de segurança Service (STS) que emite tokens de segurança.  
  
 \<system.serviceModel>  
\<associações >  
\<customBinding>  
\<associação >  
\<segurança >  
\<issuedTokenParameters >  
\<emissor >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<issuer address="Uri" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem os elementos pai de atributos e elementos filho  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|endereço|Cadeia de caracteres obrigatória. A URL do STS.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<cabeçalhos >](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|Uma coleção de cabeçalhos de endereço para o construtor pode criar os pontos de extremidade.|  
|[\<identity>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Ao usar um token emitido, especifica configurações que permitem que o cliente autenticar o servidor.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|Especifica o token emitido atual.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Autenticação e identidade de serviço](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Federação e tokens emitidos](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [Recursos de segurança com associações personalizadas](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [Federação e tokens emitidos](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Estendendo associações](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Associações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Como criar uma associação personalizada utilizando o SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Segurança de associação personalizada](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
