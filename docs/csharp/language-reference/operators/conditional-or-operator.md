---
title: Operador || – Referência de C#
ms.custom: seodec18
ms.date: 11/06/2018
f1_keywords:
- '||_CSharpKeyword'
helpviewer_keywords:
- logical OR operator [C#]
- conditional-OR operator (||) [C#]
- '|| operator [C#]'
ms.assetid: 7d442d8e-400d-421f-b4d2-034bf82bcbdc
ms.openlocfilehash: f4bb7ada12fbcebcb90fb7cd22d6e6bccad5fb57
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244564"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="81662-102">Operador || (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="81662-102">|| Operator (C# Reference)</span></span>

<span data-ttu-id="81662-103">O operador OR lógico condicional `||`, também conhecido como operador OR lógico de "curto-circuito", computa o OR lógico de seus operandos [bool](../keywords/bool.md).</span><span class="sxs-lookup"><span data-stu-id="81662-103">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its [bool](../keywords/bool.md) operands.</span></span> <span data-ttu-id="81662-104">O resultado de `x || y` será `true` se `x` ou `y` for avaliado como `true`.</span><span class="sxs-lookup"><span data-stu-id="81662-104">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="81662-105">Caso contrário, o resultado será `false`.</span><span class="sxs-lookup"><span data-stu-id="81662-105">Otherwise, the result is `false`.</span></span> <span data-ttu-id="81662-106">Se o primeiro operando for avaliado como `true`, o segundo operando não será avaliado e o resultado da operação será `true`.</span><span class="sxs-lookup"><span data-stu-id="81662-106">If the first operand evaluates to `true`, the second operand is not evaluated and the result of operation is `true`.</span></span> <span data-ttu-id="81662-107">O exemplo a seguir demonstra esse comportamento:</span><span class="sxs-lookup"><span data-stu-id="81662-107">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[conditional logical OR](~/samples/snippets/csharp/language-reference/operators/ConditionalLogicalOperatorsExamples.cs#Or)]

<span data-ttu-id="81662-108">O [operador OR lógico](or-operator.md) `|` também computa o OR lógico de seus operandos `bool`, mas sempre avalia os dois operandos.</span><span class="sxs-lookup"><span data-stu-id="81662-108">The [logical OR operator](or-operator.md) `|` also computes the logical OR of its `bool` operands, but always evaluates both operands.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="81662-109">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="81662-109">Operator overloadability</span></span>

<span data-ttu-id="81662-110">Um tipo definido pelo usuário não pode sobrecarregar o operador OR lógico condicional.</span><span class="sxs-lookup"><span data-stu-id="81662-110">A user-defined type cannot overload the conditional logical OR operator.</span></span> <span data-ttu-id="81662-111">No entanto, se um tipo definido pelo usuário sobrecarregar os operadores de [OR lógico](or-operator.md), [true e false](../keywords/true-false-operators.md) de uma determinada maneira, a operação `||` poderá ser avaliada para os operandos desse tipo.</span><span class="sxs-lookup"><span data-stu-id="81662-111">However, if a user-defined type overloads the [logical OR](or-operator.md) and [true and false operators](../keywords/true-false-operators.md) in a certain way, the `||` operation can be evaluated for the operands of that type.</span></span> <span data-ttu-id="81662-112">Para obter mais informações, veja a seção [Operadores lógicos condicionais definidos pelo usuário](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) na [especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="81662-112">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="81662-113">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="81662-113">C# language specification</span></span>

<span data-ttu-id="81662-114">Para obter mais informações, veja a seção [Operadores lógicos condicionais](~/_csharplang/spec/expressions.md#conditional-logical-operators) na [especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="81662-114">For more information, see the [Conditional logical operators](~/_csharplang/spec/expressions.md#conditional-logical-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="81662-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="81662-115">See also</span></span>

- [<span data-ttu-id="81662-116">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="81662-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="81662-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="81662-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="81662-118">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="81662-118">C# Operators</span></span>](index.md)
- [<span data-ttu-id="81662-119">Operador &&</span><span class="sxs-lookup"><span data-stu-id="81662-119">&& operator</span></span>](conditional-and-operator.md)
- [<span data-ttu-id="81662-120">Operador !</span><span class="sxs-lookup"><span data-stu-id="81662-120">! operator</span></span>](logical-negation-operator.md)
- [<span data-ttu-id="81662-121">Operador |</span><span class="sxs-lookup"><span data-stu-id="81662-121">| operator</span></span>](or-operator.md)
