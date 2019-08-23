---
title: <issuer> de <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: 77ed9534ce872e805a6a6ea2c21a38710e6bc0fe
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925260"
---
# <a name="issuer-of-issuedtokenparameters"></a><span data-ttu-id="7c788-102">\<> do emissor do \<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="7c788-102">\<issuer> of \<issuedTokenParameters></span></span>
<span data-ttu-id="7c788-103">Especifica o serviço de token de segurança (STS) que emite tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="7c788-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="7c788-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7c788-104">\<system.serviceModel></span></span>  
<span data-ttu-id="7c788-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="7c788-105">\<bindings></span></span>  
<span data-ttu-id="7c788-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="7c788-106">\<customBinding></span></span>  
<span data-ttu-id="7c788-107">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="7c788-107">\<binding></span></span>  
<span data-ttu-id="7c788-108">\<> de segurança</span><span class="sxs-lookup"><span data-stu-id="7c788-108">\<security></span></span>  
<span data-ttu-id="7c788-109">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="7c788-109">\<issuedTokenParameters></span></span>  
<span data-ttu-id="7c788-110">\<issuer></span><span class="sxs-lookup"><span data-stu-id="7c788-110">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c788-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7c788-111">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7c788-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7c788-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7c788-113">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="7c788-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7c788-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="7c788-114">Attributes</span></span>  
  
|<span data-ttu-id="7c788-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="7c788-115">Attribute</span></span>|<span data-ttu-id="7c788-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="7c788-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7c788-117">endereço</span><span class="sxs-lookup"><span data-stu-id="7c788-117">address</span></span>|<span data-ttu-id="7c788-118">Cadeia de caracteres obrigatória.</span><span class="sxs-lookup"><span data-stu-id="7c788-118">Required string.</span></span> <span data-ttu-id="7c788-119">A URL do STS.</span><span class="sxs-lookup"><span data-stu-id="7c788-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7c788-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7c788-120">Child Elements</span></span>  
  
|<span data-ttu-id="7c788-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="7c788-121">Element</span></span>|<span data-ttu-id="7c788-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="7c788-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c788-123">\<headers></span><span class="sxs-lookup"><span data-stu-id="7c788-123">\<headers></span></span>](headers-element.md)|<span data-ttu-id="7c788-124">Uma coleção de cabeçalhos de endereço para os pontos de extremidade que o construtor pode criar.</span><span class="sxs-lookup"><span data-stu-id="7c788-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="7c788-125">\<identity></span><span class="sxs-lookup"><span data-stu-id="7c788-125">\<identity></span></span>](identity.md)|<span data-ttu-id="7c788-126">Ao usar um token emitido, especifica as configurações que permitem que o cliente autentique o servidor.</span><span class="sxs-lookup"><span data-stu-id="7c788-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7c788-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7c788-127">Parent Elements</span></span>  
  
|<span data-ttu-id="7c788-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="7c788-128">Element</span></span>|<span data-ttu-id="7c788-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="7c788-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c788-130">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="7c788-130">\<issuedTokenParameters></span></span>](issuedtokenparameters.md)|<span data-ttu-id="7c788-131">Especifica o token emitido atual.</span><span class="sxs-lookup"><span data-stu-id="7c788-131">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7c788-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7c788-132">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="7c788-133">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="7c788-133">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="7c788-134">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="7c788-134">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="7c788-135">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="7c788-135">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="7c788-136">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="7c788-136">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="7c788-137">Associações</span><span class="sxs-lookup"><span data-stu-id="7c788-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7c788-138">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="7c788-138">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="7c788-139">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="7c788-139">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="7c788-140">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="7c788-140">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="7c788-141">Como: Criar uma associação personalizada usando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="7c788-141">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="7c788-142">Segurança de associação personalizada</span><span class="sxs-lookup"><span data-stu-id="7c788-142">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
