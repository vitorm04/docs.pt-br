---
title: '&lt;peerTransport&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7c9c01e997e3ba804eae3036e94f2e2e1b951b25
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltpeertransportgt"></a>&lt;peerTransport&gt;
Define um transporte de par para uma associação personalizada.  
  
 \<System. ServiceModel >  
\<associações >  
\<customBinding >  
\<associação >  
\<peerTransport >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<peerTransport   
    listenIpAddress="String"  
    maxBufferPoolSize="Integer"  
    maxReceivedMessageSize="Integer"  
    port="Integer"  
        <security>  
    </security>  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|listenIpAddress|Uma cadeia de caracteres que especifica um endereço IP no qual o nó par escutará mensagens TCP. O padrão é `null`.|  
|maxBufferPoolSize|Um inteiro positivo que especifica o tamanho máximo do pool de buffers. O padrão é 524288.<br /><br /> Muitas partes do WCF usam buffers. Criação e destruição de buffers de cada vez que elas são usadas são caro e coleta de lixo para buffers também é cara. Com os pools de buffer, usar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar. Portanto, a sobrecarga na criação e destruição de buffers é evitada.|  
|maxReceivedMessageSize|Um inteiro positivo que define o tamanho máximo em bytes, incluindo cabeçalhos. O remetente de uma mensagem recebe uma falha SOAP quando a mensagem é muito grande para o destinatário. O receptor descartará a mensagem e cria uma entrada do evento no log de rastreamento. O padrão é 65536.|  
|porta|Um inteiro que especifica a porta de interface de rede no qual esta associação irá processar mensagens TCP de canal par. Esse valor deve estar entre <xref:System.Net.IPEndPoint.MinPort> e <xref:System.Net.IPEndPoint.MaxPort>. O padrão é 0.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<segurança >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|Define as configurações de segurança para este transporte. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerSecurityElement>.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<associação >](../../../../../docs/framework/misc/binding.md)|Define todos os recursos de associação da associação personalizada.|  
  
## <a name="remarks"></a>Comentários  
 Esse transporte não pode ser usado com contratos com operações de solicitação/resposta.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.PeerTransportElement>  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Transportes](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [Selecionando um transporte](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)  
 [Estendendo associações](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Associações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
