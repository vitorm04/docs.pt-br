---
title: <peer>do <clientCredentials> elemento
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: dce7ef64de1e3eb248e3553c97cbce8e9b205b4c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400093"
---
# <a name="peer-of-clientcredentials-element"></a><span data-ttu-id="2e96f-102">\<> de pares \<de ClientCredentials > elemento</span><span class="sxs-lookup"><span data-stu-id="2e96f-102">\<peer> of \<clientCredentials> Element</span></span>
<span data-ttu-id="2e96f-103">Especifica as credenciais usadas ao autenticar clientes ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="2e96f-103">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
<span data-ttu-id="2e96f-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2e96f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2e96f-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="2e96f-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="2e96f-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="2e96f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="2e96f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> endpointBehaviors**](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="2e96f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="2e96f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="2e96f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="2e96f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="2e96f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="2e96f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> par**</span><span class="sxs-lookup"><span data-stu-id="2e96f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e96f-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2e96f-111">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2e96f-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2e96f-112">Attributes and Elements</span></span>  
 <span data-ttu-id="2e96f-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2e96f-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2e96f-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="2e96f-114">Attributes</span></span>  
 <span data-ttu-id="2e96f-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="2e96f-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2e96f-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2e96f-116">Child Elements</span></span>  
  
|<span data-ttu-id="2e96f-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="2e96f-117">Element</span></span>|<span data-ttu-id="2e96f-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="2e96f-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2e96f-119">\<certificate></span><span class="sxs-lookup"><span data-stu-id="2e96f-119">\<certificate></span></span>](certificate-element.md)|<span data-ttu-id="2e96f-120">Especifica um certificado X. 509 a ser usado para assinar e criptografar mensagens para clientes ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="2e96f-120">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="2e96f-121">.</span><span class="sxs-lookup"><span data-stu-id="2e96f-121">.</span></span>|  
|[<span data-ttu-id="2e96f-122">\<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="2e96f-122">\<peerAuthentication></span></span>](peerauthentication-element.md)|<span data-ttu-id="2e96f-123">Especifica opções de autenticação para clientes pares.</span><span class="sxs-lookup"><span data-stu-id="2e96f-123">Specifies authentication options for peer clients.</span></span>|  
|[<span data-ttu-id="2e96f-124">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="2e96f-124">\<messageSenderAuthentication></span></span>](messagesenderauthentication-element.md)|<span data-ttu-id="2e96f-125">Especifica opções de autenticação para remetentes de mensagens.</span><span class="sxs-lookup"><span data-stu-id="2e96f-125">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2e96f-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2e96f-126">Parent Elements</span></span>  
  
|<span data-ttu-id="2e96f-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="2e96f-127">Element</span></span>|<span data-ttu-id="2e96f-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="2e96f-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2e96f-129">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="2e96f-129">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="2e96f-130">Especifica as credenciais usadas para autenticar um cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="2e96f-130">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e96f-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="2e96f-131">Remarks</span></span>  
 <span data-ttu-id="2e96f-132">Esse elemento de configuração especifica as credenciais que um nó par usa para se autenticar em outros nós na malha, bem como configurações de autenticação que um nó par usa para autenticar outros nós de mesmo nível.</span><span class="sxs-lookup"><span data-stu-id="2e96f-132">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="2e96f-133">Para obter mais informações, consulte [autenticação de mensagens de canal de emparelhamento](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) e [protegendo os aplicativos de canal de mesmo nível](../../../wcf/feature-details/securing-peer-channel-applications.md).</span><span class="sxs-lookup"><span data-stu-id="2e96f-133">For more information, see [Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) and [Securing Peer Channel Applications](../../../wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e96f-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2e96f-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="2e96f-135">Rede ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="2e96f-135">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="2e96f-136">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="2e96f-136">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- <span data-ttu-id="2e96f-137">[Autenticação de mensagem de canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="2e96f-137">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="2e96f-138">[Autenticação personalizada do canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="2e96f-138">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="2e96f-139">Protegendo aplicativos de canal par</span><span class="sxs-lookup"><span data-stu-id="2e96f-139">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="2e96f-140">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="2e96f-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
