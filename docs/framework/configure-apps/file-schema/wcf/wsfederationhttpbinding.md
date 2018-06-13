---
title: '&lt;wsFederationHttpBinding&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- wsFederationBinding element
ms.assetid: 9c3312b4-2137-4e71-bf3f-de1cf8e9be79
ms.openlocfilehash: d89d0aeb68aed91b28ca7358a6140e171d3b36b2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32759420"
---
# <a name="ltwsfederationhttpbindinggt"></a>&lt;wsFederationHttpBinding&gt;
Define uma associação que dá suporte ao WS-Federation.  
  
 \<system.ServiceModel>  
\<associações >  
elemento FederationBinding  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<wsFederationHttpBinding>  
    <binding   
        bypassProxyOnLocal="Boolean"  
        closeTimeout="TimeSpan"   
        hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"  
        maxBufferPoolSize="integer"  
        maxReceivedMessageSize="integer"  
        messageEncoding="Text/Mtom"   
                name="string"  
        openTimeout="TimeSpan"   
        privacyNoticeAt="Uri"  
        privacyNoticeVersion="Integer"  
        proxyAddress="Uri"   
        receiveTimeout="TimeSpan"  
        sendTimeout="TimeSpan"  
        textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/ Utf8TextEncoding"  
        transactionFlow="Boolean"  
        useDefaultWebProxy="Boolean">  
        <security mode="None/Message/TransportWithMessageCredential">  
         <message   
            algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            issuedTokenType="string"   
            issuedKeyType="SymmetricKey/PublicKey"  
            negotiateServiceCredential="Boolean" >  
            <claimTypeRequirements>  
               <add claimType="URI"  
                    isOptional="Boolean" />  
            </claimTypeRequirements>  
                        <issuer address="Uri" >  
               <headers>  
                  <add name="String"  
                       namespace="String" />  
                          </headers>  
                              <identity>  
                                 <certificate encodedValue="String"/>  
                                <certificateReference findValue="String"   
                                 isChainIncluded="Boolean"  
                            storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
                                  storeLocation="LocalMachine/CurrentUser"  
                                   X509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
                                   <dns value="String"/>  
                                <rsa value="String"/>  
                                <servicePrincipalName value="String"/>  
                                <usePrincipalName value="String"/>  
                              </identity>  
                        </issuer>  
                        <issuerMetadata address=String" >  
               <headers>  
                  <add name="String"  
                       namespace="String" />  
               </headers>  
               <identity>  
                  <certificate encodedValue="String"/>  
                  <certificateReference findValue="String"   
                     isChainIncluded="Boolean"  
                     storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
                     storeLocation="LocalMachine/CurrentUser"  
                     x509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
                  <dns value="String"/>  
                  <rsa value="String"/>  
                  <servicePrincipalName value="String"/>  
                  <usePrincipalName value="String"/>  
               </identity>  
                        </issuerMetadata>  
            <tokenRequestParameters>  
               <xmlElement>  
               </xmlElement>  
            </tokenRequestParameters>  
           </message>  
        </security>  
        <reliableSession ordered="Boolean"  
           inactivityTimeout="TimeSpan"  
           enabled="Boolean" />  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />    </binding>  
</wsFederationBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|bypassProxyOnLocal|Um valor booliano que indica se deve ignorar o servidor proxy para endereços locais. O padrão é `false`.|  
|closeTimeout|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de fechamento concluir. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
|hostnameComparisonMode|Especifica o modo de comparação de nome de host HTTP usado para analisar URIs. Esse atributo é do tipo <xref:System.ServiceModel.HostNameComparisonMode>, que indica se o nome do host é usado para acessar o serviço ao fazer correspondência no URI. O valor padrão é <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, que ignora o nome do host na correspondência.|  
|maxBufferPoolSize|Um inteiro que especifica o tamanho do pool de buffer máximo para esta associação. O padrão é 524.288 bytes (512 * 1024). Muitas partes do Windows Communication Foundation (WCF) usam buffers. Criação e destruição de buffers de cada vez que elas são usadas são caro e coleta de lixo para buffers também é cara. Com os pools de buffer, usar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar. Portanto, a sobrecarga na criação e destruição de buffers é evitada.|  
|maxReceivedMessageSize|Um inteiro positivo que especifica o tamanho máximo, em bytes, incluindo os cabeçalhos, o que podem ser recebidos em um canal configurado com essa associação. O remetente de uma mensagem exceder esse limite recebem uma falha SOAP. O receptor descartará a mensagem e cria uma entrada do evento no log de rastreamento. O padrão é 65536.|  
|messageEncoding|Define o codificador usado para codificar a mensagem. Os valores válidos incluem o seguinte:<br /><br /> -Texto: Use um codificador de mensagem de texto.<br />-Mtom: Use um codificador de mensagem transmissão organização mecanismo 1.0 (MTOM).<br /><br /> O padrão é texto.<br /><br /> Esse atributo é do tipo <xref:System.ServiceModel.WSMessageEncoding>.|  
|name|Uma cadeia de caracteres que contém o nome da configuração da associação. Esse valor deve ser exclusivo, porque ele é usado como uma identificação para a associação. Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome. Para obter mais informações sobre a configuração padrão e associações de nomes e comportamentos, consulte [configuração simplificada](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de abertura concluir. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
|privactyNoticeAt|Uma cadeia de caracteres que especifica um URI no qual o aviso de privacidade está localizado.|  
|privactyNoticeVersion|Um inteiro que especifica a versão do aviso de privacidade atual.|  
|proxyAddress|Um URI que especifica o endereço do proxy HTTP. Se `useDefaultWebProxy` é `true`, essa configuração deve ser `null`. O padrão é `null`.|  
|receiveTimeout|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de recebimento concluir. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:10:00.|  
|sendTimeout|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de envio concluir. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
|textEncoding|Define a codificação a ser usada para emitir mensagens na associação de conjunto de caracteres. Os valores válidos incluem o seguinte:<br /><br /> -BigEndianUnicode: O Unicode BigEndian codificação.<br />-Unicode: codificação de 16 bits.<br />-UTF8: codificação de 8 bits<br /><br /> O padrão é UTF8. Esse atributo é do tipo <xref:System.Text.Encoding>.|  
|transactionFlow|Um valor booleano que especifica se a associação oferece suporte a fluxo de transações de WS. O padrão é `false`.|  
|useDefaultWebProxy|Um valor booliano que indica se o proxy HTTP configurado automaticamente do sistema é usado. O endereço de proxy deve ser `null` (ou seja, não definido) se esse atributo for `true`. O padrão é `true`.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|Define as configurações de segurança para a mensagem. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.|  
|[\<readerQuotas>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Define as restrições na complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[reliableSession](http://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|Especifica se as sessões confiáveis são estabelecidas entre pontos de extremidade de canal.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<associações >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Esse elemento contém uma coleção de associações padrão e personalizadas.|  
  
## <a name="remarks"></a>Comentários  
 Federação é a capacidade de compartilhar identidades entre vários sistemas de autenticação e autorização. Essas identidades podem referir-se a usuários ou computadores. HTTP federado dá suporte à segurança SOAP, bem como a segurança de modo misto, mas ele não oferece suporte ao uso exclusivamente a segurança de transporte. Essa associação oferece suporte do Windows Communication Foundation (WCF) para o protocolo WS-Federation. Serviços configurados com essa associação devem usar o transporte HTTP.  
  
 Associações consistem em uma pilha de elementos de associação. A pilha de elementos de associação  
  
 `wsFederationHttpBinding` é o mesmo que contidos em `wsHttpBinding`  
  
 Quando [ \<segurança >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) é definido como o valor padrão de <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>.  
  
 O `wsFederationHttpBinding` controla os detalhes das configurações de segurança de mensagem em [ \<mensagem >](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md). Observe que o [ \<segurança >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) elemento fornece obter acesso somente à medida que a segurança usada por meio da associação não pode ser alterada depois que a associação é criada.  
  
 O `wsFederationHttpBinding` também fornece um atributo privactyNoticeAt para definir e recuperar o URI no qual o aviso de privacidade está localizado.  
  
 Manter a política de segurança é especialmente importante em cenários de Federação. A recomendação é usar alguma forma de segurança, como HTTPS, para proteger a política contra usuários mal-intencionados.  
  
 Em cenários de Federação usando essa associação, possivelmente, a política de serviço tem informações importantes, como a chave usada para criptografar o token emitido (SAML), o tipo de declaração para colocar no token e assim por diante. Se essa política for violada, um invasor pode descobrir a chave do token emitido resultando em violação adicional, divulgação de informações e outros comportamentos mal-intencionados. Para evitar isso, a política deve ser obtida com segurança (por exemplo usando HTTPS) do serviço.  
  
 Para obter mais informações sobre essa associação, consulte [como: criar uma WSFederationHttpBinding](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).  
  
## <a name="example"></a>Exemplo  
  
```xml  
<configuration>  
<system.ServiceModel>  
<bindings>  
<wsFederationHttpBinding>  
    <binding   
        bypassProxyOnLocal="false"  
        transactionFlow="false"  
        hostNameComparisonMode="WeakWildcard"  
        maxReceivedMessageSize="1000"  
        messageEncoding="Mtom"   
        proxyAddress="http://foo/bar"   
        textEncoding="Utf16TextEncoding"  
        useDefaultWebProxy="false">  
        <reliableSession ordered="false"  
            inactivityTimeout="00:02:00" enabled="true" />  
        <security mode="None">  
           <message negotiateServiceCredential="false"  
                algorithmSuite="Aes128"  
                issuedTokenType="saml"   
                issuedKeyType="PublicKey">  
               <issuer address="http://localhost/Sts" />  
           </message>  
        </security>  
    </binding>  
</wsFederationBinding>  
</bindings>  
</system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.WSFederationHttpBinding>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement>  
 [Como criar um WSFederationHttpBinding](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Configurando associações fornecidas pelo sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Usando associações para configurar clientes e serviços do Windows Communication Foundation](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<associação >](../../../../../docs/framework/misc/binding.md)
