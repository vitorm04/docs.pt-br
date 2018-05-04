---
title: elemento de &lt;mensagem&gt; de &lt;ws2007FederationHttpBinding&gt;
ms.date: 03/30/2017
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
ms.openlocfilehash: 565a0c6027e94954c81c11f96fbd5473dbcd4fdf
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltmessagegt-element-of-ltws2007federationhttpbindinggt"></a>elemento de &lt;mensagem&gt; de &lt;ws2007FederationHttpBinding&gt;
Define as configurações para a segurança de nível de mensagem para o [ \<ws2007FederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) elemento.  
  
 \<system.ServiceModel>  
\<associações >  
\<ws2007FederationHttpBinding>  
\<associação >  
\<segurança >  
\<message>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<ws2007FederationBinding>  
   <binding >  
      <security>  
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
                     x509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
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
                     X509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
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
   </binding>  
</ws2007FederationBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`algorithmSuite`|Opcional. Define a criptografia de mensagens, assinatura e algoritmos de chave-wrap. Os algoritmos e os tamanhos de chave são determinados pelo <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> classe. Esses algoritmos são mapeados para aquelas especificadas na especificação de linguagem de política de segurança (WS-SecurityPolicy).<br /><br /> Consulte a tabela a seguir para os valores possíveis. O valor padrão é Basic256.|  
|`issuedKeyType`|Especifica o tipo de chave a ser emitida. Os valores válidos incluem o seguinte:<br /><br /> -SymmetricKey<br />-PublicKey<br />-BearerKey<br /><br /> O padrão é SymmetricKey. Esse atributo é do tipo <xref:System.IdentityModel.Tokens.SecurityKeyType>.|  
|`issuedTokenType`|Um URI que especifica o tipo de token a ser emitido. O padrão é `null`.|  
|`negotiateServiceCredential`|Um valor que especifica se a credencial de serviço deve ser trocada como parte da negociação ou está disponível fora da banda. O padrão é `true`, que significa que a credencial de serviço é negociada.|  
  
## <a name="algorithmsuite-attribute"></a>algorithmSuite atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Basic128|Use criptografia Aes128, Sha1 para resumo da mensagem e Rsa-oaep-mgf1p para codificação de chave.|  
|Basic192|Use a criptografia Aes192, Sha1 para resumo da mensagem, Rsa-oaep mgf1p para codificação de chave.|  
|Basic256|Use a criptografia Aes256, Sha1 para resumo da mensagem, Rsa-oaep mgf1p para codificação de chave.|  
|Basic256Rsa15|Use Aes256 para criptografia de mensagem, Sha1 para resumo da mensagem e Rsa15 para codificação de chave.|  
|Basic192Rsa15|Use Aes192 para criptografia de mensagem, Sha1 para resumo da mensagem e Rsa15 para codificação de chave.|  
|TripleDes|Use a criptografia TripleDes, Sha1 para resumo da mensagem, Rsa-oaep mgf1p para codificação de chave.|  
|Basic128Rsa15|Use Aes128 para criptografia de mensagem, Sha1 para resumo da mensagem e Rsa15 para codificação de chave.|  
|TripleDesRsa15|Use a criptografia TripleDes, Sha1 para resumo da mensagem e Rsa15 para codificação de chave.|  
|Basic128Sha256|Use Aes256 para criptografia de mensagem, Sha256 para resumo da mensagem e Rsa-oaep mgf1p para codificação de chave.|  
|Basic192Sha256|Use Aes192 para criptografia de mensagem, Sha256 para resumo da mensagem e Rsa-oaep mgf1p para codificação de chave.|  
|Basic256Sha256|Use Aes256 para criptografia de mensagem, Sha256 para resumo da mensagem e Rsa-oaep mgf1p para codificação de chave.|  
|TripleDesSha256|Use TripleDes para criptografia de mensagem, Sha256 para resumo da mensagem e Rsa-oaep mgf1p para codificação de chave.|  
|Basic128Sha256Rsa15|Use Aes128 para criptografia de mensagem, Sha256 para resumo da mensagem e Rsa15 para codificação de chave.|  
|Basic192Sha256Rsa15|Use Aes192 para criptografia de mensagem, Sha256 para resumo da mensagem e Rsa15 para codificação de chave.|  
|Basic256Sha256Rsa15|Use Aes256 para criptografia de mensagem, Sha256 para resumo da mensagem e Rsa15 para codificação de chave.|  
|TripleDesSha256Rsa15|Use TripleDes para criptografia de mensagem, Sha256 para resumo da mensagem e Rsa15 para codificação de chave.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|Especifica uma coleção de tipos de declaração para essa associação. Cada elemento é do tipo <xref:System.ServiceModel.Configuration.ClaimTypeElement>.|  
|[\<issuer>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md)|Especifica um ponto de extremidade que emite um token de segurança. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.|  
|[\<issuerMetadata>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md)|Especifica o endereço do ponto de extremidade do emissor.|  
|[\<tokenRequestParameters>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|Uma coleção de parâmetros de solicitação de token. Cada parâmetro é um elemento XML.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)|Define as configurações de segurança para uma associação.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>  
 `System.ServiceModel.Configuration.FederatedMessageSecurityElement` [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Configurando associações fornecidas pelo sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Usando associações para configurar clientes e serviços do Windows Communication Foundation](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<associação >](../../../../../docs/framework/misc/binding.md)
