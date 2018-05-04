---
title: '&lt;custom&gt;'
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: 19f960c14b6171557ec0f353dae34f26d7a7686c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltcustomgt"></a>&lt;custom&gt;
Especifica configurações para um serviço resolvedor de pares personalizado.  
  
\<system.serviceModel>  
\<associações >  
\<netPeerBinding>  
\<associação >  
\<resolver>  
\<custom>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml
<custom address="Uri" 
        resolverType="String">  
  <headers/>  
  <identity/>  
</custom>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`address`|Um URI que especifica o endereço do ponto de extremidade do nó par que hospeda o serviço resolvedor de pares personalizado.|  
|`resolverType`|Uma cadeia de caracteres que especifica o tipo do serviço resolvedor de pares personalizado.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<identity>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Especifica a identidade para os resolvedores de pares personalizado configurados com este elemento. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.IdentityElement>.|  
|[\<cabeçalhos >](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|Uma coleção de cabeçalho de endereço usado para mensagens SOAP manipulados pelo resolvedor de pares personalizado.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<resolver>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|Um resolvedor de pares que é usado para resolver um par de malha ID para um conjunto de endereços de nó par que representa vários nós que participam na malha.|  
  
## <a name="remarks"></a>Comentários  
 Este elemento define as configurações básicas para um serviço resolvedor de pares personalizado, incluindo o endereço do ponto de extremidade do par que hospeda o serviço e as configurações de associação específica. Para obter mais informações sobre a criação de um resolvedor personalizado, consulte [adicionando um resolvedor personalizado para um aplicativo PeerChannel](http://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>  
 <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>  
 <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>  
 <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>  
 [Resolvedores pares](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)  
 [Adicionando um resolvedor personalizado para um aplicativo PeerChannel](http://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419)
