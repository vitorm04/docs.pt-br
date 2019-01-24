---
title: Operador ^ – referência do C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ^_CSharpKeyword
helpviewer_keywords:
- ^ operator [C#]
- bitwise exclusive OR operator [C#]
ms.assetid: b09bc815-570f-4db6-a637-5b4ed99d014a
ms.openlocfilehash: 152be2d81d1bf340b839d74f169d63d7260f7ca5
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333701"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="bc68a-102">Operador ^ (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="bc68a-102">^ operator (C# Reference)</span></span>

<span data-ttu-id="bc68a-103">Os operadores binários `^` são predefinidos para os tipos integrais e `bool`.</span><span class="sxs-lookup"><span data-stu-id="bc68a-103">Binary `^` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="bc68a-104">Para os tipos integrais, o `^` computa o OR exclusivo bit a bit de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="bc68a-104">For integral types, `^` computes the bitwise exclusive-OR of its operands.</span></span> <span data-ttu-id="bc68a-105">Para operandos `bool`, o `^` computa o OR exclusivo lógico de seus operandos; ou seja, o resultado será `true` se e somente se exatamente um dos operandos for `true`.</span><span class="sxs-lookup"><span data-stu-id="bc68a-105">For `bool` operands, `^` computes the logical exclusive-or of its operands; that is, the result is `true` if and only if exactly one of its operands is `true`.</span></span>

## <a name="remarks"></a><span data-ttu-id="bc68a-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="bc68a-106">Remarks</span></span>

<span data-ttu-id="bc68a-107">Os tipos definidos pelo usuário podem sobrecarregar o operador `^` (consulte [operador](../keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="bc68a-107">User-defined types can overload the `^` operator (see [operator](../keywords/operator.md)).</span></span> <span data-ttu-id="bc68a-108">As operações em tipos integrais geralmente são permitidas na enumeração.</span><span class="sxs-lookup"><span data-stu-id="bc68a-108">Operations on integral types are generally allowed on enumeration.</span></span>

## <a name="example"></a><span data-ttu-id="bc68a-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bc68a-109">Example</span></span>

[!code-csharp[csRefOperators#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#30)]

<span data-ttu-id="bc68a-110">O cálculo de `0xf8 ^ 0x3f` no exemplo anterior executa um OR exclusivo bit a bit dos dois valores binários a seguir, que correspondem aos valores hexadecimais F8 e 3F:</span><span class="sxs-lookup"><span data-stu-id="bc68a-110">The computation of `0xf8 ^ 0x3f` in the previous example performs a bitwise exclusive-OR of the following two binary values, which correspond to the hexadecimal values F8 and 3F:</span></span>

`1111 1000`

`0011 1111`

<span data-ttu-id="bc68a-111">O resultado do OR exclusivo é `1100 0111`, que é igual a C7 em hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="bc68a-111">The result of the exclusive-OR is `1100 0111`, which is C7 in hexadecimal.</span></span>

## <a name="see-also"></a><span data-ttu-id="bc68a-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bc68a-112">See Also</span></span>

- [<span data-ttu-id="bc68a-113">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="bc68a-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="bc68a-114">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="bc68a-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="bc68a-115">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="bc68a-115">C# operators</span></span>](index.md)
