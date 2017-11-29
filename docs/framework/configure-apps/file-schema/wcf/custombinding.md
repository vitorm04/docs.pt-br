---
title: '&lt;customBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9da4f960-f64e-4d8a-894d-2b09eba5ce4b
caps.latest.revision: "24"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7f73ad4d09e085040e006102e5b44664ece98a58
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcustombindinggt"></a>&lt;customBinding&gt;
Fornece controle total sobre a pilha de mensagens para o usuário.  
  
 \<System. ServiceModel >  
\<associações >  
\<customBinding >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<customBinding>  
    <binding name="string"  
        closeTimeout="TimeSpan"  
        openTimeout="TimeSpan"   
        receiveTimeout="TimeSpan"  
        sendTimeout="TimeSpan"  
       <compositeDuplex clientBaseAddress="Uri"/>  
       <reliableSession acknowledgementInterval="TimeSpan"  
           advancedFlowControl="Boolean"   
           bufferedMessagesQuota="Integer"  
           inactivityTimeout="TimeSpan"  
           maxPendingChannels="Integer"  
           maxRetryCount="Integer"   
           ordered="Boolean" />  
       <pnrpPeerResolver />  
       <windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign"/>  
       <sslStreamSecurity requireClientCertificate="Boolean" />  
              <transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"/>  
       <security   
          defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
           authenticationMode="UserNameForAnonymous"  
           contextMode="Cookie"   
           defaultProtectionLevel="Sign"  
           enableKeyDerivation="false"  
           keyEntropyMode="ClientEntropy"   
                  messageProtectionOrder="SignBeforeEncryptAndEncryptSignature"   
           securityVersion="WSSecurityXXX2005">  
           <localClientSettings cacheCookies="false"  
               detectReplays="false"  
               maxCookieCachingTime="00:07:24" />  
           <localServiceSettings replayCacheSize="9"  
               maxClockSkew="00:00:03"   
               replayWindow="00:07:22.2190000" />  
       </security>  
       <binaryMessageEncoding maxReadPoolSize="Integer"  
           maxWritePoolSize="Integer"  
           maxSessionSize="Integer" />  
       <httpsTransport manualAddressing="Boolean"  
           maxMessageSize="Integer"  
           authenticationScheme="Negotiate"   
           bypassProxyOnLocal="Boolean"  
           hostNameComparisonMode="Exact"   
           mapAddressingHeadersToHttpHeaders="Boolean"   
           proxyaddress="Uri"  
           realm="String"   
           requireClientCertificate="Boolean" />  
       <peerTransport manualAddressing="false"  
          maxMessageSize="20002"  
          listenIPAddress="202.10.1.9"   
          messageAuthentication="false"  
          peerNodeAuthenticationMode="None"  
          port="1000" />  
  
<security   
      defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
   authenticationMode="UserNameForAnonymous"  
   bootstrapBindingConfiguration="String"  
   bootstrapBindingSectionName="String"  
   defaultProtectionLevel="None/Sign/EncryptAndSign"  
      requireDerivedKeys="Boolean"  
   securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"  
   includeTimestamp="Boolean"  
   keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"   
   messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"   
   protectTokens="Boolean"  
   requireSecurityContextCancellation="Boolean"  
   securityVersion=" WSSecurityJan2004/WSSecurityXXX2005"  
   requireSignatureConfirmation="Boolean" >  
   <localClientSettings cacheCookies="Boolean"  
      detectReplays="Boolean"  
      replayCacheSize="Integer"  
      maxClockSkew="TimeSpan"  
      maxCookieCachingTime="TimeSpan"  
      replayWindow="TimeSpan"  
      sessionKeyRenewalInterval="TimeSpan"  
      sessionKeyRolloverInterval="TimeSpan"  
      reconnectOnTransportFailure="Boolean"  
      timestampValidityDuration="TimeSpan"  
      cookieRenewalThresholdPercentage="Integer" />  
   <localServiceSettings detectReplays="Boolean"  
      issuedCookieLifeTime="TimeSpan"  
      maxStatefulNegotiations="Integer"  
            replayCacheSize="Integer"  
      maxClockSkew="TimeSpan"   
      negotiationTimeout="TimeSpan"  
      replayWindow="TimeSpan"  
      inactivityTimeout="TimeSpan"  
      sessionKeyRenewalInterval="TimeSpan"  
      sessionKeyRolloverInterval="TimeSpan"  
      reconnectOnTransportFailure="Boolean"  
      maxConcurrentSessions="Integer"  
      timestampValidityDuration="TimeSpan" />  
   <federationParameters trustVersion="WSTrustApr2004/WSTrustFeb2005" />  
