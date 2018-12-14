---
title: 'Operador ?: (Referência de C#)'
ms.date: 11/20/2018
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: cc9bde1d60a3272e2f24cfc05761171a31029c75
ms.sourcegitcommit: 6ae7cdd0437a32884556dd4826ca90e957b7a4e3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/06/2018
ms.locfileid: "50980616"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="ad16f-102">Operador ?: (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="ad16f-102">?: Operator (C# Reference)</span></span>

<span data-ttu-id="ad16f-103">O operador condicional `?:`, comumente conhecido como o operador condicional ternário, avalia uma expressão booliana e retorna o resultado da avaliação de uma de duas expressões, dependendo se a expressão booliana é avaliada como `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="ad16f-103">The conditional operator `?:`, commonly known as the ternary conditional operator, evaluates a Boolean expression, and returns the result of evaluating one of two expressions, depending on whether the Boolean expression evaluates to `true` or `false`.</span></span> <span data-ttu-id="ad16f-104">Começando com C# 7.2, a [expressão de referência condicional](#conditional-ref-expression) retorna a referência ao resultado de uma de duas expressões.</span><span class="sxs-lookup"><span data-stu-id="ad16f-104">Beginning with C# 7.2, the [conditional ref expression](#conditional-ref-expression) returns the reference to the result of one of the two expressions.</span></span>

<span data-ttu-id="ad16f-105">A sintaxe do operador condicional é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="ad16f-105">The syntax for the conditional operator is as follows:</span></span>

```csharp
condition ? consequence : alternative
```

<span data-ttu-id="ad16f-106">A expressão `condition` deve ser avaliada para `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="ad16f-106">The `condition` expression must evaluate to `true` or `false`.</span></span> <span data-ttu-id="ad16f-107">Se `condition` for avaliada como `true`, a expressão `consequence` será avaliada e seu resultado se tornará o resultado da operação.</span><span class="sxs-lookup"><span data-stu-id="ad16f-107">If `condition` evaluates to `true`, the `consequence` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="ad16f-108">Se `condition` for avaliada como `false`, a expressão `alternative` será avaliada e seu resultado se tornará o resultado da operação.</span><span class="sxs-lookup"><span data-stu-id="ad16f-108">If `condition` evaluates to `false`, the `alternative` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="ad16f-109">Somente `consequence` ou `alternative` é avaliada.</span><span class="sxs-lookup"><span data-stu-id="ad16f-109">Only `consequence` or `alternative` is evaluated.</span></span>

<span data-ttu-id="ad16f-110">O tipo de `consequence` e `alternative` devem ser iguais ou deve haver uma conversão implícita de um tipo para outro.</span><span class="sxs-lookup"><span data-stu-id="ad16f-110">The type of `consequence` and `alternative` must be the same, or there must be an implicit conversion from one type to the other.</span></span>

<span data-ttu-id="ad16f-111">O operador condicional é associativo direito, ou seja, uma expressão da forma</span><span class="sxs-lookup"><span data-stu-id="ad16f-111">The conditional operator is right-associative, that is, an expression of the form</span></span>

```csharp
a ? b : c ? d : e
```

<span data-ttu-id="ad16f-112">é avaliada como</span><span class="sxs-lookup"><span data-stu-id="ad16f-112">is evaluated as</span></span>

```csharp
a ? b : (c ? d : e)
```

<span data-ttu-id="ad16f-113">O exemplo a seguir demonstra o uso do operador condicional:</span><span class="sxs-lookup"><span data-stu-id="ad16f-113">The following example demonstrates the usage of the conditional operator:</span></span>

[!code-csharp[non ref condtional](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a><span data-ttu-id="ad16f-114">Expressão condicional ref</span><span class="sxs-lookup"><span data-stu-id="ad16f-114">Conditional ref expression</span></span>

<span data-ttu-id="ad16f-115">Começando com C# 7.2, use a expressão de referência condicional para retornar a referência ao resultado de uma de duas expressões.</span><span class="sxs-lookup"><span data-stu-id="ad16f-115">Beginning with C# 7.2, you can use the conditional ref expression to return the reference to the result of one of the two expressions.</span></span> <span data-ttu-id="ad16f-116">Você pode atribuir essa referência a uma variável [ref local](../keywords/ref.md#ref-locals) ou [ref readonly local](../keywords/ref.md#ref-readonly-locals) ou usá-la como um [valor de retorno de referência](../keywords/ref.md#reference-return-values) ou como um [parâmetro do método `ref`](../keywords/ref.md#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="ad16f-116">You can assign that reference to a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable, or use it as a [reference return value](../keywords/ref.md#reference-return-values) or as a [`ref` method parameter](../keywords/ref.md#passing-an-argument-by-reference).</span></span>

<span data-ttu-id="ad16f-117">A sintaxe da expressão condicional ref é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="ad16f-117">The syntax for the conditional ref expression is as follows:</span></span>

```csharp
condition ? ref consequence : ref alternative
```

<span data-ttu-id="ad16f-118">Como o operador condicional original, a expressão condicional ref avalia apenas uma das duas expressões: `consequence` ou `alternative`.</span><span class="sxs-lookup"><span data-stu-id="ad16f-118">Like the original conditional operator, the conditional ref expression evaluates only one of the two expressions: either `consequence` or `alternative`.</span></span>

<span data-ttu-id="ad16f-119">No caso da expressão condicional ref, o tipo de `consequence` e `alternative` devem ser iguais.</span><span class="sxs-lookup"><span data-stu-id="ad16f-119">In the case of the conditional ref expression, the type of `consequence` and `alternative` must be the same.</span></span>

<span data-ttu-id="ad16f-120">O exemplo a seguir demonstra o uso da expressão condicional ref:</span><span class="sxs-lookup"><span data-stu-id="ad16f-120">The following example demonstrates the usage of the conditional ref expression:</span></span>

[!code-csharp[conditional ref](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalRef)]

<span data-ttu-id="ad16f-121">Para saber mais, confira a [nota da proposta do recurso](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-7.2/conditional-ref.md).</span><span class="sxs-lookup"><span data-stu-id="ad16f-121">For more information, see the [feature proposal note](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-7.2/conditional-ref.md).</span></span>

## <a name="conditional-operator-and-an-ifelse-statement"></a><span data-ttu-id="ad16f-122">Operador condicional e uma instrução `if..else`</span><span class="sxs-lookup"><span data-stu-id="ad16f-122">Conditional operator and an `if..else` statement</span></span>

<span data-ttu-id="ad16f-123">O uso do operador condicional em uma instrução [ if-else ](../keywords/if-else.md) pode resultar em código mais conciso em casos onde você precisa calcular um valor condicionalmente.</span><span class="sxs-lookup"><span data-stu-id="ad16f-123">Use of the conditional operator over an [if-else](../keywords/if-else.md) statement might result in more concise code in cases when you need conditionally to compute a value.</span></span> <span data-ttu-id="ad16f-124">O exemplo a seguir demonstra duas maneiras de classificar um inteiro como negativo ou não negativo:</span><span class="sxs-lookup"><span data-stu-id="ad16f-124">The following example demonstrates two ways to classify an integer as negative or nonnegative:</span></span>

[!code-csharp[conditional and if-else](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#CompareWithIf)]

## <a name="operator-overloadability"></a><span data-ttu-id="ad16f-125">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="ad16f-125">Operator overloadability</span></span>

<span data-ttu-id="ad16f-126">O operador condicional não pode ser sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="ad16f-126">The conditional operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ad16f-127">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="ad16f-127">C# language specification</span></span>

<span data-ttu-id="ad16f-128">Para saber mais, confira a seção [Operador condicional](~/_csharplang/spec/expressions.md#conditional-operator) na [especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="ad16f-128">For more information, see the [Conditional operator](~/_csharplang/spec/expressions.md#conditional-operator) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ad16f-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ad16f-129">See also</span></span>

- [<span data-ttu-id="ad16f-130">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="ad16f-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ad16f-131">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="ad16f-131">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ad16f-132">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="ad16f-132">C# Operators</span></span>](index.md)
- [<span data-ttu-id="ad16f-133">Instrução if-else</span><span class="sxs-lookup"><span data-stu-id="ad16f-133">if-else statement</span></span>](../keywords/if-else.md)
- <span data-ttu-id="ad16f-134">[Operadores ?. e ?[]](null-conditional-operators.md)</span><span class="sxs-lookup"><span data-stu-id="ad16f-134">[?. and ?[] Operators](null-conditional-operators.md)</span></span>
- [<span data-ttu-id="ad16f-135">Operador ??</span><span class="sxs-lookup"><span data-stu-id="ad16f-135">?? Operator</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="ad16f-136">ref keyword</span><span class="sxs-lookup"><span data-stu-id="ad16f-136">ref keyword</span></span>](../keywords/ref.md)
