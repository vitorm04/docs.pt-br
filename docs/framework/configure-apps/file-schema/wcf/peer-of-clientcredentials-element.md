---
title: '&lt;par&gt; do elemento &lt;clientCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: f933e4c6719437d530e0cf90e3aa1da3a8143060
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616206"
---
# <a name="ltpeergt-of-ltclientcredentialsgt-element"></a><span data-ttu-id="024dc-102">&lt;par&gt; do elemento &lt;clientCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="024dc-102">&lt;peer&gt; of &lt;clientCredentials&gt; Element</span></span>
<span data-ttu-id="024dc-103">Especifica as credenciais usadas ao autenticar clientes ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="024dc-103">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="024dc-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="024dc-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="024dc-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="024dc-105">\<behaviors></span></span>  
<span data-ttu-id="024dc-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="024dc-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="024dc-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="024dc-107">\<behavior></span></span>  
<span data-ttu-id="024dc-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="024dc-108">\<clientCredentials></span></span>  
<span data-ttu-id="024dc-109">\<peer></span><span class="sxs-lookup"><span data-stu-id="024dc-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="024dc-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="024dc-110">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="024dc-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="024dc-111">Attributes and Elements</span></span>  
 <span data-ttu-id="024dc-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="024dc-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="024dc-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="024dc-113">Attributes</span></span>  
 <span data-ttu-id="024dc-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="024dc-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="024dc-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="024dc-115">Child Elements</span></span>  
  
|<span data-ttu-id="024dc-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="024dc-116">Element</span></span>|<span data-ttu-id="024dc-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="024dc-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="024dc-118">\<certificate></span><span class="sxs-lookup"><span data-stu-id="024dc-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md)|<span data-ttu-id="024dc-119">Especifica um certificado X.509 a ser usado para assinar e criptografar mensagens para clientes ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="024dc-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="024dc-120">.</span><span class="sxs-lookup"><span data-stu-id="024dc-120">.</span></span>|  
|[<span data-ttu-id="024dc-121">\<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="024dc-121">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)|<span data-ttu-id="024dc-122">Especifica as opções de autenticação para clientes ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="024dc-122">Specifies authentication options for peer clients.</span></span>|  
|[<span data-ttu-id="024dc-123">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="024dc-123">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)|<span data-ttu-id="024dc-124">Especifica opções de autenticação para remetentes de mensagens.</span><span class="sxs-lookup"><span data-stu-id="024dc-124">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="024dc-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="024dc-125">Parent Elements</span></span>  
  
|<span data-ttu-id="024dc-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="024dc-126">Element</span></span>|<span data-ttu-id="024dc-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="024dc-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="024dc-128">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="024dc-128">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="024dc-129">Especifica as credenciais usadas para autenticar um cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="024dc-129">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="024dc-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="024dc-130">Remarks</span></span>  
 <span data-ttu-id="024dc-131">Este elemento de configuração especifica as credenciais que um nó par usa para se autenticar em outros nós na malha, bem como configurações de autenticação que um nó par usa para autenticar outros nós pares.</span><span class="sxs-lookup"><span data-stu-id="024dc-131">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="024dc-132">Para obter mais informações, consulte [autenticação de mensagem de canal par](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95) e [Protegendo aplicativos de canal par](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).</span><span class="sxs-lookup"><span data-stu-id="024dc-132">For more information, see [Peer Channel Message Authentication](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95) and [Securing Peer Channel Applications](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="024dc-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="024dc-133">See also</span></span>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="024dc-134">Rede ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="024dc-134">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="024dc-135">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="024dc-135">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="024dc-136">Autenticação de mensagem de canal par</span><span class="sxs-lookup"><span data-stu-id="024dc-136">Peer Channel Message Authentication</span></span>](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)
- [<span data-ttu-id="024dc-137">Autenticação personalizada de canal par</span><span class="sxs-lookup"><span data-stu-id="024dc-137">Peer Channel Custom Authentication</span></span>](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)
- [<span data-ttu-id="024dc-138">Protegendo aplicativos de canal par</span><span class="sxs-lookup"><span data-stu-id="024dc-138">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="024dc-139">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="024dc-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
