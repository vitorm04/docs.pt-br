---
title: <security> elemento de <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
ms.openlocfilehash: 15740144b0aad7eb2798db4712e4769d08d893a6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186856"
---
# <a name="security-element-of-ws2007federationhttpbinding"></a>\<segurança > elemento \<ws2007FederationHttpBinding >
Define as configurações de segurança de [ \<ws2007FederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) elemento.  
  
 \<system.ServiceModel>  
\<bindings>  
\<ws2007FederationHttpBinding>  
\<binding>  
\<segurança >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<ws2007FederationBinding>
  <binding>
    <security mode="None/Message/TransportWithMessageCredential">
      <message negotiateServiceCredential="Boolean"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/  Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               defaultProtectionLevel="none/sign/EncryptAndSign"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey">
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
|`mode`|Opcional. Especifica o tipo de segurança que é aplicado. O valor padrão é `Message`. Esse atributo é do tipo <xref:System.ServiceModel.WSFederationHttpSecurityMode>.|  
  
## <a name="mode-attribute"></a>modo de atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Nenhum|A mensagem SOAP não é segura durante a transferência.|  
|Mensagem|São fornecidos os serviços de integridade, confidencialidade, autenticação de servidor e autenticação de cliente usando a segurança de mensagem SOAP. Por padrão, o corpo é criptografado e assinado. O serviço deve ser configurado com um certificado. A autenticação de cliente baseia-se no token emitido ao cliente por um serviço de token de segurança.|  
|TransportWithMessageCredential|A integridade, a confidencialidade e a autenticação de servidor são fornecidas por HTTPS. O serviço deve ser configurado com um certificado. A autenticação de cliente é fornecida por meio de segurança de mensagens SOAP e é baseada no token emitido ao cliente por um serviço de token de segurança.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<message>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-ws2007httpbinding.md)|Define as configurações para a segurança de nível de mensagem. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<binding>](../../../../../docs/framework/misc/binding.md)|Define todos os recursos de associação do [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [Como: Criar um WSFederationHttpBinding](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Selecionando um tipo de credencial](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [Associações](../../../../../docs/framework/wcf/bindings.md)
- [Configurando associações fornecidas pelo sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Usando associações para configurar serviços e clientes](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../../../docs/framework/misc/binding.md)
