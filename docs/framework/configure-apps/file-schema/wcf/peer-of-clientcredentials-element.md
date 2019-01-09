---
title: '&lt;par&gt; do elemento &lt;clientCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: 9846a25a8df165f51290aa8a26f907d40b6b159f
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150559"
---
# <a name="ltpeergt-of-ltclientcredentialsgt-element"></a><span data-ttu-id="4868e-102">&lt;par&gt; do elemento &lt;clientCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="4868e-102">&lt;peer&gt; of &lt;clientCredentials&gt; Element</span></span>
<span data-ttu-id="4868e-103">Especifica as credenciais usadas ao autenticar clientes ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="4868e-103">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="4868e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4868e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4868e-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="4868e-105">\<behaviors></span></span>  
<span data-ttu-id="4868e-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="4868e-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="4868e-107">\<comportamento de ></span><span class="sxs-lookup"><span data-stu-id="4868e-107">\<behavior></span></span>  
<span data-ttu-id="4868e-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="4868e-108">\<clientCredentials></span></span>  
<span data-ttu-id="4868e-109">\<par ></span><span class="sxs-lookup"><span data-stu-id="4868e-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4868e-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4868e-110">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4868e-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4868e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4868e-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4868e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4868e-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="4868e-113">Attributes</span></span>  
 <span data-ttu-id="4868e-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="4868e-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4868e-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4868e-115">Child Elements</span></span>  
  
|<span data-ttu-id="4868e-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="4868e-116">Element</span></span>|<span data-ttu-id="4868e-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="4868e-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4868e-118">\<certificado ></span><span class="sxs-lookup"><span data-stu-id="4868e-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md)|<span data-ttu-id="4868e-119">Especifica um certificado X.509 a ser usado para assinar e criptografar mensagens para clientes ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="4868e-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="4868e-120">.</span><span class="sxs-lookup"><span data-stu-id="4868e-120">.</span></span>|  
|[<span data-ttu-id="4868e-121">\<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="4868e-121">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)|<span data-ttu-id="4868e-122">Especifica as opções de autenticação para clientes ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="4868e-122">Specifies authentication options for peer clients.</span></span>|  
|[<span data-ttu-id="4868e-123">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="4868e-123">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)|<span data-ttu-id="4868e-124">Especifica opções de autenticação para remetentes de mensagens.</span><span class="sxs-lookup"><span data-stu-id="4868e-124">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4868e-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4868e-125">Parent Elements</span></span>  
  
|<span data-ttu-id="4868e-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="4868e-126">Element</span></span>|<span data-ttu-id="4868e-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="4868e-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4868e-128">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="4868e-128">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="4868e-129">Especifica as credenciais usadas para autenticar um cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="4868e-129">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4868e-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="4868e-130">Remarks</span></span>  
 <span data-ttu-id="4868e-131">Este elemento de configuração especifica as credenciais que um nó par usa para se autenticar em outros nós na malha, bem como configurações de autenticação que um nó par usa para autenticar outros nós pares.</span><span class="sxs-lookup"><span data-stu-id="4868e-131">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="4868e-132">Para obter mais informações, consulte [autenticação de mensagem de canal par](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95) e [Protegendo aplicativos de canal par](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).</span><span class="sxs-lookup"><span data-stu-id="4868e-132">For more information, see [Peer Channel Message Authentication](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95) and [Securing Peer Channel Applications](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4868e-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4868e-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [<span data-ttu-id="4868e-134">Rede ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="4868e-134">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="4868e-135">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="4868e-135">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="4868e-136">Autenticação de mensagem de canal par</span><span class="sxs-lookup"><span data-stu-id="4868e-136">Peer Channel Message Authentication</span></span>](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="4868e-137">Autenticação personalizada de canal par</span><span class="sxs-lookup"><span data-stu-id="4868e-137">Peer Channel Custom Authentication</span></span>](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="4868e-138">Protegendo aplicativos de canal par</span><span class="sxs-lookup"><span data-stu-id="4868e-138">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [<span data-ttu-id="4868e-139">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="4868e-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
