---
title: <peer>do <clientCredentials> elemento
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: dce7ef64de1e3eb248e3553c97cbce8e9b205b4c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400093"
---
# <a name="peer-of-clientcredentials-element"></a><span data-ttu-id="fdd9d-102">\<peer>do \<clientCredentials> elemento</span><span class="sxs-lookup"><span data-stu-id="fdd9d-102">\<peer> of \<clientCredentials> Element</span></span>
<span data-ttu-id="fdd9d-103">Especifica as credenciais usadas ao autenticar clientes ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="fdd9d-103">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peer>**  
  
## <a name="syntax"></a><span data-ttu-id="fdd9d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fdd9d-104">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fdd9d-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fdd9d-105">Attributes and Elements</span></span>  
 <span data-ttu-id="fdd9d-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="fdd9d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fdd9d-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="fdd9d-107">Attributes</span></span>  
 <span data-ttu-id="fdd9d-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="fdd9d-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fdd9d-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="fdd9d-109">Child Elements</span></span>  
  
|<span data-ttu-id="fdd9d-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="fdd9d-110">Element</span></span>|<span data-ttu-id="fdd9d-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="fdd9d-111">Description</span></span>|  
|-------------|-----------------|  
|[\<certificate>](certificate-element.md)|<span data-ttu-id="fdd9d-112">Especifica um certificado X. 509 a ser usado para assinar e criptografar mensagens para clientes ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="fdd9d-112">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="fdd9d-113">.</span><span class="sxs-lookup"><span data-stu-id="fdd9d-113">.</span></span>|  
|[\<peerAuthentication>](peerauthentication-element.md)|<span data-ttu-id="fdd9d-114">Especifica opções de autenticação para clientes pares.</span><span class="sxs-lookup"><span data-stu-id="fdd9d-114">Specifies authentication options for peer clients.</span></span>|  
|[\<messageSenderAuthentication>](messagesenderauthentication-element.md)|<span data-ttu-id="fdd9d-115">Especifica opções de autenticação para remetentes de mensagens.</span><span class="sxs-lookup"><span data-stu-id="fdd9d-115">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fdd9d-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="fdd9d-116">Parent Elements</span></span>  
  
|<span data-ttu-id="fdd9d-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="fdd9d-117">Element</span></span>|<span data-ttu-id="fdd9d-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="fdd9d-118">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="fdd9d-119">Especifica as credenciais usadas para autenticar um cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="fdd9d-119">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fdd9d-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="fdd9d-120">Remarks</span></span>  
 <span data-ttu-id="fdd9d-121">Esse elemento de configuração especifica as credenciais que um nó par usa para se autenticar em outros nós na malha, bem como configurações de autenticação que um nó par usa para autenticar outros nós de mesmo nível.</span><span class="sxs-lookup"><span data-stu-id="fdd9d-121">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="fdd9d-122">Para obter mais informações, consulte [autenticação de mensagens de canal de emparelhamento](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) e [protegendo os aplicativos de canal de mesmo nível](../../../wcf/feature-details/securing-peer-channel-applications.md).</span><span class="sxs-lookup"><span data-stu-id="fdd9d-122">For more information, see [Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) and [Securing Peer Channel Applications](../../../wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdd9d-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="fdd9d-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="fdd9d-124">Rede ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="fdd9d-124">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="fdd9d-125">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="fdd9d-125">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- <span data-ttu-id="fdd9d-126">[Autenticação de mensagem de canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="fdd9d-126">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="fdd9d-127">[Autenticação personalizada do canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="fdd9d-127">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="fdd9d-128">Protegendo aplicativos de canal par</span><span class="sxs-lookup"><span data-stu-id="fdd9d-128">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="fdd9d-129">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="fdd9d-129">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
