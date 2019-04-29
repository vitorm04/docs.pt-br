---
title: <knownType>
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: 4d3dd9042951ffb46b8e0a3f7bb7bcdee23fd58b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760682"
---
# <a name="knowntype"></a><span data-ttu-id="51e21-101">\<knownType></span><span class="sxs-lookup"><span data-stu-id="51e21-101">\<knownType></span></span>
<span data-ttu-id="51e21-102">Especifica um tipo a ser usado por <xref:System.Runtime.Serialization.DataContractSerializer> durante a desserialização.</span><span class="sxs-lookup"><span data-stu-id="51e21-102">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="51e21-103">O elemento Especifica um "tipo conhecido" que é retornado por um campo ou propriedade de um "tipo declarado".</span><span class="sxs-lookup"><span data-stu-id="51e21-103">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="51e21-104">Para obter mais informações, consulte [tipos conhecidos de contrato de dados](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="51e21-104">For more information, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="51e21-105">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="51e21-105">\<system.runtime.serialization></span></span>  
<span data-ttu-id="51e21-106">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="51e21-106">\<dataContractSerializer></span></span>  
<span data-ttu-id="51e21-107">\<declaredTypes > elemento</span><span class="sxs-lookup"><span data-stu-id="51e21-107">\<declaredTypes> Element</span></span>  
<span data-ttu-id="51e21-108">\<Adicionar > de \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="51e21-108">\<add> of \<declaredTypes></span></span>  
<span data-ttu-id="51e21-109">\<knownType > elemento</span><span class="sxs-lookup"><span data-stu-id="51e21-109">\<knownType> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51e21-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="51e21-110">Syntax</span></span>  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a><span data-ttu-id="51e21-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="51e21-111">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="51e21-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="51e21-112">Attributes and Elements</span></span>  
 <span data-ttu-id="51e21-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="51e21-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="51e21-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="51e21-114">Attributes</span></span>  
  
|<span data-ttu-id="51e21-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="51e21-115">Attribute</span></span>|<span data-ttu-id="51e21-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="51e21-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="51e21-117">tipo</span><span class="sxs-lookup"><span data-stu-id="51e21-117">type</span></span>|<span data-ttu-id="51e21-118">Especifica o tipo (incluindo namespace) nome do assembly, versão, cultura e token de chave pública.</span><span class="sxs-lookup"><span data-stu-id="51e21-118">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="51e21-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="51e21-119">Child Elements</span></span>  
  
|<span data-ttu-id="51e21-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="51e21-120">Element</span></span>|<span data-ttu-id="51e21-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="51e21-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="51e21-122">\<parameter></span><span class="sxs-lookup"><span data-stu-id="51e21-122">\<parameter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/parameter.md)|<span data-ttu-id="51e21-123">Especifica um índice de parâmetro quando o tipo declarado é um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="51e21-123">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="51e21-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="51e21-124">Parent Elements</span></span>  
  
|<span data-ttu-id="51e21-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="51e21-125">Element</span></span>|<span data-ttu-id="51e21-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="51e21-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="51e21-127">\<add></span><span class="sxs-lookup"><span data-stu-id="51e21-127">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="51e21-128">Adiciona um tipo declarado para a coleção de tipos declarados.</span><span class="sxs-lookup"><span data-stu-id="51e21-128">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51e21-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="51e21-129">Remarks</span></span>  
 <span data-ttu-id="51e21-130">Para obter mais informações sobre tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) e <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="51e21-130">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="51e21-131">Consulte a [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) para obter um exemplo de como usar esse elemento.</span><span class="sxs-lookup"><span data-stu-id="51e21-131">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51e21-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="51e21-132">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="51e21-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="51e21-133">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="51e21-134">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="51e21-134">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="51e21-135">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="51e21-135">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)
- [<span data-ttu-id="51e21-136">\<add></span><span class="sxs-lookup"><span data-stu-id="51e21-136">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
