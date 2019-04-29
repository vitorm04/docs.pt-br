---
title: <security> de <customBinding>
ms.date: 03/30/2017
ms.assetid: 243a5148-bbd1-447f-a8a5-6e7792c0a3f1
ms.openlocfilehash: ffe791d495a4e06c9649dd0c37d0fd010e2c64bb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670560"
---
# <a name="security-of-custombinding"></a>\<segurança > de \<customBinding >
Especifica as opções de segurança para uma associação personalizada.  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<binding>  
\<segurança >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<security allowSerializedSigningTokenOnReply="Boolean"
          authenticationMode="AuthenticationMode"
          defaultAlgorithmSuite="SecurityAlgorithmSuite"
          includeTimestamp="Boolean"
          requireDerivedKeys="Boolean"
          keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
          messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"
          messageSecurityVersion="WSSecurityJan2004/WSSecurityXXX2005"
          requireDerivedKeys="Boolean"
          requireSecurityContextCancellation="Boolean"
          requireSignatureConfirmation="Boolean"
          securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast">
   <issuedTokenParameters />
   <localClientSettings />
   <localServiceSettings />
   <secureConversationBootstrap />
</security>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|allowSerializedSigningTokenOnReply|Opcional. Um valor booliano que especifica se um token serializado pode ser usado na resposta. O valor padrão é `false`. Ao usar uma associação de dupla, a configuração padrão é `true` e qualquer configuração feita será ignorada.|  
|authenticationMode|Opcional. Especifica o modo de autenticação usado entre o iniciador e o respondente. Consulte abaixo para todos os valores.<br /><br /> O padrão é `sspiNegotiated`.|  
|defaultAlgorithmSuite|Opcional. Define a mensagem de algoritmos de criptografia e encapsulamento de chave. Os algoritmos e os tamanhos de chave são determinados pelo <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> classe. Esses algoritmos são mapeados para aqueles especificados na especificação da linguagem de política de segurança (WS-SecurityPolicy).<br /><br /> Os valores possíveis são mostrados abaixo. O valor padrão é `Basic256`.<br /><br /> Este atributo é usado ao trabalhar com uma plataforma diferente que aceita para um conjunto de algoritmos diferentes do padrão. Você deve estar atento os pontos fortes e fracos dos algoritmos relevantes ao fazer modificações a essa configuração. Esse atributo é do tipo <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.|  
|includeTimestamp|Um valor booliano que especifica se os carimbos de data / hora é incluídos em cada mensagem. O padrão é `true`.|  
|keyEntropyMode|Especifica a maneira que as chaves para proteger as mensagens são computadas. As chaves podem se basear o material de chave de cliente somente, somente o material de chave de serviço ou uma combinação de ambos. Os valores válidos são<br /><br /> -   `ClientEntropy`: A chave de sessão se baseia em dados de chave fornecidos pelo cliente.<br />-   `ServerEntropy`: A chave de sessão se baseia em dados de chave fornecidos pelo servidor.<br />-   `CombinedEntropy`: A chave de sessão se baseia nos dados de chave fornecidos pelo cliente e serviço.<br /><br /> O padrão é `CombinedEntropy`.<br /><br /> Esse atributo é do tipo <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.|  
|messageProtectionOrder|Define a ordem na qual mensagem algoritmos de segurança em nível são aplicados à mensagem. Os valores válidos incluem o seguinte:<br /><br /> -   `SignBeforeEncrypt`: Entrar pela primeira vez e, em seguida, criptografar.<br />-   `SignBeforeEncryptAndEncryptSignature`: Entrar pela primeira vez, criptografar, criptografar a assinatura.<br />-   `EncryptBeforeSign`: Criptografe primeiro, em seguida, entrada.<br /><br /> O valor padrão depende da versão do WS-Security que está sendo usado. O valor padrão é `SignBeforeEncryptAndEncryptSignature` ao usar o WS-Security 1.1. O valor padrão é `SignBeforeEncrypt` ao usar o WS-Security 1.0.<br /><br /> Esse atributo é do tipo <xref:System.ServiceModel.Security.MessageProtectionOrder>.|  
|messageSecurityVersion|Opcional. Define a versão do WS-Security, o que é usado. Os valores válidos incluem o seguinte:<br /><br /> -   WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11<br />-   WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10<br />-   WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10<br /><br /> O padrão é WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11 e podem ser expressos no XML simplesmente `Default`. Esse atributo é do tipo <xref:System.ServiceModel.MessageSecurityVersion>.|  
|requireDerivedKeys|Um valor booliano que especifica se chaves podem ser derivadas das chaves de prova originais. O padrão é `true`.|  
|requireSecurityContextCancellation|Opcional. Um valor booliano que especifica se contexto de segurança deve ser cancelado e encerrado quando ele não for mais necessário. O padrão é `true`.|  
|requireSignatureConfirmation|Opcional. Um valor booliano que especifica se a confirmação de assinatura de WS-Security está habilitada. Quando definido como `true`, as assinaturas de mensagem são confirmadas pelo respondente.  Quando a ligação personalizada está configurada para certificados mútuos ou ele está configurado para esse atributo usa como padrão de tokens de uso emitido (associações de WSS 1.1) `true`. Caso contrário, o padrão é `false`.<br /><br /> Confirmação de assinatura é usada para confirmar que o serviço está respondendo no reconhecimento total de uma solicitação.|  
|securityHeaderLayout|Opcional. Especifica a ordenação dos elementos no cabeçalho de segurança. Os valores válidos são<br /><br /> -   `Strict`: Itens são adicionados ao cabeçalho de segurança de acordo com o princípio geral de "declarar antes do uso".<br />-   `Lax`: Os itens são adicionados ao cabeçalho de segurança em qualquer ordem que confirme para o WSS: Segurança da Mensagem SOAP.<br />-   `LaxWithTimestampFirst`: Os itens são adicionados ao cabeçalho de segurança em qualquer ordem que confirme para o WSS: Segurança da Mensagem de SOAP, exceto pelo fato de que o primeiro elemento no cabeçalho de segurança precisa ser um elemento wsse:Timestamp.<br />-   `LaxWithTimestampLast`: Os itens são adicionados ao cabeçalho de segurança em qualquer ordem que confirme para o WSS: Segurança da Mensagem de SOAP, exceto pelo fato de que o último elemento no cabeçalho de segurança precisa ser um elemento wsse:Timestamp.<br /><br /> O padrão é `Strict`.<br /><br /> Esse elemento é do tipo <xref:System.ServiceModel.Channels.SecurityHeaderLayout>.|  
  
