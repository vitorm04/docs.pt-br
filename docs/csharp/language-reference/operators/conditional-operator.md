---
description: 'Operador ?: – referência do C#'
title: 'Operador ?: – referência do C#'
ms.date: 09/17/2020
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: b6add045983619169bed0cd9f32eb27dba0a0338
ms.sourcegitcommit: a8730298170b8d96b4272e0c3dfc9819c606947b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90738873"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="8cb37-103">Operador ?: (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="8cb37-103">?: operator (C# reference)</span></span>

<span data-ttu-id="8cb37-104">O operador condicional `?:` , também conhecido como operador condicional Ternário, avalia uma expressão booliana e retorna o resultado de uma das duas expressões, dependendo se a expressão booliana é avaliada como `true` ou `false` .</span><span class="sxs-lookup"><span data-stu-id="8cb37-104">The conditional operator `?:`, also known as the ternary conditional operator, evaluates a Boolean expression and returns the result of one of the two expressions, depending on whether the Boolean expression evaluates to `true` or `false`.</span></span>

<span data-ttu-id="8cb37-105">A sintaxe do operador condicional é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="8cb37-105">The syntax for the conditional operator is as follows:</span></span>

```csharp
condition ? consequent : alternative
```

<span data-ttu-id="8cb37-106">A expressão `condition` deve ser avaliada para `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="8cb37-106">The `condition` expression must evaluate to `true` or `false`.</span></span> <span data-ttu-id="8cb37-107">Se `condition` for avaliada como `true`, a expressão `consequent` será avaliada e seu resultado se tornará o resultado da operação.</span><span class="sxs-lookup"><span data-stu-id="8cb37-107">If `condition` evaluates to `true`, the `consequent` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="8cb37-108">Se `condition` for avaliada como `false`, a expressão `alternative` será avaliada e seu resultado se tornará o resultado da operação.</span><span class="sxs-lookup"><span data-stu-id="8cb37-108">If `condition` evaluates to `false`, the `alternative` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="8cb37-109">Somente `consequent` ou `alternative` é avaliada.</span><span class="sxs-lookup"><span data-stu-id="8cb37-109">Only `consequent` or `alternative` is evaluated.</span></span>

<span data-ttu-id="8cb37-110">A partir do C# 9,0, as expressões condicionais são de tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="8cb37-110">Beginning with C# 9.0, conditional expressions are target-typed.</span></span> <span data-ttu-id="8cb37-111">Ou seja, se um tipo de destino de uma expressão condicional for conhecido, os tipos de `consequent` e `alternative` deverão ser conversíveis implicitamente para o tipo de destino, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="8cb37-111">That is, if a target type of a conditional expression is known, the types of `consequent` and `alternative` must be implicitly convertible to the target type, as the following example shows:</span></span>

[!code-csharp[target-typed conditional](snippets/shared/ConditionalOperator.cs#TargetTyped)]

<span data-ttu-id="8cb37-112">Se um tipo de destino de uma expressão condicional for desconhecido (por exemplo, quando você usar a [`var`](../keywords/var.md) palavra-chave) ou em C# 8,0 e anterior, o tipo de `consequent` e `alternative` deverá ser o mesmo ou deve haver uma conversão implícita de um tipo para o outro:</span><span class="sxs-lookup"><span data-stu-id="8cb37-112">If a target type of a conditional expression is unknown (for example, when you use the [`var`](../keywords/var.md) keyword) or in C# 8.0 and earlier, the type of `consequent` and `alternative` must be the same or there must be an implicit conversion from one type to the other:</span></span>

[!code-csharp[not target-typed conditional](snippets/shared/ConditionalOperator.cs#NotTargetTyped)]

<span data-ttu-id="8cb37-113">O operador condicional é associativo direito, ou seja, uma expressão da forma</span><span class="sxs-lookup"><span data-stu-id="8cb37-113">The conditional operator is right-associative, that is, an expression of the form</span></span>

```csharp
a ? b : c ? d : e
```

<span data-ttu-id="8cb37-114">é avaliada como</span><span class="sxs-lookup"><span data-stu-id="8cb37-114">is evaluated as</span></span>

```csharp
a ? b : (c ? d : e)
```

> [!TIP]
> <span data-ttu-id="8cb37-115">Você pode usar o seguinte dispositivo mnemônico para se lembrar de como o operador condicional é avaliado:</span><span class="sxs-lookup"><span data-stu-id="8cb37-115">You can use the following mnemonic device to remember how the conditional operator is evaluated:</span></span>
>
> ```text
> is this condition true ? yes : no
> ```

<span data-ttu-id="8cb37-116">O exemplo a seguir demonstra o uso do operador condicional:</span><span class="sxs-lookup"><span data-stu-id="8cb37-116">The following example demonstrates the usage of the conditional operator:</span></span>

[!code-csharp-interactive[non ref conditional](snippets/shared/ConditionalOperator.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a><span data-ttu-id="8cb37-117">Expressão condicional ref</span><span class="sxs-lookup"><span data-stu-id="8cb37-117">Conditional ref expression</span></span>

<span data-ttu-id="8cb37-118">A partir do C# 7,2, uma variável local [ref local](../keywords/ref.md#ref-locals) ou [ref ReadOnly](../keywords/ref.md#ref-readonly-locals) pode ser atribuída condicionalmente com uma expressão ref condicional.</span><span class="sxs-lookup"><span data-stu-id="8cb37-118">Beginning with C# 7.2, a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable can be assigned conditionally with a conditional ref expression.</span></span> <span data-ttu-id="8cb37-119">Você também pode usar uma expressão ref condicional como um [valor de retorno de referência](../keywords/ref.md#reference-return-values) ou como um [ `ref` argumento de método](../keywords/ref.md#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="8cb37-119">You can also use a conditional ref expression as a [reference return value](../keywords/ref.md#reference-return-values) or as a [`ref` method argument](../keywords/ref.md#passing-an-argument-by-reference).</span></span>

<span data-ttu-id="8cb37-120">A sintaxe de uma expressão ref condicional é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="8cb37-120">The syntax for a conditional ref expression is as follows:</span></span>

```csharp
condition ? ref consequent : ref alternative
```

<span data-ttu-id="8cb37-121">Assim como o operador condicional original, uma expressão ref condicional avalia apenas uma das duas expressões: `consequent` ou `alternative` .</span><span class="sxs-lookup"><span data-stu-id="8cb37-121">Like the original conditional operator, a conditional ref expression evaluates only one of the two expressions: either `consequent` or `alternative`.</span></span>

<span data-ttu-id="8cb37-122">No caso de uma expressão ref condicional, o tipo de `consequent` e `alternative` deve ser o mesmo.</span><span class="sxs-lookup"><span data-stu-id="8cb37-122">In the case of a conditional ref expression, the type of `consequent` and `alternative` must be the same.</span></span> <span data-ttu-id="8cb37-123">As expressões de referência condicional não são de tipo alvo.</span><span class="sxs-lookup"><span data-stu-id="8cb37-123">Conditional ref expressions are not target-typed.</span></span>

<span data-ttu-id="8cb37-124">O exemplo a seguir demonstra o uso de uma expressão de referência condicional:</span><span class="sxs-lookup"><span data-stu-id="8cb37-124">The following example demonstrates the usage of a conditional ref expression:</span></span>

[!code-csharp-interactive[conditional ref](snippets/shared/ConditionalOperator.cs#ConditionalRef)]

## <a name="conditional-operator-and-an-ifelse-statement"></a><span data-ttu-id="8cb37-125">Operador condicional e uma instrução `if..else`</span><span class="sxs-lookup"><span data-stu-id="8cb37-125">Conditional operator and an `if..else` statement</span></span>

<span data-ttu-id="8cb37-126">O uso do operador condicional em vez de uma instrução [If-Else](../keywords/if-else.md) pode resultar em um código mais conciso em casos em que você precisa de uma condição para computar um valor.</span><span class="sxs-lookup"><span data-stu-id="8cb37-126">Use of the conditional operator instead of an [if-else](../keywords/if-else.md) statement might result in more concise code in cases when you need conditionally to compute a value.</span></span> <span data-ttu-id="8cb37-127">O exemplo a seguir demonstra duas maneiras de classificar um inteiro como negativo ou não negativo:</span><span class="sxs-lookup"><span data-stu-id="8cb37-127">The following example demonstrates two ways to classify an integer as negative or nonnegative:</span></span>

[!code-csharp[conditional and if-else](snippets/shared/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a><span data-ttu-id="8cb37-128">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="8cb37-128">Operator overloadability</span></span>

<span data-ttu-id="8cb37-129">Um tipo definido pelo usuário não pode sobrecarregar o operador condicional.</span><span class="sxs-lookup"><span data-stu-id="8cb37-129">A user-defined type cannot overload the conditional operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8cb37-130">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="8cb37-130">C# language specification</span></span>

<span data-ttu-id="8cb37-131">Para saber mais, confira a seção [Operador condicional](~/_csharplang/spec/expressions.md#conditional-operator) na [especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="8cb37-131">For more information, see the [Conditional operator](~/_csharplang/spec/expressions.md#conditional-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="8cb37-132">Para obter mais informações sobre os recursos adicionados em C# 7,2 e posterior, consulte as seguintes notas de proposta de recurso:</span><span class="sxs-lookup"><span data-stu-id="8cb37-132">For more information about features added in C# 7.2 and later, see the following feature proposal notes:</span></span>

- [<span data-ttu-id="8cb37-133">Expressões de referência condicional (C# 7,2)</span><span class="sxs-lookup"><span data-stu-id="8cb37-133">Conditional ref expressions (C# 7.2)</span></span>](~/_csharplang/proposals/csharp-7.2/conditional-ref.md)
- [<span data-ttu-id="8cb37-134">Expressão condicional de tipo de destino (C# 9,0)</span><span class="sxs-lookup"><span data-stu-id="8cb37-134">Target-typed conditional expression (C# 9.0)</span></span>](~/_csharplang/proposals/csharp-9.0/target-typed-conditional-expression.md)

## <a name="see-also"></a><span data-ttu-id="8cb37-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="8cb37-135">See also</span></span>

- [<span data-ttu-id="8cb37-136">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="8cb37-136">C# reference</span></span>](../index.md)
- [<span data-ttu-id="8cb37-137">Operadores e expressões C#</span><span class="sxs-lookup"><span data-stu-id="8cb37-137">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="8cb37-138">Instrução if-else</span><span class="sxs-lookup"><span data-stu-id="8cb37-138">if-else statement</span></span>](../keywords/if-else.md)
- <span data-ttu-id="8cb37-139">[Operadores ?. e ?[]](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="8cb37-139">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="8cb37-140">?? e?? = operadores</span><span class="sxs-lookup"><span data-stu-id="8cb37-140">?? and ??= operators</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="8cb37-141">ref keyword</span><span class="sxs-lookup"><span data-stu-id="8cb37-141">ref keyword</span></span>](../keywords/ref.md)
