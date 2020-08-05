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
ms.openlocfilehash: 8e6753a08bbd96f980b3c5901e763f2dfad055c6
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555351"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="d9baa-102">Operador ?: (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="d9baa-102">?: operator (C# reference)</span></span>

<span data-ttu-id="d9baa-103">O operador condicional `?:` , também conhecido como operador condicional Ternário, avalia uma expressão booliana e retorna o resultado de uma das duas expressões, dependendo se a expressão booliana é avaliada como `true` ou `false` .</span><span class="sxs-lookup"><span data-stu-id="d9baa-103">The conditional operator `?:`, also known as the ternary conditional operator, evaluates a Boolean expression and returns the result of one of the two expressions, depending on whether the Boolean expression evaluates to `true` or `false`.</span></span>

<span data-ttu-id="d9baa-104">A sintaxe do operador condicional é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="d9baa-104">The syntax for the conditional operator is as follows:</span></span>

```csharp
condition ? consequent : alternative
```

<span data-ttu-id="d9baa-105">A expressão `condition` deve ser avaliada para `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="d9baa-105">The `condition` expression must evaluate to `true` or `false`.</span></span> <span data-ttu-id="d9baa-106">Se `condition` for avaliada como `true`, a expressão `consequent` será avaliada e seu resultado se tornará o resultado da operação.</span><span class="sxs-lookup"><span data-stu-id="d9baa-106">If `condition` evaluates to `true`, the `consequent` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="d9baa-107">Se `condition` for avaliada como `false`, a expressão `alternative` será avaliada e seu resultado se tornará o resultado da operação.</span><span class="sxs-lookup"><span data-stu-id="d9baa-107">If `condition` evaluates to `false`, the `alternative` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="d9baa-108">Somente `consequent` ou `alternative` é avaliada.</span><span class="sxs-lookup"><span data-stu-id="d9baa-108">Only `consequent` or `alternative` is evaluated.</span></span>

<span data-ttu-id="d9baa-109">O tipo de `consequent` e `alternative` devem ser iguais ou deve haver uma conversão implícita de um tipo para outro.</span><span class="sxs-lookup"><span data-stu-id="d9baa-109">The type of `consequent` and `alternative` must be the same, or there must be an implicit conversion from one type to the other.</span></span>

<span data-ttu-id="d9baa-110">O operador condicional é associativo direito, ou seja, uma expressão da forma</span><span class="sxs-lookup"><span data-stu-id="d9baa-110">The conditional operator is right-associative, that is, an expression of the form</span></span>

```csharp
a ? b : c ? d : e
```

<span data-ttu-id="d9baa-111">é avaliada como</span><span class="sxs-lookup"><span data-stu-id="d9baa-111">is evaluated as</span></span>

```csharp
a ? b : (c ? d : e)
```

> [!TIP]
> <span data-ttu-id="d9baa-112">Você pode usar o seguinte dispositivo mnemônico para se lembrar de como o operador condicional é avaliado:</span><span class="sxs-lookup"><span data-stu-id="d9baa-112">You can use the following mnemonic device to remember how the conditional operator is evaluated:</span></span>
>
> ```text
> is this condition true ? yes : no
> ```

<span data-ttu-id="d9baa-113">O exemplo a seguir demonstra o uso do operador condicional:</span><span class="sxs-lookup"><span data-stu-id="d9baa-113">The following example demonstrates the usage of the conditional operator:</span></span>

[!code-csharp-interactive[non ref conditional](snippets/ConditionalOperator.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a><span data-ttu-id="d9baa-114">Expressão condicional ref</span><span class="sxs-lookup"><span data-stu-id="d9baa-114">Conditional ref expression</span></span>

<span data-ttu-id="d9baa-115">A partir do C# 7,2, uma variável local [ref local](../keywords/ref.md#ref-locals) ou [ref ReadOnly](../keywords/ref.md#ref-readonly-locals) pode ser atribuída condicionalmente com a expressão ref condicional.</span><span class="sxs-lookup"><span data-stu-id="d9baa-115">Beginning with C# 7.2, a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable can be assigned conditionally with the conditional ref expression.</span></span> <span data-ttu-id="d9baa-116">Você também pode usar a expressão ref condicional como um [valor de retorno de referência](../keywords/ref.md#reference-return-values) ou como um [ `ref` argumento de método](../keywords/ref.md#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="d9baa-116">You can also use the conditional ref expression as a [reference return value](../keywords/ref.md#reference-return-values) or as a [`ref` method argument](../keywords/ref.md#passing-an-argument-by-reference).</span></span>

<span data-ttu-id="d9baa-117">A sintaxe da expressão condicional ref é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="d9baa-117">The syntax for the conditional ref expression is as follows:</span></span>

```csharp
condition ? ref consequent : ref alternative
```

<span data-ttu-id="d9baa-118">Como o operador condicional original, a expressão condicional ref avalia apenas uma das duas expressões: `consequent` ou `alternative`.</span><span class="sxs-lookup"><span data-stu-id="d9baa-118">Like the original conditional operator, the conditional ref expression evaluates only one of the two expressions: either `consequent` or `alternative`.</span></span>

<span data-ttu-id="d9baa-119">No caso da expressão condicional ref, o tipo de `consequent` e `alternative` devem ser iguais.</span><span class="sxs-lookup"><span data-stu-id="d9baa-119">In the case of the conditional ref expression, the type of `consequent` and `alternative` must be the same.</span></span>

<span data-ttu-id="d9baa-120">O exemplo a seguir demonstra o uso da expressão condicional ref:</span><span class="sxs-lookup"><span data-stu-id="d9baa-120">The following example demonstrates the usage of the conditional ref expression:</span></span>

[!code-csharp-interactive[conditional ref](snippets/ConditionalOperator.cs#ConditionalRef)]

## <a name="conditional-operator-and-an-ifelse-statement"></a><span data-ttu-id="d9baa-121">Operador condicional e uma instrução `if..else`</span><span class="sxs-lookup"><span data-stu-id="d9baa-121">Conditional operator and an `if..else` statement</span></span>

<span data-ttu-id="d9baa-122">O uso do operador condicional em vez de uma instrução [If-Else](../keywords/if-else.md) pode resultar em um código mais conciso em casos em que você precisa de uma condição para computar um valor.</span><span class="sxs-lookup"><span data-stu-id="d9baa-122">Use of the conditional operator instead of an [if-else](../keywords/if-else.md) statement might result in more concise code in cases when you need conditionally to compute a value.</span></span> <span data-ttu-id="d9baa-123">O exemplo a seguir demonstra duas maneiras de classificar um inteiro como negativo ou não negativo:</span><span class="sxs-lookup"><span data-stu-id="d9baa-123">The following example demonstrates two ways to classify an integer as negative or nonnegative:</span></span>

[!code-csharp[conditional and if-else](snippets/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a><span data-ttu-id="d9baa-124">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="d9baa-124">Operator overloadability</span></span>

<span data-ttu-id="d9baa-125">Um tipo definido pelo usuário não pode sobrecarregar o operador condicional.</span><span class="sxs-lookup"><span data-stu-id="d9baa-125">A user-defined type cannot overload the conditional operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d9baa-126">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="d9baa-126">C# language specification</span></span>

<span data-ttu-id="d9baa-127">Para saber mais, confira a seção [Operador condicional](~/_csharplang/spec/expressions.md#conditional-operator) na [especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="d9baa-127">For more information, see the [Conditional operator](~/_csharplang/spec/expressions.md#conditional-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="d9baa-128">Para obter mais informações sobre a expressão ref condicional, consulte a [Nota de proposta de recurso](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).</span><span class="sxs-lookup"><span data-stu-id="d9baa-128">For more information about the conditional ref expression, see the [feature proposal note](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d9baa-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="d9baa-129">See also</span></span>

- [<span data-ttu-id="d9baa-130">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="d9baa-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="d9baa-131">Operadores e expressões C#</span><span class="sxs-lookup"><span data-stu-id="d9baa-131">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="d9baa-132">Instrução if-else</span><span class="sxs-lookup"><span data-stu-id="d9baa-132">if-else statement</span></span>](../keywords/if-else.md)
- <span data-ttu-id="d9baa-133">[Operadores ?. e ?[]](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="d9baa-133">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="d9baa-134">?? e?? = operadores</span><span class="sxs-lookup"><span data-stu-id="d9baa-134">?? and ??= operators</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="d9baa-135">ref keyword</span><span class="sxs-lookup"><span data-stu-id="d9baa-135">ref keyword</span></span>](../keywords/ref.md)
