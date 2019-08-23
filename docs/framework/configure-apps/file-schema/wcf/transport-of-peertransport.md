---
title: <transport> de <peerTransport>
ms.date: 03/30/2017
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
ms.openlocfilehash: 5dbc55db25c0c49d72ec2cd8dd1041a3f8705d8e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940641"
---
# <a name="transport-of-peertransport"></a><span data-ttu-id="7f777-102">\<> de transporte \<do peerTransport ></span><span class="sxs-lookup"><span data-stu-id="7f777-102">\<transport> of \<peerTransport></span></span>
<span data-ttu-id="7f777-103">Especifica o tipo de transporte para mensagens protegidas enviadas por pares configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="7f777-103">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
 <span data-ttu-id="7f777-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7f777-104">\<system.serviceModel></span></span>  
<span data-ttu-id="7f777-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="7f777-105">\<bindings></span></span>  
<span data-ttu-id="7f777-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="7f777-106">\<customBinding></span></span>  
<span data-ttu-id="7f777-107">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="7f777-107">\<binding></span></span>  
<span data-ttu-id="7f777-108">\<> peerTransport</span><span class="sxs-lookup"><span data-stu-id="7f777-108">\<peerTransport></span></span>  
<span data-ttu-id="7f777-109">\<> de segurança</span><span class="sxs-lookup"><span data-stu-id="7f777-109">\<security></span></span>  
<span data-ttu-id="7f777-110">\<> de transporte</span><span class="sxs-lookup"><span data-stu-id="7f777-110">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f777-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7f777-111">Syntax</span></span>  
  
```xml  
<security>
  <transport credentialType="Certificate/Password" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f777-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7f777-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7f777-113">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="7f777-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f777-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="7f777-114">Attributes</span></span>  
  
|<span data-ttu-id="7f777-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="7f777-115">Attribute</span></span>|<span data-ttu-id="7f777-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="7f777-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7f777-117">CredentialType</span><span class="sxs-lookup"><span data-stu-id="7f777-117">credentialType</span></span>|<span data-ttu-id="7f777-118">Opcional.</span><span class="sxs-lookup"><span data-stu-id="7f777-118">Optional.</span></span> <span data-ttu-id="7f777-119">Especifica o tipo de credenciais usadas para verificar as mensagens enviadas com o transporte de mesmo nível.</span><span class="sxs-lookup"><span data-stu-id="7f777-119">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="7f777-120">Esse atributo é do tipo <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="7f777-120">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="7f777-121">Atributo CredentialType</span><span class="sxs-lookup"><span data-stu-id="7f777-121">credentialType Attribute</span></span>  
  
|<span data-ttu-id="7f777-122">Valor</span><span class="sxs-lookup"><span data-stu-id="7f777-122">Value</span></span>|<span data-ttu-id="7f777-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="7f777-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7f777-124">Certificate</span><span class="sxs-lookup"><span data-stu-id="7f777-124">Certificate</span></span>|<span data-ttu-id="7f777-125">A autenticação do transporte de canal par requer um certificado X509.</span><span class="sxs-lookup"><span data-stu-id="7f777-125">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="7f777-126">Senha</span><span class="sxs-lookup"><span data-stu-id="7f777-126">Password</span></span>|<span data-ttu-id="7f777-127">A autenticação do transporte de canal par requer uma senha correta.</span><span class="sxs-lookup"><span data-stu-id="7f777-127">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7f777-128">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7f777-128">Child Elements</span></span>  
 <span data-ttu-id="7f777-129">Nenhum</span><span class="sxs-lookup"><span data-stu-id="7f777-129">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7f777-130">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7f777-130">Parent Elements</span></span>  
  
|<span data-ttu-id="7f777-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="7f777-131">Element</span></span>|<span data-ttu-id="7f777-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="7f777-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7f777-133">\<security></span><span class="sxs-lookup"><span data-stu-id="7f777-133">\<security></span></span>](security-of-peertransport.md)|<span data-ttu-id="7f777-134">Define as configurações de segurança para um transporte de mesmo nível.</span><span class="sxs-lookup"><span data-stu-id="7f777-134">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f777-135">Comentários</span><span class="sxs-lookup"><span data-stu-id="7f777-135">Remarks</span></span>  
 <span data-ttu-id="7f777-136">Esse elemento será definido somente se o atributo mode do [ \<> de segurança](security-of-peertransport.md) for definido `Transport` como `TransportWithMessageCredential`ou.</span><span class="sxs-lookup"><span data-stu-id="7f777-136">This element is set only if the mode attribute of [\<security>](security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f777-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7f777-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="7f777-138">Segurança de transporte</span><span class="sxs-lookup"><span data-stu-id="7f777-138">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="7f777-139">Transportes</span><span class="sxs-lookup"><span data-stu-id="7f777-139">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="7f777-140">Escolhendo um transporte</span><span class="sxs-lookup"><span data-stu-id="7f777-140">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="7f777-141">Associações</span><span class="sxs-lookup"><span data-stu-id="7f777-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7f777-142">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="7f777-142">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="7f777-143">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="7f777-143">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="7f777-144">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="7f777-144">\<customBinding></span></span>](custombinding.md)
