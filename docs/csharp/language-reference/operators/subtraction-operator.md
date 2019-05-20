---
title: '- Operador - referência do C#'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- -_CSharpKeyword
helpviewer_keywords:
- '- operator [C#]'
- subtraction operator (-) [C#]
ms.assetid: 4de7a4fa-c69d-48e6-aff1-3130af970b2d
ms.openlocfilehash: 920981addd5c779c9ad1c666ef45e1de5cd23408
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633011"
---
# <a name="--operator-c-reference"></a><span data-ttu-id="e87d2-102">Operador - (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="e87d2-102">- operator (C# Reference)</span></span>

<span data-ttu-id="e87d2-103">O operador `-` pode funcionar como um operador unário ou binário.</span><span class="sxs-lookup"><span data-stu-id="e87d2-103">The `-` operator can function as either a unary or a binary operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="e87d2-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="e87d2-104">Remarks</span></span>

<span data-ttu-id="e87d2-105">Os operadores `-` unários são predefinidos para todos os tipos numéricos.</span><span class="sxs-lookup"><span data-stu-id="e87d2-105">Unary `-` operators are predefined for all numeric types.</span></span> <span data-ttu-id="e87d2-106">O resultado de uma operação `-` unária em um tipo numérico é a negação numérica do operando.</span><span class="sxs-lookup"><span data-stu-id="e87d2-106">The result of a unary `-` operation on a numeric type is the numeric negation of the operand.</span></span>

<span data-ttu-id="e87d2-107">Os operadores `-` binários são predefinidos para todos os tipos numéricos e de enumeração para subtrair o segundo operando do primeiro.</span><span class="sxs-lookup"><span data-stu-id="e87d2-107">Binary `-` operators are predefined for all numeric and enumeration types to subtract the second operand from the first.</span></span>

<span data-ttu-id="e87d2-108">Os tipos delegados também fornecem um operador `-` binário, que executa a remoção de delegados.</span><span class="sxs-lookup"><span data-stu-id="e87d2-108">Delegate types also provide a binary `-` operator, which performs delegate removal.</span></span>

<span data-ttu-id="e87d2-109">Tipos definidos pelo usuário podem sobrecarregar os operadores `-` unários e `-` binários.</span><span class="sxs-lookup"><span data-stu-id="e87d2-109">User-defined types can overload the unary `-` and binary `-` operators.</span></span> <span data-ttu-id="e87d2-110">Para obter mais informações, confira a [palavra-chave operator](../keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="e87d2-110">For more information, see [operator keyword](../keywords/operator.md).</span></span>

## <a name="example"></a><span data-ttu-id="e87d2-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e87d2-111">Example</span></span>

[!code-csharp[csRefOperators#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#40)]

## <a name="see-also"></a><span data-ttu-id="e87d2-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e87d2-112">See also</span></span>

- [<span data-ttu-id="e87d2-113">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="e87d2-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e87d2-114">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="e87d2-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e87d2-115">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="e87d2-115">C# operators</span></span>](index.md)
