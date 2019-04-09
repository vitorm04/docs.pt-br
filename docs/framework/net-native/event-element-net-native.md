---
title: <Event> (.NET nativo)
ms.date: 03/30/2017
ms.assetid: e53b029c-9d6d-4c0a-9cdc-5cfca8a5ca47
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 89e8ddf9ea72db63c72bfb5393709b4c20de2a14
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162988"
---
# <a name="event-element-net-native"></a><span data-ttu-id="c0f25-102">\<Evento > (.NET nativo)</span><span class="sxs-lookup"><span data-stu-id="c0f25-102">\<Event> Element (.NET Native)</span></span>
<span data-ttu-id="c0f25-103">Aplica a política de reflexão de tempo de execução a um evento.</span><span class="sxs-lookup"><span data-stu-id="c0f25-103">Applies runtime reflection policy to an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0f25-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c0f25-104">Syntax</span></span>  
  
```xml  
<Event Name="event_name"   
       Browse="policy_type"   
       Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0f25-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c0f25-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c0f25-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c0f25-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0f25-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="c0f25-107">Attributes</span></span>  
  
|<span data-ttu-id="c0f25-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="c0f25-108">Attribute</span></span>|<span data-ttu-id="c0f25-109">Tipo de atributo</span><span class="sxs-lookup"><span data-stu-id="c0f25-109">Attribute type</span></span>|<span data-ttu-id="c0f25-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="c0f25-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="c0f25-111">Geral</span><span class="sxs-lookup"><span data-stu-id="c0f25-111">General</span></span>|<span data-ttu-id="c0f25-112">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="c0f25-112">Required attribute.</span></span> <span data-ttu-id="c0f25-113">Especifica o nome do evento.</span><span class="sxs-lookup"><span data-stu-id="c0f25-113">Specifies the event name.</span></span>|  
|`Browse`|<span data-ttu-id="c0f25-114">Reflexão</span><span class="sxs-lookup"><span data-stu-id="c0f25-114">Reflection</span></span>|<span data-ttu-id="c0f25-115">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="c0f25-115">Optional attribute.</span></span> <span data-ttu-id="c0f25-116">Controla consultas para obter informações sobre o evento ou para enumerá-lo, mas não permite qualquer acesso dinâmico no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c0f25-116">Controls querying for information about or enumerating the event but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="c0f25-117">Reflexão</span><span class="sxs-lookup"><span data-stu-id="c0f25-117">Reflection</span></span>|<span data-ttu-id="c0f25-118">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="c0f25-118">Optional attribute.</span></span> <span data-ttu-id="c0f25-119">Controla o acesso do tempo de execução ao evento para habilitar programação dinâmica.</span><span class="sxs-lookup"><span data-stu-id="c0f25-119">Controls runtime access to the event to enable dynamic programming.</span></span> <span data-ttu-id="c0f25-120">Essa política garante que um evento pode ser tratado dinamicamente no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c0f25-120">This policy ensures that an event can be handled dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="c0f25-121">Atributo de nome</span><span class="sxs-lookup"><span data-stu-id="c0f25-121">Name attribute</span></span>  
  
|<span data-ttu-id="c0f25-122">Valor</span><span class="sxs-lookup"><span data-stu-id="c0f25-122">Value</span></span>|<span data-ttu-id="c0f25-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="c0f25-123">Description</span></span>|  
|-----------|-----------------|  
|*<span data-ttu-id="c0f25-124">method_name</span><span class="sxs-lookup"><span data-stu-id="c0f25-124">method_name</span></span>*|<span data-ttu-id="c0f25-125">O nome do evento.</span><span class="sxs-lookup"><span data-stu-id="c0f25-125">The event name.</span></span> <span data-ttu-id="c0f25-126">O tipo do evento é definido pelo elemento pai [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) ou [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="c0f25-126">The type of the event is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="c0f25-127">Todos os outros atributos</span><span class="sxs-lookup"><span data-stu-id="c0f25-127">All other attributes</span></span>  
  
|<span data-ttu-id="c0f25-128">Valor</span><span class="sxs-lookup"><span data-stu-id="c0f25-128">Value</span></span>|<span data-ttu-id="c0f25-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="c0f25-129">Description</span></span>|  
|-----------|-----------------|  
|*<span data-ttu-id="c0f25-130">policy_setting</span><span class="sxs-lookup"><span data-stu-id="c0f25-130">policy_setting</span></span>*|<span data-ttu-id="c0f25-131">A configuração a ser aplicada a este tipo de política para o evento.</span><span class="sxs-lookup"><span data-stu-id="c0f25-131">The setting to apply to this policy type for the event.</span></span> <span data-ttu-id="c0f25-132">Os valores possíveis são `Auto`, `Excluded`, `Included` e `Required`.</span><span class="sxs-lookup"><span data-stu-id="c0f25-132">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="c0f25-133">Para obter mais informações, consulte [Configurações da política da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="c0f25-133">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c0f25-134">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c0f25-134">Child Elements</span></span>  
 <span data-ttu-id="c0f25-135">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="c0f25-135">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c0f25-136">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c0f25-136">Parent Elements</span></span>  
  
|<span data-ttu-id="c0f25-137">Elemento</span><span class="sxs-lookup"><span data-stu-id="c0f25-137">Element</span></span>|<span data-ttu-id="c0f25-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="c0f25-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c0f25-139">\<tipo ></span><span class="sxs-lookup"><span data-stu-id="c0f25-139">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="c0f25-140">Aplica a política de reflexão a um tipo e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="c0f25-140">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="c0f25-141">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="c0f25-141">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="c0f25-142">Aplica a política de reflexão a um tipo genérico construído e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="c0f25-142">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0f25-143">Comentários</span><span class="sxs-lookup"><span data-stu-id="c0f25-143">Remarks</span></span>  
 <span data-ttu-id="c0f25-144">Se uma política do evento não for definida explicitamente, ele herdará a política de tempo de execução do seu elemento pai.</span><span class="sxs-lookup"><span data-stu-id="c0f25-144">If an event's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0f25-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c0f25-145">See also</span></span>

- [<span data-ttu-id="c0f25-146">Referência do arquivo de configuração de diretivas do tempo de execução (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="c0f25-146">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="c0f25-147">Elementos da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="c0f25-147">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
- [<span data-ttu-id="c0f25-148">Configurações da política da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="c0f25-148">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