## <a name="authenticationmode-attribute"></a>authenticationMode atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Cadeia de Caracteres|`AnonymousForCertificate`<br /><br /> `AnonymousForSslNegotiated`<br /><br /> `CertificateOverTransport`<br /><br /> `IssuedToken`<br /><br /> `IssuedTokenForCertificate`<br /><br /> `IssuedTokenForSslNegotiated`<br /><br /> `IssuedTokenOverTransport`<br /><br /> `Kerberos`<br /><br /> `KerberosOverTransport`<br /><br /> `MutualCertificate`<br /><br /> `MutualCertificateDuplex`<br /><br /> `MutualSslNegotiated`<br /><br /> `SecureConversation`<br /><br /> `SspiNegotiated`<br /><br /> `UserNameForCertificate`<br /><br /> `UserNameForSslNegotiated`<br /><br /> `UserNameOverTransport`<br /><br /> `SspiNegotiatedOverTransport`|  
  
## <a name="defaultalgorithm-attribute"></a>defaultAlgorithm atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Basic128|Use criptografia Aes128, Sha1 de resumo da mensagem e Rsa-oaep-mgf1p para encapsulamento de chave.|  
|Basic192|Use a criptografia Aes192, Sha1 para o message digest, Rsa-oaep-mgf1p para encapsulamento de chave.|  
|Basic256|Use a criptografia Aes256, Sha1 para o message digest, Rsa-oaep-mgf1p para encapsulamento de chave.|  
|Basic256Rsa15|Use Aes256 para criptografia de mensagem, Sha1 de resumo da mensagem e Rsa15 para encapsulamento de chave.|  
|Basic192Rsa15|Use Aes192 para criptografia de mensagem, Sha1 de resumo da mensagem e Rsa15 para encapsulamento de chave.|  
|TripleDes|Use a criptografia TripleDes, Sha1 para o message digest, Rsa-oaep-mgf1p para encapsulamento de chave.|  
|Basic128Rsa15|Use Aes128 para criptografia de mensagem, Sha1 de resumo da mensagem e Rsa15 para encapsulamento de chave.|  
|TripleDesRsa15|Use a criptografia TripleDes, Sha1 de resumo da mensagem e Rsa15 para encapsulamento de chave.|  
|Basic128Sha256|Use Aes256 para criptografia de mensagem, o Sha256 para o resumo da mensagem e Rsa-oaep-mgf1p para encapsulamento de chave.|  
|Basic192Sha256|Use Aes192 para criptografia de mensagem, o Sha256 para o resumo da mensagem e Rsa-oaep-mgf1p para encapsulamento de chave.|  
|Basic256Sha256|Use Aes256 para criptografia de mensagem, o Sha256 para o resumo da mensagem e Rsa-oaep-mgf1p para encapsulamento de chave.|  
|TripleDesSha256|Use triplo DES para criptografia de mensagem, o Sha256 para o resumo da mensagem e Rsa-oaep-mgf1p para encapsulamento de chave.|  
|Basic128Sha256Rsa15|Use Aes128 para criptografia de mensagem, o Sha256 para o resumo da mensagem e Rsa15 para encapsulamento de chave.|  
|Basic192Sha256Rsa15|Use Aes192 para criptografia de mensagem, o Sha256 para o resumo da mensagem e Rsa15 para encapsulamento de chave.|  
|Basic256Sha256Rsa15|Use Aes256 para criptografia de mensagem, o Sha256 para o resumo da mensagem e Rsa15 para encapsulamento de chave.|  
|TripleDesSha256Rsa15|Use o triplo DES para criptografia de mensagem, o Sha256 para o resumo da mensagem e Rsa15 para encapsulamento de chave.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|Especifica um token emitido atual. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>.|  
|[\<localClientSettings>](../../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)|Especifica as configurações de segurança de um cliente local para esta associação. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>.|  
|[\<localServiceSettings>](../../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md)|Especifica as configurações de segurança de um serviço local para esta associação. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>.|  
|[\<secureConversationBootstrap>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|Especifica os valores padrão usados para iniciar um serviço de conversa segura.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<binding>](../../../../../docs/framework/misc/binding.md)|Define todos os recursos de associação de associação personalizada.|  
  
