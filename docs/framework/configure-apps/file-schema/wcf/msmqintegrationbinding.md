---
title: '&lt;msmqIntegrationBinding&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- msmqIntegrationBinding Element
ms.assetid: edf277f3-e3bf-4ed8-9f55-83b5788430a7
ms.openlocfilehash: 1493cb6f9588ee618b085186b3bb63476a9a8930
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48841012"
---
# <a name="ltmsmqintegrationbindinggt"></a>&lt;msmqIntegrationBinding&gt;
Define uma associação que dá suporte de enfileiramento de mensagens, roteamento de mensagens por meio do MSMQ.  
  
 \<system.ServiceModel>  
\<associações >  
msmqIntegrationBinding  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<msmqIntegrationBinding>  
   <binding   
       closeTimeout="TimeSpan"   
       customDeadLetterQueue="Uri"  
       deadLetterQueue="Uri"  
       durable="Boolean"  
       exactlyOnce="Boolean"   
       maxReceivedMessageSize"Integer"  
       maxRetryCycles="Integer"   
       name="string"   
       openTimeout="TimeSpan"        receiveContextEnabled="Boolean"  
       receiveErrorHandling="Drop/Fault/Move/Reject"  
       receiveTimeout="TimeSpan"   
       receiveRetryCount="Integer"  
       retryCycleDelay="TimeSpan"    
       sendTimeout="TimeSpan"   
       serializationFormat="XML/Binary/ActiveX/ByteArray/Stream">  
       timeToLive="TimeSpan"    
       useMsmqTracing="Boolean  
       useSourceJournal="Boolean"  
   </binding>  
</msmqIntegrationBinding>   
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|closeTimeout|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação close. Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>. O padrão é 01:00:00.|  
|customDeadLetterQueue|Um URI que contém o local da fila de mensagens mortas por aplicativo, em que as mensagens que expiraram ou tiveram uma falha de transferência ou entrega são colocadas.<br /><br /> A fila de mensagens mortas é uma fila no Gerenciador de fila do aplicativo de envio para mensagens expiradas que falharam ao ser entregue.<br /><br /> O URI que é especificado pelo <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> deve usar o esquema de NET. MSMQ.|  
|deadLetterQueue|Um <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>. Value especificando o tipo de fila de inatividade para usar, se houver<br /><br /> Uma fila de inatividade é o local que as mensagens que falharam ao ser entregue ao aplicativo serão transferidas.<br /><br /> Para mensagens que exigem a garantia de exactlyOnce (isto é, o `exactlyOnce` atributo é definido como `true`), esse atributo usa como padrão para a fila de inatividade transacional em todo o sistema em MSMQ.<br /><br /> Para mensagens que não exigem garantias de nenhum, esse atributo é padronizado como `null`.|  
|duráveis|Um valor booliano que indica se a mensagem é duráveis ou voláteis na fila. Uma mensagem durável sobrevive a uma falha do Gerenciador de fila, enquanto uma mensagem volátil não. Mensagens voláteis são úteis quando aplicativos exigem uma latência mais baixa e podem tolerar mensagens perdidas ocasionais. Se o `exactlyOnce` atributo é definido como `true`, as mensagens devem ser duráveis. O padrão é `true`.|  
|exactlyOnce|Um valor booliano que indica se cada mensagem seja entregue somente uma vez. O remetente, em seguida, será notificado sobre falhas de entrega. Quando `durable` é `false`, esse atributo é ignorado e as mensagens são transferidas sem garantia de entrega. O padrão é `true`. Para obter mais informações, consulte <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A>.|  
|maxReceivedMessageSize|Um inteiro positivo que define o tamanho máximo da mensagem, em bytes, incluindo os cabeçalhos, que é processado por essa associação. O remetente de uma mensagem exceder esse limite receberá uma falha de SOAP. O receptor descartará a mensagem e cria uma entrada do evento no log de rastreamento. O padrão é 65536. Este limite no tamanho da mensagem se destina a limitar a exposição a ataques de negação de serviço (DoS).|  
|maxRetryCycles|Um inteiro que indica o número de ciclos de repetição usada pelo recurso de detecção de mensagens suspeitas. Uma mensagem se torna uma mensagem suspeita quando ele falhar todas as tentativas de entrega de todos os ciclos. O padrão é 2. Para obter mais informações, consulte <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>.|  
|name|Uma cadeia de caracteres que contém o nome da configuração da associação. Esse valor deve ser exclusivo porque ele é usado como identificação para a associação. Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome. Para obter mais informações sobre a configuração padrão e sem nome associações e comportamentos, consulte [configuração simplificado](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação open. Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>. O padrão é 01:00:00.|  
|receiveErrorHandling|Um <xref:System.ServiceModel.ReceiveErrorHandling> valor que especifica como mensagens suspeitas e nondispatchable são tratadas.|  
|receiveRetryCount|Um inteiro que especifica o número máximo de novas tentativas imediatas o Gerenciador de fila deve tentar se a transmissão de uma mensagem da fila de aplicativos para o aplicativo falhar.<br /><br /> Se o número máximo de tentativas de entrega for atingido e a mensagem não é acessada pelo aplicativo, a mensagem é enviada para uma fila de repetição para nova entrega em um momento posterior. A quantidade de tempo antes que a mensagem é transferida de volta para a fila de envio é controlada pelo `retryCycleDelay`. Se os ciclos de repetição alcance o `maxRetryCycles` de valor, em seguida, a mensagem será enviada para a fila de mensagens suspeitas, ou uma confirmação negativa é enviada de volta ao remetente.|  
|receiveTimeout|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de recebimento ser concluída. Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>. O padrão é 10:00:00.|  
|receiveContextEnabled|Um valor booleano que especifica se o contexto de recebimento para processar mensagens em filas está habilitado. Quando isso é definido como `true`, um serviço pode "espiada" uma mensagem na fila para começar a processá-la e, se algo der errado, e uma exceção é lançada, ele permanecerá na fila. Os serviços também podem "bloquear" mensagens para repetir o processamento em um momento posterior no tempo. ReceiveContext fornece um mecanismo para "Concluir" a mensagem processada uma vez para que ele pode ser removido da fila. Mensagens não estão sendo lidos e gravadas novamente para filas na rede e as mensagens individuais não são saltando em instâncias de serviço diferentes durante o processamento.|  
|retryCycleDelay|Um valor de TimeSpan que especifica o tempo de espera entre ciclos ao tentar entregar uma mensagem que não pôde ser entregue imediatamente. O valor define somente o mínimo tempo de espera porque o tempo de espera real pode ser maior. O valor padrão é 30:00:00. Para obter mais informações, consulte <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A>.|  
|sendTimeout|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de envio ser concluída. Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>. O padrão é 01:00:00.|  
|serializationFormat|Define o formato usado para serialização do corpo da mensagem. Esse atributo é do tipo <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat>.|  
|timeToLive|Um valor de TimeSpan que especifica quanto tempo as mensagens são válidas antes de expirarem e coloque na fila de inatividade. O padrão é 1.00:00:00.<br /><br /> Esse atributo é definido para garantir que as mensagens de detecção de hora não tornam-se obsoletos antes que eles são processados por aplicativos de recebimento. Diz-se que uma mensagem em uma fila que não é consumida pelo aplicativo de recebimento dentro do intervalo de tempo especificado expirar. As mensagens expiradas são enviadas à fila especial chamada a fila de mensagens mortas. O local da fila de mensagens mortas é definido com o `DeadLetterQueue` de atributo ou como o padrão apropriado, com base em garantias.|  
|useMsmqTracing|Um valor booliano que especifica se as mensagens processadas por essa associação deve ser rastreado. O padrão é `false`. Quando o rastreamento está habilitado, as mensagens de relatório são criadas e enviadas para a fila de relatórios sempre que a mensagem sai ou chega a um computador do serviço de enfileiramento de mensagens.|  
|useSourceJournal|Um valor booliano que especifica as cópias de mensagens processadas por essa associação deve ser armazenado no diário de origem. O padrão é `false`.<br /><br /> Aplicativos em fila que deseja manter um registro de mensagens que deixaram a fila de saída do computador podem copiar as mensagens para uma fila do diário. Depois que uma mensagem deixa a fila de saída e uma confirmação for recebida, que a mensagem foi recebida no computador de destino, uma cópia da mensagem é mantida na fila de diário do sistema do computador de envio.|  
  
## <a name="serializationformat-attribute"></a>{serializationFormat} Atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Xml|Formato XML|  
|Binário|Formato binário|  
|ActiveX|Formato do ActiveX|  
|ByteArray|Serializa o objeto em uma matriz de bytes.|  
|Fluxo|O corpo formatado como um fluxo|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-msmqintegrationbinding.md)|Define as configurações de segurança para a associação. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<associações >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Esse elemento contém uma coleção de associações padrão e personalizadas.|  
  
