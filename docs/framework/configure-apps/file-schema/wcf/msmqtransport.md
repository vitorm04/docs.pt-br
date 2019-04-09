---
title: <msmqTransport>
ms.date: 03/30/2017
ms.assetid: 19d89f35-76ac-49dc-832b-e8bec2d5e33b
ms.openlocfilehash: 9bdaccd6183bc4ea58ed610b58aceddcb6ba0351
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59106563"
---
# <a name="msmqtransport"></a>\<msmqTransport>
Faz com que um canal transferir mensagens sobre o transporte MSMQ quando ele é incluído em uma associação personalizada.  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<binding>  
\<msmqIntegration>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<msmqTransport customDeadLetterQueue="Uri"
               deadLetterQueue="Custom/None/System"
               durable="Boolean"
               exactlyOnce="Boolean"
               manualAddressing="Boolean"
               maxBufferPoolSize="Integer"
               maxImmediateRetries="Integer"
               maxPoolSize="Integer"
               maxReceivedMessageSize="Integer"
               maxRetryCycles="Integer"
               queueTransferProtocol="Native/Srmp/SrmpSecure"
               rejectAfterLastRetry="Boolean"
               retryCycleDelay="TimeSpan"
               timeToLive="TimeSpan"
               useActiveDirectory="Boolean"
               useSourceJournal="Boolean"
               useMsmqTracing="Boolean"
               ...>
  <msmqTransportSecurity>
  </msmqTransportSecurity>
