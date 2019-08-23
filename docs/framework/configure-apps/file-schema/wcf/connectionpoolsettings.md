---
title: <connectionPoolSettings>
ms.date: 03/30/2017
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
ms.openlocfilehash: 3c8d905a04f8f6d7ecff9b0ef9e7d3c8afa727e3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925969"
---
# <a name="connectionpoolsettings"></a>\<connectionPoolSettings>
Especifica configurações de pool de conexões adicionais para uma associação de pipe nomeado.  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<> de associação  
\<namePipeTransport>  
\<connectionPoolSettings>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`groupName`|Uma cadeia de caracteres que define o nome do pool de conexões usado para canais de saída. No modo de fluxo, as conexões não são compartilhadas, o que significa que o pool de conexões está desabilitado. O padrão é uma cadeia de caracteres "padrão". Você pode modificar esse valor para isolar as conexões de um cliente específico em grupos separados.|  
|`idleTimeout`|Um positivo <xref:System.TimeSpan> que especifica o tempo máximo que a conexão pode ficar ociosa antes de ser desconectada. O padrão é 00:02:00.|  
|`maxOutboundConnectionsPerEndpoint`|Um inteiro positivo que especifica o número máximo de conexões com um ponto de extremidade remoto iniciado pelo serviço. As conexões que excedem o limite são enfileiradas até que um espaço abaixo do limite fique disponível. O `idleTimeout` limita a duração em que as conexões permanecem enfileiradas antes que uma exceção seja lançada. O padrão é 10.<br /><br /> Esse atributo limita o número de conexões ativas simultâneas do cliente para um ponto de extremidade de serviço específico. Se esse valor for excedido por ter mais conexões de cliente ativas, o serviço poderá parecer sem resposta ao cliente. Nesse caso, esse valor deve ser ajustado para exceder o número máximo de conexões de cliente simultâneas esperadas para um ponto de extremidade específico.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<namedPipeTransport>](namedpipetransport.md)|Define um transporte que faz com que um canal transfira mensagens usando pipes nomeados.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Transportes](../../../wcf/feature-details/transports.md)
- [Escolhendo um transporte](../../../wcf/feature-details/choosing-a-transport.md)
- [Associações](../../../wcf/bindings.md)
- [Estendendo associações](../../../wcf/extending/extending-bindings.md)
- [Associações personalizadas](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
