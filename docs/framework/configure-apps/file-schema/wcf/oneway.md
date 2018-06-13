---
title: '&lt;Unidirecional&gt;'
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: f9a5631501b3879463606f526485314efd5eff2b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746716"
---
# <a name="ltonewaygt"></a>&lt;Unidirecional&gt;
Permite que o roteamento de pacotes e o uso de métodos unidirecionais para uma associação personalizada.  
  
 \<system.serviceModel>  
\<associações >  
\<customBinding>  
\<associação >  
\<oneWay >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<oneWay packetRoutable="Boolean">  
        <channelPoolSettings  
           idleTimeout"TimeSpan"  
          leaseTimeout"TimeSpan"  
          maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
```xml  
</oneWay>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`packetRoutable`|Um valor booleano que especifica se o roteamento de pacotes está habilitado. O padrão é `false`.|  
|`MaxAcceptedChannels`|Um inteiro que especifica o número máximo de canais que podem ser aceitos.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<channelPoolSettings >](../../../../../docs/framework/configure-apps/file-schema/wcf/channelpoolsettings.md)|Um <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> objeto que contém as propriedades do pool de canal para o canal atual.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<associação >](../../../../../docs/framework/misc/binding.md)|Define todos os recursos de associação da associação personalizada.|  
  
## <a name="remarks"></a>Comentários  
 Para habilitar o roteamento de pacotes, uma camada de conversão unidirecional é necessária, que fornece este elemento. Um usuário pode criar uma associação personalizada que camadas essa ligação por um transporte de reconhecimento de sessão ou de solicitação-resposta para torná-lo pacote roteável. Esse elemento também é útil quando você deseja expor métodos unidirecionais de forma mais nativo. Mais transformações podem ser aplicadas por essa camada, como Duplex compostos e sistema de mensagens confiável.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>  
 <xref:System.ServiceModel.Configuration.OneWayElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Estendendo associações](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Associações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
