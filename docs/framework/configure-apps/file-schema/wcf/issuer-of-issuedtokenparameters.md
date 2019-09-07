---
title: <issuer> de <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: bdd5ad45984fae7b39defe82c4af75845dfda1b6
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397940"
---
# <a name="issuer-of-issuedtokenparameters"></a><span data-ttu-id="5e53a-102">\<> do emissor do \<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="5e53a-102">\<issuer> of \<issuedTokenParameters></span></span>
<span data-ttu-id="5e53a-103">Especifica o serviço de token de segurança (STS) que emite tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="5e53a-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
<span data-ttu-id="5e53a-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5e53a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5e53a-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5e53a-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5e53a-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="5e53a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="5e53a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de CustomBinding**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="5e53a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="5e53a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**</span><span class="sxs-lookup"><span data-stu-id="5e53a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="5e53a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de segurança**](security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="5e53a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)</span></span>\
<span data-ttu-id="5e53a-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> issuedTokenParameters**](issuedtokenparameters.md)</span><span class="sxs-lookup"><span data-stu-id="5e53a-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)</span></span>\
<span data-ttu-id="5e53a-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> do emissor**</span><span class="sxs-lookup"><span data-stu-id="5e53a-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e53a-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5e53a-112">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5e53a-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5e53a-113">Attributes and Elements</span></span>  
 <span data-ttu-id="5e53a-114">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="5e53a-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5e53a-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="5e53a-115">Attributes</span></span>  
  
|<span data-ttu-id="5e53a-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="5e53a-116">Attribute</span></span>|<span data-ttu-id="5e53a-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e53a-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5e53a-118">endereço</span><span class="sxs-lookup"><span data-stu-id="5e53a-118">address</span></span>|<span data-ttu-id="5e53a-119">Cadeia de caracteres obrigatória.</span><span class="sxs-lookup"><span data-stu-id="5e53a-119">Required string.</span></span> <span data-ttu-id="5e53a-120">A URL do STS.</span><span class="sxs-lookup"><span data-stu-id="5e53a-120">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5e53a-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5e53a-121">Child Elements</span></span>  
  
|<span data-ttu-id="5e53a-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="5e53a-122">Element</span></span>|<span data-ttu-id="5e53a-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e53a-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e53a-124">\<headers></span><span class="sxs-lookup"><span data-stu-id="5e53a-124">\<headers></span></span>](headers-element.md)|<span data-ttu-id="5e53a-125">Uma coleção de cabeçalhos de endereço para os pontos de extremidade que o construtor pode criar.</span><span class="sxs-lookup"><span data-stu-id="5e53a-125">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="5e53a-126">\<identity></span><span class="sxs-lookup"><span data-stu-id="5e53a-126">\<identity></span></span>](identity.md)|<span data-ttu-id="5e53a-127">Ao usar um token emitido, especifica as configurações que permitem que o cliente autentique o servidor.</span><span class="sxs-lookup"><span data-stu-id="5e53a-127">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5e53a-128">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5e53a-128">Parent Elements</span></span>  
  
|<span data-ttu-id="5e53a-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="5e53a-129">Element</span></span>|<span data-ttu-id="5e53a-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e53a-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e53a-131">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="5e53a-131">\<issuedTokenParameters></span></span>](issuedtokenparameters.md)|<span data-ttu-id="5e53a-132">Especifica o token emitido atual.</span><span class="sxs-lookup"><span data-stu-id="5e53a-132">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5e53a-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e53a-133">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="5e53a-134">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="5e53a-134">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="5e53a-135">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="5e53a-135">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="5e53a-136">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="5e53a-136">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="5e53a-137">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="5e53a-137">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="5e53a-138">Associações</span><span class="sxs-lookup"><span data-stu-id="5e53a-138">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5e53a-139">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="5e53a-139">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="5e53a-140">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="5e53a-140">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="5e53a-141">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="5e53a-141">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="5e53a-142">Como: Criar uma associação personalizada usando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="5e53a-142">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="5e53a-143">Segurança de associação personalizada</span><span class="sxs-lookup"><span data-stu-id="5e53a-143">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
