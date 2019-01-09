---
title: '&lt;issuerMetadata&gt; de &lt;issuedTokenParameters&gt;'
ms.date: 03/30/2017
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
ms.openlocfilehash: 76956c54739219bbde78f378a12d59563ab785c4
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148741"
---
# <a name="ltissuermetadatagt-of-ltissuedtokenparametersgt"></a><span data-ttu-id="a6fcd-102">&lt;issuerMetadata&gt; de &lt;issuedTokenParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="a6fcd-102">&lt;issuerMetadata&gt; of &lt;issuedTokenParameters&gt;</span></span>
<span data-ttu-id="a6fcd-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a6fcd-103">\<system.serviceModel></span></span>  
<span data-ttu-id="a6fcd-104">\<associações ></span><span class="sxs-lookup"><span data-stu-id="a6fcd-104">\<bindings></span></span>  
<span data-ttu-id="a6fcd-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="a6fcd-105">\<customBinding></span></span>  
<span data-ttu-id="a6fcd-106">\<associação ></span><span class="sxs-lookup"><span data-stu-id="a6fcd-106">\<binding></span></span>  
<span data-ttu-id="a6fcd-107">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="a6fcd-107">\<security></span></span>  
<span data-ttu-id="a6fcd-108">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="a6fcd-108">\<issuedTokenParameters></span></span>  
<span data-ttu-id="a6fcd-109">\<issuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="a6fcd-109">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6fcd-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a6fcd-110">Syntax</span></span>  
  
```xml  
<issuerMetaData address="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6fcd-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a6fcd-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a6fcd-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a6fcd-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6fcd-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="a6fcd-113">Attributes</span></span>  
  
|<span data-ttu-id="a6fcd-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="a6fcd-114">Attribute</span></span>|<span data-ttu-id="a6fcd-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="a6fcd-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a6fcd-116">endereço</span><span class="sxs-lookup"><span data-stu-id="a6fcd-116">address</span></span>|<span data-ttu-id="a6fcd-117">Necessário.</span><span class="sxs-lookup"><span data-stu-id="a6fcd-117">Required.</span></span> <span data-ttu-id="a6fcd-118">Uma cadeia de caracteres que especifica o endereço do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a6fcd-118">A string that specifies the address of the endpoint.</span></span> <span data-ttu-id="a6fcd-119">O endereço deve ser um URI absoluto.</span><span class="sxs-lookup"><span data-stu-id="a6fcd-119">The address must be an absolute URI.</span></span> <span data-ttu-id="a6fcd-120">O valor padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="a6fcd-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a6fcd-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a6fcd-121">Child Elements</span></span>  
  
|<span data-ttu-id="a6fcd-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="a6fcd-122">Element</span></span>|<span data-ttu-id="a6fcd-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="a6fcd-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6fcd-124">\<cabeçalhos ></span><span class="sxs-lookup"><span data-stu-id="a6fcd-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="a6fcd-125">Uma coleção de cabeçalhos de endereço.</span><span class="sxs-lookup"><span data-stu-id="a6fcd-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="a6fcd-126">\<identity></span><span class="sxs-lookup"><span data-stu-id="a6fcd-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="a6fcd-127">Uma identidade que permite a autenticação de um ponto de extremidade por outros pontos de extremidade trocando mensagens com ele.</span><span class="sxs-lookup"><span data-stu-id="a6fcd-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a6fcd-128">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a6fcd-128">Parent Elements</span></span>  
  
|<span data-ttu-id="a6fcd-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="a6fcd-129">Element</span></span>|<span data-ttu-id="a6fcd-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="a6fcd-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6fcd-131">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="a6fcd-131">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="a6fcd-132">Especifica os parâmetros para um token de segurança emitido em um cenário de segurança federada.</span><span class="sxs-lookup"><span data-stu-id="a6fcd-132">Specifies the parameters for an security token issued in a Federated security scenario.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a6fcd-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6fcd-133">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="a6fcd-134">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="a6fcd-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="a6fcd-135">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="a6fcd-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="a6fcd-136">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="a6fcd-136">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="a6fcd-137">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="a6fcd-137">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="a6fcd-138">Associações</span><span class="sxs-lookup"><span data-stu-id="a6fcd-138">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a6fcd-139">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="a6fcd-139">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="a6fcd-140">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="a6fcd-140">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="a6fcd-141">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="a6fcd-141">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="a6fcd-142">Como: Criar uma associação personalizada utilizando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="a6fcd-142">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="a6fcd-143">Segurança de associação personalizada</span><span class="sxs-lookup"><span data-stu-id="a6fcd-143">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
