---
title: <peer> de <clientCredentials> elemento
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: 7074ee992755557d7e5503035c89bdbefd678792
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107231"
---
# <a name="peer-of-clientcredentials-element"></a><span data-ttu-id="f59ca-102">\<Peer > de \<clientCredentials > elemento</span><span class="sxs-lookup"><span data-stu-id="f59ca-102">\<peer> of \<clientCredentials> Element</span></span>
<span data-ttu-id="f59ca-103">Especifica as credenciais usadas ao autenticar clientes ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="f59ca-103">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="f59ca-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f59ca-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f59ca-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="f59ca-105">\<behaviors></span></span>  
<span data-ttu-id="f59ca-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="f59ca-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="f59ca-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="f59ca-107">\<behavior></span></span>  
<span data-ttu-id="f59ca-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="f59ca-108">\<clientCredentials></span></span>  
<span data-ttu-id="f59ca-109">\<peer></span><span class="sxs-lookup"><span data-stu-id="f59ca-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f59ca-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f59ca-110">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f59ca-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f59ca-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f59ca-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f59ca-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f59ca-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="f59ca-113">Attributes</span></span>  
 <span data-ttu-id="f59ca-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="f59ca-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f59ca-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f59ca-115">Child Elements</span></span>  
  
|<span data-ttu-id="f59ca-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="f59ca-116">Element</span></span>|<span data-ttu-id="f59ca-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="f59ca-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f59ca-118">\<certificate></span><span class="sxs-lookup"><span data-stu-id="f59ca-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md)|<span data-ttu-id="f59ca-119">Especifica um certificado X.509 a ser usado para assinar e criptografar mensagens para clientes ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="f59ca-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="f59ca-120">.</span><span class="sxs-lookup"><span data-stu-id="f59ca-120">.</span></span>|  
|[<span data-ttu-id="f59ca-121">\<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="f59ca-121">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)|<span data-ttu-id="f59ca-122">Especifica as opções de autenticação para clientes ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="f59ca-122">Specifies authentication options for peer clients.</span></span>|  
|[<span data-ttu-id="f59ca-123">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="f59ca-123">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)|<span data-ttu-id="f59ca-124">Especifica opções de autenticação para remetentes de mensagens.</span><span class="sxs-lookup"><span data-stu-id="f59ca-124">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f59ca-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f59ca-125">Parent Elements</span></span>  
  
|<span data-ttu-id="f59ca-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="f59ca-126">Element</span></span>|<span data-ttu-id="f59ca-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="f59ca-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f59ca-128">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="f59ca-128">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="f59ca-129">Especifica as credenciais usadas para autenticar um cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="f59ca-129">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f59ca-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="f59ca-130">Remarks</span></span>  
 <span data-ttu-id="f59ca-131">Este elemento de configuração especifica as credenciais que um nó par usa para se autenticar em outros nós na malha, bem como configurações de autenticação que um nó par usa para autenticar outros nós pares.</span><span class="sxs-lookup"><span data-stu-id="f59ca-131">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="f59ca-132">Para obter mais informações, consulte [autenticação de mensagem de canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) e [Protegendo aplicativos de canal par](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).</span><span class="sxs-lookup"><span data-stu-id="f59ca-132">For more information, see [Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) and [Securing Peer Channel Applications](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f59ca-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f59ca-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="f59ca-134">Rede peer-to-peer</span><span class="sxs-lookup"><span data-stu-id="f59ca-134">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="f59ca-135">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="f59ca-135">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="f59ca-136">Autenticação de mensagem de canal par</span><span class="sxs-lookup"><span data-stu-id="f59ca-136">Peer Channel Message Authentication</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [<span data-ttu-id="f59ca-137">Autenticação personalizada de canal par</span><span class="sxs-lookup"><span data-stu-id="f59ca-137">Peer Channel Custom Authentication</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [<span data-ttu-id="f59ca-138">Protegendo aplicativos de canal par</span><span class="sxs-lookup"><span data-stu-id="f59ca-138">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="f59ca-139">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="f59ca-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
