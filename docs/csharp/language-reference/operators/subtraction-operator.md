---
title: '- Operadores - e -= – referência do C#'
ms.custom: seodec18
ms.date: 05/27/2019
f1_keywords:
- -_CSharpKeyword
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction operator [C#]
- delegate removal [C#]
- '- operator [C#]'
- subtraction assignment operator [C#]
- event unsubscription [C#]
- -= operator [C#]
ms.assetid: 4de7a4fa-c69d-48e6-aff1-3130af970b2d
ms.openlocfilehash: cf642fcac7233d27f2ed9052829c145038e93419
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73038884"
---
# <a name="--and---operators-c-reference"></a><span data-ttu-id="14326-102">Operadores - e -= (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="14326-102">- and -= operators (C# reference)</span></span>

<span data-ttu-id="14326-103">Os operadores de `-` e `-=` são suportados pelos tipos numéricos [internos e de](../builtin-types/integral-numeric-types.md) [ponto flutuante](../builtin-types/floating-point-numeric-types.md) e tipos [delegados](../builtin-types/reference-types.md#the-delegate-type) .</span><span class="sxs-lookup"><span data-stu-id="14326-103">The `-` and `-=` operators are supported by the built-in [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types and [delegate](../builtin-types/reference-types.md#the-delegate-type) types.</span></span>

<span data-ttu-id="14326-104">Para obter informações sobre o operador `-` aritmético, consulte as seções [Operadores de adição e subtração unários](arithmetic-operators.md#unary-plus-and-minus-operators) e [Operador de subtração -](arithmetic-operators.md#subtraction-operator--) do artigo [Operadores aritméticos](arithmetic-operators.md).</span><span class="sxs-lookup"><span data-stu-id="14326-104">For information about the arithmetic `-` operator, see the [Unary plus and minus operators](arithmetic-operators.md#unary-plus-and-minus-operators) and [Subtraction operator -](arithmetic-operators.md#subtraction-operator--) sections of the [Arithmetic operators](arithmetic-operators.md) article.</span></span>

## <a name="delegate-removal"></a><span data-ttu-id="14326-105">Remoção de delegado</span><span class="sxs-lookup"><span data-stu-id="14326-105">Delegate removal</span></span>

<span data-ttu-id="14326-106">Para operandos do mesmo tipo [delegado](../builtin-types/reference-types.md#the-delegate-type), o operador `-` retorna uma instância de delegado que é calculada da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="14326-106">For operands of the same [delegate](../builtin-types/reference-types.md#the-delegate-type) type, the `-` operator returns a delegate instance that is calculated as follows:</span></span>

- <span data-ttu-id="14326-107">Se ambos os operandos forem não nulos e a lista de invocação do operando à direita for uma sublista contígua apropriada da lista de invocação do operando à esquerda, o resultado da operação será uma nova lista de invocação obtida removendo-se as entradas do operando à direita da lista de invocação do operando à esquerda.</span><span class="sxs-lookup"><span data-stu-id="14326-107">If both operands are non-null and the invocation list of the right-hand operand is a proper contiguous sublist of the invocation list of the left-hand operand, the result of the operation is a new invocation list that is obtained by removing the right-hand operand's entries from the invocation list of the left-hand operand.</span></span> <span data-ttu-id="14326-108">Se a lista do operando à direita corresponder a várias sublistas contíguas na lista do operando à esquerda, somente a sublista correspondente mais à direita será removida.</span><span class="sxs-lookup"><span data-stu-id="14326-108">If the right-hand operand's list matches multiple contiguous sublists in the left-hand operand's list, only the right-most matching sublist is removed.</span></span> <span data-ttu-id="14326-109">Se a remoção resultar em uma lista vazia, o resultado será `null`.</span><span class="sxs-lookup"><span data-stu-id="14326-109">If removal results in an empty list, the result is `null`.</span></span>

  [!code-csharp-interactive[delegate removal](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemoval)]

- <span data-ttu-id="14326-110">Se a lista de invocação do operando à direita não for uma sublista contígua apropriada da lista de invocação do operando à esquerda, o resultado da operação será o operando à esquerda.</span><span class="sxs-lookup"><span data-stu-id="14326-110">If the invocation list of the right-hand operand is not a proper contiguous sublist of the invocation list of the left-hand operand, the result of the operation is the left-hand operand.</span></span> <span data-ttu-id="14326-111">Por exemplo, a remoção de um delegado que não faz parte do delegado multicast não tem consequências, e o delegado multicast permanece inalterado.</span><span class="sxs-lookup"><span data-stu-id="14326-111">For example, removing a delegate that is not part of the multicast delegate does nothing and results in the unchanged multicast delegate.</span></span>

  [!code-csharp-interactive[delegate removal with no effect](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemovalNoChange)]

  <span data-ttu-id="14326-112">O exemplo anterior também demonstra que, durante a remoção de delegados, as instâncias de delegado são comparadas.</span><span class="sxs-lookup"><span data-stu-id="14326-112">The preceding example also demonstrates that during delegate removal delegate instances are compared.</span></span> <span data-ttu-id="14326-113">Por exemplo, delegados produzidos pela avaliação de [expressões lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) idênticas não são iguais.</span><span class="sxs-lookup"><span data-stu-id="14326-113">For example, delegates that are produced from evaluation of identical [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) are not equal.</span></span> <span data-ttu-id="14326-114">Para saber mais sobre a igualdade de delegados, confira a seção [Operadores de igualdade de delegados](~/_csharplang/spec/expressions.md#delegate-equality-operators) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="14326-114">For more information about delegate equality, see the [Delegate equality operators](~/_csharplang/spec/expressions.md#delegate-equality-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

- <span data-ttu-id="14326-115">Se o operando à esquerda for `null`, o resultado da operação será `null`.</span><span class="sxs-lookup"><span data-stu-id="14326-115">If the left-hand operand is `null`, the result of the operation is `null`.</span></span> <span data-ttu-id="14326-116">Se o operando à direita for `null`, o resultado da operação será o operando à esquerda.</span><span class="sxs-lookup"><span data-stu-id="14326-116">If the right-hand operand is `null`, the result of the operation is the left-hand operand.</span></span>

  [!code-csharp-interactive[delegate removal and null](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemovalAndNull)]

<span data-ttu-id="14326-117">Para combinar delegados, use o [operador `+`](addition-operator.md#delegate-combination).</span><span class="sxs-lookup"><span data-stu-id="14326-117">To combine delegates, use the [`+` operator](addition-operator.md#delegate-combination).</span></span>

<span data-ttu-id="14326-118">Para obter mais informações sobre tipos de delegado, veja [Delegados](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="14326-118">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="subtraction-assignment-operator--"></a><span data-ttu-id="14326-119">Operador de atribuição de subtração -=</span><span class="sxs-lookup"><span data-stu-id="14326-119">Subtraction assignment operator -=</span></span>

<span data-ttu-id="14326-120">Uma expressão que usa o operador `-=`, como</span><span class="sxs-lookup"><span data-stu-id="14326-120">An expression using the `-=` operator, such as</span></span>

```csharp
x -= y
```

<span data-ttu-id="14326-121">equivale a</span><span class="sxs-lookup"><span data-stu-id="14326-121">is equivalent to</span></span>

```csharp
x = x - y
```

<span data-ttu-id="14326-122">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="14326-122">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="14326-123">O exemplo a seguir demonstra o uso do operador `-=`:</span><span class="sxs-lookup"><span data-stu-id="14326-123">The following example demonstrates the usage of the `-=` operator:</span></span>

[!code-csharp-interactive[-= examples](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#SubtractAndAssign)]

<span data-ttu-id="14326-124">Você também usará o operador `-=` para especificar um método de manipulador de eventos a remover ao cancelar a assinatura de um [evento](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="14326-124">You also use the `-=` operator to specify an event handler method to remove when you unsubscribe from an [event](../keywords/event.md).</span></span> <span data-ttu-id="14326-125">Para obter mais informações, confira [Como assinar e cancelar a assinatura de eventos](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="14326-125">For more information, see [How to: subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="14326-126">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="14326-126">Operator overloadability</span></span>

<span data-ttu-id="14326-127">Um tipo definido pelo usuário pode [sobrecarregar](operator-overloading.md) o operador `-`.</span><span class="sxs-lookup"><span data-stu-id="14326-127">A user-defined type can [overload](operator-overloading.md) the `-` operator.</span></span> <span data-ttu-id="14326-128">Quando um operador `-` binário é sobrecarregado, o operador `-=` também é implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="14326-128">When a binary `-` operator is overloaded, the `-=` operator is also implicitly overloaded.</span></span> <span data-ttu-id="14326-129">Um tipo definido pelo usuário não pode sobrecarregar explicitamente o operador `-=`.</span><span class="sxs-lookup"><span data-stu-id="14326-129">A user-defined type cannot explicitly overload the `-=` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="14326-130">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="14326-130">C# language specification</span></span>

<span data-ttu-id="14326-131">Para obter mais informações, veja as seções [Operador de subtração unário](~/_csharplang/spec/expressions.md#unary-minus-operator) e [Operador de subtração](~/_csharplang/spec/expressions.md#subtraction-operator) da [Especificação de linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="14326-131">For more information, see the [Unary minus operator](~/_csharplang/spec/expressions.md#unary-minus-operator) and [Subtraction operator](~/_csharplang/spec/expressions.md#subtraction-operator) sections of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="14326-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="14326-132">See also</span></span>

- [<span data-ttu-id="14326-133">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="14326-133">C# reference</span></span>](../index.md)
- [<span data-ttu-id="14326-134">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="14326-134">C# operators</span></span>](index.md)
- [<span data-ttu-id="14326-135">Eventos</span><span class="sxs-lookup"><span data-stu-id="14326-135">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="14326-136">Operadores aritméticos</span><span class="sxs-lookup"><span data-stu-id="14326-136">Arithmetic operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="14326-137">Operadores + e +=</span><span class="sxs-lookup"><span data-stu-id="14326-137">+ and += operators</span></span>](addition-operator.md)
