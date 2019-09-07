---
title: <issuerMetadata> de <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
ms.openlocfilehash: fcdd66ecd162dff5be86a1d4ab1b196f50dbd445
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400348"
---
# <a name="issuermetadata-of-issuedtokenparameters"></a><span data-ttu-id="86d5c-102">\<issuerMetadata > de \<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="86d5c-102">\<issuerMetadata> of \<issuedTokenParameters></span></span>

<span data-ttu-id="86d5c-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="86d5c-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="86d5c-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="86d5c-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="86d5c-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="86d5c-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="86d5c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de CustomBinding**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="86d5c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="86d5c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**</span><span class="sxs-lookup"><span data-stu-id="86d5c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="86d5c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de segurança**](security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="86d5c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)</span></span>\
<span data-ttu-id="86d5c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> issuedTokenParameters**](issuedtokenparameters.md)</span><span class="sxs-lookup"><span data-stu-id="86d5c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)</span></span>\
<span data-ttu-id="86d5c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> issuerMetadata**</span><span class="sxs-lookup"><span data-stu-id="86d5c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerMetadata>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86d5c-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="86d5c-111">Syntax</span></span>  
  
```xml  
<issuerMetaData address="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="86d5c-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="86d5c-112">Attributes and Elements</span></span>  
 <span data-ttu-id="86d5c-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="86d5c-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="86d5c-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="86d5c-114">Attributes</span></span>  
  
|<span data-ttu-id="86d5c-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="86d5c-115">Attribute</span></span>|<span data-ttu-id="86d5c-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="86d5c-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="86d5c-117">endereço</span><span class="sxs-lookup"><span data-stu-id="86d5c-117">address</span></span>|<span data-ttu-id="86d5c-118">Necessário.</span><span class="sxs-lookup"><span data-stu-id="86d5c-118">Required.</span></span> <span data-ttu-id="86d5c-119">Uma cadeia de caracteres que especifica o endereço do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="86d5c-119">A string that specifies the address of the endpoint.</span></span> <span data-ttu-id="86d5c-120">O endereço deve ser um URI absoluto.</span><span class="sxs-lookup"><span data-stu-id="86d5c-120">The address must be an absolute URI.</span></span> <span data-ttu-id="86d5c-121">O valor padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="86d5c-121">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="86d5c-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="86d5c-122">Child Elements</span></span>  
  
|<span data-ttu-id="86d5c-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="86d5c-123">Element</span></span>|<span data-ttu-id="86d5c-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="86d5c-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="86d5c-125">\<headers></span><span class="sxs-lookup"><span data-stu-id="86d5c-125">\<headers></span></span>](headers-element.md)|<span data-ttu-id="86d5c-126">Uma coleção de cabeçalhos de endereço.</span><span class="sxs-lookup"><span data-stu-id="86d5c-126">A collection of address headers.</span></span>|  
|[<span data-ttu-id="86d5c-127">\<identity></span><span class="sxs-lookup"><span data-stu-id="86d5c-127">\<identity></span></span>](identity.md)|<span data-ttu-id="86d5c-128">Uma identidade que permite a autenticação de um ponto de extremidade por outros pontos de extremidades que trocam mensagens com ele.</span><span class="sxs-lookup"><span data-stu-id="86d5c-128">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="86d5c-129">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="86d5c-129">Parent Elements</span></span>  
  
|<span data-ttu-id="86d5c-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="86d5c-130">Element</span></span>|<span data-ttu-id="86d5c-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="86d5c-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="86d5c-132">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="86d5c-132">\<issuedTokenParameters></span></span>](issuedtokenparameters.md)|<span data-ttu-id="86d5c-133">Especifica os parâmetros para um token de segurança emitido em um cenário de segurança federada.</span><span class="sxs-lookup"><span data-stu-id="86d5c-133">Specifies the parameters for an security token issued in a Federated security scenario.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="86d5c-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="86d5c-134">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="86d5c-135">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="86d5c-135">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="86d5c-136">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="86d5c-136">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="86d5c-137">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="86d5c-137">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="86d5c-138">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="86d5c-138">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="86d5c-139">Associações</span><span class="sxs-lookup"><span data-stu-id="86d5c-139">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="86d5c-140">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="86d5c-140">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="86d5c-141">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="86d5c-141">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="86d5c-142">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="86d5c-142">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="86d5c-143">Como: Criar uma associação personalizada usando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="86d5c-143">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="86d5c-144">Segurança de associação personalizada</span><span class="sxs-lookup"><span data-stu-id="86d5c-144">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
