---
title: '>> Operador - referência do C#'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '>>_CSharpKeyword'
helpviewer_keywords:
- '>> operator [C#]'
- right shift operator (>>) [C#]
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
ms.openlocfilehash: 703d4ee50bb9f49c66df029de9c5a280449d11fa
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55255309"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="13e12-102">Operador >> (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="13e12-102">>> operator (C# Reference)</span></span>

<span data-ttu-id="13e12-103">O operador de deslocamento para a direita (`>>`) desloca o primeiro operando à direita pelo número de bits especificado pelo seu segundo operando.</span><span class="sxs-lookup"><span data-stu-id="13e12-103">The right-shift operator (`>>`) shifts its first operand right by the number of bits specified by its second operand.</span></span>

## <a name="remarks"></a><span data-ttu-id="13e12-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="13e12-104">Remarks</span></span>

<span data-ttu-id="13e12-105">Se o primeiro operando for um [int](../keywords/int.md) ou [uint](../keywords/uint.md) (quantidade de 32 bits), a contagem de deslocamento será determinada pelos cinco bits de ordem inferior do segundo operando (segundo operando &0x1f).</span><span class="sxs-lookup"><span data-stu-id="13e12-105">If the first operand is an [int](../keywords/int.md) or [uint](../keywords/uint.md) (32-bit quantity), the shift count is given by the low-order five bits of the second operand (second operand & 0x1f).</span></span>

<span data-ttu-id="13e12-106">Se o primeiro operando for um [long](../keywords/long.md) ou [ulong](../keywords/ulong.md) (quantidade de 64 bits), a contagem de deslocamento será determinada pelos seis bits de ordem inferior do segundo operando (segundo operando & 0x3f).</span><span class="sxs-lookup"><span data-stu-id="13e12-106">If the first operand is a [long](../keywords/long.md) or [ulong](../keywords/ulong.md) (64-bit quantity), the shift count is given by the low-order six bits of the second operand (second operand & 0x3f).</span></span>

<span data-ttu-id="13e12-107">Se o primeiro operando for um [int](../keywords/int.md) ou [long](../keywords/long.md), o deslocamento para a direita será um deslocamento aritmético (bits vazios de ordem superior devem ser definidos como o bit de sinal).</span><span class="sxs-lookup"><span data-stu-id="13e12-107">If the first operand is an [int](../keywords/int.md) or [long](../keywords/long.md), the right-shift is an arithmetic shift (high-order empty bits are set to the sign bit).</span></span> <span data-ttu-id="13e12-108">Se o primeiro operando for do tipo [uint](../keywords/uint.md) ou [ulong](../keywords/ulong.md), o deslocamento para a direita será um deslocamento lógico (bits de ordem superior são preenchidos com zero).</span><span class="sxs-lookup"><span data-stu-id="13e12-108">If the first operand is of type [uint](../keywords/uint.md) or [ulong](../keywords/ulong.md), the right-shift is a logical shift (high-order bits are zero-filled).</span></span>

<span data-ttu-id="13e12-109">Tipos definidos pelo usuário podem sobrecarregar o operador `>>`; o tipo do primeiro operando deve ser o tipo definido pelo usuário e o tipo do segundo operando deve ser [int](../keywords/int.md). Para obter mais informações, consulte [operador](../keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="13e12-109">User-defined types can overload the `>>` operator; the type of the first operand must be the user-defined type, and the type of the second operand must be [int](../keywords/int.md). For more information, see [operator](../keywords/operator.md).</span></span> <span data-ttu-id="13e12-110">Quando um operador binário está sobrecarregado, o operador de atribuição correspondente, se houver, também estará implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="13e12-110">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>

## <a name="example"></a><span data-ttu-id="13e12-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="13e12-111">Example</span></span>

[!code-csharp[csRefOperators#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#26)]

## <a name="see-also"></a><span data-ttu-id="13e12-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13e12-112">See also</span></span>

- [<span data-ttu-id="13e12-113">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="13e12-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="13e12-114">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="13e12-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="13e12-115">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="13e12-115">C# operators</span></span>](index.md)