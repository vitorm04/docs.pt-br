---
title: '&lt;par&gt; do elemento &lt;clientCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: 9d64f682f67dcc7c4f0c0f1600938f8ff9ac0dd6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltpeergt-of-ltclientcredentialsgt-element"></a><span data-ttu-id="d9254-102">&lt;par&gt; do elemento &lt;clientCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="d9254-102">&lt;peer&gt; of &lt;clientCredentials&gt; Element</span></span>
<span data-ttu-id="d9254-103">Especifica as credenciais usadas ao autenticar clientes ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="d9254-103">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="d9254-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d9254-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d9254-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="d9254-105">\<behaviors></span></span>  
<span data-ttu-id="d9254-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="d9254-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="d9254-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="d9254-107">\<behavior></span></span>  
<span data-ttu-id="d9254-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="d9254-108">\<clientCredentials></span></span>  
<span data-ttu-id="d9254-109">\<par ></span><span class="sxs-lookup"><span data-stu-id="d9254-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9254-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d9254-110">Syntax</span></span>  
  
```xml  
<peer>  
  <certificate/>  
  <peerAuthentication/>  
  <messageSenderAuthentication/>  
</peer>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d9254-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d9254-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d9254-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d9254-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d9254-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="d9254-113">Attributes</span></span>  
 <span data-ttu-id="d9254-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="d9254-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d9254-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d9254-115">Child Elements</span></span>  
  
|<span data-ttu-id="d9254-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="d9254-116">Element</span></span>|<span data-ttu-id="d9254-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="d9254-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9254-118">\<certificado ></span><span class="sxs-lookup"><span data-stu-id="d9254-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md)|<span data-ttu-id="d9254-119">Especifica um certificado x. 509 a ser usado para assinar e criptografar mensagens para clientes ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="d9254-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="d9254-120">.</span><span class="sxs-lookup"><span data-stu-id="d9254-120">.</span></span>|  
|[<span data-ttu-id="d9254-121">\<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="d9254-121">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)|<span data-ttu-id="d9254-122">Especifica as opções de autenticação para clientes ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="d9254-122">Specifies authentication options for peer clients.</span></span>|  
|[<span data-ttu-id="d9254-123">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="d9254-123">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)|<span data-ttu-id="d9254-124">Especifica opções de autenticação para remetentes de mensagens.</span><span class="sxs-lookup"><span data-stu-id="d9254-124">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d9254-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d9254-125">Parent Elements</span></span>  
  
|<span data-ttu-id="d9254-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="d9254-126">Element</span></span>|<span data-ttu-id="d9254-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="d9254-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9254-128">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="d9254-128">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="d9254-129">Especifica as credenciais usadas para autenticar um cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="d9254-129">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9254-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="d9254-130">Remarks</span></span>  
 <span data-ttu-id="d9254-131">Este elemento de configuração especifica credenciais que um nó par usa para se autenticar em outros nós da malha, bem como configurações de autenticação que um nó par usa para autenticar outros nós de mesmo nível.</span><span class="sxs-lookup"><span data-stu-id="d9254-131">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="d9254-132">Para obter mais informações, consulte [autenticação de mensagem de canal par](http://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95) e [proteger aplicativos de canal par](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).</span><span class="sxs-lookup"><span data-stu-id="d9254-132">For more information, see [Peer Channel Message Authentication](http://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95) and [Securing Peer Channel Applications](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9254-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d9254-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [<span data-ttu-id="d9254-134">Rede ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="d9254-134">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="d9254-135">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="d9254-135">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="d9254-136">Autenticação de mensagens de canal par</span><span class="sxs-lookup"><span data-stu-id="d9254-136">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="d9254-137">Autenticação personalizada de canal par</span><span class="sxs-lookup"><span data-stu-id="d9254-137">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="d9254-138">Protegendo aplicativos de canal par</span><span class="sxs-lookup"><span data-stu-id="d9254-138">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [<span data-ttu-id="d9254-139">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="d9254-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
