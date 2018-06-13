---
title: elemento de &lt;mensagem&gt; de &lt;netTcpBinding&gt;
ms.date: 03/30/2017
ms.assetid: 1d71edd9-c085-4c2e-b6d3-980c313366f9
ms.openlocfilehash: 4a487d695cab259fc6b82fdf44b4c1bfdf5d04e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33364120"
---
# <a name="ltmessagegt-element-of-ltnettcpbindinggt"></a>elemento de &lt;mensagem&gt; de &lt;netTcpBinding&gt;
Define o tipo de requisitos de segurança de nível de mensagem para um ponto de extremidade configurado com o [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).  
  
 \<system.ServiceModel>  
\<associações >  
\<netTcpBinding>  
\<associação >  
\<segurança >  
\<message>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<message   
      algorithmSuite=System.Servicemodel.Security.SecurityAlgorithmsuite  
    clientCredentialType="None/Windows/UserName/Certificate/IssuedToken"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`algorithmSuite`|Define a mensagem de algoritmos de criptografia e chave-wrap. Os algoritmos e os tamanhos de chave são determinados pelo <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> classe. Esses algoritmos são mapeados para aquelas especificadas na especificação de linguagem de política de segurança (WS-SecurityPolicy).<br /><br /> Os valores possíveis são mostrados na tabela a seguir. O valor padrão é `Basic256`.<br /><br /> Se a associação de serviço Especifica uma `algorithmSuite` valor não é igual ao padrão e você gerar o arquivo de configuração usando Svcutil.exe, em seguida, ele não é gerado e você deve editar manualmente o arquivo de configuração para definir esse atributo para o valor desejado.|  
|`clientCredentialType`|Especifica o tipo de credencial a ser usada ao executar a autenticação de cliente usando a segurança baseada em mensagem. Os valores possíveis são mostrados na tabela a seguir. O valor padrão é `UserName`. Esse atributo é do tipo <xref:System.ServiceModel.MessageCredentialType>.|  
  
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
|Nenhum|Isso permite que o serviço interaja com clientes anônimos. O serviço, isso indica que o serviço não requer qualquer credencial de cliente. No cliente, isso indica que o cliente não fornece qualquer credencial de cliente.|  
|Windows|Permite que as trocas SOAP estar sob o contexto autenticado de uma credencial do Windows.|  
|UserName|Permite que o serviço exigir que o cliente seja autenticado usando uma credencial de nome de usuário. WCF não oferece suporte para enviar um resumo de senha ou a derivação de chaves usando a senha e essas chaves para segurança de mensagem. Como tal, o WCF impõe que o transporte é protegido ao usar credenciais de nome de usuário. Este modo de credencial resulta em uma troca interoperável ou uma negociação não interoperável com base no `negotiateServiceCredential` atributo.|  
|certificado|Permite que o serviço exigir que o cliente seja autenticado usando um certificado. Se o modo de segurança de mensagem é usado e o `negotiateServiceCredential` atributo é definido como `false`, o cliente deve ser provisionado com o certificado de serviço.|  
|IssuedToken|Especifica um token personalizado, em geral, emitido por um Token de segurança Service (STS).|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|Define os recursos de segurança para o <xref:System.ServiceModel.Configuration.NetTcpBindingElement>.|  
  
## <a name="remarks"></a>Comentários  
 Mensagem usa a segurança em nível de mensagem para a integridade e confidencialidade da mensagem SOAP e para a autenticação mútua de pares de comunicação. Se este modo de segurança é selecionado em uma associação, a pilha de canais é configurada com elementos de associação de segurança de mensagem e as mensagens SOAP são protegidas em conformidade com o WS-Security * padrões.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.MessageSecurityOverTcp>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.NetTcpSecurity.Message%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Configurando associações fornecidas pelo sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Usando associações para configurar clientes e serviços do Windows Communication Foundation](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<associação >](../../../../../docs/framework/misc/binding.md)
