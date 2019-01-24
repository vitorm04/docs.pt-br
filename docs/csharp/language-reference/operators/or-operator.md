---
title: Operador | – referência do C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '|_CSharpKeyword'
helpviewer_keywords:
- bitwise OR operator [C#]
- '| operator [C#]'
- binary operator (|) [C#]
ms.assetid: 82d6bb78-54c8-40bf-b679-531180ddaf70
ms.openlocfilehash: 185ea3aabff4794ec08cca541773dbec3574ab4b
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333506"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="236f4-102">Operador | (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="236f4-102">| operator (C# Reference)</span></span>

<span data-ttu-id="236f4-103">Os operadores binários `|` são predefinidos para os tipos integrais e `bool`.</span><span class="sxs-lookup"><span data-stu-id="236f4-103">Binary `|` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="236f4-104">Para tipos integrais, o `|` computa o OR bit a bit de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="236f4-104">For integral types, `|` computes the bitwise OR of its operands.</span></span> <span data-ttu-id="236f4-105">Para operandos `bool`, o `|` computa o OR lógico de seus operandos; ou seja, o resultado será `false` se e somente se, ambos seus operandos forem `false`.</span><span class="sxs-lookup"><span data-stu-id="236f4-105">For `bool` operands, `|` computes the logical OR of its operands; that is, the result is `false` if and only if both its operands are `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="236f4-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="236f4-106">Remarks</span></span>

<span data-ttu-id="236f4-107">O operador binário `|` avalia ambos os operandos, independentemente do valor do primeiro, em contraste ao [operador OR-condicional](conditional-or-operator.md) `||`.</span><span class="sxs-lookup"><span data-stu-id="236f4-107">The binary `|` operator evaluates both operands regardless of the first one's value, in contrast to the [conditional-OR operator](conditional-or-operator.md) `||`.</span></span>

<span data-ttu-id="236f4-108">Os tipos definidos pelo usuário podem sobrecarregar o operador `|` (consulte [operador](../keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="236f4-108">User-defined types can overload the `|` operator (see [operator](../keywords/operator.md)).</span></span>

## <a name="example"></a><span data-ttu-id="236f4-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="236f4-109">Example</span></span>

 [!code-csharp[csRefOperators#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#31)]

## <a name="see-also"></a><span data-ttu-id="236f4-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="236f4-110">See also</span></span>

- [<span data-ttu-id="236f4-111">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="236f4-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="236f4-112">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="236f4-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="236f4-113">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="236f4-113">C# operators</span></span>](index.md)