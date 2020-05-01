---
title: Operadores de acesso de membro e expressões-referência C#
description: Aprenda sobre operadores de C# que você pode usar para acessar membros de tipo.
ms.date: 04/17/2020
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
ms.openlocfilehash: 37a6cb7cd32a9d60607aec51b1994e4717c5349a
ms.sourcegitcommit: e09dbff13f0b21b569a101f3b3c5efa174aec204
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82624859"
---
# <a name="member-access-operators-and-expressions-c-reference"></a><span data-ttu-id="4b31d-103">Operadores de acesso de membro e expressões (referência C#)</span><span class="sxs-lookup"><span data-stu-id="4b31d-103">Member access operators and expressions (C# reference)</span></span>

<span data-ttu-id="4b31d-104">Você pode usar os seguintes operadores e expressões ao acessar um membro de tipo:</span><span class="sxs-lookup"><span data-stu-id="4b31d-104">You can use the following operators and expressions when you access a type member:</span></span>

- <span data-ttu-id="4b31d-105">[(acesso de membro): para acessar um membro de um namespace ou de um tipo `.` ](#member-access-expression-)</span><span class="sxs-lookup"><span data-stu-id="4b31d-105">[`.` (member access)](#member-access-expression-): to access a member of a namespace or a type</span></span>
- <span data-ttu-id="4b31d-106">[(elemento de matriz ou acesso de indexador): para acessar um elemento de matriz ou um indexador de tipo `[]` ](#indexer-operator-)</span><span class="sxs-lookup"><span data-stu-id="4b31d-106">[`[]` (array element or indexer access)](#indexer-operator-): to access an array element or a type indexer</span></span>
- <span data-ttu-id="4b31d-107">[and `?[]` operadores condicionais nulos): para executar uma operação de acesso de elemento ou membro somente se um operando não `?.` ](#null-conditional-operators--and-)for nulo</span><span class="sxs-lookup"><span data-stu-id="4b31d-107">[`?.` and `?[]` (null-conditional operators)](#null-conditional-operators--and-): to perform a member or element access operation only if an operand is non-null</span></span>
- <span data-ttu-id="4b31d-108">(invocação): para chamar um método acessado ou invocar um delegado [ `()` ](#invocation-expression-)</span><span class="sxs-lookup"><span data-stu-id="4b31d-108">[`()` (invocation)](#invocation-expression-): to call an accessed method or invoke a delegate</span></span>
- <span data-ttu-id="4b31d-109">[(índice de fim): para indicar que a posição do elemento é do final de uma sequência `^` ](#index-from-end-operator-)</span><span class="sxs-lookup"><span data-stu-id="4b31d-109">[`^` (index from end)](#index-from-end-operator-): to indicate that the element position is from the end of a sequence</span></span>
- <span data-ttu-id="4b31d-110">(Range): para especificar um intervalo de índices que você pode usar para obter um intervalo de elementos de sequência [ `..` ](#range-operator-)</span><span class="sxs-lookup"><span data-stu-id="4b31d-110">[`..` (range)](#range-operator-): to specify a range of indices that you can use to obtain a range of sequence elements</span></span>

## <a name="member-access-expression-"></a><span data-ttu-id="4b31d-111">Expressão de acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="4b31d-111">Member access expression .</span></span>

<span data-ttu-id="4b31d-112">Use o token `.` para acessar um membro de um namespace ou um tipo, como demonstram os exemplos a seguir:</span><span class="sxs-lookup"><span data-stu-id="4b31d-112">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="4b31d-113">Use `.` para acessar um namespace aninhado em um namespace, como mostra o exemplo a seguir de uma [ `using` diretiva](../keywords/using-directive.md) :</span><span class="sxs-lookup"><span data-stu-id="4b31d-113">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](snippets/MemberAccessOperators.cs#NestedNamespace)]

- <span data-ttu-id="4b31d-114">Use `.` para formar um *nome qualificado* para acessar um tipo dentro de um namespace, como mostra o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="4b31d-114">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](snippets/MemberAccessOperators.cs#QualifiedName)]

  <span data-ttu-id="4b31d-115">Use uma [ `using` diretiva](../keywords/using-directive.md) para tornar o uso de nomes qualificados opcional.</span><span class="sxs-lookup"><span data-stu-id="4b31d-115">Use a [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="4b31d-116">Use `.` para acessar [membros de tipo](../../programming-guide/classes-and-structs/index.md#members), estático e não-estático, como mostra o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="4b31d-116">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](snippets/MemberAccessOperators.cs#TypeMemberAccess)]

<span data-ttu-id="4b31d-117">Você também pode usar `.` para acessar um [método de extensão](../../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="4b31d-117">You can also use `.` to access an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="indexer-operator-"></a><span data-ttu-id="4b31d-118">Operador de indexador []</span><span class="sxs-lookup"><span data-stu-id="4b31d-118">Indexer operator []</span></span>

<span data-ttu-id="4b31d-119">Os colchetes, `[]`, normalmente são usados para acesso de elemento de matriz, indexador ou ponteiro.</span><span class="sxs-lookup"><span data-stu-id="4b31d-119">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

### <a name="array-access"></a><span data-ttu-id="4b31d-120">Acesso de matriz</span><span class="sxs-lookup"><span data-stu-id="4b31d-120">Array access</span></span>

<span data-ttu-id="4b31d-121">O exemplo a seguir demonstra como acessar elementos de matriz:</span><span class="sxs-lookup"><span data-stu-id="4b31d-121">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](snippets/MemberAccessOperators.cs#Arrays)]

<span data-ttu-id="4b31d-122">Se um índice de matriz estiver fora dos limites da dimensão correspondente de uma matriz, uma <xref:System.IndexOutOfRangeException> será gerada.</span><span class="sxs-lookup"><span data-stu-id="4b31d-122">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="4b31d-123">Como mostra o exemplo anterior, você também usar colchetes quando declara um tipo de matriz ou instancia uma instância de matriz.</span><span class="sxs-lookup"><span data-stu-id="4b31d-123">As the preceding example shows, you also use square brackets when you declare an array type or instantiate an array instance.</span></span>

<span data-ttu-id="4b31d-124">Para obter mais informações sobre matrizes, confira [Matrizes](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="4b31d-124">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

### <a name="indexer-access"></a><span data-ttu-id="4b31d-125">Acesso de indexador</span><span class="sxs-lookup"><span data-stu-id="4b31d-125">Indexer access</span></span>

<span data-ttu-id="4b31d-126">O exemplo a seguir usa o <xref:System.Collections.Generic.Dictionary%602> tipo .net para demonstrar o acesso ao indexador:</span><span class="sxs-lookup"><span data-stu-id="4b31d-126">The following example uses the .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](snippets/MemberAccessOperators.cs#Indexers)]

<span data-ttu-id="4b31d-127">Os indexadores permitem indexar instâncias de um tipo definido pelo usuário de maneira semelhante à indexação de matriz.</span><span class="sxs-lookup"><span data-stu-id="4b31d-127">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="4b31d-128">Ao contrário dos índices de matriz, que devem ser inteiros, os parâmetros do indexador podem ser declarados como sendo de qualquer tipo.</span><span class="sxs-lookup"><span data-stu-id="4b31d-128">Unlike array indices, which must be integer, the indexer parameters can be declared to be of any type.</span></span>

<span data-ttu-id="4b31d-129">Para obter mais informações sobre indexadores, confira [Indexadores](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="4b31d-129">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="4b31d-130">Outros usos de []</span><span class="sxs-lookup"><span data-stu-id="4b31d-130">Other usages of []</span></span>

<span data-ttu-id="4b31d-131">Para saber mais sobre o acesso a elemento de ponteiro, confira a seção [Operador de acesso a elemento de ponteiro []](pointer-related-operators.md#pointer-element-access-operator-) do artigo [Operadores relacionados a ponteiro](pointer-related-operators.md).</span><span class="sxs-lookup"><span data-stu-id="4b31d-131">For information about pointer element access, see the [Pointer element access operator []](pointer-related-operators.md#pointer-element-access-operator-) section of the [Pointer related operators](pointer-related-operators.md) article.</span></span>

<span data-ttu-id="4b31d-132">Os colchetes também são usados para especificar [atributos](../../programming-guide/concepts/attributes/index.md):</span><span class="sxs-lookup"><span data-stu-id="4b31d-132">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a><span data-ttu-id="4b31d-133">Operadores condicionais nulos ?.</span><span class="sxs-lookup"><span data-stu-id="4b31d-133">Null-conditional operators ?.</span></span> <span data-ttu-id="4b31d-134">e ?[]</span><span class="sxs-lookup"><span data-stu-id="4b31d-134">and ?[]</span></span>

<span data-ttu-id="4b31d-135">Disponível no C# 6 e posterior, um operador NULL-Conditional aplica um [acesso](#member-access-expression-)de membro `?.`, ou [acesso](#indexer-operator-)de elemento `?[]`,, operação para seu operando somente se esse operando for avaliado como não nulo; caso contrário, retornará `null`.</span><span class="sxs-lookup"><span data-stu-id="4b31d-135">Available in C# 6 and later, a null-conditional operator applies a [member access](#member-access-expression-), `?.`, or [element access](#indexer-operator-), `?[]`, operation to its operand only if that operand evaluates to non-null; otherwise, it returns `null`.</span></span> <span data-ttu-id="4b31d-136">Isto é</span><span class="sxs-lookup"><span data-stu-id="4b31d-136">That is,</span></span>

- <span data-ttu-id="4b31d-137">Se `a` for avaliada `null`como, o resultado `a?.x` de `a?[x]` ou `null`é.</span><span class="sxs-lookup"><span data-stu-id="4b31d-137">If `a` evaluates to `null`, the result of `a?.x` or `a?[x]` is `null`.</span></span>
- <span data-ttu-id="4b31d-138">Se `a` for avaliada como não nula, o `a?.x` resultado ou `a?[x]` será o mesmo que o resultado de `a.x` ou `a[x]`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="4b31d-138">If `a` evaluates to non-null, the result of `a?.x` or `a?[x]` is the same as the result of `a.x` or `a[x]`, respectively.</span></span>

  > [!NOTE]
  > <span data-ttu-id="4b31d-139">Se `a.x` ou `a[x]` lançar uma exceção, `a?.x` ou `a?[x]` geraria a mesma exceção para não NULL `a`.</span><span class="sxs-lookup"><span data-stu-id="4b31d-139">If `a.x` or `a[x]` throws an exception, `a?.x` or `a?[x]` would throw the same exception for non-null `a`.</span></span> <span data-ttu-id="4b31d-140">Por exemplo, se `a` for uma instância de matriz não nula e `x` estiver fora dos limites de `a`, `a?[x]` o geraria um <xref:System.IndexOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="4b31d-140">For example, if `a` is a non-null array instance and `x` is outside the bounds of `a`, `a?[x]` would throw an <xref:System.IndexOutOfRangeException>.</span></span>

<span data-ttu-id="4b31d-141">Os operadores condicionais nulos estão entrando em curto-circuito.</span><span class="sxs-lookup"><span data-stu-id="4b31d-141">The null-conditional operators are short-circuiting.</span></span> <span data-ttu-id="4b31d-142">Ou seja, se uma operação em uma cadeia de membro operações condicionais de acesso a membro ou elemento retornar `null`, o restante da cadeia não será executado.</span><span class="sxs-lookup"><span data-stu-id="4b31d-142">That is, if one operation in a chain of conditional member or element access operations returns `null`, the rest of the chain doesn't execute.</span></span> <span data-ttu-id="4b31d-143">No exemplo a seguir, `B` não será avaliado se `A` for avaliado como `null` e `C` não será avaliado se `A` ou `B` for avaliado como `null`:</span><span class="sxs-lookup"><span data-stu-id="4b31d-143">In the following example, `B` is not evaluated if `A` evaluates to `null` and `C` is not evaluated if `A` or `B` evaluates to `null`:</span></span>

```csharp
A?.B?.Do(C);
A?.B?[C];
```

<span data-ttu-id="4b31d-144">O exemplo a seguir demonstra o uso dos operadores `?.` e `?[]`:</span><span class="sxs-lookup"><span data-stu-id="4b31d-144">The following example demonstrates the usage of the `?.` and `?[]` operators:</span></span>

[!code-csharp-interactive[null-conditional operators](snippets/MemberAccessOperators.cs#NullConditional)]

<span data-ttu-id="4b31d-145">O exemplo anterior também usa o [ `??` operador de União nulo](null-coalescing-operator.md) para especificar uma expressão alternativa a ser avaliada, caso o resultado de uma operação condicional nula seja `null`.</span><span class="sxs-lookup"><span data-stu-id="4b31d-145">The preceding example also uses the [null-coalescing operator `??`](null-coalescing-operator.md) to specify an alternative expression to evaluate in case the result of a null-conditional operation is `null`.</span></span>

<span data-ttu-id="4b31d-146">Se `a.x` ou `a[x]` for de um tipo `T` `a?.x` de valor não anulável ou `a?[x]` for do tipo `T?`de [valor anulável](../builtin-types/nullable-value-types.md) correspondente.</span><span class="sxs-lookup"><span data-stu-id="4b31d-146">If `a.x` or `a[x]` is of a non-nullable value type `T`, `a?.x` or `a?[x]` is of the corresponding [nullable value type](../builtin-types/nullable-value-types.md) `T?`.</span></span> <span data-ttu-id="4b31d-147">Se você precisar de uma expressão do `T`tipo, aplique o operador `??` de União nula a uma expressão condicional nula, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="4b31d-147">If you need an expression of type `T`, apply the null-coalescing operator `??` to a null-conditional expression, as the following example shows:</span></span>

[!code-csharp-interactive[null-conditional with null-coalescing](snippets/MemberAccessOperators.cs#NullConditionalWithNullCoalescing)]

<span data-ttu-id="4b31d-148">No exemplo anterior, se você não usar o operador `??` , `numbers?.Length < 2` o será avaliado como `false` quando `numbers` é `null`.</span><span class="sxs-lookup"><span data-stu-id="4b31d-148">In the preceding example, if you don't use the `??` operator, `numbers?.Length < 2` evaluates to `false` when `numbers` is `null`.</span></span>

<span data-ttu-id="4b31d-149">O operador de acesso do membro condicional nulo `?.` também é conhecido como o operador Elvis.</span><span class="sxs-lookup"><span data-stu-id="4b31d-149">The null-conditional member access operator `?.` is also known as the Elvis operator.</span></span>

> [!NOTE]
> <span data-ttu-id="4b31d-150">No C# 8, o [operador NULL-tolerante](null-forgiving.md) encerra a lista de operações condicionais nulas anteriores.</span><span class="sxs-lookup"><span data-stu-id="4b31d-150">In C# 8, the [null-forgiving operator](null-forgiving.md) terminates the list of preceding null-conditional operations.</span></span> <span data-ttu-id="4b31d-151">Por exemplo, a expressão `x?.y!.z` é analisada como `(x?.y)!.z`.</span><span class="sxs-lookup"><span data-stu-id="4b31d-151">For example, the expression `x?.y!.z` is parsed as `(x?.y)!.z`.</span></span> <span data-ttu-id="4b31d-152">Devido a essa interpretação, `z` é avaliada mesmo `x` se `null`for, o que pode resultar <xref:System.NullReferenceException>em um.</span><span class="sxs-lookup"><span data-stu-id="4b31d-152">Due to this interpretation, `z` is evaluated even if `x` is `null`, which may result in a <xref:System.NullReferenceException>.</span></span>

### <a name="thread-safe-delegate-invocation"></a><span data-ttu-id="4b31d-153">Invocação de delegado thread-safe</span><span class="sxs-lookup"><span data-stu-id="4b31d-153">Thread-safe delegate invocation</span></span>

<span data-ttu-id="4b31d-154">Use o operador `?.` para verificar se um delegado é não nulo e chame-o de uma forma thread-safe (por exemplo, quando você [aciona um evento](../../../standard/events/how-to-raise-and-consume-events.md)), conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="4b31d-154">Use the `?.` operator to check if a delegate is non-null and invoke it in a thread-safe way (for example, when you [raise an event](../../../standard/events/how-to-raise-and-consume-events.md)), as the following code shows:</span></span>

```csharp
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="4b31d-155">Esse código é equivalente ao código a seguir que você usaria no C# 5 ou anterior:</span><span class="sxs-lookup"><span data-stu-id="4b31d-155">That code is equivalent to the following code that you would use in C# 5 or earlier:</span></span>

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

<span data-ttu-id="4b31d-156">Essa é uma forma thread-safe de garantir que apenas um não nulo `handler` seja invocado.</span><span class="sxs-lookup"><span data-stu-id="4b31d-156">That is a thread-safe way to ensure that only a non-null `handler` is invoked.</span></span> <span data-ttu-id="4b31d-157">Como as `handler` instâncias de delegado são imutáveis, nenhum thread pode alterar o valor referenciado pela variável local.</span><span class="sxs-lookup"><span data-stu-id="4b31d-157">Because delegate instances are immutable, no thread can change the value referenced by the `handler` local variable.</span></span> <span data-ttu-id="4b31d-158">Em particular, se o código executado por outro `PropertyChanged` thread cancelar a assinatura do evento e `PropertyChanged` se tornar `null` antes `handler` de ser invocado, o valor `handler` referenciado por permanecerá inalterado.</span><span class="sxs-lookup"><span data-stu-id="4b31d-158">In particular, if the code executed by another thread unsubscribes from the `PropertyChanged` event and `PropertyChanged` becomes `null` before `handler` is invoked, the value referenced by `handler` remains unaffected.</span></span> <span data-ttu-id="4b31d-159">O `?.` operador avalia seu operando à esquerda não mais de uma vez, garantindo que ele não possa ser alterado para `null` depois de ser verificado como não nulo.</span><span class="sxs-lookup"><span data-stu-id="4b31d-159">The `?.` operator evaluates its left-hand operand no more than once, guaranteeing that it cannot be changed to `null` after being verified as non-null.</span></span>

## <a name="invocation-expression-"></a><span data-ttu-id="4b31d-160">Expressão de invocação ()</span><span class="sxs-lookup"><span data-stu-id="4b31d-160">Invocation expression ()</span></span>

<span data-ttu-id="4b31d-161">Use parênteses, `()`, para chamar um [método](../../programming-guide/classes-and-structs/methods.md) ou invocar um [delegado](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="4b31d-161">Use parentheses, `()`, to call a [method](../../programming-guide/classes-and-structs/methods.md) or invoke a [delegate](../../programming-guide/delegates/index.md).</span></span>

<span data-ttu-id="4b31d-162">O exemplo a seguir demonstra como chamar um método (com ou sem argumentos) e invocar um delegado:</span><span class="sxs-lookup"><span data-stu-id="4b31d-162">The following example demonstrates how to call a method, with or without arguments, and invoke a delegate:</span></span>

[!code-csharp-interactive[invocation with ()](snippets/MemberAccessOperators.cs#Invocation)]

<span data-ttu-id="4b31d-163">Você também pode usar parênteses ao invocar um [construtor](../../programming-guide/classes-and-structs/constructors.md) com o operador [`new`](new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="4b31d-163">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with the [`new`](new-operator.md) operator.</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="4b31d-164">Outros usos de ()</span><span class="sxs-lookup"><span data-stu-id="4b31d-164">Other usages of ()</span></span>

<span data-ttu-id="4b31d-165">Você também pode usar parênteses para ajustar a ordem na qual as operações em uma expressão são avaliadas.</span><span class="sxs-lookup"><span data-stu-id="4b31d-165">You also use parentheses to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="4b31d-166">Para saber mais, confira [Operadores C#](index.md).</span><span class="sxs-lookup"><span data-stu-id="4b31d-166">For more information, see [C# operators](index.md).</span></span>

<span data-ttu-id="4b31d-167">[Expressões de conversão](type-testing-and-cast.md#cast-expression), que executam conversões de tipo explícitas, também usam parênteses.</span><span class="sxs-lookup"><span data-stu-id="4b31d-167">[Cast expressions](type-testing-and-cast.md#cast-expression), which perform explicit type conversions, also use parentheses.</span></span>

## <a name="index-from-end-operator-"></a><span data-ttu-id="4b31d-168">Índice do operador end ^</span><span class="sxs-lookup"><span data-stu-id="4b31d-168">Index from end operator ^</span></span>

<span data-ttu-id="4b31d-169">Disponível em C# 8,0 e posterior, o `^` operador indica a posição do elemento do final de uma sequência.</span><span class="sxs-lookup"><span data-stu-id="4b31d-169">Available in C# 8.0 and later, the `^` operator indicates the element position from the end of a sequence.</span></span> <span data-ttu-id="4b31d-170">Para uma sequência de comprimento `length`, `^n` aponta para o elemento com offset `length - n` do início de uma sequência.</span><span class="sxs-lookup"><span data-stu-id="4b31d-170">For a sequence of length `length`, `^n` points to the element with offset `length - n` from the start of a sequence.</span></span> <span data-ttu-id="4b31d-171">Por exemplo, `^1` aponta para o último elemento de uma sequência e `^length` aponta para o primeiro elemento de uma sequência.</span><span class="sxs-lookup"><span data-stu-id="4b31d-171">For example, `^1` points to the last element of a sequence and `^length` points to the first element of a sequence.</span></span>

[!code-csharp[index from end](snippets/MemberAccessOperators.cs#IndexFromEnd)]

<span data-ttu-id="4b31d-172">Como mostra o exemplo anterior, Expression `^e` é do <xref:System.Index?displayProperty=nameWithType> tipo.</span><span class="sxs-lookup"><span data-stu-id="4b31d-172">As the preceding example shows, expression `^e` is of the <xref:System.Index?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="4b31d-173">Na expressão `^e`, o resultado de `e` deve ser implicitamente conversível `int`para.</span><span class="sxs-lookup"><span data-stu-id="4b31d-173">In expression `^e`, the result of `e` must be implicitly convertible to `int`.</span></span>

<span data-ttu-id="4b31d-174">Você também pode usar o `^` operador com o [operador Range](#range-operator-) para criar um intervalo de índices.</span><span class="sxs-lookup"><span data-stu-id="4b31d-174">You can also use the `^` operator with the [range operator](#range-operator-) to create a range of indices.</span></span> <span data-ttu-id="4b31d-175">Para obter mais informações, consulte [índices e intervalos](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="4b31d-175">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="range-operator-"></a><span data-ttu-id="4b31d-176">Operador de intervalo..</span><span class="sxs-lookup"><span data-stu-id="4b31d-176">Range operator ..</span></span>

<span data-ttu-id="4b31d-177">Disponível em C# 8,0 e posterior, o `..` operador especifica o início e o término de um intervalo de índices como operandos.</span><span class="sxs-lookup"><span data-stu-id="4b31d-177">Available in C# 8.0 and later, the `..` operator specifies the start and end of a range of indices as its operands.</span></span> <span data-ttu-id="4b31d-178">O operando à esquerda é um início *inclusivo* de um intervalo.</span><span class="sxs-lookup"><span data-stu-id="4b31d-178">The left-hand operand is an *inclusive* start of a range.</span></span> <span data-ttu-id="4b31d-179">O operando de lado direito é uma extremidade *exclusiva* de um intervalo.</span><span class="sxs-lookup"><span data-stu-id="4b31d-179">The right-hand operand is an *exclusive* end of a range.</span></span> <span data-ttu-id="4b31d-180">Qualquer um dos operandos pode ser um índice do início ou do final de uma sequência, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="4b31d-180">Either of operands can be an index from the start or from the end of a sequence, as the following example shows:</span></span>

[!code-csharp[range examples](snippets/MemberAccessOperators.cs#Ranges)]

<span data-ttu-id="4b31d-181">Como mostra o exemplo anterior, Expression `a..b` é do <xref:System.Range?displayProperty=nameWithType> tipo.</span><span class="sxs-lookup"><span data-stu-id="4b31d-181">As the preceding example shows, expression `a..b` is of the <xref:System.Range?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="4b31d-182">Na expressão `a..b`, os resultados de `a` e `b` devem ser conversíveis implicitamente `int` para <xref:System.Index>ou.</span><span class="sxs-lookup"><span data-stu-id="4b31d-182">In expression `a..b`, the results of `a` and `b` must be implicitly convertible to `int` or <xref:System.Index>.</span></span>

<span data-ttu-id="4b31d-183">Você pode omitir qualquer um dos operandos do `..` operador para obter um intervalo aberto:</span><span class="sxs-lookup"><span data-stu-id="4b31d-183">You can omit any of the operands of the `..` operator to obtain an open-ended range:</span></span>

- <span data-ttu-id="4b31d-184">`a..` equivale a `a..^0`</span><span class="sxs-lookup"><span data-stu-id="4b31d-184">`a..` is equivalent to `a..^0`</span></span>
- <span data-ttu-id="4b31d-185">`..b` equivale a `0..b`</span><span class="sxs-lookup"><span data-stu-id="4b31d-185">`..b` is equivalent to `0..b`</span></span>
- <span data-ttu-id="4b31d-186">`..` equivale a `0..^0`</span><span class="sxs-lookup"><span data-stu-id="4b31d-186">`..` is equivalent to `0..^0`</span></span>

[!code-csharp[ranges with omitted operands](snippets/MemberAccessOperators.cs#RangesOptional)]

<span data-ttu-id="4b31d-187">Para obter mais informações, consulte [índices e intervalos](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="4b31d-187">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="4b31d-188">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="4b31d-188">Operator overloadability</span></span>

<span data-ttu-id="4b31d-189">Os `.`operadores `()`, `^`, e `..` não podem ser sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="4b31d-189">The `.`, `()`, `^`, and `..` operators cannot be overloaded.</span></span> <span data-ttu-id="4b31d-190">O operador `[]` também é considerado um operador não sobrecarregável.</span><span class="sxs-lookup"><span data-stu-id="4b31d-190">The `[]` operator is also considered a non-overloadable operator.</span></span> <span data-ttu-id="4b31d-191">Use [indexadores](../../programming-guide/indexers/index.md) para permitir a indexação com tipos definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="4b31d-191">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4b31d-192">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="4b31d-192">C# language specification</span></span>

<span data-ttu-id="4b31d-193">Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="4b31d-193">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="4b31d-194">Acesso de membro</span><span class="sxs-lookup"><span data-stu-id="4b31d-194">Member access</span></span>](~/_csharplang/spec/expressions.md#member-access)
- [<span data-ttu-id="4b31d-195">Acesso a elemento</span><span class="sxs-lookup"><span data-stu-id="4b31d-195">Element access</span></span>](~/_csharplang/spec/expressions.md#element-access)
- [<span data-ttu-id="4b31d-196">Operador condicional nulo</span><span class="sxs-lookup"><span data-stu-id="4b31d-196">Null-conditional operator</span></span>](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [<span data-ttu-id="4b31d-197">Expressões de invocação</span><span class="sxs-lookup"><span data-stu-id="4b31d-197">Invocation expressions</span></span>](~/_csharplang/spec/expressions.md#invocation-expressions)

<span data-ttu-id="4b31d-198">Para obter mais informações sobre índices e intervalos, consulte a [Nota de proposta de recurso](~/_csharplang/proposals/csharp-8.0/ranges.md).</span><span class="sxs-lookup"><span data-stu-id="4b31d-198">For more information about indices and ranges, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4b31d-199">Confira também</span><span class="sxs-lookup"><span data-stu-id="4b31d-199">See also</span></span>

- [<span data-ttu-id="4b31d-200">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="4b31d-200">C# reference</span></span>](../index.md)
- [<span data-ttu-id="4b31d-201">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="4b31d-201">C# operators</span></span>](index.md)
- [<span data-ttu-id="4b31d-202">?? (operador de união nula)</span><span class="sxs-lookup"><span data-stu-id="4b31d-202">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="4b31d-203">operador::</span><span class="sxs-lookup"><span data-stu-id="4b31d-203">:: operator</span></span>](namespace-alias-qualifier.md)
