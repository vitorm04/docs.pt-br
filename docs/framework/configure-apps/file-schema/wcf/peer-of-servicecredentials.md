---
title: <peer> de <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: d726ab460141b1e373a1cabf770b8958f50319eb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783390"
---
# <a name="peer-of-servicecredentials"></a><span data-ttu-id="f063b-102">\<Peer > de \<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="f063b-102">\<peer> of \<serviceCredentials></span></span>
<span data-ttu-id="f063b-103">Especifica as credenciais atuais para um nó par.</span><span class="sxs-lookup"><span data-stu-id="f063b-103">Specifies the current credentials for a peer node.</span></span>  
  
 <span data-ttu-id="f063b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f063b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f063b-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="f063b-105">\<behaviors></span></span>  
<span data-ttu-id="f063b-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="f063b-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="f063b-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="f063b-107">\<behavior></span></span>  
<span data-ttu-id="f063b-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="f063b-108">\<serviceCredentials></span></span>  
<span data-ttu-id="f063b-109">\<peer></span><span class="sxs-lookup"><span data-stu-id="f063b-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f063b-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f063b-110">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f063b-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f063b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f063b-112">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="f063b-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f063b-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="f063b-113">Attributes</span></span>  
 <span data-ttu-id="f063b-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="f063b-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f063b-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f063b-115">Child Elements</span></span>  
  
|<span data-ttu-id="f063b-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="f063b-116">Element</span></span>|<span data-ttu-id="f063b-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="f063b-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f063b-118">\<certificate></span><span class="sxs-lookup"><span data-stu-id="f063b-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-peer.md)|<span data-ttu-id="f063b-119">Especifica um certificado X.509 a ser usado para assinar e criptografar mensagens para serviços ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="f063b-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="f063b-120">.</span><span class="sxs-lookup"><span data-stu-id="f063b-120">.</span></span>|  
|[<span data-ttu-id="f063b-121">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="f063b-121">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication.md)|<span data-ttu-id="f063b-122">Especifica opções de autenticação para remetentes de mensagens.</span><span class="sxs-lookup"><span data-stu-id="f063b-122">Specifies authentication options for message senders.</span></span>|  
|[<span data-ttu-id="f063b-123">\<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="f063b-123">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication.md)|<span data-ttu-id="f063b-124">Especifica opções de autenticação para serviços ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="f063b-124">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f063b-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f063b-125">Parent Elements</span></span>  
  
|<span data-ttu-id="f063b-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="f063b-126">Element</span></span>|<span data-ttu-id="f063b-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="f063b-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f063b-128">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="f063b-128">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="f063b-129">Especifica a credencial a ser usado na autenticação do serviço e as configurações de relacionadas à validação de credenciais do cliente.</span><span class="sxs-lookup"><span data-stu-id="f063b-129">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f063b-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f063b-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="f063b-131">Rede ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="f063b-131">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="f063b-132">[Autenticação de mensagem de canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="f063b-132">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="f063b-133">[Autenticação personalizada de canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="f063b-133">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="f063b-134">Protegendo aplicativos de canal par</span><span class="sxs-lookup"><span data-stu-id="f063b-134">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="f063b-135">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="f063b-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
