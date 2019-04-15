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
ms.openlocfilehash: 38f8e21dbd07868441e0c4fbb6074f9897905222
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59312872"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="1ac4f-102">Operador | (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="1ac4f-102">| operator (C# Reference)</span></span>

<span data-ttu-id="1ac4f-103">Os operadores binários `|` são predefinidos para os tipos integrais e `bool`.</span><span class="sxs-lookup"><span data-stu-id="1ac4f-103">Binary `|` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="1ac4f-104">Para tipos integrais, o `|` computa o OR bit a bit de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="1ac4f-104">For integral types, `|` computes the bitwise OR of its operands.</span></span> <span data-ttu-id="1ac4f-105">Para operandos `bool`, o `|` computa o OR lógico de seus operandos; ou seja, o resultado será `false` se e somente se, ambos seus operandos forem `false`.</span><span class="sxs-lookup"><span data-stu-id="1ac4f-105">For `bool` operands, `|` computes the logical OR of its operands; that is, the result is `false` if and only if both its operands are `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="1ac4f-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="1ac4f-106">Remarks</span></span>

<span data-ttu-id="1ac4f-107">O operador binário `|` avalia ambos os operandos, independentemente do valor do primeiro, em contraste ao [operador OR-condicional](boolean-logical-operators.md#conditional-logical-or-operator-) `||`.</span><span class="sxs-lookup"><span data-stu-id="1ac4f-107">The binary `|` operator evaluates both operands regardless of the first one's value, in contrast to the [conditional-OR operator](boolean-logical-operators.md#conditional-logical-or-operator-) `||`.</span></span>

<span data-ttu-id="1ac4f-108">Os tipos definidos pelo usuário podem sobrecarregar o operador `|` (consulte [operador](../keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="1ac4f-108">User-defined types can overload the `|` operator (see [operator](../keywords/operator.md)).</span></span>

## <a name="example"></a><span data-ttu-id="1ac4f-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1ac4f-109">Example</span></span>

 [!code-csharp[csRefOperators#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#31)]

## <a name="see-also"></a><span data-ttu-id="1ac4f-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1ac4f-110">See also</span></span>

- [<span data-ttu-id="1ac4f-111">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="1ac4f-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1ac4f-112">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="1ac4f-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1ac4f-113">Operadores C#</span><span class="sxs-lookup"><span data-stu-id="1ac4f-113">C# operators</span></span>](index.md)