---
title: Operadores de acesso a membro - Referência de C#
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
ms.openlocfilehash: ba2a8cd4995b9baab2071d3fb3c7980e45565692
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039006"
---
# <a name="member-access-operators-c-reference"></a><span data-ttu-id="e30a3-103">Operadores de acesso a membro (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="e30a3-103">Member access operators (C# reference)</span></span>

<span data-ttu-id="e30a3-104">Você pode usar os seguintes operadores ao acessar um membro de tipo:</span><span class="sxs-lookup"><span data-stu-id="e30a3-104">You can use the following operators when you access a type member:</span></span>

- <span data-ttu-id="e30a3-105">[`.` (acesso a membro)](#member-access-operator-): para acessar um membro de um namespace ou um tipo</span><span class="sxs-lookup"><span data-stu-id="e30a3-105">[`.` (member access)](#member-access-operator-): to access a member of a namespace or a type</span></span>
- <span data-ttu-id="e30a3-106">[`[]` (acesso a um indexador ou elemento de matriz)](#indexer-operator-): para acessar um elemento de matriz ou um indexador de tipo</span><span class="sxs-lookup"><span data-stu-id="e30a3-106">[`[]` (array element or indexer access)](#indexer-operator-): to access an array element or a type indexer</span></span>
- <span data-ttu-id="e30a3-107">[`?.` e `?[]` (operadores condicionais nulos)](#null-conditional-operators--and-): para executar uma operação de acesso a membro ou elemento somente se um operando for não nulo</span><span class="sxs-lookup"><span data-stu-id="e30a3-107">[`?.` and `?[]` (null-conditional operators)](#null-conditional-operators--and-): to perform a member or element access operation only if an operand is non-null</span></span>
- <span data-ttu-id="e30a3-108">[`()` (invocação)](#invocation-operator-): chamar um método acessado ou invocar um delegado</span><span class="sxs-lookup"><span data-stu-id="e30a3-108">[`()` (invocation)](#invocation-operator-): to call an accessed method or invoke a delegate</span></span>
- <span data-ttu-id="e30a3-109">[`^` (índice de fim)](#index-from-end-operator-): para indicar que a posição do elemento é do final de uma sequência</span><span class="sxs-lookup"><span data-stu-id="e30a3-109">[`^` (index from end)](#index-from-end-operator-): to indicate that the element position is from the end of a sequence</span></span>
- <span data-ttu-id="e30a3-110">[`..` (Range)](#range-operator-): para especificar um intervalo de índices que você pode usar para obter um intervalo de elementos de sequência</span><span class="sxs-lookup"><span data-stu-id="e30a3-110">[`..` (range)](#range-operator-): to specify a range of indices that you can use to obtain a range of sequence elements</span></span>

## <a name="member-access-operator-"></a><span data-ttu-id="e30a3-111">Operador de acesso a membro.</span><span class="sxs-lookup"><span data-stu-id="e30a3-111">Member access operator .</span></span>

<span data-ttu-id="e30a3-112">Use o token `.` para acessar um membro de um namespace ou um tipo, como demonstram os exemplos a seguir:</span><span class="sxs-lookup"><span data-stu-id="e30a3-112">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="e30a3-113">Use `.` para acessar um namespace aninhado dentro de um namespace, como mostra o exemplo a seguir de uma [diretiva `using`](../keywords/using-directive.md):</span><span class="sxs-lookup"><span data-stu-id="e30a3-113">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NestedNamespace)]

- <span data-ttu-id="e30a3-114">Use `.` para formar um *nome qualificado* para acessar um tipo dentro de um namespace, como mostra o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="e30a3-114">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#QualifiedName)]

  <span data-ttu-id="e30a3-115">Use uma [diretiva `using`](../keywords/using-directive.md) para tornar o uso de nomes qualificados opcional.</span><span class="sxs-lookup"><span data-stu-id="e30a3-115">Use a [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="e30a3-116">Use `.` para acessar [membros de tipo](../../programming-guide/classes-and-structs/index.md#members), estático e não-estático, como mostra o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="e30a3-116">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#TypeMemberAccess)]

<span data-ttu-id="e30a3-117">Você também pode usar `.` para acessar um [método de extensão](../../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="e30a3-117">You can also use `.` to access an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="indexer-operator-"></a><span data-ttu-id="e30a3-118">Operador de indexador []</span><span class="sxs-lookup"><span data-stu-id="e30a3-118">Indexer operator []</span></span>

<span data-ttu-id="e30a3-119">Os colchetes, `[]`, normalmente são usados para acesso de elemento de matriz, indexador ou ponteiro.</span><span class="sxs-lookup"><span data-stu-id="e30a3-119">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

### <a name="array-access"></a><span data-ttu-id="e30a3-120">Acesso de matriz</span><span class="sxs-lookup"><span data-stu-id="e30a3-120">Array access</span></span>

<span data-ttu-id="e30a3-121">O exemplo a seguir demonstra como acessar elementos de matriz:</span><span class="sxs-lookup"><span data-stu-id="e30a3-121">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Arrays)]

<span data-ttu-id="e30a3-122">Se um índice de matriz estiver fora dos limites da dimensão correspondente de uma matriz, uma <xref:System.IndexOutOfRangeException> será gerada.</span><span class="sxs-lookup"><span data-stu-id="e30a3-122">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="e30a3-123">Como mostra o exemplo anterior, você também usar colchetes quando declara um tipo de matriz ou instancia uma instância de matriz.</span><span class="sxs-lookup"><span data-stu-id="e30a3-123">As the preceding example shows, you also use square brackets when you declare an array type or instantiate an array instance.</span></span>

<span data-ttu-id="e30a3-124">Para obter mais informações sobre matrizes, confira [Matrizes](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="e30a3-124">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

### <a name="indexer-access"></a><span data-ttu-id="e30a3-125">Acesso de indexador</span><span class="sxs-lookup"><span data-stu-id="e30a3-125">Indexer access</span></span>

<span data-ttu-id="e30a3-126">O exemplo a seguir usa o tipo de <xref:System.Collections.Generic.Dictionary%602> .NET para demonstrar o acesso ao indexador:</span><span class="sxs-lookup"><span data-stu-id="e30a3-126">The following example uses the .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Indexers)]

<span data-ttu-id="e30a3-127">Os indexadores permitem indexar instâncias de um tipo definido pelo usuário de maneira semelhante à indexação de matriz.</span><span class="sxs-lookup"><span data-stu-id="e30a3-127">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="e30a3-128">Ao contrário dos índices de matriz, que devem ser inteiros, os parâmetros do indexador podem ser declarados como sendo de qualquer tipo.</span><span class="sxs-lookup"><span data-stu-id="e30a3-128">Unlike array indices, which must be integer, the indexer parameters can be declared to be of any type.</span></span>

<span data-ttu-id="e30a3-129">Para obter mais informações sobre indexadores, confira [Indexadores](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="e30a3-129">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="e30a3-130">Outros usos de []</span><span class="sxs-lookup"><span data-stu-id="e30a3-130">Other usages of []</span></span>

<span data-ttu-id="e30a3-131">Para saber mais sobre o acesso a elemento de ponteiro, confira a seção [Operador de acesso a elemento de ponteiro []](pointer-related-operators.md#pointer-element-access-operator-) do artigo [Operadores relacionados a ponteiro](pointer-related-operators.md).</span><span class="sxs-lookup"><span data-stu-id="e30a3-131">For information about pointer element access, see the [Pointer element access operator []](pointer-related-operators.md#pointer-element-access-operator-) section of the [Pointer related operators](pointer-related-operators.md) article.</span></span>

<span data-ttu-id="e30a3-132">Os colchetes também são usados para especificar [atributos](../../programming-guide/concepts/attributes/index.md):</span><span class="sxs-lookup"><span data-stu-id="e30a3-132">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a><span data-ttu-id="e30a3-133">Operadores condicionais nulos ?.</span><span class="sxs-lookup"><span data-stu-id="e30a3-133">Null-conditional operators ?.</span></span> <span data-ttu-id="e30a3-134">e ?[]</span><span class="sxs-lookup"><span data-stu-id="e30a3-134">and ?[]</span></span>

<span data-ttu-id="e30a3-135">Disponível no C# 6 e versões posteriores, um operador nulo condicional aplicará a seu operando uma operação de acesso a membro, `?.`, ou de acesso a elemento, `?[]`, somente se o operando for avaliado como não nulo.</span><span class="sxs-lookup"><span data-stu-id="e30a3-135">Available in C# 6 and later, a null-conditional operator applies a member access, `?.`, or element access, `?[]`, operation to its operand only if that operand evaluates to non-null.</span></span> <span data-ttu-id="e30a3-136">Se o operando for avaliado como `null`, o resultado da aplicação do operador será `null`.</span><span class="sxs-lookup"><span data-stu-id="e30a3-136">If the operand evaluates to `null`, the result of applying the operator is `null`.</span></span> <span data-ttu-id="e30a3-137">O operador de acesso do membro condicional nulo `?.` também é conhecido como o operador Elvis.</span><span class="sxs-lookup"><span data-stu-id="e30a3-137">The null-conditional member access operator `?.` is also known as the Elvis operator.</span></span>

<span data-ttu-id="e30a3-138">Os operadores condicionais nulos estão entrando em curto-circuito.</span><span class="sxs-lookup"><span data-stu-id="e30a3-138">The null-conditional operators are short-circuiting.</span></span> <span data-ttu-id="e30a3-139">Ou seja, se uma operação em uma cadeia de membro operações condicionais de acesso a membro ou elemento retornar `null`, o restante da cadeia não será executado.</span><span class="sxs-lookup"><span data-stu-id="e30a3-139">That is, if one operation in a chain of conditional member or element access operations returns `null`, the rest of the chain doesn't execute.</span></span> <span data-ttu-id="e30a3-140">No exemplo a seguir, `B` não será avaliado se `A` for avaliado como `null` e `C` não será avaliado se `A` ou `B` for avaliado como `null`:</span><span class="sxs-lookup"><span data-stu-id="e30a3-140">In the following example, `B` is not evaluated if `A` evaluates to `null` and `C` is not evaluated if `A` or `B` evaluates to `null`:</span></span>

```csharp
A?.B?.Do(C);
A?.B?[C];
```

<span data-ttu-id="e30a3-141">O exemplo a seguir demonstra o uso dos operadores `?.` e `?[]`:</span><span class="sxs-lookup"><span data-stu-id="e30a3-141">The following example demonstrates the usage of the `?.` and `?[]` operators:</span></span>

[!code-csharp-interactive[null-conditional operators](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NullConditional)]

<span data-ttu-id="e30a3-142">O exemplo anterior também usa o [operador de União nulo `??`](null-coalescing-operator.md) para especificar uma expressão alternativa a ser avaliada, caso o resultado de uma operação condicional nula seja `null`.</span><span class="sxs-lookup"><span data-stu-id="e30a3-142">The preceding example also uses the [null-coalescing operator `??`](null-coalescing-operator.md) to specify an alternative expression to evaluate in case the result of a null-conditional operation is `null`.</span></span>

### <a name="thread-safe-delegate-invocation"></a><span data-ttu-id="e30a3-143">Invocação de delegado thread-safe</span><span class="sxs-lookup"><span data-stu-id="e30a3-143">Thread-safe delegate invocation</span></span>

<span data-ttu-id="e30a3-144">Use o operador `?.` para verificar se um delegado é não nulo e chame-o de uma forma thread-safe (por exemplo, quando você [aciona um evento](../../../standard/events/how-to-raise-and-consume-events.md)), conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="e30a3-144">Use the `?.` operator to check if a delegate is non-null and invoke it in a thread-safe way (for example, when you [raise an event](../../../standard/events/how-to-raise-and-consume-events.md)), as the following code shows:</span></span>

```csharp
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="e30a3-145">Esse código é equivalente ao código a seguir que você usaria no C# 5 ou anterior:</span><span class="sxs-lookup"><span data-stu-id="e30a3-145">That code is equivalent to the following code that you would use in C# 5 or earlier:</span></span>

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-operator-"></a><span data-ttu-id="e30a3-146">Operador de invocação ()</span><span class="sxs-lookup"><span data-stu-id="e30a3-146">Invocation operator ()</span></span>

<span data-ttu-id="e30a3-147">Use parênteses, `()`, para chamar um [método](../../programming-guide/classes-and-structs/methods.md) ou invocar um [delegado](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="e30a3-147">Use parentheses, `()`, to call a [method](../../programming-guide/classes-and-structs/methods.md) or invoke a [delegate](../../programming-guide/delegates/index.md).</span></span>

<span data-ttu-id="e30a3-148">O exemplo a seguir demonstra como chamar um método (com ou sem argumentos) e invocar um delegado:</span><span class="sxs-lookup"><span data-stu-id="e30a3-148">The following example demonstrates how to call a method, with or without arguments, and invoke a delegate:</span></span>

[!code-csharp-interactive[invocation with ()](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Invocation)]

<span data-ttu-id="e30a3-149">Você também pode usar parênteses ao invocar um [construtor](../../programming-guide/classes-and-structs/constructors.md) com o operador [`new`](new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="e30a3-149">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with the [`new`](new-operator.md) operator.</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="e30a3-150">Outros usos de ()</span><span class="sxs-lookup"><span data-stu-id="e30a3-150">Other usages of ()</span></span>

<span data-ttu-id="e30a3-151">Você também pode usar parênteses para ajustar a ordem na qual as operações em uma expressão são avaliadas.</span><span class="sxs-lookup"><span data-stu-id="e30a3-151">You also use parentheses to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="e30a3-152">Para saber mais, confira [Operadores C#](index.md).</span><span class="sxs-lookup"><span data-stu-id="e30a3-152">For more information, see [C# operators](index.md).</span></span>

<span data-ttu-id="e30a3-153">[Expressões de conversão](type-testing-and-cast.md#cast-operator-), que executam conversões de tipo explícitas, também usam parênteses.</span><span class="sxs-lookup"><span data-stu-id="e30a3-153">[Cast expressions](type-testing-and-cast.md#cast-operator-), which perform explicit type conversions, also use parentheses.</span></span>

## <a name="index-from-end-operator-"></a><span data-ttu-id="e30a3-154">Índice do operador end ^</span><span class="sxs-lookup"><span data-stu-id="e30a3-154">Index from end operator ^</span></span>

<span data-ttu-id="e30a3-155">Disponível em C# 8,0 e posterior, o operador`^`indica a posição do elemento do final de uma sequência.</span><span class="sxs-lookup"><span data-stu-id="e30a3-155">Available in C# 8.0 and later, the `^` operator indicates the element position from the end of a sequence.</span></span> <span data-ttu-id="e30a3-156">Para uma sequência de comprimento `length`, `^n` aponta para o elemento com deslocamento `length - n` do início de uma sequência.</span><span class="sxs-lookup"><span data-stu-id="e30a3-156">For a sequence of length `length`, `^n` points to the element with offset `length - n` from the start of a sequence.</span></span> <span data-ttu-id="e30a3-157">Por exemplo, `^1` aponta para o último elemento de uma sequência e `^length` aponta para o primeiro elemento de uma sequência.</span><span class="sxs-lookup"><span data-stu-id="e30a3-157">For example, `^1` points to the last element of a sequence and `^length` points to the first element of a sequence.</span></span>

[!code-csharp[index from end](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#IndexFromEnd)]

<span data-ttu-id="e30a3-158">Como mostra o exemplo anterior, Expression `^e` é do tipo <xref:System.Index?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e30a3-158">As the preceding example shows, expression `^e` is of the <xref:System.Index?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="e30a3-159">No Expression `^e`, o resultado de `e` deve ser implicitamente conversível em `int`.</span><span class="sxs-lookup"><span data-stu-id="e30a3-159">In expression `^e`, the result of `e` must be implicitly convertible to `int`.</span></span>

<span data-ttu-id="e30a3-160">Você também pode usar o operador `^` com o [operador Range](#range-operator-) para criar um intervalo de índices.</span><span class="sxs-lookup"><span data-stu-id="e30a3-160">You also can use the `^` operator with the [range operator](#range-operator-) to create a range of indices.</span></span> <span data-ttu-id="e30a3-161">Para obter mais informações, consulte [índices e intervalos](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="e30a3-161">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="range-operator-"></a><span data-ttu-id="e30a3-162">Operador de intervalo..</span><span class="sxs-lookup"><span data-stu-id="e30a3-162">Range operator ..</span></span>

<span data-ttu-id="e30a3-163">Disponível em C# 8,0 e posterior, o operador`..`especifica o início e o fim de um intervalo de índices como operandos.</span><span class="sxs-lookup"><span data-stu-id="e30a3-163">Available in C# 8.0 and later, the `..` operator specifies the start and end of a range of indices as its operands.</span></span> <span data-ttu-id="e30a3-164">O operando à esquerda é um início *inclusivo* de um intervalo.</span><span class="sxs-lookup"><span data-stu-id="e30a3-164">The left-hand operand is an *inclusive* start of a range.</span></span> <span data-ttu-id="e30a3-165">O operando de lado direito é uma extremidade *exclusiva* de um intervalo.</span><span class="sxs-lookup"><span data-stu-id="e30a3-165">The right-hand operand is an *exclusive* end of a range.</span></span> <span data-ttu-id="e30a3-166">Qualquer um dos operandos pode ser um índice do início ou do final de uma sequência, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="e30a3-166">Either of operands can be an index from the start or from the end of a sequence, as the following example shows:</span></span>

[!code-csharp[range examples](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Ranges)]

<span data-ttu-id="e30a3-167">Como mostra o exemplo anterior, Expression `a..b` é do tipo <xref:System.Range?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e30a3-167">As the preceding example shows, expression `a..b` is of the <xref:System.Range?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="e30a3-168">No Expression `a..b`, os resultados de `a` e `b` devem ser conversíveis implicitamente para `int` ou <xref:System.Index>.</span><span class="sxs-lookup"><span data-stu-id="e30a3-168">In expression `a..b`, the results of `a` and `b` must be implicitly convertible to `int` or <xref:System.Index>.</span></span>

<span data-ttu-id="e30a3-169">Você pode omitir qualquer um dos operandos do operador `..` para obter um intervalo aberto:</span><span class="sxs-lookup"><span data-stu-id="e30a3-169">You can omit any of the operands of the `..` operator to obtain an open-ended range:</span></span>

- <span data-ttu-id="e30a3-170">`a..` equivale a `a..^0`</span><span class="sxs-lookup"><span data-stu-id="e30a3-170">`a..` is equivalent to `a..^0`</span></span>
- <span data-ttu-id="e30a3-171">`..b` equivale a `0..b`</span><span class="sxs-lookup"><span data-stu-id="e30a3-171">`..b` is equivalent to `0..b`</span></span>
- <span data-ttu-id="e30a3-172">`..` equivale a `0..^0`</span><span class="sxs-lookup"><span data-stu-id="e30a3-172">`..` is equivalent to `0..^0`</span></span>

[!code-csharp[ranges with omitted operands](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#RangesOptional)]

<span data-ttu-id="e30a3-173">Para obter mais informações, consulte [índices e intervalos](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="e30a3-173">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="e30a3-174">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="e30a3-174">Operator overloadability</span></span>

<span data-ttu-id="e30a3-175">Os operadores `.`, `()`, `^`e `..` não podem ser sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="e30a3-175">The `.`, `()`, `^`, and `..` operators cannot be overloaded.</span></span> <span data-ttu-id="e30a3-176">O operador `[]` também é considerado um operador não sobrecarregável.</span><span class="sxs-lookup"><span data-stu-id="e30a3-176">The `[]` operator is also considered a non-overloadable operator.</span></span> <span data-ttu-id="e30a3-177">Use [indexadores](../../programming-guide/indexers/index.md) para permitir a indexação com tipos definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="e30a3-177">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e30a3-178">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="e30a3-178">C# language specification</span></span>

<span data-ttu-id="e30a3-179">Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="e30a3-179">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="e30a3-180">Acesso de membros</span><span class="sxs-lookup"><span data-stu-id="e30a3-180">Member access</span></span>](~/_csharplang/spec/expressions.md#member-access)
- [<span data-ttu-id="e30a3-181">Acesso a elemento</span><span class="sxs-lookup"><span data-stu-id="e30a3-181">Element access</span></span>](~/_csharplang/spec/expressions.md#element-access)
- [<span data-ttu-id="e30a3-182">Operador condicional nulo</span><span class="sxs-lookup"><span data-stu-id="e30a3-182">Null-conditional operator</span></span>](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [<span data-ttu-id="e30a3-183">Expressões de invocação</span><span class="sxs-lookup"><span data-stu-id="e30a3-183">Invocation expressions</span></span>](~/_csharplang/spec/expressions.md#invocation-expressions)

<span data-ttu-id="e30a3-184">Para obter mais informações sobre índices e intervalos, consulte a [Nota de proposta de recurso](~/_csharplang/proposals/csharp-8.0/ranges.md).</span><span class="sxs-lookup"><span data-stu-id="e30a3-184">For more information about indices and ranges, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e30a3-185">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e30a3-185">See also</span></span>

- [<span data-ttu-id="e30a3-186">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="e30a3-186">C# reference</span></span>](../index.md)
- [<span data-ttu-id="e30a3-187">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="e30a3-187">C# operators</span></span>](index.md)
- [<span data-ttu-id="e30a3-188">?? (operador de união nula)</span><span class="sxs-lookup"><span data-stu-id="e30a3-188">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="e30a3-189">Operador ::</span><span class="sxs-lookup"><span data-stu-id="e30a3-189">:: operator</span></span>](namespace-alias-qualifier.md)
