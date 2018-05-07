---
title: '&lt;mensagem&gt; de &lt;ws2007HttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 9ffd8db6-84a8-4b38-a9fe-2cb1a87a1c97
ms.openlocfilehash: 39d5ce66537fd6c94895205ccc855d7fb631284e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="ltmessagegt-of-ltws2007httpbindinggt"></a>&lt;mensagem&gt; de &lt;ws2007HttpBinding&gt;
Define as configurações de segurança em nível de mensagem do [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) elemento.  
  
 \<system.ServiceModel>  
\<associações >  
\<ws2007HttpBinding>  
\<associação >  
\<segurança >  
\<message>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<ws2007HttpBinding>  
 <binding >  
  <security>  
   <message clientCredentialType =  
    "None/Windows/UserName/Certificate/IssuedToken"  
    establishSecurityContext="Boolean"  
    negotiateServiceCredential="Boolean"  
    algorithmSuite= Enumeration. See algorithmSuite Attribute below.  
    defaultProtectionLevel="None/Sign/EncryptionAndSign" />  
  </security>  
 </binding>  
</ws2007HttpBinding>  
```  
  
## <a name="type"></a>Tipo  
 <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`algorithmSuite`|Define a mensagem de algoritmos de criptografia e chave-wrap. Os algoritmos e os tamanhos de chave são determinados pelo <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> classe. Esses algoritmos são mapeados para aquelas especificadas na especificação de linguagem de política de segurança (WS-SecurityPolicy).<br /><br /> O valor padrão é Basic256.|  
|`clientCredentialType`|Opcional. Especifica o tipo de credencial a ser usada ao executar a autenticação de cliente usando o modo de segurança `Message` ou `TransportWithMessageCredentials`. Consulte os valores de enumeração na tabela a seguir. O padrão é Windows.<br /><br /> Esse atributo é do tipo <xref:System.ServiceModel.MessageCredentialType>.|  
|`establishSecurityContext`|Um valor que determina se o canal de segurança estabelece uma sessão segura. Uma sessão segura estabelece um token de contexto de segurança (SCT) antes de troca de mensagens do aplicativo. Quando o SCT é estabelecida, o canal de segurança oferece um <xref:System.ServiceModel.Channels.ISession> interface para os canais superiores. Para obter mais informações sobre como usar sessões seguras, consulte [como: criar uma sessão segura](../../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md).<br /><br /> O valor padrão é `true`.|  
|`negotiateServiceCredential`|Opcional. Um valor que especifica se a credencial de serviço é provisionada no cliente fora da banda ou é obtida do serviço ao cliente por meio de um processo de negociação. Tal uma negociação é um precursor para a troca de mensagens normal.<br /><br /> Se o `clientCredentialType` atributo é igual a nenhum nome de usuário ou certificado, a configuração deste atributo como `false` implica que o certificado de serviço está disponível no cliente fora da banda e que o cliente deverá especificar o certificado de serviço (usando o [ \<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) no [ \<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) comportamento de serviço. Este modo é interoperável com pilhas SOAP que implementa o WS-Trust e WS-SecureConversation.<br /><br /> Se o `ClientCredentialType` atributo é definido como `Windows`, configuração deste atributo como `false` Especifica a autenticação baseada em Kerberos. Isso significa que o cliente e o serviço devem fazer parte do mesmo domínio do Kerberos. Este modo é interoperável com pilhas SOAP que implementam o perfil de token do Kerberos (conforme definido na OASIS WSS TC), bem como WS-Trust e WS-SecureConversation.<br /><br /> Quando esse atributo é `true`, ele faz com que uma negociação de SOAP .NET túneis <xref:System.ServiceModel.Security.Tokens.ServiceModelSecurityTokenTypes.Spnego%2A> exchange nas mensagens SOAP.<br /><br /> O padrão é `true`.|  
  
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
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`None`|Isso permite que o serviço interaja com clientes anônimos. O serviço, isso indica que o serviço não requer qualquer credencial de cliente. No cliente, isso indica que o cliente não fornece qualquer credencial de cliente.|  
|`Certificate`|Permite que o serviço exigir que o cliente seja autenticado usando um certificado. Se `message` modo de segurança é usado e o `negotiateServiceCredential` atributo é definido como `false`, o cliente deve ser provisionado com o certificado de serviço.|  
|`IssuedToken`|Especifica um token personalizado, em geral, emitido por um Token de segurança Service (STS).|  
|`UserName`|Permite que o serviço exigir que o cliente seja autenticado usando um `UserName` credencial. WCF não oferece suporte para enviar um resumo de senha ou a derivação de chaves usando a senha e essas chaves para segurança de mensagem. Como tal, o WCF impõe que o transporte é protegido ao usar `UserName` credenciais. Este modo de credencial resulta em uma troca interoperável ou uma negociação não interoperável com base no `negotiateServiceCredential` atributo.|  
|`Windows`|Permite que as trocas SOAP estar sob o contexto autenticado de uma `Windows` credencial. Se o `negotiateServiceCredential` atributo é definido como `true`, isso ou realiza uma negociação SSPI ou Kerberos (um padrão de interoperabilidade).|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-ws2007httpbinding.md)|Define as configurações de segurança para um [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md).|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.WSHttpSecurity.Message%2A>  
 <xref:System.ServiceModel.Configuration.NonDualMessageSecurityOverHttpElement>  
 [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Configurando associações fornecidas pelo sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Usando associações para configurar clientes e serviços do Windows Communication Foundation](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<associação >](../../../../../docs/framework/misc/binding.md)
