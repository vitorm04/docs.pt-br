---
title: <peer> de <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: d726ab460141b1e373a1cabf770b8958f50319eb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783390"
---
# <a name="peer-of-servicecredentials"></a>\<Peer > de \<serviceCredentials >
Especifica as credenciais atuais para um nó par.  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<serviceBehaviors>  
\<behavior>  
\<serviceCredentials>  
\<peer>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<certificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-peer.md)|Especifica um certificado X.509 a ser usado para assinar e criptografar mensagens para serviços ponto a ponto. .|  
|[\<messageSenderAuthentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication.md)|Especifica opções de autenticação para remetentes de mensagens.|  
|[\<peerAuthentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication.md)|Especifica opções de autenticação para serviços ponto a ponto.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<serviceCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Especifica a credencial a ser usado na autenticação do serviço e as configurações de relacionadas à validação de credenciais do cliente.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [Rede ponto a ponto](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- [Autenticação de mensagem de canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [Autenticação personalizada de canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [Protegendo aplicativos de canal par](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
- [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
