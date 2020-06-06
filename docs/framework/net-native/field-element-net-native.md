---
title: <Field> (.NET Nativo)
ms.date: 03/30/2017
ms.assetid: 6a14125f-1a8d-41a1-8a32-659ca0ad12de
ms.openlocfilehash: 2a63b88c399a999cd00750dee1614352cea10e80
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128416"
---
# <a name="field-element-net-native"></a><span data-ttu-id="08593-102">\<Field> (.NET Nativo)</span><span class="sxs-lookup"><span data-stu-id="08593-102">\<Field> Element (.NET Native)</span></span>
<span data-ttu-id="08593-103">Aplica a política de reflexão do runtime a um campo.</span><span class="sxs-lookup"><span data-stu-id="08593-103">Applies runtime reflection policy to a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08593-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="08593-104">Syntax</span></span>  
  
```xml  
<Field Name="field_name"  
       Browse="policy_type"  
       Dynamic="policy_type"  
       Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="08593-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="08593-105">Attributes and Elements</span></span>  
 <span data-ttu-id="08593-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="08593-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="08593-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="08593-107">Attributes</span></span>  
  
|<span data-ttu-id="08593-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="08593-108">Attribute</span></span>|<span data-ttu-id="08593-109">Tipo de atributo</span><span class="sxs-lookup"><span data-stu-id="08593-109">Attribute type</span></span>|<span data-ttu-id="08593-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="08593-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="08593-111">Geral</span><span class="sxs-lookup"><span data-stu-id="08593-111">General</span></span>|<span data-ttu-id="08593-112">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="08593-112">Required attribute.</span></span> <span data-ttu-id="08593-113">Especifica o nome do campo.</span><span class="sxs-lookup"><span data-stu-id="08593-113">Specifies the field name.</span></span>|  
|`Browse`|<span data-ttu-id="08593-114">Reflexão</span><span class="sxs-lookup"><span data-stu-id="08593-114">Reflection</span></span>|<span data-ttu-id="08593-115">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="08593-115">Optional attribute.</span></span> <span data-ttu-id="08593-116">Controla consultas para obter informações sobre o campo ou para enumerá-lo, mas não permite qualquer acesso dinâmico no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="08593-116">Controls querying for information about or enumerating the field but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="08593-117">Reflexão</span><span class="sxs-lookup"><span data-stu-id="08593-117">Reflection</span></span>|<span data-ttu-id="08593-118">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="08593-118">Optional attribute.</span></span> <span data-ttu-id="08593-119">Controla o acesso do runtime ao campo para habilitar programação dinâmica.</span><span class="sxs-lookup"><span data-stu-id="08593-119">Controls runtime access to the field to enable dynamic programming.</span></span> <span data-ttu-id="08593-120">Essa política garante que um campo pode ser definido ou recuperado dinamicamente no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="08593-120">This policy ensures that a field can be set or retrieved dynamically at run time.</span></span>|  
|`Serialize`|<span data-ttu-id="08593-121">Serialização</span><span class="sxs-lookup"><span data-stu-id="08593-121">Serialization</span></span>|<span data-ttu-id="08593-122">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="08593-122">Optional attribute.</span></span> <span data-ttu-id="08593-123">Controla o acesso do runtime a um campo para habilitar as instâncias de tipo a serem serializadas por bibliotecas como o serializador Newtonsoft JSON ou a ser usado para a associação de dados.</span><span class="sxs-lookup"><span data-stu-id="08593-123">Controls runtime access to a field to enable type instances to be serialized by libraries such as the Newtonsoft JSON serializer or to be used for data binding.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="08593-124">Atributo de nome</span><span class="sxs-lookup"><span data-stu-id="08593-124">Name attribute</span></span>  
  
|<span data-ttu-id="08593-125">Valor</span><span class="sxs-lookup"><span data-stu-id="08593-125">Value</span></span>|<span data-ttu-id="08593-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="08593-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="08593-127">*method_name*</span><span class="sxs-lookup"><span data-stu-id="08593-127">*method_name*</span></span>|<span data-ttu-id="08593-128">O nome do campo.</span><span class="sxs-lookup"><span data-stu-id="08593-128">The field name.</span></span> <span data-ttu-id="08593-129">O tipo do campo é definido pelo [\<Type>](type-element-net-native.md) elemento pai ou [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="08593-129">The type of the field is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="08593-130">Todos os outros atributos</span><span class="sxs-lookup"><span data-stu-id="08593-130">All other attributes</span></span>  
  
|<span data-ttu-id="08593-131">Valor</span><span class="sxs-lookup"><span data-stu-id="08593-131">Value</span></span>|<span data-ttu-id="08593-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="08593-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="08593-133">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="08593-133">*policy_setting*</span></span>|<span data-ttu-id="08593-134">A configuração a ser aplicada a este tipo de política para o campo.</span><span class="sxs-lookup"><span data-stu-id="08593-134">The setting to apply to this policy type for the field.</span></span> <span data-ttu-id="08593-135">Os valores possíveis são `Auto`, `Excluded`, `Included` e `Required`.</span><span class="sxs-lookup"><span data-stu-id="08593-135">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="08593-136">Para obter mais informações, consulte [Configurações da política da diretiva de runtime](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="08593-136">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="08593-137">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="08593-137">Child Elements</span></span>  
 <span data-ttu-id="08593-138">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="08593-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="08593-139">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="08593-139">Parent Elements</span></span>  
  
|<span data-ttu-id="08593-140">Elemento</span><span class="sxs-lookup"><span data-stu-id="08593-140">Element</span></span>|<span data-ttu-id="08593-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="08593-141">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="08593-142">Aplica a política de reflexão a um tipo e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="08593-142">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="08593-143">Aplica a política de reflexão a um tipo genérico construído e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="08593-143">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08593-144">Comentários</span><span class="sxs-lookup"><span data-stu-id="08593-144">Remarks</span></span>  
 <span data-ttu-id="08593-145">Se a política do campo não for definida explicitamente, ele herdará a política de runtime do seu elemento pai.</span><span class="sxs-lookup"><span data-stu-id="08593-145">If a field's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08593-146">Confira também</span><span class="sxs-lookup"><span data-stu-id="08593-146">See also</span></span>

- [<span data-ttu-id="08593-147">Elementos da diretiva de runtime</span><span class="sxs-lookup"><span data-stu-id="08593-147">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="08593-148">Referência do arquivo de configuração de diretivas do runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="08593-148">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="08593-149">Configurações da política da diretiva de runtime</span><span class="sxs-lookup"><span data-stu-id="08593-149">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
