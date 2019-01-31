---
title: <message> De <wsDualHttpBinding>
ms.date: 03/30/2017
ms.assetid: 75101744-eed8-4d61-91f4-5fc4473a21f2
ms.openlocfilehash: c827ba17e1ee889fd72294014a71008f8f118386
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278598"
---
# <a name="message-of-wsdualhttpbinding"></a>\<mensagem > de \<wsDualHttpBinding >
Define a segurança de nível de mensagem para o [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).  
  
 \<system.ServiceModel>  
\<bindings>  
\<wsDualHttpBinding>  
\<binding>  
\<segurança >  
\<message>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
         negotiateServiceCredential="Boolean"
         algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />
</message>
```  
  
## <a name="type"></a>Tipo  
 <xref:System.ServiceModel.MessageSecurityOverHttp>  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|algorithmSuite|Opcional. Define a mensagem de algoritmos de criptografia e encapsulamento de chave. Os algoritmos e os tamanhos de chave são determinados pelo <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> classe. Esses algoritmos são mapeados para aqueles especificados na especificação da linguagem de política de segurança (WS-SecurityPolicy).<br /><br /> Veja abaixo os valores possíveis. O valor padrão é `Basic256`.|  
|clientCredentialType|Opcional. Especifica o tipo de credencial a ser usada ao executar autenticação de cliente usando o modo de segurança é `Message`. Veja abaixo os valores possíveis. O padrão é `Windows`.<br /><br /> Esse atributo é do tipo <xref:System.ServiceModel.MessageCredentialType>.|  
|negotiateServiceCredential|Opcional. Um valor booliano que especifica se a credencial de serviço é provisionada no cliente fora de banda ou obtida do serviço ao cliente por meio de um processo de negociação. Dessa negociação é um precursor para a troca de mensagens comum.<br /><br /> Se o `clientCredentialType` atributo é igual a nenhum nome de usuário ou certificado, definir esse atributo como `false` implica que o certificado de serviço está disponível no cliente fora da banda e que o cliente precisa especificar o certificado de serviço (usando o [ \<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) na [ \<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) comportamento de serviço. Esse modo é interoperável com pilhas SOAP que implementam o WS-Trust e WS-SecureConversation.<br /><br /> Se o `ClientCredentialType` atributo é definido como `Windows`, definir esse atributo como `false` Especifica a autenticação baseada em Kerberos. Isso significa que o cliente e o serviço devem ser parte do mesmo domínio do Kerberos. Esse modo é interoperável com pilhas SOAP que implementam o perfil de token do Kerberos (conforme definido na OASIS WSS TC), bem como o WS-Trust e WS-SecureConversation. Quando esse atributo é `true`, faz com que uma negociação SOAP do .NET que túneis SPNego exchange sobre mensagens SOAP.<br /><br /> O padrão é `true`.|  
  
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
|Nenhum|Isso permite que o serviço interaja com clientes anônimos. No lado do serviço, isso indica que o serviço não requer qualquer credencial de cliente. No cliente, isso indica que o cliente não fornece qualquer credencial de cliente.|  
|Windows|Permite que as trocas SOAP estar sob o contexto autenticado de uma credencial do Windows. Se o `negotiateServiceCredential` atributo é definido como `true`, isso é executado tanto uma negociação SSPI ou Kerberos (um padrão de interoperabilidade).|  
|UserName|Permite que o serviço exigir que o cliente seja autenticado usando uma credencial de nome de usuário. O WCF não oferece suporte a enviar um resumo de senha ou derivação de chaves usando a senha e essas chaves para segurança de mensagem. Como tal, o WCF impõe que o transporte é protegido ao usar as credenciais de nome de usuário. Esse modo de credencial resulta em uma troca interoperável ou uma negociação não é interoperável com base no `negotiateServiceCredential` atributo.|  
|Certificado|Permite que o serviço exigir que o cliente seja autenticado usando um certificado. Se o modo de segurança de mensagem é usado e o `negotiateServiceCredential` atributo é definido como `false`, o cliente precisa ser provisionado com o certificado de serviço.|  
|IssuedToken|Especifica um token personalizado, geralmente é emitido por um serviço de Token de segurança.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsdualhttpbinding.md)|Define os recursos de segurança de [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).|  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSDualHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>
- <xref:System.ServiceModel.MessageSecurityOverHttp>
- [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Associações](../../../../../docs/framework/wcf/bindings.md)
- [Configurando associações fornecidas pelo sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Usando associações para configurar serviços e clientes](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../../../docs/framework/misc/binding.md)
