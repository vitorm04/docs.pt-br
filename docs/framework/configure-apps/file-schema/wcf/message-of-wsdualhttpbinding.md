---
title: '&lt;mensagem&gt; de &lt;wsDualHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75101744-eed8-4d61-91f4-5fc4473a21f2
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c2d4eda0a1975da4518d077b6cfa779a8e764a66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltmessagegt-of-ltwsdualhttpbindinggt"></a>&lt;mensagem&gt; de &lt;wsDualHttpBinding&gt;
Define a segurança em nível de mensagem para o [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).  
  
 \<sistema. ServiceModel >  
\<associações >  
\<wsDualHttpBinding >  
\<associação >  
\<segurança >  
\<mensagem >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<message   
      clientCredentialType="None/Windows/UserName/Certificate/CardSpace"  
     negotiateServiceCredential="Boolean"  
   algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"/>  
</message>  
```  
  
## <a name="type"></a>Tipo  
 <xref:System.ServiceModel.MessageSecurityOverHttp>  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem os elementos pai de atributos e elementos filho  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|algorithmSuite|Opcional. Define a mensagem de algoritmos de criptografia e chave-wrap. Os algoritmos e os tamanhos de chave são determinados pelo <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> classe. Esses algoritmos são mapeados para aquelas especificadas na especificação de linguagem de política de segurança (WS-SecurityPolicy).<br /><br /> Consulte abaixo para os valores possíveis. O valor padrão é `Basic256`.|  
|clientCredentialType|Opcional. Especifica o tipo de credencial a ser usada ao executar autenticação de cliente usando o modo de segurança é `Message`. Consulte abaixo para os valores possíveis. O padrão é `Windows`.<br /><br /> Esse atributo é do tipo <xref:System.ServiceModel.MessageCredentialType>.|  
|negotiateServiceCredential|Opcional. Um valor booleano que especifica se a credencial de serviço é provisionada no cliente fora da banda ou é obtida do serviço ao cliente por meio de um processo de negociação. Tal uma negociação é um precursor para a troca de mensagens normal.<br /><br /> Se o `clientCredentialType` atributo é igual a nenhum nome de usuário ou certificado, a configuração deste atributo como `false` implica que o certificado de serviço está disponível no cliente fora da banda e que o cliente precisa especificar o certificado de serviço (usando o [ \<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) no [ \<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) comportamento de serviço. Este modo é interoperável com pilhas SOAP que implementa o WS-Trust e WS-SecureConversation.<br /><br /> Se o `ClientCredentialType` atributo é definido como `Windows`, configuração deste atributo como `false` Especifica a autenticação baseada em Kerberos. Isso significa que o cliente e o serviço devem fazer parte do mesmo domínio do Kerberos. Este modo é interoperável com pilhas SOAP que implementam o perfil de token do Kerberos (conforme definido na OASIS WSS TC), bem como WS-Trust e WS-SecureConversation. Quando esse atributo é `true`, faz com que uma negociação de SOAP .NET que túneis SPNego exchange nas mensagens SOAP.<br /><br /> O padrão é `true`.|  
  
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
|Nenhum|Isso permite que o serviço interaja com clientes anônimos. No lado do serviço, isso indica que o serviço não requer qualquer credencial de cliente. No cliente, isso indica que o cliente não fornece qualquer credencial de cliente.|  
|Windows|Permite que as trocas SOAP estar sob o contexto autenticado de uma credencial do Windows. Se o `negotiateServiceCredential` atributo é definido como `true`, isso ou realiza uma negociação SSPI ou Kerberos (um padrão de interoperabilidade).|  
|UserName|Permite que o serviço exigir que o cliente seja autenticado usando uma credencial de nome de usuário. [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]não oferece suporte a enviar um resumo de senha ou a derivação de chaves usando a senha e essas chaves para segurança de mensagem. Como tal, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] impõe que o transporte é protegido ao usar credenciais de nome de usuário. Este modo de credencial resulta em uma troca interoperável ou uma negociação não interoperável com base no `negotiateServiceCredential` atributo.|  
|certificado|Permite que o serviço exigir que o cliente seja autenticado usando um certificado. Se o modo de segurança de mensagem é usado e o `negotiateServiceCredential` atributo é definido como `false`, o cliente precisa ser provisionado com o certificado de serviço.|  
|IssuedToken|Especifica um token personalizado, geralmente é emitido por um serviço de Token de segurança.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<segurança >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsdualhttpbinding.md)|Define os recursos de segurança de [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.WSDualHttpSecurity.Message%2A>  
 <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>  
 <xref:System.ServiceModel.MessageSecurityOverHttp>  
 [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)  
 [Configurando associações fornecidas pelo sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Usando associações para configurar clientes e serviços do Windows Communication Foundation](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<associação >](../../../../../docs/framework/misc/binding.md)
