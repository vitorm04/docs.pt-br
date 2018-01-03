---
title: Elemento &lt;MethodInstantiation&gt; (.NET Nativo)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3355d78-2a88-4109-8521-830d7cae260a
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c888bf806744c5c62d130ec00b89838c52f67d0a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltmethodinstantiationgt-element-net-native"></a><span data-ttu-id="f8c1e-102">Elemento &lt;MethodInstantiation&gt; (.NET Nativo)</span><span class="sxs-lookup"><span data-stu-id="f8c1e-102">&lt;MethodInstantiation&gt; Element (.NET Native)</span></span>
<span data-ttu-id="f8c1e-103">Aplica a política de reflexão de tempo de execução a um método genérico construído.</span><span class="sxs-lookup"><span data-stu-id="f8c1e-103">Applies runtime reflection policy to a constructed generic method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8c1e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f8c1e-104">Syntax</span></span>  
  
```xml  
<MethodInstantiation Name="method_name"  
                     Signature="method_signature"  
                     Arguments="method_arguments"  
                     Browse="policy_type"  
                     Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f8c1e-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f8c1e-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f8c1e-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f8c1e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f8c1e-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="f8c1e-107">Attributes</span></span>  
  
|<span data-ttu-id="f8c1e-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="f8c1e-108">Attribute</span></span>|<span data-ttu-id="f8c1e-109">Tipo de atributo</span><span class="sxs-lookup"><span data-stu-id="f8c1e-109">Attribute type</span></span>|<span data-ttu-id="f8c1e-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="f8c1e-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="f8c1e-111">Geral</span><span class="sxs-lookup"><span data-stu-id="f8c1e-111">General</span></span>|<span data-ttu-id="f8c1e-112">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="f8c1e-112">Required attribute.</span></span> <span data-ttu-id="f8c1e-113">Especifica o nome do método.</span><span class="sxs-lookup"><span data-stu-id="f8c1e-113">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="f8c1e-114">Geral</span><span class="sxs-lookup"><span data-stu-id="f8c1e-114">General</span></span>|<span data-ttu-id="f8c1e-115">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="f8c1e-115">Optional attribute.</span></span> <span data-ttu-id="f8c1e-116">Especifica os parâmetros nomeados do método.</span><span class="sxs-lookup"><span data-stu-id="f8c1e-116">Specifies named parameters of the method.</span></span> <span data-ttu-id="f8c1e-117">Vários parâmetros nomeados são separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="f8c1e-117">Multiple named parameters are separated by commas.</span></span> <span data-ttu-id="f8c1e-118">O atributo `Signature` é usado para diferenciar métodos sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="f8c1e-118">The `Signature` attribute is used to differentiate overloaded methods.</span></span>|  
|`Arguments`|<span data-ttu-id="f8c1e-119">Geral</span><span class="sxs-lookup"><span data-stu-id="f8c1e-119">General</span></span>|<span data-ttu-id="f8c1e-120">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="f8c1e-120">Required attribute.</span></span> <span data-ttu-id="f8c1e-121">Especifica os argumentos de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="f8c1e-121">Specifies the generic type arguments.</span></span> <span data-ttu-id="f8c1e-122">Se houver vários parâmetros, eles são separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="f8c1e-122">If multiple arguments are present, they are separated by commas.</span></span>|  
|`Browse`|<span data-ttu-id="f8c1e-123">Reflexão</span><span class="sxs-lookup"><span data-stu-id="f8c1e-123">Reflection</span></span>|<span data-ttu-id="f8c1e-124">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="f8c1e-124">Optional attribute.</span></span> <span data-ttu-id="f8c1e-125">Controla consultas para obter informações sobre o método ou para enumerá-lo, mas não permite qualquer invocação dinâmica no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f8c1e-125">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="f8c1e-126">Reflexão</span><span class="sxs-lookup"><span data-stu-id="f8c1e-126">Reflection</span></span>|<span data-ttu-id="f8c1e-127">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="f8c1e-127">Optional attribute.</span></span> <span data-ttu-id="f8c1e-128">Controla o acesso do tempo de execução a um construtor ou método para habilitar a programação dinâmica.</span><span class="sxs-lookup"><span data-stu-id="f8c1e-128">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="f8c1e-129">Essa política garante que um membro pode ser invocado dinamicamente no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f8c1e-129">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="f8c1e-130">Atributo de nome</span><span class="sxs-lookup"><span data-stu-id="f8c1e-130">Name attribute</span></span>  
  
|<span data-ttu-id="f8c1e-131">Valor</span><span class="sxs-lookup"><span data-stu-id="f8c1e-131">Value</span></span>|<span data-ttu-id="f8c1e-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="f8c1e-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f8c1e-133">*method_name*</span><span class="sxs-lookup"><span data-stu-id="f8c1e-133">*method_name*</span></span>|<span data-ttu-id="f8c1e-134">O nome do método.</span><span class="sxs-lookup"><span data-stu-id="f8c1e-134">The method name.</span></span> <span data-ttu-id="f8c1e-135">O tipo do método é definido pelo elemento pai [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) ou [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="f8c1e-135">The type of the method is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="f8c1e-136">Atributo de assinatura</span><span class="sxs-lookup"><span data-stu-id="f8c1e-136">Signature attribute</span></span>  
  
|<span data-ttu-id="f8c1e-137">Valor</span><span class="sxs-lookup"><span data-stu-id="f8c1e-137">Value</span></span>|<span data-ttu-id="f8c1e-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="f8c1e-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f8c1e-139">*method_signature*</span><span class="sxs-lookup"><span data-stu-id="f8c1e-139">*method_signature*</span></span>|<span data-ttu-id="f8c1e-140">Especifica os parâmetros nomeados do método.</span><span class="sxs-lookup"><span data-stu-id="f8c1e-140">Specifies the named parameters of the method.</span></span> <span data-ttu-id="f8c1e-141">Se vários parâmetros estiverem presentes, eles são separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="f8c1e-141">If multiple parameters are present, they are separated by commas.</span></span>|  
  
## <a name="arguments-attribute"></a><span data-ttu-id="f8c1e-142">Atributo de argumentos</span><span class="sxs-lookup"><span data-stu-id="f8c1e-142">Arguments attribute</span></span>  
  
|<span data-ttu-id="f8c1e-143">Valor</span><span class="sxs-lookup"><span data-stu-id="f8c1e-143">Value</span></span>|<span data-ttu-id="f8c1e-144">Descrição</span><span class="sxs-lookup"><span data-stu-id="f8c1e-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f8c1e-145">*method_arguments*</span><span class="sxs-lookup"><span data-stu-id="f8c1e-145">*method_arguments*</span></span>|<span data-ttu-id="f8c1e-146">Especifica os argumentos de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="f8c1e-146">Specifies the generic type arguments.</span></span> <span data-ttu-id="f8c1e-147">Se houver vários parâmetros, eles são separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="f8c1e-147">If multiple arguments are present, they are separated by commas.</span></span> <span data-ttu-id="f8c1e-148">Cada argumento deve conter o nome do tipo totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="f8c1e-148">Each argument must consist of the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="f8c1e-149">Todos os outros atributos</span><span class="sxs-lookup"><span data-stu-id="f8c1e-149">All other attributes</span></span>  
  
|<span data-ttu-id="f8c1e-150">Valor</span><span class="sxs-lookup"><span data-stu-id="f8c1e-150">Value</span></span>|<span data-ttu-id="f8c1e-151">Descrição</span><span class="sxs-lookup"><span data-stu-id="f8c1e-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f8c1e-152">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="f8c1e-152">*policy_setting*</span></span>|<span data-ttu-id="f8c1e-153">A configuração a ser aplicada a este tipo de política para o método.</span><span class="sxs-lookup"><span data-stu-id="f8c1e-153">The setting to apply to this policy type for the method.</span></span> <span data-ttu-id="f8c1e-154">Os valores possíveis são `Auto`, `Excluded`, `Included` e `Required`.</span><span class="sxs-lookup"><span data-stu-id="f8c1e-154">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="f8c1e-155">Para obter mais informações, consulte [Configurações da política da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="f8c1e-155">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f8c1e-156">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f8c1e-156">Child Elements</span></span>  
 <span data-ttu-id="f8c1e-157">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="f8c1e-157">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f8c1e-158">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f8c1e-158">Parent Elements</span></span>  
  
|<span data-ttu-id="f8c1e-159">Elemento</span><span class="sxs-lookup"><span data-stu-id="f8c1e-159">Element</span></span>|<span data-ttu-id="f8c1e-160">Descrição</span><span class="sxs-lookup"><span data-stu-id="f8c1e-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f8c1e-161">\<Type></span><span class="sxs-lookup"><span data-stu-id="f8c1e-161">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="f8c1e-162">Aplica a política de reflexão a um tipo e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="f8c1e-162">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="f8c1e-163">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="f8c1e-163">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="f8c1e-164">Aplica a política de reflexão a um tipo genérico construído e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="f8c1e-164">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8c1e-165">Comentários</span><span class="sxs-lookup"><span data-stu-id="f8c1e-165">Remarks</span></span>  
 <span data-ttu-id="f8c1e-166">O elemento `<MethodInstantiation>` substitui a política de reflexão de tempo de execução do seu método genérico aberto correspondente.</span><span class="sxs-lookup"><span data-stu-id="f8c1e-166">The `<MethodInstantiation>` element overrides the runtime reflection policy of its corresponding open generic method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8c1e-167">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f8c1e-167">See Also</span></span>  
 [<span data-ttu-id="f8c1e-168">Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="f8c1e-168">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="f8c1e-169">Elementos da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="f8c1e-169">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="f8c1e-170">Configurações da política da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="f8c1e-170">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [<span data-ttu-id="f8c1e-171">Elemento \<Method></span><span class="sxs-lookup"><span data-stu-id="f8c1e-171">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)
