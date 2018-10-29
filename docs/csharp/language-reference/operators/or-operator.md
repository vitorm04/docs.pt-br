---
title: Operador | (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- '|_CSharpKeyword'
helpviewer_keywords:
- bitwise OR operator [C#]
- '| operator [C#]'
- binary operator (|) [C#]
ms.assetid: 82d6bb78-54c8-40bf-b679-531180ddaf70
ms.openlocfilehash: 999df9db0819a5f33e21a29b892de0a8854dd5d8
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48028153"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="79d1c-102">Operador | (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="79d1c-102">| Operator (C# Reference)</span></span>
<span data-ttu-id="79d1c-103">Os operadores binários `|` são predefinidos para os tipos integrais e `bool`.</span><span class="sxs-lookup"><span data-stu-id="79d1c-103">Binary `|` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="79d1c-104">Para tipos integrais, o `|` computa o OR bit a bit de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="79d1c-104">For integral types, `|` computes the bitwise OR of its operands.</span></span> <span data-ttu-id="79d1c-105">Para operandos `bool`, o `|` computa o OR lógico de seus operandos; ou seja, o resultado será `false` se e somente se, ambos seus operandos forem `false`.</span><span class="sxs-lookup"><span data-stu-id="79d1c-105">For `bool` operands, `|` computes the logical OR of its operands; that is, the result is `false` if and only if both its operands are `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79d1c-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="79d1c-106">Remarks</span></span>  
 <span data-ttu-id="79d1c-107">O operador binário `|` avalia ambos os operandos, independentemente do valor do primeiro, em contraste ao [operador OR-condicional](conditional-or-operator.md) `||`.</span><span class="sxs-lookup"><span data-stu-id="79d1c-107">The binary `|` operator evaluates both operands regardless of the first one's value, in contrast to the [conditional-OR operator](conditional-or-operator.md) `||`.</span></span>
 
 <span data-ttu-id="79d1c-108">Os tipos definidos pelo usuário podem sobrecarregar o operador `|` (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="79d1c-108">User-defined types can overload the `|` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="79d1c-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="79d1c-109">Example</span></span>  
 [!code-csharp[csRefOperators#31](../../../csharp/language-reference/operators/codesnippet/CSharp/or-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="79d1c-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="79d1c-110">See Also</span></span>

- [<span data-ttu-id="79d1c-111">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="79d1c-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="79d1c-112">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="79d1c-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="79d1c-113">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="79d1c-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
