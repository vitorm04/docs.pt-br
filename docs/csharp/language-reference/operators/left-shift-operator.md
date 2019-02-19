---
title: Operador << – Referência de C#
ms.custom: seodec18
ms.date: 02/12/2019
f1_keywords:
- <<_CSharpKeyword
helpviewer_keywords:
- left shift operator (<<) [C#]
- << operator [C#]
ms.assetid: a654eb56-1ff7-4bf3-9064-b631be0cdccc
ms.openlocfilehash: deea2d0f720ba7f096e65c67378586bc88f24673
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219427"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="b4da6-102">Operador \<\< (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="b4da6-102">\<\< operator (C# Reference)</span></span>

<span data-ttu-id="b4da6-103">O operador de deslocamento à esquerda `<<` desloca o primeiro operando à esquerda pelo número de bits definido pelo segundo operando.</span><span class="sxs-lookup"><span data-stu-id="b4da6-103">The left-shift operator `<<` shifts its first operand left by the number of bits defined by its second operand.</span></span> <span data-ttu-id="b4da6-104">Todos os tipos de inteiros dão suporte ao operador `<<`.</span><span class="sxs-lookup"><span data-stu-id="b4da6-104">All integer types support the `<<` operator.</span></span> <span data-ttu-id="b4da6-105">No entanto, o tipo do segundo operando deve ser [int](../keywords/int.md) ou um tipo que tem uma [conversão numérica implícita predefinida](../keywords/implicit-numeric-conversions-table.md) para `int`.</span><span class="sxs-lookup"><span data-stu-id="b4da6-105">However, the type of the second operand must be [int](../keywords/int.md) or a type that has a [predefined implicit numeric conversion](../keywords/implicit-numeric-conversions-table.md) to `int`.</span></span>

<span data-ttu-id="b4da6-106">Os bits de ordem superior que estão fora do intervalo do tipo de resultado são descartados e as posições de bits vazios de ordem inferior são definidas como zero, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="b4da6-106">The high-order bits that are outside the range of the result type are discarded, and the low-order empty bit positions are set to zero, as the following example shows:</span></span>

[!code-csharp-interactive[left shift example](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#LeftShift)]

## <a name="shift-count"></a><span data-ttu-id="b4da6-107">Contagem de deslocamentos</span><span class="sxs-lookup"><span data-stu-id="b4da6-107">Shift count</span></span>

<span data-ttu-id="b4da6-108">Para a expressão `x << count`, a contagem real de deslocamento depende do tipo de `x` da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="b4da6-108">For the expression `x << count`, the actual shift count depends on the type of `x` as follows:</span></span>

- <span data-ttu-id="b4da6-109">Se o tipo de `x` for [int](../keywords/int.md) ou [uint](../keywords/uint.md), a contagem de deslocamentos será determinada pelos *cinco* bits de ordem inferior do segundo operando.</span><span class="sxs-lookup"><span data-stu-id="b4da6-109">If the type of `x` is [int](../keywords/int.md) or [uint](../keywords/uint.md), the shift count is given by the low-order *five* bits of the second operand.</span></span> <span data-ttu-id="b4da6-110">Ou seja, a contagem de deslocamentos é calculada a partir de `count & 0x1F` (ou `count & 0b_1_1111`).</span><span class="sxs-lookup"><span data-stu-id="b4da6-110">That is, the shift count is computed from `count & 0x1F` (or `count & 0b_1_1111`).</span></span>

- <span data-ttu-id="b4da6-111">Se o tipo de `x` for [long](../keywords/long.md) ou [ulong](../keywords/ulong.md), a contagem de deslocamentos será determinada pelos *seis* bits de ordem inferior do segundo operando.</span><span class="sxs-lookup"><span data-stu-id="b4da6-111">If the type of `x` is [long](../keywords/long.md) or [ulong](../keywords/ulong.md), the shift count is given by the low-order *six* bits of the second operand.</span></span> <span data-ttu-id="b4da6-112">Ou seja, a contagem de deslocamentos é calculada a partir de `count & 0x3F` (ou `count & 0b_11_1111`).</span><span class="sxs-lookup"><span data-stu-id="b4da6-112">That is, the shift count is computed from `count & 0x3F` (or `count & 0b_11_1111`).</span></span>

<span data-ttu-id="b4da6-113">O exemplo a seguir demonstra esse comportamento:</span><span class="sxs-lookup"><span data-stu-id="b4da6-113">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[shift count example](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#LeftShiftByLargeCount)]

## <a name="remarks"></a><span data-ttu-id="b4da6-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="b4da6-114">Remarks</span></span>

<span data-ttu-id="b4da6-115">As operações de deslocamento nunca causam estouros e produzem os mesmos resultados nos contextos [marcados e desmarcados](../keywords/checked-and-unchecked.md).</span><span class="sxs-lookup"><span data-stu-id="b4da6-115">Shift operations never cause overflows and produce the same results in [checked and unchecked](../keywords/checked-and-unchecked.md) contexts.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="b4da6-116">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="b4da6-116">Operator overloadability</span></span>

<span data-ttu-id="b4da6-117">Tipos definidos pelo usuário podem [sobrecarregar](../keywords/operator.md) o operador `<<`.</span><span class="sxs-lookup"><span data-stu-id="b4da6-117">User-defined types can [overload](../keywords/operator.md) the `<<` operator.</span></span> <span data-ttu-id="b4da6-118">Se um tipo definido pelo usuário `T` sobrecarregar o operador `<<`, o tipo do primeiro operando deverá ser `T` e o tipo do segundo operando deverá ser `int`.</span><span class="sxs-lookup"><span data-stu-id="b4da6-118">If a user-defined type `T` overloads the `<<` operator, the type of the first operand must be `T` and the type of the second operand must be `int`.</span></span> <span data-ttu-id="b4da6-119">Quando um operador `<<` é sobrecarregado, o [operador de atribuição de deslocamento para a esquerda](left-shift-assignment-operator.md) `<<=` também é implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="b4da6-119">When the `<<` operator is overloaded, the [left-shift assignment operator](left-shift-assignment-operator.md) `<<=` is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b4da6-120">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="b4da6-120">C# language specification</span></span>

<span data-ttu-id="b4da6-121">Saiba mais na seção [Operadores de deslocamento](~/_csharplang/spec/expressions.md#shift-operators) na [Especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="b4da6-121">For more information, see the [Shift operators](~/_csharplang/spec/expressions.md#shift-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b4da6-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b4da6-122">See also</span></span>

- [<span data-ttu-id="b4da6-123">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="b4da6-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b4da6-124">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="b4da6-124">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b4da6-125">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="b4da6-125">C# Operators</span></span>](index.md)
- [<span data-ttu-id="b4da6-126">Operador >></span><span class="sxs-lookup"><span data-stu-id="b4da6-126">>> operator</span></span>](right-shift-operator.md)
