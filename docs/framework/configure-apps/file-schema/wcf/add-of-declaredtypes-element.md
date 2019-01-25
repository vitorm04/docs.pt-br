---
title: '&lt;adicionar&gt; elemento &lt;declaredTypes&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
ms.openlocfilehash: dd5972c2bb25367f2566bcf77e53e7a3341d89b4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54519457"
---
# <a name="ltaddgt-of-ltdeclaredtypesgt-element"></a><span data-ttu-id="96a14-102">&lt;adicionar&gt; elemento &lt;declaredTypes&gt;</span><span class="sxs-lookup"><span data-stu-id="96a14-102">&lt;add&gt; of &lt;declaredTypes&gt; Element</span></span>
<span data-ttu-id="96a14-103">Adiciona um tipo usado pelo <xref:System.Runtime.Serialization.DataContractSerializer> durante a desserialização.</span><span class="sxs-lookup"><span data-stu-id="96a14-103">Adds a type used by the <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="96a14-104">Cada tipo declarado inclui os tipos conhecidos que serão retornados como um campo ou propriedade do tipo declarado.</span><span class="sxs-lookup"><span data-stu-id="96a14-104">Each declared type includes the known types that will be returned as a field or property of the declared type.</span></span>  
  
 <span data-ttu-id="96a14-105">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="96a14-105">system.runtime.serialization</span></span>  
<span data-ttu-id="96a14-106">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="96a14-106">\<dataContractSerializer></span></span>  
<span data-ttu-id="96a14-107">\<declaredTypes></span><span class="sxs-lookup"><span data-stu-id="96a14-107">\<declaredTypes></span></span>  
<span data-ttu-id="96a14-108">\<Adicionar > de \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="96a14-108">\<add> of \<declaredTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96a14-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="96a14-109">Syntax</span></span>  
  
```xml  
<add type="String">
  <knownType type="String">
    <parameter index="Integer"
               type="String" />
  </knownType>
</add>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="96a14-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="96a14-110">Attributes and Elements</span></span>  
 <span data-ttu-id="96a14-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="96a14-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="96a14-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="96a14-112">Attributes</span></span>  
  
|<span data-ttu-id="96a14-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="96a14-113">Attribute</span></span>|<span data-ttu-id="96a14-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="96a14-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="96a14-115">tipo</span><span class="sxs-lookup"><span data-stu-id="96a14-115">type</span></span>|<span data-ttu-id="96a14-116">Atributo de cadeia de caracteres obrigatório.</span><span class="sxs-lookup"><span data-stu-id="96a14-116">Required string attribute.</span></span><br /><br /> <span data-ttu-id="96a14-117">Especifica o nome do tipo (incluindo namespace) nome do assembly, número de versão, cultura e token de chave pública.</span><span class="sxs-lookup"><span data-stu-id="96a14-117">Specifies the type name (including namespace), assembly name, version number, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="96a14-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="96a14-118">Child Elements</span></span>  
  
|<span data-ttu-id="96a14-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="96a14-119">Element</span></span>|<span data-ttu-id="96a14-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="96a14-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96a14-121">\<knownType></span><span class="sxs-lookup"><span data-stu-id="96a14-121">\<knownType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|<span data-ttu-id="96a14-122">Especifica o tipo conhecido para o tipo declarado que está sendo adicionado.</span><span class="sxs-lookup"><span data-stu-id="96a14-122">Specifies the known type for the declared type that is being added.</span></span> <span data-ttu-id="96a14-123">Se o tipo declarado é um tipo genérico e, em seguida, você também deve adicionar um elemento de parâmetro para o `<knownType>` elemento para especificar qual parâmetro genérico é usado para retornar o tipo conhecido.</span><span class="sxs-lookup"><span data-stu-id="96a14-123">If the declared type is a generic type, then you must also add a parameter element to the `<knownType>` element to specify which generic parameter is used to return the known type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="96a14-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="96a14-124">Parent Elements</span></span>  
  
|<span data-ttu-id="96a14-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="96a14-125">Element</span></span>|<span data-ttu-id="96a14-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="96a14-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96a14-127">\<declaredTypes></span><span class="sxs-lookup"><span data-stu-id="96a14-127">\<declaredTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/declaredtypes.md)|<span data-ttu-id="96a14-128">Contém os tipos que exigem tipos conhecidos durante a desserialização, o <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="96a14-128">Contains the types that require known types during deserialization by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96a14-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="96a14-129">Remarks</span></span>  
 <span data-ttu-id="96a14-130">Para obter mais informações sobre tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) e <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="96a14-130">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="96a14-131">Consulte a [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) para obter um exemplo de como usar esse elemento.</span><span class="sxs-lookup"><span data-stu-id="96a14-131">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="96a14-132">Se você adicionar o <xref:System.Object> digitar como uma `<declaredType>`, um <xref:System.Configuration.ConfigurationErrorsException> é gerada.</span><span class="sxs-lookup"><span data-stu-id="96a14-132">If you add the <xref:System.Object> type as a `<declaredType>`, a <xref:System.Configuration.ConfigurationErrorsException> is thrown.</span></span> <span data-ttu-id="96a14-133">Isso ocorre porque o <xref:System.Object> tipo não pode ser usado como um tipo declarado na configuração.</span><span class="sxs-lookup"><span data-stu-id="96a14-133">This is because the <xref:System.Object> type cannot be used as a declared type in configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96a14-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="96a14-134">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="96a14-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96a14-135">See also</span></span>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="96a14-136">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="96a14-136">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="96a14-137">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="96a14-137">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)
- [<span data-ttu-id="96a14-138">\<Adicionar > de \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="96a14-138">\<add> of \<declaredTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
