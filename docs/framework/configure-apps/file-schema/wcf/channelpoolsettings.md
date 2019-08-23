---
title: <channelPoolSettings>
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: dd81821c74678cae8602458fe796a72bf5d379e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919551"
---
# <a name="channelpoolsettings"></a>\<channelPoolSettings>
Especifica as configurações de pool de canais para uma associação personalizada.  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<> de associação  
\<oneWay>  
\<channelPoolSettings>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<channelPoolSettings idleTimeout="TimeSpan"
                     leaseTimeout="TimeSpan"
                     maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`idleTimeout`|Um positivo <xref:System.TimeSpan> que especifica o tempo máximo que os canais no pool podem ficar ociosos antes de serem desconectados. O padrão é 00:02:00.|  
|`leaseTimeout`|Um <xref:System.TimeSpan> que especifica o intervalo de tempo após o qual um canal, quando retornado para o pool, é fechado. O padrão é 00:10:00.|  
|`maxOutboundChannelsPerEndpoint`|Um inteiro positivo que especifica o número máximo de canais que podem ser armazenados no pool para cada ponto de extremidade remoto. O padrão é 10.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<oneWay>](oneway.md)|Habilita o roteamento de pacotes para uma associação personalizada.|  
  
## <a name="remarks"></a>Comentários  
 As cotas são usadas como um mecanismo de política para evitar o consumo de recursos excessivos. Eles impedem ataques de DOS (negação de serviço) que são mal-intencionados ou não intencionais. Use este elemento ao definir cotas de canal em um canal personalizado.  
  
 `ChannelPoolSettings`especifica três cotas:  
  
- A `idleTimeout` cota é usada para atenuar ataques de dos (negação de serviço) no servidor que dependem da vinculação de recursos por um longo período de tempo. No cliente, a definição do valor correto pode aumentar a confiabilidade da conexão com o serviço. O valor padrão é baseado em uma alocação conservadormente modesto de recursos. Ele é adequado para um ambiente de desenvolvimento e pequenos cenários de instalação. Os administradores de serviço devem examinar o valor se uma instalação estiver ficando sem recursos ou se as conexões estiverem sendo limitadas, apesar da disponibilidade de recursos adicionais.  
  
- A `leaseTimeout` cota é usada para a integração com balanceadores de carga e para melhorar a confiabilidade. O valor padrão é baseado em uma alocação conservadora de recursos. Ele é adequado para um ambiente de desenvolvimento e pequenos cenários de instalação. Os administradores de serviço devem examinar o valor se uma instalação estiver ficando sem recursos ou se as conexões estiverem sendo limitadas, apesar da disponibilidade de recursos adicionais.  
  
- A `maxOutboundChannelsPerEndpoint` cota define os limites de cache no servidor e no cliente e é usada para melhorar a confiabilidade. O valor padrão é baseado em uma alocação conservadormente modesto de recursos que é adequada para um ambiente de desenvolvimento e pequenos cenários de instalação. Os administradores de serviço devem examinar o valor se uma instalação estiver ficando sem recursos ou se as conexões estiverem sendo limitadas, apesar da disponibilidade de recursos adicionais.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
- <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<oneWay>](oneway.md)
- [Associações](../../../wcf/bindings.md)
- [Estendendo associações](../../../wcf/extending/extending-bindings.md)
- [Associações personalizadas](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
