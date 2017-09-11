---
title: Elemento &lt;Field&gt; (.NET Nativo)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a14125f-1a8d-41a1-8a32-659ca0ad12de
caps.latest.revision: 9
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 84b0e28fb09f730999a8cad6e5002338957ef6a2
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="ltfieldgt-element-net-native"></a><span data-ttu-id="d1b45-102">Elemento &lt;Field&gt; (.NET Nativo)</span><span class="sxs-lookup"><span data-stu-id="d1b45-102">&lt;Field&gt; Element (.NET Native)</span></span>
<span data-ttu-id="d1b45-103">Aplica a política de reflexão do tempo de execução a um campo.</span><span class="sxs-lookup"><span data-stu-id="d1b45-103">Applies runtime reflection policy to a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1b45-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d1b45-104">Syntax</span></span>  
  
```xml  
<Field Name="field_name"  
       Browse="policy_type"  
       Dynamic="policy_type"  
       Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1b45-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d1b45-105">Attributes and Elements</span></span>  
 <span data-ttu-id="d1b45-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d1b45-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1b45-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="d1b45-107">Attributes</span></span>  
  
|<span data-ttu-id="d1b45-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="d1b45-108">Attribute</span></span>|<span data-ttu-id="d1b45-109">Tipo de atributo</span><span class="sxs-lookup"><span data-stu-id="d1b45-109">Attribute type</span></span>|<span data-ttu-id="d1b45-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="d1b45-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="d1b45-111">Geral</span><span class="sxs-lookup"><span data-stu-id="d1b45-111">General</span></span>|<span data-ttu-id="d1b45-112">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="d1b45-112">Required attribute.</span></span> <span data-ttu-id="d1b45-113">Especifica o nome do campo.</span><span class="sxs-lookup"><span data-stu-id="d1b45-113">Specifies the field name.</span></span>|  
|`Browse`|<span data-ttu-id="d1b45-114">Reflexão</span><span class="sxs-lookup"><span data-stu-id="d1b45-114">Reflection</span></span>|<span data-ttu-id="d1b45-115">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="d1b45-115">Optional attribute.</span></span> <span data-ttu-id="d1b45-116">Controla consultas para obter informações sobre o campo ou para enumerá-lo, mas não permite qualquer acesso dinâmico no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d1b45-116">Controls querying for information about or enumerating the field but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="d1b45-117">Reflexão</span><span class="sxs-lookup"><span data-stu-id="d1b45-117">Reflection</span></span>|<span data-ttu-id="d1b45-118">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="d1b45-118">Optional attribute.</span></span> <span data-ttu-id="d1b45-119">Controla o acesso do tempo de execução ao campo para habilitar programação dinâmica.</span><span class="sxs-lookup"><span data-stu-id="d1b45-119">Controls runtime access to the field to enable dynamic programming.</span></span> <span data-ttu-id="d1b45-120">Essa política garante que um campo pode ser definido ou recuperado dinamicamente no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d1b45-120">This policy ensures that a field can be set or retrieved dynamically at run time.</span></span>|  
|`Serialize`|<span data-ttu-id="d1b45-121">Serialização</span><span class="sxs-lookup"><span data-stu-id="d1b45-121">Serialization</span></span>|<span data-ttu-id="d1b45-122">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="d1b45-122">Optional attribute.</span></span> <span data-ttu-id="d1b45-123">Controla o acesso do tempo de execução a um campo para habilitar as instâncias de tipo a serem serializadas por bibliotecas como o serializador Newtonsoft JSON ou a ser usado para a associação de dados.</span><span class="sxs-lookup"><span data-stu-id="d1b45-123">Controls runtime access to a field to enable type instances to be serialized by libraries such as the Newtonsoft JSON serializer or to be used for data binding.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="d1b45-124">Atributo de nome</span><span class="sxs-lookup"><span data-stu-id="d1b45-124">Name attribute</span></span>  
  
|<span data-ttu-id="d1b45-125">Valor</span><span class="sxs-lookup"><span data-stu-id="d1b45-125">Value</span></span>|<span data-ttu-id="d1b45-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="d1b45-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d1b45-127">*method_name*</span><span class="sxs-lookup"><span data-stu-id="d1b45-127">*method_name*</span></span>|<span data-ttu-id="d1b45-128">O nome do campo.</span><span class="sxs-lookup"><span data-stu-id="d1b45-128">The field name.</span></span> <span data-ttu-id="d1b45-129">O tipo do campo é definido pelo elemento pai [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) ou [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="d1b45-129">The type of the field is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="d1b45-130">Todos os outros atributos</span><span class="sxs-lookup"><span data-stu-id="d1b45-130">All other attributes</span></span>  
  
|<span data-ttu-id="d1b45-131">Valor</span><span class="sxs-lookup"><span data-stu-id="d1b45-131">Value</span></span>|<span data-ttu-id="d1b45-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="d1b45-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d1b45-133">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="d1b45-133">*policy_setting*</span></span>|<span data-ttu-id="d1b45-134">A configuração a ser aplicada a este tipo de política para o campo.</span><span class="sxs-lookup"><span data-stu-id="d1b45-134">The setting to apply to this policy type for the field.</span></span> <span data-ttu-id="d1b45-135">Os valores possíveis são `Auto`, `Excluded`, `Included` e `Required`.</span><span class="sxs-lookup"><span data-stu-id="d1b45-135">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="d1b45-136">Para obter mais informações, consulte [Configurações da política da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="d1b45-136">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d1b45-137">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d1b45-137">Child Elements</span></span>  
 <span data-ttu-id="d1b45-138">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="d1b45-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d1b45-139">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d1b45-139">Parent Elements</span></span>  
  
|<span data-ttu-id="d1b45-140">Elemento</span><span class="sxs-lookup"><span data-stu-id="d1b45-140">Element</span></span>|<span data-ttu-id="d1b45-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="d1b45-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d1b45-142">\<Type></span><span class="sxs-lookup"><span data-stu-id="d1b45-142">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="d1b45-143">Aplica a política de reflexão a um tipo e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="d1b45-143">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="d1b45-144">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="d1b45-144">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="d1b45-145">Aplica a política de reflexão a um tipo genérico construído e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="d1b45-145">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1b45-146">Comentários</span><span class="sxs-lookup"><span data-stu-id="d1b45-146">Remarks</span></span>  
 <span data-ttu-id="d1b45-147">Se a política do campo não for definida explicitamente, ele herdará a política de tempo de execução do seu elemento pai.</span><span class="sxs-lookup"><span data-stu-id="d1b45-147">If a field's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1b45-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d1b45-148">See Also</span></span>  
 <span data-ttu-id="d1b45-149">[Elementos da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-elements.md) </span><span class="sxs-lookup"><span data-stu-id="d1b45-149">[Runtime Directive Elements](../../../docs/framework/net-native/runtime-directive-elements.md) </span></span>  
 <span data-ttu-id="d1b45-150">[Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) </span><span class="sxs-lookup"><span data-stu-id="d1b45-150">[Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) </span></span>  
 [<span data-ttu-id="d1b45-151">Configurações da política da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="d1b45-151">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)

