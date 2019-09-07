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
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400651"
---
# <a name="add-of-declaredtypes-element"></a><span data-ttu-id="74f27-102">\<Adicionar > do \<elemento declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="74f27-102">\<add> of \<declaredTypes> Element</span></span>
<span data-ttu-id="74f27-103">Adiciona um tipo usado pelo durante <xref:System.Runtime.Serialization.DataContractSerializer> a desserialização.</span><span class="sxs-lookup"><span data-stu-id="74f27-103">Adds a type used by the <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="74f27-104">Cada tipo declarado inclui os tipos conhecidos que serão retornados como um campo ou Propriedade do tipo declarado.</span><span class="sxs-lookup"><span data-stu-id="74f27-104">Each declared type includes the known types that will be returned as a field or property of the declared type.</span></span>  
  
<span data-ttu-id="74f27-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="74f27-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="74f27-106">&nbsp;&nbsp;[ **\<> System. Runtime. Serialization**](system-runtime-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="74f27-106">&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)</span></span>\
<span data-ttu-id="74f27-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> do dataContractSerializer**](datacontractserializer.md)</span><span class="sxs-lookup"><span data-stu-id="74f27-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)</span></span>\
<span data-ttu-id="74f27-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> declaredTypes**](declaredtypes.md)</span><span class="sxs-lookup"><span data-stu-id="74f27-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)</span></span>\
<span data-ttu-id="74f27-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Adicionar >**</span><span class="sxs-lookup"><span data-stu-id="74f27-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74f27-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="74f27-110">Syntax</span></span>  
  
```xml  
<add type="String">
  <knownType type="String">
    <parameter index="Integer"
               type="String" />
  </knownType>
</add>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="74f27-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="74f27-111">Attributes and Elements</span></span>  
 <span data-ttu-id="74f27-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="74f27-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="74f27-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="74f27-113">Attributes</span></span>  
  
|<span data-ttu-id="74f27-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="74f27-114">Attribute</span></span>|<span data-ttu-id="74f27-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="74f27-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="74f27-116">tipo</span><span class="sxs-lookup"><span data-stu-id="74f27-116">type</span></span>|<span data-ttu-id="74f27-117">Atributo de cadeia de caracteres obrigatório.</span><span class="sxs-lookup"><span data-stu-id="74f27-117">Required string attribute.</span></span><br /><br /> <span data-ttu-id="74f27-118">Especifica o nome do tipo (incluindo o namespace), o nome do assembly, o número de versão, a cultura e o token de chave pública.</span><span class="sxs-lookup"><span data-stu-id="74f27-118">Specifies the type name (including namespace), assembly name, version number, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="74f27-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="74f27-119">Child Elements</span></span>  
  
|<span data-ttu-id="74f27-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="74f27-120">Element</span></span>|<span data-ttu-id="74f27-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="74f27-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="74f27-122">\<knownType ></span><span class="sxs-lookup"><span data-stu-id="74f27-122">\<knownType></span></span>](knowntype.md)|<span data-ttu-id="74f27-123">Especifica o tipo conhecido para o tipo declarado que está sendo adicionado.</span><span class="sxs-lookup"><span data-stu-id="74f27-123">Specifies the known type for the declared type that is being added.</span></span> <span data-ttu-id="74f27-124">Se o tipo declarado for um tipo genérico, você também deverá adicionar um elemento de parâmetro ao `<knownType>` elemento para especificar qual parâmetro genérico é usado para retornar o tipo conhecido.</span><span class="sxs-lookup"><span data-stu-id="74f27-124">If the declared type is a generic type, then you must also add a parameter element to the `<knownType>` element to specify which generic parameter is used to return the known type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="74f27-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="74f27-125">Parent Elements</span></span>  
  
|<span data-ttu-id="74f27-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="74f27-126">Element</span></span>|<span data-ttu-id="74f27-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="74f27-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="74f27-128">\<declaredTypes></span><span class="sxs-lookup"><span data-stu-id="74f27-128">\<declaredTypes></span></span>](declaredtypes.md)|<span data-ttu-id="74f27-129">Contém os tipos que exigem tipos conhecidos durante a <xref:System.Runtime.Serialization.DataContractSerializer>desserialização pelo.</span><span class="sxs-lookup"><span data-stu-id="74f27-129">Contains the types that require known types during deserialization by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74f27-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="74f27-130">Remarks</span></span>  
 <span data-ttu-id="74f27-131">Para obter mais informações sobre tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../wcf/feature-details/data-contract-known-types.md) e. <xref:System.Runtime.Serialization.DataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="74f27-131">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="74f27-132">Consulte o [ \<> do DataContractSerializer](datacontractserializer-element.md) para obter um exemplo de como usar esse elemento.</span><span class="sxs-lookup"><span data-stu-id="74f27-132">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="74f27-133">Se você adicionar o <xref:System.Object> tipo como um `<declaredType>`, um <xref:System.Configuration.ConfigurationErrorsException> será lançado.</span><span class="sxs-lookup"><span data-stu-id="74f27-133">If you add the <xref:System.Object> type as a `<declaredType>`, a <xref:System.Configuration.ConfigurationErrorsException> is thrown.</span></span> <span data-ttu-id="74f27-134">Isso ocorre porque o <xref:System.Object> tipo não pode ser usado como um tipo declarado na configuração.</span><span class="sxs-lookup"><span data-stu-id="74f27-134">This is because the <xref:System.Object> type cannot be used as a declared type in configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74f27-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="74f27-135">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="74f27-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="74f27-136">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="74f27-137">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="74f27-137">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="74f27-138">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="74f27-138">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="74f27-139">\<Adicionar > de \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="74f27-139">\<add> of \<declaredTypes></span></span>](add-of-declaredtypes-element.md)
