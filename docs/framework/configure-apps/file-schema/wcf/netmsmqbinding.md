---
title: '&lt;netMsmqBinding&gt;'
ms.date: 03/30/2017
ms.assetid: a68b44d7-7799-43a3-9e63-f07c782810a6
ms.openlocfilehash: d4d28a799acecd335d8155a7ae67b6365b3f0023
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltnetmsmqbindinggt"></a>&lt;netMsmqBinding&gt;
Define uma associação enfileirada adequada para comunicação entre computadores.  
  
 \<system.ServiceModel>  
\<associações >  
\<netMsmqBinding>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<netMsmqBinding>  
    <binding   
       closeTimeout="TimeSpan"   
       customDeadLetterQueue="Uri"  
       deadLetterQueue="Uri"  
       durable="Boolean"  
       exactlyOnce="Boolean"   
       maxBufferPoolSize="Integer"  
       maxReceivedMessageSize"Integer"  
       maxRetryCycles="Integer"   
       name="string"   
       openTimeout="TimeSpan"   
       poisonMessageHandling="Disabled/EnabledIfSupported"   
       queueTransferProtocol="Native/Srmp/SrmpSecure"  
       receiveErrorHandling="Drop/Fault/Move/Reject"  
       receiveTimeout="TimeSpan"   
       receiveRetryCount="Integer"  
       rejectAfterLastRetry="Boolean"   
       retryCycleDelay="TimeSpan"    
       sendTimeout="TimeSpan"   
       timeToLive="TimeSpan"    
       useActiveDirectory="Boolean"  
       useMsmqTracing="Boolean  
       useSourceJournal="Boolean"  
          <security>  
                  <message    
                        algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            clientCredentialType="None/Windows/UserName/Certificate/InfoCard "/>  
                  <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"  
            msmqEncryptionAlgorithm="RC4Stream/AES"  
            msmqProtectionLevel="None/Sign/EncryptAndSign"  
            msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
          </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />   </binding></netMsmqBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`closeTimeout`|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de fechamento concluir. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
