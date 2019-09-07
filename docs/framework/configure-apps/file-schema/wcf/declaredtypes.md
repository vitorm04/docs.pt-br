---
title: <declaredTypes>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- declaredTypes element
- DataContractSerializer
- KnownTypes
- <declaredTypes> element
ms.assetid: f35184e4-9d9e-4d37-8fb4-d5b58220eb3e
ms.openlocfilehash: c45a4e67d0a2d98c0e9c1a91e07f25b81370244c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398059"
---
# <a name="declaredtypes"></a><span data-ttu-id="62d57-101">\<declaredTypes></span><span class="sxs-lookup"><span data-stu-id="62d57-101">\<declaredTypes></span></span>
<span data-ttu-id="62d57-102">Contém os tipos conhecidos que o <xref:System.Runtime.Serialization.DataContractSerializer> usa ao desserializar.</span><span class="sxs-lookup"><span data-stu-id="62d57-102">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span>  
  
 <span data-ttu-id="62d57-103">Para obter mais informações sobre contratos de dados e tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="62d57-103">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
<span data-ttu-id="62d57-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="62d57-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="62d57-105">&nbsp;&nbsp;[ **\<> System. Runtime. Serialization**](system-runtime-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="62d57-105">&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)</span></span>\
<span data-ttu-id="62d57-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> do dataContractSerializer**](datacontractserializer.md)</span><span class="sxs-lookup"><span data-stu-id="62d57-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)</span></span>\
<span data-ttu-id="62d57-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> declaredTypes**</span><span class="sxs-lookup"><span data-stu-id="62d57-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<declaredTypes>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62d57-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="62d57-108">Syntax</span></span>  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer>
      <declaredTypes>
        <add type="String ">
          <knownType type="String">
            <parameter index="Integer"/>
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62d57-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="62d57-109">Attributes and Elements</span></span>  
 <span data-ttu-id="62d57-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="62d57-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62d57-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="62d57-111">Attributes</span></span>  
 <span data-ttu-id="62d57-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="62d57-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="62d57-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="62d57-113">Child Elements</span></span>  
  
|<span data-ttu-id="62d57-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="62d57-114">Element</span></span>|<span data-ttu-id="62d57-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="62d57-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="62d57-116">\<add></span><span class="sxs-lookup"><span data-stu-id="62d57-116">\<add></span></span>](add-of-declaredtypes-element.md)|<span data-ttu-id="62d57-117">Adiciona tipos que exigem tipos conhecidos.</span><span class="sxs-lookup"><span data-stu-id="62d57-117">Adds types that require known types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="62d57-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="62d57-118">Parent Elements</span></span>  
  
|<span data-ttu-id="62d57-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="62d57-119">Element</span></span>|<span data-ttu-id="62d57-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="62d57-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="62d57-121">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="62d57-121">\<dataContractSerializer></span></span>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="62d57-122">Contém dados de configuração para <xref:System.Runtime.Serialization.DataContractSerializer>o.</span><span class="sxs-lookup"><span data-stu-id="62d57-122">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62d57-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="62d57-123">Remarks</span></span>  
 <span data-ttu-id="62d57-124">Para obter mais informações sobre tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../wcf/feature-details/data-contract-known-types.md) e. <xref:System.Runtime.Serialization.DataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="62d57-124">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62d57-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="62d57-125">Example</span></span>  
 <span data-ttu-id="62d57-126">O código XML a seguir mostra tipos declarados e tipos conhecidos `DataContractSerializer` adicionados a um elemento.</span><span class="sxs-lookup"><span data-stu-id="62d57-126">The following XML code shows declared types and known types added to a `DataContractSerializer` element.</span></span> <span data-ttu-id="62d57-127">O exemplo mostra três tipos que estão sendo adicionados.</span><span class="sxs-lookup"><span data-stu-id="62d57-127">The example shows three types being added.</span></span> <span data-ttu-id="62d57-128">O primeiro é um tipo personalizado chamado "Orders" que usa um tipo conhecido chamado "item".</span><span class="sxs-lookup"><span data-stu-id="62d57-128">The first is a custom type named "Orders" that uses a known type named "Item".</span></span> <span data-ttu-id="62d57-129">O segundo tipo declarado é um <xref:System.Collections.Generic.List%601> que usa `Item` como um tipo conhecido.</span><span class="sxs-lookup"><span data-stu-id="62d57-129">The second declared type is a <xref:System.Collections.Generic.List%601> that uses `Item` as a known type.</span></span> <span data-ttu-id="62d57-130">Por fim, o terceiro tipo declarado <xref:System.Collections.Generic.Dictionary%602>é um.</span><span class="sxs-lookup"><span data-stu-id="62d57-130">Finally the third declared type is a <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="62d57-131">O <xref:System.Collections.Generic.Dictionary%602> tipo de classe é um tipo genérico, com dois parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="62d57-131">The <xref:System.Collections.Generic.Dictionary%602> class type is a generic type, with two type parameters.</span></span> <span data-ttu-id="62d57-132">O primeiro representa a chave e a segunda representa o valor.</span><span class="sxs-lookup"><span data-stu-id="62d57-132">The first represents the key and the second represents the value.</span></span> <span data-ttu-id="62d57-133">O exemplo a seguir adiciona <xref:System.Collections.Generic.List%601> um do segundo tipo (o valor) à lista de tipos conhecidos.</span><span class="sxs-lookup"><span data-stu-id="62d57-133">The following example adds a <xref:System.Collections.Generic.List%601> of the second type (the value) to the list of known types.</span></span> <span data-ttu-id="62d57-134">Você deve usar o `index` atributo para especificar o parâmetro de tipo a ser usado no tipo conhecido.</span><span class="sxs-lookup"><span data-stu-id="62d57-134">You must use the `index` attribute to specify which type parameter to use in the known type.</span></span> <span data-ttu-id="62d57-135">Nesse caso, o tipo de valor é indicado pelo atributo de índice definido como "1" (a coleção é baseada em zero).</span><span class="sxs-lookup"><span data-stu-id="62d57-135">In this case, the value type is indicated by the index attribute set to "1" (the collection is zero-based).</span></span>  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer>
      <declaredTypes>
        <add type="Examples.Types.Orders, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />
        </add>
        <add type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />
        </add>
        <add type="System.Collections.Generic.Dictionary`2, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
          <knownType type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
            <parameter index="1"/>
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="62d57-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="62d57-136">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="62d57-137">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="62d57-137">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="62d57-138">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="62d57-138">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="62d57-139">\<add></span><span class="sxs-lookup"><span data-stu-id="62d57-139">\<add></span></span>](add-of-declaredtypes-element.md)
