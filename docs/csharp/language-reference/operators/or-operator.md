---
title: Operador | – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '|_CSharpKeyword'
helpviewer_keywords:
- bitwise OR operator [C#]
- '| operator [C#]'
- binary operator (|) [C#]
ms.assetid: 82d6bb78-54c8-40bf-b679-531180ddaf70
ms.openlocfilehash: 19a37bbb54d2ef3e15e4465df05c9b6df705206c
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240353"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="533b1-102">Operador | (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="533b1-102">| Operator (C# Reference)</span></span>
<span data-ttu-id="533b1-103">Os operadores binários `|` são predefinidos para os tipos integrais e `bool`.</span><span class="sxs-lookup"><span data-stu-id="533b1-103">Binary `|` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="533b1-104">Para tipos integrais, o `|` computa o OR bit a bit de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="533b1-104">For integral types, `|` computes the bitwise OR of its operands.</span></span> <span data-ttu-id="533b1-105">Para operandos `bool`, o `|` computa o OR lógico de seus operandos; ou seja, o resultado será `false` se e somente se, ambos seus operandos forem `false`.</span><span class="sxs-lookup"><span data-stu-id="533b1-105">For `bool` operands, `|` computes the logical OR of its operands; that is, the result is `false` if and only if both its operands are `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="533b1-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="533b1-106">Remarks</span></span>  
 <span data-ttu-id="533b1-107">O operador binário `|` avalia ambos os operandos, independentemente do valor do primeiro, em contraste ao [operador OR-condicional](conditional-or-operator.md) `||`.</span><span class="sxs-lookup"><span data-stu-id="533b1-107">The binary `|` operator evaluates both operands regardless of the first one's value, in contrast to the [conditional-OR operator](conditional-or-operator.md) `||`.</span></span>
 
 <span data-ttu-id="533b1-108">Os tipos definidos pelo usuário podem sobrecarregar o operador `|` (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="533b1-108">User-defined types can overload the `|` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="533b1-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="533b1-109">Example</span></span>  
 [!code-csharp[csRefOperators#31](../../../csharp/language-reference/operators/codesnippet/CSharp/or-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="533b1-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="533b1-110">See Also</span></span>

- [<span data-ttu-id="533b1-111">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="533b1-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="533b1-112">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="533b1-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="533b1-113">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="533b1-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