|`customDeadLetterQueue`|Um URI que contém o local da fila de inatividade por aplicativo, onde as mensagens que expiraram ou tiveram uma falha de transferência ou entrega são colocadas.<br /><br /> Fila de mensagens mortas é uma fila no Gerenciador de fila do aplicativo de envio para mensagens expiradas que falharam ao ser entregue.<br /><br /> O URI que é especificado pelo <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> devem usar o esquema NET. MSMQ.|  
|`deadLetterQueue`|Um <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> valor que especifica o tipo de fila de mensagens mortas a usar, se houver.<br /><br /> Uma fila de mensagens mortas é o local onde as mensagens que falharam a serem enviadas para o aplicativo serão transferidas.<br /><br /> Para mensagens que exigem `exactlyOnce` garantia (ou seja, o `exactlyOnce` atributo é definido como `true`), esse atributo padrão é a fila de mensagens mortas transacional de todo o sistema em MSMQ.<br /><br /> Para mensagens que não exigem nenhuma garantia, esse atributo é padronizado como `null`.|  
|`durable`|Um valor booliano que indica se a mensagem é duráveis ou voláteis na fila. Uma mensagem durável sobrevive a uma falha do Gerenciador de fila, enquanto uma mensagem volátil não. Mensagens voláteis são úteis quando aplicativos necessitam de latência mais baixa e podem tolerar mensagens perdidas ocasionais. Se o `exactlyOnce` atributo é definido como `true`, as mensagens devem ser duráveis. O padrão é `true`.|  
|`exactlyOnce`|Um valor booliano que indica se cada mensagem processada por essa associação é entregue apenas uma vez. O remetente, em seguida, será notificado das falhas de entrega. Quando `durable` é `false`, esse atributo é ignorado e mensagens são transferidas sem garantia de entrega. O padrão é `true`. Para obter mais informações, consulte <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A>.|  
|`maxBufferPoolSize`|Um inteiro que especifica o tamanho do pool de buffer máximo para esta associação. O padrão é 8.|  
|`maxReceivedMessageSize`|Um número inteiro positivo que define o tamanho máximo, em bytes, incluindo os cabeçalhos, que é processado por essa associação. O remetente de uma mensagem exceder esse limite recebem uma falha SOAP. O receptor descartará a mensagem e cria uma entrada do evento no log de rastreamento. O padrão é 65536. Isso associado ao tamanho da mensagem serve para limitar a exposição a ataques dos (negação de serviço).|  
|`maxRetryCycles`|Um inteiro que indica o número de ciclos de repetição usada pelo recurso de detecção de mensagens suspeitas. Uma mensagem se torna uma mensagem suspeita quando falhar todas as tentativas de entrega de todos os ciclos. O padrão é 3. Para obter mais informações, consulte <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>.|  
|`name`|Atributo obrigatório. Uma cadeia de caracteres que contém o nome da configuração da associação. Esse valor deve ser exclusivo, porque ele é usado como uma identificação para a associação. Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome. Para obter mais informações sobre a configuração padrão e associações de nomes e comportamentos, consulte [configuração simplificada](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`openTimeout`|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de abertura concluir. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
|`QueueTransferProtocol`|Uma opção válida <xref:System.ServiceModel.QueueTransferProtocol> valor que especifica o transporte de canal de comunicação em fila que esta associação usa. MSMQ não oferece suporte a endereçamento de Active Directory, ao usar o protocolo de mensagens confiável SOAP. Portanto, você não deve definir esse atributo `Srmp` ou `Srmps` quando o `u``seActiveDirectory` atributo é definido como `true`.|  
|`receiveErrorHandling`|Um <xref:System.ServiceModel.ReceiveErrorHandling> valor que especifica como mensagens suspeitas e nondispatchable são tratadas.|  
|`receiveRetryCount`|Um inteiro que especifica o número máximo de vezes que o Gerenciador de fila deve tentar enviar uma mensagem antes de transferi-lo para a fila de repetição.|  
|`receiveTimeout`|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de recebimento concluir. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:10:00.|  
|`retryCycleDelay`|Um valor TimeSpan que especifica o tempo de espera entre ciclos de tentativa de entregar uma mensagem que não pôde ser entregue imediatamente. O valor define apenas o mínimo tempo de espera porque o tempo de espera real pode ser maior. O valor padrão é 00:10:00. Para obter mais informações, consulte <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A>.|  
|`sendTimeout`|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de envio concluir. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
|`timeToLive`|Um valor TimeSpan que especifica quanto tempo as mensagens são válidos antes de expirarem e colocados na fila de mensagens mortas. O padrão é 1.00:00:00.<br /><br /> Esse atributo é definido para garantir que as mensagens de detecção de hora não tornam-se obsoletos antes que elas são processadas pelos aplicativos de recebimento. Uma mensagem em uma fila que não é consumida pelo aplicativo de recebimento dentro do intervalo de tempo especificado deve ser expirados. As mensagens expiradas são enviadas à fila especial chamada fila de mensagens mortas. O local da fila de mensagens mortas é definido com o `DeadLetterQueue` de atributo ou como o padrão apropriado, com base em garantia.|  
|`usingActiveDirectory`|Um valor booleano que especifica se os endereços de fila devem ser convertidos usando o Active Directory.<br /><br /> Endereços de fila MSMQ podem consistir em nomes de caminho ou nomes de formato direto. Com um nome de formato direto, MSMQ resolve o nome do computador usando o IP, NetBIOS ou DNS. Com um nome de caminho, MSMQ resolve o nome do computador usando o Active Directory.<br /><br /> Por padrão, o Windows Communication Foundation (WCF) na fila transporte converte o URI de uma fila de mensagens para um nome de formato direto. Definindo o `UseActiveDirectory` propriedade como true, um aplicativo pode especificar que o transporte em fila deve resolver o nome do computador usando o Active Directory em vez de DNS, NetBIOS ou IP.|  
|`useMsmqTracing`|Um valor booleano que especifica se as mensagens processadas por essa associação deve ser rastreado. O padrão é `false`. Quando o rastreamento estiver habilitado, as mensagens de relatório criadas e enviadas para a fila de relatórios sempre que a mensagem sai ou chega em um computador do serviço de enfileiramento de mensagens.|  
|`useSourceJournal`|Um valor booleano que especifica as cópias de mensagens processadas por essa associação deve ser armazenado no diário de origem. O padrão é `false`.<br /><br /> Na fila de aplicativos que deseja manter um registro das mensagens que deixaram a fila de saída do computador podem copiar as mensagens para uma fila do diário. Depois que uma mensagem deixa a fila de saída e é recebida uma confirmação que a mensagem foi recebida no computador de destino, uma cópia da mensagem é mantida na fila de diário do sistema do computador de envio.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<readerQuotas>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Define as restrições na complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|Define as configurações de segurança para a associação. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<associações >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Esse elemento contém uma coleção de associações padrão e personalizadas.|  
  
## <a name="remarks"></a>Comentários  
 O `netMsmqBinding` associação oferece suporte para enfileiramento de mensagens utilizando o Microsoft Message Queuing (MSMQ) como um transporte e habilita o suporte para operações de redistribuição e desconectadas de carregamento de aplicativos acoplados de forma flexível, isolamento de falha. Para uma discussão sobre esses recursos, consulte [filas no WCF](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md).  
  
## <a name="example"></a>Exemplo  
  
```xml  
<configuration>  
<system.ServiceModel>  
    <bindings>  
           <netMsmqBinding>  
                <binding   
                         closeTimeout="00:00:10"   
                         openTimeout="00:00:20"   
                         receiveTimeout="00:00:30"  
                         sendTimeout="00:00:40"  
                         deadLetterQueue="net.msmq://localhost/blah"   
                         durable="true"   
                         exactlyOnce="true"   
                         maxReceivedMessageSize="1000"  
                         maxRetries="11"  
                         maxRetryCycles="12"   
                         poisonMessageHandling="Disabled"   
                         rejectAfterLastRetry="false"   
                         retryCycleDelay="00:05:55"   
                         timeToLive="00:11:11"   
                         sourceJournal="true"  
                         useMsmqTracing="true"  
                         useActiveDirectory="true">  
                         <security>  
                             <message clientCredentialType="Windows" />  
                         </security>  
            </netMsmqBinding>  
    </bindings>  
</system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.NetMsmqBinding>  
 <xref:System.ServiceModel.Configuration.NetMsmqBindingElement>  
 [\<associação >](../../../../../docs/framework/misc/binding.md)  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Configurando associações fornecidas pelo sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Usando associações para configurar clientes e serviços do Windows Communication Foundation](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [Filas no WCF](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
