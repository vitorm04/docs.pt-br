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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3754964d07dd80442fbffd7c632304ef9d83ab1d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltpeergt-of-ltservicecredentialsgt"></a><span data-ttu-id="7b9ce-102">&lt;peer&gt; de &lt;serviceCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="7b9ce-102">&lt;peer&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="7b9ce-103">Especifica as credenciais atuais de um nó ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="7b9ce-103">Specifies the current credentials for a peer node.</span></span>  
  
 <span data-ttu-id="7b9ce-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="7b9ce-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7b9ce-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="7b9ce-105">\<behaviors></span></span>  
<span data-ttu-id="7b9ce-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="7b9ce-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="7b9ce-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="7b9ce-107">\<behavior></span></span>  
<span data-ttu-id="7b9ce-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="7b9ce-108">\<serviceCredentials></span></span>  
<span data-ttu-id="7b9ce-109">\<par ></span><span class="sxs-lookup"><span data-stu-id="7b9ce-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b9ce-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7b9ce-110">Syntax</span></span>  
  
```xml  
<peer>  
  <certificate/>  
  <peerAuthentication/>  
  <messageSenderAuthentication/>  
</peer>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7b9ce-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7b9ce-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7b9ce-112">As seções a seguir descrevem os elementos pai de atributos e elementos filho</span><span class="sxs-lookup"><span data-stu-id="7b9ce-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7b9ce-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="7b9ce-113">Attributes</span></span>  
 <span data-ttu-id="7b9ce-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="7b9ce-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7b9ce-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7b9ce-115">Child Elements</span></span>  
  
|<span data-ttu-id="7b9ce-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="7b9ce-116">Element</span></span>|<span data-ttu-id="7b9ce-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="7b9ce-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7b9ce-118">\<certificado ></span><span class="sxs-lookup"><span data-stu-id="7b9ce-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-peer.md)|<span data-ttu-id="7b9ce-119">Especifica um certificado x. 509 a ser usado para assinar e criptografar mensagens para serviços ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="7b9ce-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="7b9ce-120">.</span><span class="sxs-lookup"><span data-stu-id="7b9ce-120">.</span></span>|  
|[<span data-ttu-id="7b9ce-121">\<messageSenderAuthentication ></span><span class="sxs-lookup"><span data-stu-id="7b9ce-121">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication.md)|<span data-ttu-id="7b9ce-122">Especifica opções de autenticação para remetentes de mensagens.</span><span class="sxs-lookup"><span data-stu-id="7b9ce-122">Specifies authentication options for message senders.</span></span>|  
|[<span data-ttu-id="7b9ce-123">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="7b9ce-123">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication.md)|<span data-ttu-id="7b9ce-124">Especifica opções de autenticação para serviços ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="7b9ce-124">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7b9ce-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7b9ce-125">Parent Elements</span></span>  
  
|<span data-ttu-id="7b9ce-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="7b9ce-126">Element</span></span>|<span data-ttu-id="7b9ce-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="7b9ce-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7b9ce-128">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="7b9ce-128">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="7b9ce-129">Especifica a credencial a ser usado na autenticação do serviço e as configurações de relacionadas à validação de credenciais do cliente.</span><span class="sxs-lookup"><span data-stu-id="7b9ce-129">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7b9ce-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7b9ce-130">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [<span data-ttu-id="7b9ce-131">Rede ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="7b9ce-131">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="7b9ce-132">Autenticação de mensagens de canal par</span><span class="sxs-lookup"><span data-stu-id="7b9ce-132">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="7b9ce-133">Autenticação personalizada de canal par</span><span class="sxs-lookup"><span data-stu-id="7b9ce-133">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="7b9ce-134">Protegendo aplicativos de canal par</span><span class="sxs-lookup"><span data-stu-id="7b9ce-134">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [<span data-ttu-id="7b9ce-135">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="7b9ce-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
