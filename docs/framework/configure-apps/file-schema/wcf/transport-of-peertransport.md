---
title: '&lt;transporte&gt; de &lt;peerTransport&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 787d4569416203364e04898c6adcd57fb5a7aec8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="lttransportgt-of-ltpeertransportgt"></a><span data-ttu-id="29ac0-102">&lt;transporte&gt; de &lt;peerTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="29ac0-102">&lt;transport&gt; of &lt;peerTransport&gt;</span></span>
<span data-ttu-id="29ac0-103">Especifica o tipo de transporte seguro mensagens enviadas pelos pares configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="29ac0-103">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
 <span data-ttu-id="29ac0-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="29ac0-104">\<system.serviceModel></span></span>  
<span data-ttu-id="29ac0-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="29ac0-105">\<bindings></span></span>  
<span data-ttu-id="29ac0-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="29ac0-106">\<customBinding></span></span>  
<span data-ttu-id="29ac0-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="29ac0-107">\<binding></span></span>  
<span data-ttu-id="29ac0-108">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="29ac0-108">\<peerTransport></span></span>  
<span data-ttu-id="29ac0-109">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="29ac0-109">\<security></span></span>  
<span data-ttu-id="29ac0-110">\<transporte ></span><span class="sxs-lookup"><span data-stu-id="29ac0-110">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29ac0-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="29ac0-111">Syntax</span></span>  
  
```xml  
<security>  
   <transport credentialType="Certificate/Password" />  
</security>         
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29ac0-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="29ac0-112">Attributes and Elements</span></span>  
 <span data-ttu-id="29ac0-113">As seções a seguir descrevem os elementos pai de atributos e elementos filho</span><span class="sxs-lookup"><span data-stu-id="29ac0-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29ac0-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="29ac0-114">Attributes</span></span>  
  
|<span data-ttu-id="29ac0-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="29ac0-115">Attribute</span></span>|<span data-ttu-id="29ac0-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="29ac0-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="29ac0-117">credentialType</span><span class="sxs-lookup"><span data-stu-id="29ac0-117">credentialType</span></span>|<span data-ttu-id="29ac0-118">Opcional.</span><span class="sxs-lookup"><span data-stu-id="29ac0-118">Optional.</span></span> <span data-ttu-id="29ac0-119">Especifica o tipo de credenciais usado para verificar as mensagens enviadas com o transporte de par.</span><span class="sxs-lookup"><span data-stu-id="29ac0-119">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="29ac0-120">Esse atributo é do tipo <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="29ac0-120">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="29ac0-121">credentialType atributo</span><span class="sxs-lookup"><span data-stu-id="29ac0-121">credentialType Attribute</span></span>  
  
|<span data-ttu-id="29ac0-122">Valor</span><span class="sxs-lookup"><span data-stu-id="29ac0-122">Value</span></span>|<span data-ttu-id="29ac0-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="29ac0-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="29ac0-124">certificado</span><span class="sxs-lookup"><span data-stu-id="29ac0-124">Certificate</span></span>|<span data-ttu-id="29ac0-125">Requer a autenticação do transporte de canal par X509 certificado.</span><span class="sxs-lookup"><span data-stu-id="29ac0-125">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="29ac0-126">Senha</span><span class="sxs-lookup"><span data-stu-id="29ac0-126">Password</span></span>|<span data-ttu-id="29ac0-127">A autenticação do transporte de canal par requer uma senha correta.</span><span class="sxs-lookup"><span data-stu-id="29ac0-127">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="29ac0-128">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="29ac0-128">Child Elements</span></span>  
 <span data-ttu-id="29ac0-129">Nenhum</span><span class="sxs-lookup"><span data-stu-id="29ac0-129">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="29ac0-130">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="29ac0-130">Parent Elements</span></span>  
  
|<span data-ttu-id="29ac0-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="29ac0-131">Element</span></span>|<span data-ttu-id="29ac0-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="29ac0-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="29ac0-133">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="29ac0-133">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|<span data-ttu-id="29ac0-134">Define as configurações de segurança para um transporte de par.</span><span class="sxs-lookup"><span data-stu-id="29ac0-134">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29ac0-135">Comentários</span><span class="sxs-lookup"><span data-stu-id="29ac0-135">Remarks</span></span>  
 <span data-ttu-id="29ac0-136">Esse elemento é definido somente se o atributo de modo de [ \<segurança >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md) é definido como `Transport` ou `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="29ac0-136">This element is set only if the mode attribute of [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29ac0-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29ac0-137">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>  
 <xref:System.ServiceModel.PeerTransportSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="29ac0-138">Segurança de transporte</span><span class="sxs-lookup"><span data-stu-id="29ac0-138">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [<span data-ttu-id="29ac0-139">Transportes</span><span class="sxs-lookup"><span data-stu-id="29ac0-139">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="29ac0-140">Selecionando um transporte</span><span class="sxs-lookup"><span data-stu-id="29ac0-140">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 <span data-ttu-id="29ac0-141">[Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)</span><span class="sxs-lookup"><span data-stu-id="29ac0-141">[Bindings](../../../../../docs/framework/wcf/bindings.md)</span></span>  
 [<span data-ttu-id="29ac0-142">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="29ac0-142">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="29ac0-143">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="29ac0-143">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="29ac0-144">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="29ac0-144">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
