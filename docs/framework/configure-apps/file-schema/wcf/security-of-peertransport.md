---
title: '&lt;segurança&gt; de &lt;peerTransport&gt;'
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: 8b0b8c5f230e8e93c07e13212201896010429af0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585374"
---
# <a name="ltsecuritygt-of-ltpeertransportgt"></a><span data-ttu-id="1bf5b-102">&lt;segurança&gt; de &lt;peerTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="1bf5b-102">&lt;security&gt; of &lt;peerTransport&gt;</span></span>
<span data-ttu-id="1bf5b-103">Contém as definições de segurança associadas a um canal de pares, incluindo o tipo de autenticação utilizada e a segurança usada para o transporte de mensagens.</span><span class="sxs-lookup"><span data-stu-id="1bf5b-103">Contains the security settings associated with a peer channel, including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="1bf5b-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1bf5b-104">\<system.serviceModel></span></span>  
<span data-ttu-id="1bf5b-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="1bf5b-105">\<bindings></span></span>  
<span data-ttu-id="1bf5b-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="1bf5b-106">\<customBinding></span></span>  
<span data-ttu-id="1bf5b-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="1bf5b-107">\<binding></span></span>  
<span data-ttu-id="1bf5b-108">\<peerTransport></span><span class="sxs-lookup"><span data-stu-id="1bf5b-108">\<peerTransport></span></span>  
<span data-ttu-id="1bf5b-109">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="1bf5b-109">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bf5b-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1bf5b-110">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">
  <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1bf5b-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1bf5b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1bf5b-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1bf5b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1bf5b-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="1bf5b-113">Attributes</span></span>  
  
|<span data-ttu-id="1bf5b-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="1bf5b-114">Attribute</span></span>|<span data-ttu-id="1bf5b-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="1bf5b-115">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="1bf5b-116">Especifica o tipo de segurança a ser aplicada.</span><span class="sxs-lookup"><span data-stu-id="1bf5b-116">Specifies the type of security to be applied.</span></span> <span data-ttu-id="1bf5b-117">O valor padrão é a mensagem.</span><span class="sxs-lookup"><span data-stu-id="1bf5b-117">The default value is Message.</span></span> <span data-ttu-id="1bf5b-118">Esse atributo é do tipo <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="1bf5b-118">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="1bf5b-119">modo de atributo</span><span class="sxs-lookup"><span data-stu-id="1bf5b-119">mode Attribute</span></span>  
  
|<span data-ttu-id="1bf5b-120">Valor</span><span class="sxs-lookup"><span data-stu-id="1bf5b-120">Value</span></span>|<span data-ttu-id="1bf5b-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="1bf5b-121">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="1bf5b-122">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="1bf5b-122">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="1bf5b-123">A proteção é fornecida usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="1bf5b-123">Security is provided using HTTPS.</span></span>|  
|`Message`|<span data-ttu-id="1bf5b-124">Segurança SOAP fornece autenticação, integridade e confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="1bf5b-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="1bf5b-125">HTTPS fornece autenticação e confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="1bf5b-125">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="1bf5b-126">As mensagens SOAP fornecem tipos de credencial avançados.</span><span class="sxs-lookup"><span data-stu-id="1bf5b-126">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1bf5b-127">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1bf5b-127">Child Elements</span></span>  
  
|<span data-ttu-id="1bf5b-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="1bf5b-128">Element</span></span>|<span data-ttu-id="1bf5b-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="1bf5b-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1bf5b-130">\<transport></span><span class="sxs-lookup"><span data-stu-id="1bf5b-130">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-peertransport.md)|<span data-ttu-id="1bf5b-131">Define um transporte de par para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="1bf5b-131">Defines a peer transport for a custom binding.</span></span> <span data-ttu-id="1bf5b-132">Este elemento tem um `clientCredentialType` atributo que especifica as credenciais a serem usadas ao interagir com um serviço.</span><span class="sxs-lookup"><span data-stu-id="1bf5b-132">This element has a `clientCredentialType` attribute that specifies the credentials to be used when interacting with a service.</span></span> <span data-ttu-id="1bf5b-133">Esse atributo é do tipo <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="1bf5b-133">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span><br /><br /> <span data-ttu-id="1bf5b-134">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="1bf5b-134">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1bf5b-135">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1bf5b-135">Parent Elements</span></span>  
  
|<span data-ttu-id="1bf5b-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="1bf5b-136">Element</span></span>|<span data-ttu-id="1bf5b-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="1bf5b-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1bf5b-138">\<peerTransport></span><span class="sxs-lookup"><span data-stu-id="1bf5b-138">\<peerTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peertransport.md)|<span data-ttu-id="1bf5b-139">Define um transporte de par para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="1bf5b-139">Defines a peer transport for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1bf5b-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1bf5b-140">See also</span></span>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="1bf5b-141">Segurança de transporte</span><span class="sxs-lookup"><span data-stu-id="1bf5b-141">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)
- [<span data-ttu-id="1bf5b-142">Transportes</span><span class="sxs-lookup"><span data-stu-id="1bf5b-142">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="1bf5b-143">Escolhendo um transporte</span><span class="sxs-lookup"><span data-stu-id="1bf5b-143">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="1bf5b-144">Associações</span><span class="sxs-lookup"><span data-stu-id="1bf5b-144">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="1bf5b-145">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="1bf5b-145">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="1bf5b-146">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="1bf5b-146">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="1bf5b-147">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="1bf5b-147">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
