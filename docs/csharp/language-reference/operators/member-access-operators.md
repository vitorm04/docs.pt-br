---
title: Operadores e expressões de acesso a membros - referência C#
description: Aprenda sobre operadores de C# que você pode usar para acessar membros de tipo.
ms.date: 09/18/2019
author: pkulikov
f1_keywords:
- ._CSharpKeyword
- '[]_CSharpKeyword'
- ()_CSharpKeyword
- ^_CSharpKeyword
- .._CSharpKeyword
helpviewer_keywords:
- member access operators [C#]
- member access operator [C#]
- dot operator [C#]
- . operator [C#]
- subscript operator [C#]
- square brackets [] operator [C#]
- indexer operator [C#]
- '[] operator [C#]'
- null-conditional operators [C#]
- Elvis operator [C#]
- ?. operator [C#]
- ?[] operator [C#]
- invocation operator [C#]
- method call [C#]
- method invocation [C#]
- delegate invocation [C#]
- () operator [C#]
- ^ operator [C#]
- index from end operator [C#]
- hat operator [C#]
- .. operator [C#]
- range operator [C#]
ms.openlocfilehash: da2ca4517bd007678d74ae9b76e10cad4c2696b4
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546634"
---
# <a name="member-access-operators-and-expressions-c-reference"></a><span data-ttu-id="59a00-103">Operadores e expressões de acesso a membros (referência C#)</span><span class="sxs-lookup"><span data-stu-id="59a00-103">Member access operators and expressions (C# reference)</span></span>

<span data-ttu-id="59a00-104">Você pode usar os seguintes operadores e expressões quando acessar um membro do tipo:</span><span class="sxs-lookup"><span data-stu-id="59a00-104">You can use the following operators and expressions when you access a type member:</span></span>

- <span data-ttu-id="59a00-105">(acesso ao membro): para acessar um membro de um namespace ou um tipo [ `.` ](#member-access-expression-)</span><span class="sxs-lookup"><span data-stu-id="59a00-105">[`.` (member access)](#member-access-expression-): to access a member of a namespace or a type</span></span>
- <span data-ttu-id="59a00-106">[(acesso a elemento de matriz ou indexador) : para acessar um elemento de matriz ou um indexador de tipo `[]` ](#indexer-operator-)</span><span class="sxs-lookup"><span data-stu-id="59a00-106">[`[]` (array element or indexer access)](#indexer-operator-): to access an array element or a type indexer</span></span>
- <span data-ttu-id="59a00-107">[e `?[]` (operadores condicionais nulos) : realizar uma operação de acesso a membros ou elementos somente se um operand não for `?.` ](#null-conditional-operators--and-)nulo</span><span class="sxs-lookup"><span data-stu-id="59a00-107">[`?.` and `?[]` (null-conditional operators)](#null-conditional-operators--and-): to perform a member or element access operation only if an operand is non-null</span></span>
- <span data-ttu-id="59a00-108">(invocação) : chamar um método acessado ou invocar um delegado [ `()` ](#invocation-expression-)</span><span class="sxs-lookup"><span data-stu-id="59a00-108">[`()` (invocation)](#invocation-expression-): to call an accessed method or invoke a delegate</span></span>
- <span data-ttu-id="59a00-109">[(índice a partir do fim): para indicar que a posição do elemento é do final de uma seqüência `^` ](#index-from-end-operator-)</span><span class="sxs-lookup"><span data-stu-id="59a00-109">[`^` (index from end)](#index-from-end-operator-): to indicate that the element position is from the end of a sequence</span></span>
- <span data-ttu-id="59a00-110">(intervalo) : para especificar uma gama de índices que você pode usar para obter uma gama de elementos de seqüência [ `..` ](#range-operator-)</span><span class="sxs-lookup"><span data-stu-id="59a00-110">[`..` (range)](#range-operator-): to specify a range of indices that you can use to obtain a range of sequence elements</span></span>

## <a name="member-access-expression-"></a><span data-ttu-id="59a00-111">Expressão de acesso ao membro .</span><span class="sxs-lookup"><span data-stu-id="59a00-111">Member access expression .</span></span>

<span data-ttu-id="59a00-112">Use o token `.` para acessar um membro de um namespace ou um tipo, como demonstram os exemplos a seguir:</span><span class="sxs-lookup"><span data-stu-id="59a00-112">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="59a00-113">Use `.` para acessar um namespace aninhado dentro de um namespace, como mostra o exemplo a seguir de uma [ `using` diretiva:](../keywords/using-directive.md)</span><span class="sxs-lookup"><span data-stu-id="59a00-113">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](snippets/MemberAccessOperators.cs#NestedNamespace)]

- <span data-ttu-id="59a00-114">Use `.` para formar um *nome qualificado* para acessar um tipo dentro de um namespace, como mostra o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="59a00-114">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](snippets/MemberAccessOperators.cs#QualifiedName)]

  <span data-ttu-id="59a00-115">Use [ `using` ](../keywords/using-directive.md) uma diretiva para tornar opcional o uso de nomes qualificados.</span><span class="sxs-lookup"><span data-stu-id="59a00-115">Use a [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="59a00-116">Use `.` para acessar [membros de tipo](../../programming-guide/classes-and-structs/index.md#members), estático e não-estático, como mostra o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="59a00-116">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](snippets/MemberAccessOperators.cs#TypeMemberAccess)]

<span data-ttu-id="59a00-117">Você também pode usar `.` para acessar um [método de extensão](../../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="59a00-117">You can also use `.` to access an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="indexer-operator-"></a><span data-ttu-id="59a00-118">Operador de indexador []</span><span class="sxs-lookup"><span data-stu-id="59a00-118">Indexer operator []</span></span>

<span data-ttu-id="59a00-119">Os colchetes, `[]`, normalmente são usados para acesso de elemento de matriz, indexador ou ponteiro.</span><span class="sxs-lookup"><span data-stu-id="59a00-119">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

### <a name="array-access"></a><span data-ttu-id="59a00-120">Acesso de matriz</span><span class="sxs-lookup"><span data-stu-id="59a00-120">Array access</span></span>

<span data-ttu-id="59a00-121">O exemplo a seguir demonstra como acessar elementos de matriz:</span><span class="sxs-lookup"><span data-stu-id="59a00-121">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](snippets/MemberAccessOperators.cs#Arrays)]

<span data-ttu-id="59a00-122">Se um índice de matriz estiver fora dos limites da dimensão correspondente de uma matriz, uma <xref:System.IndexOutOfRangeException> será gerada.</span><span class="sxs-lookup"><span data-stu-id="59a00-122">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="59a00-123">Como mostra o exemplo anterior, você também usar colchetes quando declara um tipo de matriz ou instancia uma instância de matriz.</span><span class="sxs-lookup"><span data-stu-id="59a00-123">As the preceding example shows, you also use square brackets when you declare an array type or instantiate an array instance.</span></span>

<span data-ttu-id="59a00-124">Para obter mais informações sobre matrizes, confira [Matrizes](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="59a00-124">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

### <a name="indexer-access"></a><span data-ttu-id="59a00-125">Acesso de indexador</span><span class="sxs-lookup"><span data-stu-id="59a00-125">Indexer access</span></span>

<span data-ttu-id="59a00-126">O exemplo a seguir <xref:System.Collections.Generic.Dictionary%602> usa o tipo .NET para demonstrar o acesso ao indexador:</span><span class="sxs-lookup"><span data-stu-id="59a00-126">The following example uses the .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](snippets/MemberAccessOperators.cs#Indexers)]

<span data-ttu-id="59a00-127">Os indexadores permitem indexar instâncias de um tipo definido pelo usuário de maneira semelhante à indexação de matriz.</span><span class="sxs-lookup"><span data-stu-id="59a00-127">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="59a00-128">Ao contrário dos índices de matriz, que devem ser inteiros, os parâmetros do indexador podem ser declarados de qualquer tipo.</span><span class="sxs-lookup"><span data-stu-id="59a00-128">Unlike array indices, which must be integer, the indexer parameters can be declared to be of any type.</span></span>

<span data-ttu-id="59a00-129">Para obter mais informações sobre indexadores, confira [Indexadores](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="59a00-129">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="59a00-130">Outros usos de []</span><span class="sxs-lookup"><span data-stu-id="59a00-130">Other usages of []</span></span>

<span data-ttu-id="59a00-131">Para saber mais sobre o acesso a elemento de ponteiro, confira a seção [Operador de acesso a elemento de ponteiro []](pointer-related-operators.md#pointer-element-access-operator-) do artigo [Operadores relacionados a ponteiro](pointer-related-operators.md).</span><span class="sxs-lookup"><span data-stu-id="59a00-131">For information about pointer element access, see the [Pointer element access operator []](pointer-related-operators.md#pointer-element-access-operator-) section of the [Pointer related operators](pointer-related-operators.md) article.</span></span>

<span data-ttu-id="59a00-132">Os colchetes também são usados para especificar [atributos](../../programming-guide/concepts/attributes/index.md):</span><span class="sxs-lookup"><span data-stu-id="59a00-132">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a><span data-ttu-id="59a00-133">Operadores condicionais nulos ?.</span><span class="sxs-lookup"><span data-stu-id="59a00-133">Null-conditional operators ?.</span></span> <span data-ttu-id="59a00-134">e ?[]</span><span class="sxs-lookup"><span data-stu-id="59a00-134">and ?[]</span></span>

<span data-ttu-id="59a00-135">Disponível em C# 6 e posterior, um operador condicionado a `?[]`membros aplica um acesso a [membros](#member-access-expression-), `?.`ou acesso a [elementos](#indexer-operator-), operação ao seu operativo e somente se esse operand avaliar a não-nulo; caso contrário, `null`ele retorna .</span><span class="sxs-lookup"><span data-stu-id="59a00-135">Available in C# 6 and later, a null-conditional operator applies a [member access](#member-access-expression-), `?.`, or [element access](#indexer-operator-), `?[]`, operation to its operand only if that operand evaluates to non-null; otherwise, it returns `null`.</span></span> <span data-ttu-id="59a00-136">Isto é</span><span class="sxs-lookup"><span data-stu-id="59a00-136">That is,</span></span>

- <span data-ttu-id="59a00-137">Se `a` avaliar `null`, o `a?.x` resultado `a?[x]` `null`de ou é .</span><span class="sxs-lookup"><span data-stu-id="59a00-137">If `a` evaluates to `null`, the result of `a?.x` or `a?[x]` is `null`.</span></span>
- <span data-ttu-id="59a00-138">Se `a` avalia-se para não nulo, o resultado `a?.x` ou `a.x` `a[x]` `a?[x]` é o mesmo que o resultado ou, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="59a00-138">If `a` evaluates to non-null, the result of `a?.x` or `a?[x]` is the same as the result of `a.x` or `a[x]`, respectively.</span></span>

  > [!NOTE]
  > <span data-ttu-id="59a00-139">Se `a.x` `a[x]` ou lançar `a?.x` uma `a?[x]` exceção, ou lançar `a`a mesma exceção para não-nulo .</span><span class="sxs-lookup"><span data-stu-id="59a00-139">If `a.x` or `a[x]` throws an exception, `a?.x` or `a?[x]` would throw the same exception for non-null `a`.</span></span> <span data-ttu-id="59a00-140">Por exemplo, `a` se for uma instância `x` de matriz não `a` `a?[x]` nula <xref:System.IndexOutOfRangeException>e estiver fora dos limites de , lançaria um .</span><span class="sxs-lookup"><span data-stu-id="59a00-140">For example, if `a` is a non-null array instance and `x` is outside the bounds of `a`, `a?[x]` would throw an <xref:System.IndexOutOfRangeException>.</span></span>

<span data-ttu-id="59a00-141">Os operadores condicionais nulos estão entrando em curto-circuito.</span><span class="sxs-lookup"><span data-stu-id="59a00-141">The null-conditional operators are short-circuiting.</span></span> <span data-ttu-id="59a00-142">Ou seja, se uma operação em uma cadeia de membro operações condicionais de acesso a membro ou elemento retornar `null`, o restante da cadeia não será executado.</span><span class="sxs-lookup"><span data-stu-id="59a00-142">That is, if one operation in a chain of conditional member or element access operations returns `null`, the rest of the chain doesn't execute.</span></span> <span data-ttu-id="59a00-143">No exemplo a seguir, `B` não será avaliado se `A` for avaliado como `null` e `C` não será avaliado se `A` ou `B` for avaliado como `null`:</span><span class="sxs-lookup"><span data-stu-id="59a00-143">In the following example, `B` is not evaluated if `A` evaluates to `null` and `C` is not evaluated if `A` or `B` evaluates to `null`:</span></span>

```csharp
A?.B?.Do(C);
A?.B?[C];
```

<span data-ttu-id="59a00-144">O exemplo a seguir demonstra o uso dos operadores `?.` e `?[]`:</span><span class="sxs-lookup"><span data-stu-id="59a00-144">The following example demonstrates the usage of the `?.` and `?[]` operators:</span></span>

[!code-csharp-interactive[null-conditional operators](snippets/MemberAccessOperators.cs#NullConditional)]

<span data-ttu-id="59a00-145">O exemplo anterior também usa o [operador `??` de coalizão nula](null-coalescing-operator.md) para especificar uma expressão alternativa `null`para avaliar caso o resultado de uma operação condicionada seja .</span><span class="sxs-lookup"><span data-stu-id="59a00-145">The preceding example also uses the [null-coalescing operator `??`](null-coalescing-operator.md) to specify an alternative expression to evaluate in case the result of a null-conditional operation is `null`.</span></span>

<span data-ttu-id="59a00-146">O operador de acesso do membro condicional nulo `?.` também é conhecido como o operador Elvis.</span><span class="sxs-lookup"><span data-stu-id="59a00-146">The null-conditional member access operator `?.` is also known as the Elvis operator.</span></span>

### <a name="thread-safe-delegate-invocation"></a><span data-ttu-id="59a00-147">Invocação de delegado thread-safe</span><span class="sxs-lookup"><span data-stu-id="59a00-147">Thread-safe delegate invocation</span></span>

<span data-ttu-id="59a00-148">Use o operador `?.` para verificar se um delegado é não nulo e chame-o de uma forma thread-safe (por exemplo, quando você [aciona um evento](../../../standard/events/how-to-raise-and-consume-events.md)), conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="59a00-148">Use the `?.` operator to check if a delegate is non-null and invoke it in a thread-safe way (for example, when you [raise an event](../../../standard/events/how-to-raise-and-consume-events.md)), as the following code shows:</span></span>

```csharp
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="59a00-149">Esse código é equivalente ao código a seguir que você usaria no C# 5 ou anterior:</span><span class="sxs-lookup"><span data-stu-id="59a00-149">That code is equivalent to the following code that you would use in C# 5 or earlier:</span></span>

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-expression-"></a><span data-ttu-id="59a00-150">Expressão de invocação ()</span><span class="sxs-lookup"><span data-stu-id="59a00-150">Invocation expression ()</span></span>

<span data-ttu-id="59a00-151">Use parênteses, `()`, para chamar um [método](../../programming-guide/classes-and-structs/methods.md) ou invocar um [delegado](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="59a00-151">Use parentheses, `()`, to call a [method](../../programming-guide/classes-and-structs/methods.md) or invoke a [delegate](../../programming-guide/delegates/index.md).</span></span>

<span data-ttu-id="59a00-152">O exemplo a seguir demonstra como chamar um método (com ou sem argumentos) e invocar um delegado:</span><span class="sxs-lookup"><span data-stu-id="59a00-152">The following example demonstrates how to call a method, with or without arguments, and invoke a delegate:</span></span>

[!code-csharp-interactive[invocation with ()](snippets/MemberAccessOperators.cs#Invocation)]

<span data-ttu-id="59a00-153">Você também pode usar parênteses ao invocar um [construtor](../../programming-guide/classes-and-structs/constructors.md) com o operador [`new`](new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="59a00-153">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with the [`new`](new-operator.md) operator.</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="59a00-154">Outros usos de ()</span><span class="sxs-lookup"><span data-stu-id="59a00-154">Other usages of ()</span></span>

<span data-ttu-id="59a00-155">Você também pode usar parênteses para ajustar a ordem na qual as operações em uma expressão são avaliadas.</span><span class="sxs-lookup"><span data-stu-id="59a00-155">You also use parentheses to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="59a00-156">Para saber mais, confira [Operadores C#](index.md).</span><span class="sxs-lookup"><span data-stu-id="59a00-156">For more information, see [C# operators](index.md).</span></span>

<span data-ttu-id="59a00-157">[Expressões de conversão](type-testing-and-cast.md#cast-operator-), que executam conversões de tipo explícitas, também usam parênteses.</span><span class="sxs-lookup"><span data-stu-id="59a00-157">[Cast expressions](type-testing-and-cast.md#cast-operator-), which perform explicit type conversions, also use parentheses.</span></span>

## <a name="index-from-end-operator-"></a><span data-ttu-id="59a00-158">Índice do operador final ^</span><span class="sxs-lookup"><span data-stu-id="59a00-158">Index from end operator ^</span></span>

<span data-ttu-id="59a00-159">Disponível em C# 8.0 `^` e posteriormente, o operador indica a posição do elemento a partir do final de uma seqüência.</span><span class="sxs-lookup"><span data-stu-id="59a00-159">Available in C# 8.0 and later, the `^` operator indicates the element position from the end of a sequence.</span></span> <span data-ttu-id="59a00-160">Para uma seqüência de `length`comprimento, `length - n` `^n` aponta para o elemento com deslocamento desde o início de uma seqüência.</span><span class="sxs-lookup"><span data-stu-id="59a00-160">For a sequence of length `length`, `^n` points to the element with offset `length - n` from the start of a sequence.</span></span> <span data-ttu-id="59a00-161">Por exemplo, `^1` aponta para o último `^length` elemento de uma seqüência e aponta para o primeiro elemento de uma seqüência.</span><span class="sxs-lookup"><span data-stu-id="59a00-161">For example, `^1` points to the last element of a sequence and `^length` points to the first element of a sequence.</span></span>

[!code-csharp[index from end](snippets/MemberAccessOperators.cs#IndexFromEnd)]

<span data-ttu-id="59a00-162">Como o exemplo anterior `^e` mostra, <xref:System.Index?displayProperty=nameWithType> a expressão é do tipo.</span><span class="sxs-lookup"><span data-stu-id="59a00-162">As the preceding example shows, expression `^e` is of the <xref:System.Index?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="59a00-163">Em `^e`expressão, o `e` resultado deve ser `int`implicitamente conversível para .</span><span class="sxs-lookup"><span data-stu-id="59a00-163">In expression `^e`, the result of `e` must be implicitly convertible to `int`.</span></span>

<span data-ttu-id="59a00-164">Você também pode `^` usar o operador com o [operador de alcance](#range-operator-) para criar uma série de índices.</span><span class="sxs-lookup"><span data-stu-id="59a00-164">You also can use the `^` operator with the [range operator](#range-operator-) to create a range of indices.</span></span> <span data-ttu-id="59a00-165">Para obter mais informações, consulte [Índices e faixas](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="59a00-165">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="range-operator-"></a><span data-ttu-id="59a00-166">Operador de alcance ..</span><span class="sxs-lookup"><span data-stu-id="59a00-166">Range operator ..</span></span>

<span data-ttu-id="59a00-167">Disponível em C# 8.0 `..` e posterior, o operador especifica o início e o fim de uma série de índices como seus operadores.</span><span class="sxs-lookup"><span data-stu-id="59a00-167">Available in C# 8.0 and later, the `..` operator specifies the start and end of a range of indices as its operands.</span></span> <span data-ttu-id="59a00-168">O operand esquerdo é um começo *inclusivo* de uma faixa.</span><span class="sxs-lookup"><span data-stu-id="59a00-168">The left-hand operand is an *inclusive* start of a range.</span></span> <span data-ttu-id="59a00-169">O operand direito é um fim *exclusivo* de um alcance.</span><span class="sxs-lookup"><span data-stu-id="59a00-169">The right-hand operand is an *exclusive* end of a range.</span></span> <span data-ttu-id="59a00-170">Qualquer um dos operands pode ser um índice desde o início ou a partir do final de uma seqüência, como o exemplo a seguir mostra:</span><span class="sxs-lookup"><span data-stu-id="59a00-170">Either of operands can be an index from the start or from the end of a sequence, as the following example shows:</span></span>

[!code-csharp[range examples](snippets/MemberAccessOperators.cs#Ranges)]

<span data-ttu-id="59a00-171">Como o exemplo anterior `a..b` mostra, <xref:System.Range?displayProperty=nameWithType> a expressão é do tipo.</span><span class="sxs-lookup"><span data-stu-id="59a00-171">As the preceding example shows, expression `a..b` is of the <xref:System.Range?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="59a00-172">Em `a..b`expressão, os `a` `b` resultados e devem `int` ser <xref:System.Index>implicitamente conversíveis para ou .</span><span class="sxs-lookup"><span data-stu-id="59a00-172">In expression `a..b`, the results of `a` and `b` must be implicitly convertible to `int` or <xref:System.Index>.</span></span>

<span data-ttu-id="59a00-173">Você pode omitir qualquer um dos `..` operands do operador para obter um intervalo aberto:</span><span class="sxs-lookup"><span data-stu-id="59a00-173">You can omit any of the operands of the `..` operator to obtain an open-ended range:</span></span>

- <span data-ttu-id="59a00-174">`a..` equivale a `a..^0`</span><span class="sxs-lookup"><span data-stu-id="59a00-174">`a..` is equivalent to `a..^0`</span></span>
- <span data-ttu-id="59a00-175">`..b` equivale a `0..b`</span><span class="sxs-lookup"><span data-stu-id="59a00-175">`..b` is equivalent to `0..b`</span></span>
- <span data-ttu-id="59a00-176">`..` equivale a `0..^0`</span><span class="sxs-lookup"><span data-stu-id="59a00-176">`..` is equivalent to `0..^0`</span></span>

[!code-csharp[ranges with omitted operands](snippets/MemberAccessOperators.cs#RangesOptional)]

<span data-ttu-id="59a00-177">Para obter mais informações, consulte [Índices e faixas](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="59a00-177">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="59a00-178">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="59a00-178">Operator overloadability</span></span>

<span data-ttu-id="59a00-179">Os `.` `()` `..` operadores `^`não podem ser sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="59a00-179">The `.`, `()`, `^`, and `..` operators cannot be overloaded.</span></span> <span data-ttu-id="59a00-180">O operador `[]` também é considerado um operador não sobrecarregável.</span><span class="sxs-lookup"><span data-stu-id="59a00-180">The `[]` operator is also considered a non-overloadable operator.</span></span> <span data-ttu-id="59a00-181">Use [indexadores](../../programming-guide/indexers/index.md) para permitir a indexação com tipos definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="59a00-181">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="59a00-182">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="59a00-182">C# language specification</span></span>

<span data-ttu-id="59a00-183">Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="59a00-183">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="59a00-184">Acesso ao membro</span><span class="sxs-lookup"><span data-stu-id="59a00-184">Member access</span></span>](~/_csharplang/spec/expressions.md#member-access)
- [<span data-ttu-id="59a00-185">Acesso a elemento</span><span class="sxs-lookup"><span data-stu-id="59a00-185">Element access</span></span>](~/_csharplang/spec/expressions.md#element-access)
- [<span data-ttu-id="59a00-186">Operador condicional nulo</span><span class="sxs-lookup"><span data-stu-id="59a00-186">Null-conditional operator</span></span>](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [<span data-ttu-id="59a00-187">Expressões de invocação</span><span class="sxs-lookup"><span data-stu-id="59a00-187">Invocation expressions</span></span>](~/_csharplang/spec/expressions.md#invocation-expressions)

<span data-ttu-id="59a00-188">Para obter mais informações sobre índices e faixas, consulte a [nota de proposta do recurso](~/_csharplang/proposals/csharp-8.0/ranges.md).</span><span class="sxs-lookup"><span data-stu-id="59a00-188">For more information about indices and ranges, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="59a00-189">Confira também</span><span class="sxs-lookup"><span data-stu-id="59a00-189">See also</span></span>

- [<span data-ttu-id="59a00-190">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="59a00-190">C# reference</span></span>](../index.md)
- [<span data-ttu-id="59a00-191">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="59a00-191">C# operators</span></span>](index.md)
- [<span data-ttu-id="59a00-192">?? (operador de união nula)</span><span class="sxs-lookup"><span data-stu-id="59a00-192">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="59a00-193">:: operador</span><span class="sxs-lookup"><span data-stu-id="59a00-193">:: operator</span></span>](namespace-alias-qualifier.md)
