---
title: '&lt;par&gt; do elemento &lt;clientCredentials&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f26321afdbe53c4ab3750eae4a7a730bcb5ae4e4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltpeergt-of-ltclientcredentialsgt-element"></a><span data-ttu-id="5b89c-102">&lt;par&gt; do elemento &lt;clientCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="5b89c-102">&lt;peer&gt; of &lt;clientCredentials&gt; Element</span></span>
<span data-ttu-id="5b89c-103">Especifica as credenciais usadas ao autenticar clientes ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="5b89c-103">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="5b89c-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="5b89c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5b89c-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="5b89c-105">\<behaviors></span></span>  
<span data-ttu-id="5b89c-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="5b89c-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="5b89c-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="5b89c-107">\<behavior></span></span>  
<span data-ttu-id="5b89c-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="5b89c-108">\<clientCredentials></span></span>  
<span data-ttu-id="5b89c-109">\<par ></span><span class="sxs-lookup"><span data-stu-id="5b89c-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b89c-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5b89c-110">Syntax</span></span>  
  
```xml  
<peer>  
  <certificate/>  
  <peerAuthentication/>  
  <messageSenderAuthentication/>  
</peer>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5b89c-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5b89c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5b89c-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5b89c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5b89c-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="5b89c-113">Attributes</span></span>  
 <span data-ttu-id="5b89c-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="5b89c-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5b89c-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5b89c-115">Child Elements</span></span>  
  
|<span data-ttu-id="5b89c-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="5b89c-116">Element</span></span>|<span data-ttu-id="5b89c-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="5b89c-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5b89c-118">\<certificado ></span><span class="sxs-lookup"><span data-stu-id="5b89c-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md)|<span data-ttu-id="5b89c-119">Especifica um certificado x. 509 a ser usado para assinar e criptografar mensagens para clientes ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="5b89c-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="5b89c-120">.</span><span class="sxs-lookup"><span data-stu-id="5b89c-120">.</span></span>|  
|[<span data-ttu-id="5b89c-121">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="5b89c-121">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)|<span data-ttu-id="5b89c-122">Especifica as opções de autenticação para clientes ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="5b89c-122">Specifies authentication options for peer clients.</span></span>|  
|[<span data-ttu-id="5b89c-123">\<messageSenderAuthentication ></span><span class="sxs-lookup"><span data-stu-id="5b89c-123">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)|<span data-ttu-id="5b89c-124">Especifica opções de autenticação para remetentes de mensagens.</span><span class="sxs-lookup"><span data-stu-id="5b89c-124">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5b89c-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5b89c-125">Parent Elements</span></span>  
  
|<span data-ttu-id="5b89c-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="5b89c-126">Element</span></span>|<span data-ttu-id="5b89c-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="5b89c-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5b89c-128">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="5b89c-128">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="5b89c-129">Especifica as credenciais usadas para autenticar um cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="5b89c-129">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b89c-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="5b89c-130">Remarks</span></span>  
 <span data-ttu-id="5b89c-131">Este elemento de configuração especifica credenciais que um nó par usa para se autenticar em outros nós da malha, bem como configurações de autenticação que um nó par usa para autenticar outros nós de mesmo nível.</span><span class="sxs-lookup"><span data-stu-id="5b89c-131">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="5b89c-132">Para obter mais informações, consulte [autenticação de mensagem de canal par](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95) e [proteger aplicativos de canal par](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).</span><span class="sxs-lookup"><span data-stu-id="5b89c-132">For more information, see [Peer Channel Message Authentication](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95) and [Securing Peer Channel Applications](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b89c-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5b89c-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [<span data-ttu-id="5b89c-134">Rede ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="5b89c-134">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 <span data-ttu-id="5b89c-135">[Securing Clients](../../../../../docs/framework/wcf/securing-clients.md) (Protegendo clientes)</span><span class="sxs-lookup"><span data-stu-id="5b89c-135">[Securing Clients](../../../../../docs/framework/wcf/securing-clients.md)</span></span>  
 [<span data-ttu-id="5b89c-136">Autenticação de mensagens de canal par</span><span class="sxs-lookup"><span data-stu-id="5b89c-136">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="5b89c-137">Autenticação personalizada de canal par</span><span class="sxs-lookup"><span data-stu-id="5b89c-137">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="5b89c-138">Protegendo aplicativos de canal par</span><span class="sxs-lookup"><span data-stu-id="5b89c-138">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [<span data-ttu-id="5b89c-139">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="5b89c-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
