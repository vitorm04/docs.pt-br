---
title: <security> de <peerTransport>
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: 270ca844f586be256b6483653c868d1cc4396657
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399777"
---
# <a name="security-of-peertransport"></a>\<> de segurança \<do peerTransport >
Contém as definições de segurança associadas a um canal de pares, incluindo o tipo de autenticação utilizada e a segurança usada para o transporte de mensagens.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de CustomBinding**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> peerTransport**](peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de segurança**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">
  <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`mode`|Especifica o tipo de segurança a ser aplicado. O valor padrão é Message. Esse atributo é do tipo <xref:System.ServiceModel.SecurityMode>.|  
  
## <a name="mode-attribute"></a>Atributo de modo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`None`|A segurança é desabilitada.|  
|`Transport`|A proteção é fornecida usando HTTPS.|  
|`Message`|A segurança SOAP fornece autenticação, integridade e confidencialidade.|  
|`TransportWithMessageCredential`|O HTTPS fornece autenticação e confidencialidade. As mensagens SOAP fornecem tipos de credenciais avançados.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<> de transporte](transport-of-peertransport.md)|Define um transporte de mesmo nível para uma associação personalizada. Esse elemento tem um `clientCredentialType` atributo que especifica as credenciais a serem usadas ao interagir com um serviço. Esse atributo é do tipo <xref:System.ServiceModel.PeerTransportCredentialType>.<br /><br /> Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<peerTransport>](peertransport.md)|Define um transporte de mesmo nível para uma associação personalizada.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Segurança de transporte](../../../wcf/feature-details/transport-security.md)
- [Transportes](../../../wcf/feature-details/transports.md)
- [Escolhendo um transporte](../../../wcf/feature-details/choosing-a-transport.md)
- [Associações](../../../wcf/bindings.md)
- [Estendendo associações](../../../wcf/extending/extending-bindings.md)
- [Associações personalizadas](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