</msmqTransport>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|customDeadLetterQueue|Um URI que indica o local da fila de mensagens mortas por aplicativo, onde as mensagens que tem expirado ou não puderam ser entregues ao aplicativo são transferidas.<br /><br /> Para mensagens que exigem garantias ExactlyOnce (isto é, `exactlyOnce` é definido como `true`), esse atributo usa como padrão para a fila de inatividade transacional em todo o sistema em MSMQ.<br /><br /> Para mensagens que não exigem garantias de nenhum (ou seja, `exactlyOnce` é definido como `false`), esse atributo padrão é `null`.<br /><br /> O valor deve usar o esquema de NET. MSMQ. O padrão é `null`.<br /><br /> Se `deadLetterQueue` é definido como `None` ou `System`, em seguida, esse atributo deve ser definido como `null`. Se esse atributo não for `null`, em seguida, `deadLetterQueue` deve ser definida como `Custom`.|  
|deadLetterQueue|Especifica o tipo de fila de mensagens mortas a ser usada.<br /><br /> Os valores válidos incluem<br /><br /> -Personalizado: Fila de mensagens mortas personalizada.<br />-None: Nenhuma fila de mensagens mortas deve ser usada.<br />-Sistema: Use a fila de mensagens mortas do sistema.<br /><br /> Esse atributo é do tipo DeadLetterQueue.|  
|duráveis|Um valor booliano que especifica se as mensagens processadas por essa associação são duráveis ou voláteis. O padrão é `true`.<br /><br /> Uma mensagem durável sobrevive a uma falha do Gerenciador de fila, enquanto uma mensagem volátil não. Mensagens voláteis são úteis quando aplicativos exigem uma latência mais baixa e podem tolerar mensagens perdidas ocasionais.<br /><br /> Se `exactlyOnce` é definido como `true`, as mensagens devem ser duráveis.|  
|exactlyOnce|Um booliano que especifica se as mensagens processadas por essa associação serão recebidas exatamente uma vez. O padrão é `true`.<br /><br /> Uma mensagem pode ser enviada com ou sem garantias. Garantia de permite que um aplicativo garantir que uma mensagem enviada chegou à fila de mensagem de recebimento, ou se ele não tenha anotado, o aplicativo pode determinar isso lendo a fila de mensagens mortas.<br /><br /> `exactlyOnce`, quando definido como `true`, indica que o MSMQ garantirá que uma mensagem enviada é entregue para a fila de recebimento de mensagem, apenas uma vez e se a entrega falhar, a mensagem é enviada para a fila de mensagens mortas.<br /><br /> As mensagens enviadas com `exactlyOnce` definido como `true` deve ser enviada para uma fila transacional somente.|  
|manualAddressing|Um valor booliano que permite ao usuário assumir o controle do endereçamento de mensagem. Essa propriedade normalmente é usada em cenários de roteador, onde o aplicativo determina que uma de vários destinos para enviar uma mensagem.<br /><br /> Quando definido como `true`, o canal pressupõe que a mensagem já foi abordada e não adiciona qualquer informação adicional a ele. O usuário pode, em seguida, abordar todas as mensagens individualmente.<br /><br /> Quando definido como `false`, o mecanismo de endereçamento padrão Windows Communication Foundation (WCF) cria automaticamente os endereços para todas as mensagens.<br /><br /> O padrão é `false`.|  
|maxBufferPoolSize|Um inteiro positivo que especifica o tamanho máximo do pool de buffers. O padrão é 524288.<br /><br /> Muitas partes do WCF usam buffers. Criação e destruição de buffers de cada vez que elas são usadas são caro e coleta de lixo para buffers também é dispendiosa. Com os pools de buffer, usar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar. Portanto, a sobrecarga na criação e destruição de buffers é evitada.|  
|maxImmediateRetries|Tentativas de um inteiro que especifica o número máximo de repetição imediata em uma mensagem que é lida da fila de aplicativos. O padrão é 5.<br /><br /> Se o número máximo de novas tentativas imediatas para a mensagem é tentado e a mensagem não é consumida pelo aplicativo, a mensagem é enviada para uma fila de repetição para tentar novamente em algum momento posterior no tempo. Se sem ciclos de repetição são especificados, em seguida, as mensagens será enviado para a fila de mensagens suspeitas ou uma confirmação negativa é enviada de volta ao remetente.|  
|maxPoolSize|Um inteiro positivo que especifica o tamanho máximo do pool. O padrão é 524288.|  
|maxReceivedMessageSize|Um inteiro positivo que especifica o tamanho máximo em bytes, incluindo cabeçalhos. O remetente de uma mensagem recebe uma falha SOAP quando a mensagem é muito grande para o receptor. O receptor descartará a mensagem e cria uma entrada do evento no log de rastreamento. O padrão é 65536.|  
|maxRetryCycles|Um inteiro que especifica o número máximo de ciclos de repetição para tentar entregar mensagens para o aplicativo de recebimento. O padrão é <xref:System.Int32.MaxValue>.<br /><br /> Um ciclo único de repetição tenta entregar uma mensagem para um aplicativo um número de vezes especificado. O número de tentativas feitas é definido pelo `maxImmediateRetries` atributo. Se o aplicativo não conseguir consumir a mensagem depois que as tentativas de entrega tiverem se esgotado, a mensagem é enviada para uma fila de repetição. Consistem em ciclos de repetição subsequentes da mensagem que está sendo retornada da fila de repetição para a fila de aplicativos para tentar entregar para o aplicativo novamente, após um atraso especificado pelo `retryCycleDelay` atributo. O `maxRetryCycles` atributo especifica o número de ciclos de repetição, o aplicativo usa para tentar entregar a mensagem.|  
|queueTransferProtocol|Especifica o transporte de canal de comunicação em fila que esta associação usa. Os valores válidos são<br /><br /> -Nativo:  Use o protocolo nativo do MSMQ.<br />-Srmp:  Use o protocolo SRMP (Soap Reliable Messaging Protocol).<br />-   SrmpSecure: Use o transporte SRMPS (Soap Reliable Messaging Protocol Secure).<br /><br /> Esse atributo é do tipo <xref:System.ServiceModel.QueueTransferProtocol>.<br /><br /> Uma vez que o MSMQ não oferece suporte a endereçamento de Active Directory ao usar o SOAP Reliable Messaging Protocol, você não deve definir esse atributo para Srmp ou Srmps quando `useActiveDirectory` é definido como `true`.|  
|rejectAfterLastRetry|Um valor booliano que especifica qual ação será tomada por uma mensagem que falha na entrega após o número máximo de novas tentativas foram tentadas.<br /><br /> `true` significa que uma confirmação negativa é retornada ao remetente e a mensagem será removida; `false` significa que a mensagem é enviada para a fila de mensagens suspeitas. O padrão é `false`.<br /><br /> Se o valor for `false`, o aplicativo de recebimento pode ler a fila de mensagens suspeitas para processar mensagens suspeitas (ou seja, mensagens com falha na entrega).<br /><br /> O MSMQ 3.0 não oferece suporte para retornar uma confirmação negativa para o remetente, portanto, esse atributo será ignorado no MSMQ 3.0.|  
|retryCycleDelay|Um <xref:System.TimeSpan> que especifica o tempo de espera entre os ciclos de repetição ao tentar entregar uma mensagem que não pôde ser entregue imediatamente. O padrão é 10:00:00.<br /><br /> Um ciclo único de repetição tenta entregar uma mensagem para um aplicativo de recebimento um número de vezes especificado. O número de tentativas feitas é especificado pelo `maxImmediateRetries` atributo. Se o aplicativo não conseguir consumir a mensagem após o número especificado de novas tentativas imediatas, a mensagem é enviada para uma fila de repetição. Consistem em ciclos de repetição subsequentes da mensagem que está sendo retornada da fila de repetição para a fila de aplicativos para tentar entregar para o aplicativo novamente, após um atraso especificado pelo `retryCycleDelay` atributo. O número de ciclos de repetição é especificado pelo `maxRetryCycles` atributo.|  
|timeToLive|Um <xref:System.TimeSpan> que especifica quanto tempo as mensagens são válidas antes de eles expirarem e serem colocados na fila de inatividade. O padrão é 1.00:00:00, o que significa 1 dia.<br /><br /> Esse atributo é definido para garantir que as mensagens de detecção de hora não tornam-se obsoletos antes que eles são processados por aplicativos de recebimento. Diz-se que uma mensagem em uma fila que não é consumida pelo aplicativo de recebimento dentro do intervalo de tempo especificado expirar. As mensagens expiradas são enviadas à fila especial chamada a fila de mensagens mortas. O local da fila de mensagens mortas é definido com o `customDeadLetterQueue` de atributo ou como o padrão apropriado, com base em garantias.|  
|UseActiveDirectory|Um valor booliano que especifica se os endereços de fila devem ser convertidos usando o Active Directory.<br /><br /> Endereços de fila MSMQ podem consistir de nomes de caminho ou nomes de formato direto. Com um nome de formato direto, o MSMQ resolve o nome do computador usando o IP, NetBIOS ou DNS. Com um nome de caminho, o MSMQ resolve o nome do computador usando o Active Directory. Por padrão, o Windows Communication Framework (WCF) na fila de transporte converte o URI de uma fila de mensagens para um nome de formato direto. Definindo este atributo como `true`, um aplicativo pode especificar que o transporte em fila deve resolver o nome do computador usando o IP, NetBIOS em vez de DNS ou Active Directory.|  
|useMsmqTracing|Um valor booliano que especifica se as mensagens processadas por essa associação deve ser rastreado. O padrão é `false`.<br /><br /> Quando o rastreamento está habilitado, as mensagens de relatório são criadas e enviadas para a fila de relatórios sempre que a mensagem sai ou chega a um computador do serviço de enfileiramento de mensagens.|  
|useSourceJournal|Um valor booliano que especifica se as cópias de mensagens processadas por essa associação devem ser armazenadas na fila de diário de origem. O padrão é `false`.<br /><br /> Aplicativos em fila que deseja manter um registro de mensagens que deixaram a fila de saída do computador podem copiar as mensagens para uma fila do diário. Depois que uma mensagem deixa a fila de saída e uma confirmação for recebida, que a mensagem foi recebida no computador de destino, uma cópia da mensagem é mantida na fila de diário do sistema do computador de envio.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<msmqTransportSecurity>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqtransportsecurity.md)|Especifica as configurações de segurança de transporte para essa associação. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<binding>](../../../../../docs/framework/misc/binding.md)|Define todos os recursos de associação de associação personalizada.|  
  
## <a name="remarks"></a>Comentários  
 O `msmqTransport` elemento permite que o usuário definir as propriedades do canal de comunicação em fila. O canal de comunicação em fila utiliza o enfileiramento de mensagens para o transporte.  
  
 Este elemento de associação é o elemento de associação padrão usado pela associação padrão enfileiramento de mensagens (`netMsmqBinding`).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.MsmqTransportElement>
- <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Filas no WCF](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [Transportes](../../../../../docs/framework/wcf/feature-details/transports.md)
- [Selecionando um transporte](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [Associações](../../../../../docs/framework/wcf/bindings.md)
- [Estendendo associações](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Associações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
