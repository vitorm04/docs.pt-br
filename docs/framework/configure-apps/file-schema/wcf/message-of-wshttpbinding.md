---
title: <message> de <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 621abbde-590b-454d-90ac-68dc3c69c720
ms.openlocfilehash: 8cb8879d866eca3b1dafbd139de39373874dad14
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397803"
---
# <a name="message-of-wshttpbinding"></a>\<> de mensagens \<de WSHttpBinding >
Define as configurações de segurança em nível de mensagem do [ \<> de WSHttpBinding](wshttpbinding.md).  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsHttpBinding >** ](wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de segurança**](security-of-wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de mensagem**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
         clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
         establishSecurityContext="Boolean"
         negotiateServiceCredential="Boolean" />
```  
  
## <a name="type"></a>Tipo  
 <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|algorithmSuite|Define a criptografia de mensagem e os algoritmos de encapsulamento de chaves. Os algoritmos e os tamanhos de chave são determinados <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> pela classe. Esses algoritmos são mapeados para aqueles especificados na especificação do WS-SecurityPolicy (Security Policy Language).<br /><br /> O valor padrão é `Basic256`.|  
|clientCredentialType|Opcional. Especifica o tipo de credencial a ser usado ao executar a autenticação do cliente usando o `Message` modo `TransportWithMessageCredentials`de segurança é ou. Consulte os valores de enumeração abaixo. O padrão é `Windows`.<br /><br /> Esse atributo é do tipo <xref:System.ServiceModel.MessageCredentialType>.|  
|establishSecurityContext|Um valor booliano que determina se o canal de segurança estabelece uma sessão segura. Uma sessão segura estabelece um identificador de contexto de segurança (SCT) antes de trocar as mensagens do aplicativo. Quando o SCT é estabelecido, o canal de segurança oferece <xref:System.ServiceModel.Channels.ISession> uma interface para os canais superiores. Para obter mais informações sobre como usar sessões seguras [, consulte Como: Crie uma sessão](../../../wcf/feature-details/how-to-create-a-secure-session.md)segura.<br /><br /> O valor padrão é `true`.|  
|negotiateServiceCredential|Opcional. Um valor booliano que especifica se a credencial de serviço é provisionada no cliente fora da banda ou é obtida do serviço para o cliente por meio de um processo de negociação. Essa negociação é um precurso para a troca de mensagens usual.<br /><br /> Se o `clientCredentialType` atributo for igual a None, username ou Certificate, definir esse atributo como `false` implica que o certificado de serviço está disponível no cliente fora de banda e que o cliente precisa especificar o certificado de serviço (usando o > do ServiceId) no comportamento do [ \<serviço ServiceCredentials >](servicecredentials.md) . [ \<](servicecertificate-of-servicecredentials.md) Esse modo é interoperável com pilhas SOAP que implementam WS-Trust e WS-SecureConversation.<br /><br /> Se o `ClientCredentialType` atributo for definido como `Windows`, definir esse atributo para `false` especifica a autenticação baseada em Kerberos. Isso significa que o cliente e o serviço devem fazer parte do mesmo domínio Kerberos. Esse modo é interoperável com pilhas SOAP que implementam o perfil de token Kerberos (conforme definido no OASIS WSS TC), bem como WS-Trust e WS-SecureConversation.<br /><br /> Quando esse atributo é `true`, ele faz uma negociação SOAP .NET que túneis SPNEGO trocas por mensagens SOAP.<br /><br /> O padrão é `true`.|  
  
## <a name="algorithmsuite-attribute"></a>Atributo algorithmSuite  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Basic128|Use criptografia Basic128, SHA1 para síntese de mensagem e rsa-oaep-mgf1p para encapsulamento de chave.|  
|Basic192|Use a criptografia Basic192, SHA1 para Message Digest, rsa-oaep-mgf1p para quebra automática de chave.|  
|Basic256|Use a criptografia Basic256, SHA1 para Message Digest, rsa-oaep-mgf1p para quebra automática de chave.|  
|Basic256Rsa15|Use Basic256 para criptografia de mensagem, SHA1 para Message Digest e Rsa15 para Key Wrap.|  
|Basic192Rsa15|Use Basic192 para criptografia de mensagem, SHA1 para Message Digest e Rsa15 para Key Wrap.|  
|TripleDes|Use a criptografia TripleDes, SHA1 para Message Digest, rsa-oaep-mgf1p para quebra automática de chave.|  
|Basic128Rsa15|Use Basic128 para criptografia de mensagem, SHA1 para Message Digest e Rsa15 para Key Wrap.|  
|TripleDesRsa15|Use a criptografia TripleDes, SHA1 para síntese de mensagem e Rsa15 para o encapsulamento de chave.|  
|Basic128Sha256|Use Basic256 para criptografia de mensagem, SHA256 para síntese de mensagem e rsa-oaep-mgf1p para encapsulamento de chave.|  
|Basic192Sha256|Use Basic192 para criptografia de mensagem, SHA256 para síntese de mensagem e rsa-oaep-mgf1p para encapsulamento de chave.|  
|Basic256Sha256|Use Basic256 para criptografia de mensagem, SHA256 para síntese de mensagem e rsa-oaep-mgf1p para encapsulamento de chave.|  
|TripleDesSha256|Use TripleDes para criptografia de mensagem, SHA256 para síntese de mensagem e rsa-oaep-mgf1p para encapsulamento de chave.|  
|Basic128Sha256Rsa15|Use Basic128 para criptografia de mensagem, SHA256 para síntese de mensagem e Rsa15 para quebra de chave.|  
|Basic192Sha256Rsa15|Use Basic192 para criptografia de mensagem, SHA256 para síntese de mensagem e Rsa15 para quebra de chave.|  
|Basic256Sha256Rsa15|Use Basic256 para criptografia de mensagem, SHA256 para síntese de mensagem e Rsa15 para quebra de chave.|  
|TripleDesSha256Rsa15|Use TripleDes para criptografia de mensagem, SHA256 para síntese de mensagem e Rsa15 para quebra de chave.|  
  
## <a name="clientcredentialtype-attribute"></a>Atributo clientCredentialtype  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Nenhum|Isso permite que o serviço interaja com clientes anônimos. No lado do serviço, isso indica que o serviço não requer nenhuma credencial do cliente. No cliente, isso indica que o cliente não fornece nenhuma credencial de cliente.|  
|Certificate|Permite que o serviço exija que o cliente seja autenticado usando um certificado. Se o modo de segurança da mensagem for `negotiateServiceCredential` usado e o atributo `false`for definido como, o cliente precisará ser provisionado com o certificado de serviço.|  
|IssuedToken|Especifica um token personalizado, geralmente emitido por um serviço de token de segurança.|  
|UserName|Permite que o serviço exija que o cliente seja autenticado usando uma credencial de nome de usuário. O WCF não dá suporte ao envio de um resumo de senha ou à derivação de chaves usando a senha e usando essas chaves para segurança de mensagem. Dessa forma, o WCF impõe que o transporte seja protegido ao usar credenciais de nome de usuário. Esse modo de credencial resulta em um intercâmbio interoperável ou em uma negociação não interoperável `negotiateServiceCredential` com base no atributo.|  
|Windows|Permite que as trocas SOAP estejam sob o contexto autenticado de uma credencial do Windows. Se o `negotiateServiceCredential` atributo for definido como `true`, isso executará uma negociação SSPI ou o Kerberos (um padrão interoperável).|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<security>](security-of-wshttpbinding.md)|Define as configurações de segurança para um [ \<> de WSHttpBinding](wshttpbinding.md).|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.NonDualMessageSecurityOverHttpElement>
- [Protegendo serviços e clientes](../../../wcf/feature-details/securing-services-and-clients.md)
- [Associações](../../../wcf/bindings.md)
- [Configurando associações fornecidas pelo sistema](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Usando associações para configurar serviços e clientes](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../misc/binding.md)
