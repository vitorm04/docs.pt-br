---
title: <peer> de <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: ca97be7b1ab562382895fea4f1d1fc716151b70b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397641"
---
# <a name="peer-of-servicecredentials"></a><span data-ttu-id="af0c8-102">\<peer> de \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="af0c8-102">\<peer> of \<serviceCredentials></span></span>
<span data-ttu-id="af0c8-103">Especifica as credenciais atuais para um nó par.</span><span class="sxs-lookup"><span data-stu-id="af0c8-103">Specifies the current credentials for a peer node.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peer>**  
  
## <a name="syntax"></a><span data-ttu-id="af0c8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="af0c8-104">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="af0c8-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="af0c8-105">Attributes and Elements</span></span>  
 <span data-ttu-id="af0c8-106">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="af0c8-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="af0c8-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="af0c8-107">Attributes</span></span>  
 <span data-ttu-id="af0c8-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="af0c8-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="af0c8-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="af0c8-109">Child Elements</span></span>  
  
|<span data-ttu-id="af0c8-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="af0c8-110">Element</span></span>|<span data-ttu-id="af0c8-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="af0c8-111">Description</span></span>|  
|-------------|-----------------|  
|[\<certificate>](certificate-of-peer.md)|<span data-ttu-id="af0c8-112">Especifica um certificado X. 509 a ser usado para assinar e criptografar mensagens para serviços ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="af0c8-112">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="af0c8-113">.</span><span class="sxs-lookup"><span data-stu-id="af0c8-113">.</span></span>|  
|[\<messageSenderAuthentication>](messagesenderauthentication.md)|<span data-ttu-id="af0c8-114">Especifica opções de autenticação para remetentes de mensagens.</span><span class="sxs-lookup"><span data-stu-id="af0c8-114">Specifies authentication options for message senders.</span></span>|  
|[\<peerAuthentication>](peerauthentication.md)|<span data-ttu-id="af0c8-115">Especifica opções de autenticação para serviços de mesmo nível.</span><span class="sxs-lookup"><span data-stu-id="af0c8-115">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="af0c8-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="af0c8-116">Parent Elements</span></span>  
  
|<span data-ttu-id="af0c8-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="af0c8-117">Element</span></span>|<span data-ttu-id="af0c8-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="af0c8-118">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="af0c8-119">Especifica a credencial a ser usada na autenticação do serviço e as configurações relacionadas à validação da credencial do cliente.</span><span class="sxs-lookup"><span data-stu-id="af0c8-119">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="af0c8-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="af0c8-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="af0c8-121">Rede ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="af0c8-121">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="af0c8-122">[Autenticação de mensagem de canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="af0c8-122">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="af0c8-123">[Autenticação personalizada do canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="af0c8-123">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="af0c8-124">Protegendo aplicativos de canal par</span><span class="sxs-lookup"><span data-stu-id="af0c8-124">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="af0c8-125">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="af0c8-125">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
