---
title: '&lt;msmqIntegration&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ab677405-1ffe-457a-803f-00c1770e51e2
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: efa224477dfdf396af2403f509f252b8e0f2a55f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltmsmqintegrationgt"></a>&lt;msmqIntegration&gt;
Especifica um transporte MSMQ para associação personalizada.  
  
 \<System. ServiceModel >  
\<associações >  
\<customBinding >  
\<associação >  
\<msmqIntegration >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<msmqIntegration>  
        customDeadLetterQueue="Uri"  
        deadLetterQueue="Custom/None/System"  
    durable="Boolean"  
    exactlyOnce="Boolean"  
    manualAddressing="Boolean"  
    maxBufferPoolSize="Integer"  
    maxImmediateRetries="Integer"  
    maxReceivedMessageSize="Integer"  
    maxRetryCycles="Integer"  
    rejectAfterLastRetry="Boolean"  
    retryCycleDelay="TimeSpan"  
    serializationFormat="XML/Binary/ActiveX/ByteArray/Stream"  
    timeToLive="TimeSpan"  
    useSourceJournal="Boolean"  
    useMsmqTracing="Boolean"  
    <msmqTransportSecurity>  
    </msmqTransportSecurity>  
</msmqIntegration>  
```  
  
## <a name="type"></a>Tipo  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|CustomDeadLetterQueue|Um URI que indica o local da fila de inatividade por aplicativo, onde as mensagens que tenham expirado ou não pôde ser entregue ao aplicativo são transferidas.<br /><br /> Para mensagens que exigem garantias ExactlyOnce (isto é, `exactlyOnce` é definido como `true`), esse atributo padrão é a fila de mensagens mortas transacional de todo o sistema em MSMQ.<br /><br /> Para mensagens que não exigem nenhuma garantia (ou seja, `exactlyOnce` é definido como `false`), esse atributo padrão é `null`.<br /><br /> O valor deve usar o esquema NET. MSMQ. O padrão é `null`.<br /><br /> Se `d``eadLetterQueue` é definido como `None` ou `System`, em seguida, esse atributo deve ser definido como `null`. Se esse atributo não for `null`, em seguida, `deadLetterQueue` deve ser definido como `Custom`.|  
|DeadLetterQueue|Especifica o tipo de fila de mensagens mortas a usar.<br /><br /> Os valores válidos incluem<br /><br /> -Custom: Fila de mensagens mortas personalizada.<br />-Nenhum: Nenhuma fila de mensagens mortas é para ser usado.<br />-Sistema: Use a fila de mensagens mortas do sistema.<br /><br /> Esse atributo é do tipo DeadLetterQueue.|  
|duráveis|Um valor booleano que especifica se as mensagens processadas por essa associação são duráveis ou voláteis. O padrão é `true`.<br /><br /> Uma mensagem durável sobrevive a uma falha do Gerenciador de fila, enquanto uma mensagem volátil não. Mensagens voláteis são úteis quando aplicativos necessitam de latência mais baixa e podem tolerar mensagens perdidas ocasionais.<br /><br /> Se `exactlyOnce` é definido como `true`, as mensagens devem ser duráveis.|  
|ExactlyOnce|Um valor booleano que especifica se as mensagens processadas por essa associação serão recebidas exatamente uma vez. O padrão é `true`.<br /><br /> Uma mensagem pode ser enviada com ou sem garantias. Uma garantia permite que um aplicativo garantir que a fila de recebimento de mensagem de repetição de uma mensagem enviada ou se não estiver, o aplicativo pode determinar isso lendo a fila de mensagens mortas.<br /><br /> `exactlyOnce`, quando definido como `true`, indica que o MSMQ irá garantir que uma mensagem enviada é entregue para a fila de recebimento de mensagem somente uma vez e se a entrega falhar, a mensagem é enviada para a fila de mensagens mortas.<br /><br /> As mensagens enviadas com `exactlyOnce` definida como `true` devem ser enviadas para uma fila transacional somente.|  
|manualAddressing|Um valor booleano que permite ao usuário assumir o controle do endereçamento da mensagem. Essa propriedade normalmente é usada em cenários de roteador, onde o aplicativo determina que uma de vários destinos para enviar uma mensagem.<br /><br /> Quando definido como `true`, o canal assume a mensagem já tiver sido resolvida e não adiciona informações adicionais a ele. O usuário pode, em seguida, abordar cada mensagem individualmente.<br /><br /> Quando definido como `false`, o mecanismo de endereçamento do Windows Communication Foundation (WCF) padrão cria automaticamente os endereços de todas as mensagens.<br /><br /> O padrão é `false`.|  
|maxBufferPoolSize|Um inteiro positivo que especifica o tamanho máximo do pool de buffers. O padrão é 524288.<br /><br /> Muitas partes do WCF usam buffers. Criação e destruição de buffers de cada vez que elas são usadas são caro e coleta de lixo para buffers também é cara. Com os pools de buffer, usar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar. Portanto, a sobrecarga na criação e destruição de buffers é evitada.|  
|maxImmediateRetries|Tentativas de um inteiro que especifica o número máximo de repetição imediatas em uma mensagem que é lida da fila de aplicativos. O padrão é 5.<br /><br /> Se o número máximo de repetições imediatas para a mensagem é tentado e a mensagem não é consumida pelo aplicativo, a mensagem é enviada para uma fila de repetição para tentar novamente posteriormente no tempo. Se nenhum ciclos de repetição for especificados, as mensagens ou é enviado para a fila de mensagens suspeitas, ou uma confirmação negativa será enviada de volta ao remetente.|  
|maxReceivedMessageSize|Um inteiro positivo que especifica o tamanho máximo em bytes, incluindo cabeçalhos. O remetente de uma mensagem recebe uma falha SOAP quando a mensagem é muito grande para o destinatário. O receptor descartará a mensagem e cria uma entrada do evento no log de rastreamento. O padrão é 65536.|  
|MaxRetryCycles|Um inteiro que especifica o número máximo de ciclos de repetição para tentar entregar mensagens para o aplicativo receptor. O padrão é <xref:System.Int32.MaxValue>.<br /><br /> Um ciclo de repetição de único tenta entregar uma mensagem para um aplicativo um número de vezes especificado. O número de tentativas feitas é definido pelo `maxImmediateRetries` atributo. Se o aplicativo falhar consumir a mensagem depois de tentativas de entrega foram esgotadas, a mensagem é enviada para uma fila de repetição. Consistem em ciclos de repetição subsequente da mensagem que está sendo retornada da fila de repetição para a fila de aplicativo para tentar entregar ao aplicativo novamente, após um atraso especificado pelo `retryCycleDelay` atributo. O `maxRetryCycles` atributo especifica o número de ciclos de repetição que o aplicativo usa para tentar entregar a mensagem.|  
|rejectAfterLastRetry|Um valor booleano que especifica a ação a ser tomada para uma mensagem de falha na entrega após o número máximo de novas tentativas foram tentadas.<br /><br /> `true`significa que uma confirmação negativa será retornada para o remetente e a mensagem é removida; `false` significa que a mensagem é enviada para a fila de mensagens suspeitas. O padrão é `false`.<br /><br /> Se o valor for `false`, o aplicativo receptor pode ler a fila de mensagens suspeitas para processar mensagens suspeitas (ou seja, as mensagens com falha na entrega).<br /><br /> MSMQ 3.0 não oferece suporte para retornar uma confirmação negativa para o remetente, para que esse atributo será ignorado em MSMQ 3.0.|  
|RetryCycleDelay|Um <xref:System.TimeSpan> que especifica o tempo de espera entre os ciclos de repetição ao tentar entregar uma mensagem que não pôde ser entregue imediatamente. O padrão é 00:10:00.<br /><br /> Um ciclo de repetição de único tenta entregar uma mensagem para um aplicativo que recebe um número de vezes especificado. O número de tentativas feitas for especificado o `maxImmediateRetries` atributo. Se o aplicativo não consegue consumir a mensagem após o número especificado de tentativas de imediatos, a mensagem é enviada para uma fila de repetição. Consistem em ciclos de repetição subsequente da mensagem que está sendo retornada da fila de repetição para a fila de aplicativo para tentar entregar ao aplicativo novamente, após um atraso especificado pelo `retryCycleDelay` atributo. O número de ciclos de repetição é especificado pelo `maxRetryCycles` atributo.|  
|serializationFormat|Especifica o formatador que é usado para serializar objetos que são enviados como parte de uma mensagem MSMQ. Os valores válidos são<br /><br /> -ActiveX: O formatador do ActiveX é usado ao serializar objetos COM.<br />-Binário: Serializa o objeto em um pacote de binário.<br />-ByteArray: Serializa o objeto em uma matriz de bytes.<br />-Fluxo: Serializa o objeto em um fluxo.<br />-Xml: Serializa o objeto em um pacote XML. O padrão é XML.<br /><br /> Esse atributo é do tipo <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat>.|  
|TimeToLive|Um <xref:System.TimeSpan> que especifica quanto tempo as mensagens são válidas antes de expirarem e são colocadas na fila de mensagens mortas. O padrão é 1.00:00:00, o que significa que 1 dia.<br /><br /> Esse atributo é definido para garantir que as mensagens de detecção de hora não tornam-se obsoletos antes que elas são processadas pelos aplicativos de recebimento. Uma mensagem em uma fila que não é consumida pelo aplicativo de recebimento dentro do intervalo de tempo especificado deve ser expirados. As mensagens expiradas são enviadas à fila especial chamada fila de mensagens mortas. O local da fila de mensagens mortas é definido com o `customDeadLetterQueue` de atributo ou como o padrão apropriado, com base em garantia.|  
|UseMsmqTracing|Um valor booleano que especifica se as mensagens processadas por essa associação deve ser rastreado. O padrão é `false`.<br /><br /> Quando o rastreamento estiver habilitado, as mensagens de relatório criadas e enviadas para a fila de relatórios sempre que a mensagem sai ou chega em um computador do serviço de enfileiramento de mensagens.|  
|UseSourceJournal|Um valor booleano que especifica se as cópias de mensagens processadas por essa associação devem ser armazenadas na fila de diário de origem. O padrão é `false`.<br /><br /> Na fila de aplicativos que deseja manter um registro das mensagens que deixaram a fila de saída do computador podem copiar as mensagens para uma fila do diário. Depois que uma mensagem deixa a fila de saída e é recebida uma confirmação que a mensagem foi recebida no computador de destino, uma cópia da mensagem é mantida na fila de diário do sistema do computador de envio.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|msmqTransportSecurity|Especifica as configurações de segurança de transporte para esta associação. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<associação >](../../../../../docs/framework/misc/binding.md)|Define todos os recursos de associação da associação personalizada.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Transportes](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [Filas no WCF](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [Escolhendo um transporte](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Estendendo associações](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Associações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
