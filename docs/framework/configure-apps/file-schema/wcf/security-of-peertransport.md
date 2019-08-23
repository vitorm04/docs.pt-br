---
title: <security> de <peerTransport>
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: bdd3b236c9bae198f8027c4ca0c0fa5b70d30342
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936634"
---
# <a name="security-of-peertransport"></a><span data-ttu-id="42b35-102">\<> de segurança \<do peerTransport ></span><span class="sxs-lookup"><span data-stu-id="42b35-102">\<security> of \<peerTransport></span></span>
<span data-ttu-id="42b35-103">Contém as definições de segurança associadas a um canal de pares, incluindo o tipo de autenticação utilizada e a segurança usada para o transporte de mensagens.</span><span class="sxs-lookup"><span data-stu-id="42b35-103">Contains the security settings associated with a peer channel, including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="42b35-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="42b35-104">\<system.serviceModel></span></span>  
<span data-ttu-id="42b35-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="42b35-105">\<bindings></span></span>  
<span data-ttu-id="42b35-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="42b35-106">\<customBinding></span></span>  
<span data-ttu-id="42b35-107">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="42b35-107">\<binding></span></span>  
<span data-ttu-id="42b35-108">\<> peerTransport</span><span class="sxs-lookup"><span data-stu-id="42b35-108">\<peerTransport></span></span>  
<span data-ttu-id="42b35-109">\<> de segurança</span><span class="sxs-lookup"><span data-stu-id="42b35-109">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42b35-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="42b35-110">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">
  <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="42b35-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="42b35-111">Attributes and Elements</span></span>  
 <span data-ttu-id="42b35-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="42b35-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="42b35-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="42b35-113">Attributes</span></span>  
  
|<span data-ttu-id="42b35-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="42b35-114">Attribute</span></span>|<span data-ttu-id="42b35-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="42b35-115">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="42b35-116">Especifica o tipo de segurança a ser aplicado.</span><span class="sxs-lookup"><span data-stu-id="42b35-116">Specifies the type of security to be applied.</span></span> <span data-ttu-id="42b35-117">O valor padrão é Message.</span><span class="sxs-lookup"><span data-stu-id="42b35-117">The default value is Message.</span></span> <span data-ttu-id="42b35-118">Esse atributo é do tipo <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="42b35-118">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="42b35-119">Atributo de modo</span><span class="sxs-lookup"><span data-stu-id="42b35-119">mode Attribute</span></span>  
  
|<span data-ttu-id="42b35-120">Valor</span><span class="sxs-lookup"><span data-stu-id="42b35-120">Value</span></span>|<span data-ttu-id="42b35-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="42b35-121">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="42b35-122">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="42b35-122">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="42b35-123">A proteção é fornecida usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="42b35-123">Security is provided using HTTPS.</span></span>|  
|`Message`|<span data-ttu-id="42b35-124">A segurança SOAP fornece autenticação, integridade e confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="42b35-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="42b35-125">O HTTPS fornece autenticação e confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="42b35-125">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="42b35-126">As mensagens SOAP fornecem tipos de credenciais avançados.</span><span class="sxs-lookup"><span data-stu-id="42b35-126">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="42b35-127">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="42b35-127">Child Elements</span></span>  
  
|<span data-ttu-id="42b35-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="42b35-128">Element</span></span>|<span data-ttu-id="42b35-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="42b35-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="42b35-130">\<> de transporte</span><span class="sxs-lookup"><span data-stu-id="42b35-130">\<transport></span></span>](transport-of-peertransport.md)|<span data-ttu-id="42b35-131">Define um transporte de mesmo nível para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="42b35-131">Defines a peer transport for a custom binding.</span></span> <span data-ttu-id="42b35-132">Esse elemento tem um `clientCredentialType` atributo que especifica as credenciais a serem usadas ao interagir com um serviço.</span><span class="sxs-lookup"><span data-stu-id="42b35-132">This element has a `clientCredentialType` attribute that specifies the credentials to be used when interacting with a service.</span></span> <span data-ttu-id="42b35-133">Esse atributo é do tipo <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="42b35-133">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span><br /><br /> <span data-ttu-id="42b35-134">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="42b35-134">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="42b35-135">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="42b35-135">Parent Elements</span></span>  
  
|<span data-ttu-id="42b35-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="42b35-136">Element</span></span>|<span data-ttu-id="42b35-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="42b35-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="42b35-138">\<peerTransport></span><span class="sxs-lookup"><span data-stu-id="42b35-138">\<peerTransport></span></span>](peertransport.md)|<span data-ttu-id="42b35-139">Define um transporte de mesmo nível para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="42b35-139">Defines a peer transport for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="42b35-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="42b35-140">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="42b35-141">Segurança de transporte</span><span class="sxs-lookup"><span data-stu-id="42b35-141">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="42b35-142">Transportes</span><span class="sxs-lookup"><span data-stu-id="42b35-142">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="42b35-143">Escolhendo um transporte</span><span class="sxs-lookup"><span data-stu-id="42b35-143">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="42b35-144">Associações</span><span class="sxs-lookup"><span data-stu-id="42b35-144">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="42b35-145">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="42b35-145">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="42b35-146">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="42b35-146">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="42b35-147">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="42b35-147">\<customBinding></span></span>](custombinding.md)
