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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398059"
---
# \<declaredTypes>
<span data-ttu-id="51b80-101">Contém os tipos conhecidos que o <xref:System.Runtime.Serialization.DataContractSerializer> usa ao desserializar.</span><span class="sxs-lookup"><span data-stu-id="51b80-101">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span>  
  
 <span data-ttu-id="51b80-102">Para obter mais informações sobre contratos de dados e tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="51b80-102">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<declaredTypes>**  
  
## <a name="syntax"></a><span data-ttu-id="51b80-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="51b80-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="51b80-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="51b80-104">Attributes and Elements</span></span>  
 <span data-ttu-id="51b80-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="51b80-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="51b80-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="51b80-106">Attributes</span></span>  
 <span data-ttu-id="51b80-107">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="51b80-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="51b80-108">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="51b80-108">Child Elements</span></span>  
  
|<span data-ttu-id="51b80-109">Elemento</span><span class="sxs-lookup"><span data-stu-id="51b80-109">Element</span></span>|<span data-ttu-id="51b80-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="51b80-110">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-declaredtypes-element.md)|<span data-ttu-id="51b80-111">Adiciona tipos que exigem tipos conhecidos.</span><span class="sxs-lookup"><span data-stu-id="51b80-111">Adds types that require known types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="51b80-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="51b80-112">Parent Elements</span></span>  
  
|<span data-ttu-id="51b80-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="51b80-113">Element</span></span>|<span data-ttu-id="51b80-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="51b80-114">Description</span></span>|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="51b80-115">Contém dados de configuração para o <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="51b80-115">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51b80-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="51b80-116">Remarks</span></span>  
 <span data-ttu-id="51b80-117">Para obter mais informações sobre tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../wcf/feature-details/data-contract-known-types.md) e <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="51b80-117">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51b80-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="51b80-118">Example</span></span>  
 <span data-ttu-id="51b80-119">O código XML a seguir mostra tipos declarados e tipos conhecidos adicionados a um `DataContractSerializer` elemento.</span><span class="sxs-lookup"><span data-stu-id="51b80-119">The following XML code shows declared types and known types added to a `DataContractSerializer` element.</span></span> <span data-ttu-id="51b80-120">O exemplo mostra três tipos que estão sendo adicionados.</span><span class="sxs-lookup"><span data-stu-id="51b80-120">The example shows three types being added.</span></span> <span data-ttu-id="51b80-121">O primeiro é um tipo personalizado chamado "Orders" que usa um tipo conhecido chamado "item".</span><span class="sxs-lookup"><span data-stu-id="51b80-121">The first is a custom type named "Orders" that uses a known type named "Item".</span></span> <span data-ttu-id="51b80-122">O segundo tipo declarado é um <xref:System.Collections.Generic.List%601> que usa `Item` como um tipo conhecido.</span><span class="sxs-lookup"><span data-stu-id="51b80-122">The second declared type is a <xref:System.Collections.Generic.List%601> that uses `Item` as a known type.</span></span> <span data-ttu-id="51b80-123">Por fim, o terceiro tipo declarado é um <xref:System.Collections.Generic.Dictionary%602> .</span><span class="sxs-lookup"><span data-stu-id="51b80-123">Finally the third declared type is a <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="51b80-124">O <xref:System.Collections.Generic.Dictionary%602> tipo de classe é um tipo genérico, com dois parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="51b80-124">The <xref:System.Collections.Generic.Dictionary%602> class type is a generic type, with two type parameters.</span></span> <span data-ttu-id="51b80-125">O primeiro representa a chave e a segunda representa o valor.</span><span class="sxs-lookup"><span data-stu-id="51b80-125">The first represents the key and the second represents the value.</span></span> <span data-ttu-id="51b80-126">O exemplo a seguir adiciona um <xref:System.Collections.Generic.List%601> do segundo tipo (o valor) à lista de tipos conhecidos.</span><span class="sxs-lookup"><span data-stu-id="51b80-126">The following example adds a <xref:System.Collections.Generic.List%601> of the second type (the value) to the list of known types.</span></span> <span data-ttu-id="51b80-127">Você deve usar o `index` atributo para especificar o parâmetro de tipo a ser usado no tipo conhecido.</span><span class="sxs-lookup"><span data-stu-id="51b80-127">You must use the `index` attribute to specify which type parameter to use in the known type.</span></span> <span data-ttu-id="51b80-128">Nesse caso, o tipo de valor é indicado pelo atributo de índice definido como "1" (a coleção é baseada em zero).</span><span class="sxs-lookup"><span data-stu-id="51b80-128">In this case, the value type is indicated by the index attribute set to "1" (the collection is zero-based).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="51b80-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="51b80-129">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [<span data-ttu-id="51b80-130">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="51b80-130">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<add>](add-of-declaredtypes-element.md)
