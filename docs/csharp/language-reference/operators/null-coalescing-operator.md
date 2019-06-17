---
title: ?? Operador – referência do C#
ms.custom: seodec18
ms.date: 06/07/2019
f1_keywords:
- ??_CSharpKeyword
helpviewer_keywords:
- null-coalescing operator [C#]
- ?? operator [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: 8ca97261b348b7813ab179abbc1f2c5f535966a1
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816015"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="84311-103">??</span><span class="sxs-lookup"><span data-stu-id="84311-103">??</span></span> <span data-ttu-id="84311-104">operator (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="84311-104">operator (C# Reference)</span></span>

<span data-ttu-id="84311-105">O operador de coalescência nula `??` retornará o valor do operando esquerdo se não for `null`; caso contrário, ele avaliará o operando direito e retornará seu resultado.</span><span class="sxs-lookup"><span data-stu-id="84311-105">The null-coalescing operator `??` returns the value of its left-hand operand if it isn't `null`; otherwise, it evaluates the right-hand operand and returns its result.</span></span> <span data-ttu-id="84311-106">O operador `??` não avaliará seu operando direito se o operando esquerdo for avaliado como não nulo.</span><span class="sxs-lookup"><span data-stu-id="84311-106">The `??` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

<span data-ttu-id="84311-107">O operador de coalescência nula é associativo direito, ou seja, uma expressão do formulário</span><span class="sxs-lookup"><span data-stu-id="84311-107">The null-coalescing operator is right-associative, that is, an expression of the form</span></span>

```csharp
a ?? b ?? c
```

<span data-ttu-id="84311-108">é avaliada como</span><span class="sxs-lookup"><span data-stu-id="84311-108">is evaluated as</span></span>

```csharp
a ?? (b ?? c)
```

<span data-ttu-id="84311-109">O operador `??` pode ser útil nos seguintes cenários:</span><span class="sxs-lookup"><span data-stu-id="84311-109">The `??` operator can be useful in the following scenarios:</span></span>

- <span data-ttu-id="84311-110">Em expressões com os [operadores condicionais nulos ?. e ?[]](member-access-operators.md#null-conditional-operators--and-), você pode usar o operador de coalescência nula para fornecer uma expressão alternativa a ser avaliada caso o resultado da expressão com operação condicional nula seja `null`:</span><span class="sxs-lookup"><span data-stu-id="84311-110">In expressions with the [null-conditional operators ?. and ?[]](member-access-operators.md#null-conditional-operators--and-), you can use the null-coalescing operator to provide an alternative expression to evaluate in case the result of the expression with null-conditional operations is `null`:</span></span>

  [!code-csharp-interactive[with null-conditional](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullConditional)]

- <span data-ttu-id="84311-111">Quando você trabalhar com [tipos que permitem valor nulo](../../programming-guide/nullable-types/index.md) e precisar fornecer o valor de um tipo subjacente, use o operador de coalescência nula para especificar o valor a ser fornecido caso o tipo que permite valor nulo seja `null`:</span><span class="sxs-lookup"><span data-stu-id="84311-111">When you work with [nullable value types](../../programming-guide/nullable-types/index.md) and need to provide a value of an underlying value type, use the null-coalescing operator to specify the value to provide in case a nullable type value is `null`:</span></span>

  [!code-csharp-interactive[with nullable types](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullableTypes)]

  <span data-ttu-id="84311-112">Use o método <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> se o valor a ser usado quando um valor de tipo que permite valor nulo for `null` tiver que ser o valor padrão do tipo de valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="84311-112">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a nullable type value is `null` should be the default value of the underlying value type.</span></span>

- <span data-ttu-id="84311-113">A partir do C# 7.0, você pode usar uma expressão [`throw` ](../keywords/throw.md#the-throw-expression) como o operando direito do operador de coalescência nula para tornar o código de verificação de argumento mais conciso:</span><span class="sxs-lookup"><span data-stu-id="84311-113">Starting with C# 7.0, you can use a [`throw` expression](../keywords/throw.md#the-throw-expression) as the right-hand operand of the null-coalescing operator to make the argument-checking code more concise:</span></span>

  [!code-csharp[with throw expression](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithThrowExpression)]

  <span data-ttu-id="84311-114">O exemplo anterior também demonstra como usar [membros aptos para expressão](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) para definir uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="84311-114">The preceding example also demonstrates how to use [expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) to define a property.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="84311-115">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="84311-115">Operator overloadability</span></span>

<span data-ttu-id="84311-116">O operador de coalescência nula não pode ser sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="84311-116">The null-coalescing operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="84311-117">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="84311-117">C# language specification</span></span>

<span data-ttu-id="84311-118">Para saber mais, confira a seção [O operador coalescente nulo](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="84311-118">For more information, see [The null coalescing operator](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="84311-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="84311-119">See also</span></span>

- [<span data-ttu-id="84311-120">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="84311-120">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="84311-121">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="84311-121">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="84311-122">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="84311-122">C# operators</span></span>](index.md)
- <span data-ttu-id="84311-123">[Operadores ?. e ?[]](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="84311-123">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="84311-124">Operador ?:</span><span class="sxs-lookup"><span data-stu-id="84311-124">?: operator</span></span>](conditional-operator.md)
