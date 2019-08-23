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
# <a name="peer-of-clientcredentials-element"></a><span data-ttu-id="4a579-102">\<> de pares \<de ClientCredentials > elemento</span><span class="sxs-lookup"><span data-stu-id="4a579-102">\<peer> of \<clientCredentials> Element</span></span>
<span data-ttu-id="4a579-103">Especifica as credenciais usadas ao autenticar clientes ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="4a579-103">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="4a579-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4a579-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4a579-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="4a579-105">\<behaviors></span></span>  
<span data-ttu-id="4a579-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="4a579-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="4a579-107">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="4a579-107">\<behavior></span></span>  
<span data-ttu-id="4a579-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="4a579-108">\<clientCredentials></span></span>  
<span data-ttu-id="4a579-109">\<peer></span><span class="sxs-lookup"><span data-stu-id="4a579-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a579-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4a579-110">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4a579-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4a579-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4a579-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4a579-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4a579-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="4a579-113">Attributes</span></span>  
 <span data-ttu-id="4a579-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="4a579-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4a579-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4a579-115">Child Elements</span></span>  
  
|<span data-ttu-id="4a579-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="4a579-116">Element</span></span>|<span data-ttu-id="4a579-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="4a579-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4a579-118">\<certificate></span><span class="sxs-lookup"><span data-stu-id="4a579-118">\<certificate></span></span>](certificate-element.md)|<span data-ttu-id="4a579-119">Especifica um certificado X. 509 a ser usado para assinar e criptografar mensagens para clientes ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="4a579-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="4a579-120">.</span><span class="sxs-lookup"><span data-stu-id="4a579-120">.</span></span>|  
|[<span data-ttu-id="4a579-121">\<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="4a579-121">\<peerAuthentication></span></span>](peerauthentication-element.md)|<span data-ttu-id="4a579-122">Especifica opções de autenticação para clientes pares.</span><span class="sxs-lookup"><span data-stu-id="4a579-122">Specifies authentication options for peer clients.</span></span>|  
|[<span data-ttu-id="4a579-123">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="4a579-123">\<messageSenderAuthentication></span></span>](messagesenderauthentication-element.md)|<span data-ttu-id="4a579-124">Especifica opções de autenticação para remetentes de mensagens.</span><span class="sxs-lookup"><span data-stu-id="4a579-124">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4a579-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4a579-125">Parent Elements</span></span>  
  
|<span data-ttu-id="4a579-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="4a579-126">Element</span></span>|<span data-ttu-id="4a579-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="4a579-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4a579-128">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="4a579-128">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="4a579-129">Especifica as credenciais usadas para autenticar um cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="4a579-129">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a579-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="4a579-130">Remarks</span></span>  
 <span data-ttu-id="4a579-131">Esse elemento de configuração especifica as credenciais que um nó par usa para se autenticar em outros nós na malha, bem como configurações de autenticação que um nó par usa para autenticar outros nós de mesmo nível.</span><span class="sxs-lookup"><span data-stu-id="4a579-131">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="4a579-132">Para obter mais informações, consulte [autenticação de mensagens de canal de emparelhamento](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) e [protegendo os aplicativos de canal de mesmo nível](../../../wcf/feature-details/securing-peer-channel-applications.md).</span><span class="sxs-lookup"><span data-stu-id="4a579-132">For more information, see [Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) and [Securing Peer Channel Applications](../../../wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a579-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4a579-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="4a579-134">Rede ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="4a579-134">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="4a579-135">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="4a579-135">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- <span data-ttu-id="4a579-136">[Autenticação de mensagem de canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="4a579-136">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="4a579-137">[Autenticação personalizada do canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="4a579-137">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="4a579-138">Protegendo aplicativos de canal par</span><span class="sxs-lookup"><span data-stu-id="4a579-138">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="4a579-139">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="4a579-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
