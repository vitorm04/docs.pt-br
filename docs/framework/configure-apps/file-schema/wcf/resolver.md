---
title: <resolver>
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: f3d4b049afe55fb9fb80cbad56c49e8ec13e60db
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/06/2019
ms.locfileid: "55758736"
---
# <a name="resolver"></a>\<resolver>
Especifica a ID de malha de um resolvedor de pares que é usado para resolver um par para um conjunto de endereços de nó par que representa vários nós que participam da malha.  
  
 \<system.ServiceModel>  
\<bindings>  
\<netPeerBinding>  
\<binding>  
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
|[\<headers>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|Especifica configurações para um serviço de resolvedor de pares personalizado.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<binding>](../../../../../docs/framework/misc/binding.md)|Define todos os recursos de associação do [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).|  
  
## <a name="remarks"></a>Comentários  
 Um resolvedor de pares nome é um serviço de descoberta usado pelos canais pares para localizar nós que participam de uma malha ponto a ponto a ponto a ponto. Ele também é usado para "Registrar" um nó com uma malha ponto a ponto, o mecanismo pelo qual o nó par se torna conhecidos e estão disponíveis na malha ponto a ponto. Para obter mais informações sobre os resolvedores de pares, consulte [resolvedores de pares](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.PeerResolver>
- <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>
- <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>
- <xref:System.ServiceModel.Configuration.PeerResolverElement>
- [Resolvedores pares](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
- [Adicionando um resolvedor personalizado a um aplicativo PeerChannel](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))
