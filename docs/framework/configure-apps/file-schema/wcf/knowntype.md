---
title: '&lt;knownType&gt;'
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: cb36a0d1d1ceb13a6db902904783ee15b14e673b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54541060"
---
# <a name="ltknowntypegt"></a><span data-ttu-id="2aaee-102">&lt;knownType&gt;</span><span class="sxs-lookup"><span data-stu-id="2aaee-102">&lt;knownType&gt;</span></span>
<span data-ttu-id="2aaee-103">Especifica um tipo a ser usado por <xref:System.Runtime.Serialization.DataContractSerializer> durante a desserialização.</span><span class="sxs-lookup"><span data-stu-id="2aaee-103">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="2aaee-104">O elemento Especifica um "tipo conhecido" que é retornado por um campo ou propriedade de um "tipo declarado".</span><span class="sxs-lookup"><span data-stu-id="2aaee-104">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="2aaee-105">Para obter mais informações, consulte [tipos conhecidos de contrato de dados](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="2aaee-105">For more information, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="2aaee-106">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="2aaee-106">\<system.runtime.serialization></span></span>  
<span data-ttu-id="2aaee-107">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="2aaee-107">\<dataContractSerializer></span></span>  
<span data-ttu-id="2aaee-108">\<declaredTypes > elemento</span><span class="sxs-lookup"><span data-stu-id="2aaee-108">\<declaredTypes> Element</span></span>  
<span data-ttu-id="2aaee-109">\<Adicionar > de \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="2aaee-109">\<add> of \<declaredTypes></span></span>  
<span data-ttu-id="2aaee-110">\<knownType > elemento</span><span class="sxs-lookup"><span data-stu-id="2aaee-110">\<knownType> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2aaee-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2aaee-111">Syntax</span></span>  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a><span data-ttu-id="2aaee-112">Tipo</span><span class="sxs-lookup"><span data-stu-id="2aaee-112">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2aaee-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2aaee-113">Attributes and Elements</span></span>  
 <span data-ttu-id="2aaee-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2aaee-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2aaee-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="2aaee-115">Attributes</span></span>  
  
|<span data-ttu-id="2aaee-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="2aaee-116">Attribute</span></span>|<span data-ttu-id="2aaee-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="2aaee-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2aaee-118">tipo</span><span class="sxs-lookup"><span data-stu-id="2aaee-118">type</span></span>|<span data-ttu-id="2aaee-119">Especifica o tipo (incluindo namespace) nome do assembly, versão, cultura e token de chave pública.</span><span class="sxs-lookup"><span data-stu-id="2aaee-119">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2aaee-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2aaee-120">Child Elements</span></span>  
  
|<span data-ttu-id="2aaee-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="2aaee-121">Element</span></span>|<span data-ttu-id="2aaee-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="2aaee-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2aaee-123">\<parameter></span><span class="sxs-lookup"><span data-stu-id="2aaee-123">\<parameter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/parameter.md)|<span data-ttu-id="2aaee-124">Especifica um índice de parâmetro quando o tipo declarado é um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="2aaee-124">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2aaee-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2aaee-125">Parent Elements</span></span>  
  
|<span data-ttu-id="2aaee-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="2aaee-126">Element</span></span>|<span data-ttu-id="2aaee-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="2aaee-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2aaee-128">\<add></span><span class="sxs-lookup"><span data-stu-id="2aaee-128">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="2aaee-129">Adiciona um tipo declarado para a coleção de tipos declarados.</span><span class="sxs-lookup"><span data-stu-id="2aaee-129">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2aaee-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="2aaee-130">Remarks</span></span>  
 <span data-ttu-id="2aaee-131">Para obter mais informações sobre tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) e <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="2aaee-131">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="2aaee-132">Consulte a [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) para obter um exemplo de como usar esse elemento.</span><span class="sxs-lookup"><span data-stu-id="2aaee-132">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2aaee-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2aaee-133">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2aaee-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2aaee-134">See also</span></span>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="2aaee-135">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="2aaee-135">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="2aaee-136">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="2aaee-136">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)
- [<span data-ttu-id="2aaee-137">\<add></span><span class="sxs-lookup"><span data-stu-id="2aaee-137">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
