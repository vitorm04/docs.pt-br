---
title: <parameter>
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: 07fa410109a7bd2fa315132c4737301698bb3a93
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400108"
---
# <a name="parameter"></a><span data-ttu-id="43ee8-101">\<parameter></span><span class="sxs-lookup"><span data-stu-id="43ee8-101">\<parameter></span></span>
<span data-ttu-id="43ee8-102">Especifica o parâmetro genérico quando um tipo declarado é um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="43ee8-102">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
<span data-ttu-id="43ee8-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="43ee8-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="43ee8-104">&nbsp;&nbsp;[ **\<> System. Runtime. Serialization**](system-runtime-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="43ee8-104">&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)</span></span>\
<span data-ttu-id="43ee8-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> do dataContractSerializer**](datacontractserializer.md)</span><span class="sxs-lookup"><span data-stu-id="43ee8-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)</span></span>\
<span data-ttu-id="43ee8-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> declaredTypes**](declaredtypes.md)</span><span class="sxs-lookup"><span data-stu-id="43ee8-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)</span></span>\
<span data-ttu-id="43ee8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Adicionar >** ](add-of-declaredtypes-element.md)</span><span class="sxs-lookup"><span data-stu-id="43ee8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-of-declaredtypes-element.md)</span></span>\
<span data-ttu-id="43ee8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<knownType >** ](knowntype.md)</span><span class="sxs-lookup"><span data-stu-id="43ee8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<knownType>**](knowntype.md)</span></span>\
<span data-ttu-id="43ee8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de parâmetro**</span><span class="sxs-lookup"><span data-stu-id="43ee8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<parameter>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43ee8-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="43ee8-110">Syntax</span></span>  
  
```xml  
<parameter index="Integer"
           type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43ee8-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="43ee8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="43ee8-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="43ee8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43ee8-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="43ee8-113">Attributes</span></span>  
  
|<span data-ttu-id="43ee8-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="43ee8-114">Attribute</span></span>|<span data-ttu-id="43ee8-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="43ee8-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="43ee8-116">índice</span><span class="sxs-lookup"><span data-stu-id="43ee8-116">index</span></span>|<span data-ttu-id="43ee8-117">Quando o tipo declarado é um tipo genérico, especifica o parâmetro genérico que retornará o tipo conhecido.</span><span class="sxs-lookup"><span data-stu-id="43ee8-117">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="43ee8-118">tipo</span><span class="sxs-lookup"><span data-stu-id="43ee8-118">type</span></span>|<span data-ttu-id="43ee8-119">Uma cadeia de caracteres que descreve o tipo conhecido usado para serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="43ee8-119">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="43ee8-120">Atributo de índice</span><span class="sxs-lookup"><span data-stu-id="43ee8-120">index Attribute</span></span>  
  
|<span data-ttu-id="43ee8-121">Valor</span><span class="sxs-lookup"><span data-stu-id="43ee8-121">Value</span></span>|<span data-ttu-id="43ee8-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="43ee8-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="43ee8-123">"0"</span><span class="sxs-lookup"><span data-stu-id="43ee8-123">"0"</span></span>|<span data-ttu-id="43ee8-124">O primeiro parâmetro no tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="43ee8-124">The first parameter in the generic type.</span></span> <span data-ttu-id="43ee8-125">Por exemplo, um <xref:System.Collections.Generic.List%601> tem apenas um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="43ee8-125">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="43ee8-126">Se for usado como o tipo declarado, o índice será definido como "0".</span><span class="sxs-lookup"><span data-stu-id="43ee8-126">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="43ee8-127">"1"</span><span class="sxs-lookup"><span data-stu-id="43ee8-127">"1"</span></span>|<span data-ttu-id="43ee8-128">O segundo parâmetro em um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="43ee8-128">The second parameter in a generic type.</span></span> <span data-ttu-id="43ee8-129">Por exemplo, um <xref:System.Collections.Generic.Dictionary%602> tem dois parâmetros.</span><span class="sxs-lookup"><span data-stu-id="43ee8-129">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="43ee8-130">Se o tipo conhecido for retornado pelo segundo parâmetro, defina o atributo de índice como "1".</span><span class="sxs-lookup"><span data-stu-id="43ee8-130">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="43ee8-131">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="43ee8-131">Child Elements</span></span>  
 <span data-ttu-id="43ee8-132">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="43ee8-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="43ee8-133">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="43ee8-133">Parent Elements</span></span>  
  
|<span data-ttu-id="43ee8-134">Elemento</span><span class="sxs-lookup"><span data-stu-id="43ee8-134">Element</span></span>|<span data-ttu-id="43ee8-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="43ee8-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43ee8-136">\<knownType ></span><span class="sxs-lookup"><span data-stu-id="43ee8-136">\<knownType></span></span>](knowntype.md)|<span data-ttu-id="43ee8-137">Especifica um tipo conhecido que pode ser retornado por um campo ou Propriedade do tipo declarado.</span><span class="sxs-lookup"><span data-stu-id="43ee8-137">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43ee8-138">Comentários</span><span class="sxs-lookup"><span data-stu-id="43ee8-138">Remarks</span></span>  
 <span data-ttu-id="43ee8-139">Para obter mais informações sobre tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../wcf/feature-details/data-contract-known-types.md) e. <xref:System.Runtime.Serialization.DataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="43ee8-139">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="43ee8-140">Consulte o [ \<> do DataContractSerializer](datacontractserializer-element.md) para obter um exemplo de como usar esse elemento.</span><span class="sxs-lookup"><span data-stu-id="43ee8-140">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="43ee8-141">Este elemento de configuração não pode ter ambos os atributos ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="43ee8-141">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="43ee8-142">Se ambos os atributos forem definidos, <xref:System.Configuration.ConfigurationErrorsException> ocorrerá um.</span><span class="sxs-lookup"><span data-stu-id="43ee8-142">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43ee8-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43ee8-143">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="43ee8-144">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="43ee8-144">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="43ee8-145">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="43ee8-145">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="43ee8-146">\<add></span><span class="sxs-lookup"><span data-stu-id="43ee8-146">\<add></span></span>](add-of-declaredtypes-element.md)
