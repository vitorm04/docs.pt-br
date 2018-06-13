---
title: '&lt;resolver&gt;'
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: f29c34f53a8bdaee4b30c72bb5d764ae3935fe7a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749017"
---
# <a name="ltresolvergt"></a>&lt;resolver&gt;
Especifica a ID de um resolvedor de pares que é usado para resolver um par de malha para um conjunto de endereços de nó par que representa vários nós que participam na malha.  
  
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
|`mode`|Uma cadeia de caracteres que especifica se a instância do resolvedor peer associada a esse serviço é específico PNRP, um resolvedor personalizado ou determinado automaticamente. Esse atributo é do tipo <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.|  
|`referralPolicy`|Uma cadeia de caracteres que especifica a forma como referências são compartilhadas entre pares. Esse atributo é do tipo <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<cabeçalhos >](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|Especifica configurações para um serviço resolvedor de pares personalizado.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<associação >](../../../../../docs/framework/misc/binding.md)|Define todos os recursos de associação do [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).|  
  
## <a name="remarks"></a>Comentários  
 Um resolvedor de nome de ponto a ponto é um serviço de descoberta usado pelos canais de ponto a ponto para localizar nós que participam de uma malha de pontos de ponto a ponto. Ele também é usado para "Registrar" de um nó com uma malha de ponto a ponto, o mecanismo pelo qual o nó par torna-se e conhecida da malha ponto a ponto. Para obter mais informações sobre o resolvedor peer, consulte [resolvedor Peer](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.PeerResolver>  
 <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>  
 <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>  
 <xref:System.ServiceModel.Configuration.PeerResolverElement>  
 [Resolvedores pares](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)  
 [Adicionando um resolvedor personalizado para um aplicativo PeerChannel](http://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419)
