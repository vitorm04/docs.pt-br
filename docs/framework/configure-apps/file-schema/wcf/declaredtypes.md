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
ms.openlocfilehash: cef34a8836c7b17fe9a85cac190090f42653df14
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919249"
---
# <a name="declaredtypes"></a><span data-ttu-id="36f75-101">\<declaredTypes></span><span class="sxs-lookup"><span data-stu-id="36f75-101">\<declaredTypes></span></span>
<span data-ttu-id="36f75-102">Contém os tipos conhecidos que o <xref:System.Runtime.Serialization.DataContractSerializer> usa ao desserializar.</span><span class="sxs-lookup"><span data-stu-id="36f75-102">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span>  
  
 <span data-ttu-id="36f75-103">Para obter mais informações sobre contratos de dados e tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="36f75-103">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="36f75-104">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="36f75-104">system.runtime.serialization</span></span>  
<span data-ttu-id="36f75-105">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="36f75-105">\<dataContractSerializer></span></span>  
<span data-ttu-id="36f75-106">\<declaredTypes></span><span class="sxs-lookup"><span data-stu-id="36f75-106">\<declaredTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36f75-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="36f75-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="36f75-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="36f75-108">Attributes and Elements</span></span>  
 <span data-ttu-id="36f75-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="36f75-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="36f75-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="36f75-110">Attributes</span></span>  
 <span data-ttu-id="36f75-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="36f75-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="36f75-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="36f75-112">Child Elements</span></span>  
  
|<span data-ttu-id="36f75-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="36f75-113">Element</span></span>|<span data-ttu-id="36f75-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="36f75-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="36f75-115">\<add></span><span class="sxs-lookup"><span data-stu-id="36f75-115">\<add></span></span>](add-of-declaredtypes-element.md)|<span data-ttu-id="36f75-116">Adiciona tipos que exigem tipos conhecidos.</span><span class="sxs-lookup"><span data-stu-id="36f75-116">Adds types that require known types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="36f75-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="36f75-117">Parent Elements</span></span>  
  
|<span data-ttu-id="36f75-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="36f75-118">Element</span></span>|<span data-ttu-id="36f75-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="36f75-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="36f75-120">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="36f75-120">\<dataContractSerializer></span></span>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="36f75-121">Contém dados de configuração para <xref:System.Runtime.Serialization.DataContractSerializer>o.</span><span class="sxs-lookup"><span data-stu-id="36f75-121">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36f75-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="36f75-122">Remarks</span></span>  
 <span data-ttu-id="36f75-123">Para obter mais informações sobre tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../wcf/feature-details/data-contract-known-types.md) e. <xref:System.Runtime.Serialization.DataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="36f75-123">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36f75-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="36f75-124">Example</span></span>  
 <span data-ttu-id="36f75-125">O código XML a seguir mostra tipos declarados e tipos conhecidos `DataContractSerializer` adicionados a um elemento.</span><span class="sxs-lookup"><span data-stu-id="36f75-125">The following XML code shows declared types and known types added to a `DataContractSerializer` element.</span></span> <span data-ttu-id="36f75-126">O exemplo mostra três tipos que estão sendo adicionados.</span><span class="sxs-lookup"><span data-stu-id="36f75-126">The example shows three types being added.</span></span> <span data-ttu-id="36f75-127">O primeiro é um tipo personalizado chamado "Orders" que usa um tipo conhecido chamado "item".</span><span class="sxs-lookup"><span data-stu-id="36f75-127">The first is a custom type named "Orders" that uses a known type named "Item".</span></span> <span data-ttu-id="36f75-128">O segundo tipo declarado é um <xref:System.Collections.Generic.List%601> que usa `Item` como um tipo conhecido.</span><span class="sxs-lookup"><span data-stu-id="36f75-128">The second declared type is a <xref:System.Collections.Generic.List%601> that uses `Item` as a known type.</span></span> <span data-ttu-id="36f75-129">Por fim, o terceiro tipo declarado <xref:System.Collections.Generic.Dictionary%602>é um.</span><span class="sxs-lookup"><span data-stu-id="36f75-129">Finally the third declared type is a <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="36f75-130">O <xref:System.Collections.Generic.Dictionary%602> tipo de classe é um tipo genérico, com dois parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="36f75-130">The <xref:System.Collections.Generic.Dictionary%602> class type is a generic type, with two type parameters.</span></span> <span data-ttu-id="36f75-131">O primeiro representa a chave e a segunda representa o valor.</span><span class="sxs-lookup"><span data-stu-id="36f75-131">The first represents the key and the second represents the value.</span></span> <span data-ttu-id="36f75-132">O exemplo a seguir adiciona <xref:System.Collections.Generic.List%601> um do segundo tipo (o valor) à lista de tipos conhecidos.</span><span class="sxs-lookup"><span data-stu-id="36f75-132">The following example adds a <xref:System.Collections.Generic.List%601> of the second type (the value) to the list of known types.</span></span> <span data-ttu-id="36f75-133">Você deve usar o `index` atributo para especificar o parâmetro de tipo a ser usado no tipo conhecido.</span><span class="sxs-lookup"><span data-stu-id="36f75-133">You must use the `index` attribute to specify which type parameter to use in the known type.</span></span> <span data-ttu-id="36f75-134">Nesse caso, o tipo de valor é indicado pelo atributo de índice definido como "1" (a coleção é baseada em zero).</span><span class="sxs-lookup"><span data-stu-id="36f75-134">In this case, the value type is indicated by the index attribute set to "1" (the collection is zero-based).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="36f75-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36f75-135">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="36f75-136">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="36f75-136">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="36f75-137">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="36f75-137">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="36f75-138">\<add></span><span class="sxs-lookup"><span data-stu-id="36f75-138">\<add></span></span>](add-of-declaredtypes-element.md)
