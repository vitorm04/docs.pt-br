---
title: <peer> de <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: ca97be7b1ab562382895fea4f1d1fc716151b70b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397641"
---
# <a name="peer-of-servicecredentials"></a><span data-ttu-id="2d2ef-102">\<> de pontos \<de ServiceCredentials ></span><span class="sxs-lookup"><span data-stu-id="2d2ef-102">\<peer> of \<serviceCredentials></span></span>
<span data-ttu-id="2d2ef-103">Especifica as credenciais atuais para um nó par.</span><span class="sxs-lookup"><span data-stu-id="2d2ef-103">Specifies the current credentials for a peer node.</span></span>  
  
<span data-ttu-id="2d2ef-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2d2ef-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2d2ef-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="2d2ef-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="2d2ef-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="2d2ef-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="2d2ef-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de portais**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="2d2ef-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="2d2ef-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="2d2ef-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="2d2ef-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="2d2ef-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="2d2ef-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> par**</span><span class="sxs-lookup"><span data-stu-id="2d2ef-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d2ef-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2d2ef-111">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2d2ef-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2d2ef-112">Attributes and Elements</span></span>  
 <span data-ttu-id="2d2ef-113">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="2d2ef-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2d2ef-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="2d2ef-114">Attributes</span></span>  
 <span data-ttu-id="2d2ef-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="2d2ef-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2d2ef-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2d2ef-116">Child Elements</span></span>  
  
|<span data-ttu-id="2d2ef-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="2d2ef-117">Element</span></span>|<span data-ttu-id="2d2ef-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="2d2ef-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2d2ef-119">\<certificate></span><span class="sxs-lookup"><span data-stu-id="2d2ef-119">\<certificate></span></span>](certificate-of-peer.md)|<span data-ttu-id="2d2ef-120">Especifica um certificado X. 509 a ser usado para assinar e criptografar mensagens para serviços ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="2d2ef-120">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="2d2ef-121">.</span><span class="sxs-lookup"><span data-stu-id="2d2ef-121">.</span></span>|  
|[<span data-ttu-id="2d2ef-122">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="2d2ef-122">\<messageSenderAuthentication></span></span>](messagesenderauthentication.md)|<span data-ttu-id="2d2ef-123">Especifica opções de autenticação para remetentes de mensagens.</span><span class="sxs-lookup"><span data-stu-id="2d2ef-123">Specifies authentication options for message senders.</span></span>|  
|[<span data-ttu-id="2d2ef-124">\<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="2d2ef-124">\<peerAuthentication></span></span>](peerauthentication.md)|<span data-ttu-id="2d2ef-125">Especifica opções de autenticação para serviços de mesmo nível.</span><span class="sxs-lookup"><span data-stu-id="2d2ef-125">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2d2ef-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2d2ef-126">Parent Elements</span></span>  
  
|<span data-ttu-id="2d2ef-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="2d2ef-127">Element</span></span>|<span data-ttu-id="2d2ef-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="2d2ef-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2d2ef-129">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="2d2ef-129">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="2d2ef-130">Especifica a credencial a ser usada na autenticação do serviço e as configurações relacionadas à validação da credencial do cliente.</span><span class="sxs-lookup"><span data-stu-id="2d2ef-130">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2d2ef-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2d2ef-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="2d2ef-132">Rede ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="2d2ef-132">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="2d2ef-133">[Autenticação de mensagem de canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="2d2ef-133">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="2d2ef-134">[Autenticação personalizada do canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="2d2ef-134">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="2d2ef-135">Protegendo aplicativos de canal par</span><span class="sxs-lookup"><span data-stu-id="2d2ef-135">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="2d2ef-136">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="2d2ef-136">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
