---
title: Cotas de transporte
ms.date: 03/30/2017
helpviewer_keywords:
- transport quotas [WCF]
ms.assetid: 3e71dd3d-f981-4d9c-9c06-ff8abb61b717
ms.openlocfilehash: 44bda0838689fcf8096017060be970f2291a86e0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174623"
---
# <a name="transport-quotas"></a>Cotas de transporte
Cotas de transporte são um mecanismo de política para decidir quando uma conexão está consumindo recursos excessivos. Uma cota é um limite rígido que impede o uso de recursos adicionais depois que o valor da cota é excedido. Cotas de transporte impedir mal-intencionados ou não intencionais ataques de negação de serviço.  
  
 Transportes do Windows Communication Foundation (WCF) têm valores de cota padrão que se baseiam em uma alocação conservadora de recursos. Esses valores padrão são adequados para cenários de instalação pequenos e ambientes de desenvolvimento. Os administradores de serviço devem examinar as cotas de transporte e ajustar os valores de cota individual se uma instalação está ficando sem recursos ou se as conexões estão sendo limitadas, apesar da disponibilidade de recursos adicionais.  
  
## <a name="types-of-transport-quotas"></a>Tipos de cotas de transporte  
 Transportes WCF têm três tipos de cotas:  
  
-   *Tempos limite* atenuar ataques negação de serviço que dependem de prender os recursos por um longo período de tempo.  
  
-   *Limites de alocação de memória* impedir que uma única conexão de esgotamento de memória do sistema e negação de serviço para outras conexões.  
  
-   *Limites de tamanho da coleção* associado o consumo de recursos que indiretamente alocar memória ou que estão em quantidades limitadas.  
  
## <a name="transport-quota-descriptions"></a>Descrições de cota de transporte  
 Esta seção descreve as cotas de transporte disponíveis para os transportes WCF padrão: HTTP (S), TCP/IP e pipes nomeados. Transportes personalizados podem expor seus próprios cotas configuráveis que não são incluídas nessa lista. Consulte a documentação para um transporte personalizado saber mais sobre suas cotas.  
  
 Cada configuração de cota tem um tipo, o valor mínimo e o valor padrão. O valor máximo de uma cota é limitado por seu tipo. Devido a limitações de máquina, ele nem sempre é possível definir uma cota para seu valor máximo.  
  
|Nome|Tipo|Mín.<br /><br /> Valor |Padrão<br /><br /> Valor |Descrição|  
|----------|----------|--------------------|-----------------------|-----------------|  
|`ChannelInitializationTimeout`|TimeSpan|1 tique|5 s|Tempo máximo de espera para uma conexão enviar o preâmbulo durante a leitura inicial. Esses dados são recebidos antes que a autenticação ocorra. Essa configuração é geralmente muito menor do que o `ReceiveTimeout` valor da cota.|  
|`CloseTimeout`|TimeSpan|0|1 min|Tempo máximo de espera para uma conexão ser fechado antes que o transporte gere uma exceção.|  
|`ConnectionBufferSize`|Inteiro|1|8 KB|O tamanho, em bytes, de transmissão e recebimento de buffers de transporte subjacente. Aumentar o tamanho do buffer pode melhorar a taxa de transferência ao enviar mensagens grandes.|  
|`IdleTimeout`|TimeSpan|0|2 min|Tempo máximo de que uma conexão em pool pode permanecer ocioso antes de serem fechados.<br /><br /> Essa configuração só se aplica a conexões em pool.|  
|`LeaseTimeout`|TimeSpan|0|5 min|Tempo de vida máximo de uma conexão em pool Active Directory. Depois de decorrido o tempo especificado, a conexão é fechada depois que a solicitação atual é atendida.<br /><br /> Essa configuração só se aplica a conexões em pool.|  
|`ListenBacklog`|Inteiro|1|10|Número máximo de conexões que o ouvinte pode ter unserviced antes das conexões adicionais ao ponto de extremidade é negado.|  
|`MaxBufferPoolSize`|Long|0|512 KB|Máximo de memória, em bytes, que o transporte dedica para pool de buffers de mensagens reutilizáveis. Quando o pool não pode fornecer um buffer de mensagem, um novo buffer é alocado para uso temporário.<br /><br /> As instalações que cria várias fábricas de canais ou ouvintes poderá alocar grandes quantidades de memória para pools de buffers. Reduzir o tamanho do buffer pode reduzir consideravelmente o uso de memória nesse cenário.|  
|`MaxBufferSize`|Inteiro|1|64 KB|Tamanho máximo, em bytes, de um buffer usado para transmissão de dados. Se essa cota de transporte não for definida, ou o transporte não está usando o streaming, então o valor da cota é o mesmo que o menor do `MaxReceivedMessageSize` o valor de cota e <xref:System.Int32.MaxValue>.|  
|`MaxOutboundConnectionsPerEndpoint`|Inteiro|1|10|Número máximo de conexões de saída que pode ser associado um ponto de extremidade específico.<br /><br /> Essa configuração só se aplica a conexões em pool.|  
|`MaxOutputDelay`|TimeSpan|0|200 ms|Tempo máximo de espera após uma operação de envio para mensagens adicionais em uma única operação de envio em lote. As mensagens são enviadas anteriormente se encher o buffer de transporte subjacente. Enviar mensagens adicionais não redefine o período de atraso.|  
|`MaxPendingAccepts`|Inteiro|1|1|Número máximo de aceita para canais que o ouvinte pode ter em espera.<br /><br /> Há um intervalo de tempo entre a concluir a aceitação e um novo accept iniciado. Aumentar esse tamanho da coleção pode impedir que os clientes que se conectam durante esse intervalo seja descartado.|  
|`MaxPendingConnections`|Inteiro|1|10|Número máximo de conexões que o ouvinte pode ter aguardando para serem aceitas pelo aplicativo. Quando esse valor de cota for excedida, novas conexões de entrada são descartadas em vez de esperar para ser aceito.<br /><br /> Recursos de Conexão, como segurança de mensagem podem fazer com que um cliente abrir mais de uma conexão. Os administradores de serviço devem levar em consideração para essas conexões adicionais ao definir esse valor de cota.|  
|`MaxReceivedMessageSize`|Long|1|64 KB|Tamanho máximo, em bytes, de uma mensagem recebida, incluindo os cabeçalhos, antes que o transporte gere uma exceção.|  
|`OpenTimeout`|TimeSpan|0|1 min|Tempo máximo de espera para uma conexão seja estabelecida antes que o transporte gere uma exceção.|  
|`ReceiveTimeout`|TimeSpan|0|10 min|Tempo máximo de espera para uma operação de leitura seja concluída antes do transporte gere uma exceção.|  
|`SendTimeout`|Timespan|0|1 min|Tempo máximo de espera para uma operação de gravação seja concluída antes do transporte gere uma exceção.|  
  
 As cotas de transporte `MaxPendingConnections` e `MaxOutboundConnectionsPerEndpoint` são combinados em uma cota única de transporte chamada `MaxConnections` quando configurada por meio de associação ou a configuração. Apenas o elemento de associação permite definir esses valores de cota individualmente. O `MaxConnections` cota de transporte tem os mesmos valores mínimo e padrão.  
  
