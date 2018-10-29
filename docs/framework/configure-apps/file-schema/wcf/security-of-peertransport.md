---
title: '&lt;segurança&gt; de &lt;peerTransport&gt;'
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: c7a2a2cde58dac87b1b378fe2ac8148493c1cf09
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50200451"
---
# <a name="ltsecuritygt-of-ltpeertransportgt"></a><span data-ttu-id="f6ac4-102">&lt;segurança&gt; de &lt;peerTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="f6ac4-102">&lt;security&gt; of &lt;peerTransport&gt;</span></span>
<span data-ttu-id="f6ac4-103">Contém as definições de segurança associadas a um canal de pares, incluindo o tipo de autenticação utilizada e a segurança usada para o transporte de mensagens.</span><span class="sxs-lookup"><span data-stu-id="f6ac4-103">Contains the security settings associated with a peer channel, including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="f6ac4-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f6ac4-104">\<system.serviceModel></span></span>  
<span data-ttu-id="f6ac4-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="f6ac4-105">\<bindings></span></span>  
<span data-ttu-id="f6ac4-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="f6ac4-106">\<customBinding></span></span>  
<span data-ttu-id="f6ac4-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="f6ac4-107">\<binding></span></span>  
<span data-ttu-id="f6ac4-108">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="f6ac4-108">\<peerTransport></span></span>  
<span data-ttu-id="f6ac4-109">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="f6ac4-109">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6ac4-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f6ac4-110">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">  
    <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />  
</security  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f6ac4-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f6ac4-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f6ac4-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f6ac4-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f6ac4-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="f6ac4-113">Attributes</span></span>  
  
|<span data-ttu-id="f6ac4-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="f6ac4-114">Attribute</span></span>|<span data-ttu-id="f6ac4-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6ac4-115">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="f6ac4-116">Especifica o tipo de segurança a ser aplicada.</span><span class="sxs-lookup"><span data-stu-id="f6ac4-116">Specifies the type of security to be applied.</span></span> <span data-ttu-id="f6ac4-117">O valor padrão é a mensagem.</span><span class="sxs-lookup"><span data-stu-id="f6ac4-117">The default value is Message.</span></span> <span data-ttu-id="f6ac4-118">Esse atributo é do tipo <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="f6ac4-118">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="f6ac4-119">modo de atributo</span><span class="sxs-lookup"><span data-stu-id="f6ac4-119">mode Attribute</span></span>  
  
|<span data-ttu-id="f6ac4-120">Valor</span><span class="sxs-lookup"><span data-stu-id="f6ac4-120">Value</span></span>|<span data-ttu-id="f6ac4-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6ac4-121">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="f6ac4-122">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="f6ac4-122">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="f6ac4-123">A proteção é fornecida usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f6ac4-123">Security is provided using HTTPS.</span></span>|  
|`Message`|<span data-ttu-id="f6ac4-124">Segurança SOAP fornece autenticação, integridade e confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="f6ac4-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="f6ac4-125">HTTPS fornece autenticação e confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="f6ac4-125">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="f6ac4-126">As mensagens SOAP fornecem tipos de credencial avançados.</span><span class="sxs-lookup"><span data-stu-id="f6ac4-126">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f6ac4-127">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f6ac4-127">Child Elements</span></span>  
  
|<span data-ttu-id="f6ac4-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="f6ac4-128">Element</span></span>|<span data-ttu-id="f6ac4-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6ac4-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f6ac4-130">\<transporte ></span><span class="sxs-lookup"><span data-stu-id="f6ac4-130">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-peertransport.md)|<span data-ttu-id="f6ac4-131">Define um transporte de par para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="f6ac4-131">Defines a peer transport for a custom binding.</span></span> <span data-ttu-id="f6ac4-132">Este elemento tem um `clientCredentialType` atributo que especifica as credenciais a serem usadas ao interagir com um serviço.</span><span class="sxs-lookup"><span data-stu-id="f6ac4-132">This element has a `clientCredentialType` attribute that specifies the credentials to be used when interacting with a service.</span></span> <span data-ttu-id="f6ac4-133">Esse atributo é do tipo <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="f6ac4-133">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span><br /><br /> <span data-ttu-id="f6ac4-134">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="f6ac4-134">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f6ac4-135">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f6ac4-135">Parent Elements</span></span>  
  
|<span data-ttu-id="f6ac4-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="f6ac4-136">Element</span></span>|<span data-ttu-id="f6ac4-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6ac4-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f6ac4-138">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="f6ac4-138">\<peerTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peertransport.md)|<span data-ttu-id="f6ac4-139">Define um transporte de par para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="f6ac4-139">Defines a peer transport for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f6ac4-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f6ac4-140">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="f6ac4-141">Segurança de transporte</span><span class="sxs-lookup"><span data-stu-id="f6ac4-141">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [<span data-ttu-id="f6ac4-142">Transportes</span><span class="sxs-lookup"><span data-stu-id="f6ac4-142">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="f6ac4-143">Escolhendo um transporte</span><span class="sxs-lookup"><span data-stu-id="f6ac4-143">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="f6ac4-144">Associações</span><span class="sxs-lookup"><span data-stu-id="f6ac4-144">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="f6ac4-145">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="f6ac4-145">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="f6ac4-146">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="f6ac4-146">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="f6ac4-147">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="f6ac4-147">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
