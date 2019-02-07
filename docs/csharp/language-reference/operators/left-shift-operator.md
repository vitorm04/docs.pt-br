---
title: Operador << – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <<_CSharpKeyword
helpviewer_keywords:
- left shift operator (<<) [C#]
- << operator [C#]
ms.assetid: a654eb56-1ff7-4bf3-9064-b631be0cdccc
ms.openlocfilehash: 0271c97bc624a8946b90508e9ce39d217a128c05
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55261744"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="29d4d-102">Operador \<\< (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="29d4d-102">\<\< operator (C# Reference)</span></span>

<span data-ttu-id="29d4d-103">O operador de deslocamento para a esquerda (`<<`) desloca o primeiro operando à esquerda pelo número de bits especificado pelo segundo operando.</span><span class="sxs-lookup"><span data-stu-id="29d4d-103">The left-shift operator (`<<`) shifts its first operand left by the number of bits specified by its second operand.</span></span> <span data-ttu-id="29d4d-104">O tipo do segundo operando deve ser um [int](../keywords/int.md) ou um tipo que tem uma conversão numérica implícita predefinida para `int`.</span><span class="sxs-lookup"><span data-stu-id="29d4d-104">The type of the second operand must be an [int](../keywords/int.md) or a type that has a predefined implicit numeric conversion to `int`.</span></span>

## <a name="remarks"></a><span data-ttu-id="29d4d-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="29d4d-105">Remarks</span></span>

<span data-ttu-id="29d4d-106">Se o primeiro operando for um [int](../keywords/int.md) ou [uint](../keywords/uint.md) (quantidade de 32 bits), a contagem de deslocamento será determinada pelos cinco bits de ordem inferior do segundo operando.</span><span class="sxs-lookup"><span data-stu-id="29d4d-106">If the first operand is an [int](../keywords/int.md) or [uint](../keywords/uint.md) (32-bit quantity), the shift count is given by the low-order five bits of the second operand.</span></span> <span data-ttu-id="29d4d-107">Ou seja, a contagem real de deslocamento é de 0 a 31 bits.</span><span class="sxs-lookup"><span data-stu-id="29d4d-107">That is, the actual shift count is 0 to 31 bits.</span></span>

<span data-ttu-id="29d4d-108">Se o primeiro operando for um [long](../keywords/long.md) ou [ulong](../keywords/ulong.md) (quantidade de 64 bits), a contagem de deslocamento será determinada pelos seis bits de ordem inferior do segundo operando.</span><span class="sxs-lookup"><span data-stu-id="29d4d-108">If the first operand is a [long](../keywords/long.md) or [ulong](../keywords/ulong.md) (64-bit quantity), the shift count is given by the low-order six bits of the second operand.</span></span> <span data-ttu-id="29d4d-109">Ou seja, a contagem real de deslocamento é de 0 a 63 bits.</span><span class="sxs-lookup"><span data-stu-id="29d4d-109">That is, the actual shift count is 0 to 63 bits.</span></span>

<span data-ttu-id="29d4d-110">Quaisquer bits de ordem superior que não estão dentro do intervalo do tipo do primeiro operando após a mudança são descartados e os bits vazios de ordem inferior são preenchidos com zeros.</span><span class="sxs-lookup"><span data-stu-id="29d4d-110">Any high-order bits that are not within the range of the type of the first operand after the shift are discarded, and the low-order empty bits are zero-filled.</span></span> <span data-ttu-id="29d4d-111">As operações de deslocamento nunca causam estouros.</span><span class="sxs-lookup"><span data-stu-id="29d4d-111">Shift operations never cause overflows.</span></span>

<span data-ttu-id="29d4d-112">Tipos definidos pelo usuário podem sobrecarregar o operador `<<` (consulte [operador](../keywords/operator.md)); o tipo do primeiro operando deve ser o tipo definido pelo usuário e o tipo do segundo operando deve ser `int`.</span><span class="sxs-lookup"><span data-stu-id="29d4d-112">User-defined types can overload the `<<` operator (see [operator](../keywords/operator.md)); the type of the first operand must be the user-defined type, and the type of the second operand must be `int`.</span></span> <span data-ttu-id="29d4d-113">Quando um operador binário está sobrecarregado, o operador de atribuição correspondente, se houver, também estará implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="29d4d-113">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>

## <a name="example"></a><span data-ttu-id="29d4d-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="29d4d-114">Example</span></span>

[!code-csharp[csRefOperators#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#14)]

## <a name="comments"></a><span data-ttu-id="29d4d-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="29d4d-115">Comments</span></span>

<span data-ttu-id="29d4d-116">Observe que `i<<1` e `i<<33` fornecem o mesmo resultado, porque 1 e 33 têm os mesmos cinco bits de ordem inferior.</span><span class="sxs-lookup"><span data-stu-id="29d4d-116">Note that `i<<1` and `i<<33` give the same result, because 1 and 33 have the same low-order five bits.</span></span>

## <a name="see-also"></a><span data-ttu-id="29d4d-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29d4d-117">See also</span></span>

- [<span data-ttu-id="29d4d-118">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="29d4d-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="29d4d-119">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="29d4d-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="29d4d-120">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="29d4d-120">C# Operators</span></span>](index.md)
