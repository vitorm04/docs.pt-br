---
title: <security> de <peerTransport>
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: 1aff79bf5867a3a1ebe05e3f812475dac4b413e9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59116851"
---
# <a name="security-of-peertransport"></a><span data-ttu-id="0e063-102">\<segurança > de \<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="0e063-102">\<security> of \<peerTransport></span></span>
<span data-ttu-id="0e063-103">Contém as definições de segurança associadas a um canal de pares, incluindo o tipo de autenticação utilizada e a segurança usada para o transporte de mensagens.</span><span class="sxs-lookup"><span data-stu-id="0e063-103">Contains the security settings associated with a peer channel, including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="0e063-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="0e063-104">\<system.serviceModel></span></span>  
<span data-ttu-id="0e063-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="0e063-105">\<bindings></span></span>  
<span data-ttu-id="0e063-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="0e063-106">\<customBinding></span></span>  
<span data-ttu-id="0e063-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="0e063-107">\<binding></span></span>  
<span data-ttu-id="0e063-108">\<peerTransport></span><span class="sxs-lookup"><span data-stu-id="0e063-108">\<peerTransport></span></span>  
<span data-ttu-id="0e063-109">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="0e063-109">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e063-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0e063-110">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">
  <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0e063-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0e063-111">Attributes and Elements</span></span>  
 <span data-ttu-id="0e063-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0e063-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0e063-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="0e063-113">Attributes</span></span>  
  
|<span data-ttu-id="0e063-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="0e063-114">Attribute</span></span>|<span data-ttu-id="0e063-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="0e063-115">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="0e063-116">Especifica o tipo de segurança a ser aplicada.</span><span class="sxs-lookup"><span data-stu-id="0e063-116">Specifies the type of security to be applied.</span></span> <span data-ttu-id="0e063-117">O valor padrão é a mensagem.</span><span class="sxs-lookup"><span data-stu-id="0e063-117">The default value is Message.</span></span> <span data-ttu-id="0e063-118">Esse atributo é do tipo <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="0e063-118">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="0e063-119">modo de atributo</span><span class="sxs-lookup"><span data-stu-id="0e063-119">mode Attribute</span></span>  
  
|<span data-ttu-id="0e063-120">Valor</span><span class="sxs-lookup"><span data-stu-id="0e063-120">Value</span></span>|<span data-ttu-id="0e063-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="0e063-121">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="0e063-122">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="0e063-122">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="0e063-123">A proteção é fornecida usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="0e063-123">Security is provided using HTTPS.</span></span>|  
|`Message`|<span data-ttu-id="0e063-124">Segurança SOAP fornece autenticação, integridade e confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="0e063-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="0e063-125">HTTPS fornece autenticação e confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="0e063-125">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="0e063-126">As mensagens SOAP fornecem tipos de credencial avançados.</span><span class="sxs-lookup"><span data-stu-id="0e063-126">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0e063-127">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0e063-127">Child Elements</span></span>  
  
|<span data-ttu-id="0e063-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="0e063-128">Element</span></span>|<span data-ttu-id="0e063-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="0e063-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0e063-130">\<transport></span><span class="sxs-lookup"><span data-stu-id="0e063-130">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-peertransport.md)|<span data-ttu-id="0e063-131">Define um transporte de par para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="0e063-131">Defines a peer transport for a custom binding.</span></span> <span data-ttu-id="0e063-132">Este elemento tem um `clientCredentialType` atributo que especifica as credenciais a serem usadas ao interagir com um serviço.</span><span class="sxs-lookup"><span data-stu-id="0e063-132">This element has a `clientCredentialType` attribute that specifies the credentials to be used when interacting with a service.</span></span> <span data-ttu-id="0e063-133">Esse atributo é do tipo <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="0e063-133">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span><br /><br /> <span data-ttu-id="0e063-134">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="0e063-134">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0e063-135">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0e063-135">Parent Elements</span></span>  
  
|<span data-ttu-id="0e063-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="0e063-136">Element</span></span>|<span data-ttu-id="0e063-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="0e063-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0e063-138">\<peerTransport></span><span class="sxs-lookup"><span data-stu-id="0e063-138">\<peerTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peertransport.md)|<span data-ttu-id="0e063-139">Define um transporte de par para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="0e063-139">Defines a peer transport for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0e063-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0e063-140">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="0e063-141">Segurança de transporte</span><span class="sxs-lookup"><span data-stu-id="0e063-141">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)
- [<span data-ttu-id="0e063-142">Transportes</span><span class="sxs-lookup"><span data-stu-id="0e063-142">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="0e063-143">Escolhendo um transporte</span><span class="sxs-lookup"><span data-stu-id="0e063-143">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="0e063-144">Associações</span><span class="sxs-lookup"><span data-stu-id="0e063-144">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="0e063-145">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="0e063-145">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="0e063-146">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="0e063-146">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="0e063-147">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="0e063-147">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
