---
title: '&lt;emissor&gt; de &lt;issuedTokenParameters&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b31214f5552283c40cdc93e6e72a374bbfef9997
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltissuergt-of-ltissuedtokenparametersgt"></a><span data-ttu-id="86a4a-102">&lt;emissor&gt; de &lt;issuedTokenParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="86a4a-102">&lt;issuer&gt; of &lt;issuedTokenParameters&gt;</span></span>
<span data-ttu-id="86a4a-103">Especifica o Token de segurança Service (STS) que emite tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="86a4a-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="86a4a-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="86a4a-104">\<system.serviceModel></span></span>  
<span data-ttu-id="86a4a-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="86a4a-105">\<bindings></span></span>  
<span data-ttu-id="86a4a-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="86a4a-106">\<customBinding></span></span>  
<span data-ttu-id="86a4a-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="86a4a-107">\<binding></span></span>  
<span data-ttu-id="86a4a-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="86a4a-108">\<security></span></span>  
<span data-ttu-id="86a4a-109">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="86a4a-109">\<issuedTokenParameters></span></span>  
<span data-ttu-id="86a4a-110">\<emissor ></span><span class="sxs-lookup"><span data-stu-id="86a4a-110">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86a4a-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="86a4a-111">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="86a4a-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="86a4a-112">Attributes and Elements</span></span>  
 <span data-ttu-id="86a4a-113">As seções a seguir descrevem os elementos pai de atributos e elementos filho</span><span class="sxs-lookup"><span data-stu-id="86a4a-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="86a4a-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="86a4a-114">Attributes</span></span>  
  
|<span data-ttu-id="86a4a-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="86a4a-115">Attribute</span></span>|<span data-ttu-id="86a4a-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="86a4a-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="86a4a-117">endereço</span><span class="sxs-lookup"><span data-stu-id="86a4a-117">address</span></span>|<span data-ttu-id="86a4a-118">Cadeia de caracteres obrigatória.</span><span class="sxs-lookup"><span data-stu-id="86a4a-118">Required string.</span></span> <span data-ttu-id="86a4a-119">A URL do STS.</span><span class="sxs-lookup"><span data-stu-id="86a4a-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="86a4a-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="86a4a-120">Child Elements</span></span>  
  
|<span data-ttu-id="86a4a-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="86a4a-121">Element</span></span>|<span data-ttu-id="86a4a-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="86a4a-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="86a4a-123">\<cabeçalhos ></span><span class="sxs-lookup"><span data-stu-id="86a4a-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="86a4a-124">Uma coleção de cabeçalhos de endereço para o construtor pode criar os pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="86a4a-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="86a4a-125">\<identidade ></span><span class="sxs-lookup"><span data-stu-id="86a4a-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="86a4a-126">Ao usar um token emitido, especifica configurações que permitem que o cliente autenticar o servidor.</span><span class="sxs-lookup"><span data-stu-id="86a4a-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="86a4a-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="86a4a-127">Parent Elements</span></span>  
  
|<span data-ttu-id="86a4a-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="86a4a-128">Element</span></span>|<span data-ttu-id="86a4a-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="86a4a-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="86a4a-130">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="86a4a-130">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="86a4a-131">Especifica o token emitido atual.</span><span class="sxs-lookup"><span data-stu-id="86a4a-131">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="86a4a-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="86a4a-132">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="86a4a-133">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="86a4a-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="86a4a-134">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="86a4a-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="86a4a-135">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="86a4a-135">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="86a4a-136">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="86a4a-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="86a4a-137">Associações</span><span class="sxs-lookup"><span data-stu-id="86a4a-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="86a4a-138">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="86a4a-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="86a4a-139">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="86a4a-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="86a4a-140">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="86a4a-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="86a4a-141">Como criar uma associação personalizada utilizando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="86a4a-141">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="86a4a-142">Segurança de associação personalizada</span><span class="sxs-lookup"><span data-stu-id="86a4a-142">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
