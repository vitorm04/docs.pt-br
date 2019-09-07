---
title: <security> de <peerTransport>
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: 270ca844f586be256b6483653c868d1cc4396657
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399777"
---
# <a name="security-of-peertransport"></a><span data-ttu-id="2d198-102">\<> de segurança \<do peerTransport ></span><span class="sxs-lookup"><span data-stu-id="2d198-102">\<security> of \<peerTransport></span></span>
<span data-ttu-id="2d198-103">Contém as definições de segurança associadas a um canal de pares, incluindo o tipo de autenticação utilizada e a segurança usada para o transporte de mensagens.</span><span class="sxs-lookup"><span data-stu-id="2d198-103">Contains the security settings associated with a peer channel, including the type of authentication used and the security used for the message transport.</span></span>  
  
<span data-ttu-id="2d198-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2d198-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2d198-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="2d198-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="2d198-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="2d198-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="2d198-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de CustomBinding**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="2d198-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="2d198-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**</span><span class="sxs-lookup"><span data-stu-id="2d198-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="2d198-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> peerTransport**](peertransport.md)</span><span class="sxs-lookup"><span data-stu-id="2d198-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peerTransport>**](peertransport.md)</span></span>\
<span data-ttu-id="2d198-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de segurança**</span><span class="sxs-lookup"><span data-stu-id="2d198-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d198-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2d198-111">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">
  <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2d198-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2d198-112">Attributes and Elements</span></span>  
 <span data-ttu-id="2d198-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2d198-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2d198-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="2d198-114">Attributes</span></span>  
  
|<span data-ttu-id="2d198-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="2d198-115">Attribute</span></span>|<span data-ttu-id="2d198-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="2d198-116">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="2d198-117">Especifica o tipo de segurança a ser aplicado.</span><span class="sxs-lookup"><span data-stu-id="2d198-117">Specifies the type of security to be applied.</span></span> <span data-ttu-id="2d198-118">O valor padrão é Message.</span><span class="sxs-lookup"><span data-stu-id="2d198-118">The default value is Message.</span></span> <span data-ttu-id="2d198-119">Esse atributo é do tipo <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="2d198-119">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="2d198-120">Atributo de modo</span><span class="sxs-lookup"><span data-stu-id="2d198-120">mode Attribute</span></span>  
  
|<span data-ttu-id="2d198-121">Valor</span><span class="sxs-lookup"><span data-stu-id="2d198-121">Value</span></span>|<span data-ttu-id="2d198-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="2d198-122">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="2d198-123">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="2d198-123">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="2d198-124">A proteção é fornecida usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2d198-124">Security is provided using HTTPS.</span></span>|  
|`Message`|<span data-ttu-id="2d198-125">A segurança SOAP fornece autenticação, integridade e confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="2d198-125">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="2d198-126">O HTTPS fornece autenticação e confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="2d198-126">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="2d198-127">As mensagens SOAP fornecem tipos de credenciais avançados.</span><span class="sxs-lookup"><span data-stu-id="2d198-127">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2d198-128">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2d198-128">Child Elements</span></span>  
  
|<span data-ttu-id="2d198-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="2d198-129">Element</span></span>|<span data-ttu-id="2d198-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="2d198-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2d198-131">\<> de transporte</span><span class="sxs-lookup"><span data-stu-id="2d198-131">\<transport></span></span>](transport-of-peertransport.md)|<span data-ttu-id="2d198-132">Define um transporte de mesmo nível para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="2d198-132">Defines a peer transport for a custom binding.</span></span> <span data-ttu-id="2d198-133">Esse elemento tem um `clientCredentialType` atributo que especifica as credenciais a serem usadas ao interagir com um serviço.</span><span class="sxs-lookup"><span data-stu-id="2d198-133">This element has a `clientCredentialType` attribute that specifies the credentials to be used when interacting with a service.</span></span> <span data-ttu-id="2d198-134">Esse atributo é do tipo <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="2d198-134">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span><br /><br /> <span data-ttu-id="2d198-135">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="2d198-135">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2d198-136">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2d198-136">Parent Elements</span></span>  
  
|<span data-ttu-id="2d198-137">Elemento</span><span class="sxs-lookup"><span data-stu-id="2d198-137">Element</span></span>|<span data-ttu-id="2d198-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="2d198-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2d198-139">\<peerTransport></span><span class="sxs-lookup"><span data-stu-id="2d198-139">\<peerTransport></span></span>](peertransport.md)|<span data-ttu-id="2d198-140">Define um transporte de mesmo nível para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="2d198-140">Defines a peer transport for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2d198-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2d198-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="2d198-142">Segurança de transporte</span><span class="sxs-lookup"><span data-stu-id="2d198-142">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="2d198-143">Transportes</span><span class="sxs-lookup"><span data-stu-id="2d198-143">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="2d198-144">Escolhendo um transporte</span><span class="sxs-lookup"><span data-stu-id="2d198-144">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="2d198-145">Associações</span><span class="sxs-lookup"><span data-stu-id="2d198-145">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="2d198-146">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="2d198-146">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="2d198-147">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="2d198-147">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="2d198-148">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="2d198-148">\<customBinding></span></span>](custombinding.md)
