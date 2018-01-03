---
title: "Elementos da diretiva de tempo de execução"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e2566c5ebe8c94610c8f7e258da7c77adb86a49f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="runtime-directive-elements"></a><span data-ttu-id="28328-102">Elementos da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="28328-102">Runtime Directive Elements</span></span>
<span data-ttu-id="28328-103">O formato do arquivo de diretivas (rd.xml) do tempo de execução suporta os seguintes elementos de diretiva de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="28328-103">The runtime directives (rd.xml) file format supports the following runtime directive elements.</span></span> <span data-ttu-id="28328-104">Consulte a [Referência do arquivo de configuração (rd.xml) de diretivas de tempo de execução](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) para uma representação hierárquica.</span><span class="sxs-lookup"><span data-stu-id="28328-104">See [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) for a hierarchical representation.</span></span>  
  
 [<span data-ttu-id="28328-105">\<Application></span><span class="sxs-lookup"><span data-stu-id="28328-105">\<Application></span></span>](../../../docs/framework/net-native/application-element-net-native.md)  
 <span data-ttu-id="28328-106">Aplica a política de reflexão de tempo de execução a todos os tipos usados pelo aplicativo e serve como um contêiner para tipos amplos de aplicativos e membros de tipo cujos metadados estão disponíveis para reflexão no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="28328-106">Applies runtime reflection policy to all types used by the app, and serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="28328-107">Este é um filho do elemento [\<Directives>](../../../docs/framework/net-native/directives-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="28328-107">This is a child of the [\<Directives>](../../../docs/framework/net-native/directives-element-net-native.md) element.</span></span>  
  
 [<span data-ttu-id="28328-108">\<Assembly></span><span class="sxs-lookup"><span data-stu-id="28328-108">\<Assembly></span></span>](../../../docs/framework/net-native/assembly-element-net-native.md)  
 <span data-ttu-id="28328-109">Aplica a política de tempo de execução para todos os tipos em um assembly.</span><span class="sxs-lookup"><span data-stu-id="28328-109">Applies runnntime policy to all the types in an assembly.</span></span> <span data-ttu-id="28328-110">Esse é um filho dos elementos [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) e [\<Library>](../../../docs/framework/net-native/library-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="28328-110">This is a child of the [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) and [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="28328-111">\<AttributeImplies></span><span class="sxs-lookup"><span data-stu-id="28328-111">\<AttributeImplies></span></span>](../../../docs/framework/net-native/attributeimplies-element-net-native.md)  
 <span data-ttu-id="28328-112">Se sua diretiva recipiente [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) for um atributo, ela se aplicará à política de tempo de execução para elementos de código aos quais esse atributo é aplicado.</span><span class="sxs-lookup"><span data-stu-id="28328-112">If its containing [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) directive is an attribute, applies runtime policy to code elements to which that attribute is applied.</span></span>  
  
 [<span data-ttu-id="28328-113">\<Directives></span><span class="sxs-lookup"><span data-stu-id="28328-113">\<Directives></span></span>](../../../docs/framework/net-native/directives-element-net-native.md)  
 <span data-ttu-id="28328-114">O elemento raiz em todos os arquivos de diretivas de tempo de execução para [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="28328-114">The root element in every runtime directives file for [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="28328-115">Seus elementos filhos são [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) e [\<Library>](../../../docs/framework/net-native/library-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="28328-115">Its child elements are [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) and [\<Library>](../../../docs/framework/net-native/library-element-net-native.md).</span></span>  
  
 [<span data-ttu-id="28328-116">\<Event></span><span class="sxs-lookup"><span data-stu-id="28328-116">\<Event></span></span>](../../../docs/framework/net-native/event-element-net-native.md)  
 <span data-ttu-id="28328-117">Aplica a política de tempo de execução a um evento.</span><span class="sxs-lookup"><span data-stu-id="28328-117">Applies runtime policy to an event.</span></span> <span data-ttu-id="28328-118">Esse é um filho dos elementos [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) e [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="28328-118">This is a child of the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) and [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="28328-119">\<Field></span><span class="sxs-lookup"><span data-stu-id="28328-119">\<Field></span></span>](../../../docs/framework/net-native/field-element-net-native.md)  
 <span data-ttu-id="28328-120">Aplica a política de tempo de execução a um campo.</span><span class="sxs-lookup"><span data-stu-id="28328-120">Applies runtime policy to a field.</span></span> <span data-ttu-id="28328-121">Esse é um filho dos elementos [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) e [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="28328-121">This is a child of the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) and [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="28328-122">\<GenericParameter></span><span class="sxs-lookup"><span data-stu-id="28328-122">\<GenericParameter></span></span>](../../../docs/framework/net-native/genericparameter-element-net-native.md)  
 <span data-ttu-id="28328-123">Aplica a política de tempo de execução ao tipo de parâmetro de um tipo ou método genérico.</span><span class="sxs-lookup"><span data-stu-id="28328-123">Applies runtime policy to the parameter type of a generic type or method.</span></span>  
  
 [<span data-ttu-id="28328-124">\<ImpliesType></span><span class="sxs-lookup"><span data-stu-id="28328-124">\<ImpliesType></span></span>](../../../docs/framework/net-native/impliestype-element-net-native.md)  
 <span data-ttu-id="28328-125">Aplica a política de tempo de execução a um tipo, se ela tiver sido aplicada ao tipo ou método recipiente.</span><span class="sxs-lookup"><span data-stu-id="28328-125">Applies runtime policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
 [<span data-ttu-id="28328-126">\<Library></span><span class="sxs-lookup"><span data-stu-id="28328-126">\<Library></span></span>](../../../docs/framework/net-native/library-element-net-native.md)  
 <span data-ttu-id="28328-127">Aplica a política de tempo de execução a todos os tipos em um assembly.</span><span class="sxs-lookup"><span data-stu-id="28328-127">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="28328-128">Esse é um filho dos elementos [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) e [\<Library>](../../../docs/framework/net-native/library-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="28328-128">This is a child of the [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) and [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="28328-129">\<Method></span><span class="sxs-lookup"><span data-stu-id="28328-129">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)  
 <span data-ttu-id="28328-130">Aplica a política de tempo de execução a um método.</span><span class="sxs-lookup"><span data-stu-id="28328-130">Applies runtime policy to a method.</span></span> <span data-ttu-id="28328-131">Esse é um filho dos elementos [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) e [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="28328-131">This is a child of the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) and [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="28328-132">\<MethodInstantiation></span><span class="sxs-lookup"><span data-stu-id="28328-132">\<MethodInstantiation></span></span>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)  
 <span data-ttu-id="28328-133">Aplica a diretiva de tempo de execução para um método genérico construído.</span><span class="sxs-lookup"><span data-stu-id="28328-133">Applies runtime policy to a constructed generic method.</span></span> <span data-ttu-id="28328-134">Esse é um filho dos elementos [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) e [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="28328-134">This is a child of the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) and [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="28328-135">\<Namespace></span><span class="sxs-lookup"><span data-stu-id="28328-135">\<Namespace></span></span>](../../../docs/framework/net-native/namespace-element-net-native.md)  
 <span data-ttu-id="28328-136">Aplica a política de tempo de execução a todos os tipos em um namespace.</span><span class="sxs-lookup"><span data-stu-id="28328-136">Applies runtime policy to all the types in a namespace.</span></span>  
  
 [<span data-ttu-id="28328-137">\<Parameter></span><span class="sxs-lookup"><span data-stu-id="28328-137">\<Parameter></span></span>](../../../docs/framework/net-native/parameter-element-net-native.md)  
 <span data-ttu-id="28328-138">Aplica a política de tempo de execução ao tipo do argumento passado para um método.</span><span class="sxs-lookup"><span data-stu-id="28328-138">Applies runtime policy to the type of the argument passed to a method.</span></span>  
  
 [<span data-ttu-id="28328-139">\<Property></span><span class="sxs-lookup"><span data-stu-id="28328-139">\<Property></span></span>](../../../docs/framework/net-native/property-element-net-native.md)  
 <span data-ttu-id="28328-140">Aplica a política de tempo de execução a uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="28328-140">Applies runtime policy to a property.</span></span> <span data-ttu-id="28328-141">Esse é um filho dos elementos [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) e [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="28328-141">This is a child of the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) and [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="28328-142">\<Subtypes></span><span class="sxs-lookup"><span data-stu-id="28328-142">\<Subtypes></span></span>](../../../docs/framework/net-native/subtypes-element-net-native.md)  
 <span data-ttu-id="28328-143">Aplica a política de tempo de execução a todas as classes herdadas do tipo recipiente.</span><span class="sxs-lookup"><span data-stu-id="28328-143">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
 [<span data-ttu-id="28328-144">\<Type></span><span class="sxs-lookup"><span data-stu-id="28328-144">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)  
 <span data-ttu-id="28328-145">Aplica a política de tempo de execução a um tipo.</span><span class="sxs-lookup"><span data-stu-id="28328-145">Applies runtime policy to a type.</span></span>  
  
 [<span data-ttu-id="28328-146">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="28328-146">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)  
 <span data-ttu-id="28328-147">Aplica a política de tempo de execução a um tipo genérico construído.</span><span class="sxs-lookup"><span data-stu-id="28328-147">Applies runtime policy to a constructed generic type.</span></span>  
  
 [<span data-ttu-id="28328-148">\<TypeParameter></span><span class="sxs-lookup"><span data-stu-id="28328-148">\<TypeParameter></span></span>](../../../docs/framework/net-native/typeparameter-element-net-native.md)  
 <span data-ttu-id="28328-149">Aplica a política de tempo de execução ao tipo representado por um argumento <xref:System.Type> passado para um método.</span><span class="sxs-lookup"><span data-stu-id="28328-149">Applies runtime policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28328-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="28328-150">See Also</span></span>  
 [<span data-ttu-id="28328-151">Referência do arquivo de configuração rd.xml</span><span class="sxs-lookup"><span data-stu-id="28328-151">rd.xml Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
