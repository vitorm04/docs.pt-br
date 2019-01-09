---
title: '&lt;segurança&gt; de &lt;peerTransport&gt;'
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: 901a1d0b29fa6ea7d9e520b379dc7c7ff1d1e522
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151950"
---
# <a name="ltsecuritygt-of-ltpeertransportgt"></a><span data-ttu-id="9443a-102">&lt;segurança&gt; de &lt;peerTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="9443a-102">&lt;security&gt; of &lt;peerTransport&gt;</span></span>
<span data-ttu-id="9443a-103">Contém as definições de segurança associadas a um canal de pares, incluindo o tipo de autenticação utilizada e a segurança usada para o transporte de mensagens.</span><span class="sxs-lookup"><span data-stu-id="9443a-103">Contains the security settings associated with a peer channel, including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="9443a-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9443a-104">\<system.serviceModel></span></span>  
<span data-ttu-id="9443a-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="9443a-105">\<bindings></span></span>  
<span data-ttu-id="9443a-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="9443a-106">\<customBinding></span></span>  
<span data-ttu-id="9443a-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="9443a-107">\<binding></span></span>  
<span data-ttu-id="9443a-108">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="9443a-108">\<peerTransport></span></span>  
<span data-ttu-id="9443a-109">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="9443a-109">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9443a-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9443a-110">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">
  <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9443a-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9443a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9443a-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9443a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9443a-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="9443a-113">Attributes</span></span>  
  
|<span data-ttu-id="9443a-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="9443a-114">Attribute</span></span>|<span data-ttu-id="9443a-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="9443a-115">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="9443a-116">Especifica o tipo de segurança a ser aplicada.</span><span class="sxs-lookup"><span data-stu-id="9443a-116">Specifies the type of security to be applied.</span></span> <span data-ttu-id="9443a-117">O valor padrão é a mensagem.</span><span class="sxs-lookup"><span data-stu-id="9443a-117">The default value is Message.</span></span> <span data-ttu-id="9443a-118">Esse atributo é do tipo <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="9443a-118">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="9443a-119">modo de atributo</span><span class="sxs-lookup"><span data-stu-id="9443a-119">mode Attribute</span></span>  
  
|<span data-ttu-id="9443a-120">Valor</span><span class="sxs-lookup"><span data-stu-id="9443a-120">Value</span></span>|<span data-ttu-id="9443a-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="9443a-121">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="9443a-122">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="9443a-122">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="9443a-123">A proteção é fornecida usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="9443a-123">Security is provided using HTTPS.</span></span>|  
|`Message`|<span data-ttu-id="9443a-124">Segurança SOAP fornece autenticação, integridade e confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="9443a-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="9443a-125">HTTPS fornece autenticação e confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="9443a-125">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="9443a-126">As mensagens SOAP fornecem tipos de credencial avançados.</span><span class="sxs-lookup"><span data-stu-id="9443a-126">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9443a-127">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9443a-127">Child Elements</span></span>  
  
|<span data-ttu-id="9443a-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="9443a-128">Element</span></span>|<span data-ttu-id="9443a-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="9443a-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9443a-130">\<transporte ></span><span class="sxs-lookup"><span data-stu-id="9443a-130">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-peertransport.md)|<span data-ttu-id="9443a-131">Define um transporte de par para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="9443a-131">Defines a peer transport for a custom binding.</span></span> <span data-ttu-id="9443a-132">Este elemento tem um `clientCredentialType` atributo que especifica as credenciais a serem usadas ao interagir com um serviço.</span><span class="sxs-lookup"><span data-stu-id="9443a-132">This element has a `clientCredentialType` attribute that specifies the credentials to be used when interacting with a service.</span></span> <span data-ttu-id="9443a-133">Esse atributo é do tipo <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="9443a-133">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span><br /><br /> <span data-ttu-id="9443a-134">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="9443a-134">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9443a-135">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9443a-135">Parent Elements</span></span>  
  
|<span data-ttu-id="9443a-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="9443a-136">Element</span></span>|<span data-ttu-id="9443a-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="9443a-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9443a-138">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="9443a-138">\<peerTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peertransport.md)|<span data-ttu-id="9443a-139">Define um transporte de par para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="9443a-139">Defines a peer transport for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9443a-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9443a-140">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="9443a-141">Segurança de transporte</span><span class="sxs-lookup"><span data-stu-id="9443a-141">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [<span data-ttu-id="9443a-142">Transportes</span><span class="sxs-lookup"><span data-stu-id="9443a-142">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="9443a-143">Escolhendo um transporte</span><span class="sxs-lookup"><span data-stu-id="9443a-143">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="9443a-144">Associações</span><span class="sxs-lookup"><span data-stu-id="9443a-144">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="9443a-145">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="9443a-145">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="9443a-146">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="9443a-146">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="9443a-147">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="9443a-147">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
