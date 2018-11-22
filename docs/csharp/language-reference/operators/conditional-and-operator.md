---
title: Operador &amp;&amp; (Referência de C#)
ms.date: 11/06/2018
f1_keywords:
- '&&_CSharpKeyword'
helpviewer_keywords:
- '&& operator [C#]'
- logical AND operator [C#]
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
ms.openlocfilehash: d0e6d9a5aedc7dc87393e3dea070bf442b3268dc
ms.sourcegitcommit: b5cd9d5d3b75a5537fc9ad8a3f085f0bb1845ee0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2018
ms.locfileid: "43529229"
---
# <a name="ampamp-operator-c-reference"></a><span data-ttu-id="eb4f1-102">Operador &amp;&amp; (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="eb4f1-102">&amp;&amp; Operator (C# Reference)</span></span>

<span data-ttu-id="eb4f1-103">O operador AND lógico condicional `&&`, também conhecido como operador AND lógico de "curto-circuito", computa o AND lógico de seus operandos [bool](../keywords/bool.md).</span><span class="sxs-lookup"><span data-stu-id="eb4f1-103">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its [bool](../keywords/bool.md) operands.</span></span> <span data-ttu-id="eb4f1-104">O resultado de `x && y` será `true` se ambos `x` e `y` forem avaliados como `true`.</span><span class="sxs-lookup"><span data-stu-id="eb4f1-104">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="eb4f1-105">Caso contrário, o resultado será `false`.</span><span class="sxs-lookup"><span data-stu-id="eb4f1-105">Otherwise, the result is `false`.</span></span> <span data-ttu-id="eb4f1-106">Se o primeiro operando for avaliado como `false`, o segundo operando não será avaliado e o resultado da operação será `false`.</span><span class="sxs-lookup"><span data-stu-id="eb4f1-106">If the first operand evaluates to `false`, the second operand is not evaluated and the result of operation is `false`.</span></span> <span data-ttu-id="eb4f1-107">O exemplo a seguir demonstra esse comportamento:</span><span class="sxs-lookup"><span data-stu-id="eb4f1-107">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[conditional logical AND](~/samples/snippets/csharp/language-reference/operators/ConditionalLogicalOperatorsExamples.cs#And)]

<span data-ttu-id="eb4f1-108">O [operador AND lógico](and-operator.md) `&` também computa o AND lógico de seus `bool` operandos, mas sempre avalia os dois operandos.</span><span class="sxs-lookup"><span data-stu-id="eb4f1-108">The [logical AND operator](and-operator.md) `&` also computes the logical AND of its `bool` operands, but always evaluates both operands.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="eb4f1-109">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="eb4f1-109">Operator overloadability</span></span>

<span data-ttu-id="eb4f1-110">Um tipo definido pelo usuário não pode sobrecarregar o operador AND lógico condicional.</span><span class="sxs-lookup"><span data-stu-id="eb4f1-110">A user-defined type cannot overload the conditional logical AND operator.</span></span> <span data-ttu-id="eb4f1-111">No entanto, se um tipo definido pelo usuário sobrecarregar os operadores de [AND lógico](and-operator.md), [true](../keywords/true-operator.md) e [false](../keywords/false-operator.md) de uma determinada maneira, a operação `&&` poderá ser avaliada para os operandos desse tipo.</span><span class="sxs-lookup"><span data-stu-id="eb4f1-111">However, if a user-defined type overloads the [logical AND](and-operator.md), [true](../keywords/true-operator.md), and [false](../keywords/false-operator.md) operators in a certain way, the `&&` operation can be evaluated for the operands of that type.</span></span> <span data-ttu-id="eb4f1-112">Para obter mais informações, veja a seção [Operadores lógicos condicionais definidos pelo usuário](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) na [especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="eb4f1-112">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="eb4f1-113">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="eb4f1-113">C# language specification</span></span>

<span data-ttu-id="eb4f1-114">Para obter mais informações, veja a seção [Operadores lógicos condicionais](~/_csharplang/spec/expressions.md#conditional-logical-operators) na [especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="eb4f1-114">For more information, see the [Conditional logical operators](~/_csharplang/spec/expressions.md#conditional-logical-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="eb4f1-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eb4f1-115">See also</span></span>

- [<span data-ttu-id="eb4f1-116">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="eb4f1-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="eb4f1-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="eb4f1-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="eb4f1-118">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="eb4f1-118">C# Operators</span></span>](index.md)
- [<span data-ttu-id="eb4f1-119">Operador ||</span><span class="sxs-lookup"><span data-stu-id="eb4f1-119">|| operator</span></span>](conditional-or-operator.md)
- [<span data-ttu-id="eb4f1-120">Operador \!</span><span class="sxs-lookup"><span data-stu-id="eb4f1-120">! operator</span></span>](logical-negation-operator.md)
- [<span data-ttu-id="eb4f1-121">Operador &</span><span class="sxs-lookup"><span data-stu-id="eb4f1-121">& operator</span></span>](and-operator.md)
