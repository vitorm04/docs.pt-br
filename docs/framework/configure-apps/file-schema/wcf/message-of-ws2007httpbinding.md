---
title: <message> de <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 9ffd8db6-84a8-4b38-a9fe-2cb1a87a1c97
ms.openlocfilehash: bf0ed2de73505d5634d6c7d26881f9800a0bf1f2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59166732"
---
# <a name="message-of-ws2007httpbinding"></a>\<mensagem > de \<ws2007HttpBinding >
Define as configurações de segurança em nível de mensagem do [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) elemento.  
  
 \<system.ServiceModel>  
\<bindings>  
\<ws2007HttpBinding>  
\<binding>  
\<segurança >  
\<message>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<ws2007HttpBinding>
  <binding>
    <security>
      <message clientCredentialType="None/Windows/UserName/Certificate/IssuedToken"
               establishSecurityContext="Boolean"
               negotiateServiceCredential="Boolean"
               algorithmSuite="Enumeration. See algorithmSuite Attribute below."
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
|`algorithmSuite`|Define a mensagem de algoritmos de criptografia e encapsulamento de chave. Os algoritmos e os tamanhos de chave são determinados pelo <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> classe. Esses algoritmos são mapeados para aqueles especificados na especificação da linguagem de política de segurança (WS-SecurityPolicy).<br /><br /> O valor padrão é Basic256.|  
|`clientCredentialType`|Opcional. Especifica o tipo de credencial a ser usada ao executar a autenticação de cliente usando o modo de segurança `Message` ou `TransportWithMessageCredentials`. Consulte os valores de enumeração na tabela a seguir. O padrão é Windows.<br /><br /> Esse atributo é do tipo <xref:System.ServiceModel.MessageCredentialType>.|  
|`establishSecurityContext`|Um valor que determina se o canal de segurança estabelece uma sessão segura. Uma sessão segura estabelece um token de contexto de segurança (SCT) antes da troca de mensagens do aplicativo. Quando o SCT é estabelecido, o canal de segurança oferece uma <xref:System.ServiceModel.Channels.ISession> interface para os canais superiores. Para obter mais informações sobre como usar sessões seguras, consulte [como: Criar uma sessão segura](../../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md).<br /><br /> O valor padrão é `true`.|  
|`negotiateServiceCredential`|Opcional. Um valor que especifica se a credencial de serviço é provisionada no cliente fora de banda ou obtida do serviço ao cliente por meio de um processo de negociação. Dessa negociação é um precursor para a troca de mensagens comum.<br /><br /> Se o `clientCredentialType` atributo é igual a nenhum nome de usuário ou certificado, definir esse atributo como `false` implica que o certificado de serviço está disponível no cliente fora da banda e que o cliente deve especificar o certificado de serviço (usando o [ \<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) na [ \<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) comportamento de serviço. Esse modo é interoperável com pilhas SOAP que implementam o WS-Trust e WS-SecureConversation.<br /><br /> Se o `ClientCredentialType` atributo é definido como `Windows`, definir esse atributo como `false` Especifica a autenticação baseada em Kerberos. Isso significa que o cliente e o serviço devem ser parte do mesmo domínio do Kerberos. Esse modo é interoperável com pilhas SOAP que implementam o perfil de token do Kerberos (conforme definido na OASIS WSS TC), bem como o WS-Trust e WS-SecureConversation.<br /><br /> Quando esse atributo está `true`, faz com que uma negociação de SOAP .NET túneis <xref:System.ServiceModel.Security.Tokens.ServiceModelSecurityTokenTypes.Spnego%2A> exchange sobre mensagens SOAP.<br /><br /> O padrão é `true`.|  
  
## <a name="algorithmsuite-attribute"></a>algorithmSuite atributo  
  
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
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType de atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`None`|Isso permite que o serviço interaja com clientes anônimos. No serviço, isso indica que o serviço não requer qualquer credencial de cliente. No cliente, isso indica que o cliente não fornece qualquer credencial de cliente.|  
|`Certificate`|Permite que o serviço exigir que o cliente seja autenticado usando um certificado. Se `message` modo de segurança é usado e o `negotiateServiceCredential` atributo é definido como `false`, o cliente deve ser provisionado com o certificado de serviço.|  
|`IssuedToken`|Especifica um token personalizado, geralmente emitido por um Security Token Service (STS).|  
|`UserName`|Permite que o serviço exigir que o cliente seja autenticado usando um `UserName` credencial. O WCF não oferece suporte a enviar um resumo de senha ou derivação de chaves usando a senha e essas chaves para segurança de mensagem. Como tal, o WCF impõe que o transporte é protegido ao usar `UserName` credenciais. Esse modo de credencial resulta em uma troca interoperável ou uma negociação não é interoperável com base no `negotiateServiceCredential` atributo.|  
|`Windows`|Permite que as trocas SOAP estar sob o contexto autenticado de uma `Windows` credencial. Se o `negotiateServiceCredential` atributo é definido como `true`, isso é executado tanto uma negociação SSPI ou Kerberos (um padrão de interoperabilidade).|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-ws2007httpbinding.md)|Define as configurações de segurança para um [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md).|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.NonDualMessageSecurityOverHttpElement>
- [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Associações](../../../../../docs/framework/wcf/bindings.md)
- [Configurando associações fornecidas pelo sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Usando associações para configurar serviços e clientes](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../../../docs/framework/misc/binding.md)
