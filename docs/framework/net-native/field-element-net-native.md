---
title: <Field> (.NET nativo)
ms.date: 03/30/2017
ms.assetid: 6a14125f-1a8d-41a1-8a32-659ca0ad12de
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c58be27334bcb862367464475a4eade5e01bdbb2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59221607"
---
# <a name="field-element-net-native"></a><span data-ttu-id="3e0a8-102">\<Campo > (.NET nativo)</span><span class="sxs-lookup"><span data-stu-id="3e0a8-102">\<Field> Element (.NET Native)</span></span>
<span data-ttu-id="3e0a8-103">Aplica a política de reflexão do tempo de execução a um campo.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-103">Applies runtime reflection policy to a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e0a8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3e0a8-104">Syntax</span></span>  
  
```xml  
<Field Name="field_name"  
       Browse="policy_type"  
       Dynamic="policy_type"  
       Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e0a8-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3e0a8-105">Attributes and Elements</span></span>  
 <span data-ttu-id="3e0a8-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e0a8-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="3e0a8-107">Attributes</span></span>  
  
|<span data-ttu-id="3e0a8-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="3e0a8-108">Attribute</span></span>|<span data-ttu-id="3e0a8-109">Tipo de atributo</span><span class="sxs-lookup"><span data-stu-id="3e0a8-109">Attribute type</span></span>|<span data-ttu-id="3e0a8-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="3e0a8-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="3e0a8-111">Geral</span><span class="sxs-lookup"><span data-stu-id="3e0a8-111">General</span></span>|<span data-ttu-id="3e0a8-112">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-112">Required attribute.</span></span> <span data-ttu-id="3e0a8-113">Especifica o nome do campo.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-113">Specifies the field name.</span></span>|  
|`Browse`|<span data-ttu-id="3e0a8-114">Reflexão</span><span class="sxs-lookup"><span data-stu-id="3e0a8-114">Reflection</span></span>|<span data-ttu-id="3e0a8-115">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-115">Optional attribute.</span></span> <span data-ttu-id="3e0a8-116">Controla consultas para obter informações sobre o campo ou para enumerá-lo, mas não permite qualquer acesso dinâmico no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-116">Controls querying for information about or enumerating the field but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="3e0a8-117">Reflexão</span><span class="sxs-lookup"><span data-stu-id="3e0a8-117">Reflection</span></span>|<span data-ttu-id="3e0a8-118">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-118">Optional attribute.</span></span> <span data-ttu-id="3e0a8-119">Controla o acesso do tempo de execução ao campo para habilitar programação dinâmica.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-119">Controls runtime access to the field to enable dynamic programming.</span></span> <span data-ttu-id="3e0a8-120">Essa política garante que um campo pode ser definido ou recuperado dinamicamente no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-120">This policy ensures that a field can be set or retrieved dynamically at run time.</span></span>|  
|`Serialize`|<span data-ttu-id="3e0a8-121">Serialização</span><span class="sxs-lookup"><span data-stu-id="3e0a8-121">Serialization</span></span>|<span data-ttu-id="3e0a8-122">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-122">Optional attribute.</span></span> <span data-ttu-id="3e0a8-123">Controla o acesso do tempo de execução a um campo para habilitar as instâncias de tipo a serem serializadas por bibliotecas como o serializador Newtonsoft JSON ou a ser usado para a associação de dados.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-123">Controls runtime access to a field to enable type instances to be serialized by libraries such as the Newtonsoft JSON serializer or to be used for data binding.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="3e0a8-124">Atributo de nome</span><span class="sxs-lookup"><span data-stu-id="3e0a8-124">Name attribute</span></span>  
  
|<span data-ttu-id="3e0a8-125">Valor</span><span class="sxs-lookup"><span data-stu-id="3e0a8-125">Value</span></span>|<span data-ttu-id="3e0a8-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="3e0a8-126">Description</span></span>|  
|-----------|-----------------|  
|*<span data-ttu-id="3e0a8-127">method_name</span><span class="sxs-lookup"><span data-stu-id="3e0a8-127">method_name</span></span>*|<span data-ttu-id="3e0a8-128">O nome do campo.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-128">The field name.</span></span> <span data-ttu-id="3e0a8-129">O tipo do campo é definido pelo elemento pai [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) ou [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="3e0a8-129">The type of the field is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="3e0a8-130">Todos os outros atributos</span><span class="sxs-lookup"><span data-stu-id="3e0a8-130">All other attributes</span></span>  
  
|<span data-ttu-id="3e0a8-131">Valor</span><span class="sxs-lookup"><span data-stu-id="3e0a8-131">Value</span></span>|<span data-ttu-id="3e0a8-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="3e0a8-132">Description</span></span>|  
|-----------|-----------------|  
|*<span data-ttu-id="3e0a8-133">policy_setting</span><span class="sxs-lookup"><span data-stu-id="3e0a8-133">policy_setting</span></span>*|<span data-ttu-id="3e0a8-134">A configuração a ser aplicada a este tipo de política para o campo.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-134">The setting to apply to this policy type for the field.</span></span> <span data-ttu-id="3e0a8-135">Os valores possíveis são `Auto`, `Excluded`, `Included` e `Required`.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-135">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="3e0a8-136">Para obter mais informações, consulte [Configurações da política da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="3e0a8-136">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3e0a8-137">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3e0a8-137">Child Elements</span></span>  
 <span data-ttu-id="3e0a8-138">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3e0a8-139">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3e0a8-139">Parent Elements</span></span>  
  
|<span data-ttu-id="3e0a8-140">Elemento</span><span class="sxs-lookup"><span data-stu-id="3e0a8-140">Element</span></span>|<span data-ttu-id="3e0a8-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="3e0a8-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3e0a8-142">\<tipo ></span><span class="sxs-lookup"><span data-stu-id="3e0a8-142">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="3e0a8-143">Aplica a política de reflexão a um tipo e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-143">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="3e0a8-144">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="3e0a8-144">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="3e0a8-145">Aplica a política de reflexão a um tipo genérico construído e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-145">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e0a8-146">Comentários</span><span class="sxs-lookup"><span data-stu-id="3e0a8-146">Remarks</span></span>  
 <span data-ttu-id="3e0a8-147">Se a política do campo não for definida explicitamente, ele herdará a política de tempo de execução do seu elemento pai.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-147">If a field's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e0a8-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e0a8-148">See also</span></span>

- [<span data-ttu-id="3e0a8-149">Elementos da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="3e0a8-149">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
- [<span data-ttu-id="3e0a8-150">Referência do arquivo de configuração de diretivas do tempo de execução (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="3e0a8-150">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="3e0a8-151">Configurações da política da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="3e0a8-151">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
