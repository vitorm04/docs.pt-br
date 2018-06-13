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
ms.openlocfilehash: 7b62af53f0d8b7cba29f4496887717f1726eabf9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33265681"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="12a3e-102">Operador | (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="12a3e-102">| Operator (C# Reference)</span></span>
<span data-ttu-id="12a3e-103">Os operadores binários `|` são predefinidos para os tipos integrais e `bool`.</span><span class="sxs-lookup"><span data-stu-id="12a3e-103">Binary `|` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="12a3e-104">Para tipos integrais, o `|` computa o OR bit a bit de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="12a3e-104">For integral types, `|` computes the bitwise OR of its operands.</span></span> <span data-ttu-id="12a3e-105">Para operandos `bool`, o `|` computa o OR lógico de seus operandos; ou seja, o resultado será `false` se e somente se, ambos seus operandos forem `false`.</span><span class="sxs-lookup"><span data-stu-id="12a3e-105">For `bool` operands, `|` computes the logical OR of its operands; that is, the result is `false` if and only if both its operands are `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12a3e-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="12a3e-106">Remarks</span></span>  
 <span data-ttu-id="12a3e-107">Os tipos definidos pelo usuário podem sobrecarregar o operador `|` (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="12a3e-107">User-defined types can overload the `|` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="12a3e-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="12a3e-108">Example</span></span>  
 [!code-csharp[csRefOperators#31](../../../csharp/language-reference/operators/codesnippet/CSharp/or-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="12a3e-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="12a3e-109">See Also</span></span>  
 [<span data-ttu-id="12a3e-110">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="12a3e-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="12a3e-111">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="12a3e-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="12a3e-112">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="12a3e-112">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