## <a name="setting-transport-quotas"></a>Cotas de transporte de configuração  
 As cotas de transporte são definidas por meio do elemento de associação de transporte, a associação de transporte, configuração de aplicativo ou política de host. Este documento não abrange os transportes de configuração por meio da política de host. Consulte a documentação para o transporte subjacente descobrir as configurações para cotas de política de host. O [Configuring HTTP and HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md) tópico descreve as configurações de cota para o driver HTTP. sys. Pesquise a Base de Conhecimento Microsoft para obter mais informações sobre como configurar limites do Windows em HTTP, TCP/IP e conexões de pipe nomeado.  
  
 Outros tipos de cotas indiretamente aplicam a todos os transportes. O codificador de mensagem que usa o transporte para transformar uma mensagem em bytes pode ter suas próprias configurações de cota. No entanto, essas cotas são independentes do tipo de transporte que está sendo usado.  
  
### <a name="controlling-transport-quotas-from-the-binding-element"></a>Controlando as cotas de transporte do elemento de associação  
 Configurando cotas de transporte por meio do elemento de associação oferece mais flexibilidade para controlar o comportamento do transporte. Os tempos limite padrão para fechar, abrir, Receive e enviar operações são executadas da associação, quando um canal é criado.  
  
|Nome|HTTP|TCP/IP|pipe nomeado|  
|----------|----------|-------------|----------------|  
|`ChannelInitializationTimeout`||X|X|  
|`CloseTimeout`||||  
|`ConnectionBufferSize`||X|X|  
|`IdleTimeout`||X|X|  
|`LeaseTimeout`||X||  
|`ListenBacklog`||X||  
|`MaxBufferPoolSize`|X|X|X|  
|`MaxBufferSize`|X|X|X|  
|`MaxOutboundConnectionsPerEndpoint`||X|X|  
|`MaxOutputDelay`||X|X|  
|`MaxPendingAccepts`||X|X|  
|`MaxPendingConnections`||X|X|  
|`MaxReceivedMessageSize`|X|X|X|  
|`OpenTimeout`||||  
|`ReceiveTimeout`||||  
|`SendTimeout`||||  
  
### <a name="controlling-transport-quotas-from-the-binding"></a>Controlando as cotas de transporte da associação  
 Configurando cotas de transporte por meio da associação oferece um conjunto simplificado de cotas para sua escolha e ainda oferecem acesso aos valores de cota mais comuns.  
  
|Nome|HTTP|TCP/IP|pipe nomeado|  
|----------|----------|-------------|----------------|  
|`ChannelInitializationTimeout`||||  
|`CloseTimeout`|X|X|X|  
|`ConnectionBufferSize`||||  
|`IdleTimeout`||||  
|`LeaseTimeout`||||  
|`ListenBacklog`||X||  
|`MaxBufferPoolSize`|X|X|X|  
|`MaxBufferSize`|1|X|X|  
|`MaxOutboundConnectionsPerEndpoint`||2|2|  
|`MaxOutputDelay`||||  
|`MaxPendingAccepts`||||  
|`MaxPendingConnections`||2|2|  
|`MaxReceivedMessageSize`|X|X|X|  
|`OpenTimeout`|X|X|X|  
|`ReceiveTimeout`|X|X|X|  
|`SendTimeout`|X|X|X|  
  
1.  O `MaxBufferSize` cota de transporte só está disponível no `BasicHttp` associação. O `WSHttp` associações são para cenários que não dão suporte a modos de transporte em fluxo.  
  
2.  As cotas de transporte `MaxPendingConnections` e `MaxOutboundConnectionsPerEndpoint` são combinados em uma cota única de transporte chamada `MaxConnections`.  
  
### <a name="controlling-transport-quotas-from-configuration"></a>Controlando as cotas de transporte da configuração  
 Configuração de aplicativo pode definir as cotas de transporte mesmo como acessar diretamente as propriedades em uma associação. Arquivos de configuração, o nome de uma cota de transporte sempre começa com uma letra minúscula. Por exemplo, o `CloseTimeout` propriedade em uma associação corresponde à `closeTimeout` na configuração e o `MaxConnections` propriedade em uma associação corresponde à `maxConnections` na configuração.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
