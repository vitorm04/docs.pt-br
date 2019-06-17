---
title: '?: Operador – Referência de C#'
ms.custom: seodec18
ms.date: 11/20/2018
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: ae3039df2c1260211f4c7ec3e813db1d0c6cd42b
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/10/2019
ms.locfileid: "66815929"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="62b3e-102">?: Operador (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="62b3e-102">?: Operator (C# Reference)</span></span>

<span data-ttu-id="62b3e-103">O operador condicional `?:`, comumente conhecido como o operador condicional ternário, avalia uma expressão booliana e retorna o resultado da avaliação de uma de duas expressões, dependendo se a expressão booliana é avaliada como `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="62b3e-103">The conditional operator `?:`, commonly known as the ternary conditional operator, evaluates a Boolean expression, and returns the result of evaluating one of two expressions, depending on whether the Boolean expression evaluates to `true` or `false`.</span></span> <span data-ttu-id="62b3e-104">Começando com C# 7.2, a [expressão de referência condicional](#conditional-ref-expression) retorna a referência ao resultado de uma de duas expressões.</span><span class="sxs-lookup"><span data-stu-id="62b3e-104">Beginning with C# 7.2, the [conditional ref expression](#conditional-ref-expression) returns the reference to the result of one of the two expressions.</span></span>

<span data-ttu-id="62b3e-105">A sintaxe do operador condicional é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="62b3e-105">The syntax for the conditional operator is as follows:</span></span>

```csharp
condition ? consequent : alternative
```

<span data-ttu-id="62b3e-106">A expressão `condition` deve ser avaliada para `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="62b3e-106">The `condition` expression must evaluate to `true` or `false`.</span></span> <span data-ttu-id="62b3e-107">Se `condition` for avaliada como `true`, a expressão `consequent` será avaliada e seu resultado se tornará o resultado da operação.</span><span class="sxs-lookup"><span data-stu-id="62b3e-107">If `condition` evaluates to `true`, the `consequent` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="62b3e-108">Se `condition` for avaliada como `false`, a expressão `alternative` será avaliada e seu resultado se tornará o resultado da operação.</span><span class="sxs-lookup"><span data-stu-id="62b3e-108">If `condition` evaluates to `false`, the `alternative` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="62b3e-109">Somente `consequent` ou `alternative` é avaliada.</span><span class="sxs-lookup"><span data-stu-id="62b3e-109">Only `consequent` or `alternative` is evaluated.</span></span>

<span data-ttu-id="62b3e-110">O tipo de `consequent` e `alternative` devem ser iguais ou deve haver uma conversão implícita de um tipo para outro.</span><span class="sxs-lookup"><span data-stu-id="62b3e-110">The type of `consequent` and `alternative` must be the same, or there must be an implicit conversion from one type to the other.</span></span>

<span data-ttu-id="62b3e-111">O operador condicional é associativo direito, ou seja, uma expressão da forma</span><span class="sxs-lookup"><span data-stu-id="62b3e-111">The conditional operator is right-associative, that is, an expression of the form</span></span>

```csharp
a ? b : c ? d : e
```

<span data-ttu-id="62b3e-112">é avaliada como</span><span class="sxs-lookup"><span data-stu-id="62b3e-112">is evaluated as</span></span>

```csharp
a ? b : (c ? d : e)
```

> [!TIP]
> <span data-ttu-id="62b3e-113">Você pode usar o seguinte dispositivo mnemônico para se lembrar de como o operador condicional é avaliado:</span><span class="sxs-lookup"><span data-stu-id="62b3e-113">You can use the following mnemonic device to remember how the conditional operator is evaluated:</span></span>
>
> ```text
> is this condition true ? yes : no
> ```

<span data-ttu-id="62b3e-114">O exemplo a seguir demonstra o uso do operador condicional:</span><span class="sxs-lookup"><span data-stu-id="62b3e-114">The following example demonstrates the usage of the conditional operator:</span></span>

[!code-csharp-interactive[non ref conditional](~/samples/csharp/language-reference/operators/ConditionalOperator.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a><span data-ttu-id="62b3e-115">Expressão condicional ref</span><span class="sxs-lookup"><span data-stu-id="62b3e-115">Conditional ref expression</span></span>

<span data-ttu-id="62b3e-116">Começando com C# 7.2, use a expressão de referência condicional para retornar a referência ao resultado de uma de duas expressões.</span><span class="sxs-lookup"><span data-stu-id="62b3e-116">Beginning with C# 7.2, you can use the conditional ref expression to return the reference to the result of one of the two expressions.</span></span> <span data-ttu-id="62b3e-117">Você pode atribuir essa referência a uma variável [ref local](../keywords/ref.md#ref-locals) ou [ref readonly local](../keywords/ref.md#ref-readonly-locals) ou usá-la como um [valor de retorno de referência](../keywords/ref.md#reference-return-values) ou como um [parâmetro do método `ref`](../keywords/ref.md#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="62b3e-117">You can assign that reference to a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable, or use it as a [reference return value](../keywords/ref.md#reference-return-values) or as a [`ref` method parameter](../keywords/ref.md#passing-an-argument-by-reference).</span></span>

<span data-ttu-id="62b3e-118">A sintaxe da expressão condicional ref é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="62b3e-118">The syntax for the conditional ref expression is as follows:</span></span>

```csharp
condition ? ref consequent : ref alternative
```

<span data-ttu-id="62b3e-119">Como o operador condicional original, a expressão condicional ref avalia apenas uma das duas expressões: `consequent` ou `alternative`.</span><span class="sxs-lookup"><span data-stu-id="62b3e-119">Like the original conditional operator, the conditional ref expression evaluates only one of the two expressions: either `consequent` or `alternative`.</span></span>

<span data-ttu-id="62b3e-120">No caso da expressão condicional ref, o tipo de `consequent` e `alternative` devem ser iguais.</span><span class="sxs-lookup"><span data-stu-id="62b3e-120">In the case of the conditional ref expression, the type of `consequent` and `alternative` must be the same.</span></span>

<span data-ttu-id="62b3e-121">O exemplo a seguir demonstra o uso da expressão condicional ref:</span><span class="sxs-lookup"><span data-stu-id="62b3e-121">The following example demonstrates the usage of the conditional ref expression:</span></span>

[!code-csharp-interactive[conditional ref](~/samples/csharp/language-reference/operators/ConditionalOperator.cs#ConditionalRef)]

<span data-ttu-id="62b3e-122">Para saber mais, confira a [nota da proposta do recurso](../../../../_csharplang/proposals/csharp-7.2/conditional-ref.md).</span><span class="sxs-lookup"><span data-stu-id="62b3e-122">For more information, see the [feature proposal note](../../../../_csharplang/proposals/csharp-7.2/conditional-ref.md).</span></span>

## <a name="conditional-operator-and-an-ifelse-statement"></a><span data-ttu-id="62b3e-123">Operador condicional e uma instrução `if..else`</span><span class="sxs-lookup"><span data-stu-id="62b3e-123">Conditional operator and an `if..else` statement</span></span>

<span data-ttu-id="62b3e-124">O uso do operador condicional em uma instrução [ if-else ](../keywords/if-else.md) pode resultar em código mais conciso em casos onde você precisa calcular um valor condicionalmente.</span><span class="sxs-lookup"><span data-stu-id="62b3e-124">Use of the conditional operator over an [if-else](../keywords/if-else.md) statement might result in more concise code in cases when you need conditionally to compute a value.</span></span> <span data-ttu-id="62b3e-125">O exemplo a seguir demonstra duas maneiras de classificar um inteiro como negativo ou não negativo:</span><span class="sxs-lookup"><span data-stu-id="62b3e-125">The following example demonstrates two ways to classify an integer as negative or nonnegative:</span></span>

[!code-csharp[conditional and if-else](~/samples/csharp/language-reference/operators/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a><span data-ttu-id="62b3e-126">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="62b3e-126">Operator overloadability</span></span>

<span data-ttu-id="62b3e-127">O operador condicional não pode ser sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="62b3e-127">The conditional operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="62b3e-128">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="62b3e-128">C# language specification</span></span>

<span data-ttu-id="62b3e-129">Para saber mais, confira a seção [Operador condicional](~/_csharplang/spec/expressions.md#conditional-operator) na [especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="62b3e-129">For more information, see the [Conditional operator](~/_csharplang/spec/expressions.md#conditional-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="62b3e-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="62b3e-130">See also</span></span>

- [<span data-ttu-id="62b3e-131">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="62b3e-131">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="62b3e-132">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="62b3e-132">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="62b3e-133">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="62b3e-133">C# Operators</span></span>](index.md)
- [<span data-ttu-id="62b3e-134">Instrução if-else</span><span class="sxs-lookup"><span data-stu-id="62b3e-134">if-else statement</span></span>](../keywords/if-else.md)
- <span data-ttu-id="62b3e-135">[Operadores ?. e ?[]](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="62b3e-135">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="62b3e-136">Operador ??</span><span class="sxs-lookup"><span data-stu-id="62b3e-136">?? operator</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="62b3e-137">ref keyword</span><span class="sxs-lookup"><span data-stu-id="62b3e-137">ref keyword</span></span>](../keywords/ref.md)