## <a name="remarks"></a>Comentários  
 Para obter mais informações sobre como usar esse elemento, consulte [modos de autenticação de SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md) e [como: Criar uma associação personalizada utilizando o SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como configurar a segurança usando uma associação personalizada. Ele mostra como usar uma ligação personalizada para habilitar a segurança em nível de mensagem junto com um transporte seguro. Isso é útil quando um transporte seguro é necessária para transmitir as mensagens entre o cliente e o serviço e ao mesmo tempo as mensagens devem ser seguras no nível da mensagem. Essa configuração não é suportada por associações fornecidas pelo sistema.  
  
 A configuração de serviço define uma associação personalizada que dá suporte à comunicação TCP protegida usando o protocolo TLS/SSL e segurança de mensagem do Windows. A associação personalizada usa um certificado de serviço para autenticar o serviço no nível de transporte e proteger as mensagens durante a transmissão entre cliente e serviço. Isso é feito usando o [ \<sslStreamSecurity >](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) elemento de associação. O certificado do serviço é configurado usando um comportamento de serviço.  
  
 Além disso, a associação personalizada usa segurança de mensagem com o tipo de credencial do Windows - esse é o tipo de credencial padrão. Isso é feito usando o [segurança](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elemento de associação. Cliente e o serviço são autenticados usando a segurança de nível de mensagem se o mecanismo de autenticação Kerberos está disponível. Se o mecanismo de autenticação Kerberos não estiver disponível, a autenticação NTLM é usada. NTLM autentica o cliente para o serviço, mas não autenticar o serviço ao cliente. O [segurança](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elemento de associação está configurado para usar `SecureConversation` authenticationType, o que resulta na criação de uma sessão de segurança no cliente e o serviço. Isso é necessário para habilitar o contrato do serviço duplex trabalhar. Para obter mais informações sobre como executar este exemplo, consulte [segurança de associação personalizado](../../../../../docs/framework/wcf/samples/custom-binding-security.md).  
  
```xml  
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <host>
          <baseAddresses>
            <!-- use following base address -->
            <add baseAddress="net.tcp://localhost:8000/ServiceModelSamples/Service"/>
          </baseAddresses>
        </host>
        <endpoint address=""
                  binding="customBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />
        <!-- the mex endpoint is exposed at net.tcp://localhost:8000/ServiceModelSamples/service/mex -->
        <endpoint address="mex"
                  binding="mexTcpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <bindings>
      <!-- configure a custom binding -->
      <customBinding>
        <binding name="Binding1">
          <security authenticationMode="SecureConversation"
                    requireSecurityContextCancellation="true">
          </security>
          <textMessageEncoding messageVersion="Soap12WSAddressing10"
                               writeEncoding="utf-8" />
          <sslStreamSecurity requireClientCertificate="false" />
          <tcpTransport />
        </binding>
      </customBinding>
    </bindings>
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata />
          <serviceDebug includeExceptionDetailInFaults="False" />
          <serviceCredentials>
            <serviceCertificate findValue="localhost"
                                storeLocation="LocalMachine"
                                storeName="My"
                                x509FindType="FindBySubjectName" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.SecurityElement>
- <xref:System.ServiceModel.Channels.SecurityBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Associações](../../../../../docs/framework/wcf/bindings.md)
- [Estendendo associações](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Associações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [Como: Criar uma associação personalizada utilizando o SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Segurança de associação personalizada](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
