---
title: <issuer> De <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: 690ab14ea33ba9bef29788b2eb35f86ed945ce2b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113536"
---
# <a name="issuer-of-issuedtokenparameters"></a><span data-ttu-id="752e9-102">\<emissor > de \<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="752e9-102">\<issuer> of \<issuedTokenParameters></span></span>
<span data-ttu-id="752e9-103">Especifica a Security Token Service (STS) que emite tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="752e9-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="752e9-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="752e9-104">\<system.serviceModel></span></span>  
<span data-ttu-id="752e9-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="752e9-105">\<bindings></span></span>  
<span data-ttu-id="752e9-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="752e9-106">\<customBinding></span></span>  
<span data-ttu-id="752e9-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="752e9-107">\<binding></span></span>  
<span data-ttu-id="752e9-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="752e9-108">\<security></span></span>  
<span data-ttu-id="752e9-109">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="752e9-109">\<issuedTokenParameters></span></span>  
<span data-ttu-id="752e9-110">\<issuer></span><span class="sxs-lookup"><span data-stu-id="752e9-110">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="752e9-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="752e9-111">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="752e9-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="752e9-112">Attributes and Elements</span></span>  
 <span data-ttu-id="752e9-113">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="752e9-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="752e9-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="752e9-114">Attributes</span></span>  
  
|<span data-ttu-id="752e9-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="752e9-115">Attribute</span></span>|<span data-ttu-id="752e9-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="752e9-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="752e9-117">endereço</span><span class="sxs-lookup"><span data-stu-id="752e9-117">address</span></span>|<span data-ttu-id="752e9-118">Cadeia de caracteres obrigatória.</span><span class="sxs-lookup"><span data-stu-id="752e9-118">Required string.</span></span> <span data-ttu-id="752e9-119">A URL do STS.</span><span class="sxs-lookup"><span data-stu-id="752e9-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="752e9-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="752e9-120">Child Elements</span></span>  
  
|<span data-ttu-id="752e9-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="752e9-121">Element</span></span>|<span data-ttu-id="752e9-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="752e9-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="752e9-123">\<headers></span><span class="sxs-lookup"><span data-stu-id="752e9-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="752e9-124">Uma coleção de cabeçalhos de endereço para o construtor pode criar os pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="752e9-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="752e9-125">\<identity></span><span class="sxs-lookup"><span data-stu-id="752e9-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="752e9-126">Ao usar um token emitido, especifica as configurações que permitem que o cliente autenticar o servidor.</span><span class="sxs-lookup"><span data-stu-id="752e9-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="752e9-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="752e9-127">Parent Elements</span></span>  
  
|<span data-ttu-id="752e9-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="752e9-128">Element</span></span>|<span data-ttu-id="752e9-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="752e9-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="752e9-130">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="752e9-130">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="752e9-131">Especifica o token emitido atual.</span><span class="sxs-lookup"><span data-stu-id="752e9-131">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="752e9-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="752e9-132">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="752e9-133">Identidade e autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="752e9-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="752e9-134">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="752e9-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="752e9-135">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="752e9-135">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="752e9-136">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="752e9-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="752e9-137">Associações</span><span class="sxs-lookup"><span data-stu-id="752e9-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="752e9-138">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="752e9-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="752e9-139">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="752e9-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="752e9-140">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="752e9-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="752e9-141">Como: criar uma associação personalizada utilizando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="752e9-141">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="752e9-142">Segurança de associação personalizada</span><span class="sxs-lookup"><span data-stu-id="752e9-142">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
