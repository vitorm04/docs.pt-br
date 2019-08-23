---
title: <transport> de <netPeerTcpBinding>
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: 837d01540fa63579877ab4085bd8034c78f2fbe0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915571"
---
# <a name="transport-of-netpeertcpbinding"></a>\<> de transporte \<do NetPeerTcpBinding >
Especifica as configurações de segurança de nível de transporte ao usar o [ \<> NetPeerTcpBinding](netpeertcpbinding.md).  
  
 \<system.ServiceModel>  
\<bindings>  
\<netPeerTcpBinding>  
\<> de associação  
\<> de segurança  
\<> de transporte  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<netPeerTcpBinding>
  <binding>
    <security>
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerTcpBinding>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|CredentialType|Opcional. Especifica o tipo de credenciais usadas para verificar as mensagens enviadas com o transporte de mesmo nível. Esse atributo é do tipo <xref:System.ServiceModel.PeerTransportCredentialType>.|  
  
## <a name="credentialtype-attribute"></a>Atributo CredentialType  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Certificate|A autenticação do transporte de canal par requer um certificado X509.|  
|Senha|A autenticação do transporte de canal par requer uma senha correta.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<security>](security-of-netpeerbinding.md)|Define as configurações de segurança para o [ \<> NetPeerTcpBinding](netpeertcpbinding.md).|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- [Protegendo serviços e clientes](../../../wcf/feature-details/securing-services-and-clients.md)
- [Associações](../../../wcf/bindings.md)
- [Configurando associações fornecidas pelo sistema](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Usando associações para configurar serviços e clientes](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../misc/binding.md)