<security   
   defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/ Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
   authenticationMode="UserNameForAnonymous"  
   bootstrapBindingConfiguration="String"  
   bootstrapBindingSectionName="String"  
   defaultProtectionLevel="None/Sign/EncryptAndSign"  
      requireDerivedKeys="Boolean"  
   securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"  
   includeTimestamp="Boolean"  
   keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"   
   messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"   
   protectTokens="Boolean"  
   requireSecurityContextCancellation="Boolean"  
   securityVersion=" WSSecurityJan2004/WSSecurityXXX2005"  
   requireSignatureConfirmation="Boolean" >  
   <localClientSettings cacheCookies="Boolean"  
      detectReplays="Boolean"  
      replayCacheSize="Integer"  
      maxClockSkew="TimeSpan"  
      maxCookieCachingTime="TimeSpan"  
      replayWindow="TimeSpan"  
      sessionKeyRenewalInterval="TimeSpan"  
      sessionKeyRolloverInterval="TimeSpan"  
      reconnectOnTransportFailure="Boolean"  
      timestampValidityDuration="TimeSpan"  
      cookieRenewalThresholdPercentage="Integer" />  
   <localServiceSettings detectReplays="Boolean"  
      issuedCookieLifeTime="TimeSpan"  
      maxStatefulNegotiations="Integer"  
            replayCacheSize="Integer"  
      maxClockSkew="TimeSpan"   
      negotiationTimeout="TimeSpan"  
      replayWindow="TimeSpan"  
      inactivityTimeout="TimeSpan"  
      sessionKeyRenewalInterval="TimeSpan"  
      sessionKeyRolloverInterval="TimeSpan"  
      reconnectOnTransportFailure="Boolean"  
      maxConcurrentSessions="Integer"  
      timestampValidityDuration="TimeSpan" />  
   <federationParameters trustVersion="WSTrustApr2004/WSTrustFeb2005" />  
   <GenericIssuedTokenParameters>   
      <LocalIssuerIssuedTokenParameters keyType=" SymmeticKey/PublicKey"  
        keySize="Integer"  
        tokenType="String" />  
     <IssuedTokenParametersEndpointAddress address="URI"  
        bindingConfiguration="String"  
        binding="String" />  
     <IssuedTokenClient localIssuerChannelBehaviors="String"  
        cacheIssuedTokens="Boolean"  
        maxIssuedTokenCachingTime="TimeSpan"  
        keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy" />  
     <IssuedTokenClientBehavior issuerAddress="String"  
        behaviorConfiguration="String" />  
     <IssuedTokenClientBehavior address="URI"  
        bindingConfiguration="String"  
        binding="String" />  
   </GenericIssuedTokenParameters>   
