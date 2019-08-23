---
title: <knownType>
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: a0794314cfcb87df00d66b6832356fb130787eba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928861"
---
# <a name="knowntype"></a><span data-ttu-id="dd1b0-101">\<knownType ></span><span class="sxs-lookup"><span data-stu-id="dd1b0-101">\<knownType></span></span>
<span data-ttu-id="dd1b0-102">Especifica um tipo a ser usado pelo <xref:System.Runtime.Serialization.DataContractSerializer> durante a desserialização.</span><span class="sxs-lookup"><span data-stu-id="dd1b0-102">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="dd1b0-103">O elemento especifica um "tipo conhecido" que é retornado por um campo ou propriedade de um "tipo declarado".</span><span class="sxs-lookup"><span data-stu-id="dd1b0-103">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="dd1b0-104">Para obter mais informações, consulte [tipos conhecidos de contrato de dados](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="dd1b0-104">For more information, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="dd1b0-105">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="dd1b0-105">\<system.runtime.serialization></span></span>  
<span data-ttu-id="dd1b0-106">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="dd1b0-106">\<dataContractSerializer></span></span>  
<span data-ttu-id="dd1b0-107">\<Elemento de > declaredTypes</span><span class="sxs-lookup"><span data-stu-id="dd1b0-107">\<declaredTypes> Element</span></span>  
<span data-ttu-id="dd1b0-108">\<Adicionar > de \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="dd1b0-108">\<add> of \<declaredTypes></span></span>  
<span data-ttu-id="dd1b0-109">\<Elemento > knownType</span><span class="sxs-lookup"><span data-stu-id="dd1b0-109">\<knownType> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd1b0-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dd1b0-110">Syntax</span></span>  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a><span data-ttu-id="dd1b0-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="dd1b0-111">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd1b0-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="dd1b0-112">Attributes and Elements</span></span>  
 <span data-ttu-id="dd1b0-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="dd1b0-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd1b0-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="dd1b0-114">Attributes</span></span>  
  
|<span data-ttu-id="dd1b0-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="dd1b0-115">Attribute</span></span>|<span data-ttu-id="dd1b0-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="dd1b0-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dd1b0-117">tipo</span><span class="sxs-lookup"><span data-stu-id="dd1b0-117">type</span></span>|<span data-ttu-id="dd1b0-118">Especifica o tipo (incluindo o namespace), o nome do assembly, a versão, a cultura e o token de chave pública.</span><span class="sxs-lookup"><span data-stu-id="dd1b0-118">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dd1b0-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="dd1b0-119">Child Elements</span></span>  
  
|<span data-ttu-id="dd1b0-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="dd1b0-120">Element</span></span>|<span data-ttu-id="dd1b0-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="dd1b0-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd1b0-122">\<parameter></span><span class="sxs-lookup"><span data-stu-id="dd1b0-122">\<parameter></span></span>](parameter.md)|<span data-ttu-id="dd1b0-123">Especifica um índice de parâmetro quando o tipo declarado é um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="dd1b0-123">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dd1b0-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="dd1b0-124">Parent Elements</span></span>  
  
|<span data-ttu-id="dd1b0-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="dd1b0-125">Element</span></span>|<span data-ttu-id="dd1b0-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="dd1b0-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd1b0-127">\<add></span><span class="sxs-lookup"><span data-stu-id="dd1b0-127">\<add></span></span>](add-of-declaredtypes-element.md)|<span data-ttu-id="dd1b0-128">Adiciona um tipo declarado à coleção de tipos declarados.</span><span class="sxs-lookup"><span data-stu-id="dd1b0-128">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd1b0-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="dd1b0-129">Remarks</span></span>  
 <span data-ttu-id="dd1b0-130">Para obter mais informações sobre tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../wcf/feature-details/data-contract-known-types.md) e. <xref:System.Runtime.Serialization.DataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="dd1b0-130">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="dd1b0-131">Consulte o [ \<> do DataContractSerializer](datacontractserializer-element.md) para obter um exemplo de como usar esse elemento.</span><span class="sxs-lookup"><span data-stu-id="dd1b0-131">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd1b0-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dd1b0-132">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dd1b0-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dd1b0-133">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="dd1b0-134">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="dd1b0-134">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="dd1b0-135">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="dd1b0-135">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="dd1b0-136">\<add></span><span class="sxs-lookup"><span data-stu-id="dd1b0-136">\<add></span></span>](add-of-declaredtypes-element.md)
