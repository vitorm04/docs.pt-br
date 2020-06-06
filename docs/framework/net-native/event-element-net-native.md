---
title: <Event> (.NET Nativo)
ms.date: 03/30/2017
ms.assetid: e53b029c-9d6d-4c0a-9cdc-5cfca8a5ca47
ms.openlocfilehash: 60da48d5872d7ce61afcffa7977411bc6e1efc7f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79181032"
---
# <a name="event-element-net-native"></a><span data-ttu-id="6fecb-102">\<Event> (.NET Nativo)</span><span class="sxs-lookup"><span data-stu-id="6fecb-102">\<Event> Element (.NET Native)</span></span>
<span data-ttu-id="6fecb-103">Aplica a política de reflexão de runtime a um evento.</span><span class="sxs-lookup"><span data-stu-id="6fecb-103">Applies runtime reflection policy to an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fecb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6fecb-104">Syntax</span></span>  
  
```xml  
<Event Name="event_name"
       Browse="policy_type"
       Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6fecb-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6fecb-105">Attributes and Elements</span></span>  
 <span data-ttu-id="6fecb-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6fecb-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6fecb-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="6fecb-107">Attributes</span></span>  
  
|<span data-ttu-id="6fecb-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="6fecb-108">Attribute</span></span>|<span data-ttu-id="6fecb-109">Tipo de atributo</span><span class="sxs-lookup"><span data-stu-id="6fecb-109">Attribute type</span></span>|<span data-ttu-id="6fecb-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="6fecb-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="6fecb-111">Geral</span><span class="sxs-lookup"><span data-stu-id="6fecb-111">General</span></span>|<span data-ttu-id="6fecb-112">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="6fecb-112">Required attribute.</span></span> <span data-ttu-id="6fecb-113">Especifica o nome do evento.</span><span class="sxs-lookup"><span data-stu-id="6fecb-113">Specifies the event name.</span></span>|  
|`Browse`|<span data-ttu-id="6fecb-114">Reflexão</span><span class="sxs-lookup"><span data-stu-id="6fecb-114">Reflection</span></span>|<span data-ttu-id="6fecb-115">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="6fecb-115">Optional attribute.</span></span> <span data-ttu-id="6fecb-116">Controla consultas para obter informações sobre o evento ou para enumerá-lo, mas não permite qualquer acesso dinâmico no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6fecb-116">Controls querying for information about or enumerating the event but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="6fecb-117">Reflexão</span><span class="sxs-lookup"><span data-stu-id="6fecb-117">Reflection</span></span>|<span data-ttu-id="6fecb-118">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="6fecb-118">Optional attribute.</span></span> <span data-ttu-id="6fecb-119">Controla o acesso do runtime ao evento para habilitar programação dinâmica.</span><span class="sxs-lookup"><span data-stu-id="6fecb-119">Controls runtime access to the event to enable dynamic programming.</span></span> <span data-ttu-id="6fecb-120">Essa política garante que um evento pode ser tratado dinamicamente no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6fecb-120">This policy ensures that an event can be handled dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="6fecb-121">Atributo de nome</span><span class="sxs-lookup"><span data-stu-id="6fecb-121">Name attribute</span></span>  
  
|<span data-ttu-id="6fecb-122">Valor</span><span class="sxs-lookup"><span data-stu-id="6fecb-122">Value</span></span>|<span data-ttu-id="6fecb-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="6fecb-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6fecb-124">*method_name*</span><span class="sxs-lookup"><span data-stu-id="6fecb-124">*method_name*</span></span>|<span data-ttu-id="6fecb-125">O nome do evento.</span><span class="sxs-lookup"><span data-stu-id="6fecb-125">The event name.</span></span> <span data-ttu-id="6fecb-126">O tipo do evento é definido pelo [\<Type>](type-element-net-native.md) elemento pai ou [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="6fecb-126">The type of the event is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="6fecb-127">Todos os outros atributos</span><span class="sxs-lookup"><span data-stu-id="6fecb-127">All other attributes</span></span>  
  
|<span data-ttu-id="6fecb-128">Valor</span><span class="sxs-lookup"><span data-stu-id="6fecb-128">Value</span></span>|<span data-ttu-id="6fecb-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="6fecb-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6fecb-130">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="6fecb-130">*policy_setting*</span></span>|<span data-ttu-id="6fecb-131">A configuração a ser aplicada a este tipo de política para o evento.</span><span class="sxs-lookup"><span data-stu-id="6fecb-131">The setting to apply to this policy type for the event.</span></span> <span data-ttu-id="6fecb-132">Os valores possíveis são `Auto`, `Excluded`, `Included` e `Required`.</span><span class="sxs-lookup"><span data-stu-id="6fecb-132">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="6fecb-133">Para obter mais informações, consulte [Configurações da política da diretiva de runtime](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="6fecb-133">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6fecb-134">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6fecb-134">Child Elements</span></span>  
 <span data-ttu-id="6fecb-135">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="6fecb-135">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6fecb-136">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6fecb-136">Parent Elements</span></span>  
  
|<span data-ttu-id="6fecb-137">Elemento</span><span class="sxs-lookup"><span data-stu-id="6fecb-137">Element</span></span>|<span data-ttu-id="6fecb-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="6fecb-138">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="6fecb-139">Aplica a política de reflexão a um tipo e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="6fecb-139">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="6fecb-140">Aplica a política de reflexão a um tipo genérico construído e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="6fecb-140">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6fecb-141">Comentários</span><span class="sxs-lookup"><span data-stu-id="6fecb-141">Remarks</span></span>  
 <span data-ttu-id="6fecb-142">Se uma política do evento não for definida explicitamente, ele herdará a política de runtime do seu elemento pai.</span><span class="sxs-lookup"><span data-stu-id="6fecb-142">If an event's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fecb-143">Confira também</span><span class="sxs-lookup"><span data-stu-id="6fecb-143">See also</span></span>

- [<span data-ttu-id="6fecb-144">Referência do arquivo de configuração de diretivas do runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="6fecb-144">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="6fecb-145">Elementos da diretiva de runtime</span><span class="sxs-lookup"><span data-stu-id="6fecb-145">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="6fecb-146">Configurações da política da diretiva de runtime</span><span class="sxs-lookup"><span data-stu-id="6fecb-146">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
