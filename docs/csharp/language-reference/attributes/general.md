---
title: 'C# atributos reservados: Condicional, obsoleto, atributoUso'
ms.date: 04/09/2020
description: Esses atributos são interpretados pelo compilador para afetar o código gerado pelo compilador
ms.openlocfilehash: ca3b76387de2a57380d6eb0848991d979a558662
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389866"
---
# <a name="reserved-attributes-conditionalattribute-obsoleteattribute-attributeusageattribute"></a><span data-ttu-id="3ab3c-103">Atributos reservados: ConditionalAttribute, ObsoleteAttribute, AttributeUseAttribute</span><span class="sxs-lookup"><span data-stu-id="3ab3c-103">Reserved attributes: ConditionalAttribute, ObsoleteAttribute, AttributeUsageAttribute</span></span>

<span data-ttu-id="3ab3c-104">Esses atributos podem ser aplicados a elementos do seu código.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-104">These attributes can be applied to elements in your code.</span></span> <span data-ttu-id="3ab3c-105">Eles adicionam significado semântico a esses elementos.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-105">They add semantic meaning to those elements.</span></span> <span data-ttu-id="3ab3c-106">O compilador usa esses significados semânticos para alterar sua saída e relatar possíveis erros por parte dos desenvolvedores usando seu código.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-106">The compiler uses those semantic meanings to alter its output and report possible mistakes by developers using your code.</span></span>

## <a name="conditional-attribute"></a><span data-ttu-id="3ab3c-107">Atributo `Conditional`</span><span class="sxs-lookup"><span data-stu-id="3ab3c-107">`Conditional` attribute</span></span>

<span data-ttu-id="3ab3c-108">O atributo `Conditional` torna a execução de um método dependente de um identificador de pré-processamento.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-108">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="3ab3c-109">O atributo `Conditional` é um alias para <xref:System.Diagnostics.ConditionalAttribute> e pode ser aplicado a um método ou uma classe de atributo.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-109">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>

<span data-ttu-id="3ab3c-110">No exemplo a `Conditional` seguir, é aplicado a um método para ativar ou desativar a exibição de informações de diagnóstico específicas do programa:</span><span class="sxs-lookup"><span data-stu-id="3ab3c-110">In the following example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>

::::::code language="csharp" source="snippets/trace.cs" interactive="try-dotnet" :::

<span data-ttu-id="3ab3c-111">Se `TRACE_ON` o identificador não for definido, a saída de rastreamento não será exibida.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-111">If the `TRACE_ON` identifier isn't defined, the trace output isn't displayed.</span></span> <span data-ttu-id="3ab3c-112">Explore você mesmo na janela interativa.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-112">Explore for yourself in the interactive window.</span></span>

<span data-ttu-id="3ab3c-113">O `Conditional` atributo é `DEBUG` frequentemente usado com o identificador para habilitar recursos de rastreamento e registro para compilações de depuração, mas não em compilações de versão, como mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="3ab3c-113">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, as shown in the following example:</span></span>

::::::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetConditional" :::

<span data-ttu-id="3ab3c-114">Quando um método marcado como condicional é chamado, a presença ou ausência do símbolo de pré-processamento especificado determina se a chamada está incluída ou omitida.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-114">When a method marked conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="3ab3c-115">Se o símbolo estiver definido, a chamada será incluída, caso contrário, a chamada será omitida.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-115">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="3ab3c-116">Um método condicional deve ser um método em uma declaração `void` de classe ou estrutura e deve ter um tipo de retorno.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-116">A conditional method must be a method in a class or struct declaration and must have a `void` return type.</span></span> <span data-ttu-id="3ab3c-117">O `Conditional` uso é mais limpo, mais elegante e menos `#if…#endif` propenso a erros do que os métodos de fechamento dentro de blocos.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-117">Using `Conditional` is cleaner, more elegant, and less error-prone than enclosing methods inside `#if…#endif` blocks.</span></span>

