---
title: '&lt;channelPoolSettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 44e79c7af470cefead8bcfb0ef96606ecde30383
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltchannelpoolsettingsgt"></a>&lt;channelPoolSettings&gt;
Especifica as configurações de pool do canal para uma associação personalizada.  
  
 \<System. ServiceModel >  
\<associações >  
\<customBinding >  
\<associação >  
\<oneWay >  
\<channelPoolSettings >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<channelPoolSettings  
    idleTimeout"TimeSpan"  
        leaseTimeout"TimeSpan"  
    maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`idleTimeout`|Um positivo <xref:System.TimeSpan> que especifica o tempo máximo de canais no pool podem ficar ociosos antes de ser desconectada. O padrão é 00:02:00.|  
|`leaseTimeout`|Um <xref:System.TimeSpan> que especifica o intervalo de tempo após o qual um canal, quando retornado para o pool está fechado. O padrão é 00:10:00.|  
|`maxOutboundChannelsPerEndpoint`|Um inteiro positivo que especifica o número máximo de canais que podem ser armazenados no pool para cada ponto de extremidade remoto. O padrão é 10.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<oneWay >](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)|Permite que o roteamento de pacotes para uma associação personalizada.|  
  
## <a name="remarks"></a>Comentários  
 As cotas são usadas como um mecanismo de política para evitar o consumo de recursos em excesso. Elas impedem ataques de negação de serviço (DOS) que são mal-intencionados ou não intencionais. Use esse elemento ao definir cotas de canal em um canal personalizado.  
  
 `ChannelPoolSettings`Especifica as cotas de três:  
  
-   O `idleTimeout` cota é usada para reduzir os ataques de negação de serviço (DOS) no servidor que se baseiam na prender os recursos por um longo período de tempo. No cliente, definir o valor correto pode aumentar a confiabilidade de conexão com o serviço. O valor padrão baseia-se em uma forma prudente modesta alocação de recursos. Ele é adequado para um ambiente de desenvolvimento e cenários de instalação pequeno. Os administradores de serviço devem examinar o valor se uma instalação está ficando sem recursos ou se as conexões estão sendo limitadas apesar da disponibilidade dos recursos adicionais.  
  
-   O `leaseTimeout` cota é usada para integração com balanceadores de carga e para melhorar a confiabilidade. O valor padrão baseia-se em uma alocação de recursos de conservadora. Ele é adequado para um ambiente de desenvolvimento e cenários de instalação pequeno. Os administradores de serviço devem examinar o valor se uma instalação está ficando sem recursos ou se as conexões estão sendo limitadas apesar da disponibilidade dos recursos adicionais.  
  
-   O `maxOutboundChannelsPerEndpoint` cota define limites de cache no servidor e o cliente e é usada para melhorar a confiabilidade. O valor padrão baseia-se em uma forma prudente modesta alocação de recursos que é adequada para um ambiente de desenvolvimento e cenários de instalação pequeno. Os administradores de serviço devem examinar o valor se uma instalação está ficando sem recursos ou se as conexões estão sendo limitadas apesar da disponibilidade dos recursos adicionais.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>  
 <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>  
 <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [\<oneWay >](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)  
 [Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)  
 [Estendendo associações](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Associações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
