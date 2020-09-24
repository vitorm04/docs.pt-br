---
title: <security> de <peerTransport>
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: f37c336b0e42993e1eef3f06e2f919705f425a2e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169954"
---
# <a name="security-of-peertransport"></a><span data-ttu-id="9a5f0-102">\<security> de \<peerTransport></span><span class="sxs-lookup"><span data-stu-id="9a5f0-102">\<security> of \<peerTransport></span></span>

<span data-ttu-id="9a5f0-103">Contém as definições de segurança associadas a um canal de pares, incluindo o tipo de autenticação utilizada e a segurança usada para o transporte de mensagens.</span><span class="sxs-lookup"><span data-stu-id="9a5f0-103">Contains the security settings associated with a peer channel, including the type of authentication used and the security used for the message transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peerTransport>**](peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="9a5f0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9a5f0-104">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">
  <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9a5f0-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9a5f0-105">Attributes and Elements</span></span>  

 <span data-ttu-id="9a5f0-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9a5f0-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9a5f0-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="9a5f0-107">Attributes</span></span>  
  
|<span data-ttu-id="9a5f0-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="9a5f0-108">Attribute</span></span>|<span data-ttu-id="9a5f0-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="9a5f0-109">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="9a5f0-110">Especifica o tipo de segurança a ser aplicado.</span><span class="sxs-lookup"><span data-stu-id="9a5f0-110">Specifies the type of security to be applied.</span></span> <span data-ttu-id="9a5f0-111">O valor padrão é Message.</span><span class="sxs-lookup"><span data-stu-id="9a5f0-111">The default value is Message.</span></span> <span data-ttu-id="9a5f0-112">Esse atributo é do tipo <xref:System.ServiceModel.SecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="9a5f0-112">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="9a5f0-113">Atributo de modo</span><span class="sxs-lookup"><span data-stu-id="9a5f0-113">mode Attribute</span></span>  
  
|<span data-ttu-id="9a5f0-114">Valor</span><span class="sxs-lookup"><span data-stu-id="9a5f0-114">Value</span></span>|<span data-ttu-id="9a5f0-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="9a5f0-115">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="9a5f0-116">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="9a5f0-116">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="9a5f0-117">A proteção é fornecida usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="9a5f0-117">Security is provided using HTTPS.</span></span>|  
|`Message`|<span data-ttu-id="9a5f0-118">A segurança SOAP fornece autenticação, integridade e confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="9a5f0-118">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="9a5f0-119">O HTTPS fornece autenticação e confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="9a5f0-119">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="9a5f0-120">As mensagens SOAP fornecem tipos de credenciais avançados.</span><span class="sxs-lookup"><span data-stu-id="9a5f0-120">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9a5f0-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9a5f0-121">Child Elements</span></span>  
  
|<span data-ttu-id="9a5f0-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="9a5f0-122">Element</span></span>|<span data-ttu-id="9a5f0-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="9a5f0-123">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-peertransport.md)|<span data-ttu-id="9a5f0-124">Define um transporte de mesmo nível para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="9a5f0-124">Defines a peer transport for a custom binding.</span></span> <span data-ttu-id="9a5f0-125">Esse elemento tem um `clientCredentialType` atributo que especifica as credenciais a serem usadas ao interagir com um serviço.</span><span class="sxs-lookup"><span data-stu-id="9a5f0-125">This element has a `clientCredentialType` attribute that specifies the credentials to be used when interacting with a service.</span></span> <span data-ttu-id="9a5f0-126">Esse atributo é do tipo <xref:System.ServiceModel.PeerTransportCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="9a5f0-126">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span><br /><br /> <span data-ttu-id="9a5f0-127">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="9a5f0-127">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9a5f0-128">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9a5f0-128">Parent Elements</span></span>  
  
|<span data-ttu-id="9a5f0-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="9a5f0-129">Element</span></span>|<span data-ttu-id="9a5f0-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="9a5f0-130">Description</span></span>|  
|-------------|-----------------|  
|[\<peerTransport>](peertransport.md)|<span data-ttu-id="9a5f0-131">Define um transporte de mesmo nível para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="9a5f0-131">Defines a peer transport for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9a5f0-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="9a5f0-132">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="9a5f0-133">Segurança de transporte</span><span class="sxs-lookup"><span data-stu-id="9a5f0-133">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="9a5f0-134">Transportes</span><span class="sxs-lookup"><span data-stu-id="9a5f0-134">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="9a5f0-135">Selecionando um transporte</span><span class="sxs-lookup"><span data-stu-id="9a5f0-135">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="9a5f0-136">Associações</span><span class="sxs-lookup"><span data-stu-id="9a5f0-136">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9a5f0-137">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="9a5f0-137">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="9a5f0-138">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="9a5f0-138">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
