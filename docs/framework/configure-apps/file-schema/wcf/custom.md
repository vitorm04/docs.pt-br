---
title: '&lt;custom&gt;'
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: 5180b8866d8b0155a8683ab9cb6135c26f696929
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54734981"
---
# <a name="ltcustomgt"></a>&lt;custom&gt;
Especifica configurações para um serviço de resolvedor de pares personalizado.  
  
\<system.serviceModel>  
\<bindings>  
\<netPeerBinding>  
\<binding>  
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
|`address`|Um URI que especifica o endereço do ponto de extremidade do nó par que hospeda o serviço de resolvedor de pares personalizado.|  
|`resolverType`|Uma cadeia de caracteres que especifica o tipo de serviço resolvedor de pares personalizado.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<identity>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Especifica a identidade para os resolvedores de pares personalizados configurados com este elemento. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.IdentityElement>.|  
|[\<headers>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|Uma coleção de cabeçalho de endereço usado para mensagens SOAP manipuladas pelo resolvedor de pares personalizado.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<resolver>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|Um resolvedor de pares que é usado para resolver um par de ID de malha para um conjunto de endereços de nó par que representa vários nós que participam da malha.|  
  
## <a name="remarks"></a>Comentários  
 Este elemento define as configurações básicas para um serviço de resolvedor de pares personalizado, incluindo o endereço do ponto de extremidade do par que hospeda o serviço e quaisquer configurações de associação específica. Para obter mais informações sobre a criação de um resolvedor personalizado, consulte [adicionando um resolvedor personalizado a um aplicativo PeerChannel](https://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419).  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>
- <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>
- <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>
- <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>
- [Resolvedores pares](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
- [Adicionando um resolvedor personalizado a um aplicativo PeerChannel](https://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419)
