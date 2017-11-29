---
title: '&lt;peer&gt; de &lt;serviceCredentials&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a3af8c07e86b7ccdf5443a666626b523914a2c45
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltpeergt-of-ltservicecredentialsgt"></a>&lt;peer&gt; de &lt;serviceCredentials&gt;
Especifica as credenciais atuais de um nó ponto a ponto.  
  
 \<sistema. ServiceModel >  
\<comportamentos >  
\<serviceBehaviors >  
\<comportamento >  
\<serviceCredentials >  
\<par >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<peer>  
  <certificate/>  
  <peerAuthentication/>  
  <messageSenderAuthentication/>  
</peer>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem os elementos pai de atributos e elementos filho  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<certificado >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-peer.md)|Especifica um certificado x. 509 a ser usado para assinar e criptografar mensagens para serviços ponto a ponto. .|  
|[\<messageSenderAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication.md)|Especifica opções de autenticação para remetentes de mensagens.|  
|[\<peerAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication.md)|Especifica opções de autenticação para serviços ponto a ponto.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Especifica a credencial a ser usado na autenticação do serviço e as configurações de relacionadas à validação de credenciais do cliente.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [Rede ponto a ponto](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [Autenticação de mensagens de canal par](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [Autenticação personalizada de canal par](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [Protegendo aplicativos de canal par](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
