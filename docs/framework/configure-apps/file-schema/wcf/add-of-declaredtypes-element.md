---
title: <add>do <declaredTypes> elemento
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
ms.openlocfilehash: a001e8743b2c24f68b1b23cbccf3e5ac162c4e71
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400651"
---
# <a name="add-of-declaredtypes-element"></a><span data-ttu-id="00dd7-102">\<add>do \<declaredTypes> elemento</span><span class="sxs-lookup"><span data-stu-id="00dd7-102">\<add> of \<declaredTypes> Element</span></span>
<span data-ttu-id="00dd7-103">Adiciona um tipo usado pelo <xref:System.Runtime.Serialization.DataContractSerializer> durante a desserialização.</span><span class="sxs-lookup"><span data-stu-id="00dd7-103">Adds a type used by the <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="00dd7-104">Cada tipo declarado inclui os tipos conhecidos que serão retornados como um campo ou Propriedade do tipo declarado.</span><span class="sxs-lookup"><span data-stu-id="00dd7-104">Each declared type includes the known types that will be returned as a field or property of the declared type.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="00dd7-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="00dd7-105">Syntax</span></span>  
  
```xml  
<add type="String">
  <knownType type="String">
    <parameter index="Integer"
               type="String" />
  </knownType>
</add>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="00dd7-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="00dd7-106">Attributes and Elements</span></span>  
 <span data-ttu-id="00dd7-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="00dd7-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="00dd7-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="00dd7-108">Attributes</span></span>  
  
|<span data-ttu-id="00dd7-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="00dd7-109">Attribute</span></span>|<span data-ttu-id="00dd7-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="00dd7-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="00dd7-111">type</span><span class="sxs-lookup"><span data-stu-id="00dd7-111">type</span></span>|<span data-ttu-id="00dd7-112">Atributo de cadeia de caracteres obrigatório.</span><span class="sxs-lookup"><span data-stu-id="00dd7-112">Required string attribute.</span></span><br /><br /> <span data-ttu-id="00dd7-113">Especifica o nome do tipo (incluindo o namespace), o nome do assembly, o número de versão, a cultura e o token de chave pública.</span><span class="sxs-lookup"><span data-stu-id="00dd7-113">Specifies the type name (including namespace), assembly name, version number, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="00dd7-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="00dd7-114">Child Elements</span></span>  
  
|<span data-ttu-id="00dd7-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="00dd7-115">Element</span></span>|<span data-ttu-id="00dd7-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="00dd7-116">Description</span></span>|  
|-------------|-----------------|  
|[\<knownType>](knowntype.md)|<span data-ttu-id="00dd7-117">Especifica o tipo conhecido para o tipo declarado que está sendo adicionado.</span><span class="sxs-lookup"><span data-stu-id="00dd7-117">Specifies the known type for the declared type that is being added.</span></span> <span data-ttu-id="00dd7-118">Se o tipo declarado for um tipo genérico, você também deverá adicionar um elemento de parâmetro ao `<knownType>` elemento para especificar qual parâmetro genérico é usado para retornar o tipo conhecido.</span><span class="sxs-lookup"><span data-stu-id="00dd7-118">If the declared type is a generic type, then you must also add a parameter element to the `<knownType>` element to specify which generic parameter is used to return the known type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="00dd7-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="00dd7-119">Parent Elements</span></span>  
  
|<span data-ttu-id="00dd7-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="00dd7-120">Element</span></span>|<span data-ttu-id="00dd7-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="00dd7-121">Description</span></span>|  
|-------------|-----------------|  
|[\<declaredTypes>](declaredtypes.md)|<span data-ttu-id="00dd7-122">Contém os tipos que exigem tipos conhecidos durante a desserialização pelo <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="00dd7-122">Contains the types that require known types during deserialization by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00dd7-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="00dd7-123">Remarks</span></span>  
 <span data-ttu-id="00dd7-124">Para obter mais informações sobre tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../wcf/feature-details/data-contract-known-types.md) e <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="00dd7-124">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="00dd7-125">Consulte o [\<dataContractSerializer>](datacontractserializer-element.md) para obter um exemplo de como usar esse elemento.</span><span class="sxs-lookup"><span data-stu-id="00dd7-125">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="00dd7-126">Se você adicionar o <xref:System.Object> tipo como um `<declaredType>` , um <xref:System.Configuration.ConfigurationErrorsException> será lançado.</span><span class="sxs-lookup"><span data-stu-id="00dd7-126">If you add the <xref:System.Object> type as a `<declaredType>`, a <xref:System.Configuration.ConfigurationErrorsException> is thrown.</span></span> <span data-ttu-id="00dd7-127">Isso ocorre porque o <xref:System.Object> tipo não pode ser usado como um tipo declarado na configuração.</span><span class="sxs-lookup"><span data-stu-id="00dd7-127">This is because the <xref:System.Object> type cannot be used as a declared type in configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00dd7-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="00dd7-128">Example</span></span>  
  
```xml  
<add type="MyCompany.Library.Shape,
           MyAssembly, Version=2.0.0.0, Culture=neutral,
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">
  <knownType type="MyCompany.Library.Circle,
                   MyAssembly, Version=2.0.0.0, Culture=neutral,
                   PublicKeyToken=XXXXXX,
                   processorArchitecture=MSIL" />
</add>
```  
  
## <a name="see-also"></a><span data-ttu-id="00dd7-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="00dd7-129">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="00dd7-130">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="00dd7-130">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [<span data-ttu-id="00dd7-131">\<add>desse\<declaredTypes></span><span class="sxs-lookup"><span data-stu-id="00dd7-131">\<add> of \<declaredTypes></span></span>](add-of-declaredtypes-element.md)
