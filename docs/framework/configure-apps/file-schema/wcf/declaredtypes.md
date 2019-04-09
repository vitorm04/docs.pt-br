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
ms.openlocfilehash: 8919ee717012f8badcf7015bf8d850ed431c5943
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090271"
---
# <a name="declaredtypes"></a><span data-ttu-id="377bf-101">\<declaredTypes></span><span class="sxs-lookup"><span data-stu-id="377bf-101">\<declaredTypes></span></span>
<span data-ttu-id="377bf-102">Contém tipos conhecidos de que o <xref:System.Runtime.Serialization.DataContractSerializer> usa durante a desserialização.</span><span class="sxs-lookup"><span data-stu-id="377bf-102">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span>  
  
 <span data-ttu-id="377bf-103">Para obter mais informações sobre contratos de dados e tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="377bf-103">For more information about data contracts and known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="377bf-104">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="377bf-104">system.runtime.serialization</span></span>  
<span data-ttu-id="377bf-105">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="377bf-105">\<dataContractSerializer></span></span>  
<span data-ttu-id="377bf-106">\<declaredTypes></span><span class="sxs-lookup"><span data-stu-id="377bf-106">\<declaredTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="377bf-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="377bf-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="377bf-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="377bf-108">Attributes and Elements</span></span>  
 <span data-ttu-id="377bf-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="377bf-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="377bf-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="377bf-110">Attributes</span></span>  
 <span data-ttu-id="377bf-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="377bf-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="377bf-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="377bf-112">Child Elements</span></span>  
  
|<span data-ttu-id="377bf-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="377bf-113">Element</span></span>|<span data-ttu-id="377bf-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="377bf-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="377bf-115">\<add></span><span class="sxs-lookup"><span data-stu-id="377bf-115">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="377bf-116">Adiciona tipos que exigem tipos conhecidos.</span><span class="sxs-lookup"><span data-stu-id="377bf-116">Adds types that require known types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="377bf-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="377bf-117">Parent Elements</span></span>  
  
|<span data-ttu-id="377bf-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="377bf-118">Element</span></span>|<span data-ttu-id="377bf-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="377bf-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="377bf-120">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="377bf-120">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="377bf-121">Contém dados de configuração para o <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="377bf-121">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="377bf-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="377bf-122">Remarks</span></span>  
 <span data-ttu-id="377bf-123">Para obter mais informações sobre tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) e <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="377bf-123">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="377bf-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="377bf-124">Example</span></span>  
 <span data-ttu-id="377bf-125">O código XML a seguir mostra tipos declarados e tipos conhecidos adicionados a um `DataContractSerializer` elemento.</span><span class="sxs-lookup"><span data-stu-id="377bf-125">The following XML code shows declared types and known types added to a `DataContractSerializer` element.</span></span> <span data-ttu-id="377bf-126">O exemplo mostra três tipos que está sendo adicionados.</span><span class="sxs-lookup"><span data-stu-id="377bf-126">The example shows three types being added.</span></span> <span data-ttu-id="377bf-127">A primeira é um tipo personalizado chamado "Orders" que usa um tipo conhecido chamado "Item".</span><span class="sxs-lookup"><span data-stu-id="377bf-127">The first is a custom type named "Orders" that uses a known type named "Item".</span></span> <span data-ttu-id="377bf-128">O segundo declarado o tipo é um <xref:System.Collections.Generic.List%601> que usa `Item` como um tipo conhecido.</span><span class="sxs-lookup"><span data-stu-id="377bf-128">The second declared type is a <xref:System.Collections.Generic.List%601> that uses `Item` as a known type.</span></span> <span data-ttu-id="377bf-129">Finalmente o terceiro declarado o tipo é um <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="377bf-129">Finally the third declared type is a <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="377bf-130">O <xref:System.Collections.Generic.Dictionary%602> tipo de classe é um tipo genérico, com dois parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="377bf-130">The <xref:System.Collections.Generic.Dictionary%602> class type is a generic type, with two type parameters.</span></span> <span data-ttu-id="377bf-131">O primeiro representa a chave e a segunda representa o valor.</span><span class="sxs-lookup"><span data-stu-id="377bf-131">The first represents the key and the second represents the value.</span></span> <span data-ttu-id="377bf-132">O exemplo a seguir adiciona um <xref:System.Collections.Generic.List%601> do segundo tipo (o valor) à lista de tipos conhecidos.</span><span class="sxs-lookup"><span data-stu-id="377bf-132">The following example adds a <xref:System.Collections.Generic.List%601> of the second type (the value) to the list of known types.</span></span> <span data-ttu-id="377bf-133">Você deve usar o `index` atributo para especificar qual parâmetro de tipo para usar o tipo conhecido.</span><span class="sxs-lookup"><span data-stu-id="377bf-133">You must use the `index` attribute to specify which type parameter to use in the known type.</span></span> <span data-ttu-id="377bf-134">Nesse caso, o tipo de valor é indicado pelo atributo índice definido como "1" (a coleção é baseado em zero).</span><span class="sxs-lookup"><span data-stu-id="377bf-134">In this case, the value type is indicated by the index attribute set to "1" (the collection is zero-based).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="377bf-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="377bf-135">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="377bf-136">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="377bf-136">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)
- [<span data-ttu-id="377bf-137">Tipos de contratos de dados conhecidos</span><span class="sxs-lookup"><span data-stu-id="377bf-137">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="377bf-138">\<add></span><span class="sxs-lookup"><span data-stu-id="377bf-138">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
