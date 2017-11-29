---
title: '&lt;issuerMetadata&gt; de &lt;issuedTokenParameters&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9e8df1ffb74c59bfed2b9fa2f1e87e7669fe3ad9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltissuermetadatagt-of-ltissuedtokenparametersgt"></a><span data-ttu-id="c6ad6-102">&lt;issuerMetadata&gt; de &lt;issuedTokenParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="c6ad6-102">&lt;issuerMetadata&gt; of &lt;issuedTokenParameters&gt;</span></span>
<span data-ttu-id="c6ad6-103">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c6ad6-103">\<system.serviceModel></span></span>  
<span data-ttu-id="c6ad6-104">\<associações ></span><span class="sxs-lookup"><span data-stu-id="c6ad6-104">\<bindings></span></span>  
<span data-ttu-id="c6ad6-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="c6ad6-105">\<customBinding></span></span>  
<span data-ttu-id="c6ad6-106">\<associação ></span><span class="sxs-lookup"><span data-stu-id="c6ad6-106">\<binding></span></span>  
<span data-ttu-id="c6ad6-107">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="c6ad6-107">\<security></span></span>  
<span data-ttu-id="c6ad6-108">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="c6ad6-108">\<issuedTokenParameters></span></span>  
<span data-ttu-id="c6ad6-109">\<issuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="c6ad6-109">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6ad6-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c6ad6-110">Syntax</span></span>  
  
```xml  
<issuerMetaData address=String"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c6ad6-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c6ad6-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c6ad6-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c6ad6-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6ad6-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="c6ad6-113">Attributes</span></span>  
  
|<span data-ttu-id="c6ad6-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="c6ad6-114">Attribute</span></span>|<span data-ttu-id="c6ad6-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="c6ad6-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c6ad6-116">endereço</span><span class="sxs-lookup"><span data-stu-id="c6ad6-116">address</span></span>|<span data-ttu-id="c6ad6-117">Necessário.</span><span class="sxs-lookup"><span data-stu-id="c6ad6-117">Required.</span></span> <span data-ttu-id="c6ad6-118">Uma cadeia de caracteres que especifica o endereço do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="c6ad6-118">A string that specifies the address of the endpoint.</span></span> <span data-ttu-id="c6ad6-119">O endereço deve ser um URI absoluto.</span><span class="sxs-lookup"><span data-stu-id="c6ad6-119">The address must be an absolute URI.</span></span> <span data-ttu-id="c6ad6-120">O valor padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="c6ad6-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c6ad6-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c6ad6-121">Child Elements</span></span>  
  
|<span data-ttu-id="c6ad6-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="c6ad6-122">Element</span></span>|<span data-ttu-id="c6ad6-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="c6ad6-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6ad6-124">\<cabeçalhos ></span><span class="sxs-lookup"><span data-stu-id="c6ad6-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="c6ad6-125">Uma coleção de cabeçalhos de endereço.</span><span class="sxs-lookup"><span data-stu-id="c6ad6-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="c6ad6-126">\<identidade ></span><span class="sxs-lookup"><span data-stu-id="c6ad6-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="c6ad6-127">Uma identidade que permite a autenticação de um ponto de extremidade por outros pontos de extremidade de troca de mensagens com ele.</span><span class="sxs-lookup"><span data-stu-id="c6ad6-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c6ad6-128">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c6ad6-128">Parent Elements</span></span>  
  
|<span data-ttu-id="c6ad6-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="c6ad6-129">Element</span></span>|<span data-ttu-id="c6ad6-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="c6ad6-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6ad6-131">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="c6ad6-131">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="c6ad6-132">Especifica os parâmetros de um token de segurança emitido em um cenário de segurança federada.</span><span class="sxs-lookup"><span data-stu-id="c6ad6-132">Specifies the parameters for an security token issued in a Federated security scenario.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c6ad6-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c6ad6-133">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="c6ad6-134">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="c6ad6-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="c6ad6-135">Federação e Tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="c6ad6-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="c6ad6-136">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="c6ad6-136">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="c6ad6-137">Federação e Tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="c6ad6-137">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 <span data-ttu-id="c6ad6-138">[Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)</span><span class="sxs-lookup"><span data-stu-id="c6ad6-138">[Bindings](../../../../../docs/framework/wcf/bindings.md)</span></span>  
 [<span data-ttu-id="c6ad6-139">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="c6ad6-139">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="c6ad6-140">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="c6ad6-140">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="c6ad6-141">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="c6ad6-141">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="c6ad6-142">Como: criar uma associação personalizada utilizando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="c6ad6-142">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="c6ad6-143">Segurança de associação personalizada</span><span class="sxs-lookup"><span data-stu-id="c6ad6-143">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
