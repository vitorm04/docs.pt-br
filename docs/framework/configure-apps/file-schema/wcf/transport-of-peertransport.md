---
title: <transport> De <peerTransport>
ms.date: 03/30/2017
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
ms.openlocfilehash: 3dbeda5d418c30f378515fa83979eaca289370f9
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55284005"
---
# <a name="transport-of-peertransport"></a><span data-ttu-id="6e27a-102">\<transporte > de \<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="6e27a-102">\<transport> of \<peerTransport></span></span>
<span data-ttu-id="6e27a-103">Especifica o tipo de transporte para mensagens protegidas enviadas pelos pares configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="6e27a-103">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
 <span data-ttu-id="6e27a-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="6e27a-104">\<system.serviceModel></span></span>  
<span data-ttu-id="6e27a-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="6e27a-105">\<bindings></span></span>  
<span data-ttu-id="6e27a-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="6e27a-106">\<customBinding></span></span>  
<span data-ttu-id="6e27a-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="6e27a-107">\<binding></span></span>  
<span data-ttu-id="6e27a-108">\<peerTransport></span><span class="sxs-lookup"><span data-stu-id="6e27a-108">\<peerTransport></span></span>  
<span data-ttu-id="6e27a-109">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="6e27a-109">\<security></span></span>  
<span data-ttu-id="6e27a-110">\<transporte ></span><span class="sxs-lookup"><span data-stu-id="6e27a-110">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e27a-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6e27a-111">Syntax</span></span>  
  
```xml  
<security>
  <transport credentialType="Certificate/Password" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6e27a-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6e27a-112">Attributes and Elements</span></span>  
 <span data-ttu-id="6e27a-113">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="6e27a-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6e27a-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="6e27a-114">Attributes</span></span>  
  
|<span data-ttu-id="6e27a-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="6e27a-115">Attribute</span></span>|<span data-ttu-id="6e27a-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e27a-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6e27a-117">credentialType</span><span class="sxs-lookup"><span data-stu-id="6e27a-117">credentialType</span></span>|<span data-ttu-id="6e27a-118">Opcional.</span><span class="sxs-lookup"><span data-stu-id="6e27a-118">Optional.</span></span> <span data-ttu-id="6e27a-119">Especifica o tipo de credenciais usado para verificar as mensagens enviadas com o transporte de par.</span><span class="sxs-lookup"><span data-stu-id="6e27a-119">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="6e27a-120">Esse atributo é do tipo <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="6e27a-120">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="6e27a-121">credentialType atributo</span><span class="sxs-lookup"><span data-stu-id="6e27a-121">credentialType Attribute</span></span>  
  
|<span data-ttu-id="6e27a-122">Valor</span><span class="sxs-lookup"><span data-stu-id="6e27a-122">Value</span></span>|<span data-ttu-id="6e27a-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e27a-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6e27a-124">Certificado</span><span class="sxs-lookup"><span data-stu-id="6e27a-124">Certificate</span></span>|<span data-ttu-id="6e27a-125">A autenticação do transporte de canal par requer um certificado X509.</span><span class="sxs-lookup"><span data-stu-id="6e27a-125">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="6e27a-126">Senha</span><span class="sxs-lookup"><span data-stu-id="6e27a-126">Password</span></span>|<span data-ttu-id="6e27a-127">A autenticação do transporte de canal par requer uma senha correta.</span><span class="sxs-lookup"><span data-stu-id="6e27a-127">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6e27a-128">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6e27a-128">Child Elements</span></span>  
 <span data-ttu-id="6e27a-129">Nenhum</span><span class="sxs-lookup"><span data-stu-id="6e27a-129">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6e27a-130">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6e27a-130">Parent Elements</span></span>  
  
|<span data-ttu-id="6e27a-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="6e27a-131">Element</span></span>|<span data-ttu-id="6e27a-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e27a-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6e27a-133">\<security></span><span class="sxs-lookup"><span data-stu-id="6e27a-133">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|<span data-ttu-id="6e27a-134">Define as configurações de segurança para um transporte de par.</span><span class="sxs-lookup"><span data-stu-id="6e27a-134">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e27a-135">Comentários</span><span class="sxs-lookup"><span data-stu-id="6e27a-135">Remarks</span></span>  
 <span data-ttu-id="6e27a-136">Esse elemento será definido somente se o atributo do modo de [ \<segurança >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md) é definido como `Transport` ou `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="6e27a-136">This element is set only if the mode attribute of [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e27a-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6e27a-137">See also</span></span>
- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="6e27a-138">Segurança de transporte</span><span class="sxs-lookup"><span data-stu-id="6e27a-138">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)
- [<span data-ttu-id="6e27a-139">Transportes</span><span class="sxs-lookup"><span data-stu-id="6e27a-139">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="6e27a-140">Escolhendo um transporte</span><span class="sxs-lookup"><span data-stu-id="6e27a-140">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="6e27a-141">Associações</span><span class="sxs-lookup"><span data-stu-id="6e27a-141">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="6e27a-142">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="6e27a-142">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="6e27a-143">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="6e27a-143">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="6e27a-144">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="6e27a-144">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
