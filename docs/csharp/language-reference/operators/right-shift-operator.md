---
title: '>> Operador - referência do C#'
ms.custom: seodec18
ms.date: 02/12/2019
f1_keywords:
- '>>_CSharpKeyword'
helpviewer_keywords:
- '>> operator [C#]'
- right shift operator (>>) [C#]
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
ms.openlocfilehash: 809cd2cab29d3378892ea224cf846e9d0909b073
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219718"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="3eb1e-102">Operador >> (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="3eb1e-102">>> operator (C# Reference)</span></span>

<span data-ttu-id="3eb1e-103">O operador de deslocamento para a direita `>>` desloca o primeiro operando à direita pelo número de bits definido pelo seu segundo operando.</span><span class="sxs-lookup"><span data-stu-id="3eb1e-103">The right-shift operator `>>` shifts its first operand right by the number of bits defined by its second operand.</span></span> <span data-ttu-id="3eb1e-104">Todos os tipos de inteiros dão suporte ao operador `>>`.</span><span class="sxs-lookup"><span data-stu-id="3eb1e-104">All integer types support the `>>` operator.</span></span> <span data-ttu-id="3eb1e-105">No entanto, o tipo do segundo operando deve ser [int](../keywords/int.md) ou um tipo que tem uma [conversão numérica implícita predefinida](../keywords/implicit-numeric-conversions-table.md) para `int`.</span><span class="sxs-lookup"><span data-stu-id="3eb1e-105">However, the type of the second operand must be [int](../keywords/int.md) or a type that has a [predefined implicit numeric conversion](../keywords/implicit-numeric-conversions-table.md) to `int`.</span></span>

<span data-ttu-id="3eb1e-106">A operação de deslocamento à direita descarta os bits de ordem inferior.</span><span class="sxs-lookup"><span data-stu-id="3eb1e-106">The right-shift operation discards the low-order bits.</span></span> <span data-ttu-id="3eb1e-107">As posições vazias de bit de ordem superior são definidas com base no tipo do primeiro operando da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="3eb1e-107">The high-order empty bit positions are set based on the type of the first operand as follows:</span></span>

- <span data-ttu-id="3eb1e-108">Se o primeiro operando for do tipo [int](../keywords/int.md) ou [long](../keywords/long.md), o operador de deslocamento à direita executará um deslocamento **aritmético**: o valor do bit mais significativo (o bit de sinal) do primeiro operando é propagado para as posições vazias de bits de ordem superior.</span><span class="sxs-lookup"><span data-stu-id="3eb1e-108">If the first operand is of type [int](../keywords/int.md) or [long](../keywords/long.md), the right-shift operator performs an **arithmetic** shift: the value of the most significant bit (the sign bit) of the first operand is propagated to the high-order empty bit positions.</span></span> <span data-ttu-id="3eb1e-109">Ou seja, as posições vazias de bit de ordem superior são definidas como zero se o primeiro operando for positivo e definidas como um se ele for negativo.</span><span class="sxs-lookup"><span data-stu-id="3eb1e-109">That is, the high-order empty bit positions are set to zero if the first operand is non-negative and set to one if it's negative.</span></span>

- <span data-ttu-id="3eb1e-110">Se o primeiro operando for do tipo [uint](../keywords/uint.md) ou [ulong](../keywords/ulong.md), o operador de deslocamento à direita executará um deslocamento **lógico**: as posições vazias de bit de ordem superior são sempre definidas como zero.</span><span class="sxs-lookup"><span data-stu-id="3eb1e-110">If the first operand is of type [uint](../keywords/uint.md) or [ulong](../keywords/ulong.md), the right-shift operator performs a **logical** shift: the high-order empty bit positions are always set to zero.</span></span>

<span data-ttu-id="3eb1e-111">O exemplo a seguir demonstra esse comportamento:</span><span class="sxs-lookup"><span data-stu-id="3eb1e-111">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[right shift example](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#RightShift)]

## <a name="shift-count"></a><span data-ttu-id="3eb1e-112">Contagem de deslocamentos</span><span class="sxs-lookup"><span data-stu-id="3eb1e-112">Shift count</span></span>

<span data-ttu-id="3eb1e-113">Para a expressão `x >> count`, a contagem real de deslocamento depende do tipo de `x` da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="3eb1e-113">For the expression `x >> count`, the actual shift count depends on the type of `x` as follows:</span></span>

- <span data-ttu-id="3eb1e-114">Se o tipo de `x` for [int](../keywords/int.md) ou [uint](../keywords/uint.md), a contagem de deslocamentos será determinada pelos *cinco* bits de ordem inferior do segundo operando.</span><span class="sxs-lookup"><span data-stu-id="3eb1e-114">If the type of `x` is [int](../keywords/int.md) or [uint](../keywords/uint.md), the shift count is given by the low-order *five* bits of the second operand.</span></span> <span data-ttu-id="3eb1e-115">Ou seja, a contagem de deslocamentos é calculada a partir de `count & 0x1F` (ou `count & 0b_1_1111`).</span><span class="sxs-lookup"><span data-stu-id="3eb1e-115">That is, the shift count is computed from `count & 0x1F` (or `count & 0b_1_1111`).</span></span>

- <span data-ttu-id="3eb1e-116">Se o tipo de `x` for [long](../keywords/long.md) ou [ulong](../keywords/ulong.md), a contagem de deslocamentos será determinada pelos *seis* bits de ordem inferior do segundo operando.</span><span class="sxs-lookup"><span data-stu-id="3eb1e-116">If the type of `x` is [long](../keywords/long.md) or [ulong](../keywords/ulong.md), the shift count is given by the low-order *six* bits of the second operand.</span></span> <span data-ttu-id="3eb1e-117">Ou seja, a contagem de deslocamentos é calculada a partir de `count & 0x3F` (ou `count & 0b_11_1111`).</span><span class="sxs-lookup"><span data-stu-id="3eb1e-117">That is, the shift count is computed from `count & 0x3F` (or `count & 0b_11_1111`).</span></span>

<span data-ttu-id="3eb1e-118">O exemplo a seguir demonstra esse comportamento:</span><span class="sxs-lookup"><span data-stu-id="3eb1e-118">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[shift count example](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#RightShiftByLargeCount)]

## <a name="remarks"></a><span data-ttu-id="3eb1e-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="3eb1e-119">Remarks</span></span>

<span data-ttu-id="3eb1e-120">As operações de deslocamento nunca causam estouros e produzem os mesmos resultados nos contextos [marcados e desmarcados](../keywords/checked-and-unchecked.md).</span><span class="sxs-lookup"><span data-stu-id="3eb1e-120">Shift operations never cause overflows and produce the same results in [checked and unchecked](../keywords/checked-and-unchecked.md) contexts.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="3eb1e-121">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="3eb1e-121">Operator overloadability</span></span>

<span data-ttu-id="3eb1e-122">Tipos definidos pelo usuário podem [sobrecarregar](../keywords/operator.md) o operador `>>`.</span><span class="sxs-lookup"><span data-stu-id="3eb1e-122">User-defined types can [overload](../keywords/operator.md) the `>>` operator.</span></span> <span data-ttu-id="3eb1e-123">Se um tipo definido pelo usuário `T` sobrecarregar o operador `>>`, o tipo do primeiro operando deverá ser `T` e o tipo do segundo operando deverá ser `int`.</span><span class="sxs-lookup"><span data-stu-id="3eb1e-123">If a user-defined type `T` overloads the `>>` operator, the type of the first operand must be `T` and the type of the second operand must be `int`.</span></span> <span data-ttu-id="3eb1e-124">Quando um operador `>>` é sobrecarregado, o [operador de atribuição de deslocamento à direita](right-shift-assignment-operator.md) `>>=` também é implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="3eb1e-124">When the `>>` operator is overloaded, the [right-shift assignment operator](right-shift-assignment-operator.md) `>>=` is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3eb1e-125">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="3eb1e-125">C# language specification</span></span>

<span data-ttu-id="3eb1e-126">Saiba mais na seção [Operadores de deslocamento](~/_csharplang/spec/expressions.md#shift-operators) na [Especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="3eb1e-126">For more information, see the [Shift operators](~/_csharplang/spec/expressions.md#shift-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3eb1e-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3eb1e-127">See also</span></span>

- [<span data-ttu-id="3eb1e-128">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="3eb1e-128">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3eb1e-129">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="3eb1e-129">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3eb1e-130">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="3eb1e-130">C# operators</span></span>](index.md)
- [<span data-ttu-id="3eb1e-131">Operador <<</span><span class="sxs-lookup"><span data-stu-id="3eb1e-131"><< operator</span></span>](left-shift-operator.md)