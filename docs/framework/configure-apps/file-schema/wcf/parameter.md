---
title: <parameter>
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: 8b14dc1908ef3a06549154f70efb2d4e5cb10076
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55289414"
---
# <a name="parameter"></a><span data-ttu-id="61996-101">\<parameter></span><span class="sxs-lookup"><span data-stu-id="61996-101">\<parameter></span></span>
<span data-ttu-id="61996-102">Especifica o parâmetro genérico quando um tipo declarado é um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="61996-102">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
 <span data-ttu-id="61996-103">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="61996-103">\<system.runtime.serialization></span></span>  
<span data-ttu-id="61996-104">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="61996-104">\<dataContractSerializer></span></span>  
<span data-ttu-id="61996-105">\<declaredTypes > elemento</span><span class="sxs-lookup"><span data-stu-id="61996-105">\<declaredTypes> Element</span></span>  
<span data-ttu-id="61996-106">\<Adicionar > elemento para \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="61996-106">\<add> element for \<declaredTypes></span></span>  
<span data-ttu-id="61996-107">\<knownType > elemento</span><span class="sxs-lookup"><span data-stu-id="61996-107">\<knownType> Element</span></span>  
<span data-ttu-id="61996-108">\<parâmetro > elemento</span><span class="sxs-lookup"><span data-stu-id="61996-108">\<parameter> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61996-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="61996-109">Syntax</span></span>  
  
```xml  
<parameter index="Integer"
           type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="61996-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="61996-110">Attributes and Elements</span></span>  
 <span data-ttu-id="61996-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="61996-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="61996-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="61996-112">Attributes</span></span>  
  
|<span data-ttu-id="61996-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="61996-113">Attribute</span></span>|<span data-ttu-id="61996-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="61996-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="61996-115">índice</span><span class="sxs-lookup"><span data-stu-id="61996-115">index</span></span>|<span data-ttu-id="61996-116">Quando o tipo declarado é um tipo genérico, especifica o parâmetro genérico que retornará o tipo conhecido.</span><span class="sxs-lookup"><span data-stu-id="61996-116">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="61996-117">tipo</span><span class="sxs-lookup"><span data-stu-id="61996-117">type</span></span>|<span data-ttu-id="61996-118">Uma cadeia de caracteres que descreve o tipo conhecido usado para serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="61996-118">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="61996-119">Atributo de índice</span><span class="sxs-lookup"><span data-stu-id="61996-119">index Attribute</span></span>  
  
|<span data-ttu-id="61996-120">Valor</span><span class="sxs-lookup"><span data-stu-id="61996-120">Value</span></span>|<span data-ttu-id="61996-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="61996-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="61996-122">"0"</span><span class="sxs-lookup"><span data-stu-id="61996-122">"0"</span></span>|<span data-ttu-id="61996-123">O primeiro parâmetro no tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="61996-123">The first parameter in the generic type.</span></span> <span data-ttu-id="61996-124">Por exemplo, um <xref:System.Collections.Generic.List%601> tem apenas um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="61996-124">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="61996-125">Se ele for usado como o tipo declarado, o índice seria definido como "0".</span><span class="sxs-lookup"><span data-stu-id="61996-125">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="61996-126">"1"</span><span class="sxs-lookup"><span data-stu-id="61996-126">"1"</span></span>|<span data-ttu-id="61996-127">O segundo parâmetro em um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="61996-127">The second parameter in a generic type.</span></span> <span data-ttu-id="61996-128">Por exemplo, um <xref:System.Collections.Generic.Dictionary%602> tem dois parâmetros.</span><span class="sxs-lookup"><span data-stu-id="61996-128">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="61996-129">Se o tipo conhecido é retornado pelo segundo parâmetro, defina o atributo de índice como "1".</span><span class="sxs-lookup"><span data-stu-id="61996-129">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="61996-130">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="61996-130">Child Elements</span></span>  
 <span data-ttu-id="61996-131">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="61996-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="61996-132">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="61996-132">Parent Elements</span></span>  
  
|<span data-ttu-id="61996-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="61996-133">Element</span></span>|<span data-ttu-id="61996-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="61996-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="61996-135">\<knownType></span><span class="sxs-lookup"><span data-stu-id="61996-135">\<knownType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|<span data-ttu-id="61996-136">Especifica um tipo conhecido que pode ser retornado por um campo ou propriedade do tipo declarado.</span><span class="sxs-lookup"><span data-stu-id="61996-136">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61996-137">Comentários</span><span class="sxs-lookup"><span data-stu-id="61996-137">Remarks</span></span>  
 <span data-ttu-id="61996-138">Para obter mais informações sobre tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) e <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="61996-138">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="61996-139">Consulte a [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) para obter um exemplo de como usar esse elemento.</span><span class="sxs-lookup"><span data-stu-id="61996-139">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="61996-140">Este elemento de configuração não pode ter os dois atributos ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="61996-140">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="61996-141">Se ambos os atributos são definidos, um <xref:System.Configuration.ConfigurationErrorsException> ocorre.</span><span class="sxs-lookup"><span data-stu-id="61996-141">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61996-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61996-142">See also</span></span>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="61996-143">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="61996-143">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="61996-144">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="61996-144">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)
- [<span data-ttu-id="61996-145">\<add></span><span class="sxs-lookup"><span data-stu-id="61996-145">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
