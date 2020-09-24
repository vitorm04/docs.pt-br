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
ms.openlocfilehash: 281d9d7d7e51a837de4f86f85472815956a20319
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153905"
---
# \<declaredTypes>

<span data-ttu-id="2c9d1-101">Contém os tipos conhecidos que o <xref:System.Runtime.Serialization.DataContractSerializer> usa ao desserializar.</span><span class="sxs-lookup"><span data-stu-id="2c9d1-101">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span>  
  
 <span data-ttu-id="2c9d1-102">Para obter mais informações sobre contratos de dados e tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="2c9d1-102">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<declaredTypes>**  
  
## <a name="syntax"></a><span data-ttu-id="2c9d1-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="2c9d1-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2c9d1-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2c9d1-104">Attributes and Elements</span></span>  

 <span data-ttu-id="2c9d1-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2c9d1-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2c9d1-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="2c9d1-106">Attributes</span></span>  

 <span data-ttu-id="2c9d1-107">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="2c9d1-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2c9d1-108">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2c9d1-108">Child Elements</span></span>  
  
|<span data-ttu-id="2c9d1-109">Elemento</span><span class="sxs-lookup"><span data-stu-id="2c9d1-109">Element</span></span>|<span data-ttu-id="2c9d1-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="2c9d1-110">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-declaredtypes-element.md)|<span data-ttu-id="2c9d1-111">Adiciona tipos que exigem tipos conhecidos.</span><span class="sxs-lookup"><span data-stu-id="2c9d1-111">Adds types that require known types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2c9d1-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2c9d1-112">Parent Elements</span></span>  
  
|<span data-ttu-id="2c9d1-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="2c9d1-113">Element</span></span>|<span data-ttu-id="2c9d1-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="2c9d1-114">Description</span></span>|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="2c9d1-115">Contém dados de configuração para o <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="2c9d1-115">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c9d1-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="2c9d1-116">Remarks</span></span>  

 <span data-ttu-id="2c9d1-117">Para obter mais informações sobre tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../wcf/feature-details/data-contract-known-types.md) e <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="2c9d1-117">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c9d1-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2c9d1-118">Example</span></span>  

 <span data-ttu-id="2c9d1-119">O código XML a seguir mostra tipos declarados e tipos conhecidos adicionados a um `DataContractSerializer` elemento.</span><span class="sxs-lookup"><span data-stu-id="2c9d1-119">The following XML code shows declared types and known types added to a `DataContractSerializer` element.</span></span> <span data-ttu-id="2c9d1-120">O exemplo mostra três tipos que estão sendo adicionados.</span><span class="sxs-lookup"><span data-stu-id="2c9d1-120">The example shows three types being added.</span></span> <span data-ttu-id="2c9d1-121">O primeiro é um tipo personalizado chamado "Orders" que usa um tipo conhecido chamado "item".</span><span class="sxs-lookup"><span data-stu-id="2c9d1-121">The first is a custom type named "Orders" that uses a known type named "Item".</span></span> <span data-ttu-id="2c9d1-122">O segundo tipo declarado é um <xref:System.Collections.Generic.List%601> que usa `Item` como um tipo conhecido.</span><span class="sxs-lookup"><span data-stu-id="2c9d1-122">The second declared type is a <xref:System.Collections.Generic.List%601> that uses `Item` as a known type.</span></span> <span data-ttu-id="2c9d1-123">Por fim, o terceiro tipo declarado é um <xref:System.Collections.Generic.Dictionary%602> .</span><span class="sxs-lookup"><span data-stu-id="2c9d1-123">Finally the third declared type is a <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="2c9d1-124">O <xref:System.Collections.Generic.Dictionary%602> tipo de classe é um tipo genérico, com dois parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="2c9d1-124">The <xref:System.Collections.Generic.Dictionary%602> class type is a generic type, with two type parameters.</span></span> <span data-ttu-id="2c9d1-125">O primeiro representa a chave e a segunda representa o valor.</span><span class="sxs-lookup"><span data-stu-id="2c9d1-125">The first represents the key and the second represents the value.</span></span> <span data-ttu-id="2c9d1-126">O exemplo a seguir adiciona um <xref:System.Collections.Generic.List%601> do segundo tipo (o valor) à lista de tipos conhecidos.</span><span class="sxs-lookup"><span data-stu-id="2c9d1-126">The following example adds a <xref:System.Collections.Generic.List%601> of the second type (the value) to the list of known types.</span></span> <span data-ttu-id="2c9d1-127">Você deve usar o `index` atributo para especificar o parâmetro de tipo a ser usado no tipo conhecido.</span><span class="sxs-lookup"><span data-stu-id="2c9d1-127">You must use the `index` attribute to specify which type parameter to use in the known type.</span></span> <span data-ttu-id="2c9d1-128">Nesse caso, o tipo de valor é indicado pelo atributo de índice definido como "1" (a coleção é baseada em zero).</span><span class="sxs-lookup"><span data-stu-id="2c9d1-128">In this case, the value type is indicated by the index attribute set to "1" (the collection is zero-based).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2c9d1-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="2c9d1-129">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [<span data-ttu-id="2c9d1-130">Tipos de contratos de dados conhecidos</span><span class="sxs-lookup"><span data-stu-id="2c9d1-130">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<add>](add-of-declaredtypes-element.md)
