---
title: Cotas de transporte
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: transport quotas [WCF]
ms.assetid: 3e71dd3d-f981-4d9c-9c06-ff8abb61b717
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5e9d7fbf42f2ed9b8f68b1faf2e2425050b62eaa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="transport-quotas"></a>Cotas de transporte
Cotas de transporte são um mecanismo de política para decidir quando uma conexão está consumindo recursos excessivos. Uma cota é um limite rígido que impede o uso de recursos adicionais quando o valor da cota for excedido. Cotas de transporte impedir mal-intencionados ou não intencionais ataques de negação de serviço.  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]transportes têm valores de cota padrão com base em uma alocação de recursos de conservadora. Esses valores padrão são adequados para ambientes de desenvolvimento e cenários de instalação pequeno. Os administradores de serviço devem revisar cotas de transporte e ajustar os valores de cota individuais se uma instalação está ficando sem recursos ou se as conexões estão sendo limitadas apesar da disponibilidade dos recursos adicionais.  
  
## <a name="types-of-transport-quotas"></a>Tipos de cotas de transporte  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]transportes têm três tipos de cotas:  
  
-   *Tempos limite* mitigar ataques negação de serviço que dependem de prender os recursos por um longo período de tempo.  
  
-   *Limites de alocação de memória* impedir que uma única conexão de esgotamento de memória do sistema e negação de serviço para outras conexões.  
  
-   *Limites de tamanho da coleção* associado o consumo de recursos que indiretamente alocar memória ou em oferta limitada.  
  
