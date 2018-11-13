---
title: Operador || (Referência de C#)
ms.date: 11/06/2018
f1_keywords:
- '||_CSharpKeyword'
helpviewer_keywords:
- logical OR operator [C#]
- conditional-OR operator (||) [C#]
- '|| operator [C#]'
ms.assetid: 7d442d8e-400d-421f-b4d2-034bf82bcbdc
ms.openlocfilehash: a391078372e4ec0a3882bed4515733adedffb547
ms.sourcegitcommit: b5cd9d5d3b75a5537fc9ad8a3f085f0bb1845ee0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2018
ms.locfileid: "42925534"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="f7ef0-102">Operador || (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="f7ef0-102">|| Operator (C# Reference)</span></span>

<span data-ttu-id="f7ef0-103">O operador OR lógico condicional `||`, também conhecido como operador OR lógico de "curto-circuito", computa o OR lógico de seus operandos [bool](../keywords/bool.md).</span><span class="sxs-lookup"><span data-stu-id="f7ef0-103">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its [bool](../keywords/bool.md) operands.</span></span> <span data-ttu-id="f7ef0-104">O resultado de `x || y` será `true` se `x` ou `y` for avaliado como `true`.</span><span class="sxs-lookup"><span data-stu-id="f7ef0-104">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="f7ef0-105">Caso contrário, o resultado será `false`.</span><span class="sxs-lookup"><span data-stu-id="f7ef0-105">Otherwise, the result is `false`.</span></span> <span data-ttu-id="f7ef0-106">Se o primeiro operando for avaliado como `true`, o segundo operando não será avaliado e o resultado da operação será `true`.</span><span class="sxs-lookup"><span data-stu-id="f7ef0-106">If the first operand evaluates to `true`, the second operand is not evaluated and the result of operation is `true`.</span></span> <span data-ttu-id="f7ef0-107">O exemplo a seguir demonstra esse comportamento:</span><span class="sxs-lookup"><span data-stu-id="f7ef0-107">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[conditional logical OR](~/samples/snippets/csharp/language-reference/operators/ConditionalLogicalOperatorsExamples.cs#Or)]

<span data-ttu-id="f7ef0-108">O [operador OR lógico](or-operator.md) `|` também computa o OR lógico de seus operandos `bool`, mas sempre avalia os dois operandos.</span><span class="sxs-lookup"><span data-stu-id="f7ef0-108">The [logical OR operator](or-operator.md) `|` also computes the logical OR of its `bool` operands, but always evaluates both operands.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="f7ef0-109">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="f7ef0-109">Operator overloadability</span></span>

<span data-ttu-id="f7ef0-110">Um tipo definido pelo usuário não pode sobrecarregar o operador OR lógico condicional.</span><span class="sxs-lookup"><span data-stu-id="f7ef0-110">A user-defined type cannot overload the conditional logical OR operator.</span></span> <span data-ttu-id="f7ef0-111">No entanto, se um tipo definido pelo usuário sobrecarregar os operadores de [OR lógico](or-operator.md), [true](../keywords/true-operator.md) e [false](../keywords/false-operator.md) de uma determinada maneira, a operação `||` poderá ser avaliada para os operandos desse tipo.</span><span class="sxs-lookup"><span data-stu-id="f7ef0-111">However, if a user-defined type overloads the [logical OR](or-operator.md), [true](../keywords/true-operator.md), and [false](../keywords/false-operator.md) operators in a certain way, the `||` operation can be evaluated for the operands of that type.</span></span> <span data-ttu-id="f7ef0-112">Para obter mais informações, veja a seção [Operadores lógicos condicionais definidos pelo usuário](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) na [especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="f7ef0-112">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f7ef0-113">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="f7ef0-113">C# language specification</span></span>

<span data-ttu-id="f7ef0-114">Para obter mais informações, veja a seção [Operadores lógicos condicionais](~/_csharplang/spec/expressions.md#conditional-logical-operators) na [especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="f7ef0-114">For more information, see the [Conditional logical operators](~/_csharplang/spec/expressions.md#conditional-logical-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f7ef0-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f7ef0-115">See also</span></span>

- [<span data-ttu-id="f7ef0-116">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="f7ef0-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f7ef0-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="f7ef0-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f7ef0-118">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="f7ef0-118">C# Operators</span></span>](index.md)
- [<span data-ttu-id="f7ef0-119">Operador &&</span><span class="sxs-lookup"><span data-stu-id="f7ef0-119">&& operator</span></span>](conditional-and-operator.md)
- [<span data-ttu-id="f7ef0-120">Operador !</span><span class="sxs-lookup"><span data-stu-id="f7ef0-120">! operator</span></span>](logical-negation-operator.md)
- [<span data-ttu-id="f7ef0-121">Operador |</span><span class="sxs-lookup"><span data-stu-id="f7ef0-121">| operator</span></span>](or-operator.md)
