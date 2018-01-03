---
title: Elemento &lt;Field&gt; (.NET Nativo)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a14125f-1a8d-41a1-8a32-659ca0ad12de
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2ef073004b213ee03ce9655096f612acb5750684
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltfieldgt-element-net-native"></a><span data-ttu-id="e660a-102">Elemento &lt;Field&gt; (.NET Nativo)</span><span class="sxs-lookup"><span data-stu-id="e660a-102">&lt;Field&gt; Element (.NET Native)</span></span>
<span data-ttu-id="e660a-103">Aplica a política de reflexão do tempo de execução a um campo.</span><span class="sxs-lookup"><span data-stu-id="e660a-103">Applies runtime reflection policy to a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e660a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e660a-104">Syntax</span></span>  
  
```xml  
<Field Name="field_name"  
       Browse="policy_type"  
       Dynamic="policy_type"  
       Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e660a-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e660a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="e660a-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e660a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e660a-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="e660a-107">Attributes</span></span>  
  
|<span data-ttu-id="e660a-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="e660a-108">Attribute</span></span>|<span data-ttu-id="e660a-109">Tipo de atributo</span><span class="sxs-lookup"><span data-stu-id="e660a-109">Attribute type</span></span>|<span data-ttu-id="e660a-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="e660a-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="e660a-111">Geral</span><span class="sxs-lookup"><span data-stu-id="e660a-111">General</span></span>|<span data-ttu-id="e660a-112">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="e660a-112">Required attribute.</span></span> <span data-ttu-id="e660a-113">Especifica o nome do campo.</span><span class="sxs-lookup"><span data-stu-id="e660a-113">Specifies the field name.</span></span>|  
|`Browse`|<span data-ttu-id="e660a-114">Reflexão</span><span class="sxs-lookup"><span data-stu-id="e660a-114">Reflection</span></span>|<span data-ttu-id="e660a-115">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="e660a-115">Optional attribute.</span></span> <span data-ttu-id="e660a-116">Controla consultas para obter informações sobre o campo ou para enumerá-lo, mas não permite qualquer acesso dinâmico no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e660a-116">Controls querying for information about or enumerating the field but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="e660a-117">Reflexão</span><span class="sxs-lookup"><span data-stu-id="e660a-117">Reflection</span></span>|<span data-ttu-id="e660a-118">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="e660a-118">Optional attribute.</span></span> <span data-ttu-id="e660a-119">Controla o acesso do tempo de execução ao campo para habilitar programação dinâmica.</span><span class="sxs-lookup"><span data-stu-id="e660a-119">Controls runtime access to the field to enable dynamic programming.</span></span> <span data-ttu-id="e660a-120">Essa política garante que um campo pode ser definido ou recuperado dinamicamente no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e660a-120">This policy ensures that a field can be set or retrieved dynamically at run time.</span></span>|  
|`Serialize`|<span data-ttu-id="e660a-121">Serialização</span><span class="sxs-lookup"><span data-stu-id="e660a-121">Serialization</span></span>|<span data-ttu-id="e660a-122">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="e660a-122">Optional attribute.</span></span> <span data-ttu-id="e660a-123">Controla o acesso do tempo de execução a um campo para habilitar as instâncias de tipo a serem serializadas por bibliotecas como o serializador Newtonsoft JSON ou a ser usado para a associação de dados.</span><span class="sxs-lookup"><span data-stu-id="e660a-123">Controls runtime access to a field to enable type instances to be serialized by libraries such as the Newtonsoft JSON serializer or to be used for data binding.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="e660a-124">Atributo de nome</span><span class="sxs-lookup"><span data-stu-id="e660a-124">Name attribute</span></span>  
  
|<span data-ttu-id="e660a-125">Valor</span><span class="sxs-lookup"><span data-stu-id="e660a-125">Value</span></span>|<span data-ttu-id="e660a-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="e660a-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e660a-127">*method_name*</span><span class="sxs-lookup"><span data-stu-id="e660a-127">*method_name*</span></span>|<span data-ttu-id="e660a-128">O nome do campo.</span><span class="sxs-lookup"><span data-stu-id="e660a-128">The field name.</span></span> <span data-ttu-id="e660a-129">O tipo do campo é definido pelo elemento pai [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) ou [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="e660a-129">The type of the field is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="e660a-130">Todos os outros atributos</span><span class="sxs-lookup"><span data-stu-id="e660a-130">All other attributes</span></span>  
  
|<span data-ttu-id="e660a-131">Valor</span><span class="sxs-lookup"><span data-stu-id="e660a-131">Value</span></span>|<span data-ttu-id="e660a-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="e660a-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e660a-133">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="e660a-133">*policy_setting*</span></span>|<span data-ttu-id="e660a-134">A configuração a ser aplicada a este tipo de política para o campo.</span><span class="sxs-lookup"><span data-stu-id="e660a-134">The setting to apply to this policy type for the field.</span></span> <span data-ttu-id="e660a-135">Os valores possíveis são `Auto`, `Excluded`, `Included` e `Required`.</span><span class="sxs-lookup"><span data-stu-id="e660a-135">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="e660a-136">Para obter mais informações, consulte [Configurações da política da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="e660a-136">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e660a-137">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e660a-137">Child Elements</span></span>  
 <span data-ttu-id="e660a-138">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="e660a-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e660a-139">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e660a-139">Parent Elements</span></span>  
  
|<span data-ttu-id="e660a-140">Elemento</span><span class="sxs-lookup"><span data-stu-id="e660a-140">Element</span></span>|<span data-ttu-id="e660a-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="e660a-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e660a-142">\<Type></span><span class="sxs-lookup"><span data-stu-id="e660a-142">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="e660a-143">Aplica a política de reflexão a um tipo e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="e660a-143">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="e660a-144">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="e660a-144">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="e660a-145">Aplica a política de reflexão a um tipo genérico construído e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="e660a-145">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e660a-146">Comentários</span><span class="sxs-lookup"><span data-stu-id="e660a-146">Remarks</span></span>  
 <span data-ttu-id="e660a-147">Se a política do campo não for definida explicitamente, ele herdará a política de tempo de execução do seu elemento pai.</span><span class="sxs-lookup"><span data-stu-id="e660a-147">If a field's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e660a-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e660a-148">See Also</span></span>  
 [<span data-ttu-id="e660a-149">Elementos da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="e660a-149">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="e660a-150">Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="e660a-150">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="e660a-151">Configurações da política da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="e660a-151">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