</security>  
</binding>  
</customBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem os elementos pai de atributos e elementos filho  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|closeTimeout|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de fechamento concluir. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
|name|Uma cadeia de caracteres que contém o nome da configuração da associação. Esse valor é uma cadeia de caracteres definida pelo usuário que age como a cadeia de caracteres de identificação para a associação personalizada. Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome. Para obter mais informações sobre a configuração padrão e associações de nomes e comportamentos, consulte [configuração simplificada](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de abertura concluir. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
|receiveTimeout|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de recebimento concluir. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
|sendTimeout|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de envio concluir. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<compositeDuplex >](../../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)|Especifica a mensagem bidirecional para a associação personalizada. Ele é usado com transportes que não permitem a comunicação duplex nativamente, por exemplo, HTTP. TCP, por outro lado, permite a comunicação duplex nativamente e não requer o uso desse elemento de associação para o serviço enviar mensagens para um cliente.<br /><br /> O cliente deve expor um endereço para o serviço fazer contato e estabelecer uma conexão. Este endereço de cliente é fornecido pelo `ClientBaseAddress` atributo.<br /><br /> Esse elemento é do tipo <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.|  
|[\<pnrpPeerResolver >](../../../../../docs/framework/configure-apps/file-schema/wcf/pnrppeerresolver.md)|Especifica um resolvedor de nome de ponto de resolução protocolo PNRP (Peer Name). Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.|  
|[\<reliableSession >](../../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md)|Especifica a configuração para mensagens WS-Reliable. Quando esse elemento é adicionado a uma associação personalizada, o canal resultante pode dar suporte a exatamente-uma vez garantias de entrega. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.ReliableSessionElement>.|  
|[\<segurança >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|Especifica as opções de segurança da associação personalizada. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.SecurityElement>.|  
|[\<sslStreamSecurity >](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)|Especifica as configurações de segurança para uma associação de fluxo SSL. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.|  
|[\<transactionFlow >](../../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md)|Especifica que a associação oferece suporte a fluxo de transações e o protocolo a ser usado pelo `transactionProtocol` atributo. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.TransactionFlowElement>.|  
|[\<windowsstreamsecurity está >](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md)|Especifica as opções de segurança da associação personalizada de streaming. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|associações|Contém todas as associações de aplicativos do Windows Communication Foundation.|  
  
## <a name="remarks"></a>Comentários  
 Associações personalizadas fornecem controle total sobre a pilha de mensagens do WCF. Associações personalizadas especiais podem ser criadas meu adicionando os elementos de configuração para entidades específicas. Por exemplo, o usuário pode combinar o `httpsTransport` seção, `reliableSession` seção e `security` seção para criar um https segura e confiável com base em associação.  
  
 Uma associação individual define a pilha de mensagem, especificando os elementos de configuração para os elementos da pilha na ordem em que aparecem na pilha. Cada elemento define e configura um elemento da pilha. Deve haver apenas um elemento de transporte em cada associação personalizada. Sem esse elemento, a pilha de mensagens está incompleta.  
  
 A ordem na qual os elementos aparecem na pilha é importante, porque é a ordem na qual as operações são aplicadas à mensagem. A ordem recomendada de elementos da pilha é o seguinte:  
  
1.  Transações (opcionais)  
  
2.  Confiável de mensagens (opcional)  
  
3.  Segurança (opcional)  
  
4.  Transporte  
  
5.  Codificador (opcional)  
  
 Use uma associação personalizada quando uma das associações fornecidas pelo sistema não atende aos requisitos de seu serviço. Uma associação personalizada pode ser usada, por exemplo, para habilitar o uso de um novo transporte ou um codificador de novo em um ponto de extremidade de serviço.  
  
 Uma associação personalizada é criada usando uma da <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> de uma coleção de elementos que estão "empilhados" em uma ordem específica de associação:  
  
-   Na parte superior é um recurso opcional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> que permite o fluxo de transações.  
  
-   Em seguida, é um recurso opcional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> que fornece uma sessão e o mecanismo de ordenação conforme definido na especificação WS-ReliableMessaging. Essa noção de uma sessão pode cruzar com intermediários SOAP e transporte.  
  
-   Em seguida, é um elemento de associação de segurança opcional que fornece recursos de segurança como autenticação, autorização, proteção e confidencialidade. Os seguintes elementos de associação de segurança são fornecidos por [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]:  
  
    -   <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
-   Em seguida os padrões de mensagem opcionais são especificados pelos elementos de associação:  
  
-   <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>  
  
-   Em seguida os upgrades/auxiliares de transporte opcional são elementos de associação:  
  
    -   <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
-   Em seguida, é um elemento de associação de codificação de mensagem necessário. Você pode usar seu próprio transporte ou usar uma codificação associações a mensagem a seguir:  
  
    -   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
  
-   Na parte inferior é um elemento de transporte necessário. Você pode usar seu próprio transporte ou use um dos elementos fornecidos por de associação de transporte [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]:  
  
    -   <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>  
  
    -   <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
  
 A tabela a seguir resume as opções para cada camada.  
  
|Camada|Opções|Necessária|  
|-----------|-------------|--------------|  
|Fluxo de transações|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|Não|  
|Confiabilidade|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|Não|  
|Segurança|Simétrica, assimétrica, nível de transporte|Não|  
|Alteração de forma|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>|Não|  
|Atualizações de transporte|Fluxo SSL, fluxo do Windows, resolvedor Peer|Não|  
|Codificando|Texto, binária, MTOM, personalizado|Sim|  
|Transporte|Tipos HTTP, HTTPS, TCP, Pipes nomeados, do MSMQ, personalizadas|Sim|  
  
 Além disso, você pode definir seus próprios elementos de associação e inseri-los entre qualquer uma das camadas de definido anteriores.  
  
 Para obter uma discussão sobre como usar uma associação para modificar uma associação fornecida pelo sistema personalizada, consulte [como: personalizar uma associação System-Provided](../../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).  
  
1.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.Configuration.BindingsSection>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [\<associação >](../../../../../docs/framework/misc/binding.md)  
 [Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)  
 [Estendendo associações](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Associações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [customBinding elemento](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)  
 [Configurando associações fornecidas pelo sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Usando associações para configurar clientes e serviços do Windows Communication Foundation](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)
