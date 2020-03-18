---
title: 'Operador ?: – referência do C#'
ms.date: 03/06/2020
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 1a17ba092d4228ba909c8774a2f7e15c2c50cfdc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399514"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="7a890-102">Operador ?: (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="7a890-102">?: operator (C# reference)</span></span>

<span data-ttu-id="7a890-103">O operador `?:`condicional , também conhecido como operador condicionário ternário, avalia uma expressão booleana e retorna o resultado de `true` `false`uma das duas expressões, dependendo se a expressão booleana avalia ou .</span><span class="sxs-lookup"><span data-stu-id="7a890-103">The conditional operator `?:`, also known as the ternary conditional operator, evaluates a Boolean expression and returns the result of one of the two expressions, depending on whether the Boolean expression evaluates to `true` or `false`.</span></span>

<span data-ttu-id="7a890-104">A sintaxe do operador condicional é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="7a890-104">The syntax for the conditional operator is as follows:</span></span>

```csharp
condition ? consequent : alternative
```

<span data-ttu-id="7a890-105">A expressão `condition` deve ser avaliada para `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="7a890-105">The `condition` expression must evaluate to `true` or `false`.</span></span> <span data-ttu-id="7a890-106">Se `condition` for avaliada como `true`, a expressão `consequent` será avaliada e seu resultado se tornará o resultado da operação.</span><span class="sxs-lookup"><span data-stu-id="7a890-106">If `condition` evaluates to `true`, the `consequent` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="7a890-107">Se `condition` for avaliada como `false`, a expressão `alternative` será avaliada e seu resultado se tornará o resultado da operação.</span><span class="sxs-lookup"><span data-stu-id="7a890-107">If `condition` evaluates to `false`, the `alternative` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="7a890-108">Somente `consequent` ou `alternative` é avaliada.</span><span class="sxs-lookup"><span data-stu-id="7a890-108">Only `consequent` or `alternative` is evaluated.</span></span>

<span data-ttu-id="7a890-109">O tipo de `consequent` e `alternative` devem ser iguais ou deve haver uma conversão implícita de um tipo para outro.</span><span class="sxs-lookup"><span data-stu-id="7a890-109">The type of `consequent` and `alternative` must be the same, or there must be an implicit conversion from one type to the other.</span></span>

<span data-ttu-id="7a890-110">O operador condicional é associativo direito, ou seja, uma expressão da forma</span><span class="sxs-lookup"><span data-stu-id="7a890-110">The conditional operator is right-associative, that is, an expression of the form</span></span>

```csharp
a ? b : c ? d : e
```

<span data-ttu-id="7a890-111">é avaliada como</span><span class="sxs-lookup"><span data-stu-id="7a890-111">is evaluated as</span></span>

```csharp
a ? b : (c ? d : e)
```

> [!TIP]
> <span data-ttu-id="7a890-112">Você pode usar o seguinte dispositivo mnemônico para se lembrar de como o operador condicional é avaliado:</span><span class="sxs-lookup"><span data-stu-id="7a890-112">You can use the following mnemonic device to remember how the conditional operator is evaluated:</span></span>
>
> ```text
> is this condition true ? yes : no
> ```

<span data-ttu-id="7a890-113">O exemplo a seguir demonstra o uso do operador condicional:</span><span class="sxs-lookup"><span data-stu-id="7a890-113">The following example demonstrates the usage of the conditional operator:</span></span>

[!code-csharp-interactive[non ref conditional](snippets/ConditionalOperator.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a><span data-ttu-id="7a890-114">Expressão condicional ref</span><span class="sxs-lookup"><span data-stu-id="7a890-114">Conditional ref expression</span></span>

<span data-ttu-id="7a890-115">Começando com C# 7.2, uma variável [local ou](../keywords/ref.md#ref-locals) [ref readonly](../keywords/ref.md#ref-readonly-locals) pode ser atribuída condicionalmente com a expressão condicional do ref.</span><span class="sxs-lookup"><span data-stu-id="7a890-115">Beginning with C# 7.2, a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable can be assigned conditionally with the conditional ref expression.</span></span> <span data-ttu-id="7a890-116">Você também pode usar a expressão condicional do ref como um [valor de retorno de referência](../keywords/ref.md#reference-return-values) ou como um [ `ref` argumento de método](../keywords/ref.md#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="7a890-116">You can also use the conditional ref expression as a [reference return value](../keywords/ref.md#reference-return-values) or as a [`ref` method argument](../keywords/ref.md#passing-an-argument-by-reference).</span></span>

<span data-ttu-id="7a890-117">A sintaxe da expressão condicional ref é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="7a890-117">The syntax for the conditional ref expression is as follows:</span></span>

```csharp
condition ? ref consequent : ref alternative
```

<span data-ttu-id="7a890-118">Como o operador condicional original, a expressão condicional ref avalia apenas uma das duas expressões: `consequent` ou `alternative`.</span><span class="sxs-lookup"><span data-stu-id="7a890-118">Like the original conditional operator, the conditional ref expression evaluates only one of the two expressions: either `consequent` or `alternative`.</span></span>

<span data-ttu-id="7a890-119">No caso da expressão condicional ref, o tipo de `consequent` e `alternative` devem ser iguais.</span><span class="sxs-lookup"><span data-stu-id="7a890-119">In the case of the conditional ref expression, the type of `consequent` and `alternative` must be the same.</span></span>

<span data-ttu-id="7a890-120">O exemplo a seguir demonstra o uso da expressão condicional ref:</span><span class="sxs-lookup"><span data-stu-id="7a890-120">The following example demonstrates the usage of the conditional ref expression:</span></span>

[!code-csharp-interactive[conditional ref](snippets/ConditionalOperator.cs#ConditionalRef)]

## <a name="conditional-operator-and-an-ifelse-statement"></a><span data-ttu-id="7a890-121">Operador condicional e uma instrução `if..else`</span><span class="sxs-lookup"><span data-stu-id="7a890-121">Conditional operator and an `if..else` statement</span></span>

<span data-ttu-id="7a890-122">O uso do operador condicional em vez de uma declaração [if-else](../keywords/if-else.md) pode resultar em um código mais conciso nos casos em que você precisa de condicionalmente para calcular um valor.</span><span class="sxs-lookup"><span data-stu-id="7a890-122">Use of the conditional operator instead of an [if-else](../keywords/if-else.md) statement might result in more concise code in cases when you need conditionally to compute a value.</span></span> <span data-ttu-id="7a890-123">O exemplo a seguir demonstra duas maneiras de classificar um inteiro como negativo ou não negativo:</span><span class="sxs-lookup"><span data-stu-id="7a890-123">The following example demonstrates two ways to classify an integer as negative or nonnegative:</span></span>

[!code-csharp[conditional and if-else](snippets/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a><span data-ttu-id="7a890-124">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="7a890-124">Operator overloadability</span></span>

<span data-ttu-id="7a890-125">Um tipo definido pelo usuário não pode sobrecarregar o operador condicional.</span><span class="sxs-lookup"><span data-stu-id="7a890-125">A user-defined type cannot overload the conditional operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7a890-126">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="7a890-126">C# language specification</span></span>

<span data-ttu-id="7a890-127">Para saber mais, confira a seção [Operador condicional](~/_csharplang/spec/expressions.md#conditional-operator) na [especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="7a890-127">For more information, see the [Conditional operator](~/_csharplang/spec/expressions.md#conditional-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="7a890-128">Para obter mais informações sobre a expressão condicional do árbitro, consulte a [nota de proposta do recurso](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).</span><span class="sxs-lookup"><span data-stu-id="7a890-128">For more information about the conditional ref expression, see the [feature proposal note](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7a890-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="7a890-129">See also</span></span>

- [<span data-ttu-id="7a890-130">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="7a890-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="7a890-131">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="7a890-131">C# operators</span></span>](index.md)
- [<span data-ttu-id="7a890-132">se-else declaração</span><span class="sxs-lookup"><span data-stu-id="7a890-132">if-else statement</span></span>](../keywords/if-else.md)
- <span data-ttu-id="7a890-133">[Operadores ?. e ?[]](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="7a890-133">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="7a890-134">?? E?? = operadores</span><span class="sxs-lookup"><span data-stu-id="7a890-134">?? and ??= operators</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="7a890-135">ref keyword</span><span class="sxs-lookup"><span data-stu-id="7a890-135">ref keyword</span></span>](../keywords/ref.md)
