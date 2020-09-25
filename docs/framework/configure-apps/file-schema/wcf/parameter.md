---
title: <parameter>
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: 2ef674dc8601bc9afaf6b547265988bb8a99f943
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170162"
---
# \<parameter>

<span data-ttu-id="54357-101">Especifica o parâmetro genérico quando um tipo declarado é um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="54357-101">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-of-declaredtypes-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<knownType>**](knowntype.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<parameter>**  
  
## <a name="syntax"></a><span data-ttu-id="54357-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="54357-102">Syntax</span></span>  
  
```xml  
<parameter index="Integer"
           type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="54357-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="54357-103">Attributes and Elements</span></span>  

 <span data-ttu-id="54357-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="54357-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="54357-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="54357-105">Attributes</span></span>  
  
|<span data-ttu-id="54357-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="54357-106">Attribute</span></span>|<span data-ttu-id="54357-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="54357-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="54357-108">índice</span><span class="sxs-lookup"><span data-stu-id="54357-108">index</span></span>|<span data-ttu-id="54357-109">Quando o tipo declarado é um tipo genérico, especifica o parâmetro genérico que retornará o tipo conhecido.</span><span class="sxs-lookup"><span data-stu-id="54357-109">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="54357-110">tipo</span><span class="sxs-lookup"><span data-stu-id="54357-110">type</span></span>|<span data-ttu-id="54357-111">Uma cadeia de caracteres que descreve o tipo conhecido usado para serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="54357-111">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="54357-112">Atributo de índice</span><span class="sxs-lookup"><span data-stu-id="54357-112">index Attribute</span></span>  
  
|<span data-ttu-id="54357-113">Valor</span><span class="sxs-lookup"><span data-stu-id="54357-113">Value</span></span>|<span data-ttu-id="54357-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="54357-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="54357-115">"0"</span><span class="sxs-lookup"><span data-stu-id="54357-115">"0"</span></span>|<span data-ttu-id="54357-116">O primeiro parâmetro no tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="54357-116">The first parameter in the generic type.</span></span> <span data-ttu-id="54357-117">Por exemplo, um <xref:System.Collections.Generic.List%601> tem apenas um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="54357-117">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="54357-118">Se for usado como o tipo declarado, o índice será definido como "0".</span><span class="sxs-lookup"><span data-stu-id="54357-118">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="54357-119">"1"</span><span class="sxs-lookup"><span data-stu-id="54357-119">"1"</span></span>|<span data-ttu-id="54357-120">O segundo parâmetro em um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="54357-120">The second parameter in a generic type.</span></span> <span data-ttu-id="54357-121">Por exemplo, um <xref:System.Collections.Generic.Dictionary%602> tem dois parâmetros.</span><span class="sxs-lookup"><span data-stu-id="54357-121">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="54357-122">Se o tipo conhecido for retornado pelo segundo parâmetro, defina o atributo de índice como "1".</span><span class="sxs-lookup"><span data-stu-id="54357-122">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="54357-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="54357-123">Child Elements</span></span>  

 <span data-ttu-id="54357-124">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="54357-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="54357-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="54357-125">Parent Elements</span></span>  
  
|<span data-ttu-id="54357-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="54357-126">Element</span></span>|<span data-ttu-id="54357-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="54357-127">Description</span></span>|  
|-------------|-----------------|  
|[\<knownType>](knowntype.md)|<span data-ttu-id="54357-128">Especifica um tipo conhecido que pode ser retornado por um campo ou Propriedade do tipo declarado.</span><span class="sxs-lookup"><span data-stu-id="54357-128">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54357-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="54357-129">Remarks</span></span>  

 <span data-ttu-id="54357-130">Para obter mais informações sobre tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../wcf/feature-details/data-contract-known-types.md) e <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="54357-130">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="54357-131">Consulte o [\<dataContractSerializer>](datacontractserializer-element.md) para obter um exemplo de como usar esse elemento.</span><span class="sxs-lookup"><span data-stu-id="54357-131">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="54357-132">Este elemento de configuração não pode ter ambos os atributos ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="54357-132">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="54357-133">Se ambos os atributos forem definidos, <xref:System.Configuration.ConfigurationErrorsException> ocorrerá um.</span><span class="sxs-lookup"><span data-stu-id="54357-133">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54357-134">Confira também</span><span class="sxs-lookup"><span data-stu-id="54357-134">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="54357-135">Tipos de contratos de dados conhecidos</span><span class="sxs-lookup"><span data-stu-id="54357-135">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [\<add>](add-of-declaredtypes-element.md)
