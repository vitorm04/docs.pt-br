---
title: <add>do <declaredTypes> elemento
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
ms.openlocfilehash: 1ea008dcc72d555b00e9648ace95bb9522ffc2c8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920183"
---
# <a name="add-of-declaredtypes-element"></a><span data-ttu-id="88706-102">\<Adicionar > do \<elemento declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="88706-102">\<add> of \<declaredTypes> Element</span></span>
<span data-ttu-id="88706-103">Adiciona um tipo usado pelo durante <xref:System.Runtime.Serialization.DataContractSerializer> a desserialização.</span><span class="sxs-lookup"><span data-stu-id="88706-103">Adds a type used by the <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="88706-104">Cada tipo declarado inclui os tipos conhecidos que serão retornados como um campo ou Propriedade do tipo declarado.</span><span class="sxs-lookup"><span data-stu-id="88706-104">Each declared type includes the known types that will be returned as a field or property of the declared type.</span></span>  
  
 <span data-ttu-id="88706-105">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="88706-105">system.runtime.serialization</span></span>  
<span data-ttu-id="88706-106">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="88706-106">\<dataContractSerializer></span></span>  
<span data-ttu-id="88706-107">\<declaredTypes></span><span class="sxs-lookup"><span data-stu-id="88706-107">\<declaredTypes></span></span>  
<span data-ttu-id="88706-108">\<Adicionar > de \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="88706-108">\<add> of \<declaredTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88706-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="88706-109">Syntax</span></span>  
  
```xml  
<add type="String">
  <knownType type="String">
    <parameter index="Integer"
               type="String" />
  </knownType>
</add>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="88706-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="88706-110">Attributes and Elements</span></span>  
 <span data-ttu-id="88706-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="88706-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="88706-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="88706-112">Attributes</span></span>  
  
|<span data-ttu-id="88706-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="88706-113">Attribute</span></span>|<span data-ttu-id="88706-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="88706-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="88706-115">tipo</span><span class="sxs-lookup"><span data-stu-id="88706-115">type</span></span>|<span data-ttu-id="88706-116">Atributo de cadeia de caracteres obrigatório.</span><span class="sxs-lookup"><span data-stu-id="88706-116">Required string attribute.</span></span><br /><br /> <span data-ttu-id="88706-117">Especifica o nome do tipo (incluindo o namespace), o nome do assembly, o número de versão, a cultura e o token de chave pública.</span><span class="sxs-lookup"><span data-stu-id="88706-117">Specifies the type name (including namespace), assembly name, version number, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="88706-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="88706-118">Child Elements</span></span>  
  
|<span data-ttu-id="88706-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="88706-119">Element</span></span>|<span data-ttu-id="88706-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="88706-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="88706-121">\<knownType ></span><span class="sxs-lookup"><span data-stu-id="88706-121">\<knownType></span></span>](knowntype.md)|<span data-ttu-id="88706-122">Especifica o tipo conhecido para o tipo declarado que está sendo adicionado.</span><span class="sxs-lookup"><span data-stu-id="88706-122">Specifies the known type for the declared type that is being added.</span></span> <span data-ttu-id="88706-123">Se o tipo declarado for um tipo genérico, você também deverá adicionar um elemento de parâmetro ao `<knownType>` elemento para especificar qual parâmetro genérico é usado para retornar o tipo conhecido.</span><span class="sxs-lookup"><span data-stu-id="88706-123">If the declared type is a generic type, then you must also add a parameter element to the `<knownType>` element to specify which generic parameter is used to return the known type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="88706-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="88706-124">Parent Elements</span></span>  
  
|<span data-ttu-id="88706-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="88706-125">Element</span></span>|<span data-ttu-id="88706-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="88706-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="88706-127">\<declaredTypes></span><span class="sxs-lookup"><span data-stu-id="88706-127">\<declaredTypes></span></span>](declaredtypes.md)|<span data-ttu-id="88706-128">Contém os tipos que exigem tipos conhecidos durante a <xref:System.Runtime.Serialization.DataContractSerializer>desserialização pelo.</span><span class="sxs-lookup"><span data-stu-id="88706-128">Contains the types that require known types during deserialization by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88706-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="88706-129">Remarks</span></span>  
 <span data-ttu-id="88706-130">Para obter mais informações sobre tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../wcf/feature-details/data-contract-known-types.md) e. <xref:System.Runtime.Serialization.DataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="88706-130">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="88706-131">Consulte o [ \<> do DataContractSerializer](datacontractserializer-element.md) para obter um exemplo de como usar esse elemento.</span><span class="sxs-lookup"><span data-stu-id="88706-131">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="88706-132">Se você adicionar o <xref:System.Object> tipo como um `<declaredType>`, um <xref:System.Configuration.ConfigurationErrorsException> será lançado.</span><span class="sxs-lookup"><span data-stu-id="88706-132">If you add the <xref:System.Object> type as a `<declaredType>`, a <xref:System.Configuration.ConfigurationErrorsException> is thrown.</span></span> <span data-ttu-id="88706-133">Isso ocorre porque o <xref:System.Object> tipo não pode ser usado como um tipo declarado na configuração.</span><span class="sxs-lookup"><span data-stu-id="88706-133">This is because the <xref:System.Object> type cannot be used as a declared type in configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88706-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="88706-134">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="88706-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="88706-135">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="88706-136">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="88706-136">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="88706-137">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="88706-137">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="88706-138">\<Adicionar > de \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="88706-138">\<add> of \<declaredTypes></span></span>](add-of-declaredtypes-element.md)
