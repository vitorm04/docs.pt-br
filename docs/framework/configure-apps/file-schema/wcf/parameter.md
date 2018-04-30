---
title: '&lt;parameter&gt;'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: aa4b2c870864a4359ebca0a1ae47fc1c8aaebca0
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="ltparametergt"></a><span data-ttu-id="f33cc-102">&lt;parameter&gt;</span><span class="sxs-lookup"><span data-stu-id="f33cc-102">&lt;parameter&gt;</span></span>
<span data-ttu-id="f33cc-103">Especifica o parâmetro genérico quando um tipo declarado é um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="f33cc-103">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
 <span data-ttu-id="f33cc-104">\<Serialization ></span><span class="sxs-lookup"><span data-stu-id="f33cc-104">\<system.runtime.serialization></span></span>  
<span data-ttu-id="f33cc-105">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="f33cc-105">\<dataContractSerializer></span></span>  
<span data-ttu-id="f33cc-106">\<declaredTypes > elemento</span><span class="sxs-lookup"><span data-stu-id="f33cc-106">\<declaredTypes> Element</span></span>  
<span data-ttu-id="f33cc-107">\<Adicionar > elemento para \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="f33cc-107">\<add> element for \<declaredTypes></span></span>  
<span data-ttu-id="f33cc-108">\<knownType > elemento</span><span class="sxs-lookup"><span data-stu-id="f33cc-108">\<knownType> Element</span></span>  
<span data-ttu-id="f33cc-109">\<parâmetro > elemento</span><span class="sxs-lookup"><span data-stu-id="f33cc-109">\<parameter> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f33cc-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f33cc-110">Syntax</span></span>  
  
```xml  
<parameter index="integer"  
                      type=String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f33cc-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f33cc-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f33cc-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f33cc-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f33cc-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="f33cc-113">Attributes</span></span>  
  
|<span data-ttu-id="f33cc-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="f33cc-114">Attribute</span></span>|<span data-ttu-id="f33cc-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="f33cc-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f33cc-116">índice</span><span class="sxs-lookup"><span data-stu-id="f33cc-116">index</span></span>|<span data-ttu-id="f33cc-117">Quando o tipo declarado é um tipo genérico, especifica o parâmetro genérico que retornará o tipo conhecido.</span><span class="sxs-lookup"><span data-stu-id="f33cc-117">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="f33cc-118">tipo</span><span class="sxs-lookup"><span data-stu-id="f33cc-118">type</span></span>|<span data-ttu-id="f33cc-119">Uma cadeia de caracteres que descreve o tipo conhecido usado para serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="f33cc-119">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="f33cc-120">Atributo de índice</span><span class="sxs-lookup"><span data-stu-id="f33cc-120">index Attribute</span></span>  
  
|<span data-ttu-id="f33cc-121">Valor</span><span class="sxs-lookup"><span data-stu-id="f33cc-121">Value</span></span>|<span data-ttu-id="f33cc-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="f33cc-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f33cc-123">"0"</span><span class="sxs-lookup"><span data-stu-id="f33cc-123">"0"</span></span>|<span data-ttu-id="f33cc-124">O primeiro parâmetro de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="f33cc-124">The first parameter in the generic type.</span></span> <span data-ttu-id="f33cc-125">Por exemplo, um <xref:System.Collections.Generic.List%601> tem apenas um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f33cc-125">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="f33cc-126">Se ele é usado como o tipo declarado, o índice seria definido como "0".</span><span class="sxs-lookup"><span data-stu-id="f33cc-126">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="f33cc-127">"1"</span><span class="sxs-lookup"><span data-stu-id="f33cc-127">"1"</span></span>|<span data-ttu-id="f33cc-128">O segundo parâmetro em um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="f33cc-128">The second parameter in a generic type.</span></span> <span data-ttu-id="f33cc-129">Por exemplo, um <xref:System.Collections.Generic.Dictionary%602> tem dois parâmetros.</span><span class="sxs-lookup"><span data-stu-id="f33cc-129">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="f33cc-130">Se o tipo conhecido é retornado pelo segundo parâmetro, defina o atributo de índice como "1".</span><span class="sxs-lookup"><span data-stu-id="f33cc-130">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f33cc-131">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f33cc-131">Child Elements</span></span>  
 <span data-ttu-id="f33cc-132">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="f33cc-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f33cc-133">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f33cc-133">Parent Elements</span></span>  
  
|<span data-ttu-id="f33cc-134">Elemento</span><span class="sxs-lookup"><span data-stu-id="f33cc-134">Element</span></span>|<span data-ttu-id="f33cc-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="f33cc-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f33cc-136">\<knownType ></span><span class="sxs-lookup"><span data-stu-id="f33cc-136">\<knownType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|<span data-ttu-id="f33cc-137">Especifica um tipo conhecido que pode ser retornado por um campo ou propriedade do tipo declarado.</span><span class="sxs-lookup"><span data-stu-id="f33cc-137">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f33cc-138">Comentários</span><span class="sxs-lookup"><span data-stu-id="f33cc-138">Remarks</span></span>  
 <span data-ttu-id="f33cc-139">Para obter mais informações sobre tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) e <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="f33cc-139">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="f33cc-140">Consulte o [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) para obter um exemplo de como usar esse elemento.</span><span class="sxs-lookup"><span data-stu-id="f33cc-140">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="f33cc-141">Este elemento de configuração não pode ter dois atributos ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="f33cc-141">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="f33cc-142">Se ambos os atributos são definidos, um <xref:System.Configuration.ConfigurationErrorsException> ocorre.</span><span class="sxs-lookup"><span data-stu-id="f33cc-142">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f33cc-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f33cc-143">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="f33cc-144">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="f33cc-144">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="f33cc-145">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="f33cc-145">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="f33cc-146">\<add></span><span class="sxs-lookup"><span data-stu-id="f33cc-146">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
