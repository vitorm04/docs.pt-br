---
title: Tipos de tupla-referência C#
description: 'Saiba mais sobre tuplas C#: estruturas de dados leves que você pode usar para agrupar elementos de dados livremente relacionados'
ms.date: 07/09/2020
helpviewer_keywords:
- value tuples [C#]
ms.openlocfilehash: 3d79ab19117847e2364b154db33a1521416bb3f4
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174984"
---
# <a name="tuple-types-c-reference"></a><span data-ttu-id="bfa17-103">Tipos de tupla (referência C#)</span><span class="sxs-lookup"><span data-stu-id="bfa17-103">Tuple types (C# reference)</span></span>

<span data-ttu-id="bfa17-104">Disponível em C# 7,0 e posterior, o recurso de *tuplas* fornece uma sintaxe concisa para agrupar vários elementos de dados em uma estrutura de dados leve.</span><span class="sxs-lookup"><span data-stu-id="bfa17-104">Available in C# 7.0 and later, the *tuples* feature provides concise syntax to group multiple data elements in a lightweight data structure.</span></span> <span data-ttu-id="bfa17-105">O exemplo a seguir mostra como você pode declarar uma variável de tupla, inicializá-la e acessar seus membros de dados:</span><span class="sxs-lookup"><span data-stu-id="bfa17-105">The following example shows how you can declare a tuple variable, initialize it, and access its data members:</span></span>

[!code-csharp-interactive[tuple intro](snippets/ValueTuples.cs#Introduction)]

<span data-ttu-id="bfa17-106">Como mostra o exemplo anterior, para definir um tipo de tupla, você especifica os tipos de todos os seus membros de dados e, opcionalmente, os [nomes de campo](#tuple-field-names).</span><span class="sxs-lookup"><span data-stu-id="bfa17-106">As the preceding example shows, to define a tuple type, you specify types of all its data members and, optionally, the [field names](#tuple-field-names).</span></span> <span data-ttu-id="bfa17-107">Você não pode definir métodos em um tipo de tupla, mas pode usar os métodos fornecidos pelo .NET, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="bfa17-107">You cannot define methods in a tuple type, but you can use the methods provided by .NET, as the following example shows:</span></span>

[!code-csharp-interactive[tuple methods](snippets/ValueTuples.cs#MethodOnTuples)]

<span data-ttu-id="bfa17-108">A partir do C# 7,3, os tipos de tupla dão suporte a [operadores de igualdade](../operators/equality-operators.md) `==` e `!=` .</span><span class="sxs-lookup"><span data-stu-id="bfa17-108">Beginning with C# 7.3, tuple types support [equality operators](../operators/equality-operators.md) `==` and `!=`.</span></span> <span data-ttu-id="bfa17-109">Para obter mais informações, consulte a seção de [igualdade de tupla](#tuple-equality) .</span><span class="sxs-lookup"><span data-stu-id="bfa17-109">For more information, see the [Tuple equality](#tuple-equality) section.</span></span>

<span data-ttu-id="bfa17-110">Tipos de tupla são [tipos de valor](value-types.md); os elementos de tupla são campos públicos.</span><span class="sxs-lookup"><span data-stu-id="bfa17-110">Tuple types are [value types](value-types.md); tuple elements are public fields.</span></span> <span data-ttu-id="bfa17-111">Isso torna as tuplas tipos de valor *mutável* .</span><span class="sxs-lookup"><span data-stu-id="bfa17-111">That makes tuples *mutable* value types.</span></span>

> [!NOTE]
> <span data-ttu-id="bfa17-112">O recurso de tuplas requer o <xref:System.ValueTuple?displayProperty=nameWithType> tipo e os tipos genéricos relacionados (por exemplo, <xref:System.ValueTuple%602?displayProperty=nameWithType> ), que estão disponíveis no .NET Core e .NET Framework 4,7 e posterior.</span><span class="sxs-lookup"><span data-stu-id="bfa17-112">The tuples feature requires the <xref:System.ValueTuple?displayProperty=nameWithType> type and related generic types (for example, <xref:System.ValueTuple%602?displayProperty=nameWithType>), which are available in .NET Core and .NET Framework 4.7 and later.</span></span> <span data-ttu-id="bfa17-113">Para usar tuplas em um projeto que tenha como destino .NET Framework 4.6.2 ou anterior, adicione o pacote NuGet [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/) ao projeto.</span><span class="sxs-lookup"><span data-stu-id="bfa17-113">To use tuples in a project that targets .NET Framework 4.6.2 or earlier, add the NuGet package [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/) to the project.</span></span>

<span data-ttu-id="bfa17-114">Você pode definir tuplas com um grande número arbitrário de elementos:</span><span class="sxs-lookup"><span data-stu-id="bfa17-114">You can define tuples with an arbitrary large number of elements:</span></span>

[!code-csharp-interactive[large tuple](snippets/ValueTuples.cs#LargeTuple)]

## <a name="use-cases-of-tuples"></a><span data-ttu-id="bfa17-115">Casos de uso de tuplas</span><span class="sxs-lookup"><span data-stu-id="bfa17-115">Use cases of tuples</span></span>

<span data-ttu-id="bfa17-116">Um dos casos de uso mais comuns de tuplas é como um tipo de retorno de método.</span><span class="sxs-lookup"><span data-stu-id="bfa17-116">One of the most common use cases of tuples is as a method return type.</span></span> <span data-ttu-id="bfa17-117">Ou seja, em vez de definir [ `out` parâmetros de método](../keywords/out-parameter-modifier.md), você pode agrupar resultados de método em um tipo de retorno de tupla, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="bfa17-117">That is, instead of defining [`out` method parameters](../keywords/out-parameter-modifier.md), you can group method results in a tuple return type, as the following example shows:</span></span>

[!code-csharp-interactive[multiple method outputs](snippets/ValueTuples.cs#MultipleReturns)]

<span data-ttu-id="bfa17-118">Como mostra o exemplo anterior, você pode trabalhar com a instância de tupla retornada diretamente ou [desconstruir](#tuple-assignment-and-deconstruction) -la em variáveis separadas.</span><span class="sxs-lookup"><span data-stu-id="bfa17-118">As the preceding example shows, you can work with the returned tuple instance directly or [deconstruct](#tuple-assignment-and-deconstruction) it in separate variables.</span></span>

<span data-ttu-id="bfa17-119">Você também pode usar tipos de tupla em vez de [tipos anônimos](../../programming-guide/classes-and-structs/anonymous-types.md); por exemplo, em consultas LINQ.</span><span class="sxs-lookup"><span data-stu-id="bfa17-119">You can also use tuple types instead of [anonymous types](../../programming-guide/classes-and-structs/anonymous-types.md); for example, in LINQ queries.</span></span> <span data-ttu-id="bfa17-120">Para obter mais informações, consulte [escolhendo entre tipos anônimos e de tupla](../../../standard/base-types/choosing-between-anonymous-and-tuple.md).</span><span class="sxs-lookup"><span data-stu-id="bfa17-120">For more information, see [Choosing between anonymous and tuple types](../../../standard/base-types/choosing-between-anonymous-and-tuple.md).</span></span>

<span data-ttu-id="bfa17-121">Normalmente, você usa tuplas para agrupar elementos de dados livremente relacionados.</span><span class="sxs-lookup"><span data-stu-id="bfa17-121">Typically, you use tuples to group loosely related data elements.</span></span> <span data-ttu-id="bfa17-122">Isso geralmente é útil em métodos de utilitário privado e interno.</span><span class="sxs-lookup"><span data-stu-id="bfa17-122">That is usually useful within private and internal utility methods.</span></span> <span data-ttu-id="bfa17-123">No caso da API pública, considere definir uma [classe](../keywords/class.md) ou um tipo de [estrutura](struct.md) .</span><span class="sxs-lookup"><span data-stu-id="bfa17-123">In the case of public API, consider defining a [class](../keywords/class.md) or a [structure](struct.md) type.</span></span>

## <a name="tuple-field-names"></a><span data-ttu-id="bfa17-124">Nomes de campo de tupla</span><span class="sxs-lookup"><span data-stu-id="bfa17-124">Tuple field names</span></span>

<span data-ttu-id="bfa17-125">Você pode especificar explicitamente os nomes dos campos de tupla em uma expressão de inicialização de tupla ou na definição de um tipo de tupla, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="bfa17-125">You can explicitly specify the names of tuple fields either in a tuple initialization expression or in the definition of a tuple type, as the following example shows:</span></span>

[!code-csharp-interactive[explicit field names](snippets/ValueTuples.cs#ExplicitFieldNames)]

<span data-ttu-id="bfa17-126">A partir do C# 7,1, se você não especificar um nome de campo, ele poderá ser inferido a partir do nome da variável correspondente em uma expressão de inicialização de tupla, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="bfa17-126">Beginning with C# 7.1, if you don't specify a field name, it may be inferred from the name of the corresponding variable in a tuple initialization expression, as the following example shows:</span></span>

[!code-csharp-interactive[inferred field names](snippets/ValueTuples.cs#InferFieldNames)]

<span data-ttu-id="bfa17-127">Isso é conhecido como inicializadores de projeção de tupla.</span><span class="sxs-lookup"><span data-stu-id="bfa17-127">That's known as tuple projection initializers.</span></span> <span data-ttu-id="bfa17-128">O nome de uma variável não é projetado para um nome de campo de tupla nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="bfa17-128">The name of a variable isn't projected onto a tuple field name in the following cases:</span></span>

- <span data-ttu-id="bfa17-129">O nome do candidato é um nome de membro de um tipo de tupla, por exemplo,, `Item3` `ToString` ou `Rest` .</span><span class="sxs-lookup"><span data-stu-id="bfa17-129">The candidate name is a member name of a tuple type, for example, `Item3`, `ToString`, or `Rest`.</span></span>
- <span data-ttu-id="bfa17-130">O nome do candidato é uma duplicata de outro nome de campo de tupla, explícita ou implícita.</span><span class="sxs-lookup"><span data-stu-id="bfa17-130">The candidate name is a duplicate of another tuple field name, either explicit or implicit.</span></span>

<span data-ttu-id="bfa17-131">Nesses casos, você especifica explicitamente o nome de um campo ou acessa um campo por seu nome padrão.</span><span class="sxs-lookup"><span data-stu-id="bfa17-131">In those cases you either explicitly specify the name of a field or access a field by its default name.</span></span>

<span data-ttu-id="bfa17-132">Os nomes padrão dos campos de tupla `Item1` são `Item2` , `Item3` e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="bfa17-132">The default names of tuple fields are `Item1`, `Item2`, `Item3` and so on.</span></span> <span data-ttu-id="bfa17-133">Você sempre pode usar o nome padrão de um campo, mesmo quando um nome de campo é especificado explicitamente ou inferido, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="bfa17-133">You can always use the default name of a field, even when a field name is specified explicitly or inferred, as the following example shows:</span></span>

[!code-csharp-interactive[default field names](snippets/ValueTuples.cs#DefaultFieldNames)]

<span data-ttu-id="bfa17-134">As [comparações de igualdade](#tuple-equality) de tupla e [atribuição de tupla](#tuple-assignment-and-deconstruction) não têm nomes de campo em conta.</span><span class="sxs-lookup"><span data-stu-id="bfa17-134">[Tuple assignment](#tuple-assignment-and-deconstruction) and [tuple equality comparisons](#tuple-equality) don't take field names into account.</span></span>

<span data-ttu-id="bfa17-135">No momento da compilação, o compilador substitui nomes de campo não padrão pelos nomes padrão correspondentes.</span><span class="sxs-lookup"><span data-stu-id="bfa17-135">At compile time, the compiler replaces non-default field names with the corresponding default names.</span></span> <span data-ttu-id="bfa17-136">Como resultado, nomes de campo explicitamente especificados ou inferidos não estão disponíveis em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="bfa17-136">As a result, explicitly specified or inferred field names aren't available at run time.</span></span>

## <a name="tuple-assignment-and-deconstruction"></a><span data-ttu-id="bfa17-137">Atribuição e desconstrução de tupla</span><span class="sxs-lookup"><span data-stu-id="bfa17-137">Tuple assignment and deconstruction</span></span>

<span data-ttu-id="bfa17-138">O C# dá suporte à atribuição entre tipos de tupla que atendem às duas condições a seguir:</span><span class="sxs-lookup"><span data-stu-id="bfa17-138">C# supports assignment between tuple types that satisfy both of the following conditions:</span></span>

- <span data-ttu-id="bfa17-139">ambos os tipos de tupla têm o mesmo número de elementos</span><span class="sxs-lookup"><span data-stu-id="bfa17-139">both tuple types have the same number of elements</span></span>
- <span data-ttu-id="bfa17-140">para cada posição de tupla, o tipo do elemento de tupla à direita é o mesmo que ou implicitamente conversível para o tipo do elemento de tupla esquerdo correspondente</span><span class="sxs-lookup"><span data-stu-id="bfa17-140">for each tuple position, the type of the right-hand tuple element is the same as or implicitly convertible to the type of the corresponding left-hand tuple element</span></span>

<span data-ttu-id="bfa17-141">Os valores de elemento de tupla são atribuídos após a ordem dos elementos de tupla.</span><span class="sxs-lookup"><span data-stu-id="bfa17-141">Tuple element values are assigned following the order of tuple elements.</span></span> <span data-ttu-id="bfa17-142">Os nomes dos campos de tupla são ignorados e não atribuídos, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="bfa17-142">The names of tuple fields are ignored and not assigned, as the following example shows:</span></span>

[!code-csharp-interactive[tuple assignment](snippets/ValueTuples.cs#Assignment)]

<span data-ttu-id="bfa17-143">Você também pode usar o operador de atribuição `=` para *desconstruir* uma instância de tupla em variáveis separadas.</span><span class="sxs-lookup"><span data-stu-id="bfa17-143">You can also use the assignment operator `=` to *deconstruct* a tuple instance in separate variables.</span></span> <span data-ttu-id="bfa17-144">Você pode fazer isso de uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="bfa17-144">You can do that in one of the following ways:</span></span>

- <span data-ttu-id="bfa17-145">Declare explicitamente o tipo de cada variável dentro dos parênteses:</span><span class="sxs-lookup"><span data-stu-id="bfa17-145">Explicitly declare the type of each variable inside parentheses:</span></span>

  [!code-csharp-interactive[specify types of variables](snippets/ValueTuples.cs#DeconstructExplicit)]

- <span data-ttu-id="bfa17-146">Use a `var` palavra-chave fora dos parênteses para declarar variáveis digitadas implicitamente e deixe o compilador inferir seus tipos:</span><span class="sxs-lookup"><span data-stu-id="bfa17-146">Use the `var` keyword outside the parentheses to declare implicitly typed variables and let the compiler infer their types:</span></span>

  [!code-csharp-interactive[implicitly typed variables](snippets/ValueTuples.cs#DeconstructVar)]

- <span data-ttu-id="bfa17-147">Usar variáveis existentes:</span><span class="sxs-lookup"><span data-stu-id="bfa17-147">Use existing variables:</span></span>

  [!code-csharp-interactive[existing variables](snippets/ValueTuples.cs#DeconstructExisting)]

<span data-ttu-id="bfa17-148">Para obter mais informações sobre a desconstrução de tuplas e outros tipos, consulte [decompondo tuplas e outros tipos](../../deconstruct.md).</span><span class="sxs-lookup"><span data-stu-id="bfa17-148">For more information about deconstruction of tuples and other types, see [Deconstructing tuples and other types](../../deconstruct.md).</span></span>

## <a name="tuple-equality"></a><span data-ttu-id="bfa17-149">Igualdade de tupla</span><span class="sxs-lookup"><span data-stu-id="bfa17-149">Tuple equality</span></span>

<span data-ttu-id="bfa17-150">Começando com o C# 7.3, os tipos de tupla oferecem suporte aos operadores `==` e `!=`.</span><span class="sxs-lookup"><span data-stu-id="bfa17-150">Beginning with C# 7.3, tuple types support the `==` and `!=` operators.</span></span> <span data-ttu-id="bfa17-151">Esses operadores comparam membros do operando à esquerda com os membros correspondentes do operando à direita após a ordem dos elementos de tupla.</span><span class="sxs-lookup"><span data-stu-id="bfa17-151">These operators compare members of the left-hand operand with the corresponding members of the right-hand operand following the order of tuple elements.</span></span>

[!code-csharp-interactive[tuple equality](snippets/ValueTuples.cs#TupleEquality)]

<span data-ttu-id="bfa17-152">Como mostra o exemplo anterior, as `==` `!=` operações e não levam em conta os nomes de campo de tupla.</span><span class="sxs-lookup"><span data-stu-id="bfa17-152">As the preceding example shows, the `==` and `!=` operations don't take into account tuple field names.</span></span>

<span data-ttu-id="bfa17-153">Duas tuplas são comparáveis quando as duas condições a seguir são satisfeitas:</span><span class="sxs-lookup"><span data-stu-id="bfa17-153">Two tuples are comparable when both of the following conditions are satisfied:</span></span>

- <span data-ttu-id="bfa17-154">Ambas as tuplas têm o mesmo número de elementos.</span><span class="sxs-lookup"><span data-stu-id="bfa17-154">Both tuples have the same number of elements.</span></span> <span data-ttu-id="bfa17-155">Por exemplo, `t1 != t2` não compilar se `t1` e `t2` tiver diferentes números de elementos.</span><span class="sxs-lookup"><span data-stu-id="bfa17-155">For example, `t1 != t2` doesn't compile if `t1` and `t2` have different numbers of elements.</span></span>
- <span data-ttu-id="bfa17-156">Para cada posição de tupla, os elementos correspondentes dos operandos de tupla à esquerda e à direita são comparáveis com os `==` operadores e `!=` .</span><span class="sxs-lookup"><span data-stu-id="bfa17-156">For each tuple position, the corresponding elements from the left-hand and right-hand tuple operands are comparable with the `==` and `!=` operators.</span></span> <span data-ttu-id="bfa17-157">Por exemplo, `(1, (2, 3)) == ((1, 2), 3)` não compila porque o `1` não é comparável com `(1, 2)` .</span><span class="sxs-lookup"><span data-stu-id="bfa17-157">For example, `(1, (2, 3)) == ((1, 2), 3)` doesn't compile because `1` is not comparable with `(1, 2)`.</span></span>

<span data-ttu-id="bfa17-158">Os `==` `!=` operadores e comparam tuplas na forma de curto-circuito.</span><span class="sxs-lookup"><span data-stu-id="bfa17-158">The `==` and `!=` operators compare tuples in short-circuiting way.</span></span> <span data-ttu-id="bfa17-159">Ou seja, uma operação é interrompida assim que ela atende a um par de elementos não iguais ou atinge as extremidades das tuplas.</span><span class="sxs-lookup"><span data-stu-id="bfa17-159">That is, an operation stops as soon as it meets a pair of non equal elements or reaches the ends of tuples.</span></span> <span data-ttu-id="bfa17-160">No entanto, antes de qualquer comparação, *todos os* elementos de tupla são avaliados, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="bfa17-160">However, before any comparison, *all* tuple elements are evaluated, as the following example shows:</span></span>

[!code-csharp-interactive[tuple element evaluation](snippets/ValueTuples.cs#TupleEvaluationForEquality)]

## <a name="tuples-as-out-parameters"></a><span data-ttu-id="bfa17-161">Parâmetros de tuplas como saída</span><span class="sxs-lookup"><span data-stu-id="bfa17-161">Tuples as out parameters</span></span>

<span data-ttu-id="bfa17-162">Normalmente, você refatoria um método que tem [ `out` parâmetros](../keywords/out-parameter-modifier.md) em um método que retorna uma tupla.</span><span class="sxs-lookup"><span data-stu-id="bfa17-162">Typically, you refactor a method that has [`out` parameters](../keywords/out-parameter-modifier.md) into a method that returns a tuple.</span></span> <span data-ttu-id="bfa17-163">No entanto, há casos em que um `out` parâmetro pode ser de um tipo de tupla.</span><span class="sxs-lookup"><span data-stu-id="bfa17-163">However, there are cases in which an `out` parameter can be of a tuple type.</span></span> <span data-ttu-id="bfa17-164">O exemplo a seguir mostra como trabalhar com tuplas como `out` parâmetros:</span><span class="sxs-lookup"><span data-stu-id="bfa17-164">The following example shows how to work with tuples as `out` parameters:</span></span>

[!code-csharp-interactive[tuple as out parameter](snippets/ValueTuples.cs#TupleAsOutParameter)]

## <a name="tuples-vs-systemtuple"></a><span data-ttu-id="bfa17-165">Tuplas vs`System.Tuple`</span><span class="sxs-lookup"><span data-stu-id="bfa17-165">Tuples vs `System.Tuple`</span></span>

<span data-ttu-id="bfa17-166">As tuplas do C#, que são apoiadas por <xref:System.ValueTuple?displayProperty=nameWithType> tipos, são diferentes das tuplas representadas por <xref:System.Tuple?displayProperty=nameWithType> tipos.</span><span class="sxs-lookup"><span data-stu-id="bfa17-166">C# tuples, which are backed by <xref:System.ValueTuple?displayProperty=nameWithType> types, are different from tuples that are represented by <xref:System.Tuple?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="bfa17-167">As principais diferenças são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="bfa17-167">The main differences are as follows:</span></span>

- <span data-ttu-id="bfa17-168">`ValueTuple`os tipos são [tipos de valor](value-types.md).</span><span class="sxs-lookup"><span data-stu-id="bfa17-168">`ValueTuple` types are [value types](value-types.md).</span></span> <span data-ttu-id="bfa17-169">`Tuple`tipos são [tipos de referência](../keywords/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="bfa17-169">`Tuple` types are [reference types](../keywords/reference-types.md).</span></span>
- <span data-ttu-id="bfa17-170">`ValueTuple`os tipos são mutáveis.</span><span class="sxs-lookup"><span data-stu-id="bfa17-170">`ValueTuple` types are mutable.</span></span> <span data-ttu-id="bfa17-171">`Tuple`os tipos são imutáveis.</span><span class="sxs-lookup"><span data-stu-id="bfa17-171">`Tuple` types are immutable.</span></span>
- <span data-ttu-id="bfa17-172">Os membros de dados dos `ValueTuple` tipos são campos.</span><span class="sxs-lookup"><span data-stu-id="bfa17-172">Data members of `ValueTuple` types are fields.</span></span> <span data-ttu-id="bfa17-173">Os membros de dados dos `Tuple` tipos são propriedades.</span><span class="sxs-lookup"><span data-stu-id="bfa17-173">Data members of `Tuple` types are properties.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="bfa17-174">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="bfa17-174">C# language specification</span></span>

<span data-ttu-id="bfa17-175">Para obter mais informações, consulte as seguintes notas de proposta de recurso:</span><span class="sxs-lookup"><span data-stu-id="bfa17-175">For more information, see the following feature proposal notes:</span></span>

- [<span data-ttu-id="bfa17-176">Inferir nomes de tupla (também conhecido como inicializadores de projeção de tupla)</span><span class="sxs-lookup"><span data-stu-id="bfa17-176">Infer tuple names (aka. tuple projection initializers)</span></span>](~/_csharplang/proposals/csharp-7.1/infer-tuple-names.md)
- [<span data-ttu-id="bfa17-177">Suporte para `==` e `!=` em tipos de tupla</span><span class="sxs-lookup"><span data-stu-id="bfa17-177">Support for `==` and `!=` on tuple types</span></span>](~/_csharplang/proposals/csharp-7.3/tuple-equality.md)

## <a name="see-also"></a><span data-ttu-id="bfa17-178">Veja também</span><span class="sxs-lookup"><span data-stu-id="bfa17-178">See also</span></span>

- [<span data-ttu-id="bfa17-179">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="bfa17-179">C# reference</span></span>](../index.md)
- [<span data-ttu-id="bfa17-180">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="bfa17-180">Value types</span></span>](value-types.md)
- [<span data-ttu-id="bfa17-181">Escolhendo entre tipos anônimos e de tupla</span><span class="sxs-lookup"><span data-stu-id="bfa17-181">Choosing between anonymous and tuple types</span></span>](../../../standard/base-types/choosing-between-anonymous-and-tuple.md)
- <xref:System.ValueTuple?displayProperty=nameWithType>
