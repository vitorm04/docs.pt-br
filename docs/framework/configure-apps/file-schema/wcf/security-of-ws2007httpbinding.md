---
title: '&lt;segurança&gt; de &lt;ws2007HttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: b7644e0cf9148cb489618b352ad09901799ceaa6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltsecuritygt-of-ltws2007httpbindinggt"></a>&lt;segurança&gt; de &lt;ws2007HttpBinding&gt;
Representa as configurações de segurança usadas com o [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) elemento.  
  
 \<system.serviceModel>  
\<associações >  
\<ws2007HttpBinding>  
\<associação >  
\<segurança >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.serviceModel>  
    <bindings>  
        <ws2007HttpBinding>  
            <binding name = "string">  
              <security mode="None/Message/Transport/TransportWithMessageCredential">  
                  <transport>  
                  </transport>  
                  <message>  
                  </message>  
              </security  
        </ws2007HttpBinding>  
    </bindings>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`mode`|-Opcional. Especifica o tipo de segurança que é aplicado. O padrão é `Message`.<br /><br /> Esse atributo é do tipo <xref:System.ServiceModel.SecurityMode>.|  
  
## <a name="mode-attribute"></a>Atributo mode  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`None`|A segurança é desabilitada.|  
|`Transport`|A proteção é fornecida usando HTTPS. O serviço deve ser configurado com certificados Secure Sockets Layer (SSL). A mensagem é totalmente protegida usando HTTPS e o serviço é autenticado pelo cliente usando o certificado SSL do serviço. A autenticação do cliente é controlada por meio de `ClientCredentials` atributo do [ \<transporte >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md) elemento.|  
|`Message`|A segurança é fornecida usando a segurança de mensagem SOAP. Por padrão, o corpo SOAP é criptografado e assinado. Esse modo oferece uma variedade de recursos, como se as credenciais de serviço estão disponíveis no cliente fora da banda, o conjunto de algoritmos para usar e o nível de proteção para aplicar ao corpo da mensagem por meio de <xref:System.ServiceModel.Security.SecurityMessageProperty>. Autenticação de cliente é executada uma vez para cada sessão e os resultados de autenticação são armazenados em cache para a duração da sessão.|  
|`TransportWithMessageCredential`|Nesse modo, HTTPS fornece autenticação de servidor, integridade e confidencialidade e segurança de mensagens SOAP fornece autenticação de cliente. Por padrão, autenticação de cliente é executada uma vez para cada sessão e os resultados de autenticação são armazenados em cache para a duração da sessão.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<transporte >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md)|Define as configurações de segurança de transporte. Esse elemento corresponde ao <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> tipo. Essas configurações são aplicadas somente quando o modo é definido como transporte.|  
|[\<message>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-ws2007httpbinding.md)|Define as configurações de segurança para a mensagem. Esse elemento corresponde ao <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> tipo. Essas configurações não são aplicadas quando o modo é definido como transporte.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<ws2007HttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)|Uma associação de segurança para aplicativos de transporte HTTP.|  
  
## <a name="remarks"></a>Comentários  
 Esse elemento se destina a interoperação com os serviços que implementam o WS-* especificações. A segurança de transporte para essa associação é o protocolo (SSL) via HTTP ou HTTPS.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.WSHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Configurando associações fornecidas pelo sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Usando associações para configurar clientes e serviços do Windows Communication Foundation](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<associação >](../../../../../docs/framework/misc/binding.md)
