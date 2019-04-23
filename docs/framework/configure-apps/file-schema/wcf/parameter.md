---
title: <parameter>
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: 22ef3c3c6d23d6c68c27d6b5d1ed35b7c9910d48
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59230792"
---
# <a name="parameter"></a><span data-ttu-id="d7efe-101">\<parameter></span><span class="sxs-lookup"><span data-stu-id="d7efe-101">\<parameter></span></span>
<span data-ttu-id="d7efe-102">Especifica o parâmetro genérico quando um tipo declarado é um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="d7efe-102">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
 <span data-ttu-id="d7efe-103">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="d7efe-103">\<system.runtime.serialization></span></span>  
<span data-ttu-id="d7efe-104">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="d7efe-104">\<dataContractSerializer></span></span>  
<span data-ttu-id="d7efe-105">\<declaredTypes > elemento</span><span class="sxs-lookup"><span data-stu-id="d7efe-105">\<declaredTypes> Element</span></span>  
<span data-ttu-id="d7efe-106">\<Adicionar > elemento para \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="d7efe-106">\<add> element for \<declaredTypes></span></span>  
<span data-ttu-id="d7efe-107">\<knownType > elemento</span><span class="sxs-lookup"><span data-stu-id="d7efe-107">\<knownType> Element</span></span>  
<span data-ttu-id="d7efe-108">\<parâmetro > elemento</span><span class="sxs-lookup"><span data-stu-id="d7efe-108">\<parameter> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7efe-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d7efe-109">Syntax</span></span>  
  
```xml  
<parameter index="Integer"
           type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d7efe-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d7efe-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d7efe-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d7efe-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d7efe-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="d7efe-112">Attributes</span></span>  
  
|<span data-ttu-id="d7efe-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="d7efe-113">Attribute</span></span>|<span data-ttu-id="d7efe-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="d7efe-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d7efe-115">índice</span><span class="sxs-lookup"><span data-stu-id="d7efe-115">index</span></span>|<span data-ttu-id="d7efe-116">Quando o tipo declarado é um tipo genérico, especifica o parâmetro genérico que retornará o tipo conhecido.</span><span class="sxs-lookup"><span data-stu-id="d7efe-116">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="d7efe-117">tipo</span><span class="sxs-lookup"><span data-stu-id="d7efe-117">type</span></span>|<span data-ttu-id="d7efe-118">Uma cadeia de caracteres que descreve o tipo conhecido usado para serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="d7efe-118">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="d7efe-119">Atributo de índice</span><span class="sxs-lookup"><span data-stu-id="d7efe-119">index Attribute</span></span>  
  
|<span data-ttu-id="d7efe-120">Valor</span><span class="sxs-lookup"><span data-stu-id="d7efe-120">Value</span></span>|<span data-ttu-id="d7efe-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="d7efe-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d7efe-122">"0"</span><span class="sxs-lookup"><span data-stu-id="d7efe-122">"0"</span></span>|<span data-ttu-id="d7efe-123">O primeiro parâmetro no tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="d7efe-123">The first parameter in the generic type.</span></span> <span data-ttu-id="d7efe-124">Por exemplo, um <xref:System.Collections.Generic.List%601> tem apenas um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="d7efe-124">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="d7efe-125">Se ele for usado como o tipo declarado, o índice seria definido como "0".</span><span class="sxs-lookup"><span data-stu-id="d7efe-125">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="d7efe-126">"1"</span><span class="sxs-lookup"><span data-stu-id="d7efe-126">"1"</span></span>|<span data-ttu-id="d7efe-127">O segundo parâmetro em um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="d7efe-127">The second parameter in a generic type.</span></span> <span data-ttu-id="d7efe-128">Por exemplo, um <xref:System.Collections.Generic.Dictionary%602> tem dois parâmetros.</span><span class="sxs-lookup"><span data-stu-id="d7efe-128">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="d7efe-129">Se o tipo conhecido é retornado pelo segundo parâmetro, defina o atributo de índice como "1".</span><span class="sxs-lookup"><span data-stu-id="d7efe-129">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d7efe-130">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d7efe-130">Child Elements</span></span>  
 <span data-ttu-id="d7efe-131">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="d7efe-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d7efe-132">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d7efe-132">Parent Elements</span></span>  
  
|<span data-ttu-id="d7efe-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="d7efe-133">Element</span></span>|<span data-ttu-id="d7efe-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="d7efe-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d7efe-135">\<knownType></span><span class="sxs-lookup"><span data-stu-id="d7efe-135">\<knownType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|<span data-ttu-id="d7efe-136">Especifica um tipo conhecido que pode ser retornado por um campo ou propriedade do tipo declarado.</span><span class="sxs-lookup"><span data-stu-id="d7efe-136">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7efe-137">Comentários</span><span class="sxs-lookup"><span data-stu-id="d7efe-137">Remarks</span></span>  
 <span data-ttu-id="d7efe-138">Para obter mais informações sobre tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) e <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="d7efe-138">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="d7efe-139">Consulte a [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) para obter um exemplo de como usar esse elemento.</span><span class="sxs-lookup"><span data-stu-id="d7efe-139">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="d7efe-140">Este elemento de configuração não pode ter os dois atributos ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="d7efe-140">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="d7efe-141">Se ambos os atributos são definidos, um <xref:System.Configuration.ConfigurationErrorsException> ocorre.</span><span class="sxs-lookup"><span data-stu-id="d7efe-141">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7efe-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7efe-142">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="d7efe-143">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="d7efe-143">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="d7efe-144">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="d7efe-144">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)
- [<span data-ttu-id="d7efe-145">\<add></span><span class="sxs-lookup"><span data-stu-id="d7efe-145">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
