---
title: <knownType>
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: 61f51b2ecd572ba254317a01e0f514503c7cc9e4
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397880"
---
# <a name="knowntype"></a><span data-ttu-id="5de33-101">\<knownType ></span><span class="sxs-lookup"><span data-stu-id="5de33-101">\<knownType></span></span>
<span data-ttu-id="5de33-102">Especifica um tipo a ser usado pelo <xref:System.Runtime.Serialization.DataContractSerializer> durante a desserialização.</span><span class="sxs-lookup"><span data-stu-id="5de33-102">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="5de33-103">O elemento especifica um "tipo conhecido" que é retornado por um campo ou propriedade de um "tipo declarado".</span><span class="sxs-lookup"><span data-stu-id="5de33-103">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="5de33-104">Para obter mais informações, consulte [tipos conhecidos de contrato de dados](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="5de33-104">For more information, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
<span data-ttu-id="5de33-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5de33-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5de33-106">&nbsp;&nbsp;[ **\<> System. Runtime. Serialization**](system-runtime-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="5de33-106">&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)</span></span>\
<span data-ttu-id="5de33-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> do dataContractSerializer**](datacontractserializer.md)</span><span class="sxs-lookup"><span data-stu-id="5de33-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)</span></span>\
<span data-ttu-id="5de33-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> declaredTypes**](declaredtypes.md)</span><span class="sxs-lookup"><span data-stu-id="5de33-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)</span></span>\
<span data-ttu-id="5de33-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Adicionar >** ](add-of-declaredtypes-element.md)</span><span class="sxs-lookup"><span data-stu-id="5de33-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-of-declaredtypes-element.md)</span></span>\
<span data-ttu-id="5de33-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<knownType >**</span><span class="sxs-lookup"><span data-stu-id="5de33-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<knownType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5de33-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5de33-111">Syntax</span></span>  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a><span data-ttu-id="5de33-112">Tipo</span><span class="sxs-lookup"><span data-stu-id="5de33-112">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5de33-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5de33-113">Attributes and Elements</span></span>  
 <span data-ttu-id="5de33-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5de33-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5de33-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="5de33-115">Attributes</span></span>  
  
|<span data-ttu-id="5de33-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="5de33-116">Attribute</span></span>|<span data-ttu-id="5de33-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="5de33-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5de33-118">tipo</span><span class="sxs-lookup"><span data-stu-id="5de33-118">type</span></span>|<span data-ttu-id="5de33-119">Especifica o tipo (incluindo o namespace), o nome do assembly, a versão, a cultura e o token de chave pública.</span><span class="sxs-lookup"><span data-stu-id="5de33-119">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5de33-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5de33-120">Child Elements</span></span>  
  
|<span data-ttu-id="5de33-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="5de33-121">Element</span></span>|<span data-ttu-id="5de33-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="5de33-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5de33-123">\<parameter></span><span class="sxs-lookup"><span data-stu-id="5de33-123">\<parameter></span></span>](parameter.md)|<span data-ttu-id="5de33-124">Especifica um índice de parâmetro quando o tipo declarado é um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="5de33-124">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5de33-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5de33-125">Parent Elements</span></span>  
  
|<span data-ttu-id="5de33-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="5de33-126">Element</span></span>|<span data-ttu-id="5de33-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="5de33-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5de33-128">\<add></span><span class="sxs-lookup"><span data-stu-id="5de33-128">\<add></span></span>](add-of-declaredtypes-element.md)|<span data-ttu-id="5de33-129">Adiciona um tipo declarado à coleção de tipos declarados.</span><span class="sxs-lookup"><span data-stu-id="5de33-129">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5de33-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="5de33-130">Remarks</span></span>  
 <span data-ttu-id="5de33-131">Para obter mais informações sobre tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../wcf/feature-details/data-contract-known-types.md) e. <xref:System.Runtime.Serialization.DataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="5de33-131">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="5de33-132">Consulte o [ \<> do DataContractSerializer](datacontractserializer-element.md) para obter um exemplo de como usar esse elemento.</span><span class="sxs-lookup"><span data-stu-id="5de33-132">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5de33-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5de33-133">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5de33-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5de33-134">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="5de33-135">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="5de33-135">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="5de33-136">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="5de33-136">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="5de33-137">\<add></span><span class="sxs-lookup"><span data-stu-id="5de33-137">\<add></span></span>](add-of-declaredtypes-element.md)
