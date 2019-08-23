---
title: <oneWay>
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: f4a9422f4385e37a61ec85d680fcf7743a57bc0c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932940"
---
# <a name="oneway"></a>\<oneWay>
Habilita o roteamento de pacotes e o uso de métodos unidirecionais para uma associação personalizada.  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<> de associação  
\<oneWay>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpoint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`packetRoutable`|Um valor booliano que especifica se o roteamento de pacotes está habilitado. O padrão é `false`.|  
|`MaxAcceptedChannels`|Um inteiro que especifica o número máximo de canais que podem ser aceitos.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<channelPoolSettings>](channelpoolsettings.md)|Um <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> objeto que contém as propriedades do pool de canais para o canal atual.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<binding>](../../../misc/binding.md)|Define todos os recursos de associação da associação personalizada.|  
  
## <a name="remarks"></a>Comentários  
 Para habilitar o roteamento de pacotes, é necessária uma camada de conversão unidirecional, que esse elemento fornece. Um usuário pode criar uma associação personalizada que faz a ligação por camadas em um transporte de solicitação ou resposta de sessão para torná-lo roteável. Esse elemento também é útil quando você deseja expor métodos unidirecionais de maneira mais nativa. Mais transformações podem ser aplicadas nessa camada, como Composite duplex e mensagens confiáveis.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Associações](../../../wcf/bindings.md)
- [Estendendo associações](../../../wcf/extending/extending-bindings.md)
- [Associações personalizadas](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
