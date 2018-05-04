---
title: '&lt;segurança&gt; de &lt;netTcpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: f58dd0ee1b00785e82628e5442c736866ffe7db5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltsecuritygt-of-ltnettcpbindinggt"></a>&lt;segurança&gt; de &lt;netTcpBinding&gt;
Define as configurações de segurança para uma associação.  
  
 \<system.ServiceModel>  
\<associações >  
\<netTcpBinding>  
\<associação >  
\<segurança >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">  
   <transport  
      clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
           protectionLevel="None/Sign/EncryptAndSign" />  
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
|modo|Opcional. Especifica o tipo de segurança que é aplicado. Os valores válidos são mostrados abaixo. O valor padrão é `Transport`.<br /><br /> Esse atributo é do tipo <xref:System.ServiceModel.SecurityMode>.|  
  
## <a name="mode-attribute"></a>Atributo mode  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Nenhum|A segurança é desabilitada.|  
|Transporte|Segurança de transporte é fornecida com o uso de TLS sobre TCP ou SPNego. O serviço precisará ser configurado com certificados SSL. É possível controlar o nível de proteção com esse modo.|  
|Mensagem|A segurança é fornecida usando a segurança de mensagem SOAP. Por padrão, o corpo SOAP é criptografado e assinado. Esse modo oferece uma variedade de recursos, como se as credenciais de serviço estão disponíveis no cliente fora da banda, o conjunto de algoritmos para usar e o nível de proteção para aplicar ao corpo da mensagem. Autenticação de cliente é executada uma vez por sessão e os resultados de autenticação são armazenados em cache para a duração da sessão.|  
|TransportWithMessageCredential|Segurança de transporte é associada a segurança de mensagem. Segurança de transporte é fornecida por TLS sobre TCP ou SPNego e garante a integridade, a confidencialidade e a autenticação do servidor. Segurança de mensagens SOAP fornece autenticação de cliente. Por padrão, autenticação de cliente é executada uma vez por sessão e os resultados de autenticação são armazenados em cache para a duração da sessão.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<transporte >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)|Define as configurações de segurança para o transporte. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.|  
|[\<message>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)|Define as configurações de segurança para a mensagem. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|associação|O elemento de associação do [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).|  
  
## <a name="remarks"></a>Comentários  
 Cada uma das associações padrão fornece parâmetros para controlar os requisitos de segurança de transferência. Normalmente, esses parâmetros incluem o modo de segurança especificado se a segurança de nível de mensagem ou nível de transporte é usada e a escolha do tipo de credencial de cliente. Com base na escolha das opções esses parâmetros presentes, uma pilha de canais é construído com a segurança apropriada.  
  
 As associações fornecidas pelo sistema fornecidas pelo Windows Communication Foundation (WCF) são um conjunto projetado para atender a alguns dos requisitos do cenário mais comuns. Cada uma dessas vinculações permite a especificação dos requisitos de segurança para alguns cenários de destino específicos.  
  
 Este elemento de configuração fornece as especificações de segurança para `netTcpBinding`. Isso é uma associação segura, confiável e otimizada adequada para comunicação entre computadores. Por padrão, ele gera uma pilha de comunicação em tempo de execução com suporte a TCP para entrega de mensagens e a segurança do Windows para segurança de mensagem e autenticação, WS-ReliableMessaging de confiabilidade e a codificação de mensagem binária.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.NetTcpSecurity>  
 <xref:System.ServiceModel.NetTcpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Configurando associações fornecidas pelo sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Usando associações para configurar clientes e serviços do Windows Communication Foundation](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<associação >](../../../../../docs/framework/misc/binding.md)
