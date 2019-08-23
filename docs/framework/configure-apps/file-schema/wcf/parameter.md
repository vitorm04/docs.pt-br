---
title: <parameter>
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: c3f2179835ad1232e115cad0decdd3d41bbdc160
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932841"
---
# <a name="parameter"></a><span data-ttu-id="47516-101">\<parameter></span><span class="sxs-lookup"><span data-stu-id="47516-101">\<parameter></span></span>
<span data-ttu-id="47516-102">Especifica o parâmetro genérico quando um tipo declarado é um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="47516-102">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
 <span data-ttu-id="47516-103">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="47516-103">\<system.runtime.serialization></span></span>  
<span data-ttu-id="47516-104">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="47516-104">\<dataContractSerializer></span></span>  
<span data-ttu-id="47516-105">\<Elemento de > declaredTypes</span><span class="sxs-lookup"><span data-stu-id="47516-105">\<declaredTypes> Element</span></span>  
<span data-ttu-id="47516-106">\<Adicionar > elemento para \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="47516-106">\<add> element for \<declaredTypes></span></span>  
<span data-ttu-id="47516-107">\<Elemento > knownType</span><span class="sxs-lookup"><span data-stu-id="47516-107">\<knownType> Element</span></span>  
<span data-ttu-id="47516-108">\<Elemento de > de parâmetro</span><span class="sxs-lookup"><span data-stu-id="47516-108">\<parameter> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47516-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="47516-109">Syntax</span></span>  
  
```xml  
<parameter index="Integer"
           type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="47516-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="47516-110">Attributes and Elements</span></span>  
 <span data-ttu-id="47516-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="47516-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="47516-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="47516-112">Attributes</span></span>  
  
|<span data-ttu-id="47516-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="47516-113">Attribute</span></span>|<span data-ttu-id="47516-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="47516-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="47516-115">índice</span><span class="sxs-lookup"><span data-stu-id="47516-115">index</span></span>|<span data-ttu-id="47516-116">Quando o tipo declarado é um tipo genérico, especifica o parâmetro genérico que retornará o tipo conhecido.</span><span class="sxs-lookup"><span data-stu-id="47516-116">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="47516-117">tipo</span><span class="sxs-lookup"><span data-stu-id="47516-117">type</span></span>|<span data-ttu-id="47516-118">Uma cadeia de caracteres que descreve o tipo conhecido usado para serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="47516-118">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="47516-119">Atributo de índice</span><span class="sxs-lookup"><span data-stu-id="47516-119">index Attribute</span></span>  
  
|<span data-ttu-id="47516-120">Valor</span><span class="sxs-lookup"><span data-stu-id="47516-120">Value</span></span>|<span data-ttu-id="47516-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="47516-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="47516-122">"0"</span><span class="sxs-lookup"><span data-stu-id="47516-122">"0"</span></span>|<span data-ttu-id="47516-123">O primeiro parâmetro no tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="47516-123">The first parameter in the generic type.</span></span> <span data-ttu-id="47516-124">Por exemplo, um <xref:System.Collections.Generic.List%601> tem apenas um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="47516-124">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="47516-125">Se for usado como o tipo declarado, o índice será definido como "0".</span><span class="sxs-lookup"><span data-stu-id="47516-125">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="47516-126">"1"</span><span class="sxs-lookup"><span data-stu-id="47516-126">"1"</span></span>|<span data-ttu-id="47516-127">O segundo parâmetro em um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="47516-127">The second parameter in a generic type.</span></span> <span data-ttu-id="47516-128">Por exemplo, um <xref:System.Collections.Generic.Dictionary%602> tem dois parâmetros.</span><span class="sxs-lookup"><span data-stu-id="47516-128">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="47516-129">Se o tipo conhecido for retornado pelo segundo parâmetro, defina o atributo de índice como "1".</span><span class="sxs-lookup"><span data-stu-id="47516-129">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="47516-130">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="47516-130">Child Elements</span></span>  
 <span data-ttu-id="47516-131">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="47516-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="47516-132">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="47516-132">Parent Elements</span></span>  
  
|<span data-ttu-id="47516-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="47516-133">Element</span></span>|<span data-ttu-id="47516-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="47516-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="47516-135">\<knownType ></span><span class="sxs-lookup"><span data-stu-id="47516-135">\<knownType></span></span>](knowntype.md)|<span data-ttu-id="47516-136">Especifica um tipo conhecido que pode ser retornado por um campo ou Propriedade do tipo declarado.</span><span class="sxs-lookup"><span data-stu-id="47516-136">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47516-137">Comentários</span><span class="sxs-lookup"><span data-stu-id="47516-137">Remarks</span></span>  
 <span data-ttu-id="47516-138">Para obter mais informações sobre tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../wcf/feature-details/data-contract-known-types.md) e. <xref:System.Runtime.Serialization.DataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="47516-138">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="47516-139">Consulte o [ \<> do DataContractSerializer](datacontractserializer-element.md) para obter um exemplo de como usar esse elemento.</span><span class="sxs-lookup"><span data-stu-id="47516-139">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="47516-140">Este elemento de configuração não pode ter ambos os atributos ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="47516-140">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="47516-141">Se ambos os atributos forem definidos, <xref:System.Configuration.ConfigurationErrorsException> ocorrerá um.</span><span class="sxs-lookup"><span data-stu-id="47516-141">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47516-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="47516-142">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="47516-143">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="47516-143">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="47516-144">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="47516-144">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="47516-145">\<add></span><span class="sxs-lookup"><span data-stu-id="47516-145">\<add></span></span>](add-of-declaredtypes-element.md)
