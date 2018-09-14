---
title: '&lt;netTcpBinding&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- netTcpBinding Element
ms.assetid: 5c5104a7-8754-4335-8233-46a45322503e
ms.openlocfilehash: e8ac320c1edde05074d42652a708320d10690550
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45528319"
---
# <a name="ltnettcpbindinggt"></a>&lt;netTcpBinding&gt;
Especifica uma associação segura, confiável e otimizada adequada para comunicação entre computadores. Por padrão, ele gera uma pilha de comunicação em tempo de execução com a segurança do Windows para autenticação, TCP para entrega de mensagens e codificação de mensagem binária e de segurança de mensagem.  
  
 \<system.ServiceModel>  
\<associações >  
\<netTcpBinding>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<netTcpBinding>  
   <binding   
      closeTimeout="TimeSpan"  
      hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
      listenBacklog="Integer"  
      maxBufferPoolSize="integer"  
      maxBufferSize="Integer"  
      maxConnections="Integer"   
      maxReceivedMessageSize="Integer"  
      name="string"  
      openTimeout="TimeSpan"  
      portSharingEnabled="Boolean"  
      receiveTimeout="TimeSpan"  
      sendTimeout="TimeSpan"  
      transactionFlow="Boolean"   
      transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"   
            transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
  
      <reliableSession ordered="Boolean"  
            inactivityTimeout="TimeSpan"  
            enabled="Boolean" />  
      <security mode="None/Transport/Message/Both">  
            <message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"  
                defaultProtectionLevel="None/Sign/EncryptAndSign"   
algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />  
            <transport clientCredentialType="None/Windows/Certificate"  
                protectionLevel="None/Sign/EncryptAndSign" />  
      </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />   </binding>  
</netTcpBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|closeTimeout|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação close. Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>. O padrão é 01:00:00.|  
|hostnameComparisonMode|Especifica o modo de comparação de nome de host HTTP usado para analisar URIs. Esse atributo é do tipo `System.ServiceModel.HostnameComparisonMode`, que indica se o nome do host é usado para acessar o serviço ao fazer a correspondência no URI. O valor padrão é `StrongWildcard`, que ignora o nome do host na correspondência.|  
|listenBacklog|Um inteiro positivo que especifica o número máximo de canais esperando para serem aceitos no ouvinte. As conexões que excede esse limite são enfileiradas até que o espaço abaixo do limite fica disponível. O `connectionTimeout` atributo limita o tempo que um cliente irá esperar para ser conectado antes de lançar uma exceção de conexão. O padrão é 10.|  
|maxBufferPoolSize|Um inteiro que especifica o tamanho do pool de buffer máximo para esta associação. O padrão é 512 * 1024 bytes. Muitas partes do Windows Communication Foundation (WCF) usam buffers. Criação e destruição de buffers de cada vez que elas são usadas são caro e coleta de lixo para buffers também é dispendiosa. Com os pools de buffer, usar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar. Portanto, a sobrecarga na criação e destruição de buffers é evitada.|  
|maxBufferSize|Um inteiro positivo que especifica o tamanho máximo, em bytes, do buffer usado para armazenar mensagens na memória.<br /><br /> Se o `transferMode` atributo é igual a `Buffered`, esse atributo deve ser igual ao `maxReceivedMessageSize` valor do atributo.<br /><br /> Se o `transferMode` atributo é igual a `Streamed`, esse atributo não pode ser mais do que o `maxReceivedMessageSize` valor do atributo, e deve ser pelo menos o tamanho dos cabeçalhos.<br /><br /> O padrão é 65536. Para obter mais informações, consulte <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.|  
|maxConnections|Um inteiro que especifica o número máximo de conexões de entrada e saídas de serviço cria/aceitará. Conexões de entrada e saídas são contadas em relação a um limite separado especificado por este atributo.<br /><br /> Conexões de entrada que excede o limite são enfileiradas até que um espaço abaixo do limite fica disponível.<br /><br /> Conexões de saída que excede o limite são enfileiradas até que um espaço abaixo do limite fica disponível.<br /><br /> O padrão é 10.|  
|maxReceivedMessageSize|Um inteiro positivo que especifica o tamanho máximo da mensagem, em bytes, incluindo os cabeçalhos, que podem ser recebidos em um canal configurado com essa associação. O remetente de uma mensagem exceder esse limite receberá uma falha de SOAP. O receptor descartará a mensagem e cria uma entrada do evento no log de rastreamento. O padrão é 65536.|  
|name|Uma cadeia de caracteres que contém o nome da configuração da associação. Esse valor deve ser exclusivo porque ele é usado como identificação para a associação. Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome. Para obter mais informações sobre a configuração padrão e sem nome associações e comportamentos, consulte [configuração simplificado](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação open. Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>. O padrão é 01:00:00.|  
|portSharingEnabled|Um valor booliano que especifica se o compartilhamento de porta TCP está habilitado para esta conexão. Quando se trata de `false`, cada associação usa sua própria porta exclusiva. Essa configuração é relevante apenas para serviços, porque os clientes não são afetados.|  
|receiveTimeout|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de recebimento ser concluída. Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>. O padrão é 10:00:00.|  
|sendTimeout|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de envio ser concluída. Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>. O padrão é 01:00:00.|  
|transactionFlow|Um valor booliano que especifica se a associação dá suporte a fluxo de WS-Transactions. O padrão é `false`.|  
|transactionProtocol|Especifica o protocolo de transação a ser usado com essa associação. Os valores válidos são<br /><br /> -OleTransactions<br />-   WSAtomicTransactionOctober2004<br /><br /> O padrão é OleTransactions. Esse atributo é do tipo <xref:System.ServiceModel.TransactionProtocol>.|  
|transferMode|Um <xref:System.ServiceModel.TransferMode> valor que especifica se as mensagens são armazenadas em buffer ou transmitidas ou uma solicitação ou resposta.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|Define as configurações de segurança para a associação. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>.|  
|[\<readerQuotas>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Define as restrições na complexidade das mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[reliableSession](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|Especifica se as sessões confiáveis são estabelecidas entre pontos de extremidade de canal.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<associações >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Esse elemento contém uma coleção de associações padrão e personalizadas.|  
  
## <a name="remarks"></a>Comentários  
 Essa associação gera uma pilha de comunicação de tempo de execução por padrão, que usa segurança de transporte TCP para entrega de mensagens e uma codificação de mensagem binária. Essa associação é uma Windows Communication Foundation (WCF) fornecida pelo sistema opção apropriada para se comunicar através de uma Intranet.  
  
 A configuração padrão para o `netTcpBinding` é mais rápido que a configuração fornecida pelo `wsHttpBinding`, mas é destinada apenas para comunicação do WCF. O comportamento de segurança é configurável usando opcional `securityMode` atributo. O uso de WS-ReliableMessaging é configurável usando opcional `reliableSessionEnabled` atributo. Mas o sistema de mensagens confiável está desativado por padrão. De modo geral, as HTTP associações fornecidas pelo sistema, como `wsHttpBinding` e `basicHttpBinding` são configurados para ativar as coisas por padrão, enquanto o `netTcpBinding` associação desativa as coisas por padrão para que você precise opt-in para obter suporte, por exemplo, para um dos o WS-* especificações. Isso significa que a configuração padrão para TCP mais rápida na troca de mensagens entre pontos de extremidade que aquelas configuradas para as ligações HTTP por padrão.  
  
## <a name="example"></a>Exemplo  
 A associação é especificada nos arquivos de configuração para o cliente e o serviço. O tipo de associação é especificado na `binding` atributo do `<endpoint>` elemento. Se você quiser configurar a associação netTcpBinding e alterar algumas de suas configurações, é necessário definir uma configuração de associação. O ponto de extremidade deve fazer referência a configuração de ligação com um `bindingConfiguration` atributo. No exemplo a seguir, uma configuração de associação é definida.  
  
```xml  
<services>  
  <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
    ...  
    <endpoint address=""  
              binding="netTcpBinding"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    ...  
  </service>  
</services>  
  
<bindings>  
  <netTcpBinding>  
    <binding   
             closeTimeout="00:01:00"  
             openTimeout="00:01:00"   
             receiveTimeout="00:10:00"   
             sendTimeout="00:01:00"  
             transactionFlow="false"   
             transferMode="Buffered"   
             transactionProtocol="OleTransactions"  
             hostNameComparisonMode="StrongWildcard"   
             listenBacklog="10"  
             maxBufferPoolSize="524288"   
             maxBufferSize="65536"   
             maxConnections="10"  
             maxReceivedMessageSize="65536">  
      <readerQuotas maxDepth="32"   
                    maxStringContentLength="8192"   
                    maxArrayLength="16384"  
                    maxBytesPerRead="4096"   
                    maxNameTableCharCount="16384" />  
      <reliableSession ordered="true"   
                       inactivityTimeout="00:10:00"  
                       enabled="false" />  
      <security mode="Transport">  
        <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign" />  
      </security>  
    </binding>  
  </netTcpBinding>  
</bindings>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.NetTcpBinding>  
 <xref:System.ServiceModel.Configuration.NetTcpBindingElement>  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Configurando associações fornecidas pelo sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Usando associações para configurar clientes e serviços do Windows Communication Foundation](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<associação >](../../../../../docs/framework/misc/binding.md)
