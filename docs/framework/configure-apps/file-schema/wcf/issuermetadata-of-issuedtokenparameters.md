---
title: '&lt;issuerMetadata&gt; de &lt;issuedTokenParameters&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9e8df1ffb74c59bfed2b9fa2f1e87e7669fe3ad9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltissuermetadatagt-of-ltissuedtokenparametersgt"></a>&lt;issuerMetadata&gt; de &lt;issuedTokenParameters&gt;
\<System. ServiceModel >  
\<associações >  
\<customBinding >  
\<associação >  
\<segurança >  
\<issuedTokenParameters >  
\<issuerMetadata >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<issuerMetaData address=String"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|endereço|Necessário. Uma cadeia de caracteres que especifica o endereço do ponto de extremidade. O endereço deve ser um URI absoluto. O valor padrão é uma cadeia de caracteres vazia.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<cabeçalhos >](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|Uma coleção de cabeçalhos de endereço.|  
|[\<identidade >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Uma identidade que permite a autenticação de um ponto de extremidade por outros pontos de extremidade de troca de mensagens com ele.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<issuedTokenParameters >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|Especifica os parâmetros de um token de segurança emitido em um cenário de segurança federada.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Autenticação e identidade de serviço](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Federação e Tokens emitidos](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [Recursos de segurança com associações personalizadas](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [Federação e Tokens emitidos](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)  
 [Estendendo associações](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Associações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Como: criar uma associação personalizada utilizando o SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Segurança de associação personalizada](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
