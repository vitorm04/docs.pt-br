---
title: Operador / – Referência de C#
ms.custom: seodec18
ms.date: 12/13/2018
f1_keywords:
- /_CSharpKeyword
helpviewer_keywords:
- / operator [C#]
- division operator [C#]
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
ms.openlocfilehash: 45bcd64b60e7d13f389064faefeda815ea1f32c9
ms.sourcegitcommit: d6e419f9d9cd7e8f21ebf5acde6d016c16332579
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/12/2018
ms.locfileid: "53286527"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="0ef93-102">Operador / (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="0ef93-102">/ Operator (C# Reference)</span></span>

<span data-ttu-id="0ef93-103">O operador de divisão `/` divide o primeiro operando pelo segundo.</span><span class="sxs-lookup"><span data-stu-id="0ef93-103">The division operator `/` divides its first operand by its second operand.</span></span> <span data-ttu-id="0ef93-104">Todos os tipos numéricos são compatíveis com o operador de divisão.</span><span class="sxs-lookup"><span data-stu-id="0ef93-104">All numeric types support the division operator.</span></span>

## <a name="integer-division"></a><span data-ttu-id="0ef93-105">Divisão de inteiros</span><span class="sxs-lookup"><span data-stu-id="0ef93-105">Integer division</span></span>

<span data-ttu-id="0ef93-106">Para os operandos de tipos inteiros, o resultado do operador `/` é de um tipo inteiro e igual ao quociente dos dois operandos arredondados para zero:</span><span class="sxs-lookup"><span data-stu-id="0ef93-106">For the operands of integer types, the result of the `/` operator is of an integer type and equals the quotient of the two operands rounded towards zero:</span></span>

[!code-csharp-interactive[integer division](~/samples/snippets/csharp/language-reference/operators/DivisionExamples.cs#Integer)]

<span data-ttu-id="0ef93-107">Para obter o quociente dos dois operandos como um número de ponto flutuante, use o tipo `float`, `double` ou `decimal`:</span><span class="sxs-lookup"><span data-stu-id="0ef93-107">To obtain the quotient of the two operands as a floating-point number, use the `float`, `double`, or `decimal` type:</span></span>

[!code-csharp-interactive[integer as floating-point division](~/samples/snippets/csharp/language-reference/operators/DivisionExamples.cs#IntegerAsFloatingPoint)]

## <a name="floating-point-division"></a><span data-ttu-id="0ef93-108">Divisão de ponto flutuante</span><span class="sxs-lookup"><span data-stu-id="0ef93-108">Floating-point division</span></span>

<span data-ttu-id="0ef93-109">Para os tipos `float`, `double` e `decimal`, o resultado do operador `/` é o quociente dos dois operandos:</span><span class="sxs-lookup"><span data-stu-id="0ef93-109">For the `float`, `double`, and `decimal` types, the result of the `/` operator is the quotient of the two operands:</span></span>

[!code-csharp-interactive[floating-point division](~/samples/snippets/csharp/language-reference/operators/DivisionExamples.cs#FloatingPoint)]

<span data-ttu-id="0ef93-110">Se um dos operandos é `decimal`, outro operando não pode ser `float` nem `double`, porque nem `float` ou `double` é implicitamente conversível para `decimal`.</span><span class="sxs-lookup"><span data-stu-id="0ef93-110">If one of the operands is `decimal`, another operand can be neither `float` nor `double`, because neither `float` nor `double` is implicitly convertible to `decimal`.</span></span> <span data-ttu-id="0ef93-111">Você deve converter explicitamente o operando `float` ou `double` para o tipo `decimal`.</span><span class="sxs-lookup"><span data-stu-id="0ef93-111">You must explicitly convert the `float` or `double` operand to the `decimal` type.</span></span> <span data-ttu-id="0ef93-112">Para saber mais sobre as conversões implícitas entre tipos numéricos, confira a [Tabela de conversões numéricas implícitas](../keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="0ef93-112">For more information about implicit conversions between numeric types, see [Implicit numeric conversions table](../keywords/implicit-numeric-conversions-table.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="0ef93-113">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="0ef93-113">Operator overloadability</span></span>

<span data-ttu-id="0ef93-114">Tipos definidos pelo usuário podem [sobrecarregar](../keywords/operator.md) o operador `/`.</span><span class="sxs-lookup"><span data-stu-id="0ef93-114">User-defined types can [overload](../keywords/operator.md) the `/` operator.</span></span> <span data-ttu-id="0ef93-115">Quando um operador `/` é sobrecarregado, o [operador de atribuição de divisão](division-assignment-operator.md) `/=` também é implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="0ef93-115">When the `/` operator is overloaded, the [division assignment operator](division-assignment-operator.md) `/=` is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0ef93-116">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="0ef93-116">C# language specification</span></span>

<span data-ttu-id="0ef93-117">Para saber mais, confira a seção [Operador de divisão](~/_csharplang/spec/expressions.md#division-operator) na [especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="0ef93-117">For more information, see the [Division operator](~/_csharplang/spec/expressions.md#division-operator) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0ef93-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef93-118">See also</span></span>

- [<span data-ttu-id="0ef93-119">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="0ef93-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0ef93-120">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="0ef93-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0ef93-121">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="0ef93-121">C# Operators</span></span>](index.md)
- [<span data-ttu-id="0ef93-122">Operador %</span><span class="sxs-lookup"><span data-stu-id="0ef93-122">% Operator</span></span>](remainder-operator.md)
