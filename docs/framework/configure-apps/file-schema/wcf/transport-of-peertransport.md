---
title: '&lt;transporte&gt; de &lt;peerTransport&gt;'
ms.date: 03/30/2017
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
ms.openlocfilehash: d02bb1cb4c20ab7dc482001ea7ce21180394eee7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716577"
---
# <a name="lttransportgt-of-ltpeertransportgt"></a><span data-ttu-id="7bf2d-102">&lt;transporte&gt; de &lt;peerTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="7bf2d-102">&lt;transport&gt; of &lt;peerTransport&gt;</span></span>
<span data-ttu-id="7bf2d-103">Especifica o tipo de transporte para mensagens protegidas enviadas pelos pares configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="7bf2d-103">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
 <span data-ttu-id="7bf2d-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7bf2d-104">\<system.serviceModel></span></span>  
<span data-ttu-id="7bf2d-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="7bf2d-105">\<bindings></span></span>  
<span data-ttu-id="7bf2d-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="7bf2d-106">\<customBinding></span></span>  
<span data-ttu-id="7bf2d-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="7bf2d-107">\<binding></span></span>  
<span data-ttu-id="7bf2d-108">\<peerTransport></span><span class="sxs-lookup"><span data-stu-id="7bf2d-108">\<peerTransport></span></span>  
<span data-ttu-id="7bf2d-109">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="7bf2d-109">\<security></span></span>  
<span data-ttu-id="7bf2d-110">\<transporte ></span><span class="sxs-lookup"><span data-stu-id="7bf2d-110">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bf2d-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7bf2d-111">Syntax</span></span>  
  
```xml  
<security>
  <transport credentialType="Certificate/Password" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7bf2d-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7bf2d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7bf2d-113">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="7bf2d-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7bf2d-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="7bf2d-114">Attributes</span></span>  
  
|<span data-ttu-id="7bf2d-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="7bf2d-115">Attribute</span></span>|<span data-ttu-id="7bf2d-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="7bf2d-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7bf2d-117">credentialType</span><span class="sxs-lookup"><span data-stu-id="7bf2d-117">credentialType</span></span>|<span data-ttu-id="7bf2d-118">Opcional.</span><span class="sxs-lookup"><span data-stu-id="7bf2d-118">Optional.</span></span> <span data-ttu-id="7bf2d-119">Especifica o tipo de credenciais usado para verificar as mensagens enviadas com o transporte de par.</span><span class="sxs-lookup"><span data-stu-id="7bf2d-119">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="7bf2d-120">Esse atributo é do tipo <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="7bf2d-120">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="7bf2d-121">credentialType atributo</span><span class="sxs-lookup"><span data-stu-id="7bf2d-121">credentialType Attribute</span></span>  
  
|<span data-ttu-id="7bf2d-122">Valor</span><span class="sxs-lookup"><span data-stu-id="7bf2d-122">Value</span></span>|<span data-ttu-id="7bf2d-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="7bf2d-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7bf2d-124">Certificado</span><span class="sxs-lookup"><span data-stu-id="7bf2d-124">Certificate</span></span>|<span data-ttu-id="7bf2d-125">A autenticação do transporte de canal par requer um certificado X509.</span><span class="sxs-lookup"><span data-stu-id="7bf2d-125">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="7bf2d-126">Senha</span><span class="sxs-lookup"><span data-stu-id="7bf2d-126">Password</span></span>|<span data-ttu-id="7bf2d-127">A autenticação do transporte de canal par requer uma senha correta.</span><span class="sxs-lookup"><span data-stu-id="7bf2d-127">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7bf2d-128">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7bf2d-128">Child Elements</span></span>  
 <span data-ttu-id="7bf2d-129">Nenhum</span><span class="sxs-lookup"><span data-stu-id="7bf2d-129">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7bf2d-130">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7bf2d-130">Parent Elements</span></span>  
  
|<span data-ttu-id="7bf2d-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="7bf2d-131">Element</span></span>|<span data-ttu-id="7bf2d-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="7bf2d-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7bf2d-133">\<security></span><span class="sxs-lookup"><span data-stu-id="7bf2d-133">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|<span data-ttu-id="7bf2d-134">Define as configurações de segurança para um transporte de par.</span><span class="sxs-lookup"><span data-stu-id="7bf2d-134">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7bf2d-135">Comentários</span><span class="sxs-lookup"><span data-stu-id="7bf2d-135">Remarks</span></span>  
 <span data-ttu-id="7bf2d-136">Esse elemento será definido somente se o atributo do modo de [ \<segurança >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md) é definido como `Transport` ou `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="7bf2d-136">This element is set only if the mode attribute of [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bf2d-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7bf2d-137">See also</span></span>
- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="7bf2d-138">Segurança de transporte</span><span class="sxs-lookup"><span data-stu-id="7bf2d-138">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)
- [<span data-ttu-id="7bf2d-139">Transportes</span><span class="sxs-lookup"><span data-stu-id="7bf2d-139">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="7bf2d-140">Escolhendo um transporte</span><span class="sxs-lookup"><span data-stu-id="7bf2d-140">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="7bf2d-141">Associações</span><span class="sxs-lookup"><span data-stu-id="7bf2d-141">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="7bf2d-142">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="7bf2d-142">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="7bf2d-143">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="7bf2d-143">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="7bf2d-144">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="7bf2d-144">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
