---
title: <parameter>
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: 07fa410109a7bd2fa315132c4737301698bb3a93
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400108"
---
# \<parameter>
<span data-ttu-id="be655-101">Especifica o parâmetro genérico quando um tipo declarado é um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="be655-101">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-of-declaredtypes-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<knownType>**](knowntype.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<parameter>**  
  
## <a name="syntax"></a><span data-ttu-id="be655-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="be655-102">Syntax</span></span>  
  
```xml  
<parameter index="Integer"
           type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="be655-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="be655-103">Attributes and Elements</span></span>  
 <span data-ttu-id="be655-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="be655-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="be655-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="be655-105">Attributes</span></span>  
  
|<span data-ttu-id="be655-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="be655-106">Attribute</span></span>|<span data-ttu-id="be655-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="be655-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="be655-108">índice</span><span class="sxs-lookup"><span data-stu-id="be655-108">index</span></span>|<span data-ttu-id="be655-109">Quando o tipo declarado é um tipo genérico, especifica o parâmetro genérico que retornará o tipo conhecido.</span><span class="sxs-lookup"><span data-stu-id="be655-109">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="be655-110">type</span><span class="sxs-lookup"><span data-stu-id="be655-110">type</span></span>|<span data-ttu-id="be655-111">Uma cadeia de caracteres que descreve o tipo conhecido usado para serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="be655-111">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="be655-112">Atributo de índice</span><span class="sxs-lookup"><span data-stu-id="be655-112">index Attribute</span></span>  
  
|<span data-ttu-id="be655-113">Valor</span><span class="sxs-lookup"><span data-stu-id="be655-113">Value</span></span>|<span data-ttu-id="be655-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="be655-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="be655-115">"0"</span><span class="sxs-lookup"><span data-stu-id="be655-115">"0"</span></span>|<span data-ttu-id="be655-116">O primeiro parâmetro no tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="be655-116">The first parameter in the generic type.</span></span> <span data-ttu-id="be655-117">Por exemplo, um <xref:System.Collections.Generic.List%601> tem apenas um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="be655-117">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="be655-118">Se for usado como o tipo declarado, o índice será definido como "0".</span><span class="sxs-lookup"><span data-stu-id="be655-118">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="be655-119">"1"</span><span class="sxs-lookup"><span data-stu-id="be655-119">"1"</span></span>|<span data-ttu-id="be655-120">O segundo parâmetro em um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="be655-120">The second parameter in a generic type.</span></span> <span data-ttu-id="be655-121">Por exemplo, um <xref:System.Collections.Generic.Dictionary%602> tem dois parâmetros.</span><span class="sxs-lookup"><span data-stu-id="be655-121">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="be655-122">Se o tipo conhecido for retornado pelo segundo parâmetro, defina o atributo de índice como "1".</span><span class="sxs-lookup"><span data-stu-id="be655-122">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="be655-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="be655-123">Child Elements</span></span>  
 <span data-ttu-id="be655-124">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="be655-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="be655-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="be655-125">Parent Elements</span></span>  
  
|<span data-ttu-id="be655-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="be655-126">Element</span></span>|<span data-ttu-id="be655-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="be655-127">Description</span></span>|  
|-------------|-----------------|  
|[\<knownType>](knowntype.md)|<span data-ttu-id="be655-128">Especifica um tipo conhecido que pode ser retornado por um campo ou Propriedade do tipo declarado.</span><span class="sxs-lookup"><span data-stu-id="be655-128">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be655-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="be655-129">Remarks</span></span>  
 <span data-ttu-id="be655-130">Para obter mais informações sobre tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../wcf/feature-details/data-contract-known-types.md) e <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="be655-130">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="be655-131">Consulte o [\<dataContractSerializer>](datacontractserializer-element.md) para obter um exemplo de como usar esse elemento.</span><span class="sxs-lookup"><span data-stu-id="be655-131">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="be655-132">Este elemento de configuração não pode ter ambos os atributos ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="be655-132">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="be655-133">Se ambos os atributos forem definidos, <xref:System.Configuration.ConfigurationErrorsException> ocorrerá um.</span><span class="sxs-lookup"><span data-stu-id="be655-133">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be655-134">Confira também</span><span class="sxs-lookup"><span data-stu-id="be655-134">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="be655-135">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="be655-135">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [\<add>](add-of-declaredtypes-element.md)
