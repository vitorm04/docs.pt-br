---
title: <issuerMetadata> de <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
ms.openlocfilehash: d9d7d41277eff1de43f717816b35fdc10d52192e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928873"
---
# <a name="issuermetadata-of-issuedtokenparameters"></a><span data-ttu-id="ce071-102">\<issuerMetadata > de \<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="ce071-102">\<issuerMetadata> of \<issuedTokenParameters></span></span>
<span data-ttu-id="ce071-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ce071-103">\<system.serviceModel></span></span>  
<span data-ttu-id="ce071-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="ce071-104">\<bindings></span></span>  
<span data-ttu-id="ce071-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="ce071-105">\<customBinding></span></span>  
<span data-ttu-id="ce071-106">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="ce071-106">\<binding></span></span>  
<span data-ttu-id="ce071-107">\<> de segurança</span><span class="sxs-lookup"><span data-stu-id="ce071-107">\<security></span></span>  
<span data-ttu-id="ce071-108">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="ce071-108">\<issuedTokenParameters></span></span>  
<span data-ttu-id="ce071-109">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="ce071-109">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce071-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ce071-110">Syntax</span></span>  
  
```xml  
<issuerMetaData address="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ce071-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ce071-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ce071-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ce071-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ce071-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="ce071-113">Attributes</span></span>  
  
|<span data-ttu-id="ce071-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="ce071-114">Attribute</span></span>|<span data-ttu-id="ce071-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="ce071-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ce071-116">endereço</span><span class="sxs-lookup"><span data-stu-id="ce071-116">address</span></span>|<span data-ttu-id="ce071-117">Necessário.</span><span class="sxs-lookup"><span data-stu-id="ce071-117">Required.</span></span> <span data-ttu-id="ce071-118">Uma cadeia de caracteres que especifica o endereço do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ce071-118">A string that specifies the address of the endpoint.</span></span> <span data-ttu-id="ce071-119">O endereço deve ser um URI absoluto.</span><span class="sxs-lookup"><span data-stu-id="ce071-119">The address must be an absolute URI.</span></span> <span data-ttu-id="ce071-120">O valor padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="ce071-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ce071-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ce071-121">Child Elements</span></span>  
  
|<span data-ttu-id="ce071-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="ce071-122">Element</span></span>|<span data-ttu-id="ce071-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="ce071-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ce071-124">\<headers></span><span class="sxs-lookup"><span data-stu-id="ce071-124">\<headers></span></span>](headers-element.md)|<span data-ttu-id="ce071-125">Uma coleção de cabeçalhos de endereço.</span><span class="sxs-lookup"><span data-stu-id="ce071-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="ce071-126">\<identity></span><span class="sxs-lookup"><span data-stu-id="ce071-126">\<identity></span></span>](identity.md)|<span data-ttu-id="ce071-127">Uma identidade que permite a autenticação de um ponto de extremidade por outros pontos de extremidades que trocam mensagens com ele.</span><span class="sxs-lookup"><span data-stu-id="ce071-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ce071-128">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ce071-128">Parent Elements</span></span>  
  
|<span data-ttu-id="ce071-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="ce071-129">Element</span></span>|<span data-ttu-id="ce071-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="ce071-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ce071-131">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="ce071-131">\<issuedTokenParameters></span></span>](issuedtokenparameters.md)|<span data-ttu-id="ce071-132">Especifica os parâmetros para um token de segurança emitido em um cenário de segurança federada.</span><span class="sxs-lookup"><span data-stu-id="ce071-132">Specifies the parameters for an security token issued in a Federated security scenario.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ce071-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ce071-133">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="ce071-134">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="ce071-134">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="ce071-135">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="ce071-135">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="ce071-136">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="ce071-136">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="ce071-137">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="ce071-137">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="ce071-138">Associações</span><span class="sxs-lookup"><span data-stu-id="ce071-138">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ce071-139">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="ce071-139">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="ce071-140">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="ce071-140">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="ce071-141">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="ce071-141">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="ce071-142">Como: Criar uma associação personalizada usando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="ce071-142">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="ce071-143">Segurança de associação personalizada</span><span class="sxs-lookup"><span data-stu-id="ce071-143">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
