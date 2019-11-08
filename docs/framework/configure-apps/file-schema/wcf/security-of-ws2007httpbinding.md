---
title: <security> de <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
ms.openlocfilehash: e88f55f3651d1ccd55631dce13a0349ac2772624
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736396"
---
# <a name="security-of-ws2007httpbinding"></a>\<> de segurança do \<ws2007HttpBinding >
Representa as configurações de segurança usadas com o elemento [\<ws2007HttpBinding >](ws2007httpbinding.md) .  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações**](bindings.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ws2007HttpBinding >** ](ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Binding** >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**security >**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.serviceModel>
  <bindings>
    <ws2007HttpBinding>
      <binding name = "String">
        <security mode="None/Message/Transport/TransportWithMessageCredential">
          <transport>
          </transport>
          <message>
          </message>
        </security>
      </binding>
    </ws2007HttpBinding>
  </bindings>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`mode`|Adicional. Especifica o tipo de segurança que é aplicado. O padrão é `Message`.<br /><br /> Este atributo é do tipo <xref:System.ServiceModel.SecurityMode>.|  
  
## <a name="mode-attribute"></a>Atributo de modo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`None`|A segurança é desabilitada.|  
|`Transport`|A proteção é fornecida usando HTTPS. O serviço deve ser configurado com certificados de protocolo SSL (SSL). A mensagem é totalmente protegida usando HTTPS e o serviço é autenticado pelo cliente usando o certificado SSL do serviço. A autenticação do cliente é controlada por meio do atributo `ClientCredentials` do elemento [> de transporte\<](transport-of-ws2007httpbinding.md) .|  
|`Message`|A segurança é fornecida usando a segurança de mensagem SOAP. Por padrão, o corpo SOAP é criptografado e assinado. Esse modo oferece uma variedade de recursos, como se as credenciais de serviço estão disponíveis no cliente fora da banda, o pacote de algoritmos a ser usado e qual nível de proteção aplicar ao corpo da mensagem por meio do <xref:System.ServiceModel.Security.SecurityMessageProperty>. A autenticação do cliente é executada uma vez para cada sessão e os resultados da autenticação são armazenados em cache durante a sessão.|  
|`TransportWithMessageCredential`|Nesse modo, o HTTPS fornece integridade, confidencialidade e autenticação de servidor, e a segurança de mensagem SOAP fornece autenticação de cliente. Por padrão, a autenticação do cliente é executada uma vez para cada sessão e os resultados da autenticação são armazenados em cache durante a sessão.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[> de transporte de \<](transport-of-ws2007httpbinding.md)|Define as configurações de segurança de transporte. Esse elemento corresponde ao tipo de <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>. Essas configurações são aplicadas somente quando o modo é definido como transporte.|  
|[\<message >](message-of-ws2007httpbinding.md)|Define as configurações de segurança para a mensagem. Esse elemento corresponde ao tipo de <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement>. Essas configurações não são aplicadas quando o modo é definido como transporte.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<ws2007HttpBinding >](ws2007httpbinding.md)|Uma associação segura para aplicativos de transporte HTTP.|  
  
## <a name="remarks"></a>Comentários  
 Esse elemento foi projetado para interoperação com serviços que implementam especificações WS-*. A segurança de transporte para essa associação é protocolo SSL (SSL) sobre HTTP ou HTTPS.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [Protegendo serviços e clientes](../../../wcf/feature-details/securing-services-and-clients.md)
- [Associações](../../../wcf/bindings.md)
- [Configurando associações fornecidas pelo sistema](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Usando associações para configurar serviços e clientes](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding >](bindings.md)