## <a name="transport-quota-descriptions"></a>Descrições de cota de transporte  
 Esta seção descreve as cotas de transporte disponíveis para o padrão [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transportes: HTTP (S), TCP/IP e pipes nomeados. Transportes personalizados podem expor seus próprios cotas configuráveis não incluídas nessa lista. Consulte a documentação de um transporte personalizado obter informações sobre suas cotas.  
  
 Cada configuração de cota tem um tipo, o valor mínimo e o valor padrão. O valor máximo de uma cota é limitado por seu tipo. Devido às limitações de máquina, nem sempre é possível definir uma cota para seu valor máximo.  
  
|Nome|Tipo|Min.<br /><br /> Valor |Padrão<br /><br /> Valor |Descrição|  
|----------|----------|--------------------|-----------------------|-----------------|  
|`ChannelInitializationTimeout`|TimeSpan|1 tique|5 seg|Tempo máximo de espera para uma conexão enviar o preâmbulo durante a leitura inicial. Estes dados são recebidos antes da autenticação. Essa configuração é geralmente muito menor do que o `ReceiveTimeout` valor da cota.|  
|`CloseTimeout`|TimeSpan|0|1 min|Tempo máximo de espera para uma conexão fechar antes do transporte gerará uma exceção.|  
|`ConnectionBufferSize`|Inteiro|1|8 KB|Tamanho, em bytes, de transmissão e receber buffers de transporte subjacente. Aumentar o tamanho do buffer pode melhorar o desempenho durante o envio de mensagens grandes.|  
|`IdleTimeout`|TimeSpan|0|2 min|Tempo máximo de que uma conexão em pool pode permanecer ocioso antes de ser fechado.<br /><br /> Essa configuração aplica-se somente a conexões em pool.|  
|`LeaseTimeout`|TimeSpan|0|5 min|Tempo de vida máximo de uma conexão em pool ativo. Depois de decorrido o tempo especificado, a conexão é fechada depois que a solicitação atual é atendida.<br /><br /> Essa configuração aplica-se somente a conexões em pool.|  
|`ListenBacklog`|Inteiro|1|10|Número máximo de conexões que o ouvinte pode ter unserviced antes de conexões adicionais ao ponto de extremidade é negado.|  
|`MaxBufferPoolSize`|Long|0|512 KB|Máximo de memória, em bytes, que o transporte dedica ao pool de buffers de mensagens reutilizáveis. Quando o pool não pode fornecer um buffer de mensagem, um novo buffer é alocado para uso temporário.<br /><br /> Instalações que criar muitas fábricas de canais ou ouvintes poderá alocar grandes quantidades de memória para pools de buffers. Reduzir o tamanho do buffer pode reduzir significativamente o uso de memória nesse cenário.|  
|`MaxBufferSize`|Inteiro|1|64 KB|Tamanho máximo, em bytes, de um buffer usado para streaming de dados. Se essa cota de transporte não for definida, ou o transporte não está usando para streaming, o valor da cota é o mesmo que o menor do `MaxReceivedMessageSize` o valor de cota e <xref:System.Int32.MaxValue>.|  
|`MaxOutboundConnectionsPerEndpoint`|Inteiro|1|10|Número máximo de conexões de saída que pode ser associado um ponto de extremidade específico.<br /><br /> Essa configuração aplica-se somente a conexões em pool.|  
|`MaxOutputDelay`|TimeSpan|0|200 ms|Tempo máximo de espera após uma operação de envio para mensagens adicionais em uma única operação de lote. As mensagens são enviadas anteriormente se o buffer de transporte subjacente ficar cheio. Enviar mensagens adicionais não redefine o período de atraso.|  
|`MaxPendingAccepts`|Inteiro|1|1|Número máximo de aceita de canais que o ouvinte pode ter espera.<br /><br /> Há um intervalo de tempo entre a conclusão de aceitar e um novo aceitar iniciado. Aumentar o tamanho da coleção pode impedir que os clientes que se conectam durante esse intervalo seja descartado.|  
|`MaxPendingConnections`|Inteiro|1|10|Número máximo de conexões que o ouvinte pode ter aguardando para serem aceitas pelo aplicativo. Quando esse valor de cota for ultrapassada, novas conexões de entrada são descartadas em vez de esperar ser aceito.<br /><br /> Recursos de Conexão, como segurança de mensagem podem causar um cliente abrir mais de uma conexão. Os administradores de serviço devem levar em consideração para essas conexões adicionais ao definir esse valor de cota.|  
|`MaxReceivedMessageSize`|Long|1|64 KB|Tamanho máximo, em bytes, de uma mensagem recebida, incluindo os cabeçalhos, antes do transporte gera uma exceção.|  
|`OpenTimeout`|TimeSpan|0|1 min|Tempo máximo de espera para uma conexão seja estabelecida antes do transporte gerará uma exceção.|  
|`ReceiveTimeout`|TimeSpan|0|10 min|Tempo máximo de espera para uma operação de leitura seja concluída antes do transporte gerará uma exceção.|  
|`SendTimeout`|Timespan|0|1 min|Tempo máximo de espera para uma operação de gravação seja concluída antes do transporte gerará uma exceção.|  
  
 As cotas de transporte `MaxPendingConnections` e `MaxOutboundConnectionsPerEndpoint` são combinados em uma cota de transporte único chamada `MaxConnections` quando é definido por meio de associação ou a configuração. O elemento de associação permite definir esses valores de cota individualmente. O `MaxConnections` cota de transporte tem os mesmos valores mínimo e padrão.  
  
## <a name="setting-transport-quotas"></a>Cotas de transporte de configuração  
 As cotas de transporte são definidas por meio do elemento de associação de transporte, a associação de transporte, configuração de aplicativo ou política de host. Este documento não aborda os transportes de configuração por meio da política de host. Consulte a documentação para o transporte subjacente descobrir as configurações de cotas de política de host. O [Configurando HTTP e HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md) tópico descreve as configurações de cota para o driver HTTP. sys. Pesquise a Base de dados de Conhecimento Microsoft para obter mais informações sobre como configurar limites do Windows em HTTP, TCP/IP e conexões de pipe nomeado.  
  
 Outros tipos de cotas indiretamente aplicam a todos os transportes. O codificador de mensagem que usa o transporte para transformar uma mensagem em bytes pode ter suas próprias configurações de cota. No entanto, essas cotas são independentes do tipo de transporte que está sendo usado.  
  
### <a name="controlling-transport-quotas-from-the-binding-element"></a>Controlando as cotas de transporte do elemento de associação  
 Configurando cotas de transporte por meio do elemento de associação oferece mais flexibilidade para controlar o comportamento do transporte. Os limites padrão para fechar, abrir, receber e enviar operações são executadas da associação quando um canal é criado.  
  
|Nome|HTTP|TCP/IP|Pipe nomeado|  
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
  
### <a name="controlling-transport-quotas-from-the-binding"></a>Controlando as cotas de transporte de associação  
 Configurando cotas de transporte por meio de associação oferece um conjunto simplificado de cotas para escolher enquanto ainda fornece acesso para os valores de cota mais comuns.  
  
|Nome|HTTP|TCP/IP|Pipe nomeado|  
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
  
1.  O `MaxBufferSize` cota de transporte só está disponível na `BasicHttp` associação. O `WSHttp` associações são para cenários que não oferecem suporte a modos de transporte em fluxo.  
  
2.  As cotas de transporte `MaxPendingConnections` e `MaxOutboundConnectionsPerEndpoint` são combinados em uma cota de transporte único chamada `MaxConnections`.  
  
### <a name="controlling-transport-quotas-from-configuration"></a>Controlando as cotas de transporte da configuração  
 Configuração de aplicativo pode definir as cotas de transporte mesmo como acessar diretamente as propriedades em uma associação. Arquivos de configuração, o nome de uma cota de transporte sempre começa com uma letra minúscula. Por exemplo, o `CloseTimeout` propriedade em uma associação corresponde ao `closeTimeout` configuração na configuração e o `MaxConnections` propriedade em uma associação corresponde ao `maxConnections` configuração na configuração.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
 <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>
