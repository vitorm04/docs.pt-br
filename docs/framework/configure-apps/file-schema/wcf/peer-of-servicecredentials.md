---
title: <peer> de <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: 7f6669d3f53a6ee0d189786fa9ca3625fdedd127
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162472"
---
# <a name="peer-of-servicecredentials"></a><span data-ttu-id="ddd24-102">\<peer> de \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="ddd24-102">\<peer> of \<serviceCredentials></span></span>

<span data-ttu-id="ddd24-103">Especifica as credenciais atuais para um nó par.</span><span class="sxs-lookup"><span data-stu-id="ddd24-103">Specifies the current credentials for a peer node.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peer>**  
  
## <a name="syntax"></a><span data-ttu-id="ddd24-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="ddd24-104">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ddd24-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ddd24-105">Attributes and Elements</span></span>  

 <span data-ttu-id="ddd24-106">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="ddd24-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ddd24-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="ddd24-107">Attributes</span></span>  

 <span data-ttu-id="ddd24-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="ddd24-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ddd24-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ddd24-109">Child Elements</span></span>  
  
|<span data-ttu-id="ddd24-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="ddd24-110">Element</span></span>|<span data-ttu-id="ddd24-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="ddd24-111">Description</span></span>|  
|-------------|-----------------|  
|[\<certificate>](certificate-of-peer.md)|<span data-ttu-id="ddd24-112">Especifica um certificado X. 509 a ser usado para assinar e criptografar mensagens para serviços ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="ddd24-112">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="ddd24-113">.</span><span class="sxs-lookup"><span data-stu-id="ddd24-113">.</span></span>|  
|[\<messageSenderAuthentication>](messagesenderauthentication.md)|<span data-ttu-id="ddd24-114">Especifica opções de autenticação para remetentes de mensagens.</span><span class="sxs-lookup"><span data-stu-id="ddd24-114">Specifies authentication options for message senders.</span></span>|  
|[\<peerAuthentication>](peerauthentication.md)|<span data-ttu-id="ddd24-115">Especifica opções de autenticação para serviços de mesmo nível.</span><span class="sxs-lookup"><span data-stu-id="ddd24-115">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ddd24-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ddd24-116">Parent Elements</span></span>  
  
|<span data-ttu-id="ddd24-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="ddd24-117">Element</span></span>|<span data-ttu-id="ddd24-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="ddd24-118">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="ddd24-119">Especifica a credencial a ser usada na autenticação do serviço e as configurações relacionadas à validação da credencial do cliente.</span><span class="sxs-lookup"><span data-stu-id="ddd24-119">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ddd24-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="ddd24-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="ddd24-121">Rede peer-to-peer</span><span class="sxs-lookup"><span data-stu-id="ddd24-121">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="ddd24-122">[Autenticação de mensagem de canal par](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="ddd24-122">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="ddd24-123">[Autenticação personalizada do canal par](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="ddd24-123">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="ddd24-124">Protegendo aplicativos de canal par</span><span class="sxs-lookup"><span data-stu-id="ddd24-124">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="ddd24-125">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="ddd24-125">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
