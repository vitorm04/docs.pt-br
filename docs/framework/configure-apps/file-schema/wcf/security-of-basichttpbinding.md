---
title: '&lt;segurança&gt; de &lt;basicHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: ddf120d5462c7fcb0774e29fa18e80b71727acd8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltsecuritygt-of-ltbasichttpbindinggt"></a>&lt;segurança&gt; de &lt;basicHttpBinding&gt;
Define os recursos de segurança de [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).  
  
 \<system.ServiceModel>  
\<associações >  
\<basicHttpBinding>  
\<associação >  
\<segurança >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">  
   <transport  
      clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
      proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
      realm="string" />  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem os elementos pai de atributos e elementos filho  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|modo|Opcional. Especifica o tipo de segurança que é usado. O padrão é `None`. Esse atributo é do tipo <xref:System.ServiceModel.BasicHttpSecurityMode>.|  
  
## <a name="mode-attribute"></a>Atributo mode  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Nenhum|-Mensagens não são protegidas durante a transferência.|  
|Transporte|A segurança é fornecida usando o transporte HTTPS. As mensagens SOAP são protegidas usando HTTPS. O serviço é autenticado para o cliente usando o certificado de x. 509 do serviço. O cliente é autenticado usando ClientCredentialType fornecido. Consulte o [ \<transporte >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md).|  
|Mensagem|A segurança é fornecida usando a segurança de mensagem SOAP. Por padrão, o corpo é criptografado e assinado. Para essa associação, o sistema requer que o certificado do servidor para o cliente fora da banda. Válido somente `ClientCredentialType` para essa associação é `Certificate`.|  
|TransportWithMessageCredential|Autenticação de integridade, confidencialidade e servidor são fornecidos pela segurança de transporte. A autenticação de cliente é fornecida por meio de segurança da mensagem SOAP. Esse modo é relevante quando o usuário estiver autenticando usando o nome de usuário/senha e há uma implantação existente de HTTP para transferência segura de mensagens.|  
|TransportCredentialOnly|Esse modo não fornece confidencialidade e integridade de mensagens. Ele fornece autenticação de cliente com base em http. Esse modo deve ser usado com cuidado. Ele deve ser usado em ambientes onde a segurança de transporte está sendo fornecida por outros meios (como IPSec) e somente a autenticação do cliente é fornecida pelo [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] infraestrutura.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<transporte >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md)|Define as configurações de segurança de transporte para um serviço básico de HTTP. Esse elemento corresponde a <xref:System.ServiceModel.HttpTransportSecurity>.|  
|[\<message>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md)|Define as configurações de segurança de mensagem para um serviço básico de HTTP. Esse elemento corresponde a <xref:System.ServiceModel.BasicHttpMessageSecurity>.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|associação|O elemento de associação do [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).|  
  
## <a name="remarks"></a>Comentários  
 Por padrão, a mensagem SOAP não é protegida e o cliente não está autenticado. Esse elemento permite que você defina configurações de segurança adicionais para o `basicHttpBinding` elemento.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.BasicHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Selecionando um tipo de credencial](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Configurando associações fornecidas pelo sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Usando associações para configurar clientes e serviços do Windows Communication Foundation](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<associação >](../../../../../docs/framework/misc/binding.md)
