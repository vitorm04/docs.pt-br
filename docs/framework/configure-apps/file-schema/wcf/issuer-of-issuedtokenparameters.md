---
title: '&lt;emissor&gt; de &lt;issuedTokenParameters&gt;'
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: 58fdd93eb4f69e48783873df26bf1c35a2a849e7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539149"
---
# <a name="ltissuergt-of-ltissuedtokenparametersgt"></a><span data-ttu-id="35969-102">&lt;emissor&gt; de &lt;issuedTokenParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="35969-102">&lt;issuer&gt; of &lt;issuedTokenParameters&gt;</span></span>
<span data-ttu-id="35969-103">Especifica a Security Token Service (STS) que emite tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="35969-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="35969-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="35969-104">\<system.serviceModel></span></span>  
<span data-ttu-id="35969-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="35969-105">\<bindings></span></span>  
<span data-ttu-id="35969-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="35969-106">\<customBinding></span></span>  
<span data-ttu-id="35969-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="35969-107">\<binding></span></span>  
<span data-ttu-id="35969-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="35969-108">\<security></span></span>  
<span data-ttu-id="35969-109">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="35969-109">\<issuedTokenParameters></span></span>  
<span data-ttu-id="35969-110">\<issuer></span><span class="sxs-lookup"><span data-stu-id="35969-110">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35969-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="35969-111">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="35969-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="35969-112">Attributes and Elements</span></span>  
 <span data-ttu-id="35969-113">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="35969-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="35969-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="35969-114">Attributes</span></span>  
  
|<span data-ttu-id="35969-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="35969-115">Attribute</span></span>|<span data-ttu-id="35969-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="35969-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="35969-117">endereço</span><span class="sxs-lookup"><span data-stu-id="35969-117">address</span></span>|<span data-ttu-id="35969-118">Cadeia de caracteres obrigatória.</span><span class="sxs-lookup"><span data-stu-id="35969-118">Required string.</span></span> <span data-ttu-id="35969-119">A URL do STS.</span><span class="sxs-lookup"><span data-stu-id="35969-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="35969-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="35969-120">Child Elements</span></span>  
  
|<span data-ttu-id="35969-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="35969-121">Element</span></span>|<span data-ttu-id="35969-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="35969-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="35969-123">\<headers></span><span class="sxs-lookup"><span data-stu-id="35969-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="35969-124">Uma coleção de cabeçalhos de endereço para o construtor pode criar os pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="35969-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="35969-125">\<identity></span><span class="sxs-lookup"><span data-stu-id="35969-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="35969-126">Ao usar um token emitido, especifica as configurações que permitem que o cliente autenticar o servidor.</span><span class="sxs-lookup"><span data-stu-id="35969-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="35969-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="35969-127">Parent Elements</span></span>  
  
|<span data-ttu-id="35969-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="35969-128">Element</span></span>|<span data-ttu-id="35969-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="35969-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="35969-130">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="35969-130">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="35969-131">Especifica o token emitido atual.</span><span class="sxs-lookup"><span data-stu-id="35969-131">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="35969-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="35969-132">See also</span></span>
- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="35969-133">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="35969-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="35969-134">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="35969-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="35969-135">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="35969-135">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="35969-136">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="35969-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="35969-137">Associações</span><span class="sxs-lookup"><span data-stu-id="35969-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="35969-138">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="35969-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="35969-139">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="35969-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="35969-140">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="35969-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="35969-141">Como: Criar uma associação personalizada utilizando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="35969-141">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="35969-142">Segurança de associação personalizada</span><span class="sxs-lookup"><span data-stu-id="35969-142">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
