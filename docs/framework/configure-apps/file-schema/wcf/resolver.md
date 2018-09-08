---
title: '&lt;resolver&gt;'
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: 48b6b6ca315f7ab63a8f7a64b97167fa04fe1e4e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44180794"
---
# <a name="ltresolvergt"></a>&lt;resolver&gt;
Especifica a ID de malha de um resolvedor de pares que é usado para resolver um par para um conjunto de endereços de nó par que representa vários nós que participam da malha.  
  
 \<system.ServiceModel>  
\<associações >  
\<netPeerBinding>  
\<associação >  
\<resolver>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"  
   referralPolicy="DoNotShare/Service/Share">  
</resolver>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`mode`|Uma cadeia de caracteres que especifica se a instância do resolvedor de par associada a esse serviço é PNRP específico, um resolvedor personalizado ou determinado automaticamente. Esse atributo é do tipo <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.|  
|`referralPolicy`|Uma cadeia de caracteres que especifica a forma como referências são compartilhadas entre pares. Esse atributo é do tipo <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<cabeçalhos >](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|Especifica configurações para um serviço de resolvedor de pares personalizado.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<associação >](../../../../../docs/framework/misc/binding.md)|Define todos os recursos de associação do [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).|  
  
## <a name="remarks"></a>Comentários  
 Um resolvedor de pares nome é um serviço de descoberta usado pelos canais pares para localizar nós que participam de uma malha ponto a ponto a ponto a ponto. Ele também é usado para "Registrar" um nó com uma malha ponto a ponto, o mecanismo pelo qual o nó par se torna conhecidos e estão disponíveis na malha ponto a ponto. Para obter mais informações sobre os resolvedores de pares, consulte [resolvedores de pares](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.PeerResolver>  
 <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>  
 <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>  
 <xref:System.ServiceModel.Configuration.PeerResolverElement>  
 [Resolvedores pares](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)  
 [Adicionando um resolvedor personalizado a um aplicativo PeerChannel](https://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419)
