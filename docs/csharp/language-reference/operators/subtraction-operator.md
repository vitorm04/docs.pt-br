---
title: '- Operador -= – Referência de C#'
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
ms.openlocfilehash: 9f43a863de69122e251204668af2ea989fcc993c
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300083"
---
# <a name="--and---operators-c-reference"></a><span data-ttu-id="d0115-102">Operadores - e -= (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="d0115-102">- and -= operators (C# Reference)</span></span>

<span data-ttu-id="d0115-103">O operador `-` é compatível com os tipos numéricos internos e com os tipos [delegados](../keywords/delegate.md).</span><span class="sxs-lookup"><span data-stu-id="d0115-103">The `-` operator is supported by the built-in numeric types and [delegate](../keywords/delegate.md) types.</span></span>

<span data-ttu-id="d0115-104">Para obter informações sobre o operador `-` aritmético, consulte as seções [Operadores de adição e subtração unários](arithmetic-operators.md#unary-plus-and-minus-operators) e [Operador de subtração -](arithmetic-operators.md#subtraction-operator--) do artigo [Operadores aritméticos](arithmetic-operators.md).</span><span class="sxs-lookup"><span data-stu-id="d0115-104">For information about the arithmetic `-` operator, see the [Unary plus and minus operators](arithmetic-operators.md#unary-plus-and-minus-operators) and [Subtraction operator -](arithmetic-operators.md#subtraction-operator--) sections of the [Arithmetic operators](arithmetic-operators.md) article.</span></span>

## <a name="delegate-removal"></a><span data-ttu-id="d0115-105">Remoção de delegado</span><span class="sxs-lookup"><span data-stu-id="d0115-105">Delegate removal</span></span>

<span data-ttu-id="d0115-106">Para operandos do mesmo tipo [delegado](../keywords/delegate.md), o operador `-` retorna uma instância de delegado que é calculada da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="d0115-106">For operands of the same [delegate](../keywords/delegate.md) type, the `-` operator returns a delegate instance that is calculated as follows:</span></span>

- <span data-ttu-id="d0115-107">Se ambos os operandos forem não nulos e a lista de invocação do segundo operando for uma sublista contígua apropriada da lista de invocação do primeiro operando, o resultado da operação será uma nova lista de invocação obtida removendo-se as entradas do segundo operando da lista de invocação do primeiro operando.</span><span class="sxs-lookup"><span data-stu-id="d0115-107">If both operands are non-null and the invocation list of the second operand is a proper contiguous sublist of the invocation list of the first operand, the result of the operation is a new invocation list that is obtained by removing the second operand's entries from the invocation list of the first operand.</span></span> <span data-ttu-id="d0115-108">Se a lista do segundo operando corresponder a várias sublistas contíguas na lista do primeiro operando, somente a sublista correspondente mais à direita será removida.</span><span class="sxs-lookup"><span data-stu-id="d0115-108">If the second operand's list matches multiple contiguous sublists in the first operand's list, only the right-most matching sublist is removed.</span></span> <span data-ttu-id="d0115-109">Se a remoção resultar em uma lista vazia, o resultado será `null`.</span><span class="sxs-lookup"><span data-stu-id="d0115-109">If removal results in an empty list, the result is `null`.</span></span>
- <span data-ttu-id="d0115-110">Se a lista de invocação do segundo operando não for uma sublista contígua apropriada da lista de invocação do primeiro operando, o resultado da operação será o primeiro operando.</span><span class="sxs-lookup"><span data-stu-id="d0115-110">If the invocation list of the second operand is not a proper contiguous sublist of the invocation list of the first operand, the result of the operation is the first operand.</span></span>
- <span data-ttu-id="d0115-111">Se o primeiro operando for `null`, o resultado da operação será `null`.</span><span class="sxs-lookup"><span data-stu-id="d0115-111">If the first operand is `null`, the result of the operation is `null`.</span></span> <span data-ttu-id="d0115-112">Se o segundo operando for `null`, o resultado da operação será o primeiro operando.</span><span class="sxs-lookup"><span data-stu-id="d0115-112">If the second operand is `null`, the result of the operation is the first operand.</span></span>

<span data-ttu-id="d0115-113">A exemplo a seguir mostra como a operação `-` executa a remoção de delegado:</span><span class="sxs-lookup"><span data-stu-id="d0115-113">The following example shows how the `-` operation performs delegate removal:</span></span>

[!code-csharp-interactive[delegate removal](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemoval)]

## <a name="subtraction-assignment-operator--"></a><span data-ttu-id="d0115-114">Operador de atribuição de subtração -=</span><span class="sxs-lookup"><span data-stu-id="d0115-114">Subtraction assignment operator -=</span></span>

<span data-ttu-id="d0115-115">Uma expressão que usa o operador `-=`, como</span><span class="sxs-lookup"><span data-stu-id="d0115-115">An expression using the `-=` operator, such as</span></span>

```csharp
x -= y
```

<span data-ttu-id="d0115-116">equivale a</span><span class="sxs-lookup"><span data-stu-id="d0115-116">is equivalent to</span></span>

```csharp
x = x - y
```

<span data-ttu-id="d0115-117">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="d0115-117">except that `x` is only evaluated once.</span></span>
  
<span data-ttu-id="d0115-118">O exemplo a seguir demonstra o uso do operador `-=`:</span><span class="sxs-lookup"><span data-stu-id="d0115-118">The following example demonstrates the usage of the `-=` operator:</span></span>

[!code-csharp-interactive[-= examples](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#SubtractAndAssign)]

<span data-ttu-id="d0115-119">Você também usará o operador `-=` para especificar um método de manipulador de eventos a remover ao cancelar a assinatura de um [evento](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="d0115-119">You also use the `-=` operator to specify an event handler method to remove when you unsubscribe from an [event](../keywords/event.md).</span></span> <span data-ttu-id="d0115-120">Para obter mais informações, confira [Como assinar e cancelar a assinatura de eventos](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="d0115-120">For more information, see [How to: subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="d0115-121">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="d0115-121">Operator overloadability</span></span>

<span data-ttu-id="d0115-122">Um tipo definido pelo usuário pode [sobrecarregar](../keywords/operator.md) o operador `-`.</span><span class="sxs-lookup"><span data-stu-id="d0115-122">A user-defined type can [overload](../keywords/operator.md) the `-` operator.</span></span> <span data-ttu-id="d0115-123">Quando um operador `-` binário é sobrecarregado, o operador `-=` também é implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="d0115-123">When a binary `-` operator is overloaded, the `-=` operator is also implicitly overloaded.</span></span> <span data-ttu-id="d0115-124">Um tipo definido pelo usuário não pode sobrecarregar explicitamente o operador `-=`.</span><span class="sxs-lookup"><span data-stu-id="d0115-124">A user-defined type cannot explicitly overload the `-=` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d0115-125">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="d0115-125">C# language specification</span></span>

<span data-ttu-id="d0115-126">Para obter mais informações, veja as seções [Operador de subtração unário](~/_csharplang/spec/expressions.md#unary-minus-operator) e [Operador de subtração](~/_csharplang/spec/expressions.md#subtraction-operator) da [Especificação de linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="d0115-126">For more information, see the [Unary minus operator](~/_csharplang/spec/expressions.md#unary-minus-operator) and [Subtraction operator](~/_csharplang/spec/expressions.md#subtraction-operator) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d0115-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0115-127">See also</span></span>

- [<span data-ttu-id="d0115-128">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="d0115-128">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d0115-129">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="d0115-129">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d0115-130">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="d0115-130">C# Operators</span></span>](index.md)
- [<span data-ttu-id="d0115-131">Delegados</span><span class="sxs-lookup"><span data-stu-id="d0115-131">Delegates</span></span>](../../programming-guide/delegates/index.md)
- [<span data-ttu-id="d0115-132">Eventos</span><span class="sxs-lookup"><span data-stu-id="d0115-132">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="d0115-133">Checked e unchecked</span><span class="sxs-lookup"><span data-stu-id="d0115-133">Checked and unchecked</span></span>](../keywords/checked-and-unchecked.md)
- [<span data-ttu-id="d0115-134">Operadores aritméticos</span><span class="sxs-lookup"><span data-stu-id="d0115-134">Arithmetic operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="d0115-135">Operadores + e +=</span><span class="sxs-lookup"><span data-stu-id="d0115-135">+ and += operators</span></span>](addition-operator.md)
