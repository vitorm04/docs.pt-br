---
title: <channelPoolSettings>
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: ca1f680e2de67984dfcec49b3d262799000a2625
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102577"
---
# <a name="channelpoolsettings"></a>\<channelPoolSettings>
Especifica as configurações de pool de canal para uma associação personalizada.  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<binding>  
\<oneWay>  
\<channelPoolSettings>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<channelPoolSettings idleTimeout="TimeSpan"
                     leaseTimeout="TimeSpan"
                     maxOutboundConnectionsPerEndpopint="Integer" />
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`idleTimeout`|Um positivo <xref:System.TimeSpan> que especifica o tempo máximo de canais no pool podem ficar ociosos antes de ser desconectada. O padrão é 00:02:00.|  
|`leaseTimeout`|Um <xref:System.TimeSpan> que especifica o intervalo de tempo após o qual um canal, quando retornado para o pool está fechado. O padrão é 10:00:00.|  
|`maxOutboundChannelsPerEndpoint`|Um inteiro positivo que especifica o número máximo de canais que podem ser armazenados no pool para cada ponto de extremidade remoto. O padrão é 10.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<oneWay>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)|Habilita o roteamento de pacotes para uma associação personalizada.|  
  
## <a name="remarks"></a>Comentários  
 As cotas são usadas como um mecanismo de diretiva para impedir o consumo de recursos em excesso. Elas impedir ataques de negação de serviço (DOS) que são mal-intencionados ou não intencionais. Use esse elemento ao definir cotas de canal em um canal personalizado.  
  
 `ChannelPoolSettings` Especifica as cotas de três:  
  
-   O `idleTimeout` cota é usada para reduzir os ataques de negação de serviço (DOS) no servidor que dependem de prender os recursos por um longo período de tempo. No cliente, definir o valor correto pode aumentar a confiabilidade de conexão com o serviço. O valor padrão se baseia em uma forma prudente modesta alocação de recursos. Ele é adequado para cenários de instalação pequeno e um ambiente de desenvolvimento. Os administradores de serviço devem examinar o valor se uma instalação está ficando sem recursos ou se as conexões estão sendo limitadas, apesar da disponibilidade de recursos adicionais.  
  
-   O `leaseTimeout` cota é usada para integração com os balanceadores de carga e aumentar a confiabilidade. O valor padrão se baseia em uma alocação conservadora de recursos. Ele é adequado para cenários de instalação pequeno e um ambiente de desenvolvimento. Os administradores de serviço devem examinar o valor se uma instalação está ficando sem recursos ou se as conexões estão sendo limitadas, apesar da disponibilidade de recursos adicionais.  
  
-   O `maxOutboundChannelsPerEndpoint` cota define limites de cache no servidor e o cliente e é usada para melhorar a confiabilidade. O valor padrão se baseia em uma forma prudente modesta alocação de recursos que é adequada para cenários de instalação pequeno e um ambiente de desenvolvimento. Os administradores de serviço devem examinar o valor se uma instalação está ficando sem recursos ou se as conexões estão sendo limitadas, apesar da disponibilidade de recursos adicionais.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
- <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<oneWay>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)
- [Associações](../../../../../docs/framework/wcf/bindings.md)
- [Estendendo associações](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Associações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
