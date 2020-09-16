---
title: <peer> do <clientCredentials> elemento
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: a8144ca7bad5654bf8f77259ea1717442665fc81
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555452"
---
# <a name="peer-of-clientcredentials-element"></a><span data-ttu-id="f9a0c-102">\<peer> do \<clientCredentials> elemento</span><span class="sxs-lookup"><span data-stu-id="f9a0c-102">\<peer> of \<clientCredentials> Element</span></span>
<span data-ttu-id="f9a0c-103">Especifica as credenciais usadas ao autenticar clientes ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="f9a0c-103">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peer>**  
  
## <a name="syntax"></a><span data-ttu-id="f9a0c-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="f9a0c-104">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f9a0c-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f9a0c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f9a0c-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f9a0c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f9a0c-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="f9a0c-107">Attributes</span></span>  
 <span data-ttu-id="f9a0c-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="f9a0c-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f9a0c-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f9a0c-109">Child Elements</span></span>  
  
|<span data-ttu-id="f9a0c-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="f9a0c-110">Element</span></span>|<span data-ttu-id="f9a0c-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="f9a0c-111">Description</span></span>|  
|-------------|-----------------|  
|[\<certificate>](certificate-element.md)|<span data-ttu-id="f9a0c-112">Especifica um certificado X. 509 a ser usado para assinar e criptografar mensagens para clientes ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="f9a0c-112">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="f9a0c-113">.</span><span class="sxs-lookup"><span data-stu-id="f9a0c-113">.</span></span>|  
|[\<peerAuthentication>](peerauthentication-element.md)|<span data-ttu-id="f9a0c-114">Especifica opções de autenticação para clientes pares.</span><span class="sxs-lookup"><span data-stu-id="f9a0c-114">Specifies authentication options for peer clients.</span></span>|  
|[\<messageSenderAuthentication>](messagesenderauthentication-element.md)|<span data-ttu-id="f9a0c-115">Especifica opções de autenticação para remetentes de mensagens.</span><span class="sxs-lookup"><span data-stu-id="f9a0c-115">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f9a0c-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f9a0c-116">Parent Elements</span></span>  
  
|<span data-ttu-id="f9a0c-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="f9a0c-117">Element</span></span>|<span data-ttu-id="f9a0c-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="f9a0c-118">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="f9a0c-119">Especifica as credenciais usadas para autenticar um cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="f9a0c-119">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9a0c-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="f9a0c-120">Remarks</span></span>  
 <span data-ttu-id="f9a0c-121">Esse elemento de configuração especifica as credenciais que um nó par usa para se autenticar em outros nós na malha, bem como configurações de autenticação que um nó par usa para autenticar outros nós de mesmo nível.</span><span class="sxs-lookup"><span data-stu-id="f9a0c-121">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="f9a0c-122">Para obter mais informações, consulte [autenticação de mensagens de canal de emparelhamento](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) e [protegendo os aplicativos de canal de mesmo nível](../../../wcf/feature-details/securing-peer-channel-applications.md).</span><span class="sxs-lookup"><span data-stu-id="f9a0c-122">For more information, see [Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) and [Securing Peer Channel Applications](../../../wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9a0c-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="f9a0c-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="f9a0c-124">Rede peer-to-peer</span><span class="sxs-lookup"><span data-stu-id="f9a0c-124">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="f9a0c-125">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="f9a0c-125">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- <span data-ttu-id="f9a0c-126">[Autenticação de mensagem de canal par](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="f9a0c-126">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="f9a0c-127">[Autenticação personalizada do canal par](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="f9a0c-127">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="f9a0c-128">Protegendo aplicativos de canal par</span><span class="sxs-lookup"><span data-stu-id="f9a0c-128">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="f9a0c-129">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="f9a0c-129">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
