---
title: '&lt;knownType&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 439d241d73df4db2820eac72c5e88e7d9023c6a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltknowntypegt"></a><span data-ttu-id="3a0df-102">&lt;knownType&gt;</span><span class="sxs-lookup"><span data-stu-id="3a0df-102">&lt;knownType&gt;</span></span>
<span data-ttu-id="3a0df-103">Especifica um tipo a ser usado por <xref:System.Runtime.Serialization.DataContractSerializer> durante a desserialização.</span><span class="sxs-lookup"><span data-stu-id="3a0df-103">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="3a0df-104">O elemento Especifica um "tipo conhecido" que é retornado por um campo ou propriedade de um "tipo declarado".</span><span class="sxs-lookup"><span data-stu-id="3a0df-104">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="3a0df-105">Para obter mais informações, consulte [tipos conhecidos de contrato de dados](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="3a0df-105">For more information, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="3a0df-106">\<Serialization ></span><span class="sxs-lookup"><span data-stu-id="3a0df-106">\<system.runtime.serialization></span></span>  
<span data-ttu-id="3a0df-107">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="3a0df-107">\<dataContractSerializer></span></span>  
<span data-ttu-id="3a0df-108">\<declaredTypes > elemento</span><span class="sxs-lookup"><span data-stu-id="3a0df-108">\<declaredTypes> Element</span></span>  
<span data-ttu-id="3a0df-109">\<Adicionar > de \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="3a0df-109">\<add> of \<declaredTypes></span></span>  
<span data-ttu-id="3a0df-110">\<knownType > elemento</span><span class="sxs-lookup"><span data-stu-id="3a0df-110">\<knownType> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a0df-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3a0df-111">Syntax</span></span>  
  
```xml  
<knownType type="String">  
     <parameter index="Integer"  
                type="String" />  
</knownType>  
```  
  
## <a name="type"></a><span data-ttu-id="3a0df-112">Tipo</span><span class="sxs-lookup"><span data-stu-id="3a0df-112">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a0df-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3a0df-113">Attributes and Elements</span></span>  
 <span data-ttu-id="3a0df-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3a0df-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a0df-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="3a0df-115">Attributes</span></span>  
  
|<span data-ttu-id="3a0df-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="3a0df-116">Attribute</span></span>|<span data-ttu-id="3a0df-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a0df-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3a0df-118">tipo</span><span class="sxs-lookup"><span data-stu-id="3a0df-118">type</span></span>|<span data-ttu-id="3a0df-119">Especifica o tipo (incluindo namespace), nome de assembly, versão, cultura e token de chave pública.</span><span class="sxs-lookup"><span data-stu-id="3a0df-119">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3a0df-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3a0df-120">Child Elements</span></span>  
  
|<span data-ttu-id="3a0df-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="3a0df-121">Element</span></span>|<span data-ttu-id="3a0df-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a0df-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3a0df-123">\<parâmetro ></span><span class="sxs-lookup"><span data-stu-id="3a0df-123">\<parameter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/parameter.md)|<span data-ttu-id="3a0df-124">Especifica um índice de parâmetro quando o tipo declarado é um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="3a0df-124">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3a0df-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3a0df-125">Parent Elements</span></span>  
  
|<span data-ttu-id="3a0df-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="3a0df-126">Element</span></span>|<span data-ttu-id="3a0df-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a0df-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3a0df-128">\<add></span><span class="sxs-lookup"><span data-stu-id="3a0df-128">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="3a0df-129">Adiciona um tipo declarado para a coleção de tipos declarados.</span><span class="sxs-lookup"><span data-stu-id="3a0df-129">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a0df-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="3a0df-130">Remarks</span></span>  
 <span data-ttu-id="3a0df-131">Para obter mais informações sobre tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) e <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="3a0df-131">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="3a0df-132">Consulte o [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) para obter um exemplo de como usar esse elemento.</span><span class="sxs-lookup"><span data-stu-id="3a0df-132">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a0df-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3a0df-133">Example</span></span>  
  
```xml  
<add type="MyCompany.Library.Shape,   
           MyAssembly, Version=2.0.0.0, Culture=neutral,  
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">  
           <knownType type="MyCompany.Library.Circle,   
                      MyAssembly, Version=2.0.0.0, Culture=neutral,  
                      PublicKeyToken=XXXXXX,  
                      processorArchitecture=MSIL"/>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3a0df-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3a0df-134">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="3a0df-135">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="3a0df-135">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="3a0df-136">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="3a0df-136">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="3a0df-137">\<add></span><span class="sxs-lookup"><span data-stu-id="3a0df-137">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
