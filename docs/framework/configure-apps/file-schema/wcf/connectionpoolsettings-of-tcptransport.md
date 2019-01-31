---
title: <connectionPoolSettings> De <tcpTransport>
ms.date: 03/30/2017
ms.assetid: 2fbc3aa7-fcc9-4193-99a3-85d31d60d3f7
ms.openlocfilehash: 4828357f392089be14ee04bc672acce0c0973300
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269257"
---
# <a name="connectionpoolsettings-of-tcptransport"></a>\<connectionPoolSettings> of \<tcpTransport>
Especifica as configurações do pool de conexão adicionais para um transporte TCP.  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<binding>  
\<tcpTransport>  
\<connectionPoolSettings>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        leaseTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpopint="Integer" />
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`groupName`|Uma cadeia de caracteres que define o nome do pool de conexão usado para canais de saída. No modo de streaming, as conexões não são compartilhadas, o que significa que o pooling de conexão está desabilitado. O padrão é uma cadeia de caracteres "default". Você pode modificar esse valor para isolar as conexões para um determinado cliente em grupos separados.|  
|`idleTimeout`|Um positivo <xref:System.TimeSpan> que especifica o tempo máximo que a conexão pode ficar ociosa antes de ser desconectada. O padrão é 00:02:00.|  
|`leaseTimeout`|Um <xref:System.TimeSpan> que especifica o tempo após o qual uma conexão ativa é fechada. O padrão é 00:05:00.<br /><br /> Uma conexão é fechada depois que ele foi retornado para o cache de conexão e não durante a transmissão de Active Directory. O cache de conexão usado pelo transporte TCP cria novas conexões conforme necessário para cada ponto de extremidade, até o limite de cache que é definido por `maxOutboundConnectionsPerEndpoint.`|  
|`maxOutboundConnectionsPerEndpoint`|Um inteiro positivo que especifica o número máximo de conexões para um ponto de extremidade remoto iniciado pelo serviço. Conexões além do limite são enfileiradas até que um espaço abaixo do limite fica disponível. O `idleTimeout` limita a duração em que as conexões permanecem na fila antes que uma exceção seja lançada. O padrão é 10.<br /><br /> Esse atributo limita o número de conexões ativas simultâneas do cliente para um ponto de extremidade de serviço específico. Se esse valor for excedido, fazendo com que as conexões de cliente mais ativas, o serviço pode parecer não estar respondendo ao cliente. Nesse caso, esse valor deve ser ajustado para exceder o número máximo de conexões de cliente esperado para um ponto de extremidade específico.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<namedPipeTransport>](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|Define um transporte que faz com que um canal transferir mensagens usando pipes nomeados.|  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.Configuration.TcpConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Transportes](../../../../../docs/framework/wcf/feature-details/transports.md)
- [Escolhendo um transporte](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [Associações](../../../../../docs/framework/wcf/bindings.md)
- [Estendendo associações](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Associações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
