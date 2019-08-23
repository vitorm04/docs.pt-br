---
title: <peer> de <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: 50415cb9b35d2a2053efa3313a415de518b7e36e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933782"
---
# <a name="peer-of-servicecredentials"></a><span data-ttu-id="82624-102">\<> de pontos \<de ServiceCredentials ></span><span class="sxs-lookup"><span data-stu-id="82624-102">\<peer> of \<serviceCredentials></span></span>
<span data-ttu-id="82624-103">Especifica as credenciais atuais para um nó par.</span><span class="sxs-lookup"><span data-stu-id="82624-103">Specifies the current credentials for a peer node.</span></span>  
  
 <span data-ttu-id="82624-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="82624-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="82624-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="82624-105">\<behaviors></span></span>  
<span data-ttu-id="82624-106">\<> de portais</span><span class="sxs-lookup"><span data-stu-id="82624-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="82624-107">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="82624-107">\<behavior></span></span>  
<span data-ttu-id="82624-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="82624-108">\<serviceCredentials></span></span>  
<span data-ttu-id="82624-109">\<peer></span><span class="sxs-lookup"><span data-stu-id="82624-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82624-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="82624-110">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="82624-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="82624-111">Attributes and Elements</span></span>  
 <span data-ttu-id="82624-112">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="82624-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="82624-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="82624-113">Attributes</span></span>  
 <span data-ttu-id="82624-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="82624-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="82624-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="82624-115">Child Elements</span></span>  
  
|<span data-ttu-id="82624-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="82624-116">Element</span></span>|<span data-ttu-id="82624-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="82624-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="82624-118">\<certificate></span><span class="sxs-lookup"><span data-stu-id="82624-118">\<certificate></span></span>](certificate-of-peer.md)|<span data-ttu-id="82624-119">Especifica um certificado X. 509 a ser usado para assinar e criptografar mensagens para serviços ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="82624-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="82624-120">.</span><span class="sxs-lookup"><span data-stu-id="82624-120">.</span></span>|  
|[<span data-ttu-id="82624-121">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="82624-121">\<messageSenderAuthentication></span></span>](messagesenderauthentication.md)|<span data-ttu-id="82624-122">Especifica opções de autenticação para remetentes de mensagens.</span><span class="sxs-lookup"><span data-stu-id="82624-122">Specifies authentication options for message senders.</span></span>|  
|[<span data-ttu-id="82624-123">\<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="82624-123">\<peerAuthentication></span></span>](peerauthentication.md)|<span data-ttu-id="82624-124">Especifica opções de autenticação para serviços de mesmo nível.</span><span class="sxs-lookup"><span data-stu-id="82624-124">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="82624-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="82624-125">Parent Elements</span></span>  
  
|<span data-ttu-id="82624-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="82624-126">Element</span></span>|<span data-ttu-id="82624-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="82624-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="82624-128">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="82624-128">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="82624-129">Especifica a credencial a ser usada na autenticação do serviço e as configurações relacionadas à validação da credencial do cliente.</span><span class="sxs-lookup"><span data-stu-id="82624-129">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="82624-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82624-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="82624-131">Rede ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="82624-131">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="82624-132">[Autenticação de mensagem de canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="82624-132">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="82624-133">[Autenticação personalizada do canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="82624-133">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="82624-134">Protegendo aplicativos de canal par</span><span class="sxs-lookup"><span data-stu-id="82624-134">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="82624-135">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="82624-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
