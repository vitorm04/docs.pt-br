---
title: '&lt;declaredTypes&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dataContractSerializer element
- declaredTypes element
- DataContractSerializer
- KnownTypes
- <declaredTypes> element
ms.assetid: f35184e4-9d9e-4d37-8fb4-d5b58220eb3e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 80a2959395cf8f10ae8c5bc2ccd47ea97ffdaa30
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltdeclaredtypesgt"></a><span data-ttu-id="3e0bf-102">&lt;declaredTypes&gt;</span><span class="sxs-lookup"><span data-stu-id="3e0bf-102">&lt;declaredTypes&gt;</span></span>
<span data-ttu-id="3e0bf-103">Contém de tipos conhecidos que o <xref:System.Runtime.Serialization.DataContractSerializer> usa durante a desserialização.</span><span class="sxs-lookup"><span data-stu-id="3e0bf-103">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span>  
  
 <span data-ttu-id="3e0bf-104">Para obter mais informações sobre contratos de dados e tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="3e0bf-104">For more information about data contracts and known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="3e0bf-105">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="3e0bf-105">system.runtime.serialization</span></span>  
<span data-ttu-id="3e0bf-106">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="3e0bf-106">\<dataContractSerializer></span></span>  
<span data-ttu-id="3e0bf-107">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="3e0bf-107">\<declaredTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e0bf-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3e0bf-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e0bf-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3e0bf-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3e0bf-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3e0bf-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e0bf-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="3e0bf-111">Attributes</span></span>  
 <span data-ttu-id="3e0bf-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="3e0bf-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3e0bf-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3e0bf-113">Child Elements</span></span>  
  
|<span data-ttu-id="3e0bf-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="3e0bf-114">Element</span></span>|<span data-ttu-id="3e0bf-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="3e0bf-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3e0bf-116">\<add></span><span class="sxs-lookup"><span data-stu-id="3e0bf-116">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="3e0bf-117">Adiciona tipos que exigem tipos conhecidos.</span><span class="sxs-lookup"><span data-stu-id="3e0bf-117">Adds types that require known types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3e0bf-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3e0bf-118">Parent Elements</span></span>  
  
|<span data-ttu-id="3e0bf-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="3e0bf-119">Element</span></span>|<span data-ttu-id="3e0bf-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="3e0bf-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3e0bf-121">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="3e0bf-121">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="3e0bf-122">Contém dados de configuração para o <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="3e0bf-122">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e0bf-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="3e0bf-123">Remarks</span></span>  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]<span data-ttu-id="3e0bf-124">tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) e <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="3e0bf-124"> known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e0bf-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3e0bf-125">Example</span></span>  
 <span data-ttu-id="3e0bf-126">O código XML a seguir mostra tipos declarados e tipos conhecidos adicionados a um `DataContractSerializer` elemento.</span><span class="sxs-lookup"><span data-stu-id="3e0bf-126">The following XML code shows declared types and known types added to a `DataContractSerializer` element.</span></span> <span data-ttu-id="3e0bf-127">O exemplo mostra três tipos que está sendo adicionados.</span><span class="sxs-lookup"><span data-stu-id="3e0bf-127">The example shows three types being added.</span></span> <span data-ttu-id="3e0bf-128">A primeira é um tipo personalizado chamado "Orders" que usa um tipo conhecido chamado "Item".</span><span class="sxs-lookup"><span data-stu-id="3e0bf-128">The first is a custom type named "Orders" that uses a known type named "Item".</span></span> <span data-ttu-id="3e0bf-129">O segundo declarado de tipo é um <xref:System.Collections.Generic.List%601> que usa `Item` como um tipo conhecido.</span><span class="sxs-lookup"><span data-stu-id="3e0bf-129">The second declared type is a <xref:System.Collections.Generic.List%601> that uses `Item` as a known type.</span></span> <span data-ttu-id="3e0bf-130">Finalmente a terceira declarado de tipo é um <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="3e0bf-130">Finally the third declared type is a <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="3e0bf-131">O <xref:System.Collections.Generic.Dictionary%602> tipo de classe é um tipo genérico, com parâmetros de tipo de dois.</span><span class="sxs-lookup"><span data-stu-id="3e0bf-131">The <xref:System.Collections.Generic.Dictionary%602> class type is a generic type, with two type parameters.</span></span> <span data-ttu-id="3e0bf-132">A primeira representa a chave e a segunda representa o valor.</span><span class="sxs-lookup"><span data-stu-id="3e0bf-132">The first represents the key and the second represents the value.</span></span> <span data-ttu-id="3e0bf-133">O exemplo a seguir adiciona um <xref:System.Collections.Generic.List%601> do segundo tipo (valor) à lista de tipos conhecidos.</span><span class="sxs-lookup"><span data-stu-id="3e0bf-133">The following example adds a <xref:System.Collections.Generic.List%601> of the second type (the value) to the list of known types.</span></span> <span data-ttu-id="3e0bf-134">Você deve usar o `index` atributo para especificar o parâmetro de tipo para usar o tipo conhecido.</span><span class="sxs-lookup"><span data-stu-id="3e0bf-134">You must use the `index` attribute to specify which type parameter to use in the known type.</span></span> <span data-ttu-id="3e0bf-135">Nesse caso, o tipo de valor é indicado pelo índice de atributo definido como "1" (a coleção é baseado em zero).</span><span class="sxs-lookup"><span data-stu-id="3e0bf-135">In this case, the value type is indicated by the index attribute set to "1" (the collection is zero-based).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3e0bf-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e0bf-136">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="3e0bf-137">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="3e0bf-137">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="3e0bf-138">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="3e0bf-138">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="3e0bf-139">\<add></span><span class="sxs-lookup"><span data-stu-id="3e0bf-139">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
