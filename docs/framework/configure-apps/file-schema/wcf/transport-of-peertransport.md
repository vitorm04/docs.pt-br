---
title: <transport> De <peerTransport>
ms.date: 03/30/2017
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
ms.openlocfilehash: 3dbeda5d418c30f378515fa83979eaca289370f9
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55284005"
---
# <a name="transport-of-peertransport"></a>\<transporte > de \<peerTransport >
Especifica o tipo de transporte para mensagens protegidas enviadas pelos pares configurados com essa associação.  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<binding>  
\<peerTransport>  
\<segurança >  
\<transporte >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<security>
  <transport credentialType="Certificate/Password" />
</security>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|credentialType|Opcional. Especifica o tipo de credenciais usado para verificar as mensagens enviadas com o transporte de par. Esse atributo é do tipo <xref:System.ServiceModel.PeerTransportCredentialType>.|  
  
## <a name="credentialtype-attribute"></a>credentialType atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Certificado|A autenticação do transporte de canal par requer um certificado X509.|  
|Senha|A autenticação do transporte de canal par requer uma senha correta.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|Define as configurações de segurança para um transporte de par.|  
  
## <a name="remarks"></a>Comentários  
 Esse elemento será definido somente se o atributo do modo de [ \<segurança >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md) é definido como `Transport` ou `TransportWithMessageCredential`.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Segurança de transporte](../../../../../docs/framework/wcf/feature-details/transport-security.md)
- [Transportes](../../../../../docs/framework/wcf/feature-details/transports.md)
- [Escolhendo um transporte](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [Associações](../../../../../docs/framework/wcf/bindings.md)
- [Estendendo associações](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Associações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