<span data-ttu-id="3ab3c-118">Se um método `Conditional` tiver vários atributos, uma chamada ao método será incluída se em um ou mais símbolos condicionais for definido (os símbolos estão logicamente ligados juntos usando o operador OR).</span><span class="sxs-lookup"><span data-stu-id="3ab3c-118">If a method has multiple `Conditional` attributes, a call to the method is included if at one or more conditional symbols is defined (the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="3ab3c-119">No exemplo a seguir, `A` a `B` presença de um ou resulta em uma chamada de método:</span><span class="sxs-lookup"><span data-stu-id="3ab3c-119">In the following example, the presence of either `A` or `B` results in a method call:</span></span>

::::::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetMultipleConditions" :::

### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="3ab3c-120">Usando `Conditional` com classes de atributos</span><span class="sxs-lookup"><span data-stu-id="3ab3c-120">Using `Conditional` with attribute classes</span></span>

<span data-ttu-id="3ab3c-121">O atributo `Conditional` também pode ser aplicado a uma definição de classe de atributos.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-121">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="3ab3c-122">No exemplo a seguir, `Documentation` o atributo personalizado só `DEBUG` adicionará informações aos metadados se for definido.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-122">In the following example, the custom attribute `Documentation` will only add information to the metadata if `DEBUG` is defined.</span></span>

::::::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetConditionalConditionalAttribute" :::

## <a name="obsolete-attribute"></a><span data-ttu-id="3ab3c-123">Atributo `Obsolete`</span><span class="sxs-lookup"><span data-stu-id="3ab3c-123">`Obsolete` attribute</span></span>

<span data-ttu-id="3ab3c-124">O `Obsolete` atributo marca um elemento de código como não mais recomendado para uso.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-124">The `Obsolete` attribute marks a code element as no longer recommended for use.</span></span> <span data-ttu-id="3ab3c-125">O uso de uma entidade marcada como obsoleta gera um aviso ou um erro.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-125">Use of an entity marked obsolete generates a warning or an error.</span></span> <span data-ttu-id="3ab3c-126">O atributo `Obsolete` é um atributo de uso único e pode ser aplicado a qualquer entidade que permite atributos.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-126">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="3ab3c-127">`Obsolete` é um alias para <xref:System.ObsoleteAttribute>.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-127">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>

<span data-ttu-id="3ab3c-128">No exemplo a `Obsolete` seguir, o `A` atributo `B.OldMethod`é aplicado à classe e ao método .</span><span class="sxs-lookup"><span data-stu-id="3ab3c-128">In the following example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="3ab3c-129">Como o segundo argumento do construtor de atributo aplicado a `B.OldMethod` está definido como `true`, esse método causará um erro do compilador, enquanto que ao usar a classe `A`, produzirá apenas um aviso.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-129">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="3ab3c-130">Chamar `B.NewMethod`, no entanto, não produz aviso nem erro.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-130">Calling `B.NewMethod`, however, produces no warning or error.</span></span> <span data-ttu-id="3ab3c-131">Por exemplo, ao usá-lo com as definições anteriores, o código a seguir gera um erro e dois avisos:</span><span class="sxs-lookup"><span data-stu-id="3ab3c-131">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>

::::::code language="csharp" source="snippets/ObsoleteExample.cs" interactive="try-dotnet" :::

<span data-ttu-id="3ab3c-132">A seqüência fornecida como o primeiro argumento para o construtor de atributos será exibida como parte do aviso ou erro.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-132">The string provided as the first argument to the attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="3ab3c-133">São gerados dois avisos para a classe `A`: um para a declaração da referência de classe e outro para o construtor de classe.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-133">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span> <span data-ttu-id="3ab3c-134">O `Obsolete` atributo pode ser usado sem argumentos, mas incluindo uma explicação do que usar em vez disso é recomendado.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-134">The `Obsolete` attribute can be used without arguments, but including an explanation what to use instead is recommended.</span></span>

## <a name="attributeusage-attribute"></a><span data-ttu-id="3ab3c-135">Atributo `AttributeUsage`</span><span class="sxs-lookup"><span data-stu-id="3ab3c-135">`AttributeUsage` attribute</span></span>

<span data-ttu-id="3ab3c-136">O `AttributeUsage` atributo determina como uma classe de atributo suidua pode ser usada.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-136">The `AttributeUsage` attribute determines how a custom attribute class can be used.</span></span> <span data-ttu-id="3ab3c-137"><xref:System.AttributeUsageAttribute> é um atributo aplicado a definições de atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-137"><xref:System.AttributeUsageAttribute> is an attribute you apply to custom attribute definitions.</span></span> <span data-ttu-id="3ab3c-138">O atributo `AttributeUsage` permite que você controle:</span><span class="sxs-lookup"><span data-stu-id="3ab3c-138">The `AttributeUsage` attribute enables you to control:</span></span>

- <span data-ttu-id="3ab3c-139">A quais elementos do programa o atributo pode ser aplicado.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-139">Which program elements attribute may be applied to.</span></span> <span data-ttu-id="3ab3c-140">A menos que você restrinja seu uso, um atributo poderá ser aplicado a qualquer um dos seguintes elementos do programa:</span><span class="sxs-lookup"><span data-stu-id="3ab3c-140">Unless you restrict its usage, an attribute may be applied to any of the following program elements:</span></span>
  - <span data-ttu-id="3ab3c-141">assembly</span><span class="sxs-lookup"><span data-stu-id="3ab3c-141">assembly</span></span>
  - <span data-ttu-id="3ab3c-142">module</span><span class="sxs-lookup"><span data-stu-id="3ab3c-142">module</span></span>
  - <span data-ttu-id="3ab3c-143">field</span><span class="sxs-lookup"><span data-stu-id="3ab3c-143">field</span></span>
  - <span data-ttu-id="3ab3c-144">event</span><span class="sxs-lookup"><span data-stu-id="3ab3c-144">event</span></span>
  - <span data-ttu-id="3ab3c-145">method</span><span class="sxs-lookup"><span data-stu-id="3ab3c-145">method</span></span>
  - <span data-ttu-id="3ab3c-146">param</span><span class="sxs-lookup"><span data-stu-id="3ab3c-146">param</span></span>
  - <span data-ttu-id="3ab3c-147">propriedade</span><span class="sxs-lookup"><span data-stu-id="3ab3c-147">property</span></span>
  - <span data-ttu-id="3ab3c-148">return</span><span class="sxs-lookup"><span data-stu-id="3ab3c-148">return</span></span>
  - <span data-ttu-id="3ab3c-149">type</span><span class="sxs-lookup"><span data-stu-id="3ab3c-149">type</span></span>
- <span data-ttu-id="3ab3c-150">Indica se um atributo pode ser aplicado a um único elemento do programa várias vezes.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-150">Whether an attribute can be applied to a single program element multiple times.</span></span>
- <span data-ttu-id="3ab3c-151">Indica se os atributos são herdados por classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-151">Whether attributes are inherited by derived classes.</span></span>

<span data-ttu-id="3ab3c-152">As configurações padrão se parecem com o seguinte exemplo quando aplicadas explicitamente:</span><span class="sxs-lookup"><span data-stu-id="3ab3c-152">The default settings look like the following example when applied explicitly:</span></span>

:::code language="csharp" source="snippets/NewAttribute.cs" id="SnippetUsageFirst" :::

<span data-ttu-id="3ab3c-153">Neste exemplo, a classe `NewAttribute` pode ser aplicada a qualquer elemento de programa compatível.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-153">In this example, the `NewAttribute` class can be applied to any supported program element.</span></span> <span data-ttu-id="3ab3c-154">Porém, ele pode ser aplicado apenas uma vez para cada entidade.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-154">But it can be applied only once to each entity.</span></span> <span data-ttu-id="3ab3c-155">O atributo é herdado por classes derivadas quando aplicado a uma classe base.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-155">The attribute is inherited by derived classes when applied to a base class.</span></span>

<span data-ttu-id="3ab3c-156">Os argumentos <xref:System.AttributeUsageAttribute.AllowMultiple> e <xref:System.AttributeUsageAttribute.Inherited> são opcionais e, portanto, o seguinte código tem o mesmo efeito:</span><span class="sxs-lookup"><span data-stu-id="3ab3c-156">The <xref:System.AttributeUsageAttribute.AllowMultiple> and <xref:System.AttributeUsageAttribute.Inherited> arguments are optional, so the following code has the same effect:</span></span>

:::code language="csharp" source="snippets/NewAttribute.cs" id="SnippetUsageSecond" :::

<span data-ttu-id="3ab3c-157">O primeiro argumento <xref:System.AttributeUsageAttribute> deve ser um ou mais elementos da enumeração <xref:System.AttributeTargets>.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-157">The first <xref:System.AttributeUsageAttribute> argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="3ab3c-158">Vários tipos de destino podem ser vinculados junto com o operador OR, como mostra o seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="3ab3c-158">Multiple target types can be linked together with the OR operator, like the following example shows:</span></span>

:::code language="csharp" source="snippets/NewPropertyOrFieldAttribute.cs" id="SnippetDefinePropertyAttribute" :::

<span data-ttu-id="3ab3c-159">Do C# 7.3 em diante, os atributos podem ser aplicados à propriedade ou ao campo de suporte de uma propriedade autoimplementada.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-159">Beginning in C# 7.3, attributes can be applied to either the property or the backing field for an auto-implemented property.</span></span> <span data-ttu-id="3ab3c-160">O atributo se aplica à propriedade, a menos que você especifique o especificador `field` no atributo.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-160">The attribute applies to the property, unless you specify the `field` specifier on the attribute.</span></span> <span data-ttu-id="3ab3c-161">Ambos são mostrados no seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="3ab3c-161">Both are shown in the following example:</span></span>

:::code language="csharp" source="snippets/NewPropertyOrFieldAttribute.cs" id="SnippetUsePropertyAttribute" :::

<span data-ttu-id="3ab3c-162">Se o argumento <xref:System.AttributeUsageAttribute.AllowMultiple> for `true`, o atributo resultante poderá ser aplicado mais de uma vez a uma única entidade, conforme mostrado no seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="3ab3c-162">If the <xref:System.AttributeUsageAttribute.AllowMultiple> argument is `true`, then the resulting attribute can be applied more than once to a single entity, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/MultiUseAttribute.cs" id="SnippetMultiUse" :::

<span data-ttu-id="3ab3c-163">Nesse caso, `MultiUseAttribute` pode ser aplicado repetidas vezes porque `AllowMultiple` está definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-163">In this case, `MultiUseAttribute` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="3ab3c-164">Os dois formatos mostrados para a aplicação de vários atributos são válidos.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-164">Both formats shown for applying multiple attributes are valid.</span></span>

<span data-ttu-id="3ab3c-165">Se <xref:System.AttributeUsageAttribute.Inherited> for `false`, o atributo não será herdado por classes derivadas de uma classe atribuída.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-165">If <xref:System.AttributeUsageAttribute.Inherited> is `false`, then the attribute isn't inherited by classes derived from an attributed class.</span></span> <span data-ttu-id="3ab3c-166">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="3ab3c-166">For example:</span></span>

:::code language="csharp" source="snippets/NonInheritedAttribute.cs" id="SnippetNonInherited" :::

<span data-ttu-id="3ab3c-167">Nesse caso, `NonInheritedAttribute` não é aplicado a `DClass` por meio de herança.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-167">In this case `NonInheritedAttribute` isn't applied to `DClass` via inheritance.</span></span>

## <a name="see-also"></a><span data-ttu-id="3ab3c-168">Confira também</span><span class="sxs-lookup"><span data-stu-id="3ab3c-168">See also</span></span>

- <xref:System.Attribute>
- <xref:System.Reflection>
- [<span data-ttu-id="3ab3c-169">Atributos</span><span class="sxs-lookup"><span data-stu-id="3ab3c-169">Attributes</span></span>](../../../standard/attributes/index.md)
- [<span data-ttu-id="3ab3c-170">Reflexão</span><span class="sxs-lookup"><span data-stu-id="3ab3c-170">Reflection</span></span>](../../programming-guide/concepts/reflection.md)
