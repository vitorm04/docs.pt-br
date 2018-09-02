---
title: '&lt;peer&gt; de &lt;serviceCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: 94f93a7955af3bff1c17e59a11af3fad85c9134d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43399837"
---
# <a name="ltpeergt-of-ltservicecredentialsgt"></a><span data-ttu-id="bed6b-102">&lt;peer&gt; de &lt;serviceCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="bed6b-102">&lt;peer&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="bed6b-103">Especifica as credenciais atuais para um nó par.</span><span class="sxs-lookup"><span data-stu-id="bed6b-103">Specifies the current credentials for a peer node.</span></span>  
  
 <span data-ttu-id="bed6b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bed6b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="bed6b-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="bed6b-105">\<behaviors></span></span>  
<span data-ttu-id="bed6b-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="bed6b-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="bed6b-107">\<comportamento de ></span><span class="sxs-lookup"><span data-stu-id="bed6b-107">\<behavior></span></span>  
<span data-ttu-id="bed6b-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="bed6b-108">\<serviceCredentials></span></span>  
<span data-ttu-id="bed6b-109">\<par ></span><span class="sxs-lookup"><span data-stu-id="bed6b-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bed6b-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bed6b-110">Syntax</span></span>  
  
```xml  
<peer>  
  <certificate/>  
  <peerAuthentication/>  
  <messageSenderAuthentication/>  
</peer>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bed6b-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bed6b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="bed6b-112">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="bed6b-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bed6b-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="bed6b-113">Attributes</span></span>  
 <span data-ttu-id="bed6b-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="bed6b-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bed6b-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bed6b-115">Child Elements</span></span>  
  
|<span data-ttu-id="bed6b-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="bed6b-116">Element</span></span>|<span data-ttu-id="bed6b-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="bed6b-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bed6b-118">\<certificado ></span><span class="sxs-lookup"><span data-stu-id="bed6b-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-peer.md)|<span data-ttu-id="bed6b-119">Especifica um certificado X.509 a ser usado para assinar e criptografar mensagens para serviços ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="bed6b-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="bed6b-120">.</span><span class="sxs-lookup"><span data-stu-id="bed6b-120">.</span></span>|  
|[<span data-ttu-id="bed6b-121">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="bed6b-121">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication.md)|<span data-ttu-id="bed6b-122">Especifica opções de autenticação para remetentes de mensagens.</span><span class="sxs-lookup"><span data-stu-id="bed6b-122">Specifies authentication options for message senders.</span></span>|  
|[<span data-ttu-id="bed6b-123">\<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="bed6b-123">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication.md)|<span data-ttu-id="bed6b-124">Especifica opções de autenticação para serviços ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="bed6b-124">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bed6b-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="bed6b-125">Parent Elements</span></span>  
  
|<span data-ttu-id="bed6b-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="bed6b-126">Element</span></span>|<span data-ttu-id="bed6b-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="bed6b-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bed6b-128">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="bed6b-128">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="bed6b-129">Especifica a credencial a ser usado na autenticação do serviço e as configurações de relacionadas à validação de credenciais do cliente.</span><span class="sxs-lookup"><span data-stu-id="bed6b-129">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bed6b-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bed6b-130">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [<span data-ttu-id="bed6b-131">Rede ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="bed6b-131">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="bed6b-132">Autenticação de mensagem de canal par</span><span class="sxs-lookup"><span data-stu-id="bed6b-132">Peer Channel Message Authentication</span></span>](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="bed6b-133">Autenticação personalizada de canal par</span><span class="sxs-lookup"><span data-stu-id="bed6b-133">Peer Channel Custom Authentication</span></span>](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="bed6b-134">Protegendo aplicativos de canal par</span><span class="sxs-lookup"><span data-stu-id="bed6b-134">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [<span data-ttu-id="bed6b-135">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="bed6b-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
