---
title: <peer>do <clientCredentials> elemento
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: 2f1cb5689125e2483a74dcac515beb07abbb7c70
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934041"
---
# <a name="peer-of-clientcredentials-element"></a>\<> de pares \<de ClientCredentials > elemento
Especifica as credenciais usadas ao autenticar clientes ponto a ponto.  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<endpointBehaviors>  
\<> de comportamento  
\<clientCredentials>  
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
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<certificate>](certificate-element.md)|Especifica um certificado X. 509 a ser usado para assinar e criptografar mensagens para clientes ponto a ponto. .|  
|[\<peerAuthentication>](peerauthentication-element.md)|Especifica opções de autenticação para clientes pares.|  
|[\<messageSenderAuthentication>](messagesenderauthentication-element.md)|Especifica opções de autenticação para remetentes de mensagens.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|Especifica as credenciais usadas para autenticar um cliente para um serviço.|  
  
## <a name="remarks"></a>Comentários  
 Esse elemento de configuração especifica as credenciais que um nó par usa para se autenticar em outros nós na malha, bem como configurações de autenticação que um nó par usa para autenticar outros nós de mesmo nível. Para obter mais informações, consulte [autenticação de mensagens de canal de emparelhamento](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) e [protegendo os aplicativos de canal de mesmo nível](../../../wcf/feature-details/securing-peer-channel-applications.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [Rede ponto a ponto](../../../wcf/feature-details/peer-to-peer-networking.md)
- [Protegendo clientes](../../../wcf/securing-clients.md)
- [Autenticação de mensagem de canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [Autenticação personalizada do canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [Protegendo aplicativos de canal par](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [Protegendo serviços e clientes](../../../wcf/feature-details/securing-services-and-clients.md)
