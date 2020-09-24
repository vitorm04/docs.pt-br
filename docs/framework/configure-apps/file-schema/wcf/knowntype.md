---
title: <knownType>
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: 6bb6a419d863172951d82a67de044cb8cfc30f49
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183787"
---
# \<knownType>

<span data-ttu-id="0db07-101">Especifica um tipo a ser usado pelo <xref:System.Runtime.Serialization.DataContractSerializer> durante a desserialização.</span><span class="sxs-lookup"><span data-stu-id="0db07-101">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="0db07-102">O elemento especifica um "tipo conhecido" que é retornado por um campo ou propriedade de um "tipo declarado".</span><span class="sxs-lookup"><span data-stu-id="0db07-102">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="0db07-103">Para obter mais informações, consulte [tipos conhecidos de contrato de dados](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="0db07-103">For more information, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-of-declaredtypes-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<knownType>**  
  
## <a name="syntax"></a><span data-ttu-id="0db07-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0db07-104">Syntax</span></span>  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a><span data-ttu-id="0db07-105">Tipo</span><span class="sxs-lookup"><span data-stu-id="0db07-105">Type</span></span>  

 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0db07-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0db07-106">Attributes and Elements</span></span>  

 <span data-ttu-id="0db07-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0db07-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0db07-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="0db07-108">Attributes</span></span>  
  
|<span data-ttu-id="0db07-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="0db07-109">Attribute</span></span>|<span data-ttu-id="0db07-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="0db07-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0db07-111">type</span><span class="sxs-lookup"><span data-stu-id="0db07-111">type</span></span>|<span data-ttu-id="0db07-112">Especifica o tipo (incluindo o namespace), o nome do assembly, a versão, a cultura e o token de chave pública.</span><span class="sxs-lookup"><span data-stu-id="0db07-112">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0db07-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0db07-113">Child Elements</span></span>  
  
|<span data-ttu-id="0db07-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="0db07-114">Element</span></span>|<span data-ttu-id="0db07-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="0db07-115">Description</span></span>|  
|-------------|-----------------|  
|[\<parameter>](parameter.md)|<span data-ttu-id="0db07-116">Especifica um índice de parâmetro quando o tipo declarado é um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="0db07-116">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0db07-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0db07-117">Parent Elements</span></span>  
  
|<span data-ttu-id="0db07-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="0db07-118">Element</span></span>|<span data-ttu-id="0db07-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="0db07-119">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-declaredtypes-element.md)|<span data-ttu-id="0db07-120">Adiciona um tipo declarado à coleção de tipos declarados.</span><span class="sxs-lookup"><span data-stu-id="0db07-120">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0db07-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="0db07-121">Remarks</span></span>  

 <span data-ttu-id="0db07-122">Para obter mais informações sobre tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../wcf/feature-details/data-contract-known-types.md) e <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="0db07-122">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="0db07-123">Consulte o [\<dataContractSerializer>](datacontractserializer-element.md) para obter um exemplo de como usar esse elemento.</span><span class="sxs-lookup"><span data-stu-id="0db07-123">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0db07-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0db07-124">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0db07-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="0db07-125">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="0db07-126">Tipos de contratos de dados conhecidos</span><span class="sxs-lookup"><span data-stu-id="0db07-126">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [\<add>](add-of-declaredtypes-element.md)