## <a name="remarks"></a>Comentários  
 Este elemento de associação pode ser usado para permitir que os aplicativos do Windows Communication Foundation (WCF) enviar e receber mensagens de aplicativos MSMQ existentes que usam COM, APIs nativas do MSMQ ou os tipos definidos na <xref:System.Messaging?displayProperty=nameWithType> namespace você pode usar este elemento de configuração para especificar as maneiras de abordar a fila, garantias de transferência, se as mensagens devem ser armazenadas permanentemente, e como as mensagens devem ser protegidas e autenticadas. Para obter mais informações, consulte [como: troca de mensagens com pontos de extremidade do WCF e aplicativos de enfileiramento de mensagem](../../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md).  
  
## <a name="example"></a>Exemplo  
  
```xml  
<configuration>  
<system.ServiceModel>  
    <bindings>  
       <msmqIntegrationBinding>  
           <binding   
                    closeTimeout="00:00:10"   
                    openTimeout="00:00:20"   
                    receiveTimeout="00:00:30"   
                    sendTimeout="00:00:40"   
                    deadLetterQueue="net.msmq://localhost/blah"   
                    durable="true"   
                    exactlyOnce="true"   
                    maxReceivedMessageSize="1000"   
                    maxImmediateRetries="11"   
                    maxRetryCycles="12"  
                    poisonMessageHandling="Disabled"   
                    rejectAfterLastRetry="false"   
                    retryCycleDelay="00:05:55"   
                    timeToLive="00:11:11"   
                    useSourceJournal="true"   
                    useMsmqTracing="true"   
                    serializationFormat="Binary">  
                    <security mode="None" />  
           </binding>  
       </msmqIntegrationBinding  
   </bindings>  
</system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>  
 [\<associação >](../../../../../docs/framework/misc/binding.md)  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Configurando associações fornecidas pelo sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Usando associações para configurar serviços e clientes](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [Filas no WCF](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
