---
title: Elementos da diretiva de tempo de execução
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 062f13ad92f37bb7ae29ed34dcf88f99f98e7612
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049265"
---
# <a name="runtime-directive-elements"></a><span data-ttu-id="1c3c5-102">Elementos da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="1c3c5-102">Runtime Directive Elements</span></span>
<span data-ttu-id="1c3c5-103">O formato do arquivo de diretivas (rd.xml) do tempo de execução suporta os seguintes elementos de diretiva de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="1c3c5-103">The runtime directives (rd.xml) file format supports the following runtime directive elements.</span></span> <span data-ttu-id="1c3c5-104">Consulte a [Referência do arquivo de configuração (rd.xml) de diretivas de tempo de execução](runtime-directives-rd-xml-configuration-file-reference.md) para uma representação hierárquica.</span><span class="sxs-lookup"><span data-stu-id="1c3c5-104">See [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md) for a hierarchical representation.</span></span>  
  
 [<span data-ttu-id="1c3c5-105">\<Application></span><span class="sxs-lookup"><span data-stu-id="1c3c5-105">\<Application></span></span>](application-element-net-native.md)  
 <span data-ttu-id="1c3c5-106">Aplica a política de reflexão de tempo de execução a todos os tipos usados pelo aplicativo e serve como um contêiner para tipos amplos de aplicativos e membros de tipo cujos metadados estão disponíveis para reflexão no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="1c3c5-106">Applies runtime reflection policy to all types used by the app, and serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="1c3c5-107">Este é um filho do elemento [\<Directives>](directives-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="1c3c5-107">This is a child of the [\<Directives>](directives-element-net-native.md) element.</span></span>  
  
 [<span data-ttu-id="1c3c5-108">\<Assembly></span><span class="sxs-lookup"><span data-stu-id="1c3c5-108">\<Assembly></span></span>](assembly-element-net-native.md)  
 <span data-ttu-id="1c3c5-109">Aplica a política de tempo de execução a todos os tipos em um assembly.</span><span class="sxs-lookup"><span data-stu-id="1c3c5-109">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="1c3c5-110">Esse é um filho dos elementos [\<Application>](application-element-net-native.md) e [\<Library>](library-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="1c3c5-110">This is a child of the [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="1c3c5-111">\<AttributeImplies></span><span class="sxs-lookup"><span data-stu-id="1c3c5-111">\<AttributeImplies></span></span>](attributeimplies-element-net-native.md)  
 <span data-ttu-id="1c3c5-112">Se sua diretiva recipiente [\<Type>](type-element-net-native.md) for um atributo, ela se aplicará à política de tempo de execução para elementos de código aos quais esse atributo é aplicado.</span><span class="sxs-lookup"><span data-stu-id="1c3c5-112">If its containing [\<Type>](type-element-net-native.md) directive is an attribute, applies runtime policy to code elements to which that attribute is applied.</span></span>  
  
 [<span data-ttu-id="1c3c5-113">\<Directives></span><span class="sxs-lookup"><span data-stu-id="1c3c5-113">\<Directives></span></span>](directives-element-net-native.md)  
 <span data-ttu-id="1c3c5-114">O elemento raiz em cada arquivo de diretivas de tempo de execução para .NET Native.</span><span class="sxs-lookup"><span data-stu-id="1c3c5-114">The root element in every runtime directives file for .NET Native.</span></span> <span data-ttu-id="1c3c5-115">Seus elementos filhos são [\<Application>](application-element-net-native.md) e [\<Library>](library-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="1c3c5-115">Its child elements are [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md).</span></span>  
  
 [<span data-ttu-id="1c3c5-116">\<Event></span><span class="sxs-lookup"><span data-stu-id="1c3c5-116">\<Event></span></span>](event-element-net-native.md)  
 <span data-ttu-id="1c3c5-117">Aplica a política de tempo de execução a um evento.</span><span class="sxs-lookup"><span data-stu-id="1c3c5-117">Applies runtime policy to an event.</span></span> <span data-ttu-id="1c3c5-118">Esse é um filho dos elementos [\<Type>](type-element-net-native.md) e [\<TypeInstantiation>](typeinstantiation-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="1c3c5-118">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="1c3c5-119">\<Field></span><span class="sxs-lookup"><span data-stu-id="1c3c5-119">\<Field></span></span>](field-element-net-native.md)  
 <span data-ttu-id="1c3c5-120">Aplica a política de tempo de execução a um campo.</span><span class="sxs-lookup"><span data-stu-id="1c3c5-120">Applies runtime policy to a field.</span></span> <span data-ttu-id="1c3c5-121">Esse é um filho dos elementos [\<Type>](type-element-net-native.md) e [\<TypeInstantiation>](typeinstantiation-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="1c3c5-121">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="1c3c5-122">\<GenericParameter></span><span class="sxs-lookup"><span data-stu-id="1c3c5-122">\<GenericParameter></span></span>](genericparameter-element-net-native.md)  
 <span data-ttu-id="1c3c5-123">Aplica a política de tempo de execução ao tipo de parâmetro de um tipo ou método genérico.</span><span class="sxs-lookup"><span data-stu-id="1c3c5-123">Applies runtime policy to the parameter type of a generic type or method.</span></span>  
  
 [<span data-ttu-id="1c3c5-124">\<ImpliesType></span><span class="sxs-lookup"><span data-stu-id="1c3c5-124">\<ImpliesType></span></span>](impliestype-element-net-native.md)  
 <span data-ttu-id="1c3c5-125">Aplica a política de tempo de execução a um tipo, se ela tiver sido aplicada ao tipo ou método recipiente.</span><span class="sxs-lookup"><span data-stu-id="1c3c5-125">Applies runtime policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
 [<span data-ttu-id="1c3c5-126">\<Library></span><span class="sxs-lookup"><span data-stu-id="1c3c5-126">\<Library></span></span>](library-element-net-native.md)  
 <span data-ttu-id="1c3c5-127">Aplica a política de tempo de execução a todos os tipos em um assembly.</span><span class="sxs-lookup"><span data-stu-id="1c3c5-127">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="1c3c5-128">Esse é um filho dos elementos [\<Application>](application-element-net-native.md) e [\<Library>](library-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="1c3c5-128">This is a child of the [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="1c3c5-129">\<Method></span><span class="sxs-lookup"><span data-stu-id="1c3c5-129">\<Method></span></span>](method-element-net-native.md)  
 <span data-ttu-id="1c3c5-130">Aplica a política de tempo de execução a um método.</span><span class="sxs-lookup"><span data-stu-id="1c3c5-130">Applies runtime policy to a method.</span></span> <span data-ttu-id="1c3c5-131">Esse é um filho dos elementos [\<Type>](type-element-net-native.md) e [\<TypeInstantiation>](typeinstantiation-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="1c3c5-131">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="1c3c5-132">\<MethodInstantiation></span><span class="sxs-lookup"><span data-stu-id="1c3c5-132">\<MethodInstantiation></span></span>](methodinstantiation-element-net-native.md)  
 <span data-ttu-id="1c3c5-133">Aplica a diretiva de tempo de execução para um método genérico construído.</span><span class="sxs-lookup"><span data-stu-id="1c3c5-133">Applies runtime policy to a constructed generic method.</span></span> <span data-ttu-id="1c3c5-134">Esse é um filho dos elementos [\<Type>](type-element-net-native.md) e [\<TypeInstantiation>](typeinstantiation-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="1c3c5-134">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="1c3c5-135">\<Namespace></span><span class="sxs-lookup"><span data-stu-id="1c3c5-135">\<Namespace></span></span>](namespace-element-net-native.md)  
 <span data-ttu-id="1c3c5-136">Aplica a política de tempo de execução a todos os tipos em um namespace.</span><span class="sxs-lookup"><span data-stu-id="1c3c5-136">Applies runtime policy to all the types in a namespace.</span></span>  
  
 [<span data-ttu-id="1c3c5-137">\<Parameter></span><span class="sxs-lookup"><span data-stu-id="1c3c5-137">\<Parameter></span></span>](parameter-element-net-native.md)  
 <span data-ttu-id="1c3c5-138">Aplica a política de tempo de execução ao tipo do argumento passado para um método.</span><span class="sxs-lookup"><span data-stu-id="1c3c5-138">Applies runtime policy to the type of the argument passed to a method.</span></span>  
  
 [<span data-ttu-id="1c3c5-139">\<Property></span><span class="sxs-lookup"><span data-stu-id="1c3c5-139">\<Property></span></span>](property-element-net-native.md)  
 <span data-ttu-id="1c3c5-140">Aplica a política de tempo de execução a uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="1c3c5-140">Applies runtime policy to a property.</span></span> <span data-ttu-id="1c3c5-141">Esse é um filho dos elementos [\<Type>](type-element-net-native.md) e [\<TypeInstantiation>](typeinstantiation-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="1c3c5-141">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="1c3c5-142">\<Subtypes></span><span class="sxs-lookup"><span data-stu-id="1c3c5-142">\<Subtypes></span></span>](subtypes-element-net-native.md)  
 <span data-ttu-id="1c3c5-143">Aplica a política de tempo de execução a todas as classes herdadas do tipo recipiente.</span><span class="sxs-lookup"><span data-stu-id="1c3c5-143">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
 [<span data-ttu-id="1c3c5-144">\<Type></span><span class="sxs-lookup"><span data-stu-id="1c3c5-144">\<Type></span></span>](type-element-net-native.md)  
 <span data-ttu-id="1c3c5-145">Aplica a política de tempo de execução a um tipo.</span><span class="sxs-lookup"><span data-stu-id="1c3c5-145">Applies runtime policy to a type.</span></span>  
  
 [<span data-ttu-id="1c3c5-146">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="1c3c5-146">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)  
 <span data-ttu-id="1c3c5-147">Aplica a política de tempo de execução a um tipo genérico construído.</span><span class="sxs-lookup"><span data-stu-id="1c3c5-147">Applies runtime policy to a constructed generic type.</span></span>  
  
 [<span data-ttu-id="1c3c5-148">\<TypeParameter></span><span class="sxs-lookup"><span data-stu-id="1c3c5-148">\<TypeParameter></span></span>](typeparameter-element-net-native.md)  
 <span data-ttu-id="1c3c5-149">Aplica a política de tempo de execução ao tipo representado por um argumento <xref:System.Type> passado para um método.</span><span class="sxs-lookup"><span data-stu-id="1c3c5-149">Applies runtime policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c3c5-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1c3c5-150">See also</span></span>

- [<span data-ttu-id="1c3c5-151">Referência do arquivo de configuração rd.xml</span><span class="sxs-lookup"><span data-stu-id="1c3c5-151">rd.xml Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
